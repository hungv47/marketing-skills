# Tracking Implementation Guide

Practical guidance for implementing the tracking that attribution mapping depends on.

---

## Event Naming Convention

Use `object_action` format consistently across all tracking:

| Pattern | Example | Anti-pattern |
|---------|---------|-------------|
| `object_action` | `user_signup_completed` | `signupComplete` |
| `object_action` | `page_viewed` | `PageView` |
| `object_action` | `trial_started` | `startTrial` |
| `object_action` | `feature_used` | `used_feature` |

**Rules:**
- Lowercase, underscore-separated
- Object first (what), action second (what happened)
- Past tense for completed actions (`completed`, `viewed`, `started`)
- Present tense for ongoing states (`active`, `loading`)

---

## Track for Decisions

Every tracked event should answer a specific question. If you can't name the question, don't track the event.

| Event | Question It Answers | Decision It Informs |
|-------|-------------------|-------------------|
| `user_signup_completed` | How many new users per day? | Is acquisition working? |
| `onboarding_step_completed` | Where do users drop off? | Which onboarding step needs fixing? |
| `feature_first_used` | Which features drive activation? | What to promote in onboarding? |
| `subscription_upgraded` | What triggers upgrades? | When to present upgrade prompts? |
| `support_ticket_created` | What causes friction? | Which features need improvement? |

**Anti-pattern:** Tracking everything "just in case." This creates noise, increases storage costs, and makes analysis harder. Track what you'll act on within 30 days.

---

## UTM Parameter Standards

For content attribution, use consistent UTM parameters:

```
utm_source = [platform] (e.g., linkedin, reddit, google)
utm_medium = [channel type] (e.g., organic, paid, email, referral)
utm_campaign = [campaign name] (e.g., status-waste, q1-launch)
utm_content = [content variant] (e.g., carousel-v1, thread-a)
utm_term = [keyword or angle] (optional — for paid search)
```

**Naming rules:**
- Lowercase, hyphen-separated
- No spaces, no special characters
- Consistent across all team members (document in a shared spreadsheet)

---

## Minimum Viable Tracking Stack

For teams starting from zero:

| Layer | Tool | What It Covers |
|-------|------|----------------|
| **Web analytics** | GA4 or Plausible | Page views, sessions, basic events |
| **Product analytics** | Mixpanel, Amplitude, or PostHog | User-level events, funnels, retention |
| **Attribution** | UTM parameters + GA4 | Content → conversion mapping |

Add more tools only when you have questions these three can't answer.

---

## Closing the Loop

Once tracking is implemented, re-run `attribution` to map content → conversion with real data instead of estimates.
