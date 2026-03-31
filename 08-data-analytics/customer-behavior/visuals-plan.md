# Customer Behavior Analysis — Visuals Plan

## Dashboard Visual Structure

### 1. Customer Health Overview (Landing Page)
**Layout**: KPI cards + distribution + trend

**Visual Elements**:
- **Top row**: 4 KPI cards (Total Accounts, Avg Health Score, Activation Rate, Monthly Churn) with trend arrows
- **Middle**: Health score distribution histogram (Champions/Healthy/At-Risk/Critical)
- **Bottom left**: Churn risk scatter plot (health score vs. ACV, sized by account)
- **Bottom right**: 12-month retention curve by acquisition cohort

**Color Palette**: Green (#38A169) Champions, Blue (#3182CE) Healthy, Yellow (#D69E2E) At-Risk, Red (#E53E3E) Critical

---

### 2. Activation Intelligence
**Layout**: Funnel + milestone tracker + timeline

**Visual Elements**:
- **Funnel visualization**: 47 steps from signup → first appointment → ongoing
- **Activation milestone cards**: Key milestones with completion rates
- **Time-to-value histogram**: Days from signup to first successful action
- **Cohort heat map**: Activation rate by acquisition week
- **Alert list**: Accounts at day 10 with < 2 appointments

---

### 3. Retention Analytics
**Layout**: Cohort table + curves + drivers

**Visual Elements**:
- **Cohort retention table**: Rows = acquisition month, Columns = Month 1, 2, 3... 12
- **Retention curves**: Line chart comparing segments
- **Churn drivers**: Bar chart of top 10 churn risk factors
- **Retention lift by feature**: Horizontal bar chart

---

### 4. Behavioral Clusters
**Layout**: Cluster profiles + segment performance

**Visual Elements**:
- **Cluster distribution pie**: Power Users 12%, Basic Bookers 58%, Rare Users 22%, Dormant 8%
- **Cluster profile cards**: Defining characteristics of each cluster
- **Retention by cluster**: Side-by-side bar chart
- **Feature heat map**: Feature usage by cluster

---

### 5. CS Team Dashboard
**Layout**: Action list + account detail + performance

**Visual Elements**:
- **At-risk account list**: Prioritized by health score × ACV
- **Account detail drill-down**: Health score breakdown, risk factors, recommended actions
- **Intervention tracker**: Outreach status, response rates
- **CS team performance**: Accounts per CSM, health improvement rates

---

## Chart Type Selection

| Dashboard | Primary Chart | Secondary Chart | Tertiary |
|-----------|---------------|-----------------|----------|
| Health Overview | KPI Cards | Histogram | Scatter Plot |
| Activation | Funnel | Timeline | Heat Map |
| Retention | Cohort Table | Line Curves | Bar |
| Clusters | Pie | Profile Cards | Heat Map |
| CS Dashboard | Action List | Account Detail | Performance Table |

---

## Interaction Design

### Navigation
- Top-level tabs (Overview, Activation, Retention, Clusters, CS Tools)
- Left sidebar for sub-filters and saved views
- Quick search for individual account lookup

### Drill-Down Paths
1. Health Overview → Account Segment → Individual Account → Risk Factors → Recommended Actions
2. Activation → At-Risk List → Account → Journey Timeline → Intervention
3. Retention → Cohort Detail → Segment → Behavioral Drivers
4. Clusters → Cluster Detail → Member Accounts → Feature Usage

### Alert Integration
- Day 10 activation alerts appear as banner notifications
- Critical health score drops trigger immediate CSM notification
- Monthly digest email with cohort performance summary

---

## Mobile Considerations (CSM Field Use)

- Prioritized at-risk account list visible on mobile
- One-tap call/email from account card
- Health score and risk factors visible
- Intervention reminder notifications
- Read-only access for data security

---

## Deliverables for Visuals

- [ ] Figma prototype of all 5 dashboard screens
- [ ] Component library (health score cards, funnel, cohort table)
- [ ] Color palette documentation (semantic colors for health tiers)
- [ ] Icon set for feature categories
- [ ] Mobile wireframes for CSM app
- [ ] Print-friendly cohort reports for board
