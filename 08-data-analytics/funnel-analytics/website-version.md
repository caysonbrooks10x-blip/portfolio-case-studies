# Funnel Analytics & Experiment Insights for E-commerce

## The Challenge

Streamline Commerce had $85M in revenue but no idea which marketing channels actually worked. Their conversion rate was stuck at 2.1% for 18 months. A/B tests rarely showed significance. Facebook was credited with 40% of revenue — but it was actually 23%.

## The Solution

Built comprehensive funnel analytics infrastructure combining BigQuery data warehouse, 5-model attribution suite, and a custom A/B testing platform with revenue-based metrics and sequential testing.

## Results

**62% Conversion Rate Improvement**
2.1% → 3.4% through UX fixes and optimization

**62% ROAS Improvement**
2.1x → 3.4x through attribution-informed spend reallocation

**3x Better A/B Test Success Rate**
23% → 67% of tests reaching statistical significance

**$4.67M Annual Revenue Impact**
From conversion improvement, attribution reallocation, and testing

**2.1 Month Payback**
On $125K implementation

## Key Discoveries

**Mobile Checkout Gap**: Mobile converted at 0.8% vs 3.4% desktop. UX fixes closed the 4.25x gap.

**Attribution Correction**: Facebook's true contribution was 23%, not 40% (last-touch inflated credit). Reallocated $2.1M.

**Email Undervalued**: Email attributed at 8% (last-touch) vs. 27% (data-driven). Triggered nurture overhaul.

## Technical Approach

- BigQuery streaming pipeline with unified customer journeys
- 5 attribution models (last-touch, first-touch, linear, time-decay, data-driven)
- Custom A/B testing with sequential testing (mSPRT)
- Revenue-based primary metrics (not vanity metrics)
- 47-step funnel with drop-off analysis

## Tools & Technologies

BigQuery | Looker | dbt | Google Analytics 4 | Shopify | Klaviyo | Facebook Ads API

## Client

> "Cayson didn't just build us dashboards — he built us a decision-making engine. Our conversion rate went from 2.1% to 3.4% and ROAS improved 62%. That's not incremental — it's the difference between profitable and not."
> — Sarah Martinez, VP Marketing, Streamline Commerce

## Engagement Details

- **Duration**: 20 weeks
- **Investment**: $125,000
- **Team**: 1 lead analyst, 1 data engineer, 1 UX analyst (PT)
