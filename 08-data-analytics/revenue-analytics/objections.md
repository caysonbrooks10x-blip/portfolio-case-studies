# Revenue Analytics — Objection Handling

## "Our data is too messy to build ML models."

That's exactly the starting point. Data cleaning isn't a prerequisite — it's 40% of the engagement.

I begin with a data audit that identifies:
- Schema inconsistencies across systems
- Contract term ambiguities
- Customer record duplicates or conflicts
- Historical data gaps

After this audit, we have a clear remediation roadmap. Most SaaS companies find 6-10 weeks of cleanup unlocks modeling capability. We do this work as part of the engagement — it's not preparatory, it's the first phase.

You can't build on garbage data. But you can clean the garbage.

---

## "We tried Salesforce/HubSpot reporting and it didn't work."

Native reporting tools are designed for operational workflows, not strategic analysis. They have:
- Limited historical depth
- No cross-system joining capability
- Inflexible metric definitions
- No forecasting functionality

What I build is a strategic analytics layer on top of your operational tools. Salesforce remains your CRM. It just becomes a data source, not the end-all be-all of revenue visibility.

---

## "How accurate is the churn prediction, really?"

Current accuracy: 78% on 90-day churn prediction.

That's based on:
- 90-day holdout test set (model didn't see this data during training)
- 34 features per customer
- 18 months of training data

The 22% false positive rate means some customers get intervention they didn't need. That's actually okay — proactive outreach is low-cost. The 22% miss rate is what we're continuously improving with model tuning.

Context: Without the model, churn was discovered when customers said "we're leaving." Now we have 60-90 days of early warning.

---

## "We already have a BI tool. Can't we just build dashboards?"

Dashboards show what happened. Forecasting predicts what will happen. These are fundamentally different capabilities.

A dashboard tells you churn was 3% last quarter. A forecasting model tells you which 12 customers are at 70%+ risk of churning next quarter and what specific actions would reduce that risk.

If dashboards were sufficient, your forecast accuracy would be better than 58%.

---

## "ML forecasting sounds black-box. How do we trust it?"

Valid concern. We built explainability into the model from day one:

- Feature importance visualization shows which signals drive each prediction
- Individual account predictions come with "reason codes" (top 3 factors)
- Weekly forecast reviews compare model vs. human adjustments
- Uncertainty intervals show confidence ranges, not just point estimates

The CFO initially questioned every number. Within 8 weeks, she was trusting the model over her Excel models because the model was consistently more accurate.

---

## "This sounds expensive for an early-stage company."

NovaTech was Series B with $47M ARR. If you're earlier stage with less ARR, we can scope appropriately:

Option A: Core foundation only ($80K) — BigQuery + dbt + basic dashboards, manual forecasting

Option B: Full platform ($142K) — Includes ML forecasting and churn prediction

Option C: Phased approach — Start with foundation, add ML in Phase 2 after you've proven ROI

The question isn't "can we afford this?" It's "can we afford 58% forecast accuracy and reactive churn?"

---

## "How long before we see results?"

Core infrastructure: 6 weeks
First dashboards: 8 weeks
Forecasting model live: 14 weeks
Validated accuracy: 20 weeks (need a quarter of real predictions to measure)

That's why we do backtesting on historical data to give you confidence immediately. The model's first quarter of real predictions confirms what backtesting showed.

---

## "Our CFO is resistant to 'black box' predictions."

I work directly with finance leaders to build explainability. The first 4 weeks include CFO workshops to:

- Explain model methodology in plain terms
- Show backtesting results with confidence intervals
- Establish a review process for forecast adjustments
- Create an audit trail for every forecast

The goal is to augment CFO judgment, not replace it. The model provides precision; the CFO provides context. Together, that's better than either alone.
