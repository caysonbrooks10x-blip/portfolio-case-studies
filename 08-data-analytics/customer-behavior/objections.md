# Customer Behavior Analysis — Objection Handling

## "We already have Mixpanel / Amplitude. Isn't that enough?"

Native analytics tools show what happened, not why it happened or what will happen next. They're dashboards, not intelligence systems.

What you're likely missing:
- Cross-session user identity resolution
- Predictive scoring (not just historical metrics)
- Operational integration (CSMs don't live in Mixpanel)
- HIPAA-compliant de-identification for ML workloads

Amplitude/Mixpanel is a starting point. We build the intelligence layer on top.

---

## "Healthcare data is too sensitive for this kind of tracking."

You're right to be cautious — HIPAA compliance is non-negotiable. We built a healthcare-specific architecture:

- PHI never leaves your systems
- Events track behaviors, not patient data (e.g., "Appointment:Completed" not "Dr. Smith treated patient for X")
- De-identification pipeline for any ML workloads
- BAA with Mixpanel in place
- Audit logs for all data access

We've worked with 4 healthcare companies. Compliance is built into the architecture, not bolted on.

---

## "Our users won't accept this level of tracking."

Tracking is on the provider side, not patients. Providers already accept similar tracking in EHR systems and practice management software. This is industry-standard.

We work with your legal team to ensure:
- Terms of service updates if needed
- Privacy policy language
- User consent flows
- Data retention policies

Most providers don't notice — they're focused on patient care, not analytics.

---

## "We tried segmenting customers before and it didn't change outcomes."

Segmenting without operational hooks is just coloring pictures. The value comes from:
1. Segments that predict behavior (not just describe it)
2. Workflows that act on segment membership
3. Feedback loops that refine segments over time

We build all three. Segments aren't the deliverable — operationalized interventions are.

---

## "How do you measure behavioral attribution? It's hard to know which touchpoints matter."

Multi-touch attribution is hard. We use a combination approach:

1. **First-touch attribution**: Which channel brought the customer
2. **Linear attribution**: Equal credit across all touchpoints
3. **Time-decay attribution**: More credit to recent touchpoints
4. **Survival analysis**: Which behaviors are associated with longer tenure

For retention specifically, we use survival models that identify which early behaviors are statistically associated with higher retention — controlling for other factors.

---

## "This sounds like it takes a long time to implement."

24 weeks end-to-end. But we phase delivery:

- Week 8: Instrumentation live, baseline cohort analysis
- Week 12: Health scores operational
- Week 16: First retention model validated
- Week 24: Full operationalization

You'll have insights in 8 weeks. The full system takes 24 weeks to properly operationalize.

---

## "Our CS team is already overwhelmed. How do we add more tools?"

The goal is to REDUCE CS burden, not increase it.

Current state: CSMs manually review accounts, often too late to intervene.

New state: Automated alerts tell CSMs exactly which accounts need attention and why. Prioritized. Actionable.

We also implement via Census — insights flow INTO your existing tools (Salesforce, Zendesk) so CSMs don't need another dashboard.

---

## "What if the model is wrong and we bother customers with unnecessary outreach?"

Valid concern. We built safeguards:

- Confidence thresholds (only alert on 70%+ probability)
- A/B test intervention sequences vs. control groups
- Track false positive rates and adjust thresholds quarterly
- CSM discretion — they see the score, they decide on outreach

We're not replacing CSM judgment — we're augmenting it with data.

---

## "How do we know the model isn't biased against smaller practices?"

Model fairness is a real concern. We address it through:

- Feature normalization (percentage-based, not absolute)
- Separate calibration curves for different practice sizes
- Bias testing across demographic groups
- Regular review of model decisions by CS leadership

If smaller practices are being flagged unfairly, we find out why and fix it.
