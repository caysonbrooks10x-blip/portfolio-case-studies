# KPI Architecture — Objection Handling

## "We already have dashboards. Why do we need more?"

Most companies have dashboards that show what happened. They don't have:

- Unified definitions everyone agrees on
- Leading indicators that predict future performance
- KPI trees showing how team metrics connect to company metrics
- Governance that keeps definitions from drifting

Dashboards are a tool. A KPI architecture is a system. You can have 50 dashboards with inconsistent definitions — that's worse than 5 dashboards everyone trusts.

---

## "Defining metrics takes forever. We tried and it stalled out."

Yes, metric alignment is hard because it's political, not technical. Different teams have different incentives, and metrics reveal that.

I facilitate the working sessions with structured frameworks:
- Metric decision trees (if it's X, then it's Y)
- "Coin test" (would you bet your bonus on this number?)
- Owner assignment (every metric has a CEO, not a committee)

The goal isn't perfect consensus — it's agreed-upon definitions that everyone commits to. We typically reach alignment in 3 weeks, not 3 months.

---

## "Our metrics will keep changing as we learn. Won't this framework get outdated?"

The framework includes a change management process. When a metric needs to evolve:

1. Proposed change submitted to Metric Review Board
2. Impact analysis: How does this affect historical data?
3. Cross-functional review
4. Approval and implementation
5. Communication

The framework isn't rigid — it's governed. That's different.

---

## "We don't have dedicated data resources to maintain this."

The implementation is scoped to minimize ongoing burden:

- Fivetran handles connectors (no-code)
- dbt models are simple SQL (your team can maintain them)
- Looker dashboards are self-service for most queries
- Managed services option: we handle operations

Many clients start implementation, then move to managed services while building internal capability.

---

## "How do you validate leading indicators? They might just be noise."

Leading indicators are validated statistically:

1. Collect 18 months of historical data
2. Test correlation between proposed leading indicator and lagged outcome
3. Validate on out-of-time data (did it predict last quarter?)
4. Track prediction accuracy going forward

We don't ship leading indicators until they're validated. Most proposals fail validation — only 3-4 of 10 become useful predictors.

---

## "Different investors want different metrics. How do we handle that?"

The True North metrics are internal definitions. Investor-facing metrics are a separate layer.

We build:
- Internal True North with full definitions
- Investor dashboard that maps internal metrics to investor expectations
- Data room exports that match investor templates

The internal framework doesn't change when investors change. The mapping layer adapts.

---

## "OKRs are already a struggle. Won't this add more complexity?"

The KPI architecture makes OKRs easier, not harder:

Current state: "Improve customer satisfaction" with no way to measure
New state: "Improve NRR from 108% to 115%" with weekly progress tracking

Every OKR connects to a metric. Teams know exactly what success looks like. Progress is visible, not debated.

---

## "How do you handle metric gaming? Teams will optimize for the metric, not the outcome."

This is a real risk. We address it through:

1. **Multi-metric accountability**: No single metric determines success
2. **Leading + lagging mix**: Metrics that predict outcomes, not just measure them
3. **Narrative required**: Teams explain the story behind the numbers
4. **Outcome over output**: Product metrics tied to business outcomes, not shipped features

Gaming is minimized when metrics are well-designed. The Metric Review Board also monitors for gaming behavior.

---

## "This sounds expensive for a startup."

$95K is less than one senior hire's salary for 6 months.

Alternative costs:
- Misaligned teams causing execution drag: $500K+ in wasted equity
- Messy Series C data room: $100K+ in advisor fees
- Wrong decisions from bad data: Unquantifiable but real

The ROI is 4.2 months. That's fast for an infrastructure project.
