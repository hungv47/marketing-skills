# Marketing Skills

Brand identity, content creation, campaign planning, optimization, and performance attribution.

## Installation

```bash
npx skills add hungv47/marketing-skills
```

## Skills

| Skill | Description |
|-------|-------------|
| `brand-system` | Brand identity — strategy, personality, voice, visual identity, tokens |
| `imc-plan` | Integrated Marketing Communication planning |
| `content-create` | Production-ready platform-native content assets with A/B variants |
| `copywriting` | Craft-quality copy — headlines, hooks, CTAs, full-page copy with annotations |
| `lp-optimization` | High-conversion landing page optimization |
| `seo` | Technical audit, AI/GEO optimization, programmatic SEO, competitor pages |
| `attribution` | KPI-initiative-content mapping and coverage audit |
| `humanize` | Strip AI patterns, inject voice, and compress content for density |

## Pipeline

```
brand-system (visual identity)
imc-plan → content-create → attribution
Horizontal: copywriting, lp-optimization, seo, humanize
```

Artifacts save to `.agents/mkt/`.
Exception: `.agents/product-context.md` is saved to the shared cross-stack path (not `.agents/mkt/`).

## Cross-Stack Workflow

Attribution and IMC Plan can read strategy artifacts (`.agents/solution-design.md`, `.agents/targets.md`) from [research-skills](https://github.com/hungv47/research-skills).

## Usage

- "Define brand identity" → `brand-system`
- "Create an IMC plan" → `imc-plan`
- "Create content" → `content-create`
- "Write copy" → `copywriting`
- "Write headlines" → `copywriting`
- "Optimize landing page" → `lp-optimization`
- "SEO audit" → `seo`
- "Optimize for AI search" → `seo`
- "Map attribution" → `attribution`
- "Humanize this" → `humanize`
- "Remove AI patterns" → `humanize`

## License

MIT
