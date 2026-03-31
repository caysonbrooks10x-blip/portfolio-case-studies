# FieldSync Case Study — Objections & Responses

## Sales Objections

### "This seems too fast. Can you really build a quality MVP in 9 weeks?"

**Response:**
"Yes — because we've done it 4 times in 18 months. Speed comes from discipline, not shortcuts. Here's our process:

- Week 1-2: Architecture and discovery only. No coding until we understand the problem.
- Week 3: Design frozen after 3 rounds of iteration with your design partners.
- Week 4: Scope lock. We cut 12 features to protect the timeline. You signed off.
- Weeks 5-8: Full development with daily standups and weekly demos.
- Week 9: QA, bug bash, and production deployment.

We don't skip steps. We skip features that don't serve the core value proposition. And we have a 94 Lighthouse score to prove quality wasn't sacrificed."

---

### "We were quoted $350K by an agency. How can you do it for $180K?"

**Response:**
"Three reasons:

1. **No bureaucracy.** A 6-person agency has 40 billable roles between you and the engineers. We have 7 people who care about your success.
2. **Reusable components.** We've built 4 field service apps. We bring patterns, not just programmers.
3. **Honest scope.** We tell you what you need vs. what you want. That discipline protects both of us.

The $350K quote included 6 months of discovery, a native iOS app, and a CMS you didn't need. We stripped that to what gets you to revenue: web dashboard, mobile PWA, and payments. If you want to add features later, we're available."

---

### "What if we need to pivot after we launch?"

**Response:**
"Then you pivot. The architecture is modular — dispatch board, payment processing, customer portal — each is a separate service. If your go-to-market shifts from B2C booking to B2B enterprise, we can reconfigure without rebuilding.

We also build with this in mind: database schemas are flexible, APIs are versioned, and we document decisions in ADRs (Architecture Decision Records). You own the code. You can move it anywhere."

---

### "How do we know this will scale past 500 users?"

**Response:**
"Because we load-tested to 5,000 concurrent connections before shipping. We caught a Redis bottleneck at 400 users in staging — and fixed it before you ever saw it.

PostgreSQL on Railway handles connection pooling automatically. Supabase Realtime scales horizontally. Stripe handles payment volume — they've processed billions for companies much larger than yours.

If you hit 50,000 users, we architect for that in Phase 2. MVPs don't need to scale to enterprise on day one."

---

### "Our CTO wants to build this in-house eventually. What's the transition plan?"

**Response:**
"Full code ownership. You get every line we write. We use standard languages — TypeScript, Node.js, SQL — not proprietary frameworks. Any competent engineer can read and maintain it.

We also provide:
- 40-page technical documentation
- Architecture diagrams
- Runbook for production deployment
- 30-day post-launch support period

If you want to hire an in-house team at Month 6, your new engineers will have a clean codebase and comprehensive docs. We can even do knowledge transfer sessions."

---

## Technical Objections

### "We're concerned about offline functionality for field techs."

**Response:**
"We built a custom offline-first architecture using IndexedDB and a sync queue with conflict resolution. Here's what that means practically:

- Full job reports can be completed with zero connectivity
- Photos are compressed and stored locally until sync
- Signatures are captured as vector data
- When connectivity returns, data syncs automatically
- Conflicts are flagged for office manager review

We tested this in buildings with no signal — three different contractors across Texas in July. Works perfectly."

---

### "QuickBooks integration sounds complex. What happens when Intuit changes their API?"

**Response:**
"We built an abstraction layer between QuickBooks and your app. When Intuit deprecates endpoints (they do this every 18 months), we update one service — not your entire system.

We also store a local cache of QB data so your app never waits on QuickBooks' response times. Sync happens asynchronously."

---

### "Security is a concern. How do you handle payment data?"

**Response:**
"We never touch raw card data. Stripe handles all PCI compliance on their infrastructure. We pass payment tokens, not card numbers.

Our code was audited against OWASP Top 10 before launch. We use:
- JWT with RS256 signing
- Role-based access control at every endpoint
- Request validation with Zod
- Rate limiting to prevent abuse
- Comprehensive audit logging

Your production app passed a security review. That's not a checkbox — it's a culture."

---

## Timeline Objections

### "We need to launch in 6 weeks, not 9. Can you compress?"

**Response:**
"We can, but it costs more and reduces quality. Here's what compresses:

- Remove customer portal (saves 1 week)
- Ship a simpler dispatch board without drag-drop (saves 4 days)
- Skip the beta testing phase (saves 1 week, adds risk)

Or: launch with 70% of features in 6 weeks, then iterate. That's the agile approach. We'd recommend that anyway — you learn more from real users than from planning."

---

### "Our board wants quarterly milestones. Can we phase this?"

**Response:**
"Absolutely. Here's how we'd structure it:

**Phase 1 (Weeks 1-9):** Core MVP — dispatch, mobile field app, payments
**Phase 2 (Months 4-6):** Customer portal, SMS automation, advanced reporting
**Phase 3 (Months 7-12):** Native apps, API marketplace, enterprise features

Each phase is a separate contract. You only pay for what you need when you need it. And you can bench us between phases if priorities shift."
