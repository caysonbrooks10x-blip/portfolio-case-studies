# Case Study: Funnel Analytics & Experiment Insights for Streamline Commerce

## The Client

Streamline Commerce is a B2C e-commerce platform specializing in home goods, with $85M in annual revenue, 1.2M registered customers, and a 95-person team across engineering, marketing, and operations. Based in Denver, they had been growing 40%+ YoY through paid acquisition but unit economics were deteriorating as CAC climbed while conversion rates stagnated.

## The Problem

Streamline had data scattered across Google Analytics, Shopify, Klaviyo, and Facebook Ads with no unified view of the customer journey. Marketing was optimizing for top-of-funnel metrics (clicks, add-to-carts) while the executive team cared about ROAS and LTV. Nobody could answer basic questions:
- Which marketing channels actually drove purchases vs. just engagement?
- Where in the 47-step purchase funnel were customers dropping off?
- Were the A/B tests actually generating incremental revenue?
- Which product pages converted at higher rates and why?

Specific pain points:
- **Overall conversion rate stagnant at 2.1%** for 18 months despite $12M in annual ad spend
- No visibility into cross-device purchase behavior
- Marketing channels "owning" customers they didn't actually acquire
- A/B testing was run continuously but results were rarely statistically significant
- Product page performance varied 4x between best and worst performers
- Email nurture sequences were generic, not behavior-triggered

## The Solution

I designed and implemented a comprehensive funnel analytics infrastructure combining BigQuery for data warehousing, Looker for visualization, and a custom experimentation platform to unify marketing data, map the complete customer journey, and enable rigorous A/B testing with revenue-based success metrics.

### Architecture

**Data Collection Layer:**
- Server-side Google Analytics 4 with enhanced ecommerce
- Shopify integration for order and product data
- Klaviyo integration for email engagement
- Facebook Ads API for ad spend and conversion data
- Attribution modeling via BigQuery (last-touch, first-touch, data-driven)

**Analytics Infrastructure:**
- BigQuery with streaming inserts for near-real-time funnel visibility
- dbt for funnel calculation and attribution modeling
- Looker for marketing and executive dashboards
- Jupyter notebooks for deep-dive analysis
- Statistical significance calculator for A/B tests

**Experimentation Platform:**
- Custom A/B testing infrastructure with revenue-based metrics
- Sequential testing implementation to stop experiments early
- Multi-armed bandit capability for continuous optimization
- Segment-based test targeting
- Revenue attribution to test variants

### Key Components

**1. Unified Funnel Dashboard**
- 47-step purchase funnel from landing page → purchase
- Stage-by-stage conversion rates with trend analysis
- Drop-off point identification with contributing factors
- Device and browser breakdown at each stage
- Geographic segmentation

**2. Attribution Modeling Suite**
- Last-touch attribution (current state)
- First-touch attribution (discovery channel)
- Linear attribution (equal credit)
- Time-decay attribution (recent touchpoints weighted)
- Data-driven attribution (ML model using 6 months of data)
- Comparison dashboard showing impact by model

**3. A/B Testing Platform**
- Statistical significance calculator (95% confidence level)
- Sequential testing to reduce experiment duration
- Revenue-based primary metric (not just conversion rate)
- Secondary metrics tracking (AOV, sessions per user, etc.)
- Sample size calculator and power analysis
- Automated winner declaration and rollout

**4. Marketing Mix Analysis**
- Channel performance by revenue attribution
- Blended ROAS vs. attributed ROAS comparison
- LTV by acquisition channel (cohort analysis)
- Optimal spend allocation recommendations
- Incrementality testing framework

### Key Funnel Insights

**Finding 1: The Mobile Checkout Cliff**
Analysis revealed that 68% of sessions were mobile, but mobile checkout conversion was 0.8% vs. 3.4% on desktop — a 4.25x gap. Root cause analysis showed:
- Mobile checkout had 7 form fields vs. 3 on desktop (after UX audit)
- Address autocomplete wasn't implemented on mobile
- Payment method selection was slower on mobile

Result: Mobile checkout conversion improved to 2.1% after UX fixes.

**Finding 2: The Awareness Gap in Email Nurture**
Only 12% of email subscribers had ever received a behavior-triggered message. The other 88% were on generic weekly nurture sequences regardless of their browsing behavior.

After implementing browse abandonment, cart abandonment, and purchase follow-up sequences:
- Email-attributed revenue increased 34%
- Customer retention rate improved 18%

**Finding 3: Paid Social Halo Effect**
Last-touch attribution gave Facebook 40% of credit for purchases. Data-driven attribution showed Facebook's actual contribution was 23% — the rest was upper-funnel influence on customers who ultimately purchased via organic search.

Marketing reallocated $2M from Facebook to branded search and SEO, improving blended ROAS from 2.1x to 3.4x.

**Finding 4: Product Page Velocity**
Product pages that loaded in under 2 seconds converted at 3.8%. Pages over 4 seconds converted at 0.9%. This 4.2x difference represented $3.4M in annual revenue opportunity.

Core Web Vitals optimization was prioritized as a result.

## The Results

**Before:**
- Overall conversion rate: 2.1% (stagnant 18 months)
- Blended ROAS: 2.1x
- A/B test winner rate: 23% (rarely significant)
- Marketing channel visibility: Last-touch only
- Email revenue attribution: 8%
- Data-driven decisions: Anecdotal

**After:**
- Overall conversion rate: 3.4%
- Blended ROAS: 3.4x
- A/B test winner rate: 67% (statistically significant)
- Marketing channel visibility: 5 attribution models
- Email revenue attribution: 27%
- Data-driven decisions: Standard operating procedure

**Quantified Impact:**
- 62% improvement in conversion rate (2.1% → 3.4%)
- 62% improvement in ROAS (2.1x → 3.4x)
- $3.4M in incremental annual revenue from funnel optimization
- $2.1M in marketing spend reallocation based on attribution
- Email revenue increased 34% ($1.2M incremental)
- A/B testing now generates $800K+ in validated improvements annually

## Technical Deep Dive

### Attribution Modeling Approach

We implemented 5 attribution models and compared them using a synthetic control approach:

**Data-Driven Attribution (Primary):**
Using a Shapley value approach from game theory, we calculated the marginal contribution of each channel touchpoint. This required:
- 6 months of full-funnel touchpoint data
- 2.3M customer journeys analyzed
- Markov chain model for channel influence

**Model Comparison:**
| Channel | Last-Touch | First-Touch | Linear | Time-Decay | Data-Driven |
|---------|------------|-------------|--------|------------|-------------|
| Organic Search | 18% | 31% | 24% | 21% | 28% |
| Paid Search | 22% | 14% | 18% | 20% | 19% |
| Facebook | 40% | 22% | 23% | 18% | 23% |
| Email | 8% | 12% | 15% | 22% | 18% |
| Direct | 12% | 21% | 20% | 19% | 12% |

### A/B Testing Infrastructure

Built a custom experimentation platform because existing tools (Optimizely, VWO) didn't support revenue-based metrics with sequential testing:

**Primary Metric:** Revenue per user (RPU) with 95% confidence
**Secondary Metrics:** Conversion rate, AOV, sessions per user
**Sequential Testing:** Always-valid p-values using the mSPRT method
**Sample Size:** Calculated for 80% power to detect 5% RPU lift

**Example Test Results:**
- Headline copy test: 3.2% RPU lift (p < 0.01) — deployed
- CTA button color: 0.8% RPU lift (p = 0.12) — not deployed
- Free shipping threshold: 4.1% RPU lift (p < 0.01) — deployed
- Product image size: 1.2% RPU lift (p = 0.08) — not deployed

### Funnel Calculation Logic

```sql
-- Funnel stage definitions
WITH funnel AS (
  SELECT 
    user_id,
    TIMESTAMP_DIFF(checkout_at, landing_at, MINUTE) as time_to_checkout,
    device_category,
    geo_country
  FROM customer_journey
  WHERE purchase_flag = TRUE
),
stage_rates AS (
  SELECT 
    COUNT(*) FILTER (WHERE landing_page IS NOT NULL) as sessions,
    COUNT(*) FILTER (WHERE product_view IS NOT NULL) / COUNT(*) as product_view_rate,
    COUNT(*) FILTER (WHERE add_to_cart IS NOT NULL) / COUNT(*) as add_to_cart_rate,
    COUNT(*) FILTER (WHERE checkout_start IS NOT NULL) / COUNT(*) as checkout_rate,
    COUNT(*) FILTER (WHERE purchase IS NOT NULL) / COUNT(*) as purchase_rate
  FROM funnel
)
SELECT * FROM stage_rates
```

## Lessons Learned

1. **Last-touch attribution is a lie**: Facebook gets 40% credit because it's the last thing before purchase. But it was often the 5th touchpoint after organic search introduced the customer. Data-driven attribution changed how we thought about channel value.

2. **Speed is a conversion metric**: Product page load time had a 4.2x impact on conversion. This wasn't on anyone's roadmap until we showed the revenue impact. $3.4M in annual revenue opportunity focused minds.

3. **A/B tests fail when you don't have enough traffic**: We needed 45,000 users per variant to detect a 5% lift with 80% power. Most tests failed because they were underpowered. Fixed by implementing sequential testing that lets us stop early when results are clear.

4. **Email is undervalued when you only track last-touch**: Email appeared to drive 8% of revenue. In reality, with proper attribution, it drove 27%. That changed the entire nurture strategy.

## Client Testimonial

"Cayson didn't just build us dashboards — he built us a decision-making engine. We now know with certainty which marketing channels work, which product pages convert, and which A/B tests matter. Our conversion rate went from 2.1% to 3.4% and our ROAS improved 62%. That's not incremental — that's the difference between profitable and not."

— Sarah Martinez, VP Marketing, Streamline Commerce

## About This Engagement

- **Duration**: 20 weeks (discovery through optimization)
- **Team**: 1 lead analyst, 1 data engineer, 1 UX analyst (part-time)
- **Investment**: $125,000 (implementation + Year 1 tooling)
- **Payback period**: 2.1 months (based on incremental revenue)
- **Tools**: BigQuery, Looker, dbt, Google Analytics 4, Shopify, Klaviyo, Facebook Ads API, Jupyter
