---
name: ai-seo
description: "Optimize for AI search engines, get cited by ChatGPT/Perplexity/Claude/Gemini, AI SEO audit, LLM visibility, generative engine optimization — AI SEO, GEO, LLM optimization, AI citations, AI search visibility, generative search."
license: MIT
metadata:
  author: hungv47
  version: "1.0.0"
---

# AI SEO: Generative Engine Optimization

*Communicate Track — Horizontal skill. Optimizes content to be cited by AI search engines, not just ranked by traditional search.*

**Core Question:** "How do we get cited — not just ranked?"

Traditional SEO = ranked in search results. AI SEO = cited in AI-generated answers. These are different systems with different rules.

## Inputs Required
- ICP research from `.agents/mkt/icp-research.md` (audience questions and pain points)
- IMC plan from `.agents/mkt/imc-plan.md` (content pillars and angles)
- OR: User describes content/site to audit

## Output
- `.agents/mkt/ai-seo-audit.md`

## Quality Gate
Before delivering, verify:
- [ ] Every recommendation traces to a specific AI visibility principle (not generic SEO advice)
- [ ] Content structure audit covers all three pillars: Structure, Authority, Presence
- [ ] Platform-specific recommendations for ≥3 AI engines (not just "optimize for AI")
- [ ] FAQ passages are 40-60 words each (the citation-length sweet spot)
- [ ] No keyword stuffing recommendations (reduces AI visibility by ~10% per Princeton GEO study)

## Chain Position
Previous: `icp-research` + `imc-plan` (reads audience questions and content pillars) | Next: content production / site updates

Horizontal skill — can be invoked independently or after IMC planning.

---

## Before Starting

### Step 0: Product Context
Check for `.agents/mkt/product-context.md`. If available, read for product positioning context.

### Required Artifacts
| Artifact | Source | If Missing |
|----------|--------|------------|
| `icp-research.md` | icp-research | **RECOMMENDED.** Audience questions drive AI SEO strategy. Can proceed without, but audit will be less targeted. |

### Optional Artifacts
| Artifact | Source | Benefit |
|----------|--------|---------|
| `imc-plan.md` | imc-plan | Content pillars inform topic clusters |
| `product-context.md` | icp-research | Product positioning context |

---

## The Three Pillars of AI Visibility

### Pillar 1: Structure (Make Content Citable)

AI models extract and cite content that is structured for easy parsing.

**Content Structure Rules:**

| Rule | Why | How |
|------|-----|-----|
| Clear H2/H3 hierarchy | AI models parse headings to understand topic structure | Every section answers one specific question |
| 40-60 word answer passages | This is the citation-length sweet spot — long enough to be useful, short enough to be quoted in full | Write a concise answer paragraph immediately after each H2 |
| Comparison tables | Comparisons are the #1 most-cited content type (33% of AI citations) | Use markdown/HTML tables for feature comparisons, pricing tiers, tool comparisons |
| Structured data / Schema | Helps AI models (especially Google AI Overviews) parse content type | FAQ schema, How-To schema, Article schema |
| Source citations in content | Citing sources is the strongest single factor for AI visibility (Princeton GEO study) | Link to primary sources, studies, data — AI models prefer content that itself cites evidence |

**Most-Cited Content Types** (by share of AI citations):
1. **Comparisons** — 33% (X vs Y, best tools for Z, alternatives to W)
2. **How-to guides** — 15% (step-by-step instructions)
3. **Original research** — 12% (proprietary data, surveys, studies)
4. **Definitions/explainers** — 10% (what is X, how X works)
5. **Lists/roundups** — 8% (top N, best practices)

**Priority:** If you can only create one content type, create comparisons with original data.

### Pillar 2: Authority (Be Worth Citing)

AI models prefer citing sources they assess as authoritative. Authority signals differ from traditional backlink-based SEO.

**Authority Signals for AI:**

| Signal | Impact | Action |
|--------|--------|--------|
| Third-party mentions | Brands get cited 6.5x more via third-party sources than from their own content | Get mentioned in industry publications, review sites, expert roundups |
| Original data | AI models heavily cite proprietary data that can't be found elsewhere | Publish original research, surveys, benchmarks, case studies with specific numbers |
| Expert attribution | Named experts with credentials increase citation likelihood | Attribute content to real people with relevant expertise, not "the team" |
| Consistent entity presence | AI models build entity models from consistent information across sources | Ensure brand name, descriptions, and claims are consistent across all platforms |
| Review site presence | G2, Capterra, TrustRadius presence feeds AI training data | Actively manage review profiles — these get scraped into AI training |

**Key insight:** You cannot fully control AI citations through your own site. Third-party presence is more important than on-site optimization.

### Pillar 3: Presence (Be Findable by AI)

AI models have specific crawlers and data pipelines. You need to be in the corpus.

**AI Crawler Management:**

| Crawler | AI Engine | robots.txt Directive |
|---------|-----------|---------------------|
| GoogleOther | Google AI Overviews | `User-agent: GoogleOther` |
| GPTBot | ChatGPT | `User-agent: GPTBot` |
| ClaudeBot | Claude | `User-agent: ClaudeBot` |
| PerplexityBot | Perplexity | `User-agent: PerplexityBot` |
| Bingbot | Microsoft Copilot | `User-agent: Bingbot` |

**Decision:** Allow or block each crawler based on your strategy. If you want AI citations, you must allow the crawlers. If you block GPTBot, ChatGPT won't cite you.

**Platform-Specific Optimization:**

| Platform | How It Sources | Optimization Focus |
|----------|---------------|-------------------|
| **Google AI Overviews** | Traditional search index + structured data | Schema markup, featured snippet optimization, strong E-E-A-T |
| **ChatGPT (with browsing)** | Bing index + GPTBot crawl + training data | Third-party mentions, consistent entity info, original data |
| **Perplexity** | Own crawler + Bing + multiple sources | Source citations in content, comparison tables, structured answers |
| **Claude** | Training data + ClaudeBot crawl | Expert content, original research, third-party authority |
| **Gemini** | Google index + Knowledge Graph | Schema markup, Google Business Profile, entity consistency |

---

## Step 1: Audit Current AI Visibility

### Direct Testing
Search for your brand and key topics across AI platforms:
1. Ask ChatGPT: "What is [your product]?" and "Best [your category] tools"
2. Ask Perplexity: Same queries — note which sources it cites
3. Check Google AI Overviews: Search your primary keywords, note if you appear in AI summaries
4. Ask Claude: Same queries

**Document:**
- Are you mentioned? Cited? Linked?
- What are competitors doing that you're not?
- Which platforms cite you, which don't?
- What information about you is incorrect?

### Content Structure Audit
For your top 10 pages by traffic:
- [ ] Does each page have a clear H2/H3 hierarchy?
- [ ] Are there 40-60 word answer passages after major headings?
- [ ] Are comparison tables present where relevant?
- [ ] Does the content cite external sources?
- [ ] Is structured data (schema) implemented?

### Authority Audit
- [ ] Search "[your brand] review" — what third-party content exists?
- [ ] Check G2/Capterra/TrustRadius presence
- [ ] Search for brand mentions in industry publications
- [ ] Is content attributed to named experts?

### Crawler Audit
- [ ] Check robots.txt for AI crawler directives
- [ ] Verify sitemap is accessible and current
- [ ] Check server logs for AI bot activity

---

## Step 2: Build Citation-Optimized Content

### FAQ Optimization
For each audience question (from ICP research):
1. Write a direct, 40-60 word answer
2. Cite a source or provide original data
3. Use the question as an H2 or H3
4. Add FAQ schema markup

**Template:**
```
## [Exact question the audience asks]

[40-60 word direct answer with specific numbers or facts].
According to [source], [supporting evidence]. [One sentence on implications
or next steps].
```

### Comparison Content
For each competitor or alternative:
1. Create a structured comparison table
2. Include specific, verifiable differences
3. Be honest about competitor strengths (Pratfall Effect increases trust)
4. Cite third-party reviews as evidence

### Original Research
Publish proprietary data that AI models can't find elsewhere:
- Customer survey results with specific numbers
- Industry benchmarks from your user base
- Case studies with before/after metrics
- Trend analysis with original data

---

## Step 3: Build Third-Party Presence

Your own content is necessary but not sufficient. Third-party mentions are 6.5x more likely to be cited.

**Action plan:**
1. **Review sites:** Claim and optimize G2, Capterra, TrustRadius profiles
2. **Expert roundups:** Contribute to industry comparison articles
3. **Guest content:** Publish on authoritative industry sites
4. **PR/mentions:** Get covered in industry publications
5. **Community presence:** Answer questions on Reddit, Quora, Stack Overflow where your product is relevant (genuine help, not spam)

---

## Step 4: Technical Implementation

### Schema Markup Priority
1. **FAQ Schema** — for question-answer content
2. **How-To Schema** — for instructional content
3. **Article Schema** — for blog posts and guides
4. **Organization Schema** — for brand entity info
5. **Product Schema** — for product pages

### Crawler Configuration
Review and set robots.txt directives for each AI crawler based on your citation strategy.

### Monitoring
- Monthly: Re-test AI platform queries from Step 1
- Track which AI platforms cite you and for which queries
- Monitor AI crawler activity in server logs
- Track third-party mention growth

---

## Artifact Template

```markdown
---
skill: ai-seo
version: 1
date: [today's date]
status: draft
---

# AI SEO Audit

**Date:** [today]
**Skill:** ai-seo
**Product:** [from product-context.md]

## Current AI Visibility

| Platform | Mentioned? | Cited? | Accurate? | Notes |
|----------|-----------|--------|-----------|-------|
| ChatGPT | Y/N | Y/N | Y/N | [details] |
| Perplexity | Y/N | Y/N | Y/N | [details] |
| Google AI Overviews | Y/N | Y/N | Y/N | [details] |
| Claude | Y/N | Y/N | Y/N | [details] |
| Gemini | Y/N | Y/N | Y/N | [details] |

## Structure Audit

| Page | H2/H3 Hierarchy | Answer Passages | Comparison Tables | Source Citations | Schema |
|------|-----------------|----------------|-------------------|-----------------|--------|
| [URL/page] | Pass/Fail | Pass/Fail | Pass/Fail | Pass/Fail | Pass/Fail |

## Authority Audit

| Signal | Current State | Action Needed |
|--------|--------------|---------------|
| Third-party mentions | [count/quality] | [specific action] |
| Review site presence | [platforms] | [specific action] |
| Expert attribution | [Y/N] | [specific action] |
| Original data published | [Y/N] | [specific action] |

## Crawler Status

| Crawler | Currently Allowed? | Recommendation |
|---------|-------------------|----------------|
| GPTBot | Y/N | Allow/Block — [reason] |
| ClaudeBot | Y/N | Allow/Block — [reason] |
| PerplexityBot | Y/N | Allow/Block — [reason] |
| GoogleOther | Y/N | Allow/Block — [reason] |

## Priority Actions

| # | Action | Pillar | Impact | Effort |
|---|--------|--------|--------|--------|
| 1 | [action] | Structure/Authority/Presence | H/M/L | H/M/L |
| 2 | [action] | ... | ... | ... |

## Content Recommendations

### FAQ Passages to Create
| Question (from ICP) | Target Answer (40-60 words) | Source to Cite |
|---------------------|---------------------------|----------------|
| [question] | [answer draft] | [source] |

### Comparison Content to Create
| Comparison | Why (audience demand) | Key Differentiators |
|------------|----------------------|---------------------|
| [X vs Y] | [search volume / ICP evidence] | [your advantages] |

### Original Research Opportunities
| Topic | Data Source | Format |
|-------|-----------|--------|
| [topic] | [where data comes from] | Survey / Benchmark / Case Study |

## Next Step

Implement priority actions. Re-audit in 30 days to measure AI visibility changes.

> On re-run: rename existing artifact to `ai-seo-audit.v[N].md` and create new with incremented version.
```

---

## Anti-Patterns

**Keyword stuffing for AI** — Traditional keyword density tactics reduce AI visibility by ~10% (Princeton GEO study). AI models reward clear, well-structured answers over keyword-optimized text.

**Ignoring third-party presence** — Optimizing only your own site while ignoring review sites, industry publications, and community mentions. Third-party sources drive 6.5x more AI citations than direct content.

**Blocking AI crawlers then expecting citations** — If GPTBot is blocked in robots.txt, ChatGPT can't cite your content. Crawler access must match citation goals.

**Generic "optimize for AI" advice** — Each AI platform has different data sources and optimization levers. Google AI Overviews uses your search index presence; ChatGPT uses Bing + GPTBot; Perplexity uses its own crawler. Platform-specific strategies outperform generic ones.

**Treating AI SEO as a replacement for traditional SEO** — AI SEO is additive. Traditional search still drives the majority of traffic. AI SEO ensures you're also visible in the growing AI answer channel.

**Long, unstructured walls of text** — AI models extract specific passages. If your content doesn't have clear, self-contained answer blocks (40-60 words under descriptive headings), it's harder to cite even if the information is there.

---

## References

- [references/platform-guide.md](references/platform-guide.md) — Detailed optimization for each AI platform
- [references/content-templates.md](references/content-templates.md) — Templates for citation-optimized content types
