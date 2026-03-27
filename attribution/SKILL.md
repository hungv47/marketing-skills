---
name: attribution
description: "Maps marketing activities to business outcomes — evaluates channel ROI, identifies what's driving results, and recommends where to double down or cut spend. Produces `.agents/mkt/attribution.md`. Not for setting new KPIs (use funnel-planner) or creating new content (use content-create)."
argument-hint: "[initiatives or KPIs to map]"
license: MIT
metadata:
  author: hungv47
  version: "3.0.0"
---

# Attribution Mapping — Orchestrator

*Communication — Step 4 of 4. Validates the system — every initiative and content piece connects to a KPI, with action items for every gap.*

**Core Question:** "Can we trace every initiative to a measurable outcome?"

---

## Critical Gates — Read First

1. **Every KPI has >= 1 initiative** mapped or an explicit action item. No uncovered KPIs.
2. **Every initiative maps to a KPI** or has a Kill/Reframe/Test recommendation with reason.
3. **Every recommendation is a verb** (Create / Kill / Rebalance / Test / Assign) — not an observation.
4. **Review date is set** (~4 weeks from today).
5. **Critic returns PASS** before delivery. Max 2 rewrite cycles.

---

## Inputs Required
- KPIs from `.agents/targets.md` or existing OKRs
- Initiatives from `.agents/solution-design.md`
- Content from `.agents/mkt/imc-plan.md` or `.agents/mkt/content/`

## Output
- `.agents/mkt/attribution.md`

---

## Agent Manifest

| Agent | File | Focus | Layer |
|-------|------|-------|-------|
| **kpi-hierarchy-agent** | `agents/kpi-hierarchy-agent.md` | Builds North Star → Leading → Supporting metric tree | L1 |
| **initiative-mapper-agent** | `agents/initiative-mapper-agent.md` | Maps initiatives to KPIs with contribution % and confidence | L2 (after kpi-hierarchy) |
| **content-mapper-agent** | `agents/content-mapper-agent.md` | Maps content to initiatives with funnel roles | L3 (after initiative-mapper) |
| **gap-analysis-agent** | `agents/gap-analysis-agent.md` | Identifies uncovered KPIs, low-confidence initiatives, funnel imbalances | L4 (after content-mapper) |
| **action-agent** | `agents/action-agent.md` | Converts gaps into prioritized action items | L5 (after gap-analysis) |
| **critic-agent** | `agents/critic-agent.md` | Quality gate — PASS/FAIL with rewrite routing | L6 (final) |

### Dependency Chain

```
kpi-hierarchy-agent (L1)
  └─► initiative-mapper-agent (L2) — needs KPI tree to map against
        └─► content-mapper-agent (L3) — needs initiative map to map against
              └─► gap-analysis-agent (L4) — needs full chain to analyze
                    └─► action-agent (L5) — needs gaps to convert
                          └─► critic-agent (L6) — evaluates merged output
```

**Why fully sequential:** Each agent's output is a required input for the next. Initiative mapping requires the KPI hierarchy (to know what to map to). Content mapping requires the initiative map (to know what to map to). Gap analysis requires all three maps. Actions require the gaps. The critic evaluates everything.

---

## Routing Logic

### Route A: Quick Attribution Check
**Trigger:** User asks to check attribution for specific initiatives or KPIs, or wants a lightweight audit.
**Chain:** kpi-hierarchy → initiative-mapper → gap-analysis → action → critic
**Skip:** content-mapper (no content audit needed for a quick check)

### Route B: Full Attribution
**Trigger:** User asks for full attribution mapping, or this is a first-time run.
**Chain:** kpi-hierarchy → initiative-mapper → content-mapper → gap-analysis → action → critic
**Skip:** Nothing — all agents run.

### Route C: Re-Run (Monthly Cadence)
**Trigger:** Previous `.agents/mkt/attribution.md` exists, or user says "re-run" / "monthly review."
**Chain:** Same as Route B, but with these additions:
1. Read previous `attribution.md` before dispatch
2. Pass prior action items to action-agent in pre-writing for progress tracking
3. Rename previous file to `attribution.v[N].md`
4. action-agent checks prior action status and flags escalations

---

## Dispatch Protocol

### Before Starting

#### Step 0: Product Context
Check for `.agents/product-context.md`. If available, read for product context. If missing, strongly recommend running `icp-research` first — attribution mapping is significantly more accurate with product context.
If `.agents/targets.md`, `.agents/solution-design.md`, or `.agents/mkt/imc-plan.md` `date` fields are older than 30 days, recommend re-running upstream skills — stale data produces inaccurate attribution maps.

#### Required Artifacts
None — can build from scratch by interviewing.

#### Optional Artifacts
| Artifact | Source | Benefit |
|----------|--------|---------|
| `targets.md` | funnel-planner | KPI baselines |
| `solution-design.md` | solution-design (from hungv47/strategy-skills) | Initiative list to map |
| `imc-plan.md` | imc-plan | Content plan to audit |
| Previous `attribution.md` | attribution | Check progress on prior action items |
| `experiment-*.md` | experiment (from strategy-skills) | Experiment outcomes as confidence adjustments — concluded experiments update contribution confidence |

Read upstream files if they exist: `.agents/targets.md`, `.agents/solution-design.md`, `.agents/mkt/imc-plan.md`. If previous `.agents/mkt/attribution.md` exists, read it — check progress on prior action items before building the new map.

#### Interview
If no upstream files exist, interview for:
1. "What's your North Star metric?"
2. "What are your 3-5 primary KPIs?"
3. "What initiatives are you running or planning?"
4. "What content are you producing?"

### Cross-Track Prerequisites
This skill maps content → initiatives → KPIs. For full-stack attribution:
1. **Strategy stack first** (optional): Run `problem-analysis` → `solution-design` → `funnel-planner` to generate `.agents/solution-design.md` (initiatives) and `.agents/targets.md` (KPIs).
2. **Comms stack**: Run `icp-research` → `imc-plan` → `content-create` to generate content artifacts.
3. **Then attribution**: Maps content to initiatives to KPIs with gap analysis.

Without strategy artifacts, this skill interviews for KPIs and initiatives directly — it still works, but cross-stack alignment is stronger with upstream artifacts.

### Single-Agent Fallback
If the environment does not support multi-agent dispatch, execute all steps sequentially in a single pass following the same order: build KPI hierarchy → map initiatives → map content → analyze gaps → write actions. Apply the critic checklist as a self-check before delivery.

---

## Layer Dispatch

### Pre-writing (gathered before any agent runs)
```yaml
brief: [user's attribution task]
product_context: [from product-context.md if available]
business_model: [from interview or upstream artifacts]
upstream_artifacts:
  targets: [contents of targets.md or null]
  solution_design: [contents of solution-design.md or null]
  imc_plan: [contents of imc-plan.md or null]
  previous_attribution: [contents of prior attribution.md or null]
  experiments: [contents of experiment-*.md files or null]
route: [A / B / C]
review_date: [today + 4 weeks]
```

### L1: KPI Hierarchy Agent
```yaml
agent: kpi-hierarchy-agent
input:
  brief: ${brief}
  pre-writing: ${pre_writing}
  upstream: null
  references:
    - references/attribution-models.md
    - references/attribution-examples.md
  feedback: null  # or critic feedback on rewrite cycle
```

### L2: Initiative Mapper Agent
```yaml
agent: initiative-mapper-agent
input:
  brief: ${brief}
  pre-writing: ${pre_writing}
  upstream: ${kpi_hierarchy_agent.output}
  references:
    - references/attribution-examples.md
    - references/attribution-models.md
  feedback: null
```

### L3: Content Mapper Agent (Route B and C only)
```yaml
agent: content-mapper-agent
input:
  brief: ${brief}
  pre-writing: ${pre_writing}
  upstream: ${initiative_mapper_agent.output}
  references:
    - references/attribution-examples.md
    - references/tracking-guide.md
  feedback: null
```

### L4: Gap Analysis Agent
```yaml
agent: gap-analysis-agent
input:
  brief: ${brief}
  pre-writing: ${pre_writing}
  upstream: ${merged_L1_L2_L3}  # merged output from all prior agents
  references:
    - references/attribution-models.md
    - references/tracking-guide.md
  feedback: null
```

### L5: Action Agent
```yaml
agent: action-agent
input:
  brief: ${brief}
  pre-writing: ${pre_writing}  # includes prior action items on Route C
  upstream: ${merged_all_prior}  # full chain including gap analysis
  references: []
  feedback: null
```

### L6: Critic Agent
```yaml
agent: critic-agent
input:
  brief: ${brief}
  pre-writing: ${pre_writing}
  upstream: ${merged_final_document}
  references:
    - references/attribution-examples.md
  feedback: null
```

---

## Merge Step

After each agent completes, merge its output into the growing attribution document:

1. **After L1 (kpi-hierarchy):** Document has KPI Hierarchy section
2. **After L2 (initiative-mapper):** Add Initiative → KPI Mapping + Orphan Initiatives sections
3. **After L3 (content-mapper):** Add Content → Initiative Mapping + Orphan Content sections
4. **After L4 (gap-analysis):** Add Gap Analysis section (not in final artifact — used internally)
5. **After L5 (action-agent):** Add Action Items + Previous Review Progress sections
6. **After L6 (critic):** Evaluate merged document → PASS or FAIL

Gap analysis output is consumed by the action-agent but does NOT appear as a standalone section in the final artifact. The action items table IS the user-facing output of the gap analysis.

---

## Critic Gate

- **Max 2 rewrite cycles.** If the critic returns FAIL, re-dispatch only the named agent(s) with feedback.
- On FAIL, the critic names which agent(s) to re-dispatch and provides specific fix instructions.
- Re-dispatched agents receive the **feedback** field with critic instructions. They MUST address every point.
- After rewrite, re-merge and re-run the critic.
- If still FAIL after 2 cycles: deliver with a `## Known Issues` section listing unresolved failures. Do not loop indefinitely.

### Rewrite Routing

| Failure Type | Re-dispatch to |
|-------------|---------------|
| KPI hierarchy incomplete or has vanity metrics | **kpi-hierarchy-agent** |
| Initiative mapping has unjustified confidence or missing entries | **initiative-mapper-agent** |
| Content mapping incomplete or orphans not flagged | **content-mapper-agent** |
| Gaps missed or severity misclassified | **gap-analysis-agent** |
| Actions are observations, missing owners/deadlines, or wrong verbs | **action-agent** |
| Sections contradict each other | Re-merge (orchestrator issue) |

---

## Re-Run Protocol

Review and refresh attribution maps on a regular cadence:

1. **Monthly review cycle:** Set review date ~4 weeks from creation
2. **On re-run:**
   - Read previous `.agents/mkt/attribution.md`
   - Check status of each prior action item (Done / In Progress / Blocked / Dropped)
   - Rename previous file to `attribution.v[N].md`
   - Rebuild map with current state
   - Compare: Did action items move the needle? Which KPIs improved?
3. **Escalation:** If same gaps persist across 2+ reviews, escalate from "Rebalance" to "Kill" or "Create"

**Re-run triggers:** Monthly review cycle (set review date ~4 weeks from creation), after experiments conclude, when KPIs or initiatives change.

### Status Definitions
- **Done** — shipped AND outcome measured. If no outcome data, it's In Progress.
- **In Progress** — started but not complete. Note blocker if any.
- **Parked** — deprioritized deliberately. Note what changed.
- **Dropped** — decided not to pursue. Note explicit reason.

If the same action appears as "Parked" or "Dropped" across 2+ reviews, escalate: either commit to doing it or kill the underlying initiative.

---

## Artifact Template

```markdown
---
skill: attribution
version: 1
date: [today's date]
status: draft
---

# Attribution Map

**Date:** [today]
**Skill:** attribution
**Review date:** [today + 4 weeks]

## KPI Hierarchy

​```
North Star: [metric] — [current] → [target]
├── KPI 1: [metric] — [current] → [target] — Owner: [person]
├── KPI 2: ...
└── KPI 3: ...
​```

## Initiative → KPI Mapping

| Initiative | KPI | Contribution | Confidence |
|------------|-----|-------------|------------|
| ... | ... | ... | ... |

### Orphan Initiatives
| Initiative | Action |
|------------|--------|
| ... | ... |

## Content → Initiative Mapping

| Content | Initiative | Type | Channel |
|---------|-----------|------|---------|
| ... | ... | ... | ... |

### Orphan Content
| Content | Action |
|---------|--------|
| ... | ... |

## Action Items

| # | Gap | Action | Owner | Deadline |
|---|-----|--------|-------|----------|
| 1 | ... | ... | ... | ... |

## Previous Review Progress

| # | Prior Action | Status | Outcome |
|---|-------------|--------|---------|
| 1 | [action from last review] | Done / In Progress / Parked / Dropped | [Result if Done: what metric moved? If not done: blocker or reason] |

Status definitions:
- **Done** — shipped AND outcome measured. If no outcome data, it's In Progress.
- **In Progress** — started but not complete. Note blocker if any.
- **Parked** — deprioritized deliberately. Note what changed.
- **Dropped** — decided not to pursue. Note explicit reason.

If the same action appears as "Parked" or "Dropped" across 2+ reviews, escalate: either commit to doing it or kill the underlying initiative.

> On re-run: rename existing artifact to `attribution.v[N].md` and create new with incremented version.
```

---

## Worked Example

### Pre-writing gathered
```yaml
brief: "Map our current marketing to business outcomes — we have KPIs and initiatives but no attribution"
product_context: B2B SaaS, project management tool
upstream_artifacts:
  targets: targets.md with North Star (Weekly Signups) and 3 KPIs
  solution_design: solution-design.md with 2 initiatives
  imc_plan: imc-plan.md with 3 content pieces
  previous_attribution: null
  experiments: null
route: B (full attribution — first run)
review_date: 2026-04-24
```

### L1: kpi-hierarchy-agent output
```markdown
## KPI Hierarchy

​```
North Star: Weekly Signups — 200 → 350
├── KPI 1: Paid signup rate — 1.2% → 3.0% — Owner: Sarah
├── KPI 2: Homepage bounce rate — 52% → 40% — Owner: James
└── KPI 3: Organic signups — 80/wk → 120/wk — Owner: (unassigned)
​```

## KPI Metadata

| KPI | Type | Funnel Stage | Measurement Window | Current Source |
|-----|------|-------------|-------------------|----------------|
| Weekly Signups | North Star | Acquisition | 7 days | GA4 |
| Paid signup rate | Leading | Acquisition | 14 days | GA4 + Ads |
| Homepage bounce rate | Leading | Activation | 7 days | GA4 |
| Organic signups | Leading | Acquisition | 30 days | GA4 |
```

### L2: initiative-mapper-agent output
```markdown
## Initiative → KPI Mapping

| Initiative | Primary KPI | Secondary KPIs | Contribution | Confidence |
|------------|-------------|----------------|-------------|------------|
| Restore Paid Targeting | Paid signup rate | — | ~55% of target gap | H |
| Restore Social Proof | Homepage bounce rate | — | ~35% of target gap | M |

## Confidence Justification

| Initiative | Confidence | Basis |
|------------|-----------|-------|
| Restore Paid Targeting | H | Previous campaign data: similar targeting achieved 2.8% rate |
| Restore Social Proof | M | Industry benchmark: social proof reduces bounce by 10-15pp. Our gap is 12pp, so ~35% is reasonable but unproven for our audience. |

## Orphan Initiatives
None — both initiatives map to KPIs.

## Experiment Integration
No experiment files found.
```

### L3: content-mapper-agent output
```markdown
## Content → Initiative Mapping

| Content | Initiative | Type | Channel | Tracking Status |
|---------|-----------|------|---------|----------------|
| Status Update Carousel | (none — brand awareness) | Reach | LinkedIn | Partial (no UTMs) |

## Orphan Content

| Content | Source | Current Channel | Recommendation |
|---------|--------|----------------|----------------|
| Status Update Carousel | imc-plan | LinkedIn | **Rebalance:** Add CTA linking to product page, reframe as supporting Paid Targeting initiative |

## Coverage Heatmap

| Initiative | Reach | Trust | Conversion | Total | Assessment |
|-----------|-------|-------|-----------|-------|------------|
| Restore Paid Targeting | 0 | 0 | 0 | 0 | Sparse — no content supporting this initiative |
| Restore Social Proof | 0 | 0 | 0 | 0 | Sparse — no content supporting this initiative |
```

### L4: gap-analysis-agent output (internal — not in final artifact)
```markdown
## Gap Analysis

### Uncovered KPIs
| KPI | Current Coverage | Severity |
|-----|-----------------|----------|
| Organic signups | 0 initiatives, no owner | Critical |

### Low-Confidence Initiatives
| Initiative | KPI | Confidence | Risk |
|-----------|-----|-----------|------|
| Restore Social Proof | Homepage bounce rate | M | If this fails, homepage bounce has no backup initiative |

### Funnel Imbalances
| Initiative | Reach | Trust | Conversion | Imbalance |
|-----------|-------|-------|-----------|-----------|
| Restore Paid Targeting | 0 | 0 | 0 | No content at all |
| Restore Social Proof | 0 | 0 | 0 | No content at all |

### Tracking Gaps
| Content/Initiative | Gap | Impact |
|-------------------|-----|--------|
| Status Update Carousel | No UTM parameters | Cannot attribute LinkedIn traffic to content |

### Ownership Gaps
| Item | Type | Gap |
|------|------|-----|
| Organic signups | KPI | No owner assigned |

## Severity Summary
| Severity | Count | Description |
|----------|-------|-------------|
| Critical | 2 | KPI 3 uncovered + KPI 3 no owner |
| High | 2 | Both initiatives have zero content support |
| Medium | 1 | Carousel has no UTMs |
```

### L5: action-agent output
```markdown
## Action Items

| # | Gap | Severity | Action | Owner | Deadline |
|---|-----|----------|--------|-------|----------|
| 1 | KPI 3 (organic signups) has 0 initiatives | Critical | **Create:** Run `problem-analysis` on organic traffic stagnation | James | 2026-04-03 |
| 2 | KPI 3 has no owner | Critical | **Assign:** Name an owner for organic signups KPI | Marketing lead | Now |
| 3 | Restore Paid Targeting has 0 content | High | **Create:** Run `content-create` for paid landing page and ad copy | Sarah | 2026-04-10 |
| 4 | Restore Social Proof has 0 content | High | **Create:** Run `content-create` for testimonial/case study content | James | 2026-04-10 |
| 5 | Status Update Carousel orphaned | Medium | **Rebalance:** Add product CTA to carousel, track as Paid Targeting support | Content lead | 2026-04-03 |

## Action Rationale

| # | Action | Why This Action | Why This Priority | Skill to Run |
|---|--------|----------------|------------------|-------------|
| 1 | Create initiative for organic | KPI with 0 coverage — business goal has no path | Critical — completely unaddressed goal | `problem-analysis` |
| 2 | Assign KPI owner | Metrics without owners don't improve | Critical — blocks progress | manual |
| 3 | Create content for Paid Targeting | Initiative has no content support | High — initiative is funded but unsupported | `content-create` |
| 4 | Create content for Social Proof | Initiative has no content support | High — initiative is funded but unsupported | `content-create` |
| 5 | Rebalance carousel | Orphan content is wasted effort | Medium — easy redirect | manual |

## Previous Review Progress
First run — no prior actions to review.
```

### L6: critic-agent returns PASS
All quality gates satisfied. Merged into final artifact.

---

## Anti-Patterns

**Vanity metrics as KPIs** — Tracking impressions or followers as primary KPIs. These metrics feel good but don't connect to business outcomes. KPIs must be metrics that, if improved, move the North Star.
INSTEAD: Use vanity metrics as supporting metrics under a leading KPI, not as KPIs themselves.

**Mapping everything to revenue** — Forcing every content piece to show direct revenue impact ignores the awareness and trust stages of the funnel. Map content to its appropriate funnel stage metric, not just revenue.
INSTEAD: Map content to the funnel stage it serves (Reach → Trust → Conversion). Attribution traces the chain, not a shortcut.

**Ignoring time lag** — Expecting attribution results within days for strategies that take weeks or months to show impact. Set appropriate measurement windows — brand content may take 8-12 weeks to influence pipeline.
INSTEAD: Set measurement windows per content type using `references/attribution-models.md`. Review after the window closes, not before.

**Orphan content without initiative links** — Content that exists because "we should post something" rather than supporting a specific initiative. Every piece should trace to an initiative and KPI — orphan content is wasted effort.
INSTEAD: Flag orphans explicitly with Assign / Repurpose / Sunset recommendations. Zero orphan tolerance.

**Static attribution maps** — Building the map once and never updating it. Attribution maps decay as initiatives ship, KPIs shift, and new content is produced. Set a review cadence (monthly minimum).
INSTEAD: Set review date 4 weeks out. Use Route C (re-run) to track action progress and refresh the map.

**Attribution without tracking infrastructure** — Mapping content to KPIs on paper while having no event tracking, UTM parameters, or analytics in place. The map becomes theoretical without implementation. See [references/tracking-guide.md](references/tracking-guide.md) for minimum viable tracking.
INSTEAD: content-mapper-agent flags tracking status for every piece. Untracked content generates a **Create** action item for tracking implementation.

**Wrong attribution model for the business** — Using last-touch attribution for a B2B product with 90-day sales cycles attributes everything to the final touchpoint and misses the content that created awareness. Match model to buying cycle length. See [references/attribution-models.md](references/attribution-models.md).
INSTEAD: kpi-hierarchy-agent sets measurement windows per KPI using the attribution-models reference.

**Metrics without owners** — Every KPI and initiative must have a named person (not "the team"). Unowned metrics don't get improved — they get reported on and shrugged at.
INSTEAD: kpi-hierarchy-agent flags unassigned owners. gap-analysis-agent classifies them as ownership gaps. action-agent generates **Assign** actions.

---

## Chain Position
Previous: `content-create` | Next: Monthly review (re-run this skill)
**Re-run triggers:** Monthly review cycle (set review date ~4 weeks from creation), after experiments conclude, when KPIs or initiatives change.

## References

- [references/attribution-examples.md](references/attribution-examples.md) — Worked examples across business types
- [references/attribution-models.md](references/attribution-models.md) — Model selection guide by business type and buying cycle
- [references/tracking-guide.md](references/tracking-guide.md) — Event naming conventions, UTM standards, minimum viable tracking stack
