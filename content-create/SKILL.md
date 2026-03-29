---
name: content-create
description: "Drafts marketing content assets — social posts, ads, emails, newsletters, blog posts, case studies, video scripts, and launch announcements in platform-native formats. Produces `.agents/mkt/content/[slug].md`. Not for editing existing text (use humanize) or persuasive headlines and CTAs (use copywriting)."
argument-hint: "[angle or topic]"
license: MIT
metadata:
  author: hungv47
  version: "4.0.0"
routing:
  intent-tags:
    - content-asset
    - social-post
    - email
    - blog
    - video-script
    - carousel
  position: pipeline
  produces:
    - mkt/content/[slug].md
  consumes:
    - product-context.md
    - mkt/icp-research.md
    - mkt/imc-plan.md
  requires: []
  defers-to:
    - skill: copywriting
      when: "need craft-quality headlines/CTAs, not full content assets"
    - skill: humanize
      when: "editing existing AI-sounding text"
  parallel-with: []
  interactive: false
  estimated-complexity: heavy
---

# Content Creation — Orchestrator

*Communication — Step 3 of 4. Coordinates specialized agents to turn IMC angles into production-ready content assets with A/B variants.*

**Core Question:** "Would the target persona actually stop scrolling for this?"

## Critical Gates — Read First

- **Do NOT write content without format specs.** Platform constraints (character limits, dimensions, native patterns) must be resolved FIRST. Hook/body/CTA agents cannot write without them.
- **Do NOT dispatch all agents for a single social post.** Route A exists for quick assets. Only Route B uses the full agent stack.
- **Do NOT write outlines.** Every agent must produce complete copy — every word, slide, timestamp. "Discuss benefits" is not a deliverable.
- **Stale IMC data (>30 days) produces misaligned content.** Recommend re-running `imc-plan` before proceeding if artifact dates are old.

## Philosophy

This skill focuses on content assets — choosing the right format, structuring for the platform, and producing deliverables. For copy craft (variation workflows, evaluation rubrics, annotation), use `copywriting`.

## Inputs Required
- Angle + channel from `.agents/mkt/imc-plan.md` (or user-provided)

## Output
- `.agents/mkt/content/[slug].md`

## Quality Gate
Before delivering, the **critic agent** verifies:
- [ ] Hook ≤8 words or within platform character limit
- [ ] Key lines pass 3Q test (Visual, Falsifiable, Uniquely ours)
- [ ] CTA follows formula: [action verb] + [what they get]
- [ ] A/B variant changes exactly ONE element with testable hypothesis
- [ ] Complete copy — every word written, no outlines or placeholders
- [ ] Format compliance — all platform specs met
- [ ] VoC language present — buyer words, not brand words

## Chain Position
Previous: `imc-plan` | Next: `attribution`
**Re-run triggers:** When IMC plan angles are updated, when targeting a new platform, or when A/B test results suggest a new direction.

### Skill Deference
- **Need craft-quality headlines or page copy?** → Run `copywriting` for variation workflow and rubric.
- **Page exists, problem is conversion?** → Run `lp-optimization` first.
- **Content reads as AI-generated?** → Run `humanize` after.
- **Optimizing for search/AI citations?** → Coordinate with `seo`.

---

## Agent Manifest

| Agent | Layer | File | Focus |
|-------|-------|------|-------|
| Format Agent | 1 (parallel) | `agents/format-agent.md` | Platform specs, dimensions, native patterns |
| VoC Extraction Agent | 1 (parallel) | `agents/voc-extraction-agent.md` | Buyer language from ICP research |
| Hook Agent | 1.5 (after format) | `agents/hook-agent.md` | Opening line adapted to format constraints |
| Body Agent | 1.5 (after format) | `agents/body-agent.md` | Complete content between hook and CTA |
| CTA Agent | 1.5 (after format) | `agents/cta-agent.md` | Platform-native call to action |
| Platform Compliance Agent | 2 (sequential) | `agents/platform-compliance-agent.md` | Technical spec verification |
| A/B Variant Agent | 2 (sequential) | `agents/ab-variant-agent.md` | One testable alternative |
| Critic Agent | 2 (final) | `agents/critic-agent.md` | Quality scoring, PASS/FAIL |

### Shared References (read by multiple agents)
- `references/platform-specs.md` — Platform dimensions, character limits, native patterns
- `references/examples.md` — Complete worked examples with full copy
- `references/repurposing-cascade.md` — Hero → derivative content workflow

---

## Routing Logic

### Route A: Single Asset (Quick)
**When:** One social post, one email, or one ad — not a multi-asset campaign.

```
1. Pre-dispatch: Gather context (Step 0)
2. LAYER 1 — Dispatch IN PARALLEL:
   - format-agent (determines platform constraints)
   - voc-extraction-agent (pulls buyer language)
3. LAYER 1.5 — Dispatch IN PARALLEL (after format-agent returns):
   - hook-agent (receives format specs)
   - cta-agent (receives format specs)
4. Orchestrator writes body inline (single asset doesn't need full body-agent)
5. Dispatch: platform-compliance-agent
6. Dispatch: critic-agent
7. If FAIL → re-dispatch named agent(s) with feedback (max 2 cycles)
8. Deliver artifact
```

### Route B: Full Asset (Campaign or Complex)
**When:** Multi-slide carousel, video script, email sequence, or multi-asset campaign.

```
1. Pre-dispatch: Gather context (Step 0)
2. LAYER 1 — Dispatch IN PARALLEL:
   - format-agent
   - voc-extraction-agent
3. LAYER 1.5 — Dispatch IN PARALLEL (after format-agent returns):
   - hook-agent (receives format specs + VoC)
   - body-agent (receives format specs + VoC)
   - cta-agent (receives format specs + VoC)
4. MERGE: Assemble hook + body + CTA into unified content asset
5. LAYER 2 — Dispatch SEQUENTIALLY:
   - platform-compliance-agent (receives merged asset)
   - ab-variant-agent (receives compliance-checked asset)
6. Dispatch: critic-agent (receives final asset + variant)
7. If FAIL → re-dispatch named agent(s) with feedback (max 2 cycles)
8. Deliver artifact
```

### Route C: Called by Another Skill
**When:** Invoked by `imc-plan` or `attribution` for inline content work.

```
1. Read context from calling skill's artifacts
2. Dispatch relevant agents based on caller needs
3. Dispatch: critic-agent
4. Return content to calling skill
```

---

## Step 0: Pre-Dispatch Context Gathering

### Product Context Check
Check for `.agents/product-context.md` and `.agents/mkt/imc-plan.md`. If `date` fields are older than 30 days, **warn the user** and recommend re-running upstream skills.

### Required Artifacts
| Artifact | Source | If Missing |
|----------|--------|------------|
| `imc-plan.md` | imc-plan | **INTERVIEW.** Gather: angle, channel, placement, awareness stage. |

### Optional Artifacts
| Artifact | Source | Benefit |
|----------|--------|---------|
| `icp-research.md` | icp-research | VoC language for copy |
| `product-context.md` | icp-research | Product details for accuracy |

### Context to Pass to All Agents
1. **Angle:** from IMC plan or user brief
2. **Channel + placement:** target platform and format
3. **Awareness stage:** determines hook approach and CTA commitment
4. **VoC quotes:** from voc-extraction-agent (available after Layer 1)

---

## Dispatch Protocol

### How to spawn a sub-agent

1. **Read** the agent instruction file — include its FULL content in the Agent prompt
2. **Append** the context (angle, channel, awareness stage, VoC) after the instructions
3. **Resolve file paths to absolute**: replace relative paths with absolute paths rooted at this skill's directory
4. **Pass upstream artifacts by content**: the orchestrator reads `.agents/` files FIRST, then includes relevant excerpts in context. Sub-agents should NOT read artifact files directly.
5. If **feedback** exists (from critic FAIL), append with header "## Critic Feedback — Address Every Point"

### Single-agent fallback

If multi-agent dispatch is unavailable, execute each agent's instructions sequentially in-context:
- Layer 1: resolve format specs, extract VoC
- Layer 1.5: write hook, body, CTA within format constraints
- Layer 2: check compliance, create variant, evaluate with critic rubric

---

## Layer 1: Parallel Foundation

Spawn **IN PARALLEL**:

| Agent | Instruction File | Pass These Inputs | Reference Files |
|-------|-----------------|-------------------|-----------------|
| Format Agent | `agents/format-agent.md` | brief (platform + format type) | `references/platform-specs.md` |
| VoC Extraction Agent | `agents/voc-extraction-agent.md` | brief (topic + persona) | — |

Wait for both to complete. Their outputs become inputs for Layer 1.5.

---

## Layer 1.5: Parallel Content Writers

After format-agent and voc-extraction-agent return, spawn **IN PARALLEL**:

| Agent | Instruction File | Pass These Inputs | Reference Files |
|-------|-----------------|-------------------|-----------------|
| Hook Agent | `agents/hook-agent.md` | brief + format specs + VoC quotes | — |
| Body Agent | `agents/body-agent.md` | brief + format specs + VoC quotes | `references/examples.md`, `references/repurposing-cascade.md` |
| CTA Agent | `agents/cta-agent.md` | brief + format specs + awareness stage | — |

---

## Merge Step

Assemble Layer 1.5 outputs into the artifact template:

| Section | Owner Agent |
|---------|-----------|
| Hook | Hook Agent |
| Body (all slides/tweets/sections) | Body Agent |
| CTA (text + destination + tracking) | CTA Agent |

**Assembly rule:** Hook first, then body content, then CTA at the end. CTA placement follows the format-agent's guidance (last slide, last tweet, below fold, etc.).

---

## Layer 2: Sequential Refiners

Dispatch **ONE AT A TIME, IN ORDER**:

| Step | Agent | Instruction File | Receives |
|------|-------|-----------------|----------|
| 1 | Platform Compliance Agent | `agents/platform-compliance-agent.md` | Merged content asset |
| 2 | A/B Variant Agent | `agents/ab-variant-agent.md` | Compliance-checked asset |
| 3 | Critic Agent | `agents/critic-agent.md` | Final asset + variant |

---

## Critic Gate

- **PASS:** Deliver the annotated artifact.
- **FAIL:** Re-dispatch named agent(s) with critic feedback. Max 2 rewrite cycles. After 2 failures, deliver with critic annotations and flag to user.

---

## Artifact Template

```markdown
---
skill: content-create
version: 1
date: [today's date]
status: draft
---

# Content: [Title]

**Date:** [today]
**Skill:** content-create
**Angle:** [from IMC plan]
**Channel:** [platform + placement]
**Stage:** [awareness level]

## Hook

[Exact hook text]

**3Q Test:** Visual: [Y/N] | Falsifiable: [Y/N] | Uniquely ours: [Y/N]
**Annotations:** [Rule, cut alternative, rubric score]

## Body

[Complete copy — every word, slide, or timestamp]

## CTA

- **Text:** [exact CTA copy]
- **Destination:** [URL or action]
- **Tracking:** [UTM parameters]

## A/B Variant

| Element | A (Main) | B (Variant) |
|---------|----------|-------------|
| [Hook/CTA/Format] | [Original] | [One change] |

**Test hypothesis:** If B wins, it means [specific learning].

## Asset Checklist

- [ ] [Asset with specs]
- [ ] [Brand assets needed]

> On re-run: rename existing artifact to `[slug].v[N].md` and create new with incremented version.
```

---

## Worked Example — LinkedIn Carousel (Route B)

**Brief:** LinkedIn carousel about "12 hrs/week lost to status theater"
**Audience:** Engineering managers, Problem Aware
**Channel:** LinkedIn carousel

### Step 0: Pre-Dispatch
Angle from imc-plan: "Engineering teams lose 12 hrs/week to status updates nobody reads"
Awareness: Problem Aware. Channel: LinkedIn carousel.

### Layer 1: Parallel Foundation
→ **Format agent** returns: LinkedIn carousel, 1080x1350px, 5-10 slides, ≤50 words/slide, PDF format
→ **VoC extraction agent** returns: 5 pain quotes from ICP research, buyer language "status theater," "meeting tax"

### Layer 1.5: Parallel Content Writers (receive format specs + VoC)
→ **Hook agent** returns: "Your team loses 12 hours a week to status updates nobody reads." (V:Y F:Y U:Y, Data hook)
→ **Body agent** returns: 6 slides (pie chart breakdown, 4 pain slides, fix slide)
→ **CTA agent** returns: "See how teams ship without status theater →" (link in comments)

### Merge
Assembled into 8-slide carousel: Hook slide → 6 body slides → CTA slide

### Layer 2: Sequential
→ **Platform compliance** → PASS (all slides within limits, correct dimensions)
→ **A/B variant** → Hook variant B: "I stopped doing standups. Here's what happened." (tests story vs. data)
→ **Critic** → PASS. All dimensions ≥3.5. Delivered.

---

## Anti-Patterns

**Burying the lead** — Starting with context instead of the hook. INSTEAD: The first thing the reader sees IS the hook. No preamble.

**Platform-generic content** — Same text for LinkedIn and TikTok. INSTEAD: Each platform gets its own format spec from format-agent. Native patterns outperform imported content.

**Weak CTAs** — "Learn More" or "Click Here." INSTEAD: [action verb] + [what they get]. "See how teams ship without standups →"

**A/B testing multiple variables** — Changing hook + CTA + format = untestable. INSTEAD: ONE element per variant with a stated hypothesis.

**Writing outlines** — "Slide 3: Talk about the pain point." INSTEAD: Write every word. "4 hrs — writing updates for managers who skim them."

---

## Agent Files

### Sub-Agent Instructions (agents/)
- [agents/format-agent.md](agents/format-agent.md) — Platform specs, dimensions, native patterns
- [agents/voc-extraction-agent.md](agents/voc-extraction-agent.md) — Buyer language from ICP research
- [agents/hook-agent.md](agents/hook-agent.md) — Opening line adapted to format
- [agents/body-agent.md](agents/body-agent.md) — Complete body content
- [agents/cta-agent.md](agents/cta-agent.md) — Platform-native CTA
- [agents/platform-compliance-agent.md](agents/platform-compliance-agent.md) — Technical spec verification
- [agents/ab-variant-agent.md](agents/ab-variant-agent.md) — One testable alternative
- [agents/critic-agent.md](agents/critic-agent.md) — Quality scoring, PASS/FAIL

### Shared References (references/)
- [references/platform-specs.md](references/platform-specs.md) — Platform dimensions, character limits, native patterns
- [references/examples.md](references/examples.md) — Complete worked examples with full copy
- [references/repurposing-cascade.md](references/repurposing-cascade.md) — Hero → derivative content workflow
