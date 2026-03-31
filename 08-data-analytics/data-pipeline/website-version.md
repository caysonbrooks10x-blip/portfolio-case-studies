# Data Cleanup & Reporting Pipeline for Manufacturing

## The Challenge

Pacific Northwest Manufacturing was running on 8 years of accumulated technical debt. Finance needed 47 Excel files and 8 business days to close the books. Three departments had three different versions of the truth. Production was making decisions on 24-hour-old data.

## The Solution

Built a comprehensive data infrastructure modernization with Snowflake warehouse, dbt transformations, and automated reporting. Connected 12 source systems, deduplicated customer/vendor records, and implemented real-time production monitoring.

## Results

**62% Reduction in Monthly Close**
8 business days → 3 business days

**75% Reduction in Finance Data Time**
From 60% to 15% of time spent on data gathering

**37% Reduction in Customer Records**
3,400 → 2,100 unified master records

**Real-Time Production Visibility**
24-hour delay → 15 minutes

**Forecast Accuracy Improvement**
45% → 87%

**8.4 Month Payback**
On $245K implementation

## Technical Approach

- Snowflake Enterprise warehouse with dev/staging/prod
- dbt Core for transformation and data quality
- Fivetran + custom Python ETL for 12 source systems
- Fuzzy matching for customer/vendor deduplication
- Great Expectations for data quality monitoring
- Metabase for operational dashboards
- Slowly changing dimensions for audit compliance

## Tools & Technologies

Snowflake | dbt | Metabase | Fivetran | Python | Great Expectations

## Client

> "For the first time, our sales team, operations team, and finance team are looking at the same numbers. Production is making decisions in real-time instead of reacting to yesterday's problems. The monthly close went from 8 days to 3 days. I didn't think that was possible."
> — Robert Tanaka, CFO, Pacific Northwest Manufacturing

## Engagement Details

- **Duration**: 28 weeks
- **Investment**: $245,000
- **Team**: 1 lead analyst, 2 data engineers, 1 data architect
