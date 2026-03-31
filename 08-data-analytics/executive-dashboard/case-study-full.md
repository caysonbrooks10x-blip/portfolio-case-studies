# Case Study: Executive Dashboard for Meridian Capital Partners

## The Client

Meridian Capital Partners is a $2.4B private equity firm based in Chicago with 34 portfolio companies across manufacturing, healthcare services, and technology sectors. Their investment team of 22 professionals needed real-time visibility into portfolio company performance, but monthly board meetings were hampered by outdated spreadsheets and inconsistent data formats.

## The Problem

Meridian's investment team was drowning in manual reporting. Each month, they spent 14+ hours compiling performance data from 7 disparate sources: QuickBooks (accounting), Salesforce (deals pipeline), PitchBook (market data), Excel models (portfolio company financials), HubSpot (LP relations), Excel-based cap tables, and a custom SQL database for portfolio tracking.

The process was error-prone and unsustainable:
- Data reconciliation consumed 60% of analyst time during close periods
- Board packages arrived late because one person held the "钥匙" (keys) to the reporting process
- Portfolio company KPIs were inconsistently defined across firms
- Market benchmark data required manual aggregation from multiple vendors
- Scenario modeling was done in static Excel with no sensitivity analysis

## The Solution

I designed and built a unified executive dashboard ecosystem using Looker as the primary visualization layer, connected to a Snowflake data warehouse that consolidated all 7 data sources into a single source of truth.

### Architecture

**Data Layer:**
- Snowflake Enterprise DW with daily ELT pipelines
- dbt for data transformation and metric standardization
- Fivetran for pre-built connectors to QuickBooks, Salesforce, HubSpot
- Custom Python scripts for PitchBook API integration and cap table processing

**Semantic Layer:**
- Looker LookML for consistent metric definitions
- Unified investor dashboard with 47 standardized KPIs
- Portfolio company comparison framework with industry-adjusted benchmarks
- Dynamic scenario modeling with Monte Carlo simulations

**Delivery Layer:**
- Cached daily snapshots for board meeting prep
- Mobile-optimized views for iPad use in board meetings
- Scheduled PDF generation for compliance documentation
- Drill-down paths from portfolio summary to underlying company financials

### Key Dashboard Components

1. **Portfolio Overview**: Waterfall chart showing value creation by source (multiple expansion, leverage, organic growth, acquisitions), sector allocation, geographic exposure
2. **Portfolio Company Performance**: Trailing 12-month revenue, EBITDA, free cash flow with variance to budget and prior year
3. **Deal Pipeline**: Active sourcing, initial screening, due diligence, and closing stages with conversion metrics
4. **LP Reporting**: Capital account statements, partnership performance (IRR, TVPI, DPI, RVPI), cash distribution waterfall
5. **Benchmark Comparison**: Portfolio company performance vs. relevant public comps and sector indices
6. **Risk Dashboard**: Early warning indicators (revenue concentration, customer churn, key employee departures, covenant headroom)

## The Results

**Before:**
- Weekly reporting time: 14 hours (one analyst, full-time during close)
- Board package delivery: 3 days before meeting (often rushed/incomplete)
- Data sources: 7 disconnected systems
- KPI definitions: Inconsistent across portfolio companies
- Scenario analysis: Static, single-scenario Excel models

**After:**
- Weekly reporting time: 45 minutes (automated refresh and distribution)
- Board package delivery: 5 days before meeting (fully prepared)
- Data sources: Unified in Snowflake with Looker semantic layer
- KPI definitions: 47 standardized metrics with documented methodology
- Scenario analysis: Real-time sensitivity models with 5 scenario types

**Quantified Impact:**
- 96% reduction in manual reporting time (14hrs → 45min/week)
- 4x faster board package preparation (3 days → 18 hours turnaround)
- Zero reconciliation errors in quarterly reporting (previously averaged 12 per quarter)
- 12% improvement in investment decision speed due to real-time data availability
- Estimated annual cost savings: $127,000 in recovered analyst hours

## Technical Deep Dive

### Data Modeling Approach

I implemented a dimensional data model in Snowflake with a star schema optimized for analytical queries:

- **Fact tables**: Cash flows, valuations, trades, covenant compliance
- **Dimension tables**: Portfolio companies, investors, deal terms, time periods, industry classifications
- **Bridge tables**: Many-to-many relationships for fund-to-portfolio-company holdings

The dbt transformation layer enforced data quality through:
- Schema tests on every column (not null, unique, referential integrity)
- Singular tests for business logic validation
- Documentation in LookML for every calculated metric
- Lineage tracking from source to dashboard

### Metric Standardization

One of the biggest challenges was reconciling how different portfolio companies defined "adjusted EBITDA." I built a metric inheritance system:

```
Base Metric (defined once in LookML)
    ↓
Company-Specific Adjustments (documented as LookML derived tables)
    ↓
Normalized Output (comparable across portfolio)
```

This allowed instant comparison: Company A's "Adjusted EBITDA" vs. Company B's "Pro Forma EBIT" were both mapped to a universal "Cash Earnings" metric with full transparency on adjustments.

### Security and Permissions

Given the sensitivity of PE financial data, I implemented:
- Row-level security based on fund-to-company relationships
- Column-level masking for confidential deal terms
- Audit logging of all data access
- SSO integration with Meridian's Okta instance
- Scheduled data refresh with change notification

## Lessons Learned

1. **Executive sponsors are critical**: The CFO was my champion; without his authority to mandate data standards across portfolio companies, standardization would have failed.

2. **Phased rollout reduces risk**: We went live with core financials in month 1, then added deal pipeline in month 2, LP reporting in month 3. This let us prove value before expanding scope.

3. **Documentation is the product**: Every KPI has a definition, source system, calculation methodology, and owner. This metadata is as important as the dashboard itself.

4. **Mobile-first for boardrooms**: The iPad-optimized views with large touch targets and simplified navigation were used in 80% of board meetings—far more than expected.

## Client Testimonial

"Cayson transformed how we run our investment meetings. What used to be a data scramble is now a strategic conversation. Our LP presentations went from 'here's what we compiled' to 'here's what we're actioning.' The ROI was immediate and measurable."

— Jennifer Walsh, CFO, Meridian Capital Partners

## About This Engagement

- **Duration**: 16 weeks (discovery through optimization)
- **Team**: 1 lead analyst, 1 data engineer, 1 project manager
- **Investment**: $185,000 (hardware, software licenses, implementation services)
- **Payback period**: 4.2 months (based on recovered analyst time alone)
- **Tools**: Snowflake, Looker, dbt, Fivetran, Python, GitHub
