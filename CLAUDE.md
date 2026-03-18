# Communication Skills

Marketing communication: audience research → campaign planning → content creation → attribution.

## Pipeline
icp-research → imc-plan → content-create → attribution
Horizontal: lp-optimization, seo, humanize

## Recommended Starting Point
Run `icp-research` first — it creates `.agents/product-context.md`, the canonical cross-stack artifact consumed by 12+ downstream skills across comms, strategy, prod, and design stacks.

## Artifacts
Skills write to `.agents/mkt/`:
- `.agents/product-context.md` (canonical cross-stack source — shared with strategy, prod, and design skills)
- `.agents/mkt/icp-research.md`
- `.agents/mkt/imc-plan.md`
- `.agents/mkt/content/[slug].md`
- `.agents/mkt/attribution.md`
- `.agents/mkt/seo-[mode].md` (mode = audit | ai | programmatic | competitor)
- `.agents/mkt/content/[slug].humanized.md`

## Cross-Stack (Optional)
Attribution and IMC Plan can read strategy artifacts for alignment:
- `.agents/solution-design.md` (from solution-design)
- `.agents/targets.md` (from funnel-planner)
`npx skills add hungv47/strategy-skills`