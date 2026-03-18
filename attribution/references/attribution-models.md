# Attribution Model Selection Guide

How to choose the right attribution model based on your business type and buying cycle.

---

## Model Overview

| Model | How It Works | Best For | Limitation |
|-------|-------------|----------|------------|
| **First-touch** | 100% credit to first interaction | Understanding what creates awareness | Ignores everything after discovery |
| **Last-touch** | 100% credit to final interaction before conversion | Short sales cycles, impulse purchases | Ignores what created awareness |
| **Linear** | Equal credit across all touchpoints | Simple multi-touch, early-stage teams | Treats all touchpoints as equal |
| **Time-decay** | More credit to recent touchpoints | Long sales cycles where momentum matters | Undervalues initial awareness |
| **Position-based (U-shaped)** | 40% first, 40% last, 20% split across middle | Most B2B SaaS businesses | Arbitrary weight distribution |
| **Data-driven** | ML model assigns credit based on actual impact | Mature businesses with enough data (1,000+ conversions/month) | Requires significant data volume |

---

## Selection Matrix

| Business Type | Buying Cycle | Recommended Model | Why |
|--------------|-------------|-------------------|-----|
| **B2C impulse** (e-commerce, apps) | Hours to days | Last-touch | Short cycle means last touchpoint is most relevant |
| **B2C considered** (subscriptions, courses) | Days to weeks | Linear or time-decay | Multiple touchpoints matter; recency is useful |
| **B2B SMB SaaS** | 1-4 weeks | Position-based | First touch (how they found you) and last touch (what converted them) both matter |
| **B2B Mid-Market** | 1-6 months | Position-based or time-decay | Long cycle with many touchpoints; weigh recent interactions higher |
| **B2B Enterprise** | 3-18 months | Account-based attribution | Multiple stakeholders; track at account level, not individual |
| **Creator/personal brand** | Varies | First-touch | Key question is "how did they discover me?" |
| **Marketplace** | Varies by category | Last-touch per side | Supply and demand sides may have different models |

---

## Measurement Windows

Different content types need different measurement windows. Measuring blog content on a 7-day window will always show zero impact.

| Content Type | Measurement Window | Rationale |
|-------------|-------------------|-----------|
| **Paid ads** | 7-14 days | Direct response, short attribution path |
| **Email campaigns** | 3-7 days | Click-through is immediate, conversion may lag |
| **SEO / blog content** | 30-90 days | Discovery → trust → conversion takes time |
| **Brand / awareness content** | 60-120 days | May not drive direct conversion but influences later decisions |
| **Events / webinars** | 30-60 days | Relationship building that converts over time |
| **Social media organic** | 14-30 days | Engagement may not lead to immediate conversion |

### Setting Lag-Time Defaults

When tracking attribution, apply these defaults unless you have data suggesting otherwise:

- **Direct response channels** (paid, email): 7-day click, 1-day view
- **Content channels** (blog, SEO): 30-day click, 7-day view
- **Brand channels** (social, PR): 60-day window
- **Adjust based on data:** If you see conversions spiking at day 45 after blog visits, extend to 60 days

---

## Common Pitfalls

### Last-Touch Bias
Most analytics tools default to last-touch. This means:
- Blog posts that introduce 1,000 people to your brand get zero credit
- The pricing page or "book a demo" button gets all credit
- Teams optimize for bottom-of-funnel and starve top-of-funnel

**Fix:** Run parallel first-touch and last-touch reports. If they tell different stories, you need multi-touch.

### Channel-Level vs. Content-Level
- **Channel-level:** "LinkedIn drives 30% of leads" — useful for budget allocation
- **Content-level:** "This specific carousel drove 50 leads" — useful for content strategy

Track both. Channel-level informs where to invest; content-level informs what to create.

### Self-Reported Attribution
Ask "How did you hear about us?" on signup forms. This captures dark social (podcast mentions, Slack recommendations, word of mouth) that no tracking tool can see.

Self-reported data often contradicts analytics data — both are useful:
- Analytics: tells you what they clicked
- Self-reported: tells you what they remember (often the first meaningful touchpoint)

---

## Implementation Priorities

If building attribution from scratch:

1. **Start with last-touch** — it's in every analytics tool, requires no setup
2. **Add self-reported attribution** — one dropdown on your signup form
3. **Add UTM tracking** — tag all links with source/medium/campaign
4. **Move to position-based** — once you have 3+ months of multi-touch data
5. **Consider data-driven** — only when you have 1,000+ conversions/month

Don't wait for perfect attribution to make decisions. Directional data with last-touch + self-reported beats no data while you build the perfect model.
