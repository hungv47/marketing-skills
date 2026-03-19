# Communication Skills

Marketing communication: audience research → campaign planning → content creation → attribution.

## Pipeline
icp-research → imc-plan → content-create → attribution
Horizontal: lp-optimization, seo, humanize, copywriting
Foundational: product-description, icp-research

## Recommended Starting Point
Run `product-description` or `icp-research` first — they are foundational "Step 0" skills:
- **`product-description`** when you need deep product intelligence (features, positioning, competitors, value props) → creates `.agents/mkt/product-description.md` and updates `.agents/product-context.md`
- **`icp-research`** when you need audience understanding (personas, pain points, habitats) → creates `.agents/mkt/icp-research.md` and `.agents/product-context.md`

Either can run first. Running both gives downstream skills the strongest foundation.

## Artifacts
Skills write to `.agents/mkt/`, except `product-context.md` which is cross-stack:
- `.agents/product-context.md` (cross-stack — shared with strategy, prod, and design skills)
- `.agents/mkt/product-description.md`
- `.agents/mkt/icp-research.md`
- `.agents/mkt/imc-plan.md`
- `.agents/mkt/content/[slug].md`
- `.agents/mkt/content/[slug].copy.md`
- `.agents/mkt/attribution.md`
- `.agents/mkt/seo-[mode].md` (mode = audit | ai | programmatic | competitor)
- `.agents/mkt/content/[slug].humanized.md`

## Cross-Stack (Optional)
Attribution and IMC Plan can read strategy artifacts for alignment:
- `.agents/solution-design.md` (from solution-design)
- `.agents/targets.md` (from funnel-planner)
`npx skills add hungv47/strategy-skills`
