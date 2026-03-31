# Case Study: KPI Architecture for Scaling Business at Velocity Health

## The Client

Velocity Health is a Series B healthcare technology company with $38M in ARR, 180 employees, and a mission to modernize insurance prior authorization. After closing a $28M Series B, they were scaling rapidly — headcount growing 80% YoY, expanding into 3 new states, and preparing for a Series C in 18 months. The CEO recognized that as the company scaled, the old "everyone knows the numbers" startup culture wouldn't work. They needed a KPI architecture that could对齐 everyone's efforts and provide the board with consistent, reliable metrics.

## The Problem

Velocity was experiencing growing pains common to scaling startups:

- **No unified KPI framework**: Different teams used different definitions for basic metrics like "active user" or "prior auth completed"
- **Board packages took 3 days** to compile because finance was manually aggregating data from 5 systems
- **Engineers celebrated "shipped features"** while the business needed "revenue impact"
- **Sales team claimed 120% of quota** while finance showed 94% — same quarter, different numbers
- **No leading indicators**: Leadership only saw lagging metrics 2-4 weeks after the fact
- **Product roadmap disconnected** from business outcomes — teams optimized for output, not impact
- **OKRs felt arbitrary** because there was no data to validate whether objectives were achieved

## The Solution

I designed and implemented a comprehensive KPI architecture program that established company-wide metric definitions, built the data infrastructure to track them, created alignment frameworks for teams, and developed a governance model to maintain integrity as the company scales.

### Architecture

**Data Foundation:**
- Snowflake for metrics data warehouse
- dbt for metric calculations and transformations
- Looker for executive and team dashboards
- Fivetran for source system connectors (Salesforce, HubSpot, Zendesk, internal DB)
- Census for reverse ETL of calculated metrics to operational tools

**KPI Framework:**
- Executive Scorecard (12 metrics)
- Team-level dashboards (per team)
- OKR tracking integration
- Board reporting automation

**Governance:**
- Metric definitions document (single source of truth)
- Change management process for metric updates
- Data stewardship assignments
- Automated alerting on metric anomalies

### The KPI Framework

I designed a three-tier hierarchy:

**Tier 1: Company Metrics (The "True North")**
These 12 metrics define success for the entire company. Every employee should be able to explain how their work affects these metrics.

| Metric | Definition | Target | Current |
|--------|------------|--------|---------|
| ARR | Annual Recurring Revenue | — | $38M |
| Net New ARR | New ARR + Expansion - Churn | — | — |
| Gross Revenue Retention | % retained from prior period | > 90% | 91% |
| Net Revenue Retention | % retained + expansion | > 115% | 108% |
| CAC Payback | Months to recover CAC | < 18 | 16 |
| LTV:CAC | Lifetime value / CAC | > 3:1 | 2.8:1 |
| Magic Number | Net New ARR / S&M spend | > 1.0 | 0.9 |
| Burn Multiple | Net Burn / Net New ARR | < 1.5 | 1.8 |
| Rule of 40 | Growth % + Free Cash Flow % | > 40 | 35 |
| Time to First Value | Days from signup to value | < 30 | 42 |
| Product Qualified Leads | Leads with 10+ API calls | — | — |
| NPS | Net Promoter Score | > 50 | 47 |

**Tier 2: Team Metrics**
Each team has 5-8 metrics they directly influence. These metrics roll up to Tier 1.

- **Sales**: Pipeline coverage, win rate, average deal size, sales cycle length, quota attainment
- **Marketing**: MQLs, CAC, conversion rates, brand awareness, content ROI
- **Product**: Active users, feature adoption, NPS by feature, tech debt ratio, shipped value
- **Customer Success**: NRR, churn rate, CSAT, time to resolution, health score
- **Engineering**: Deployment frequency, incident rate, cycle time, code review time

**Tier 3: Operational Metrics**
Daily/weekly metrics that drive Tier 2. Used for tactical decisions.

- Daily signups, API call volume, support ticket volume, etc.

### Alignment Framework

**The "KPI Tree"**
Every team built a "KPI Tree" showing how their metrics connect to company metrics:

```
Company True North: NRR > 115%
    ↓
CS Team Metric: NRR = 108%
    ↓
CS Operational Metrics:
  - Churn Rate < 5%
  - Expansion Rate > 15%
  - Time to Value < 30 days
    ↓
CS Daily Actions:
  - At-risk account monitoring
  - Expansion outreach triggers
  - Onboarding check-ins
```

**OKR Integration**
Each Q1/Q2 OKR was required to have a metric connection:
- Objective: "Become the market leader in oncology prior auth"
  - KR1: Increase oncology MQLs by 40% (tied to Marketing metric)
  - KR2: Achieve 95% completion rate for oncology auths (tied to Product metric)
  - KR3: Reduce oncology churn to < 3% (tied to CS metric)

### Board Reporting Automation

I built an automated board package that pulled directly from the metrics warehouse:

- 12 slides generated from Looker
- Variance analysis (current vs. target vs. prior quarter)
- Cohort analysis included automatically
- ARR waterfall updated daily
- Burn rate tracking with scenario modeling
- Narrative draft generated from data

Board package creation: 3 days → 4 hours

## The Results

**Before:**
- Board package: 3 days to compile
- Metric definitions: Inconsistent across teams
- OKR validation: No data to validate achievement
- Leading indicators: None
- Sales/Finance alignment: 26% variance
- Product/business alignment: None

**After:**
- Board package: 4 hours (automated)
- Metric definitions: Unified company-wide
- OKR validation: Real-time progress tracking
- Leading indicators: 8 weeks ahead of results
- Sales/Finance alignment: < 2% variance
- Product/business alignment: KPI trees for all teams

**Quantified Impact:**
- Board package time: 72 hours → 4 hours (94% reduction)
- Finance team freed from manual reporting: 15 hours/week
- Decision-making speed: 40% faster (data-driven vs. debate)
- Sales/Finance alignment: 26% variance → < 2%
- Series C preparation: Clean data room enabled $45M raise
- 4.2 month payback period

## Technical Deep Dive

### Metric Calculation in dbt

I built a semantic layer in dbt that ensured consistent calculations:

```sql
-- Net Revenue Retention calculation
SELECT 
    account_id,
    period_start,
    period_end,
    SUM(arr) as starting_arr,
    SUM(CASE WHEN status = 'new' THEN arr ELSE 0 END) as new_arr,
    SUM(CASE WHEN status = 'expansion' THEN arr ELSE 0 END) as expansion_arr,
    SUM(CASE WHEN status = 'churn' THEN arr ELSE 0 END) as churn_arr,
    SUM(CASE WHEN status = 'contraction' THEN arr ELSE 0 END) as contraction_arr,
    -- NRR formula
    (SUM(arr) + SUM(expansion_arr) - SUM(churn_arr) - SUM(contraction_arr)) 
        / SUM(arr) * 100 as nrr_pct
FROM customer_arr_history
GROUP BY account_id, period_start, period_end
```

### Metric Anomaly Detection

For critical metrics, I implemented statistical anomaly detection:

```python
def detect_anomaly(metric_series, threshold=2.5):
    """
    Detect anomalies using rolling Z-score.
    Flag points where current value is > 2.5 std dev from rolling mean.
    """
    rolling_mean = metric_series.rolling(window=12).mean()
    rolling_std = metric_series.rolling(window=12).std()
    z_score = (metric_series - rolling_mean) / rolling_std
    
    return z_score.abs() > threshold
```

### The Metrics Governance Model

**Metric Review Board**
Quarterly review of all metrics with representatives from:
- Finance (revenue definitions)
- Product (usage definitions)
- Engineering (data infrastructure)
- Each business function (their metrics)

**Change Process**
1. Proposed change submitted to Metric Review Board
2. Impact analysis: How does this affect historical data?
3. Cross-functional review: Does this break any dependent metrics?
4. Approval: Finance + relevant function head
5. Implementation: dbt model update + documentation
6. Communication: All-hands announcement

## Lessons Learned

1. **Definitions are political**: "Active user" meant different things to different teams. We spent 3 weeks in working sessions to align. The goal isn't perfect definitions — it's agreed-upon definitions that everyone trusts.

2. **Leading indicators require hypothesis**: We identified 8 leading indicators for NRR, but only 3 proved statistically predictive. Building the framework is step 1. Validating the indicators is ongoing.

3. **Dashboards without governance rot**: Without the Metric Review Board, dashboards drift over time. Definitions change without documentation. We built governance into the architecture from day 1.

4. **Board packages are a forcing function**: Automating the board package was valuable not just for time savings — it forced us to make every metric auditable and explainable.

## Client Testimonial

"Cayson helped us scale with confidence. When you're 50 people, everyone knows the numbers. At 180 people, you need infrastructure. He built us a KPI architecture that对齐 everyone's work to a common definition of success. Our Series C data room was the cleanest the investors had seen. We closed $45M."

— Lisa Park, CEO, Velocity Health

## About This Engagement

- **Duration**: 20 weeks (discovery through optimization)
- **Team**: 1 lead analyst, 1 data engineer
- **Investment**: $95,000 (implementation + Year 1 tooling)
- **Payback period**: 4.2 months
- **Tools**: Snowflake, Looker, dbt, Fivetran, Census, Causal (OKR)
