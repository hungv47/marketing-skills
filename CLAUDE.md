# Marketing Skills

Brand identity, content creation, campaign planning, optimization, and attribution.

## Pipeline
brand-system (visual identity foundation)
content-research (research-skills) → imc-plan → content-create → attribution
Horizontal: copywriting, lp-optimization, seo, humanize

## Recommended Starting Point
Run `icp-research` (from [research-skills](https://github.com/hungv47/research-skills)) first — it creates `.agents/product-context.md`, the canonical cross-stack artifact consumed by 12+ downstream skills.

## Artifacts
Skills write to `.agents/mkt/`, except `product-context.md` which is cross-stack:
- `.agents/product-context.md` (cross-stack — created by icp-research in research-skills)
- `.agents/mkt/icp-research.md`
- `.agents/mkt/content-research.md` (from content-research in research-skills)
- `.agents/mkt/imc-plan.md`
- `.agents/mkt/content/[slug].md`
- `.agents/mkt/content/[slug].copy.md`
- `.agents/mkt/attribution.md`
- `.agents/mkt/seo-[mode].md` (mode = audit | ai | programmatic | competitor)
- `.agents/mkt/content/[slug].humanized.md`
- `brand/BRAND.md` (brand narrative, voice, positioning, archetype)
- `brand/DESIGN.md` (AI-readable design system with palettes, tokens, components)

## Cross-Stack (Optional)
Attribution and IMC Plan can read research artifacts for alignment:
- `.agents/solution-design.md` (from solution-design in research-skills)
- `.agents/targets.md` (from funnel-planner in research-skills)
`npx skills add hungv47/research-skills`

## Multi-Agent Skills

All 8 skills use a two-layer multi-agent orchestration pattern:

- `SKILL.md` = **orchestrator** — dispatch graph, routing logic, merge step, critic gate
- `agents/` = **sub-agent instruction files** — each with role, input/output contracts, domain knowledge, self-check
- `references/` = **shared data catalogs** — formula lists, template libraries read by multiple agents

### How it works
1. Orchestrator gathers context (pre-writing, artifacts, brief)
2. **Layer 1** agents run in parallel — each writes one section independently
3. Orchestrator merges outputs into the artifact template
4. **Layer 2** agents run sequentially — each refines the full document through one lens
5. **Critic agent** scores the output and returns PASS or FAIL (max 2 rewrite cycles)

### Skills using this pattern
- `brand-system` — 8 agents (strategy, personality, voice, visual, token-architect, component-token, accessibility, critic). Layer 1 parallel (strategy + personality) → Layer 2 sequential (voice→visual→token-architect→component-token→accessibility→critic).
- `copywriting` — 9 agents (hook, body, CTA, social-proof, variant, voice, psychology, zero-risk, critic)
- `content-create` — 8 agents (format, voc-extraction, hook, body, CTA, platform-compliance, ab-variant, critic). Layer 1→1.5→2 pattern (format resolves first, then writers parallel).
- `imc-plan` — 6 agents (pillar, angle, channel, timeline, launch-sequencing, critic). Primarily sequential.
- `humanize` — 6 agents (pattern-scanner, voice-extractor, strip, soul-injection, compression, critic). Layer 1 parallel (scan + extract) → Layer 2 sequential (strip→inject→compress→critic).
- `lp-optimization` — 7 agents (hero-audit, trust-audit, cta-audit, ux-audit, message-match, prioritization, critic). Layer 1 parallel (4 audit agents) → Layer 2 sequential (message-match→prioritization→critic).
- `seo` — 11 agents across 4 modes (technical, AI, programmatic, competitor). Mode-based routing.
- `attribution` — 7 agents (kpi-hierarchy, initiative-mapper, channel-attribution, content-mapper, gap-analysis, action, critic). Fully sequential.

### Reusable template
`copywriting/agents/_template.md` defines the standard structure for agent instruction files.
