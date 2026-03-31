# Data Cleanup & Reporting Pipeline — Visuals Plan

## Dashboard Visual Structure

### 1. Executive Overview (Landing Page)
**Layout**: KPI cards + trends + alerts

**Visual Elements**:
- **Top row**: 4 KPI cards (Monthly Close Status, Data Quality Score, System Uptime, Active Alerts)
- **Middle**: Monthly close timeline Gantt chart
- **Bottom left**: Data quality trend (% pass rate over time)
- **Bottom right**: Source system health grid

**Color Palette**: Navy (#1E3A5F) primary, Green (#38A169) healthy, Yellow (#D69E2E) warning, Red (#E53E3E) critical

---

### 2. Master Data Management
**Layout**: Match rates + review queue + history

**Visual Elements**:
- **Top**: Match rate metrics (auto-matched, manual review, unmatched)
- **Middle**: Fuzzy match review interface (record pairs with confidence scores)
- **Bottom**: Historical deduplication progress (records over time)

**For Vendors and Customers separately**

---

### 3. Financial Close Dashboard
**Layout**: Checklist + timeline + reconciliation status

**Visual Elements**:
- **Close checklist**: Task list with owner, status, completion time
- **Timeline**: Gantt showing close activities by day and owner
- **GL reconciliation status**: Account-level pass/fail grid
- **Intercompany eliminations**: Transaction count and net amounts

---

### 4. Production Operations Dashboard
**Layout**: Real-time metrics + trends + alerts

**Visual Elements**:
- **Real-time KPIs**: Units produced, uptime %, scrap rate, first-pass yield
- **Facility comparison**: 4 plants side-by-side
- **Shift performance**: Day vs. Evening vs. Night
- **Alert panel**: Quality exceptions, downtime warnings

**Refreshes every 15 minutes**

---

### 5. Inventory & Supply Chain
**Layout**: Heat map + trends + drill-down

**Visual Elements**:
- **Inventory heat map**: By SKU (turns vs. value)
- **Stockout risk**: Items below safety stock
- **Lead time trends**: By supplier
- **Demand forecast**: 13-week rolling projection

---

## Chart Type Selection

| Dashboard | Primary Chart | Secondary Chart | Tertiary |
|-----------|---------------|-----------------|----------|
| Executive | KPI Cards | Gantt (timeline) | Trend Line |
| Master Data | Match Rate | Review Queue | History |
| Financial Close | Checklist | Gantt | Grid |
| Production | KPI Cards | Bar (facilities) | Trend |
| Inventory | Heat Map | Line | Table |

---

## Interaction Design

### Navigation
- Left sidebar menu (collapsible)
- Breadcrumb navigation for drill-down
- Quick filters in header

### Drill-Down Paths
1. Executive → Close Task → Owner → Completion Details
2. Production → Facility → Line → Machine → Batch Details
3. Inventory → Category → SKU → Transaction History
4. Master Data → Customer → All Sources → Merge Preview

### Alert Integration
- Data quality failures: Email to data steward
- Pipeline failures: Slack to data engineering
- Close deadline approaching: Email to close owner
- Production alerts: SMS to plant manager

---

## Mobile Considerations (Plant Managers)

- Simplified KPI view
- Push notification for critical alerts
- Quick action buttons (acknowledge, escalate)
- Read-only dashboard access

---

## Deliverables for Visuals

- [ ] Figma prototype of all 5 dashboard screens
- [ ] Component library (close checklist, match review, production cards)
- [ ] Color palette documentation (semantic colors)
- [ ] Print-friendly close checklist template
- [ ] Mobile wireframes for plant manager app
- [ ] Alert notification templates
