# Revenue Analytics — Visuals Plan

## Dashboard Visual Structure

### 1. Revenue Overview (Landing Page)
**Layout**: KPI cards + waterfall + trend

**Visual Elements**:
- **Top row**: 4 hero KPI cards (Total ARR, NRR, GRR, Forecast Accuracy) with trend arrows
- **Middle**: ARR waterfall chart showing New → Expansion → Churn → Contraction → Ending
- **Bottom**: 12-month ARR trend line with confidence interval shading

**Color Palette**: Deep Blue (#1A365D) primary, Green (#38A169) for positive, Red (#E53E3E) for negative, Gray (#718096) for neutral

---

### 2. ARR Waterfall Analysis
**Layout**: Waterfall + cohort table

**Visual Elements**:
- **Waterfall chart**: Animated progression from Beginning ARR to Ending ARR
- **Cohort table**: Rows = acquisition quarter, Columns = Q1, Q2, Q3... retention
- **Color coding**: Green (healthy), Yellow (at-risk), Red (churned)
- **Filters**: Time period, customer segment, product tier

---

### 3. Customer Revenue Intelligence
**Layout**: Account table + detail panel

**Visual Elements**:
- **Account table**: Sortable (ACV, MRR, Health Score, Risk Tier, Renewal Date)
- **Detail expansion**: Click to reveal account timeline, usage trends, risk factors
- **Expansion alerts**: Badge on accounts hitting usage thresholds
- **Renewal calendar**: 12-month forward view of upcoming renewals

---

### 4. Forecast Workbench
**Layout**: Three-column (scenarios + trends + details)

**Visual Elements**:
- **Left column**: Scenario toggles (Base/Bull/Bear) with assumptions
- **Center**: Forecast chart with Prophet trend + LightGBM confidence interval
- **Right column**: Variance table (forecast vs. actual by segment)
- **Bottom**: 13-week weekly breakdown with probability weighting

---

### 5. Churn Risk Scorecard
**Layout**: Heat map + account list

**Visual Elements**:
- **Risk heat map**: Accounts plotted by churn probability (x) vs. ACV (y), sized by revenue exposure
- **At-risk table**: Sorted by risk score, shows top 3 reason codes per account
- **Intervention tracker**: Shows which at-risk accounts have CSM action plans
- **Trend chart**: Overall portfolio risk score over time

---

## Chart Type Selection

| Dashboard | Primary Chart | Secondary Chart | Tertiary |
|-----------|---------------|-----------------|----------|
| Revenue Overview | KPI Cards | Waterfall | Line Trend |
| ARR Analysis | Waterfall | Cohort Heat Map | Bar |
| Customer Intelligence | Data Table | Line (usage) | Scatter (health vs. value) |
| Forecast Workbench | Area (uncertainty) | Scenario Bars | Variance Table |
| Churn Risk | Scatter (risk map) | Table | Trend Line |

---

## Interaction Design

### Navigation
- Top tabs for main sections (Overview, ARR, Customers, Forecast, Churn)
- Left sidebar for sub-navigation within each section
- Quick filters in header (time period, segment)

### Drill-Down Paths
1. ARR Overview → Quarter → Cohort → Account → Account Detail
2. Forecast → Scenario Detail → Account-level contributions
3. Churn Risk → Account → Risk Factors → Intervention Plan → Outcome

### Alert Integration
- Churn risk alerts appear as toast notifications
- Forecast variance > 5% triggers email to CFO
- Expansion signals appear inline in account table

---

## Mobile Considerations

- Critical KPIs visible on mobile (ARR, NRR, Churn Count)
- Churn risk list accessible for CSMs on-the-go
- Weekly forecast summary push notification (optional)
- Read-only access (no data entry on mobile)

---

## Deliverables for Visuals

- [ ] Figma prototype of all 5 dashboard screens
- [ ] Component library (KPI cards, waterfal, risk scatter)
- [ ] Color palette documentation with semantic meaning
- [ ] Animation specs (waterfall progression, trend reveals)
- [ ] Print-friendly versions for board materials
- [ ] Dark mode variants for analyst preference
