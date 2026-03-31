# Funnel Analytics — Talking Points

## Opening

"I help e-commerce companies understand their customer journey from first click to final purchase. I recently worked with an $85M brand whose conversion rate had been stuck at 2.1% for 18 months. They had data — it was just useless because nobody could connect marketing spend to revenue."

"The core problem was attribution. They were making $12M/year in marketing decisions based on last-touch attribution, which is essentially fiction."

## Problem Framing

"Last-touch attribution gives 100% credit to the last channel before purchase. If someone clicks a Facebook ad, Googles your brand, and then buys directly, Facebook gets 100% of the credit."

"Facebook doesn't drive purchases — it drives awareness. Email nurtures. Organic search converts. But last-touch says Facebook is king, so they got 40% of the budget."

"This isn't a minor accounting issue. It's a $2M/year misallocation problem."

"Meanwhile, their conversion rate was stuck because nobody knew where the funnel broke. They had 47 steps from landing page to purchase. Which ones were dropping? Mobile vs. desktop? Product page to cart? Cart to checkout?"

## Solution Highlights

"We built a complete funnel analytics and experimentation infrastructure:

1. **Unified Data Layer**: BigQuery warehouse combining Google Analytics 4, Shopify, Klaviyo, Facebook Ads. Every customer journey in one place.

2. **Funnel Intelligence**: 47-step funnel mapped with stage-by-stage conversion rates. We found the mobile checkout cliff — mobile converted at 0.8% vs. 3.4% on desktop.

3. **Attribution Suite**: 5 different attribution models. Data-driven attribution using Markov chains and Shapley values. Suddenly you know which channels ACTUALLY drive purchases.

4. **Experimentation Platform**: Custom A/B testing with revenue-based primary metrics and sequential testing. 67% of tests now reach significance vs. 23% before."

## Results That Resonate

"Mobile checkout was a disaster. 68% of sessions were mobile but conversion was 0.8% vs. 3.4% desktop. Why? Seven form fields on mobile vs. three on desktop. Slow address autocomplete. We found it in 2 hours of analysis. UX fixes recovered $3.4M annually."

"Facebook's actual contribution was 23%, not 40%. We reallocated $2.1M to organic search and email. ROAS improved from 2.1x to 3.4x."

"Email was driving 27% of revenue, not 8%. Once we showed this, they invested in behavior-triggered nurture sequences. Email revenue up 34%."

## Technical Depth (When Asked)

"Data-driven attribution uses a Shapley value approach from game theory. We calculate the marginal contribution of each channel by simulating what happens when you remove each channel from the journey. It's computationally expensive — 2.3M customer journeys — but the accuracy is worth it."

"Sequential testing uses the mSPRT (mixture Sequential Probability Ratio Test) method. Instead of waiting for a fixed sample size, you can stop early when results are clearly positive or negative. This reduced average test duration from 6 weeks to 3 weeks while maintaining 95% confidence."

"The funnel calculation uses a state machine approach. Each user journey is a sequence of events. We match these against funnel stage definitions and calculate conversion rates at each stage. The beauty is it handles multi-session journeys — someone might browse on Monday, abandon, and return Thursday."

## Closing Questions

"What's your current conversion rate? Do you know why it's that number?"

"How is your marketing budget allocated? Based on what evidence?"

"Are your A/B tests actually detecting real effects, or are they underpowered?"
