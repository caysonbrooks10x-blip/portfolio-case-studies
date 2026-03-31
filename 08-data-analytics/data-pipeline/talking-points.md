# Data Cleanup & Reporting Pipeline — Talking Points

## Opening

"I specialize in untangling data chaos. I recently worked with a $180M manufacturing company that had grown through acquisition over 8 years but never modernized their data infrastructure. They had 47 Excel files, 12 source systems, three conflicting versions of truth, and a finance team spending 60% of their time just gathering data."

"The result? Monthly close went from 8 business days to 3. Production data went from 24-hour delay to real-time. Finance time on data gathering dropped from 60% to 15%."

## Problem Framing

"Manufacturing companies accumulate data debt faster than anyone. Each acquisition brings new systems, new formats, new definitions. PNM had three ERP systems with different chart of accounts, different customer ID schemes, different product hierarchies."

"The problem isn't just technical. When Finance sees one number, Operations sees another, and Sales sees a third — that's a trust problem. People stop making decisions because they don't trust the data."

"Monthly close was 8 days because everything was manual. GL reconciliation was done in Excel. PO matching was paper-based. Intercompany eliminations required 4 people with spreadsheets."

## Solution Highlights

"We built a complete data infrastructure modernization:

1. **Snowflake Data Warehouse**: Central repository for all 12 source systems. Dev/staging/prod environments with proper access controls.

2. **dbt Transformation Layer**: Staging → Intermediate → Mart architecture. 400+ dbt models. Data quality tests on every column.

3. **Master Data Management**: Fuzzy matching algorithm deduplicated 3,400 customers to 2,100 master records. 200+ vendors to 180 master vendors.

4. **Data Quality Framework**: Great Expectations + dbt tests. Completeness, accuracy, timeliness, consistency monitoring.

5. **Automated Reporting**: Financial close automation. Real-time production dashboards. Scheduled report distribution."

## Results That Resonate

"Monthly close went from 8 business days to 3. That freed up 5 days of finance team time each month — 60 days per year. At $12K/day in overhead, that's $720K in annual savings just from the close."

"Finance team time on data gathering dropped from 60% to 15%. They're finally doing analysis instead of data entry."

"Production has real-time visibility now. The plant floor dashboard refreshes every 15 minutes. Before, they were making decisions on yesterday's data. Now they see what's happening now."

"Vendor payment errors dropped 85%. The fuzzy matching and PO matching automation caught duplicates and discrepancies before payments went out. $220K in prevented losses."

## Technical Depth (When Asked)

"The fuzzy matching algorithm was critical. We used a combination of Levenshtein distance for name similarity, Jaro-Winkler for addresses, and exact matches on phone/email where available. The threshold was 85% confidence — above that, auto-merge; below that, manual review queue."

"Slowly changing dimensions were important for compliance. Vendor addresses change, customer contacts change. We implemented Type 2 SCD — every change creates a new record with effective dates. Full audit trail."

"The Great Expectations integration with dbt was powerful. We wrote expectation suites for each staging model. Every ELT run generates a data quality report. Any failure triggers alerts before downstream impact."

## Closing Questions

"How long does your monthly close take? If it's more than 5 days, there's likely significant waste."

"How many versions of truth does your organization have? If you don't know, that's the first problem."

"Where would real-time production data create the most value? Can you currently see that?"
