---
name: product-description
description: "This skill should be invoked when the user needs a comprehensive product intelligence document — the single source of truth for what the product is, how it works, why it matters, and how it compares. Triggers include 'describe our product', 'product overview', 'product description', 'what does our product do', 'product intelligence', 'product analysis', 'competitive analysis', 'how do we compare', 'value proposition', 'what makes us different', 'product positioning', 'product brief', or when downstream skills need deeper product understanding than product-context.md provides. Not for audience/persona research (use icp-research), campaign planning (use imc-plan), writing marketing copy (use copywriting), or brand identity (use brand-system)."
license: MIT
metadata:
  author: hungv47
  version: "1.0.0"
---

# Product Description & Intelligence

*Foundational skill — produces the comprehensive product intelligence document that feeds all downstream communication skills.*

**Core Question:** "What exactly is this product, how does it work, why does it matter, and how does it compare?"

## Philosophy

Every downstream skill — copywriting, IMC planning, content creation, landing page optimization, brand systems — needs deep product understanding. The lightweight 8-field `product-context.md` gives them a starting point, but teams describe the product differently every time, and shallow product knowledge produces shallow marketing. This skill produces a comprehensive, source-verified product intelligence document so every downstream skill starts with the same rich foundation.

Research first, interview second. Scan every available public source before asking the user a single question. The user should confirm and fill gaps, not dictate from scratch — this surfaces information the team has forgotten or takes for granted.

## Inputs Required
- Product name or URL (minimum starting point)
- Willingness to confirm findings and fill gaps in Phase 2

## Output
- **Primary:** `.agents/mkt/product-description.md` (comprehensive product intelligence)
- **Secondary:** Updates `.agents/product-context.md` (lightweight 8-field cross-stack file) with any improved data

## Quality Gate
Before delivering, verify:
- [ ] Every product claim sourced (website, docs, review, or user-confirmed) — no assumptions
- [ ] Competitors named with specific differentiators (not "better than alternatives")
- [ ] Value props pass the Swap Test (replace product name with competitor — if still works, rewrite)
- [ ] Pricing reflects current public info, confirmed by user
- [ ] ≥3 external sources consulted
- [ ] Gaps/unknowns explicitly flagged with `[UNKNOWN]`, not filled with guesses
- [ ] `product-context.md` updated with improved data
- [ ] Confidence level marked per section (HIGH / MEDIUM / LOW)

## Chain Position
Previous: none (entry point, foundational) | Next: all skills reading `product-context.md` — `icp-research`, `imc-plan`, `copywriting`, `content-create`, `lp-optimization`, `brand-system`, `seo`, etc.

**Foundational role:** Sits alongside `icp-research` as a "Step 0" skill. While `icp-research` answers "who are we talking to?", this skill answers "what are we talking about?" Together they provide the complete foundation for all downstream skills.
**Re-run triggers:** Major product update, new feature launch, rebrand, entering new market, quarterly for active products.

### Skill Deference
- **Need audience personas and pain points?** → Use `icp-research` — this skill focuses on the product, not the audience.
- **Need marketing copy written?** → Use `copywriting` — this skill produces raw intelligence, not polished copy.
- **Need a brand identity system?** → Use `brand-system` — this skill captures existing voice, not designing a new one.
- **Need competitive strategy?** → Use `solution-design` (from strategy-skills) — this skill maps competitors, not strategic responses.

---

## Before Starting

### Step 0: Check Existing Artifacts
Check for `.agents/product-context.md` and `.agents/mkt/product-description.md`. If the product description already exists, check its `date` field — if older than 90 days, recommend a full re-run. If recent, ask whether the user wants a targeted update or full re-run.

### Required Artifacts
None — this is an entry point skill. Only needs a product name or URL.

### Optional Artifacts
| Artifact | Source | Benefit |
|----------|--------|---------|
| `product-context.md` | icp-research | Existing product snapshot to build on |
| `icp-research.md` | icp-research | Audience context enriches positioning analysis |
| `problem-analysis.md` | problem-analysis | Problem context sharpens value prop extraction |

---

## Phase 1: Automated Research Scan

Before asking the user a single question, scan all available public sources. Use research tools in priority order:

**Research tool priority:**
1. **Exa MCP** or **Perplexity MCP** (if installed) — best for semantic search across product reviews, comparison articles, and press coverage.
2. **Firecrawl** or **Defuddle** (if installed) — for scraping specific pages (product landing pages, pricing pages, documentation).
3. **WebSearch** — supporting role for broad discovery and gap-filling. Always available as fallback.
4. **User interview fallback** — Phase 2 handles this.

### Source Scan Matrix

For each source type, extract specific information. Skip sources that don't exist (not every product has app store listings or G2 reviews).

| Source | Search Pattern | What to Extract |
|--------|---------------|----------------|
| **Product website / landing page** | `[product name] site:[domain]` | Value prop, features, pricing, CTAs, social proof, messaging hierarchy, brand voice |
| **Documentation / README** | `[product name] documentation OR docs OR readme` | Technical capabilities, integrations, API, limitations, architecture |
| **App store listings** | `site:apps.apple.com OR site:play.google.com "[product name]"` | Category, ratings, review count, update frequency, screenshots |
| **G2 / Capterra reviews** | `site:g2.com OR site:capterra.com "[product name]"` | Strengths, weaknesses, use cases, competitor comparisons, satisfaction scores |
| **Social media profiles** | `[product name] site:twitter.com OR site:linkedin.com` | Brand voice in practice, community size, engagement patterns |
| **Competitor comparison pages** | `[product name] vs OR alternative OR compared to` | How they position against alternatives, claimed differentiators |
| **Press / media coverage** | `[product name] launch OR funding OR raised OR interview` | Narrative, founding story, funding, team, milestones |
| **Pricing page** | `[product name] pricing` | Plans, pricing model, free tier, enterprise options |

### Research Notes Format

As you scan, record findings in this structure (internal working notes — not part of final artifact):

```
### [Source: URL or description]
**Confidence:** HIGH / MEDIUM / LOW
**Key findings:**
- [finding 1]
- [finding 2]
**Quotes/evidence:**
- "[exact text from source]"
**Conflicts with other sources:**
- [note any contradictions]
```

See [references/product-analysis-framework.md](references/product-analysis-framework.md) for source reliability hierarchy and conflict resolution.

---

## Phase 2: Gap Interview

Present a structured summary of research findings to the user, organized by what you found and what's missing. This is NOT a blank questionnaire — it's a confirmation-and-gap-fill conversation.

### Interview Structure

**Part A — Confirm or Correct** (present what you found):
> "Based on my research, here's what I've gathered about [product]. Please confirm, correct, or add nuance:"
>
> 1. **Core function:** [your finding]
> 2. **Primary value prop:** [your finding]
> 3. **Key differentiators:** [your findings]
> 4. **Pricing:** [your finding]
> 5. **Main competitors:** [your findings]

**Part B — Fill Gaps** (ask only what research couldn't answer):
- Product stage (concept/MVP/beta/launch/growth/mature)?
- Internal roadmap items that affect positioning?
- Unpublished features or upcoming changes?
- Known limitations you're transparent about?
- Onboarding flow details (time-to-value)?
- Referral, affiliate, or partner programs?
- Security/compliance certifications?
- Anything the public sources get wrong?

**Part C — Positioning Intent** (strategic context):
- How do YOU describe the product in one sentence?
- What competitor do prospects most often compare you to?
- What's the #1 reason customers choose you over alternatives?
- What's the #1 reason prospects DON'T choose you?

Keep the interview focused. If research was thorough, Part B should be short.

---

## Phase 3: Synthesize Comprehensive Document

Build the 12-section product intelligence document. Every claim must be sourced — cite `[website]`, `[docs]`, `[G2 review]`, `[user-confirmed]`, etc.

### Section Guide

**1. Product Snapshot**
- Name, tagline, category, stage, platform(s), URL
- One-sentence description (from user confirmation in Phase 2)

**2. Core Value Proposition**
- Primary value prop (the single most important promise)
- Supporting value props (2-3 additional)
- "Only we can say" statement — derived via the Swap Test (see [references/value-proposition-canvas.md](references/value-proposition-canvas.md))
- Value prop hierarchy: primary → supporting → proof points

**3. How It Works**
- User journey from signup to value realization
- Key mechanics that deliver the value prop
- Core workflow in 3-5 steps

**4. Feature Analysis**
- Features grouped by capability area
- For each major feature: what it does, why it matters, how it compares to competitors
- Feature maturity indicators where available (new, stable, flagship)

**5. Competitive Positioning**
- Named competitors classified as direct, indirect, or alternative/status quo
- Positioning matrix (see [references/competitive-positioning.md](references/competitive-positioning.md))
- Moat analysis (network effects, switching costs, data, brand, scale, regulatory)
- Key differentiators with evidence

**6. Target Market Overview**
- High-level market description (B2B/B2C, size, industry, geo)
- Primary use cases
- Note: defer deep audience research to `icp-research` — this section provides product-side market context only

**7. Pricing & Business Model**
- Plans and pricing (current public info)
- Pricing model (subscription, freemium, usage-based, etc.)
- Free tier details if applicable
- Enterprise/custom pricing indicators

**8. Trust & Credibility**
- Social proof inventory (testimonials, logos, stats, awards)
- Security certifications and compliance (SOC 2, GDPR, HIPAA, etc.)
- Uptime/reliability claims with evidence
- Team credibility signals (founders, advisors, investors)

**9. Brand Voice & Personality**
- Voice adjectives (3-5, derived from actual copy analysis)
- Tone examples pulled from real website/social copy
- Brand personality traits observable from messaging
- Note: captures existing voice — for designing a new voice, use `brand-system`

**10. Vision & Roadmap**
- Public vision statement or mission
- Publicly known roadmap items
- User-confirmed upcoming changes (flagged as `[user-confirmed, not public]`)

**11. Getting Started / Onboarding**
- Steps from first touch to first value
- Estimated time-to-value
- Key activation moments
- Common friction points (from reviews)

**12. Programs & Incentives**
- Referral programs
- Affiliate/partner programs
- Loyalty/reward programs
- Promotional offers or discounts

### Confidence Scoring

Mark each section with a confidence level:
- **HIGH** — verified from ≥2 independent sources or user-confirmed
- **MEDIUM** — single source, plausible but unverified
- **LOW** — inferred, limited data, or conflicting sources

Flag unknowns explicitly with `[UNKNOWN — reason]` rather than guessing.

---

## Phase 4: Update product-context.md

After completing the comprehensive document, sync improved data back to `.agents/product-context.md`. This ensures the lightweight cross-stack file benefits from the deeper research.

Map findings to the 8 fields:
| product-context.md field | Source from product-description |
|--------------------------|-------------------------------|
| Product | Section 1 (Snapshot) — one-sentence description |
| Buyer | Section 6 (Target Market) — primary buyer |
| Problem | Section 2 (Value Prop) — primary pain solved |
| Differentiator | Section 5 (Competitive Positioning) — top differentiator |
| Social Proof | Section 8 (Trust) — best testimonial or stat |
| Model | Section 7 (Pricing) — price and model |
| Voice | Section 9 (Brand Voice) — 3 adjectives |
| Primary CTA | Section 1 or 11 — main call to action |

Only update fields where the new research provides better/more current data than what exists. Preserve user-confirmed data that research didn't improve.

---

## Artifact Template

```markdown
---
skill: product-description
version: 1
date: [today's date]
status: draft
sources-consulted: [number]
---

# Product Description: [Product Name]

**Date:** [today]
**Skill:** product-description
**Sources:** [list of source types consulted]

## 1. Product Snapshot

| Field | Value |
|-------|-------|
| **Name** | [name] |
| **Tagline** | [tagline] |
| **Category** | [category] |
| **Stage** | [stage] |
| **Platform** | [platforms] |
| **URL** | [url] |

**One-sentence description:** [description]

*Confidence: [HIGH/MEDIUM/LOW]*

## 2. Core Value Proposition

**Primary:** [primary value prop]

**Supporting:**
1. [supporting value prop 1]
2. [supporting value prop 2]
3. [supporting value prop 3]

**"Only we can say":** [statement that fails the Swap Test for competitors]

**Proof points:**
- [proof point 1] — [source]
- [proof point 2] — [source]

*Confidence: [HIGH/MEDIUM/LOW]*

## 3. How It Works

1. [Step 1 — what happens]
2. [Step 2 — what happens]
3. [Step 3 — what happens]
4. [Step 4 — what happens]

**Key mechanics:** [explain the core mechanism that delivers value]

*Confidence: [HIGH/MEDIUM/LOW]*

## 4. Feature Analysis

### [Capability Area 1]
| Feature | What It Does | Why It Matters | vs. Competitors |
|---------|-------------|----------------|-----------------|
| [feature] | [description] | [benefit] | [comparison] |

### [Capability Area 2]
[Same format]

*Confidence: [HIGH/MEDIUM/LOW]*

## 5. Competitive Positioning

### Competitor Map
| Competitor | Type | Key Strength | Key Weakness | vs. Us |
|-----------|------|-------------|-------------|--------|
| [name] | Direct/Indirect/Alternative | [strength] | [weakness] | [differentiator] |

### Positioning Matrix
[2x2 or key dimensions from competitive-positioning.md]

### Moat Analysis
| Moat Type | Strength | Evidence |
|-----------|----------|---------|
| [type] | None/Weak/Moderate/Strong | [evidence] |

*Confidence: [HIGH/MEDIUM/LOW]*

## 6. Target Market Overview

**Market:** [B2B/B2C, size, industry, geo]
**Primary use cases:**
1. [use case 1]
2. [use case 2]
3. [use case 3]

*→ For deep audience research, run `icp-research`.*

*Confidence: [HIGH/MEDIUM/LOW]*

## 7. Pricing & Business Model

| Plan | Price | Key Features |
|------|-------|-------------|
| [plan] | [price] | [features] |

**Model:** [subscription/freemium/usage-based/etc.]
**Free tier:** [yes/no — details]

*Confidence: [HIGH/MEDIUM/LOW]*

## 8. Trust & Credibility

**Social proof:**
- [testimonial, stat, logo, or award — with source]

**Security & compliance:**
- [certifications, standards]

**Team credibility:**
- [founder/team signals]

*Confidence: [HIGH/MEDIUM/LOW]*

## 9. Brand Voice & Personality

**Voice adjectives:** [adj 1], [adj 2], [adj 3]

**Tone examples from actual copy:**
- "[quote from website]" — [page/context]
- "[quote from social]" — [platform]

**Personality traits:** [observable traits from messaging]

*→ For designing a new brand voice, run `brand-system`.*

*Confidence: [HIGH/MEDIUM/LOW]*

## 10. Vision & Roadmap

**Vision:** [public vision/mission statement]

**Known roadmap:**
- [item 1] — [source]
- [item 2] — [source]

*Confidence: [HIGH/MEDIUM/LOW]*

## 11. Getting Started / Onboarding

1. [Entry point]
2. [Activation action]
3. [First value moment]
4. [Expansion trigger]

**Time-to-value:** [estimated time from signup to first value]
**Common friction:** [from reviews — source]

*Confidence: [HIGH/MEDIUM/LOW]*

## 12. Programs & Incentives

- **Referral:** [details or UNKNOWN]
- **Affiliate/Partner:** [details or UNKNOWN]
- **Loyalty:** [details or UNKNOWN]
- **Promotions:** [details or UNKNOWN]

*Confidence: [HIGH/MEDIUM/LOW]*

---

## Source Log

| # | Source | Type | Date Accessed | Key Contribution |
|---|--------|------|---------------|-----------------|
| 1 | [URL or description] | [website/docs/review/press/user] | [date] | [what it contributed] |

## Next Steps
- Run `icp-research` to build deep audience intelligence
- Run `imc-plan` to plan communication campaigns
- Run `copywriting` for craft-quality copy based on this intelligence

> On re-run: rename existing artifact to `product-description.v[N].md` and create new with incremented version.
```

---

## Worked Example

**User:** "Describe our product — it's called Railtrack, railtrack.app"

**Phase 1 — Research Scan:**
Agent scans railtrack.app landing page, docs, G2 reviews, Twitter, comparison articles. Finds: project tracking tool for Rails developers, integrates with GitHub, $15/mo per seat, 4.3 on G2, main competitors are Linear and Shortcut.

**Phase 2 — Gap Interview:**
> "Based on my research, here's what I've gathered about Railtrack:
> 1. **Core function:** Project tracking built specifically for Rails teams, with GitHub integration
> 2. **Primary value prop:** Native Rails conventions in project management (migrations as tasks, PR-linked stories)
> 3. **Pricing:** $15/seat/month, free tier for up to 3 users
> 4. **Main competitors:** Linear, Shortcut, Jira
>
> Please confirm or correct. Also:
> - What stage are you at? (looks like Growth based on G2 review count)
> - Any upcoming features that affect positioning?
> - What's the #1 reason customers choose you over Linear?"

User confirms, adds: "We're post-launch/growth. The #1 reason is our deploy-linked task completion — when a PR merges, linked tasks auto-close with deploy context. Nobody else does that natively."

**Phase 3 — Artifact saved to `.agents/mkt/product-description.md`:**

```markdown
---
skill: product-description
version: 1
date: 2026-03-19
status: draft
sources-consulted: 5
---

# Product Description: Railtrack

**Date:** 2026-03-19
**Skill:** product-description
**Sources:** product website, documentation, G2 reviews, Twitter, user interview

## 1. Product Snapshot

| Field | Value |
|-------|-------|
| **Name** | Railtrack |
| **Tagline** | "Project tracking that thinks in Rails" |
| **Category** | Developer tools — project management |
| **Stage** | Growth |
| **Platform** | Web app |
| **URL** | railtrack.app |

**One-sentence description:** Project tracking tool built for Rails teams that auto-closes tasks when linked PRs deploy.

*Confidence: HIGH*

## 2. Core Value Proposition

**Primary:** Ship Rails projects without context-switching between your tracker and your codebase.

**Supporting:**
1. Deploy-linked task completion — PR merges auto-close tasks with deploy context
2. Rails-native conventions — migrations, generators, and console patterns as first-class task types
3. GitHub-native — no sync lag, no broken links

**"Only we can say":** "The only project tracker where merging your PR closes the task with deploy context — no webhooks, no Zapier, no 'mark as done'." (Swap Test: Linear/Shortcut can't claim native deploy-linked closure.)

*Confidence: HIGH*

## 5. Competitive Positioning

### Competitor Map
| Competitor | Type | Key Strength | Key Weakness | vs. Us |
|-----------|------|-------------|-------------|--------|
| Linear | Direct | Speed, design polish, keyboard-first UX | No framework-specific features | We have Rails-native conventions and deploy-linked closure |
| Shortcut | Direct | API flexibility, Clubhouse legacy community | Slower iteration, less polished | We have tighter GitHub integration |
| Jira | Indirect | Enterprise features, ecosystem | Complexity, configuration overhead | We're opinionated for Rails; they're configurable for everyone |
| Spreadsheets | Alternative/Status quo | Zero learning curve | No automation, no code integration | We automate the tracking they do manually |

*Confidence: HIGH*
```

**Phase 4 — Updated `.agents/product-context.md`:**
- Product: "Railtrack — project tracking for Rails teams with deploy-linked task completion"
- Differentiator: "Only tracker where merging a PR auto-closes the task with deploy context"
- Model: "$15/seat/month, free for ≤3 users"

---

## Anti-Patterns

**Brochure copy instead of objective analysis** — This skill produces intelligence, not marketing copy. "Revolutionary platform that transforms project management" is copywriting output. "Project tracking tool with deploy-linked task closure, differentiating from Linear via Rails-native conventions" is product intelligence. Write the latter.

**Assumed features not verified from sources** — If you didn't find it on the website, in docs, or in reviews, and the user didn't confirm it, don't include it. Mark it `[UNKNOWN]` instead.

**Competitor hand-waving without naming names** — "Better than alternatives" is not competitive analysis. Name the competitors, state their strengths, and explain specific differentiators with evidence.

**Ignoring limitations** — Honest limitations help downstream copywriting (Pratfall Effect) and prevent overpromising. If G2 reviews consistently mention slow load times, include it. If the product only supports Rails, that's a limitation AND a differentiator — capture both.

**Duplicating ICP research** — This skill analyzes the product from a market perspective. It notes "B2B, Rails development teams" but does NOT build personas, collect VoC quotes, or map audience habitats. Defer all audience depth to `icp-research`.

**Filling gaps with guesses** — When data is unavailable, the correct output is `[UNKNOWN — no public pricing found]`, not an estimate. Guesses propagate through downstream skills and become "facts."

---

## References

- [references/product-analysis-framework.md](references/product-analysis-framework.md) — Research methodology, source hierarchy, confidence scoring, conflict resolution
- [references/value-proposition-canvas.md](references/value-proposition-canvas.md) — Value prop extraction, Swap Test, hierarchy, anti-patterns
- [references/competitive-positioning.md](references/competitive-positioning.md) — Positioning matrix, moat analysis, competitor classification
