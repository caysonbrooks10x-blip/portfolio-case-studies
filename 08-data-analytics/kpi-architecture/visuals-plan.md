# KPI Architecture — Visuals Plan

## Dashboard Visual Structure

### 1. Executive Scorecard (Landing Page)
**Layout**: 12 KPI cards + trend + variance

**Visual Elements**:
- **Top row**: 4 hero cards (ARR, NRR, GRR, Burn Multiple) with trend arrows
- **Middle row**: 8 metric cards (remaining True North metrics)
- **Bottom**: 12-week trend for all 12 metrics with target overlay
- **Right sidebar**: Variance analysis (current vs. target vs. prior quarter)

**Color Palette**: Navy (#1E3A5F) primary, Green (#38A169) on track, Yellow (#D69E2E) at risk, Red (#E53E3E) off track

---

### 2. Board Package Dashboard
**Layout**: Slide preview + data tables + export

**Visual Elements**:
- **Slide preview**: Looker embeds of board slide layouts
- **ARR waterfall**: Beginning → New → Expansion → Churn → Ending
- **Cohort analysis**: Retention curves by acquisition quarter
- **Burn analysis**: Monthly burn with runway projection
- **Variance summary**: All metrics vs. target
- **One-click export**: PDF generation

---

### 3. Leading Indicators Dashboard
**Layout**: Prediction cards + accuracy + signals

**Visual Elements**:
- **Prediction cards**: 8 leading indicators with current value, trend, prediction
- **Prediction accuracy**: Tracking of predictions vs. actuals
- **Signal strength**: Visual indicator of prediction confidence
- **Alert list**: Active alerts for metric movements

**Refreshes weekly**

---

### 4. Team KPI Dashboard (Sales Example)
**Layout**: Team metrics + KPI tree + OKR progress

**Visual Elements**:
- **Team metrics grid**: 7 sales metrics with current, target, trend
- **KPI tree visualization**: How team metrics connect to company True North
- **OKR progress**: Current quarter OKRs with metric-linked KRs
- **Leaderboard**: Rep performance (if applicable)

---

### 5. Metric Governance Dashboard
**Layout**: Change log + review calendar + definitions

**Visual Elements**:
- **Change request log**: Pending, approved, implemented changes
- **Review calendar**: Upcoming Metric Review Board meetings
- **Metric definitions browser**: Searchable library of all metrics
- **Data freshness**: Last update time for each metric

---

## Chart Type Selection

| Dashboard | Primary Chart | Secondary Chart | Tertiary |
|-----------|---------------|-----------------|----------|
| Executive Scorecard | KPI Cards | Line (trend) | Variance Table |
| Board Package | Waterfall | Cohort | Bar |
| Leading Indicators | Gauge | Line | Accuracy Tracker |
| Team KPI | Cards + Tree | OKR Progress | Table |
| Governance | Log Table | Calendar | Search |

---

## Interaction Design

### Navigation
- Top tabs (Scorecard, Board, Leading, Teams, Governance)
- Quick filter for time period
- Metric owner search

### Drill-Down Paths
1. Executive Scorecard → Metric → Metric Detail → Source Data
2. Leading Indicators → Prediction → Indicator Detail → Methodology
3. Team Dashboard → Metric → KPI Tree → Company True North
4. Governance → Metric → Definition → Change History

### Alert Integration
- Anomaly detection alerts via email
- OKR at-risk notifications
- Metric target breach alerts
- Weekly digest email

---

## Mobile Considerations (Executive Use)

- Executive scorecard visible on mobile
- Push notifications for anomaly alerts
- OKR at-risk notifications
- Read-only dashboard access

---

## Deliverables for Visuals

- [ ] Figma prototype of all 5 dashboard screens
- [ ] Component library (KPI cards, KPI trees, prediction cards)
- [ ] Color palette documentation (semantic colors for status)
- [ ] Board slide templates (PowerPoint)
- [ ] Mobile wireframes for executive app
- [ ] Animation specs for trend reveals
