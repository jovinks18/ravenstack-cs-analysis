# Customer Health Framework
**RavenStack CS Operations • V1.0**

---

## Purpose

A consistent, transparent way to bucket accounts into **Green, Yellow, Red** so the CS team can prioritize effort, trigger plays, and surface risk to leadership — without ad-hoc judgment from individual CSMs.

---

## The five signals

The score combines five categories of customer behavior, each capturing a different dimension of relationship health.

| Signal | Weight | What it measures | Why it matters |
|---|---|---|---|
| **Usage trend** | 30% | % change in product usage, last 90d vs prior 90d | Declining usage is the leading indicator of disengagement |
| **Support burden** | 25% | Ticket volume, high-priority count, escalations, CSAT | Friction with the product or service signals risk |
| **Tenure & contract posture** | 20% | Tenure length, auto-renew status, downgrade history, renewal proximity | Commitment depth and renewal stage drive retention |
| **Engagement breadth** | 15% | Active days in last 90d | Single-user adoption is fragile; breadth = stickiness |
| **Commercial posture** | 10% | MRR level, upgrade history, prior churn events | Bigger and growing accounts deserve more investment |

---

## Scoring

Each signal scores 0–100. The composite is the weighted sum, also 0–100.

**Health buckets:**

| Bucket | Score | Meaning | CS action |
|---|---|---|---|
| 🟢 **Green** | 75+ | Healthy. Reference candidate. | Quarterly check-in. Expansion conversation. Advocacy ask. |
| 🟡 **Yellow** | 50–74 | Watch. Some signal of friction. | EBR within 30 days. Usage diagnostic. Success plan refresh. |
| 🔴 **Red** | <50 | At risk. Active intervention. | Exec sponsor outreach. Joint save plan. Decision in 30 days on save vs managed churn. |

---

## Worked example: Company_486 (A-d792a6)

| Component | Score | Why |
|---|---|---|
| Usage trend | 50/100 | -18% last 90d vs prior |
| Support | 80/100 | Low ticket volume, no recent escalations |
| Tenure & contract | 70/100 | 1.9 yrs, auto-renew on |
| Engagement | 15/100 | Only 6 active days of 90 — adoption gap |
| Commercial | 60/100 | Recent expansion offsets 2 prior churns |
| **Composite** | **57** | **Yellow** — requires EBR + adoption plan |

---

## Honest limitations

This is a v1. Three things a real production score would add:

- **Qualitative signals from CRM**: sponsor changes, M&A flags, competitive losses, exec sentiment from calls. These often matter more than telemetry.
- **Segment-specific weights**: Enterprise churn is procurement-driven (renewal stage matters most). SMB churn is engagement-driven (usage matters most). One weight set doesn't fit both.
- **Outcome-validated weights**: when this score was tested against historical churn in the RavenStack dataset, predictive lift was weak. In a real CS org, weights should be calibrated against churn outcomes quarterly, not designed in isolation.

---

## How to operationalize

1. **Score recalculation cadence:** weekly. Daily is overkill, monthly is too slow for renewal motions.
2. **Trigger automation:** when an account moves from Green → Yellow, auto-create a task for the CSM. When Yellow → Red, auto-notify the CSM's manager.
3. **Review cadence:** weekly CS team review of all Red accounts. Monthly review of Yellow trend (additions, exits, time-in-bucket).
4. **Override policy:** CSMs can override the bucket with documented reasoning. Overrides reviewed monthly to identify signal gaps the score is missing.