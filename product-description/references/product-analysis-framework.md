# Product Analysis Framework

Reference for the `product-description` skill. Defines the scan-then-interview methodology, source reliability, and confidence scoring.

---

## Scan-Then-Interview Methodology

The core principle: **research first, interview second.** Users shouldn't have to answer questions that public sources already answer. This surfaces information the team has forgotten or takes for granted.

### Execution Order

1. **Automated scan** — exhaust all available research tools against all source types
2. **Organize findings** — structure by the 12 artifact sections, noting coverage gaps
3. **Present findings** — show the user what you found, organized for easy confirmation
4. **Interview for gaps** — ask ONLY about what research couldn't answer
5. **Resolve conflicts** — where sources disagree, present both and ask the user to clarify

### When to Stop Scanning

Stop scanning a source category when:
- You've found consistent information from ≥2 independent sources
- The source type doesn't exist for this product (e.g., no app store listing for a B2B SaaS)
- You've spent 3+ queries on a source type with no results

Don't over-research. The goal is sufficient coverage, not exhaustive scraping.

---

## Source Reliability Hierarchy

When sources conflict, trust them in this order:

| Priority | Source Type | Reliability | Why |
|----------|-----------|-------------|-----|
| 1 | **Official documentation / API docs** | Highest | Written for accuracy, maintained by the team, versioned |
| 2 | **Product website (current)** | High | Reflects current positioning, but may be aspirational |
| 3 | **User-confirmed information** | High | First-party knowledge, but may be biased or outdated |
| 4 | **Recent user reviews (G2, Capterra, <6 months)** | Medium-High | Real user experience, but individual perspective |
| 5 | **Press coverage / interviews** | Medium | Journalistic filter, but may be based on PR materials |
| 6 | **Social media (official accounts)** | Medium | Current voice/positioning, but performative |
| 7 | **Older reviews (>6 months)** | Medium-Low | Product may have changed significantly |
| 8 | **Third-party comparison articles** | Low-Medium | May be affiliate content or outdated |
| 9 | **Social media (community mentions)** | Low | Anecdotal, may be unrepresentative |
| 10 | **AI-generated summaries** | Do not use | Circular — may hallucinate or recycle stale data |

### Handling Conflicting Information

When two sources disagree:

1. **Check recency** — more recent source wins unless the older source is higher-reliability
2. **Check specificity** — specific claim beats general claim ("$15/seat/month" beats "affordable pricing")
3. **Check independence** — if two sources say the same thing, they might be citing the same original source. Trace back.
4. **Flag for user** — if still unclear, present both versions in the gap interview: "Your website says X, but G2 reviewers report Y — which is current?"

### Source-Specific Search Patterns

**Product Website:**
```
[product name] site:[domain]
[product name] features
[product name] pricing
[product name] about
[product name] security OR compliance OR trust
```

**Documentation:**
```
[product name] docs OR documentation
[product name] API reference
[product name] getting started OR quickstart
[product name] integrations
[product name] changelog OR release notes
```

**Reviews:**
```
site:g2.com "[product name]"
site:capterra.com "[product name]"
site:trustradius.com "[product name]"
"[product name]" review pros cons
```

**Competitive Intelligence:**
```
"[product name]" vs
"[product name]" alternative
"[product name]" compared to
switch from "[competitor]" to "[product name]"
"[product name]" OR "[competitor]" comparison
```

**Press & Media:**
```
"[product name]" launch OR announce OR funding OR raised
"[product name]" founder OR CEO interview
"[product name]" TechCrunch OR ProductHunt OR HackerNews
```

**Social & Community:**
```
"[product name]" site:twitter.com
"[product name]" site:reddit.com
"[product name]" site:linkedin.com
"[product name]" site:producthunt.com
```

---

## Confidence Scoring

Assign a confidence level to each of the 12 sections in the final artifact.

| Level | Criteria | Action |
|-------|----------|--------|
| **HIGH** | Verified from ≥2 independent sources, OR user-confirmed, OR from official documentation | Include as-is |
| **MEDIUM** | Single reliable source, plausible but unverified by user or second source | Include with source citation, recommend user verification |
| **LOW** | Inferred from indirect evidence, limited data, or conflicting sources unresolved | Include with `[LOW CONFIDENCE]` flag and reasoning |
| **UNKNOWN** | No data found, conflicting sources unresolved, or user declined to answer | Mark as `[UNKNOWN — reason]`, do not guess |

### Confidence Decay

Product information ages. As a general guide:
- **Pricing:** stale after 3 months (companies adjust frequently)
- **Features:** stale after 6 months (especially for SaaS)
- **Positioning/competitors:** stale after 6 months (market shifts)
- **Vision/mission:** relatively stable, 12+ months
- **Team/founding story:** stable unless major changes

When re-running the skill, prioritize re-scanning sections with MEDIUM/LOW confidence and sections where the original data is oldest.

---

## Research Notes Template

Use this structure for internal working notes during Phase 1. These notes are NOT part of the final artifact — they're your working material.

```markdown
## Research Notes: [Product Name]

### Source: [URL or description]
**Type:** [website/docs/review/press/social/user]
**Date accessed:** [date]
**Confidence:** HIGH / MEDIUM / LOW
**Key findings:**
- [finding 1]
- [finding 2]

**Quotes/evidence:**
- "[exact text]" — [page/section]

**Conflicts with other sources:**
- [note contradictions]

**Sections this informs:** [list section numbers]
```
