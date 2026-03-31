# KPI Architecture — Talking Points

## Opening

"I help scaling companies create a common language for success. I recently worked with a Series B healthcare tech company that was growing from 50 to 180 employees. Everyone felt aligned — until you asked two teams what 'active user' meant. Then the arguments started."

"The result was transformational: 94% reduction in board package time, sales and finance aligned to < 2% variance, and a Series C data room that investors called 'the cleanest they'd seen.'"

## Problem Framing

"At 50 people, you don't need a KPI architecture. Everyone sits near each other, shares a spreadsheet, and 'just knows' the numbers. At 180 people, you have departments, time zones, and competing priorities. Without a shared definition of success, you get:

- Sales and Finance arguing about quota attainment
- Product teams optimizing for output instead of outcomes
- OKRs that feel arbitrary because there's no data to validate them
- Board packages that take 3 days because nobody trusts the numbers

This isn't a data problem. It's an alignment problem that manifests as a data problem."

## Solution Highlights

"We built a complete KPI architecture with four components:

1. **True North Metrics**: 12 company-level metrics that define success. Every employee can explain how their work affects these metrics.

2. **KPI Trees**: Each team built a tree showing how their metrics roll up to company metrics. Product ships features that move metrics. Sales acquires accounts that move metrics. Everyone is pointing the same direction.

3. **Leading Indicators**: We identified and validated 8 metrics that predict future performance 8 weeks ahead. Leadership stopped flying blind.

4. **Governance Model**: A Metric Review Board ensures definitions stay consistent as the company scales. Changes go through a documented process."

## Results That Resonate

"Board package went from 3 days to 4 hours. Not through magic — through automation. Every metric in the board deck is calculated in dbt, pushed to Looker, and the slides write themselves."

"Sales and Finance were 26% apart on quota attainment. Same quarter, same company. After aligning on definitions, they're within 2%. The debate isn't about numbers anymore — it's about strategy."

"We identified 8 leading indicators for NRR, churn, and growth. These predict outcomes 8 weeks in advance. Now leadership can course-correct before problems appear in lagging metrics."

"Series C data room: Investors told them it was the cleanest data room they'd seen. $45M raise closed. The KPI architecture wasn't just internally valuable — it was an external signal of company maturity."

## Technical Depth (When Asked)

"The hardest part was definitions, not technology. 'Active user' meant 6 different things across 4 teams. We spent 3 weeks in working sessions to align. The output was a Metric Definitions Document — every metric has definition, calculation, source system, owner, and change history."

"The dbt semantic layer ensures consistent calculations. When finance calculates ARR, it's the same ARR that sales sees, that the board sees. No more 'which version of truth do you want?'"

"We built statistical anomaly detection into critical metrics. When a metric moves outside 2.5 standard deviations from its rolling mean, we alert the metric owner. This catches problems before they become crises."

## Closing Questions

"How many people in your company can explain how their work affects revenue?"

"Do you have visibility into leading indicators, or are you always looking in the rearview mirror?"

"How long does your board package take to compile? If it were ready in 4 hours instead of 3 days, what would you do with that time?"
