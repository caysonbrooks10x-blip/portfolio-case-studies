# Case Study: Customer Behavior Analysis for HealthBridge Platform

## The Client

HealthBridge Platform is a healthcare technology company operating a B2B2C network connecting patients, providers, and payers. Based in Boston with 280 employees, they process 2.3M patient appointments annually through their platform. After raising a $28M Series B, the new CEO demanded evidence-based decisions on product development and customer retention — not executive intuition.

## The Problem

HealthBridge had extensive data but no behavioral intelligence. They knew WHAT happened (appointment booked, claim submitted) but not WHY customers behaved the way they did. Product development was driven by anecdotal feedback. Customer success was reactive. Growth was stalling at 12% YoY when investors expected 30%+.

Specific pain points:
- **Activation rate of 34%** — only 1 in 3 new provider accounts became active users
- No understanding of which product features drove retention vs. churn
- Patient engagement dropped 60% after initial onboarding — no intervention strategy
- Customer success teams had no data on which accounts needed attention
- Product roadmap was built on "gut feel" rather than usage patterns
- Marketing campaigns were broad-reach with no personalization capability

## The Solution

I designed and implemented a comprehensive customer behavioral analytics system using Mixpanel for event tracking, BigQuery for data warehousing, and a combination of Jupyter notebooks for analysis and a Looker dashboard layer for operational visibility.

### Architecture

**Data Collection Layer:**
- Mixpanel SDK instrumentation across web, iOS, Android
- Server-side event tracking for API calls and claims processing
- CRM integration (Salesforce) for customer data enrichment
- Zendesk integration for support interaction data
- Custom data pipeline to BigQuery for ML workloads

**Analytics Infrastructure:**
- BigQuery for scalable query performance on event data
- dbt for customer journey transformation
- Jupyter notebooks for ad-hoc analysis and model development
- Looker for operational dashboards
- Census for reverse ETL to operational tools

**Behavioral Intelligence:**
- Cohort analysis framework
- Customer health scoring (engagement + outcome metrics)
- Feature adoption segmentation
- Predictive models for activation, engagement, churn
- Personalization recommendation engine

### Key Components

**1. Customer Journey Analytics**
- End-to-end journey mapping from signup → first appointment → ongoing usage
- Funnel analysis with 47 distinct conversion steps identified
- Drop-off point identification with root cause analysis
- Time-to-value tracking (days from signup to first successful action)

**2. Activation Intelligence**
- 14-point activation checklist with milestone tracking
- "Aha moment" identification: providers who complete 3 appointments in 14 days have 89% retention
- Automated in-app guidance for activation stalls
- CSM alerts when activation milestones are missed

**3. Engagement Scoring**
- Composite health score combining:
  - Login frequency (30% weight)
  - Feature breadth (25% weight)
  - Claim volume trend (20% weight)
  - Support burden (15% weight)
  - Clinical outcome metrics (10% weight)
- Segment tiers: Champions (80+), Healthy (60-79), At-Risk (40-59), Critical (<40)

**4. Retention Prediction**
- 90-day retention model using behavioral signals
- 23 features including login patterns, feature adoption, demographic factors
- Individual account risk scoring
- Intervention recommendation engine

### Key Behavioral Findings

Through analysis, we discovered insights that transformed product and growth strategy:

**Finding 1: The 14-Day Activation Window**
Providers who complete 3 appointments within 14 days of signup have 89% one-year retention. Those who don't hit this milestone have 23% retention. This led to:
- Automated onboarding sequence targeting this milestone
- CSM outreach for accounts at day 10 with 0-1 appointments
- Product changes to reduce friction to second appointment booking

**Finding 2: Feature Engagement Clusters**
Cluster analysis revealed 4 distinct usage patterns:
- **Power Users (12%)**: Use scheduling, billing, and analytics. 96% retention.
- **Basic Bookers (58%)**: Only scheduling. 78% retention.
- **Rare Users (22%)**: Monthly logins, low engagement. 56% retention.
- **Dormant (8%)**: No logins in 60+ days. 4% retention.

**Finding 3: The Week 4 Engagement Cliff**
Patient engagement drops 60% after week 4 regardless of appointment completion. This led to:
- Automated reminder sequences at week 3
- Proactive outreach programs
- New product features for between-appointment engagement

## The Results

**Before:**
- Activation rate: 34%
- One-year retention: 67%
- Time to first value: 18 days (median)
- Customer success model: Reactive
- Product decisions: Intuition-based

**After:**
- Activation rate: 71%
- One-year retention: 84%
- Time to first value: 7 days (median)
- Customer success model: Proactive with predictive scoring
- Product decisions: Data-driven with usage analytics

**Quantified Impact:**
- 37% improvement in activation rate (34% → 71%)
- 25% improvement in retention (67% → 84%)
- 61% reduction in time to first value (18 days → 7 days)
- 34% reduction in customer churn
- $4.2M in retained annual revenue from improved retention
- Product team now prioritizes features with 3x retention lift evidence

## Technical Deep Dive

### Mixpanel Implementation

We implemented comprehensive event tracking with 180 distinct events across 4 object types (Provider, Patient, Appointment, Claim). Key instrumentation principles:

**Naming Convention:** Object:Action (e.g., Provider:Login, Appointment:Booked, Claim:Submitted)

**Properties Captured:**
- User properties: role, specialty, years in practice, practice size, geography
- Event properties: duration, feature version, device type, referral source
- Context properties: time of day, day of week, appointment lead time

**Data Governance:**
- HIPAA-compliant data handling (no PHI in events)
- Data retention: 26 months for analysis
- De-identification pipeline for ML workloads

### Customer Health Score Model

The composite health score uses a weighted combination approach:

```
Health_Score = 0.30 × Engagement_Factor 
             + 0.25 × Feature_Adoption_Factor
             + 0.20 × Outcome_Factor
             + 0.15 × Support_Factor
             + 0.10 × Tenure_Factor
```

Each factor is normalized to 0-100 scale based on percentile distribution. Thresholds are calibrated quarterly against actual retention outcomes.

### Cohort Analysis Framework

We built a cohort analysis system that tracks 23 cohort dimensions:
- Acquisition channel
- Provider specialty
- Practice size
- Geography
- Product tier
- Onboarding completion status
- First appointment timing

Retention curves are generated for any cohort combination, enabling precise understanding of which factors drive long-term retention.

## Lessons Learned

1. **Instrument everything, analyze later**: We added 40 additional events in month 3 based on new questions. A flexible instrumentation strategy pays off.

2. **HIPAA constraints shape everything**: Healthcare analytics requires careful data handling. We built a de-identification layer for ML workloads that became a competitive advantage.

3. **Actionable insights require operational hooks**: Finding that "14-day activation" matters is useless if CSMs don't know which accounts are at day 10 with 0 appointments. We built the intervention workflows alongside the analysis.

4. **Behavioral segments beat demographic segments**: Demographic segments explained 12% of variance in retention. Behavioral clusters explained 67%. Focus on what people DO, not who they ARE.

## Client Testimonial

"Cayson transformed how we think about our customers. We went from gut-feel product decisions to evidence-based prioritization. Our activation rate doubled in 6 months. That's not incremental — that's transformational. We now have more visibility into our customer behavior than our competitors twice our size."

— Dr. Amanda Rodriguez, CEO, HealthBridge Platform

## About This Engagement

- **Duration**: 24 weeks (discovery through optimization)
- **Team**: 1 lead analyst, 1 data engineer, 1 product analyst
- **Investment**: $168,000 (implementation + Year 1 tooling)
- **Payback period**: 2.8 months (based on retained revenue)
- **Tools**: Mixpanel, BigQuery, dbt, Looker, Jupyter, Census, Salesforce, Zendesk
