---
name: content-create
description: "Creates platform-native content with hooks, body copy, CTAs, and A/B variants from IMC plan angles. Use when the user asks to create content, write a content brief, make social posts, write copy, create headlines, write taglines, or improve copy — content creation, creative briefs, platform-native content, carousel, video script, thread, social media copy, A/B variants, copywriting, persuasive writing, headline formulas, CTA optimization."
argument-hint: "[angle or topic]"
license: MIT
metadata:
  author: hungv47
  version: "2.2.0"
---

# Content Creation

*Communicate Track — Step 3 of 4. Turns IMC angles into production-ready content with A/B variants.*

**Core Question:** "Would the target persona actually stop scrolling for this?"

## Philosophy

The copy frameworks (PAS, 3-Question Test, CTA formula) are proven tools — not mandatory templates. A skilled writer may combine frameworks, or write a hook that breaks the 8-word guideline because the extra words earn their place. The test is: does this stop the scroll and move the reader? Frameworks get you there faster. They don't define the only path.

## Inputs Required
- Angle + channel from `.agents/mkt/imc-plan.md` (or user-provided)

## Output
- `.agents/mkt/content/[slug].md`

## Quality Gate
Before delivering, verify:
- [ ] Hook communicable concisely — ≤8 words is a strong target; if longer, every extra word must earn its place by adding specificity or surprise
- [ ] Hook passes 3-question test: visual? falsifiable? uniquely yours?
- [ ] Every headline/hook contains concrete nouns or specific numbers (no abstract "better," "innovative," "leading")
- [ ] Key headlines pass the Competitor Swap Test (swap in competitor name — if it still works, rewrite)
- [ ] CTA follows formula: [action verb] + [what they get] (not "Learn More" or "Click Here")
- [ ] A/B variant changes exactly ONE element — and hypothesis states the learning if B wins

## Chain Position
Previous: `imc-plan` | Next: `attribution`
**Re-run triggers:** When IMC plan angles are updated, when targeting a new platform, or when A/B test results suggest a new direction.

### Skill Deference
- **Page already exists and problem is conversion?** → Run `lp-optimization` first — it diagnoses conversion blockers before rewriting.
- **Content reads as AI-generated?** → Run `humanize` after this skill — it strips AI patterns and compresses.
- **Seven-Sweeps (Step 6) is a quality pass within this skill.** If output still reads as AI-generated after Seven-Sweeps, run `humanize` as a dedicated pass.
- **Angle already defined in IMC plan?** → Use it directly — don't re-derive. This skill refines hooks within an angle, not replaces the angle.
- **Optimizing for search/AI citations?** → Coordinate with `seo` for keyword targeting, schema markup, and content structure.

---

## Before Starting

### Step 0: Product Context
Check for `.agents/product-context.md`. If available, read for product details and accuracy.
If `.agents/mkt/imc-plan.md` or `.agents/product-context.md` `date` fields are older than 30 days, recommend re-running upstream skills before proceeding — stale data produces misaligned content.

### Required Artifacts
| Artifact | Source | If Missing |
|----------|--------|------------|
| `imc-plan.md` | imc-plan | **INTERVIEW.** Gather: angle, channel, placement, awareness stage. |

### Optional Artifacts
| Artifact | Source | Benefit |
|----------|--------|---------|
| `icp-research.md` | icp-research | VoC language for copy |
| `product-context.md` | icp-research | Product details for accuracy |

Read `.agents/mkt/imc-plan.md` if it exists — pull angle, hook type, awareness stage, channel. If it doesn't exist, interview for:
1. Target angle for this content piece
2. Channel and placement
3. Audience awareness stage

Use WebSearch to verify current platform specs before writing — specs change frequently and outdated dimensions waste production time: `"[platform] [format] specs [year]"` (e.g., "LinkedIn carousel specs 2026"). See [references/platform-specs.md](references/platform-specs.md) for baseline reference.

---

## Step 1: Write the Hook

The hook stops the scroll. Write the exact text.

| Hook Type | Pattern | Example |
|-----------|---------|---------|
| Question | "Have you ever [relatable]?" | "Have you ever spent more time reporting than doing?" |
| Bold claim | "[Controversial statement]" | "Your meetings problem isn't meetings." |
| How-to | "How to [outcome] without [sacrifice]" | "How to ship 2x faster without hiring" |
| Story | "I [action] and [surprise]" | "I cut meetings 80%. Output doubled." |
| Data | "[Surprising stat]" | "31 hours/month in unproductive meetings" |
| Contrarian | "Stop [common advice]" | "Stop tracking velocity." |

Run the hook through the 3-question test. If any answer is no, rewrite before continuing — weak hooks waste every downstream production effort.

Write 3-5 hook variations using different hook types before selecting. Run each through the 3-question test. Keep the strongest; present top 2 as alternatives with annotations explaining why each works. See [references/copywriting-craft.md](references/copywriting-craft.md) for the full variation workflow and evaluation rubric.

**When 2+ hooks tie on the 3Q test**, apply secondary criteria:

| Tiebreaker | Question | Higher Score Wins |
|-----------|---------|-------------------|
| **Surprise** | Which hook was least obvious / most unexpected? | Surprising hooks stop the scroll |
| **ICP anchor** | Which hook maps to a specific metric or pain from ICP research? | Grounded hooks convert better |
| **Objection-free** | Which hook triggers zero obvious objections? | Clean hooks have less falloff |

Document which tiebreaker you used — this trains your judgment for future content.

---

## Step 2: Write the Body

Write the ACTUAL copy — not an outline, not a description.

**Video:** Timestamped script with text-on-screen, voiceover, and visual direction.
**Static post:** Complete caption, every word.
**Carousel:** Every slide, cover to CTA.
**Thread:** Every post, numbered.
**Full-page copy** (landing pages, homepages): Organize output section-by-section with 2-3 alternatives per key section — see [references/copywriting-craft.md](references/copywriting-craft.md) for section structure.
**Email** (drip campaigns, onboarding sequences, lifecycle emails): Subject line (≤50 chars, A/B variants) + preview text (≤90 chars) + body (one CTA per email, PAS or story framework) + CTA button text + P.S. line (optional — high-read section). For sequences, include send timing and trigger conditions between emails.

---

## Step 3: Write the CTA

| Stage | Pattern | Example |
|-------|---------|---------|
| Unaware | Discover | "See why this matters →" |
| Problem Aware | Explore | "Discover the fix →" |
| Solution Aware | Compare | "See how we're different →" |
| Product Aware | Try | "Start free trial →" |
| Most Aware | Act | "Start now — first month free →" |

Starting vocabulary, not a prescription. Match CTA energy to audience readiness, not just the awareness stage label. A Most Aware audience may respond better to a softer CTA if trust is already established.

Include: exact CTA text, destination, tracking parameters.

---

## Step 4: A/B Variant

Create variant B that changes exactly ONE element:

| What to Test | When | What You Learn if B Wins |
|-------------|------|------------------------|
| Hook | Default — always test the hook first | Audience responds more to [B's approach] than [A's] |
| CTA | Hook is strong, conversion is weak | [B's framing] reduces friction better |
| Format | Engagement is low despite good hook | Audience prefers [B's format] on this platform |
| Angle framing | Testing different emotional entry points | [B's emotion] resonates more than [A's] |

---

## Step 5: VoC Validation Check

Before finalizing, verify the content echoes actual audience language:
- [ ] Hook uses words/phrases from VoC quotes in ICP research (not marketing-speak)
- [ ] Pain expressions match how the audience actually describes the problem
- [ ] Emotional triggers are grounded in ICP emotional drivers (not assumed)

If `.agents/mkt/icp-research.md` exists, pull 2-3 VoC quotes and check: does this content sound like something the persona would share, or something a marketer would write? The gap between these two is where content underperforms.

---

## Step 6: Asset Checklist

What the production team needs. Be specific about dimensions, formats, and brand assets.

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
**Annotations:** [Rule that drove hook choice, cut alternative, rubric score — see copywriting-craft.md annotation guide]

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

**Test hypothesis:** If B wins, it means [specific learning about the audience].

## Asset Checklist

- [ ] [Asset with specs]
- [ ] [Asset with specs]
- [ ] [Brand assets needed]

> On re-run: rename existing artifact to `[slug].v[N].md` and create new with incremented version.
```

---

## Worked Example

```markdown
# Content: Status Update Waste — LinkedIn Carousel

**Date:** 2026-03-13
**Skill:** content-create
**Angle:** "Engineering teams lose 12 hrs/week to status updates nobody reads"
**Channel:** LinkedIn carousel, @brand
**Stage:** Problem Aware

## Hook

"Your team loses 12 hours a week to status updates nobody reads."

**3Q Test:** Visual: Y (12 hours, status updates) | Falsifiable: Y (12 is a specific, checkable number) | Uniquely ours: Y (cites our research data)

## Body

- Slide 1: "Your team loses 12 hours a week to status updates nobody reads."
- Slide 2: "Here's where those hours go:" [pie chart visual]
- Slide 3: "4 hrs — writing updates for managers who skim them"
- Slide 4: "3 hrs — standups where 8 people wait to give 30-second updates"
- Slide 5: "3 hrs — switching between tools to piece together who's doing what"
- Slide 6: "2 hrs — 'quick syncs' that could have been a dashboard"
- Slide 7: "The fix isn't better updates. It's fewer updates with better visibility."
- Slide 8: CTA slide

## CTA

- **Text:** "See how teams ship without status theater →"
- **Destination:** /product/visibility
- **Tracking:** utm_source=linkedin&utm_medium=organic&utm_campaign=status-waste&utm_content=carousel-v1

## A/B Variant

| Element | A (Main) | B (Variant) |
|---------|----------|-------------|
| Hook | "Your team loses 12 hrs/week..." (Data) | "I stopped doing standups. Here's what happened." (Story) |

**Test hypothesis:** If B wins, our audience responds more to personal narrative than statistics on LinkedIn.

## Asset Checklist

- [ ] 8 slides, 1080×1350px (LinkedIn carousel format)
- [ ] Slide 2: pie chart showing hour breakdown
- [ ] Brand fonts + colors applied to all slides
- [ ] Logo on slides 1 and 8
```

---

## Anti-Patterns

**Burying the lead** — Starting with context or background instead of the hook. The first line must stop the scroll — everything before the hook is wasted because nobody reads past a weak opening.

**Platform-generic content** — Writing the same way for LinkedIn, Twitter, and Instagram. Each platform has native patterns (carousel slides vs. threads vs. reels) — content that ignores format conventions underperforms regardless of message quality.

**Weak CTAs** — "Learn More" and "Click Here" tell the reader nothing about what they get. Every CTA must follow [action verb] + [what they get] — specificity increases click-through.

**A/B testing multiple variables** — Changing the hook, CTA, and format simultaneously makes results uninterpretable. Change exactly ONE element per variant — the learning is more valuable than the lift.

**Writing outlines instead of copy** — Delivering "Slide 3: Talk about the pain point" instead of the actual words. Content creation means writing every word, slide, and timestamp — outlines are not deliverables.

**Adjective-heavy copy** — "Innovative, cutting-edge, best-in-class solution" says nothing specific. Replace every adjective with a fact: "Used by 3,000 teams" beats "trusted by many."

**Features without benefits** — "Real-time sync" is a feature. "Never ask 'did you see my update?' again" is a benefit. Lead with the outcome the reader cares about, then mention the feature that enables it.

**Writing for the brand, not the buyer** — Copy that sounds impressive to the marketing team but doesn't use the buyer's language. Pull phrasing from VoC quotes and ICP research — write how they talk, not how the brand talks.

**AI copy slop** — Recognizable AI-generated patterns that signal generic output: "Unlock the power of...", "In today's fast-paced world...", "Revolutionize your workflow", "Seamlessly integrate", "Whether you're a [X] or a [Y]". The Competitor Swap Test catches most of these — if it reads like any SaaS website's hero, it fails.

---

## Copy Principles

### The Three-Question Test

Run every key sentence through this filter:

1. **Visual?** Close eyes — can the reader see it? ("Couch to 5K" = yes. "Regain fitness" = no.)
2. **Falsifiable?** Is it true or false? ("6'2, reads on the tube" = yes. "Funny, smart, good values" = no.)
3. **Uniquely yours?** Could a competitor sign this? ("The dating app designed to be deleted" = only Hinge. "The best platform" = anyone.)

Three yeses = keep. Any no = rewrite.

### Core Rules

**Make It Visual** — Abstract words evaporate. Concrete words stick. Zoom-in technique: Write the abstract word → ask "what do I actually mean?" → keep zooming until you hit something you can drop on your foot.

**Make It Falsifiable** — True-or-false statements put your head on the chopping block. "Don't talk, only point" — point at the graph, the statistic, the specific feature.

**Make It Yours Alone** — "Never write an ad a competitor can sign." Test: Swap in competitor's name. Still works? Rewrite.

**Facts Over Adjectives** — Start with a fact. Build from there. "Even when it's not Heinz, it's Heinz."

### CTA Formula

`[Action Verb] + [What They Get] + [Qualifier]`

Bad: Submit, Learn More, Click Here
Good: "Start your free trial", "Download the 2026 playbook", "See pricing for your team"

### Speed Test

Show someone the copy for two seconds. If they don't get it, rewrite.

### Copy Process

Before writing any key line, answer:
1. Who am I talking to? What do they currently believe?
2. What should they believe after reading this?
3. What can I say that nobody else can?

### Page-Specific Guidance

| Page | Key Principle |
|------|--------------|
| **Homepage** | What you do in one sentence. Primary use case, not every feature. |
| **Landing Page** | One goal, one CTA. Match headline to traffic source. Remove nav. |
| **Pricing** | Lead with value, not price. Anchor with most popular plan. |
| **Feature** | Lead with outcome ("Track time in one click"), not feature name. |
| **About** | Founding story. What you believe. Team photos + real context. |

---

## References

- [references/examples.md](references/examples.md) — Complete worked examples with full copy
- [references/platform-specs.md](references/platform-specs.md) — Platform dimensions, limits, native patterns
- [references/copy-frameworks.md](references/copy-frameworks.md) — Headline formulas, PAS framework, page templates
- [references/copywriting-craft.md](references/copywriting-craft.md) — Variation workflow, extended techniques, evaluation rubric, annotation guide
- [references/seven-sweeps.md](references/seven-sweeps.md) — Structured 7-pass editing method (Clarity → Voice → So What → Prove It → Specificity → Emotion → Zero Risk)
- [references/repurposing-cascade.md](references/repurposing-cascade.md) — Hero → derivative content workflow across channels
