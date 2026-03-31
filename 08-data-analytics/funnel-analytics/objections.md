# Funnel Analytics — Objection Handling

## "We already have Google Analytics. Why do we need more?"

Google Analytics shows you what happened on your website. It doesn't show you:
- Cross-device purchase behavior
- Which channels actually drive purchases (not just sessions)
- Revenue attribution by channel
- A/B test results with statistical rigor
- The full funnel from awareness to purchase

GA4 is a great tool for understanding site traffic. It's not a business intelligence platform for understanding customer value.

---

## "Attribution modeling sounds overly complex. Is it worth it?"

Complexity is relative. The alternative is making $12M/year in marketing decisions based on a lie.

Last-touch attribution inflates the credit of bottom-funnel channels (retargeting, direct) and undervalues upper-funnel channels (branded search, content, email).

The complexity is in the implementation. Once it's running, you just look at the dashboard. The insight is simple: "Allocate more to the channels that actually drive purchases."

---

## "Our team doesn't have time to analyze all this data."

That's exactly the problem. You have the data but can't extract value from it.

We build operational dashboards that surface actionable insights, not raw data. CSMs see "Account #247 is at risk, here's why." Marketers see "Channel X is underperforming, here's the evidence."

The goal is to REDUCE analysis burden, not increase it.

---

## "We tried A/B testing before and never saw significant results."

Two likely causes:

1. **Underpowered tests**: You need ~45,000 users per variant to detect a 5% lift with 80% power. Most companies run tests with 5,000 users and are surprised when nothing is significant.

2. **Wrong metrics**: Testing conversion rate when you should be testing revenue per user. A test might reduce conversion rate but increase AOV, resulting in higher revenue.

We implemented sequential testing that lets you stop tests early when results are clear, and we use revenue-based primary metrics.

---

## "Mobile optimization is on our roadmap but deprioritized."

That's a $3.4M annual revenue opportunity sitting on a roadmap.

Our analysis showed: Product pages under 2 seconds load converted at 3.8%. Pages over 4 seconds converted at 0.9%. That's a 4.2x difference.

The roadmap should be driven by revenue impact, not executive intuition. We provide the evidence.

---

## "How do we validate attribution without a control group?"

We use multiple methods:

1. **Compare models**: If all 5 attribution models agree, confidence is high
2. **Holdout tests**: Tag some traffic with no attribution and track their behavior
3. **Incrementality tests**: Temporarily suppress certain channels and measure the drop
4. **Cohort analysis**: Compare LTV by acquisition channel

Attribution is never 100% certain, but it's much better than last-touch.

---

## "Privacy changes (iOS 14+) have broken our tracking."

iOS 14+ did impact Facebook conversion tracking. We address this by:
- Server-side conversion tracking (more reliable than pixel-based)
- First-party data enrichment from Shopify
- Aggregate modeling for attribution
- Focus on owned channels (email, push) that don't depend on tracking

Privacy-compliant tracking is actually more sustainable long-term.

---

## "This seems expensive for a 20-week engagement."

The alternative is continued $12M/year in misallocated marketing spend.

We showed 62% ROAS improvement: from 2.1x to 3.4x. On a $12M base, that's equivalent to $4.8M in effective marketing capacity.

$125K implementation → $4.67M annual impact. 2.1 month payback.

The question isn't "can we afford this?" It's "can we afford NOT to know which channels work?"

---

## "We need to see quick wins to justify this to our board."

We design for quick wins:

- Week 2: Funnel analysis identifies mobile checkout gap
- Week 6: First attribution insights
- Week 10: First A/B test results
- Week 20: Full platform operational

The funnel optimization alone — mobile UX fixes — was $3.4M in recovered revenue. That's visible within the first month.
