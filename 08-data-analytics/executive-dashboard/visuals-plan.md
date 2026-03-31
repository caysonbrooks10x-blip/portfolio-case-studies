# Executive Dashboard — Visuals Plan

## Dashboard Visual Structure

### 1. Portfolio Overview (Landing Page)
**Layout**: Hero metric cards + waterfall + allocation grid

**Visual Elements**:
- **Top row**: 4 KPI cards (Total AUM, YTD Return, IRR, TVPI) with sparkline trends
- **Middle**: Value creation waterfall chart (starting value → multiple expansion → leverage → organic growth → acquisitions → ending value)
- **Bottom**: Geographic allocation map + sector pie chart side-by-side

**Color Palette**: Navy (#1E3A5F) primary, Gold (#C9A227) accent, White backgrounds

---

### 2. Portfolio Company Performance
**Layout**: Table with drill-down + trend sparklines

**Visual Elements**:
- **Main table**: Sortable columns (Company, Sector, Revenue, EBITDA, FCF, Growth %, Budget Variance %)
- **Row expansion**: Click to reveal trailing 12-month trend chart, key metrics breakdown
- **Conditional formatting**: Red/yellow/green for budget variance thresholds
- **Filters**: Sector dropdown, fund dropdown, time period selector

---

### 3. Deal Pipeline
**Layout**: Kanban board + funnel visualization

**Visual Elements**:
- **Kanban columns**: Sourcing → Screening → Due Diligence → IC Review → Closing
- **Deal cards**: Company name, sector, estimated deal size, days in stage, next action
- **Funnel chart**: Conversion rates between stages with % labels
- **Cycle time chart**: Average days per stage (bar chart)

---

### 4. LP Reporting Suite
**Layout**: Statement format + waterfall + performance cards

**Visual Elements**:
- **Capital account statement**: Table with beginning balance, contributions, distributions, appreciation, ending balance
- **Performance waterfall**: How $1 invested became $X (contributions, gains, distributions)
- **KPI cards**: IRR, TVPI, DPI, RVPI with trend comparison to benchmark
- **Cash flow timeline**: Gantt-style chart of expected distributions

---

### 5. Risk Dashboard
**Layout**: Heat map matrix + alert list

**Visual Elements**:
- **Risk matrix**: Impact (x-axis) vs. Likelihood (y-axis) with company bubbles sized by exposure
- **Alert list**: Sortable table of early warning indicators with severity badges
- **Covenant headroom gauge**: Dial chart showing cushion to breach thresholds
- **Churn risk barometer**: Visual indicator of predicted customer concentration risk

---

## Chart Type Selection

| Dashboard | Primary Chart | Secondary Chart | Tertiary |
|-----------|---------------|-----------------|----------|
| Portfolio Overview | Waterfall | Pie/Donut | KPI Cards |
| Company Performance | Data Table | Line Trend | Bar Comparison |
| Deal Pipeline | Kanban | Funnel | Bar (cycle time) |
| LP Reporting | Waterfall | Table | Line (trend) |
| Risk | Heat Map | Table | Gauge |

---

## Interaction Design

### Navigation
- Left sidebar menu with icons + labels (collapsible on mobile)
- Breadcrumb navigation for drill-down paths
- "Back to overview" persistent button

### Filters
- Global time period selector (affects all dashboards)
- Dashboard-specific filters in top toolbar
- Saved filter views for different user roles

### Drill-Down Paths
1. Portfolio → Fund → Portfolio Company → Quarterly Performance → Underlying Metrics
2. Deal Pipeline → Deal → Due Diligence Progress → Financial Model
3. Risk → Company → Risk Factors → Mitigation Actions

---

## Mobile Considerations (iPad)

- Touch-friendly: Minimum 44px tap targets
- Swipe navigation between dashboard sections
- Landscape orientation optimized
- Critical KPIs visible without scrolling
- Offline capability for boardroom use (cached data)

---

## Deliverables for Visuals

- [ ] Figma prototype of all 5 dashboard screens
- [ ] Component library (buttons, cards, charts)
- [ ] Color palette documentation
- [ ] Typography guide
- [ ] Responsive breakpoints specification
- [ ] Interaction flow diagrams
- [ ] Dashboard walkthrough video (5 minutes)
