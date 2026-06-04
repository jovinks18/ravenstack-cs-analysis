# RavenStack Customer Success Analysis
### A Customer Success operating framework built on B2B SaaS churn data

**Author:** Jovin
**Role focus:** Customer Success Manager / Customer Success Operations
**Time invested:** ~6 hours
**Dataset:** [RavenStack](https://www.kaggle.com/datasets/rivalytics/saas-subscription-and-churn-analytics-dataset) (synthetic B2B SaaS, multi-table) by Rivalytics on Kaggle

---

## 1. Why this project exists

Most "churn analysis" projects in CS portfolios are data science exercises wearing a CS costume: build a model, plot a confusion matrix, declare victory. That is not what a Customer Success Manager actually does.

This project answers the question a VP of Customer Success would actually ask on a Monday morning:

> *"We have $11.8M in active ARR across 500 accounts. How much of it is at risk in the next 90 days, which accounts are most exposed, what is actually causing customers to leave, and what should the CS team do about it?"*

The output is not a model. It is a decision-grade view of the customer book with an operating recommendation attached.

---

## 2. What I built

Four deliverables, each one usable by a different audience inside a SaaS company:

| Deliverable | Audience | Decision it supports |
|---|---|---|
| **Executive summary (1 page)** | CRO, CFO, CEO | Where is revenue exposed and what is the plan |
| **Customer Health Framework** | CS leadership, RevOps | How we score and segment accounts |
| **QBR deck (Company_486)** | CSM, account exec | How we run a real save/expansion conversation |
| **CS Operating Model recommendation** | Head of CS | How the team should be structured |

---

## 3. The thinking — frameworks applied

I deliberately leaned on three frameworks that are standard in mature CS organizations, rather than inventing methodology:

**a) The Green / Yellow / Red Health Model** — a weighted composite score across five signal categories (usage, support, tenure/contract, engagement, commercial posture). Used by virtually every B2B SaaS CS org from Gainsight and ChurnZero to in-house systems. Chosen because it's interpretable to non-technical executives and maps cleanly to playbooks.

**b) The Gross Revenue Retention (GRR) lens, not the logo retention lens.** A 5% logo churn rate is meaningless if it's your top 5 customers. Every analysis in this project is **revenue-weighted**, because that is how CS leaders think and how boards measure success.

**c) The "CS-addressable vs CS-influence-only" churn split.** Borrowed from how Head-of-CS roles actually divide their attention: separate the churn CS can directly stop (service quality, onboarding) from the churn CS can only influence (product, pricing). Forces an honest conversation about where CS effort should go.

---

## 4. The approach — what I did, in order

1. **Joined 5 raw tables** (accounts, subscriptions, feature usage, support tickets, churn events) into one account-level master view.
2. **Designed a v1 health score** with explicit weights *before* looking at outcomes, so the methodology was defensible rather than reverse-engineered.
3. **Stress-tested the score** against actual historical churn. The score showed weak predictive lift.
4. **Diagnosed why** rather than tweaking weights. Found that 85% of churned ARR was driven by reasons CS could not directly fix.
5. **Reframed the recommendation** around what the data actually said, including a 79% reactivation rate as the dataset's most striking and underused signal.
6. **Built a QBR for one real account** (Company_486 — a 3rd-cycle Enterprise customer with two prior churns) to demonstrate how the framework translates to operational work.

---

## 5. Headline findings

- **$11.8M active ARR, $3M historical churn.** Active book churn exposure: ~$4.5M weighted (Red + 50% Yellow).
- **85% of churned ARR is product/pricing/competitive — not CS-directly-addressable.** Pricing and budget alone account for 50% of churn.
- **The v1 behavioral health score failed validation.** Individual signals showed minimal lift between churned and retained accounts. The interpretation is not "the score is wrong" but "behavioral telemetry alone is insufficient for this book."
- **79% reactivation rate, $8M ARR recovered.** Customers churn and come back. This is currently accidental — it should be a defined CS program.
- **Tenured accounts churn more than new accounts** (371 vs 329 days). Renewal-stage intervention matters more than onboarding telemetry in this book.

---

## 6. Recommendations

1. **Reorient CS from saves to influence.** Treat the 15% CS-addressable churn as a playbook (service quality, onboarding). Treat the 85% non-addressable churn as an influence motion: deliver a quarterly **churn-evidence brief** to Product and Finance.
2. **Build a structured win-back program.** With a 79% reactivation rate, this is the highest-ROI motion available. Define plays, owners, and metrics.
3. **Segment-specific operating model.** Enterprise = relationship-managed (sponsor maps, exec syncs, quarterly business reviews). SMB = pooled CS + product-led signals.
4. **Renewal-stage CS, not lifecycle-stage CS.** Front-load CSM attention 90 days before renewal for tenured accounts. The data shows churn clusters at contract end, not at disengagement.

---

## 7. Honest limitations

- **The dataset is synthetic.** Behavioral signals are noisier than in a real production CS system. The methodology is the deliverable; the absolute numbers are illustrative.
- **No qualitative signals.** A real CS health score integrates CRM notes, sponsor changes, M&A flags, and competitive losses. None of those are in this dataset, which itself became part of the finding.
- **Reactivation flag is interpreted from event history.** The dataset doesn't explicitly label reactivated accounts; I derived this from churn events combined with current active status.
- **No NPS, no QBR cadence data, no contract terms detail.** Standard CS signals that would be in a real Gainsight/Salesforce setup.

---

## 8. Tech stack and why

- **Python (pandas, numpy)** — industry-standard for analyst-flavored CS work. Most CS Ops job specs list pandas as a nice-to-have. Choosing Python over Excel signals "I can scale this when the book is 5,000 accounts, not 500."
- **VS Code + Jupyter** — keeps the analysis reproducible and version-controlled. Hiring managers can clone the repo and re-run.
- **matplotlib + seaborn** — for static charts in the deck. Lightweight, no Tableau license needed, fully portable.
- **Markdown deliverables** — executive summary and framework are written so they could be lifted into Notion, Google Docs, or a real CS playbook with no rework.

I deliberately did *not* use ML libraries (scikit-learn, etc.) even though the dataset supports it. The point of this project is to demonstrate CS judgment, not modeling skill.

---

## 9. What I'd do next with more time

- **Cohort analysis** by signup month to find onboarding-cohort effects.
- **Tenure-stage health score** (different weights for <1yr vs >1yr customers).
- **Time-series visualization** of churn velocity and reactivation lag.
- **Build the win-back playbook** as a one-pager: triggers, plays, scripts, exit criteria.
- **Wire it into a real CS tool** (Gainsight, Catalyst, Vitally) to show how the framework operationalizes.

---

## Repository structure