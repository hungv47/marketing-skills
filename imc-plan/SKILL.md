---
name: imc-plan
description: "Create an IMC plan, develop integrated marketing, build a campaign strategy, plan a product launch — IMC, integrated marketing, multi-channel marketing, campaign planning, content pillars, angle development, channel strategy, launch timeline."
license: MIT
metadata:
  author: hungv47
  version: "7.1.0"
---

# Integrated Marketing Communication (IMC)

*Communicate Track — Step 2 of 4. Turns audience insights into pillars, tested angles, channel assignments, and a phased timeline.*

**Core Question:** "How do all these channels work together?"

## Inputs Required
- ICP research from `.agents/mkt/icp-research.md`

## Output
- `.agents/mkt/imc-plan.md`

## Quality Gate
Before delivering, verify:
- [ ] Every pillar traces to a specific pain or aspiration from ICP research (with a quotable VoC source)
- [ ] Every angle passes ALL three questions: visual? falsifiable? uniquely yours?
- [ ] Every channel assignment cites the habitat map (not guessed)
- [ ] Timeline has specific dates, not just "Phase 1"

## Chain Position
Previous: `icp-research` | Next: `content-create`

---

## Before Starting

### Step 0: Product Context
Check for `.agents/mkt/product-context.md`. If available, read for product positioning context.

### Required Artifacts
| Artifact | Source | If Missing |
|----------|--------|------------|
| `icp-research.md` | icp-research | **STOP.** "Run icp-research first — guessed audiences produce weak IMC plans." |

### Optional Artifacts
| Artifact | Source | Benefit |
|----------|--------|---------|
| `product-context.md` | icp-research | Product positioning context |
| `solution-design.md` | solution-design (from hungv47/strategy-skills) | Aligns content pillars with solution priorities |

Read `.agents/mkt/icp-research.md`. Import personas, pains, habitat maps, VoC quotes.

---

## Step 1: Foundation

**Goals:** Define the objective. (Awareness / Leads / Sales / Retention) Timeline? Situation? (Launch / Ongoing / Seasonal)

**Core Message:** If the audience remembers one thing, what is it?

**Awareness Levels:** Where is the audience now?

| Stage | They think... | Your job |
|-------|---------------|----------|
| Unaware | "No problem" | Surface it |
| Problem Aware | "Problem, no fix" | Demonstrate understanding |
| Solution Aware | "Fixes exist, which?" | Differentiate |
| Product Aware | "I know this, not sure" | Overcome objections |
| Most Aware | "Ready" | Clear CTA |

---

## Step 2: Pillars (from ICP pains)

Extract 3-5 pillars from ICP research:

| Source | Pillar Type | % Content |
|--------|------------|-----------|
| Top Pain Points | Problem | 25-30% |
| Aspirational Identity | Transformation | 30-35% |
| Current Workarounds | Alternative | 20-25% |
| Decision Criteria | Trust | 15-20% |

Trace each pillar to a VoC quote or ICP finding — pillars without audience evidence produce content that sounds generic.

---

## Step 3: Angles (3 per pillar, tested)

For each pillar, generate 3 angles combining: hook type + awareness stage + emotional trigger.

### The 3-Question Test

Every angle must pass ALL three:

1. **Visual?** Picture it — does an image form? ("12 hours lost to status updates" = yes. "Improve productivity" = no.)
2. **Falsifiable?** Can it be proven true or false? ("31 hrs/month in unproductive meetings" = yes. "We help teams succeed" = no.)
3. **Uniquely yours?** Could a competitor use this? ("The dating app designed to be deleted" = only Hinge. "The best project tool" = anyone.)

3 yeses → keep. Any no → rewrite or cut — angles that fail even one question underperform in production.

Also screen for AI copy slop — if the angle reads like generic SaaS marketing ("Unlock the power of...", "Revolutionize your...", "In today's fast-paced world..."), it fails Uniquely Yours regardless of the product name. Slop enters the pipeline here; catching it prevents wasted production effort in `content-create`.

See [references/3d-angle-framework.md](references/3d-angle-framework.md) for hook types and generation framework.

### Angle Prioritization (when angles exceed capacity)

When multiple angles pass the 3-Question Test, score them to decide production order:

| Factor | Weight | Score 1-5 |
|--------|--------|-----------|
| Audience Pain Intensity | 40% | How acute is the underlying pain? (from ICP research) |
| 3-Question Score | 30% | How strongly does it pass visual + falsifiable + unique? |
| Channel-Content Fit | 20% | How well does the angle suit available channels? |
| Production Effort | 10% | How easy to produce? (lower effort = higher score) |

**Weighted score** = (Pain × 0.4) + (3Q × 0.3) + (Fit × 0.2) + (Effort × 0.1)

Produce highest-scoring angles first. This prevents the common trap of producing easy content that doesn't address the sharpest audience pains.

### Content Classification

Tag each surviving angle as **Searchable** (captures existing demand via keywords), **Shareable** (creates demand via novelty/emotion), or **Both**. See [references/channel-strategy.md](references/channel-strategy.md) for classification details and channel routing rules.

---

## Step 4: Channels (from habitat map)

Pull channel assignments from the persona habitat maps in ICP research — guessing channels wastes budget on platforms where the audience isn't active.

Assign one clear angle per channel:

| Platform | Specific Channel | Angle | Why (habitat evidence) |
|----------|-----------------|-------|----------------------|
| [Platform] | [Specific group/account] | "[Angle text]" | [Density + engagement from ICP] |

See [references/channel-strategy.md](references/channel-strategy.md) for channel hierarchy.

---

## Step 5: Phase Timeline

| Phase | Dates | Focus | Content Mix |
|-------|-------|-------|-------------|
| Pre-launch | [start–end] | Build anticipation, educate on problem | 70% Problem, 30% Solution |
| Launch | [start–end] | Drive action, prove value | 30% Problem, 40% Proof, 30% CTA |
| Sustain | [start–ongoing] | Maintain presence, deepen trust | 40% Solution, 30% Proof, 30% Brand |

---

## Artifact Template

```markdown
---
skill: imc-plan
version: 1
date: [today's date]
status: draft
---

# IMC Plan

**Date:** [today]
**Skill:** imc-plan
**Core Message:** [one sentence]
**Audience:** [primary persona from ICP]

## Pillars

| # | Pillar | Type | Source (ICP) | % Content |
|---|--------|------|-------------|-----------|
| 1 | [Name] | Problem | VoC: "[quote]" | 30% |
| 2 | [Name] | Transformation | Aspiration: [from ICP] | 30% |
| 3 | [Name] | Trust | Criteria: [from ICP] | 20% |
| 4 | [Name] | Brand | — | 20% |

## Angle Bank

| Pillar | Angle | Hook Type | Stage | 3Q: V/F/U | Priority Score | Type |
|--------|-------|-----------|-------|-----------|---------------|------|
| 1 | "[angle text]" | Data | Problem Aware | Y/Y/Y | [X.X] | Searchable/Shareable/Both |
| 1 | "[angle text]" | Contrarian | Solution Aware | Y/Y/Y | [X.X] | Searchable/Shareable/Both |
| 1 | "[angle text]" | Story | Unaware | Y/Y/Y | [X.X] | Searchable/Shareable/Both |
| 2 | ... | ... | ... | ... | ... | ... |

## Channel Assignments

| Platform | Channel | Angle | Habitat Evidence |
|----------|---------|-------|-----------------|
| Reddit | r/[subreddit] | "[angle]" | Density: H, Engagement: Lurker→Engager |
| LinkedIn | [group/feed] | "[angle]" | Density: M, Engagement: Creator |

## Timeline

| Phase | Dates | Focus | Key Actions |
|-------|-------|-------|-------------|
| Pre-launch | [date–date] | Problem awareness | [Specific actions] |
| Launch | [date–date] | Drive action | [Specific actions] |
| Sustain | [date–ongoing] | Trust + brand | [Specific actions] |

## Next Step

Run `content-create` to turn angles into production-ready content.

> On re-run: rename existing artifact to `imc-plan.v[N].md` and create new with incremented version.
```

---

## Worked Example

**User:** "Create an IMC plan for our project management tool launch."

**Artifact saved to `.agents/mkt/imc-plan.md`:**

```markdown
# IMC Plan

**Date:** 2026-03-17
**Skill:** imc-plan
**Core Message:** Engineering teams deserve visibility without status theater.
**Audience:** Overwhelmed EM (from ICP)

## Pillars

| # | Pillar | Type | Source (ICP) | % Content |
|---|--------|------|-------------|-----------|
| 1 | Status update waste | Problem | VoC: "I spend more time telling people what I did than doing it" | 30% |
| 2 | Async-first leadership | Transformation | Aspiration: "Ship without meetings" | 30% |
| 3 | Real teams, real results | Trust | Switching reasons from G2 reviews | 20% |
| 4 | Engineering culture | Brand | — | 20% |

## Angle Bank

| Pillar | Angle | Hook Type | Stage | 3Q: V/F/U |
|--------|-------|-----------|-------|-----------|
| 1 | "Your team loses 12 hrs/week to status updates nobody reads" | Data | Problem Aware | Y/Y/Y |
| 1 | "I stopped doing standups. Output doubled." | Story | Unaware | Y/Y/Y |
| 2 | "How to ship 2x faster without adding headcount" | How-to | Solution Aware | Y/Y/Y |

## Channel Assignments

| Platform | Channel | Angle | Habitat Evidence |
|----------|---------|-------|-----------------|
| Reddit | r/ExperiencedDevs | "Status update waste" | Density: H, Engagement: Engager |
| LinkedIn | #engineeringmanagement | "Async-first leadership" | Density: M, Engagement: Creator |

## Next Step

Run `content-create` to turn angles into production-ready content.
```

---

## Anti-Patterns

**Channel-first planning** — Choosing channels before defining pillars and angles produces content that fits the platform but misses the audience. Always start from ICP pains → pillars → angles → then assign channels.

**Identical message across channels** — Copy-pasting the same angle to every platform wastes the channel's native strengths. Each channel assignment should use an angle suited to that platform's engagement type.

**No pillar-to-audience connection** — Pillars that sound strategic but can't trace back to a specific VoC quote or ICP finding. Untethered pillars produce content that sounds generic and underperforms.

**Timeline without dependencies** — Listing phases without specifying what must complete before the next phase begins. Pre-launch content must exist before launch — if it doesn't, the timeline is fiction.

**Too many pillars** — More than 5 pillars dilutes content quality and makes the editorial calendar unmanageable. Force-rank by audience pain intensity and cut to 3-5.

---

## References

- [references/3d-angle-framework.md](references/3d-angle-framework.md) — Hook types × awareness × triggers
- [references/channel-strategy.md](references/channel-strategy.md) — Channel types and fit matrices
- [references/examples.md](references/examples.md) — Worked examples across B2B SaaS, D2C, Creator, Crypto
