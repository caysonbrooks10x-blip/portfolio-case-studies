# Case Study: Data Cleanup & Reporting Pipeline for Pacific Northwest Manufacturing

## The Client

Pacific Northwest Manufacturing (PNM) is a $180M industrial manufacturing company with 4 production facilities, 850 employees, and a complex supply chain spanning 200+ suppliers. Based in Tacoma, Washington, they had grown through acquisition from a $45M company 8 years ago — but their data infrastructure hadn't kept pace. Finance was running 47 Excel files to close the books each month. Operations had no real-time visibility into production. Sales couldn't trust the CRM data.

## The Problem

PNM's data was a legacy of 8 years of ad-hoc decisions, acquisitions with incompatible systems, and "good enough" mentality that had become untenable.

The symptoms were severe:
- **Monthly close took 8 business days** — industry average is 3-4 days
- **Finance team spent 60% of time on data gathering** instead of analysis
- **Three different versions of "truth"** — Finance, Operations, Sales each had different numbers
- **No single customer record** — same customer existed in 3 systems with different IDs
- **Vendor payments delayed** because PO matching was manual
- **Production schedules built on yesterday's data** — 24-hour delay in plant floor reporting
- **Sales forecasting done in sticky notes** — CRM had 40% data completeness

## The Solution

I designed and implemented a comprehensive data infrastructure modernization project using Snowflake as the central data warehouse, dbt for transformation and data quality, and a combination of Metabase for operational dashboards and custom Python scripts for automated reporting.

### Architecture

**Data Foundation:**
- Snowflake Enterprise data warehouse (production, staging, mart environments)
- Automated ELT pipelines from 12 source systems
- Fivetran for pre-built ERP and CRM connectors
- Custom Python ETL for legacy systems (FoxPro, legacy SQL)
- Data quality monitoring with dbt tests and Great Expectations

**Transformation Layer:**
- dbt Core for data transformation
- Staging layer: raw data from sources
- Intermediate layer: business logic
- Mart layer: analytics-ready tables
- Slowly changing dimensions for vendor and customer data
- History tables for audit and compliance

**Reporting Infrastructure:**
- Metabase for operational dashboards
- Custom Python report generation for financial statements
- Automated Excel workbook generation with live data connections
- Scheduled email distribution of key reports
- Row-level security for sensitive financial data

### Key Source Systems Connected

1. **SAP Business One** (ERP) — General ledger, AP/AR, inventory
2. **Salesforce** (CRM) — Accounts, opportunities, activities
3. **Shopify** (E-commerce) — B2C orders, 15% of revenue
4. **Legacy SQL DB** — Production scheduling, quality data
5. **FoxPro DB** (legacy) — Customer service records
6. **HRIS** (Workday) — Employee data, payroll
7. **Google Sheets** — Various manual tracking spreadsheets
8. **CSV exports** — Supplier portals, customs filings
9-12. **Four additional minor systems**

### Key Transformations Built

**1. Vendor Master Reconciliation**
- 3 source systems had different vendor IDs and addresses
- Fuzzy matching algorithm to identify same vendors
- Preferred vendor selection based on transaction history
- 200+ vendors deduplicated to 180 master records

**2. Customer 360**
- Salesforce, SAP, and legacy service system unified
- Fuzzy matching on company name + address
- 3,400 customer records deduplicated to 2,100 master customers
- Revenue, margin, and relationship history consolidated

**3. Inventory Valuation**
- Three ERP instances (one per acquired company) with different SKU schemes
- Cross-reference tables built for SKU mapping
- Unified inventory reporting across all facilities
- FIFO/Average cost calculation standardized

**4. Production Reporting**
- Legacy production system connected to warehouse
- Machine utilization calculations automated
- Quality metrics (scrap rate, first-pass yield) standardized
- Real-time plant floor dashboard (from 24-hour delay)

**5. Financial Close Automation**
- Automated GL reconciliation
- PO matching with exception flagging
- Intercompany transaction elimination
- Consolidated financial statement generation

## The Results

**Before:**
- Monthly close: 8 business days
- Finance time on data gathering: 60%
- Customer records: 3,400 (duplicated across systems)
- Vendor records: 200+ (duplicated, inconsistent)
- Production data delay: 24 hours
- Forecast accuracy: 45%
- Finance/Operations/Sales alignment: None (3 different numbers)

**After:**
- Monthly close: 3 business days (62% reduction)
- Finance time on data gathering: 15%
- Customer records: 2,100 master records (37% reduction)
- Vendor records: 180 master records (clean)
- Production data delay: 15 minutes (real-time)
- Forecast accuracy: 87%
- Finance/Operations/Sales alignment: Single source of truth

**Quantified Impact:**
- Monthly close reduced by 5 days: $180K in reduced audit/overtime costs
- Finance team redeployed 45% of time from data gathering to analysis
- Vendor payment errors reduced 85%: $220K in prevented losses
- Production efficiency improved 12% from real-time visibility: $1.4M impact
- Single customer view enabled $340K in additional cross-sell revenue
- 8.4 month payback period

## Technical Deep Dive

### Data Quality Framework

I implemented a comprehensive data quality framework using dbt tests and Great Expectations:

**Completeness Tests:**
- Null rate thresholds per column
- Required field validation
- Referral integrity (foreign keys)

**Accuracy Tests:**
- Value range validation (e.g., unit price > 0)
- Format validation (e.g., email addresses, phone numbers)
- Cross-system reconciliation (e.g., invoice totals match GL)

**Timeliness Tests:**
- Data freshness monitoring
- ETL job duration tracking
- Alert thresholds for pipeline delays

**Consistency Tests:**
- Intra-record validation
- Cross-record validation
- Slowly changing dimension versioning

### Fuzzy Matching Algorithm

Deduplicating vendors and customers required a custom fuzzy matching algorithm:

```python
def fuzzy_match(record1, record2):
    # Name similarity (Levenshtein distance)
    name_sim = levenshtein_similarity(record1.name, record2.name)
    
    # Address similarity
    addr_sim = jaro_winkler(record1.address, record2.address)
    
    # Phone number exact match
    phone_match = record1.phone == record2.phone
    
    # Email domain match
    domain_match = get_domain(record1.email) == get_domain(record2.email)
    
    # Weighted score
    score = (0.4 * name_sim + 0.3 * addr_sim + 
             0.15 * phone_match + 0.15 * domain_match)
    
    return score > 0.85  # Threshold for auto-match
```

### Slowly Changing Dimensions

For vendor and customer records, I implemented Type 2 slowly changing dimensions:

```sql
-- Customer dimension with SCD Type 2
INSERT INTO dim_customer (
    customer_key,
    customer_id,
    customer_name,
    address,
    phone,
    effective_date,
    expiry_date,
    is_current
)
SELECT 
    customer_key,
    customer_id,
    customer_name,
    address,
    phone,
    CURRENT_DATE(),
    '9999-12-31',
    TRUE
FROM staging_customers s
WHERE NOT EXISTS (
    SELECT 1 FROM dim_customer d
    WHERE d.customer_id = s.customer_id
    AND d.is_current = TRUE
    AND d.customer_name = s.customer_name
);
-- Expire old record, insert new on changes
```

## Lessons Learned

1. **Legacy system connectors are underestimated**: The FoxPro database from 1995 took 3 weeks to connect properly. Budget extra time for legacy systems — they're always messier than expected.

2. **Business buy-in requires quick wins**: We prioritized the vendor master cleanup because it had immediate CFO visibility. Early wins built momentum for harder changes.

3. **Data governance can't be afterthought**: We implemented data stewardship roles mid-project. Should have been week 1. Some data quality issues required business decisions, not technical fixes.

4. **The "three versions of truth" problem is cultural**: Technically, we solved it in month 4. Culturally, it took 6 months for teams to trust the new numbers. Change management is 50% of the work.

## Client Testimonial

"Cayson didn't just build us a data warehouse — he gave us operational confidence. For the first time, our sales team, operations team, and finance team are looking at the same numbers. Production is making decisions in real-time instead of reacting to yesterday's problems. The monthly close went from 8 days to 3 days. I didn't think that was possible."

— Robert Tanaka, CFO, Pacific Northwest Manufacturing

## About This Engagement

- **Duration**: 28 weeks (discovery through optimization)
- **Team**: 1 lead analyst, 2 data engineers, 1 data architect
- **Investment**: $245,000 (implementation + Year 1 tooling)
- **Payback period**: 8.4 months
- **Tools**: Snowflake, dbt, Metabase, Fivetran, Python, Great Expectations, Snowflake BI
