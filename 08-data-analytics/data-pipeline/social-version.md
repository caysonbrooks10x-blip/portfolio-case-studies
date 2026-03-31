# LinkedIn Post

Just finished a data infrastructure nightmare project — and the results were transformational.

Pacific Northwest Manufacturing: $180M industrial company that had grown through acquisition but never modernized their data infrastructure.

Their situation:
→ 47 Excel files to close the books monthly
→ 8 business days to complete monthly close (industry avg: 3-4)
→ 3 different versions of "truth" across departments
→ 3,400 customer records scattered across 3 systems
→ Production data 24 hours old
→ 60% of finance team's time on data gathering

We built:
→ Snowflake data warehouse unifying 12 source systems
→ dbt transformation layer with data quality framework
→ Vendor and customer master data cleanup (fuzzy matching)
→ Real-time production monitoring
→ Automated financial close process

Results:
• Monthly close: 8 days → 3 days (62% reduction)
• Finance time on data: 60% → 15%
• Customer records: 3,400 → 2,100 unified
• Production data: 24hr delay → 15 minutes
• Forecast accuracy: 45% → 87%
• $2.3M annual impact
• 8.4 month payback

The lesson: manufacturing companies have more data chaos than anyone, and the ROI of fixing it is massive.

What does your monthly close look like? 👇

#Manufacturing #DataEngineering #DataAnalytics #Snowflake #dbt

---

# Twitter/X Thread

🧵 Data infrastructure nightmare → modern analytics platform.

Client: $180M manufacturing company, 8 years of acquisition tech debt, 47 Excel files to close the books.

The chaos:
• 8 day monthly close (industry: 3-4 days)
• 3 conflicting versions of truth
• 3,400 customer records in 3 systems
• 24hr production data delay
• Finance team: 60% data gathering, 40% analysis

We built:

1/ Snowflake data warehouse
   → 12 source systems connected

2/ dbt transformation layer
   → Data quality framework
   → Slowly changing dimensions

3/ Master data management
   → Fuzzy matching deduplication
   → 200+ vendors → 180 master
   → 3,400 customers → 2,100 master

4/ Real-time production reporting
   → 24hr delay → 15 minutes

5/ Automated financial close
   → GL reconciliation
   → PO matching
   → Exception flagging

Results:
→ Close: 8 days → 3 days
→ Finance data time: 60% → 15%
→ Customer records: -37%
→ Production data: real-time
→ Forecast accuracy: 45% → 87%
→ $2.3M annual impact
→ 8.4 month payback

---

# Instagram Caption

From 47 Excel files to a unified data platform. 📊

Built Pacific Northwest Manufacturing a complete data infrastructure overhaul with @snowflakedw + @getdbt + custom ETL.

The kicker? Their production team finally has real-time visibility — 24-hour data lag reduced to 15 minutes.

Monthly close went from 8 business days to 3.
Finance team's data gathering time: cut by 75%.
Forecast accuracy: doubled.

$245K implementation → $2.3M annual impact. 8.4 month payback.

#dataengineering #manufacturing #analytics #dataquality #modernization
