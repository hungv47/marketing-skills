# Communication Skills

Marketing communication skills — audience research, campaign planning, content creation, and performance attribution.

## Installation

```bash
npx skills add hungv47/comms-skills
```

## Skills

| Skill | Description |
|-------|-------------|
| `icp-research` | Deep audience research and Ideal Customer Profile development |
| `imc-plan` | Integrated Marketing Communication planning |
| `content-create` | Production-ready platform-native content with A/B variants and copy principles |
| `attribution` | KPI-initiative-content mapping and coverage audit |
| `lp-optimization` | High-conversion landing page optimization |
| `seo` | Technical audit, AI/GEO optimization, programmatic SEO, competitor pages |
| `humanize` | Strip AI patterns, inject voice, and compress content for density |

## Pipeline

```
icp-research → imc-plan → content-create → attribution
Horizontal: lp-optimization, seo, humanize
```

Artifacts save to `.agents/mkt/`.
Exception: `.agents/product-context.md` is saved to the shared cross-stack path (not `.agents/mkt/`).

## Cross-Stack Workflow

Attribution and IMC Plan can read strategy artifacts (`.agents/solution-design.md`, `.agents/targets.md`) from [strategy-skills](https://github.com/hungv47/strategy-skills).

## Usage

- "Research my ICP" → `icp-research`
- "Create an IMC plan" → `imc-plan`
- "Create content" → `content-create`
- "Write copy" → `content-create`
- "Map attribution" → `attribution`
- "Optimize landing page" → `lp-optimization`
- "SEO audit" → `seo`
- "Optimize for AI search" → `seo`
- "Build programmatic SEO pages" → `seo`
- "Humanize this" → `humanize`
- "Make this concise" → `humanize`
- "Remove AI patterns" → `humanize`

## License

MIT
