# Funnel Analytics — Visuals Plan

## Dashboard Visual Structure

### 1. Marketing Overview (Landing Page)
**Layout**: KPI cards + channel breakdown + trend

**Visual Elements**:
- **Top row**: 4 KPI cards (Revenue, ROAS, Conversion Rate, Sessions) with trend arrows
- **Middle left**: Revenue by channel (attribution model selector)
- **Middle right**: ROAS by channel comparison (attributed vs. blended)
- **Bottom**: 12-week trend for key metrics

**Color Palette**: Purple (#553C9A) primary, Green (#38A169) positive, Red (#E53E3E) negative, Gray (#718096) neutral

---

### 2. Funnel Analysis Dashboard
**Layout**: Funnel visualization + drop-off table + trends

**Visual Elements**:
- **Funnel chart**: 8 major stages with conversion rates (animated)
- **Drop-off table**: Stage, sessions, drop-off count, drop-off rate, recommended action
- **Trend chart**: Stage conversion over time (line chart)
- **Device breakdown**: Conversion by device at each stage

---

### 3. Attribution Comparison
**Layout**: Model comparison + channel breakdown + waterfall

**Visual Elements**:
- **Model selector**: Dropdown to switch between 5 attribution models
- **Channel bar chart**: Revenue by channel (bars colored by model selection)
- **Waterfall chart**: How credit flows from first touch to last touch
- **Attribution shift table**: Which channels gain/lose credit under different models

---

### 4. A/B Test Results
**Layout**: Active tests + completed results + leaderboard

**Visual Elements**:
- **Active test cards**: Variant, sample size, current lift, confidence level, days remaining
- **Sequential chart**: Cumulative revenue by variant with confidence bands
- **Completed test table**: Test name, winner, lift, confidence, status (deployed/not)
- **Test leaderboard**: Top 10 highest-impact tests

---

### 5. Device & Geography Analysis
**Layout**: Device comparison + geo heat map + product matrix

**Visual Elements**:
- **Device funnel**: Side-by-side funnel for Desktop/Mobile/Tablet
- **Geo heat map**: Conversion rate by US state (color gradient)
- **Product performance matrix**: Conversion vs. AOV by product category
- **Browser breakdown table**: Conversion by Chrome/Safari/Firefox/Edge

---

## Chart Type Selection

| Dashboard | Primary Chart | Secondary Chart | Tertiary |
|-----------|---------------|-----------------|----------|
| Marketing Overview | KPI Cards | Bar (channel) | Line (trend) |
| Funnel Analysis | Funnel | Table | Line (trend) |
| Attribution | Bar (channel) | Waterfall | Comparison Table |
| A/B Testing | Sequential Chart | Test Cards | Leaderboard |
| Device/Geo | Side-by-Side Funnel | Heat Map | Scatter |

---

## Interaction Design

### Navigation
- Top tabs (Overview, Funnel, Attribution, Testing, Segments)
- Dashboard-level filters (date range, device, geography)
- Attribution model selector (affects all charts)

### Drill-Down Paths
1. Marketing Overview → Channel → Sub-campaign → Individual campaigns
2. Funnel → Stage → User segment → Sample journey
3. Attribution → Channel → Campaign → Ad set → Ad
4. A/B Test → Test Detail → Variant Analysis → Revenue breakdown

### Alert Integration
- Test significance achieved notification
- Funnel anomaly detection (conversion drop > 10%)
- Daily digest email with key metrics

---

## Mobile Considerations (for Executive Use)

- Daily KPI snapshot
- ROAS by channel summary
- Active test count and average lift
- Read-only dashboards

---

## Deliverables for Visuals

- [ ] Figma prototype of all 5 dashboard screens
- [ ] Component library (funnel, attribution bars, sequential chart)
- [ ] Color palette documentation
- [ ] Animation specs for funnel progression
- [ ] Print-friendly weekly report template
- [ ] Mobile wireframes for executive app
