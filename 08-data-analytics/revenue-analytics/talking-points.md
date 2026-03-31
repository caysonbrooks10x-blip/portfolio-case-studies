# Revenue Analytics — Talking Points

## Opening

"I specialize in helping SaaS companies understand their revenue with precision. I recently worked with a $47M ARR company whose CFO was essentially guessing — 58% forecast accuracy, 20 hours of monthly manual work, and zero visibility into churn or expansion."

"The first thing I tell prospects: you already have the data. You just don't have the infrastructure to act on it."

## Problem Framing

"Most SaaS companies have a data fragmentation problem. Salesforce has one view, Stripe has another, your CS tool has a third. Nobody agrees on what 'ARR' actually means."

"When your Finance team and Sales team have different numbers, you have a data problem — not a people problem. The solution isn't to have more meetings. It's to build one source of truth."

"Churn prediction is a classic 'too late' problem. By the time a customer says they're leaving, it's over. The signals are there months earlier — product usage dropping, support tickets increasing, stakeholders going quiet. You just need to connect the dots."

## Solution Highlights

"We built a revenue intelligence platform with four core components:

1. **Data Foundation**: BigQuery warehouse unifying all revenue sources — CRM, billing, product analytics, customer success. Single source of truth, automated refresh.

2. **Semantic Layer**: dbt models that define 'ARR,' 'NRR,' 'GRR' consistently. No more arguing about what the numbers mean.

3. **Forecasting Engine**: Ensemble model combining Prophet for trend/seasonality with LightGBM for account-level predictions. 91% quarterly accuracy.

4. **Churn Prevention**: 34-feature ML model scoring every customer. 78% accuracy on 90-day churn prediction. Gives CSMs specific actions, not just risk scores."

## Results That Resonate

"91% forecast accuracy — that's not a dashboard, that's strategic capability. When you know your number with 91% certainty, you can make real decisions."

"Weekly forecasting time dropped from 20 hours to 2 hours. The CFO told me she finally has time to actually analyze the business instead of just compiling data."

"6 accounts worth $2.1M in ARR were flagged as churn risk and intervention was initiated before it was too late. That's not analytics — that's revenue protection."

## Technical Depth (When Asked)

"The ensemble approach is key. Prophet captures macro trends and seasonality — it knows that Q4 is always strong because of budget cycles. LightGBM captures account-level signals — it knows Account #247 has a 73% chance of expanding because their admin user is suddenly very active and they've hit 80% of their seat limit."

"We trained on 18 months of historical data, validated on a 90-day out-of-time holdout. The 91% accuracy number is on real predictions, not backtesting."

"Data quality took 6 weeks to fix before we could even build models. Contract data was a mess — some deals were in Salesforce with annual values, some with monthly, some with multi-year terms. The dbt semantic layer normalizes all of this."

## Closing Questions

"What's your current forecast accuracy? If you don't know, that's your first problem."

"How much revenue did you lose last year to churn that might have been preventable with earlier warning?"

"If you could know with 90%+ certainty what next quarter's revenue would be, what decisions would change?"
