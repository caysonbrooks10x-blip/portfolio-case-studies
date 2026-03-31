# Executive Dashboard — Talking Points

## Opening

"I help investment firms turn scattered data into strategic advantage. Recently, I worked with a $2.4B private equity firm spending 700+ hours/year on manual reporting. We reduced that to 40 hours — and gave them real-time portfolio visibility."

## Problem Framing

"Most firms think their reporting problem is a tooling problem. It's not — it's an architecture problem. When you have 7 data sources with inconsistent definitions, no amount of Excel gymnastics will fix it."

"You need a semantic layer that standardizes definitions BEFORE visualization. That's where most dashboard projects fail — they visualize mess instead of fixing the mess."

## Solution Highlights

"Built a unified Looker + Snowflake ecosystem with:
- Automated ELT pipelines (no more manual data pulls)
- dbt transformation layer with 47 standardized KPIs
- Row-level security for sensitive fund-level data
- Mobile-optimized views for boardroom iPads"

"Key insight: We didn't just build dashboards. We created a metric inheritance system where every calculation traces back to a single definition. Company A's 'Adjusted EBITDA' and Company B's 'Pro Forma EBIT' both map to a universal 'Cash Earnings' with full transparency."

## Results That Resonate

"96% reduction in weekly reporting time. That's 13+ hours/week recovered per analyst."

"Board packages went from 3-day turnaround to 18 hours. Their CFO told me investment meetings shifted from 'data scramble' to 'strategic conversation.'"

"Zero reconciliation errors in the first quarter after launch. Previously averaged 12 per quarter."

## Closing Questions

"What would your team do with an extra 13 hours per week?"

"How much is reliable, real-time data worth to your investment decisions?"

## Technical Depth (When Asked)

"We used Fivetran for pre-built connectors and custom Python for PitchBook API integration. The dbt layer enforced data quality through schema tests on every column and business logic validation."

"Security was critical — PE data is sensitive. We implemented fund-to-company row-level security with column masking for confidential deal terms, plus full audit logging."

## Objection Handling

"If they say 'We tried Tableau and it didn't work': Tool选错不是问题 — the issue is usually semantic layer design. We can migrate or optimize existing investments."

"If they say 'Our data is too messy': That's exactly why you need a transformation layer before visualization. Happy to do a data audit to show what's achievable."

"If they say 'Timeline is too long': 16 weeks is fast for this scope. We phase delivery so you see value in month 1."
