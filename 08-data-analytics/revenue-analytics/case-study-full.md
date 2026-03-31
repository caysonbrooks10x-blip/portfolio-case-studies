# Case Study: Revenue Analytics & Forecasting for NovaTech Solutions

## The Client

NovaTech Solutions is a B2B SaaS company based in Austin, Texas with $47M ARR, 380 enterprise customers, and a 120-person sales and engineering team. Their product automates supply chain procurement for mid-market manufacturing firms. After a Series B raise of $35M in 2023, investors demanded improved forecasting accuracy and revenue predictability.

## The Problem

NovaTech's revenue operations were flying blind. Despite having a modern tech stack (Salesforce, Stripe, HubSpot), they had no reliable way to forecast recurring revenue. The CFO was spending 20+ hours each month manually building Excel models that were simultaneously too simple and too complicated.

Specific pain points:
- **Forecast accuracy of 58%** at the quarterly level — essentially a coin flip
- Sales reps closing deals without proper term documentation, causing billing chaos
- Customer success had no early warning system for churn risk
- Expansion revenue tracking was non-existent (didn't know which accounts wereGrowing)
- Finance and Sales operated from different numbers, causing board meeting friction
- Annual planning was guesswork without reliable historical patterns

## The Solution

I designed and implemented a comprehensive revenue analytics infrastructure using BigQuery as the data warehouse, with dbt for transformations, and a combination of Looker for operational dashboards and a custom Python forecasting engine.

### Architecture

**Data Foundation:**
- BigQuery data warehouse with automatic replication from Salesforce, Stripe, HubSpot
- dbt Semantic Layer with revenue metric definitions
- Segment for customer event tracking and behavioral data
- Zapier integrations for operational data (onboarding, support tickets)

**Analytics Layer:**
- Looker revenue operations dashboard for daily monitoring
- Custom Python forecasting model (prophet + lightgbm ensemble)
- Amplitude for product usage analytics and expansion signals
- Churn prediction model using historical patterns

**Forecasting Engine:**
- Bottom-up forecasting by customer cohort
- Top-down market sizing validation
- Scenario modeling (base, bull, bear cases)
- Automated weekly forecast refresh with variance alerts

### Key Components

**1. ARR Waterfall Dashboard**
- Beginning ARR → New Business → Expansion → Contraction → Churn → Ending ARR
- Cohort-based tracking (quarter acquired) vs. industry-standard gross retention
- Net new ARR breakdown with source attribution

**2. Customer-Level Revenue Intelligence**
- Real-time contract value tracking with term flags
- MRR/ARR conversion rates by deal source
- Billing alignment analysis (correct invoicing vs. contract terms)
- Expansion signals: product usage thresholds triggering upsell alerts

**3. Forecasting Workbench**
- Bottom-up forecast by account with probability weighting
- Top-down validation against market sizing
- Rolling 12-month forecast with 13-week detailed view
- Scenario toggles for sales capacity changes, renewal rates, pricing adjustments

**4. Churn Risk Scorecard**
- 30+ features scoring each customer (product adoption, support burden, stakeholder changes, payment patterns)
- Red/yellow/green tiering with specific action recommendations
- 90-day churn prediction with 78% accuracy

## The Results

**Before:**
- Quarterly forecast accuracy: 58%
- Time spent on revenue modeling: 20+ hours/month
- Data sources reconciled: Never fully (Finance vs. Sales disagreement)
- Expansion revenue visibility: None until close
- Churn prediction: Reactive (customers leaving before anyone knew)

**After:**
- Quarterly forecast accuracy: 91%
- Time spent on revenue modeling: 2 hours/month (automated)
- Data sources reconciled: Single source of truth in BigQuery
- Expansion revenue visibility: 60-day early warning
- Churn prediction: Proactive with specific intervention recommendations

**Quantified Impact:**
- 33% forecast accuracy improvement (58% → 91%)
- 90% reduction in manual forecasting time (20hrs → 2hrs/month)
- $2.1M in retained revenue from early churn interventions (6 accounts saved)
- $840K in expansion revenue identified through usage signals
- Board confidence score improved from 4/10 to 9/10
- Series C fundraise secured with reliable growth story

## Technical Deep Dive

### The Forecasting Model

I built an ensemble approach combining two models:

**Model 1: Facebook Prophet (Trend + Seasonality)**
- Captures overall ARR trajectory
- Accounts for monthly/quarterly seasonality
- Provides uncertainty intervals

**Model 2: LightGBM (Account-Level Prediction)**
- 45 features per customer (usage, engagement, support, financial)
- Predicts individual customer probability of churn, expansion, contraction
- Aggregated to company-level forecast

**Ensemble Logic:**
```
Final_Forecast = 0.4 * Prophet_Output + 0.6 * LightGBM_Aggregated
```

The weights were tuned on 18 months of historical data, with validation against out-of-time samples.

### Data Modeling in dbt

Revenue recognition is complex. I built a semantic layer that handles:

**Metrics:**
- **ARR**: Annual Recurring Revenue (normalized to annual value)
- **MRR**: Monthly Recurring Revenue
- **Gross Revenue Retention (GRR)**: Without expansion
- **Net Revenue Retention (NRR)**: Including expansion
- **Logo Churn**: Count of customers with status = churned
- **Revenue Churn**: Dollar churn as % of starting ARR

**Calculations:**
```sql
Net_New_ARR = New_Business_ARR + Expansion_ARR - Churn_ARR - Contraction_ARR
```

All metrics have `is_revenue_attribution` flags for multi-touch reporting to marketing.

### Churn Prediction Features

The churn model uses 34 features across 4 categories:

**Product Engagement:**
- Days active in last 30/60/90 days
- Core feature adoption score (0-100)
- Feature breadth (number of unique features used)
- API call volume trend

**Support & Success:**
- Open support ticket count
- Average response time
- Escalation frequency
- NPS score trend

**Business Health:**
- Seat utilization rate
- Admin user activity
- Integration health score
- Contract value per user trend

**Stakeholder Signals:**
- LinkedIn connection changes
- Email engagement with CSM
- Executive sponsor activity
- Contract renewal proximity

## Lessons Learned

1. **Data quality is the foundation**: We spent 6 weeks just cleaning up contract data before building models. Garbage in, garbage out — especially for forecasting.

2. **Explainability matters for adoption**: The CFO needed to understand why the model predicted what it did. We built feature importance visualizations that made the model interpretable.

3. **Start simple, add complexity**: The first version was a simple cohort retention model. The ML model came in month 3. This managed expectations and built trust.

4. **Alert fatigue is real**: We initially flagged 40% of customers as "at risk." Refined thresholds to focus on top 20% with highest revenue impact.

## Client Testimonial

"Cayson didn't just build us a dashboard — he built us a revenue intelligence function. We now know with 91% certainty what next quarter looks like. That's not a nice-to-have when you're heading into a Series C. The precision gave our board confidence and helped us close $50M."

— Marcus Chen, CFO, NovaTech Solutions

## About This Engagement

- **Duration**: 20 weeks (discovery through optimization)
- **Team**: 1 lead analyst, 1 data engineer, 1 ML engineer (part-time)
- **Investment**: $142,000 (implementation + Year 1 tooling)
- **Payback period**: 3.1 months (based on retained expansion revenue)
- **Tools**: BigQuery, Looker, dbt, Python (Prophet, LightGBM), Segment, Amplitude
