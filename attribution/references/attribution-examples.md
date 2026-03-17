# Attribution Mapping Examples

Worked examples of initiative-to-KPI and content-to-initiative attribution mapping.

---

## Example 1: B2B SaaS (Product-Led Growth)

### KPI Hierarchy

```
North Star: Monthly Active Users (MAU)
├── KPI 1: New Signups (Acquisition)
│   ├── Supporting: Organic traffic
│   └── Supporting: Signup page conversion rate
├── KPI 2: Activation Rate — % reaching "aha" moment in 7 days (Activation)
│   ├── Supporting: Onboarding completion rate
│   └── Supporting: Time to first value
├── KPI 3: Trial-to-Paid Conversion (Revenue)
│   ├── Supporting: Feature adoption depth
│   └── Supporting: Upgrade page views
└── KPI 4: Monthly Churn Rate (Retention)
    ├── Supporting: Weekly active usage
    └── Supporting: Support ticket volume
```

### Initiative-to-KPI Map

| Initiative | Primary KPI | Secondary KPIs | Expected Contribution | Confidence |
|------------|-------------|----------------|----------------------|------------|
| SEO content hub (30 articles) | New Signups | — | +800 signups/mo (25% of target) | M |
| Onboarding redesign | Activation Rate | Trial-to-Paid | +15pp activation (45% → 60%) | H |
| In-app upgrade prompts | Trial-to-Paid | — | +3pp conversion (8% → 11%) | M |
| Customer health scoring | Churn Rate | — | -1.5pp churn (5% → 3.5%) | L |
| Referral program | New Signups | Churn Rate (referrers churn less) | +400 signups/mo (12% of target) | L |

### Flags

**Orphan initiatives:** None — all map to KPIs.

**Uncovered KPIs:** Churn Rate has only 1 initiative (health scoring) at low confidence. Recommendation: add a retention-focused initiative (e.g., re-engagement email sequence).

### Content-to-Initiative Map

| Content | Initiative | Funnel Stage | Contribution Type |
|---------|-----------|--------------|-------------------|
| 30 SEO articles | SEO content hub | Awareness | Reach |
| 5 comparison pages | SEO content hub | Consideration | Trust |
| Interactive onboarding tutorial | Onboarding redesign | Activation | Conversion |
| "Getting Started" email sequence | Onboarding redesign | Activation | Conversion |
| 3 case studies | In-app upgrade prompts | Consideration | Trust |
| Monthly product newsletter | Customer health scoring | Retention | Retention |
| Referral landing page | Referral program | Acquisition | Conversion |

**Orphan content:** The company blog's weekly "industry news" posts don't support any initiative. Recommendation: either connect to SEO content hub strategy or reduce frequency.

### Coverage Analysis

| KPI | Initiatives | Content Pieces | Assessment |
|-----|-------------|----------------|------------|
| New Signups | 2 | 7 | Balanced |
| Activation Rate | 1 | 2 | Adequate (high-confidence initiative) |
| Trial-to-Paid | 1 | 3 | Adequate |
| Churn Rate | 1 | 1 | Under-covered — needs more |

---

## Example 2: Developer Tools (API Platform)

### KPI Hierarchy

```
North Star: Monthly API Calls
├── KPI 1: New Developer Signups (Acquisition)
│   ├── Supporting: Documentation page views
│   └── Supporting: Signup-to-first-call rate
├── KPI 2: API Integration Depth (Activation)
│   ├── Supporting: Endpoints used per account
│   └── Supporting: Time to first production call
├── KPI 3: Free-to-Paid Conversion (Revenue)
│   ├── Supporting: Usage approaching free tier limit
│   └── Supporting: Pricing page views
└── KPI 4: Monthly Developer Retention (Retention)
    ├── Supporting: Weekly active API callers
    └── Supporting: Support ticket resolution time
```

### Initiative-to-KPI Map

| Initiative | Primary KPI | Expected Contribution | Confidence |
|------------|-------------|----------------------|------------|
| Developer content hub (tutorials + guides) | New Developer Signups | +1,500 signups/mo | M |
| Hackathon sponsorship program | New Developer Signups | +800 signups/mo | M |
| Interactive API playground | API Integration Depth | +25pp activation (40% → 65%) | H |
| Usage-based upgrade nudges | Free-to-Paid Conversion | +4pp conversion (6% → 10%) | M |
| Developer community (Discord) | Monthly Developer Retention | -2pp churn (8% → 6%) | L |

### Flags

**Orphan initiatives:** None — all map to KPIs.

**Uncovered KPIs:** Monthly Developer Retention has only 1 low-confidence initiative (community). Recommendation: add a developer success initiative (e.g., proactive outreach when usage drops).

---

## Example 3: E-Commerce Brand (D2C)

### KPI Hierarchy

```
North Star: Monthly Revenue
├── KPI 1: New Customer Acquisition (volume)
│   ├── Supporting: Site traffic by channel
│   └── Supporting: New visitor conversion rate
├── KPI 2: Repeat Purchase Rate (retention)
│   ├── Supporting: Email list engagement
│   └── Supporting: Days between purchases
└── KPI 3: Average Order Value (value)
    ├── Supporting: Items per order
    └── Supporting: Upsell/cross-sell conversion
```

### Initiative-to-KPI Map

| Initiative | Primary KPI | Expected Contribution | Confidence |
|------------|-------------|----------------------|------------|
| Influencer seeding program | New Customer Acquisition | +15% new customers | M |
| UGC content strategy | New Customer Acquisition | +10% organic traffic | L |
| Post-purchase email flow | Repeat Purchase Rate | +8pp repeat rate | H |
| Loyalty/rewards program | Repeat Purchase Rate | +5pp repeat rate | M |
| Product bundling | Average Order Value | +$12 AOV | H |
| Free shipping threshold | Average Order Value | +$8 AOV | M |

### Coverage Analysis

| KPI | Initiatives | Assessment |
|-----|-------------|------------|
| New Customer Acquisition | 2 | Balanced but both at M/L confidence |
| Repeat Purchase Rate | 2 | Well-covered with 1 high-confidence |
| Average Order Value | 2 | Well-covered with 1 high-confidence |

**Balance:** Slightly bottom-heavy. Both acquisition initiatives are lower confidence. Consider adding a proven acquisition channel (e.g., paid social with clear ROAS targets).

### Content-to-Initiative Map

| Content | Initiative | Contribution Type |
|---------|-----------|-------------------|
| Influencer unboxing videos | Influencer seeding | Reach |
| Customer review campaigns | UGC strategy | Trust |
| "Complete your set" emails | Post-purchase flow | Conversion |
| Loyalty tier explanations | Loyalty program | Retention |
| "Frequently bought together" page modules | Product bundling | Conversion |
| Cart progress bar ("$15 away from free shipping") | Free shipping threshold | Conversion |

**Orphan content:** Seasonal lookbook content (published quarterly) doesn't map to any initiative. Either connect to acquisition or treat as brand investment and track accordingly.
