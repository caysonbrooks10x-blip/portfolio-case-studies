# Nexus Freight — Objections & Responses

## Sales Objections

### "This seems like a big risk. What if the framework doesn't work for our carriers?"

**Response:**
"We've done this before — 3 times in logistics, twice in healthcare. The pattern-first approach de-risks the project:

1. **Week 1-4:** We analyze your 47 integrations, not guess at them. We find the actual patterns.
2. **Week 4:** You see the architecture based on real data, not assumptions.
3. **Week 4-14:** We build the core platform. You can kill the project if the architecture doesn't match reality.

The framework isn't theoretical. It's derived from your specific integrations."

---

### "Our carriers have unique requirements. A standard framework won't work."

**Response:**
"We've worked with 47 carriers. Yes, some have unique requirements. Here's the breakdown:

- **90% of functionality:** 6 common patterns (rate fetching, shipment creation, tracking, documents)
- **10% of functionality:** Carrier-specific quirks (special rate types, custom fields, unique auth)

The framework handles the 90% with a standardized interface. Adapters handle the 10% with clean extension points.

This is exactly how Stripe, Twilio, and Plaid work. They have standard APIs with carrier-specific implementations underneath. It scales."

---

### "Migration will be risky. We can't afford downtime."

**Response:**
"We've migrated 3 other logistics platforms. Here's the playbook:

**Weeks 12-15: Parallel Running**
- Old and new systems run simultaneously
- Every request validates against both
- Discrepancies trigger alerts
- We investigate, not you

**Weeks 15-18: Traffic Shifting**
- 10% of traffic on new system
- Monitor for 1 week
- 25% if metrics are green
- 50%, 75%, 100% gradually

**Zero downtime. Zero data loss.** We've done this 3 times. It works."

---

### "Our engineering team is already stretched thin. Where do we find time for this?"

**Response:**
"We staff the project with our team. Your engineers contribute:
- Week 1-4: Integration access and knowledge transfer (2-4 hours/week)
- Week 4-20: Review and feedback (2-4 hours/week)
- Week 12-18: Carrier migration assistance (optional, 4 hours/week)

You don't build this. We build this. Your team reviews and approves."

---

### "How do you handle carriers that don't have APIs?"

**Response:**
"Three options depending on carrier capability:

1. **Modern carriers (40%):** Real-time APIs. Webhook support. Full integration.
2. **Legacy carriers (50%):** EDI or polling-based. We build polling adapters with rate limiting.
3. **Manual carriers (10%):** Phone/fax. We build a manual workflow UI. Upload documents, enter data manually.

The framework handles all three. Most platforms give up on legacy carriers. We don't."

---

## Technical Objections

### "GraphQL adds complexity. Why not just use REST?"

**Response:**
"Two reasons:

1. **Shipper use cases vary.** Some need full shipment details. Some need just status. GraphQL lets each consumer request exactly what they need.
2. **Legacy compatibility.** We expose REST for existing integrations. GraphQL is opt-in for new consumers.

We learned from 3 other logistics projects: GraphQL adoption is higher when you don't force it. Start with REST, add GraphQL for complex queries."

---

### "How do you handle carrier API rate limits?"

**Response:**
"With a multi-layered approach:

1. **Per-carrier rate limiting:** Redis tracks requests per carrier. Exceed the limit? Queue with backoff.
2. **Circuit breakers:** If a carrier's error rate spikes, we stop requests for 30 seconds.
3. **Response caching:** Rates cached for 5-15 minutes (configurable). No API call needed.
4. **Request coalescing:** Multiple requests for same carrier/route consolidated.

We've implemented this for 3 other platforms. Carrier rate limit errors dropped from 3% to 0.02%."

---

### "How does the transformation engine handle complex mappings?"

**Response:**
"JSONata for transformations. Here's an example:

```
{ "origin": payload.shipFrom,
  "destination": payload.shipTo,
  "rate": payload.rateAmount * $.config.markup }
```

Simple mappings: JSONata expressions.
Complex mappings: Custom JavaScript functions registered in the engine.

We also built a visual editor for non-engineers. Your rate team can create transformations without writing code."

---

### "What happens when a carrier changes their API?"

**Response:**
"Adapter versioning. When a carrier changes their API:

1. **Detection:** Automated monitoring flags API changes (schema, errors, latencies)
2. **Versioning:** New adapter version created (v2)
3. **Testing:** New version runs in shadow mode
4. **Rollout:** Gradual traffic shift to new version

Your team gets alerted before users see errors. We've had to do this 8 times in 12 months. Average time to recover: 4 hours."

---

## Timeline Objections

### "We need this in 12 weeks, not 20. Can you compress?"

**Response:**
"Options for compression:

**Option A (12 weeks):**
- Core API Gateway only
- Migrate 10 carriers (not 20)
- Skip Developer Portal
- Tracking aggregation in Phase 2

**Option B (16 weeks):**
- Full platform
- 15 carrier migrations
- Basic portal (no sandbox)

**Option C (20 weeks, full):**
- Everything in scope
- 20 carrier migrations
- Full Developer Portal

What matters most: platform capability, or carrier count?"

---

### "Can we do a phased rollout where some carriers stay on the old system?"

**Response:**
"Yes — this is actually our recommendation.

**Phase 1 (Month 1-5):** 20 carriers on new platform
**Phase 2 (Month 6-8):** 15 more carriers
**Phase 3 (Month 9-12):** Remaining 12 carriers

Old system runs in parallel until all carriers migrate. Shippers see one API regardless of which system their carrier uses."
