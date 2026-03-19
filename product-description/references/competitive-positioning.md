# Competitive Positioning

Reference for the `product-description` skill. Defines competitor classification, positioning matrix, moat analysis, and differentiation mapping.

---

## Competitor Classification

Not all competitors are equal. Classify each into one of three types to understand the real competitive landscape.

### Three Types

| Type | Definition | Example (for a Rails project tracker) |
|------|-----------|---------------------------------------|
| **Direct** | Same category, same buyer, overlapping features | Linear, Shortcut, Jira |
| **Indirect** | Different category, same job-to-be-done | GitHub Projects, Notion databases, Basecamp |
| **Alternative / Status Quo** | What the buyer does if they buy nothing | Spreadsheets, Slack threads, standup meetings |

### Why Classification Matters

- **Direct competitors** are who buyers compare you to. Your positioning must address them by name.
- **Indirect competitors** reveal how buyers think about the problem. They may not search for "project tracker" — they search for "how to manage Rails sprints."
- **Alternatives / status quo** are often the biggest competitor. Most prospects are doing *something* today, and inertia is powerful. Your positioning must address "why change at all."

### Identification Method

1. **From research:** Comparison articles, "vs" searches, G2/Capterra alternatives sections
2. **From reviews:** "I switched from X to Y" mentions
3. **From user interview:** "What were you using before?" and "What did you evaluate?"
4. **From website:** Competitor comparison pages, positioning statements

Aim for 2-4 direct, 2-3 indirect, and 1-2 alternatives. If you find more, prioritize by:
- Frequency of mention in reviews and comparisons
- Market share / mindshare in the category
- Relevance to the specific buyer segment

---

## Positioning Matrix

A positioning matrix visualizes where the product sits relative to competitors along the two dimensions that matter most to the buyer.

### How to Choose Dimensions

The two axes should be:
1. **Differentiating** — the product scores differently from competitors on this dimension
2. **Important to buyers** — buyers actually care about this dimension (not just technically interesting)
3. **Observable** — buyers can evaluate this without deep expertise

### Common Dimension Pairs

| Dimension Pair | Good For |
|---------------|----------|
| Ease of use ↔ Power/flexibility | Tools with different complexity tradeoffs |
| Specialist ↔ Generalist | Products serving specific vs. broad audiences |
| Self-serve ↔ Enterprise | Products with different go-to-market models |
| Speed ↔ Comprehensiveness | Tools trading off speed vs. depth |
| Price ↔ Feature richness | Products at different price points |

### Matrix Template

```
                    [Dimension 1: High]
                         │
          ┌──────────────┼──────────────┐
          │              │              │
          │  [Quadrant]  │  [Quadrant]  │
          │              │              │
[Dim 2:   ├──────────────┼──────────────┤  [Dim 2:
 Low]     │              │              │   High]
          │  [Quadrant]  │  [Quadrant]  │
          │              │              │
          └──────────────┼──────────────┘
                         │
                    [Dimension 1: Low]
```

Place each competitor (direct and indirect) on the matrix. The goal is to identify:
- **White space** — quadrants with no competitors (opportunity or warning)
- **Crowded zones** — quadrants with 3+ competitors (differentiation is critical)
- **Your position** — where you are and whether it's defensible

### Positioning Statement Formula

After completing the matrix, synthesize into a positioning statement:

> **For** [target audience] **who** [situation/need], **[product]** is the **[category]** that **[key differentiator]** **unlike** [primary competitor] **which** [competitor's approach].

Example:
> **For** Rails engineering teams **who** need project tracking that reflects what actually shipped, **Railtrack** is the **developer project tracker** that **auto-closes tasks when PRs deploy** **unlike** Linear **which** requires manual status updates or generic webhook automation.

---

## Moat Analysis

A moat is a sustainable competitive advantage that makes it hard for competitors to replicate your position. Identify which moats exist (or don't) for honest positioning.

### Six Moat Types

| Moat Type | Definition | Signals | Questions to Ask |
|-----------|-----------|---------|-----------------|
| **Network Effects** | Product becomes more valuable as more people use it | Marketplace dynamics, social features, shared workspaces | Does adding one user make the product better for existing users? |
| **Switching Costs** | High cost (time, money, data) to switch away | Data lock-in, workflow dependencies, integrations, team training | How painful would it be for a team to migrate to a competitor? |
| **Data Advantage** | Proprietary data that improves the product over time | ML models trained on usage, benchmark datasets, historical analytics | Does the product get smarter/better with more usage data? |
| **Brand** | Recognition and trust that competitors can't quickly replicate | NPS, word-of-mouth, community, thought leadership | If a competitor built the same features, would customers still choose you? |
| **Scale Economies** | Cost advantages from volume | Infrastructure costs, content library, distribution channels | Do unit economics improve significantly with scale? |
| **Regulatory / IP** | Patents, licenses, certifications that create barriers | Patents filed, compliance certifications, exclusive partnerships | Are there legal or regulatory barriers competitors must overcome? |

### Moat Strength Assessment

For each moat type, assess strength:

| Strength | Definition |
|----------|-----------|
| **Strong** | Active moat that demonstrably deters competitors. Evidence of competitors failing to replicate. |
| **Moderate** | Moat exists but hasn't been tested. Competitors could overcome with significant investment. |
| **Weak** | Early-stage moat or easily replicable advantage. Provides temporary breathing room only. |
| **None** | No advantage on this dimension. Competitors can match freely. |

### Honest Moat Reporting

Most startups and growth-stage products have 0-2 weak moats. That's normal and worth reporting honestly — it informs positioning strategy:

- **Strong moats** → lean into them in messaging
- **Weak moats** → invest in strengthening them, don't over-claim in messaging
- **No moats** → positioning must rely on execution speed, specialization, or brand
- **Multiple no-moats** → flag this as a strategic risk; recommend `solution-design` for strategic response

---

## Feature Parity vs. Differentiation Mapping

Mapping features against competitors reveals where you have parity (table stakes) and where you differentiate (positioning leverage).

### Feature Comparison Template

| Feature | Us | Competitor A | Competitor B | Status |
|---------|----|-----------|-----------|----|
| [feature 1] | ✅ | ✅ | ✅ | **Parity** — table stakes |
| [feature 2] | ✅ | ✅ | ❌ | **Partial parity** |
| [feature 3] | ✅ | ❌ | ❌ | **Differentiator** — positioning leverage |
| [feature 4] | ❌ | ✅ | ✅ | **Gap** — acknowledged limitation |
| [feature 5] | ❌ | ✅ | ❌ | **Gap** — evaluate priority |

### How to Use the Map

- **Parity features:** Don't lead with these in positioning — everyone has them. Mention only to reassure.
- **Differentiators:** These ARE your positioning. Lead with them. Run the Swap Test to confirm they're truly unique.
- **Gaps:** Be honest about these. Downstream skills (copywriting, lp-optimization) handle gaps better when they know about them — the Pratfall Effect makes honest limitations increase trust.
- **Partial parity:** These are nuance opportunities. "We both have X, but ours does Y differently because Z."

### Differentiation Durability

Not all differentiators last. Assess each:

| Durability | Definition | Example |
|-----------|-----------|---------|
| **Durable (12+ months)** | Requires deep architecture changes or domain expertise to replicate | Deploy-linked task closure built into core data model |
| **Moderate (6-12 months)** | Competitor could build it, but it's not on their roadmap | Rails-specific task templates |
| **Fragile (<6 months)** | Easy for competitor to copy, or they're already building it | Dark mode, mobile app |

Flag fragile differentiators in the artifact — downstream skills shouldn't build messaging on advantages that may disappear by launch.
