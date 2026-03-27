---
name: seo
description: "Audits and plans search visibility — keyword research, on-page optimization, technical SEO, link building strategy, and AI search optimization. Produces `.agents/mkt/seo-[mode].md`. Not for landing page conversion (use lp-optimization) or writing content (use content-create)."
argument-hint: "[url or mode]"
license: MIT
metadata:
  author: hungv47
  version: "2.0.0"
---

# SEO — Orchestrator

*Communication — Horizontal. Covers the full SEO surface: technical foundations, AI/generative engine optimization, programmatic page generation, and competitor comparison content.*

**Core Question:** "How do we get found — by both search engines and AI models?"

## Philosophy

SEO combines hard technical constraints (Google's CWV thresholds, character limits) with strategic judgment. This skill distinguishes between the two. Technical specs from platform documentation are constraints. Strategic recommendations are defaults with context for when to deviate.

---

## Critical Gates

Before delivering any SEO artifact, these must be true:

1. **Every recommendation has a specific fix.** No "consider improving" or "you might want to." If a finding cannot name the exact page, the exact change, and the expected impact, it is not ready.
2. **AI SEO is additive, not alternative.** Do the technical audit too. There is no point optimizing for AI citations if crawlers cannot reach your content.
3. **Source recency matters.** AI platform behavior changes fast. Verify all data and recommendations are current — not citing deprecated practices, outdated crawlers, or stale metrics.
4. **Mode is explicitly chosen based on diagnosis.** Not a generic "do SEO" deliverable.

---

## Agent Manifest

| Agent | File | Layer | Mode(s) | Focus |
|-------|------|-------|---------|-------|
| crawl-agent | `agents/crawl-agent.md` | 1 (parallel) | Technical Audit, Full | Crawlability, indexation, robots.txt, sitemaps, canonicals |
| foundations-agent | `agents/foundations-agent.md` | 1 (parallel) | Technical Audit, Full | CWV, mobile, HTTPS, URL structure, on-page optimization |
| content-quality-agent | `agents/content-quality-agent.md` | 1 (parallel) | Technical Audit, Full | E-E-A-T, thin content, duplicate detection, content gaps |
| authority-agent | `agents/authority-agent.md` | 1 (parallel) | Technical Audit, Full | Backlink profile, internal linking, link equity |
| ai-structure-agent | `agents/ai-structure-agent.md` | 1 (parallel) | AI SEO, Full | Schema, heading hierarchy, answer passages, structured data |
| ai-presence-agent | `agents/ai-presence-agent.md` | 1 (parallel) | AI SEO, Full | AI crawler access, llms.txt, citation monitoring, GEO |
| programmatic-template-agent | `agents/programmatic-template-agent.md` | 1 (parallel) | Programmatic | Template design, URL architecture, defensibility |
| programmatic-quality-agent | `agents/programmatic-quality-agent.md` | 1 (parallel) | Programmatic | Thin page detection, quality gates, monitoring plan |
| comparison-page-agent | `agents/comparison-page-agent.md` | 1 (parallel) | Competitor Pages | Page format, content architecture, comparison matrices |
| prioritization-agent | `agents/prioritization-agent.md` | 2 (sequential) | All | Impact x effort ranking of all findings |
| critic-agent | `agents/critic-agent.md` | 2 (sequential) | All | Quality gate — specific fixes, no vague language, actionability |

---

## Inputs Required

- ICP research from `.agents/mkt/icp-research.md` (audience questions, pain points, search behavior)
- IMC plan from `.agents/mkt/imc-plan.md` (content pillars and angles)
- OR: User describes their SEO situation / site to audit

## Output

- `.agents/mkt/seo-[mode].md` (mode = audit | ai | programmatic | competitor)

## Chain Position

Previous: `icp-research` + `imc-plan` (reads audience questions and content pillars) | Next: content production / site updates / `experiment` (to test SEO changes)

Horizontal skill — can be invoked independently or after IMC planning.

**Re-run triggers:** Technical audit quarterly, AI SEO monthly (AI landscape changes fast), after Google core updates, when entering new keyword territories.

### Skill Deference
- **Need production-quality copy for comparison pages?** → Run `content-create` after SEO defines the page structure and keyword targets.
- **Content pillar prioritization?** → Defer to `imc-plan` for audience-driven prioritization; SEO provides search demand data.

### Coordination with IMC Plan

When both `seo` and `imc-plan` are in use, they should coordinate:

| Situation | Who Leads | How They Coordinate |
|-----------|----------|-------------------|
| Content pillar has search demand | SEO leads topic selection | IMC provides angles and audience language; SEO provides keyword clusters and structure |
| Content pillar is novel/contrarian | IMC leads topic selection | IMC creates shareable content; SEO optimizes for related informational queries |
| Existing content needs both reach types | Both | Tag angles as Searchable/Shareable in IMC; SEO optimizes searchable angles for AI+traditional |
| Angles include competitor comparisons | IMC leads prioritization | IMC decides which comparisons to produce and when; SEO owns technical optimization (schema, structure, internal linking) of those pages |

**Rule:** Don't let SEO keyword data override IMC audience insights or vice versa. The best content addresses a real audience pain (IMC) AND has search demand (SEO). When they conflict, audience pain wins — you can promote great content through non-search channels, but you can't make irrelevant content convert even if it ranks.

---

## Before Starting

### Step 0: Product Context
Check for `.agents/product-context.md`. If available, read for product positioning context.
If `.agents/mkt/icp-research.md` or `.agents/mkt/imc-plan.md` `date` fields are older than 30 days, recommend re-running upstream skills — stale audience data weakens SEO strategy.

### Required Artifacts
| Artifact | Source | If Missing |
|----------|--------|------------|
| `icp-research.md` | icp-research | **RECOMMENDED.** Audience search behavior drives SEO strategy. Can proceed without, but recommendations will be less targeted. |

### Optional Artifacts
| Artifact | Source | Benefit |
|----------|--------|---------|
| `imc-plan.md` | imc-plan | Content pillars inform topic clusters |
| `product-context.md` | icp-research | Product positioning context |

---

## Routing Logic — Mode-Based Dispatch

### Step 1: Determine Mode

Not every SEO problem needs the same solution. Diagnose first, then enter the right mode.

| Situation | Mode | Route |
|-----------|------|-------|
| "Our site has technical issues / traffic dropped / we've never done an SEO audit" | **Technical Audit** | Route A |
| "We want to be cited by ChatGPT / Perplexity / AI search engines" | **AI SEO (GEO)** | Route B |
| "We have structured data and want to generate pages at scale" | **Programmatic SEO** | Route C |
| "We want to rank for competitor comparison queries" | **Competitor Pages** | Route D |
| "We need a comprehensive SEO strategy" | **Full SEO** (Technical + AI) | Route E |

Multiple modes can run sequentially. Start with Technical Audit if the site has never been audited — no point optimizing for AI citations if crawlers can't reach your content.

### Step 2: Dispatch per Route

**Route A — Technical Audit:**
```
Layer 1 (parallel): crawl-agent + foundations-agent + content-quality-agent + authority-agent
       ↓ merge
Layer 2 (sequential): prioritization-agent → critic-agent
```

**Route B — AI SEO:**
```
Layer 1 (parallel): ai-structure-agent + ai-presence-agent
       ↓ merge
Layer 2 (sequential): prioritization-agent → critic-agent
```

**Route C — Programmatic SEO:**
```
Layer 1 (parallel): programmatic-template-agent + programmatic-quality-agent
       ↓ merge
Layer 2 (sequential): prioritization-agent → critic-agent
```

**Route D — Competitor Pages:**
```
Layer 1: comparison-page-agent
       ↓
Layer 2 (sequential): prioritization-agent → critic-agent
```

**Route E — Full SEO (Technical + AI combined):**
```
Layer 1 (parallel): crawl-agent + foundations-agent + content-quality-agent + authority-agent + ai-structure-agent + ai-presence-agent
       ↓ merge
Layer 2 (sequential): prioritization-agent → critic-agent
```

---

## Dispatch Protocol

### Multi-Agent Dispatch (default)

1. **Gather context:** Read available artifacts (product-context, icp-research, imc-plan). Identify site type, CMS/framework, and known issues.
2. **Determine mode:** Apply the routing table from Step 1. If unclear, ask the user. If "comprehensive SEO," use Route E.
3. **Prepare pre-writing object:**
   ```
   {
     site_url: "[URL]",
     site_type: "[SaaS / E-commerce / Content-Blog / Local Business / Hybrid]",
     cms_framework: "[WordPress / Next.js / Webflow / etc.]",
     mode: "[audit / ai / programmatic / competitor / full]",
     known_issues: "[any issues the user mentioned]",
     icp_data: "[audience questions, pain points from icp-research if available]",
     competitors: "[competitor domains if available]",
     brand_name: "[brand name]",
     category: "[product category for AI search testing]"
   }
   ```
4. **Dispatch Layer 1 agents** in parallel with the pre-writing object and relevant reference file paths (resolved to absolute paths).
5. **Merge Layer 1 outputs** into the artifact template. Each agent's output maps to its designated sections.
6. **Dispatch prioritization-agent** with the merged document as upstream.
7. **Dispatch critic-agent** with the prioritized document as upstream.
8. **Apply critic verdict:**
   - PASS → deliver the artifact
   - FAIL → re-dispatch the named agents with the critic's feedback (max 2 cycles)

### Single-Agent Fallback

If multi-agent dispatch is unavailable, execute the full skill as a single agent:

1. Read this SKILL.md completely (including all referenced sections below)
2. Read the reference files for the active mode
3. Follow the mode's audit steps (documented in the Reference Knowledge sections below)
4. Apply the quality gate: every finding must have Issue, Impact, Evidence, Fix, and Priority
5. Produce the artifact using the template at the end of this file

---

## Layer 1: Mode-Specific Domain Knowledge

The following sections contain the domain knowledge that Layer 1 agents use. In multi-agent mode, each agent reads its own reference files. In single-agent fallback, read the sections relevant to the active mode.

### Technical Audit Domain (Route A)

Work top-down — lower layers depend on upper layers being healthy:

```
Layer 1: Crawlability & Indexation (can search engines find your pages?)
Layer 2: Technical Foundations (is the site fast, mobile-friendly, secure?)
Layer 3: On-Page Optimization (are pages targeting the right queries?)
Layer 4: Content Quality (is the content worth ranking?)
Layer 5: Authority & Links (does the site have external credibility?)
```

**Crawlability & Indexation — crawl-agent covers:**
- robots.txt verification (including AI crawler directives)
- XML sitemap existence, submission, and accuracy
- Orphan page detection
- Click depth (important pages within 3 clicks of homepage)
- Canonical tag correctness
- Duplicate content (www/non-www, HTTP/HTTPS, trailing slashes)
- Crawl budget waste (low-value pages)

**Technical Foundations — foundations-agent covers:**
- Core Web Vitals: LCP < 2.5s, INP < 200ms, CLS < 0.1 (Google's official thresholds)
- Mobile-friendly (responsive, touch targets >=44px)
- HTTPS everywhere
- URL structure (clean, lowercase, hyphenated)
- 404 handling and redirect chains
- On-page optimization (title tags, meta descriptions, heading hierarchy, images, internal links)
- Keyword cannibalization

**Content Quality — content-quality-agent covers:**
- E-E-A-T signal assessment (Experience, Expertise, Authoritativeness, Trustworthiness)
- Thin content detection
- Duplicate content analysis
- Content gap identification (vs. ICP research questions)

**Authority & Links — authority-agent covers:**
- Backlink profile quality and toxic link detection
- Internal linking architecture and topic clusters
- Link building opportunities

**Site-Type-Specific Issues:**

| Site Type | Watch For |
|-----------|----------|
| **SaaS** | Pricing page indexation, feature page cannibalization, documentation vs. marketing SEO conflict |
| **E-commerce** | Faceted navigation creating duplicate pages, out-of-stock page handling, product schema |
| **Content/Blog** | Thin content, category/tag page bloat, author page optimization |
| **Local Business** | Google Business Profile accuracy, NAP consistency, local schema |

**Schema detection caveat:** Web fetching / curl cannot reliably detect JSON-LD schema because CMS plugins (Yoast, AIOSEO, RankMath) often inject it via client-side JavaScript. Use Google Rich Results Test or browser DevTools to verify schema presence — don't flag missing schema based on raw HTML alone.

See [references/technical-audit.md](references/technical-audit.md) for the full audit report template.

### AI SEO Domain (Route B)

**The Three Pillars of AI Visibility:**

#### Pillar 1: Structure — ai-structure-agent covers

AI models extract and cite content that's structured for easy parsing.

| Rule | Why | How |
|------|-----|-----|
| Clear H2/H3 hierarchy | AI models parse headings to understand topic structure | Every section answers one specific question |
| 40-60 word answer passages | Citation-length sweet spot (adjust for complexity: 20-30 for definitions, 80-100 for technical) | Write a concise answer paragraph immediately after each H2 |
| Comparison tables | Comparisons are #1 most-cited content type (33% of AI citations) | Use tables for feature comparisons, pricing tiers, tool comparisons |
| Source citations in content | **Strongest single factor** for AI visibility — +40% citation boost (Princeton GEO study) | Link to primary sources, studies, data |
| Statistics in content | +37% citation boost | Include specific numbers, percentages, data points |

**Most-Cited Content Types:**
1. Comparisons — 33% (X vs Y, best tools for Z)
2. How-to guides — 15% (step-by-step instructions)
3. Original research — 12% (proprietary data, surveys)
4. Definitions/explainers — 10% (what is X, how X works)
5. Lists/roundups — 8% (top N, best practices)

**Princeton GEO Study — optimization impact on AI citations:**

| Optimization | Citation Impact |
|-------------|----------------|
| Citing sources | +40% |
| Including statistics | +37% |
| Including quotations | +30% |
| Authoritative tone | +25% |
| Clarity of writing | +20% |
| Technical terminology (appropriate) | +18% |
| Unique vocabulary | +15% |
| Fluency | +15-30% |
| Keyword stuffing | **-10%** (hurts) |

#### Pillar 2: Authority (Be Worth Citing)

| Signal | Impact | Action |
|--------|--------|--------|
| Third-party mentions | Brands cited 6.5x more via third-party sources than their own content | Get mentioned in industry publications, review sites, expert roundups |
| Original data | AI models heavily cite proprietary data | Publish original research, surveys, benchmarks with specific numbers |
| Expert attribution | Named experts increase citation likelihood | Attribute content to real people with credentials |
| Review site presence | G2, Capterra, TrustRadius feed AI training data | Actively manage review profiles |
| Wikipedia presence | 7.8% of ChatGPT citations come from Wikipedia | Contribute to relevant Wikipedia articles (following their guidelines) |

#### Pillar 3: Presence — ai-presence-agent covers

**AI Crawler Management:**

| Crawler | AI Engine | robots.txt Directive |
|---------|-----------|---------------------|
| GoogleOther | Google AI Overviews | `User-agent: GoogleOther` |
| GPTBot | ChatGPT | `User-agent: GPTBot` |
| ClaudeBot | Claude | `User-agent: ClaudeBot` |
| PerplexityBot | Perplexity | `User-agent: PerplexityBot` |
| Bingbot | Microsoft Copilot | `User-agent: Bingbot` |

Decision: If you want AI citations, allow the crawlers. If GPTBot is blocked, ChatGPT won't cite you.

**Platform-Specific Focus:**

| Platform | Data Source | Optimization Priority |
|----------|-----------|----------------------|
| Google AI Overviews | Traditional search index + schema | Schema markup, featured snippets, E-E-A-T |
| ChatGPT | Bing + GPTBot + training data | Third-party mentions, original data, entity consistency |
| Perplexity | Own crawler + Bing | Source citations in content, comparison tables, freshness |
| Claude | Training data + ClaudeBot | Expert content, balanced analysis, original research |
| Gemini | Google index + Knowledge Graph | Google Business Profile, YouTube, schema |

**AI SEO Validation Protocol:**

Baseline (before optimization):
1. Pick 10-20 queries: 5 brand, 5 category, 5 "how to" from ICP research
2. Run each across ChatGPT, Perplexity, Google AI Overviews, Claude
3. Score: 0 = not mentioned, 1 = mentioned not cited, 2 = cited with attribution
4. Record total baseline score

Post-optimization (re-test weekly for 4 weeks):

| Outcome | Interpretation | Action |
|---------|---------------|--------|
| Score improves >20% in 4 weeks | Optimization working | Continue and expand |
| Score flat after 4 weeks | Wrong target | Re-diagnose: Structure, Authority, or Presence? |
| Improves on some platforms, not others | Platform-specific gap | Focus on lagging platform's data source |
| Score decreases | Something broke | Check crawler access, content freshness, entity consistency |

See [references/ai-seo.md](references/ai-seo.md) for platform-specific optimization details and content templates.

### Programmatic SEO Domain (Route C)

**programmatic-template-agent covers template design; programmatic-quality-agent covers quality control.**

**When to Use pSEO:**

| Use When | Don't Use When |
|----------|---------------|
| You have structured data with many entities | You'd be creating thin pages with no unique value |
| Each page serves a distinct search intent | All pages would answer the same question |
| You can add unique value beyond the data | You're just spinning templates for indexed pages |
| Your data is defensible | The same data is freely available everywhere |

**Data Defensibility Hierarchy:**

| Tier | Data Type | Example | Defensibility |
|------|-----------|---------|---------------|
| 1 | **Proprietary** | Your own user data, benchmarks | Highest |
| 2 | **Product-derived** | Integration data, compatibility | High |
| 3 | **User-generated** | Reviews, community content | Medium |
| 4 | **Licensed** | Purchased datasets, API data | Low-medium |
| 5 | **Public** | Government data, free APIs | Lowest |

**Rule:** Tier 4-5 data needs exceptional template quality or proprietary enrichment.

**12 pSEO Playbook Patterns:**

| Pattern | Example | Search Intent |
|---------|---------|--------------|
| **Templates** | "[Tool] [use case] template" | Canva's templates, Notion templates |
| **Curation** | "Best [category] in [city]" | NomadList, Yelp |
| **Conversions** | "[Unit A] to [Unit B]" | Wise currency pages |
| **Comparisons** | "[Tool A] vs [Tool B]" | G2 comparison pages |
| **Examples** | "[Type] examples" | Dribbble, Behance |
| **Locations** | "[Service] in [City]" | Thumbtack, Yelp |
| **Personas** | "[Tool] for [role/industry]" | Monday.com's use-case pages |
| **Integrations** | "[Your tool] + [Other tool]" | Zapier's integration pages |
| **Glossary** | "What is [term]" | HubSpot's glossary |
| **Translations** | "[Phrase] in [language]" | Google Translate pages |
| **Directory** | "[Category] companies/tools" | ProductHunt, G2 |
| **Profiles** | "[Entity] overview/stats" | CrunchBase, LinkedIn |

**pSEO Quality Requirements (every page must pass):**
- [ ] Unique value test: offers something no other page on the site provides
- [ ] Search intent match: answers what the searcher actually wants
- [ ] Heading hierarchy: proper H1/H2/H3 structure
- [ ] Schema markup: appropriate structured data
- [ ] Internal linking: connected to hub and related pages
- [ ] Indexation strategy: only index pages meeting quality bar

See [references/programmatic-seo.md](references/programmatic-seo.md) for template patterns and implementation guide.

### Competitor Pages Domain (Route D)

**comparison-page-agent covers page format selection, content architecture, and competitive positioning.**

**Four Page Formats:**

| Format | URL Pattern | Search Intent | Example |
|--------|------------|--------------|---------|
| **Singular alternative** | `/alternatives/[competitor]` | "I want to leave [competitor]" | `/alternatives/salesforce` |
| **Plural alternatives** | `/[competitor]-alternatives` | "What are my options?" | `/salesforce-alternatives` |
| **Direct comparison** | `/vs/[competitor]` | "How does [us] compare?" | `/vs/salesforce` |
| **Third-party comparison** | `/[comp-a]-vs-[comp-b]` | "Which is better, A or B?" | `/salesforce-vs-hubspot` |

**Priority:** Direct comparison for top 3 competitors first. Then alternatives. Third-party only if you have authority.

**Content Architecture (essential sections per page):**
1. TL;DR summary — 40-60 word direct answer (AI-citable)
2. Comparison table — specific, verifiable features (not vague "better UX")
3. Category breakdown — compare by use case, not just feature list
4. Audience segmentation — "Choose [them] if... Choose [us] if..."
5. Migration guidance — how to switch, with social proof
6. Honest assessment — acknowledge competitor strengths (Pratfall Effect builds trust)

**Internal Linking (hub-and-spoke):**
- Hub: `/alternatives` or `/compare` (links to all comparison pages)
- Spokes: individual comparison pages (link back to hub + related comparisons)
- Cross-links: each comparison page links to 2-3 related comparisons

**Update Cadence:**
- Quarterly: verify competitor pricing and feature changes
- Annually: full content refresh
- Triggered: competitor launches major feature or changes pricing

See [references/competitor-pages.md](references/competitor-pages.md) for content templates and keyword targeting.

---

## Layer 2: Prioritization and Critic

### Prioritization (all modes)

The **prioritization-agent** takes all Layer 1 findings and produces a single ranked action plan:

1. **Quick Wins** (High Impact, Low Effort) — execute first
2. **Strategic Investments** (High Impact, High Effort) — plan for next
3. **Low-Hanging Fruit** (Medium Impact, Low Effort) — fill gaps
4. **Backlog** (Low Impact or High Effort) — defer

Implementation phases with timelines: Phase 1 (Week 1-2), Phase 2 (Month 1), Phase 3 (Month 2-3), Phase 4 (Ongoing).

Dependencies are mapped — no action recommended before its prerequisite.

### Critic Gate (all modes)

The **critic-agent** evaluates the full document against these standards:

- Every finding has Issue, Impact, Evidence, and Fix
- Every Fix is specific enough to implement without further research
- No vague language: "consider," "might want to," "could potentially"
- Actions are force-ranked (not flat "High priority" lists)
- Mode-appropriate coverage is complete
- Technical specs reference correct thresholds

**Verdict:** PASS or FAIL (binary — no conditional pass).
**Max cycles:** 2 rewrites. If the document fails after 2 cycles, deliver with a note explaining what remains unresolved.

On FAIL, the critic names which agent to re-dispatch with specific fix instructions.

---

## Artifact Template

```markdown
---
skill: seo
mode: [audit | ai | programmatic | competitor]
version: 1
date: [today's date]
status: draft
---

# SEO: [Mode Name]

**Date:** [today]
**Skill:** seo
**Mode:** [Technical Audit | AI SEO | Programmatic SEO | Competitor Pages]
**Product:** [from product-context.md]

## Diagnosis

[Why this mode was chosen. What's the current situation?]

## Findings

[Mode-specific findings from Layer 1 agents — merged by section]

### [Section from Agent 1]
[Agent 1's findings]

### [Section from Agent 2]
[Agent 2's findings]

[Continue for all Layer 1 agents in the active mode]

## Priority Actions

| # | Action | Category | Impact | Effort | Timeline |
|---|--------|----------|--------|--------|----------|
| 1 | [action] | Quick Win | H | L | [timeline] |
| 2 | [action] | Strategic | H | H | [timeline] |

## Implementation Plan

### Phase 1: Immediate (Week 1-2)
[Quick wins]

### Phase 2: Short-term (Month 1)
[Strategic investments]

### Phase 3: Medium-term (Month 2-3)
[Remaining items]

### Phase 4: Ongoing
[Maintenance and monitoring]

## Dependencies

| Action | Depends On | Why |
|--------|-----------|-----|
| [action] | [prerequisite] | [reason] |

## Metrics to Track

| Metric | Current | Target | Check Frequency |
|--------|---------|--------|----------------|
| [metric] | [value] | [value] | [frequency] |

## Next Step

[What to do after implementing — re-audit timeline, experiment to run, etc.]

> On re-run: rename existing artifact to `seo-[mode].v[N].md` and create new with incremented version.
```

---

## Worked Example: Technical Audit (Route A)

**Scenario:** SaaS company, Next.js site, first SEO audit. User says "Our organic traffic dropped 30% last quarter."

**Step 1: Mode determination** → Technical Audit (traffic drop + never audited = Route A)

**Step 2: Context gathering**
```
pre-writing: {
  site_url: "https://example.com",
  site_type: "SaaS",
  cms_framework: "Next.js",
  mode: "audit",
  known_issues: "30% organic traffic drop last quarter",
  icp_data: "from .agents/mkt/icp-research.md",
  competitors: ["competitor-a.com", "competitor-b.com"]
}
```

**Step 3: Layer 1 dispatch (parallel)**

*crawl-agent finds:*
```
- Issue: robots.txt line 8 blocks /resources/ (47 indexed guides)
- Impact: 47 guide pages deindexed, ~2,300 sessions/month lost
- Fix: Replace Disallow: /resources/ with Disallow: /resources/internal/
- Priority: Critical
```

*foundations-agent finds:*
```
- Issue: LCP is 4.2s on /pricing (hero image 2.4MB PNG)
- Impact: Fails CWV (threshold: <2.5s), poor mobile experience on highest-intent page
- Fix: Convert hero.png to WebP via next/image, add priority loading. Expected: ~180KB, LCP <2s.
- Priority: Critical
```

*content-quality-agent finds:*
```
- Issue: 23 integration pages average 142 words unique content each
- Impact: Helpful Content Update risk — thin pSEO pages can drag down domain quality
- Fix: Add 2-3 unique workflows + setup steps per integration page. Target 600+ unique words.
- Priority: High
```

*authority-agent finds:*
```
- Issue: /pricing has 0 internal links from blog posts (12 posts mention pricing)
- Impact: Highest-intent page has no internal link equity from content
- Fix: Add contextual links to /pricing from 12 blog posts that mention pricing
- Priority: Medium
```

**Step 4: Merge + prioritization-agent**

Quick Wins:
1. Fix robots.txt /resources/ block (Critical, 5 minutes)
2. Add internal links to /pricing from 12 blog posts (Medium impact, 2 hours)

Strategic Investments:
3. Convert hero images to WebP across site (Critical, 1-2 days)
4. Enrich 23 integration pages with unique content (High, 2-3 weeks)

**Step 5: critic-agent evaluates** → PASS (every finding has specific fix, no vague language, priorities are ranked)

**Step 6: Deliver** `.agents/mkt/seo-audit.md`

---

## Anti-Patterns

**"Do SEO" without diagnosis** — Running a generic checklist without determining whether the problem is technical, content, authority, or AI visibility. Different problems need different modes.
INSTEAD: Diagnose first using the routing table. Ask the user what triggered the SEO request.

**Keyword stuffing (traditional or AI)** — Reduces AI visibility by ~10% (Princeton GEO study) and triggers Google's spam detection.
INSTEAD: Write for humans, structure for machines. Use natural language headings that match audience questions.

**pSEO as a content farm** — Generating thousands of thin pages with no unique value per page. Google's Helpful Content Update specifically targets this.
INSTEAD: Better to have 100 great pages than 10,000 thin ones. Apply the 60% uniqueness threshold.

**Ignoring third-party presence for AI SEO** — Optimizing only your own site while ignoring review sites and publications. Third-party sources drive 6.5x more AI citations.
INSTEAD: Build G2/Capterra profiles, pursue industry mentions, manage review responses.

**Blocking AI crawlers then expecting citations** — If GPTBot is blocked in robots.txt, ChatGPT can't cite your content.
INSTEAD: Audit robots.txt for all 5 AI crawler directives. Allow crawlers for platforms where you want citations.

**Flat competitor comparison tables** — Listing features with checkmarks tells the reader nothing about context.
INSTEAD: Compare by use case and audience. Every cell has specific data, not checkmarks.

**Schema false positives** — Flagging missing schema based on raw HTML when CMS plugins inject JSON-LD via client-side JavaScript.
INSTEAD: Verify schema with Google Rich Results Test or browser DevTools.

**One-and-done audits** — SEO is ongoing. Technical issues resurface, competitors change, algorithms update.
INSTEAD: Set re-audit cadence: quarterly for technical, monthly for AI visibility.

**"Consider improving" recommendations** — Vague hedge language that gives the reader nothing to act on.
INSTEAD: Every recommendation names the exact page, the exact change, and the expected impact.

---

## References

- [references/technical-audit.md](references/technical-audit.md) — Full audit report template and detailed checklists
- [references/ai-seo.md](references/ai-seo.md) — Platform-specific AI optimization and content templates
- [references/programmatic-seo.md](references/programmatic-seo.md) — pSEO template patterns and implementation
- [references/competitor-pages.md](references/competitor-pages.md) — Comparison page templates and keyword targeting
- [references/schema-reference.md](references/schema-reference.md) — Schema types, implementation contexts, and validation
