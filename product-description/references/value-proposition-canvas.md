# Value Proposition Canvas

Reference for the `product-description` skill. Defines value prop extraction, the Swap Test, hierarchy construction, and common anti-patterns.

---

## Jobs-to-Be-Done Extraction

Every product feature maps to a job the user is trying to get done. Extracting JTBD from features produces value propositions grounded in user need, not product capability.

### Feature → Job → Value Prop Pipeline

| Step | Question | Example |
|------|----------|---------|
| 1. **Feature** | What does it do? | "Deploy-linked task completion" |
| 2. **Functional job** | What task does this help them accomplish? | "Track project progress without manual updates" |
| 3. **Emotional job** | How does this make them feel? | "Confident that the board reflects reality" |
| 4. **Social job** | How does this make them look to others? | "Team lead who runs a tight ship without micromanaging" |
| 5. **Value prop** | Why does this matter? | "Ship without wondering if your tracker is lying to you" |

### Extraction Method

For each major feature discovered in Phase 1:
1. State the feature objectively (what it does)
2. Ask: "So what?" — what job does it help accomplish?
3. Ask again: "So what?" — why does accomplishing that job matter?
4. Ask a third time: "So what?" — what's the ultimate outcome or avoided pain?

The third "so what" usually reveals the real value proposition. The first is just a feature description.

**Example:**
- Feature: "Real-time GitHub sync"
- So what? → "Tasks update automatically when code changes"
- So what? → "No more stale boards that don't reflect reality"
- So what? → "Stop wasting standup time reconciling what actually shipped"

Value prop: "Stop wasting standup time reconciling what actually shipped."

---

## The Swap Test

The Swap Test determines whether a value proposition is truly unique or generic enough that any competitor could claim it.

### How to Run the Swap Test

1. Write the value proposition or key claim
2. Replace the product name with the top 2-3 competitors' names
3. Read it aloud. Does it still make sense? Does it still feel true?
4. **If yes → rewrite.** The claim is generic.
5. **If no → keep.** The claim is uniquely yours.

### Swap Test Examples

| Claim | Swap with Competitor | Result |
|-------|---------------------|--------|
| "Railtrack helps teams ship faster" | "Linear helps teams ship faster" → still works | **FAIL** — generic speed claim |
| "Railtrack auto-closes tasks when your PR deploys" | "Linear auto-closes tasks when your PR deploys" → Linear can't do this | **PASS** — specific, unique capability |
| "The best project tracker for developers" | "The best project tracker for developers" → anyone can say this | **FAIL** — subjective superlative |
| "The only tracker where merging a PR closes the task with deploy context" | Can't swap — capability is unique | **PASS** — factual and exclusive |

### When Claims Are Borderline

Some claims are technically unique but feel generic:
- "Built specifically for Rails teams" → Could a competitor retarget? If Linear made a Rails integration, could they say this? If yes but they haven't, it's **currently unique but fragile.** Note this.
- "AI-powered insights" → Anyone building AI features could say this. **FAIL.**

For borderline cases, add a qualifier that makes it concrete: "Built by Rails core contributors" is harder to swap than "Built for Rails teams."

---

## "Only We Can Say" Statement

The ultimate output of value prop analysis: a statement that is factually true for your product and factually false for every named competitor.

### Derivation Process

1. List all claimed differentiators from Phase 1 research
2. Run each through the Swap Test against top 3 competitors
3. Survivors become candidate "only we can say" statements
4. Rank candidates by:
   - **Relevance** — does the buyer care about this?
   - **Verifiability** — can they check if it's true?
   - **Durability** — will this still be true in 12 months?
5. Top-ranked candidate becomes the "only we can say" statement

If no claim survives the Swap Test, that's a finding worth reporting — it means the product's positioning needs work. Don't manufacture uniqueness that doesn't exist.

---

## Value Prop Hierarchy

Value propositions operate at different levels. A complete product description needs all three, in order.

### Level 1: Primary Value Prop
- The single most important promise
- Answers: "Why should I use this instead of doing nothing?"
- Must pass the Swap Test
- Goes in the hero section of any landing page

### Level 2: Supporting Value Props (2-3)
- Additional reasons that reinforce the primary
- Each addresses a different concern or benefit dimension
- Answers: "What else do I get?"
- Go in feature/benefit sections

### Level 3: Proof Points
- Specific evidence that each value prop is true
- Stats, testimonials, case studies, certifications
- Answers: "How do I know this is true?"
- Go in social proof, trust, and credibility sections

### Hierarchy Example

```
PRIMARY: "Ship Rails projects without context-switching between tracker and codebase"

SUPPORTING:
├── "Deploy-linked closure: PR merge → task done, automatically"
│   └── PROOF: "Used by 400+ Rails teams" [G2], "4.3★ rating" [G2]
├── "Rails-native conventions: migrations and generators as task types"
│   └── PROOF: "Built by Rails core contributors" [about page]
└── "GitHub-native: zero sync lag, no broken links"
    └── PROOF: "Real-time webhook sync, <1s delay" [docs]
```

---

## Common Value Prop Anti-Patterns

| Anti-Pattern | Example | Fix |
|-------------|---------|-----|
| **Superlative without proof** | "The best project tracker" | Replace with specific claim: "The only tracker with deploy-linked closure" |
| **Feature masquerading as value** | "Real-time sync" | Add the "so what": "Never update a task manually again" |
| **Audience-agnostic** | "Great for all teams" | Narrow: "Built for Rails teams shipping to production weekly" |
| **Benefit without mechanism** | "Save hours every week" | Add how: "Auto-close tasks on deploy — no manual status updates" |
| **Competitor-blind** | "Better than alternatives" | Name them: "Unlike Linear, tasks close when your PR actually ships, not when you click a button" |
| **Aspiration stated as fact** | "Trusted by thousands" | If you have 200 users, say "Used by 200 Rails teams." Honest is more credible. |
| **Buzzword salad** | "AI-powered next-gen platform" | Strip to concrete: what does AI specifically do in this product? |
