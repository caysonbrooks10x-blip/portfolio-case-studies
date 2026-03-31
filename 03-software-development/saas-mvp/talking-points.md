# FieldSync Case Study — Talking Points

## For Sales Conversations

### Opening Hook
"FieldSync needed to build a field service platform to compete with ServiceTitan. They had 12 months of runway and a $180K budget. We delivered a production MVP in 9 weeks. Three months later, they closed an $8M Series A."

### Differentiator #1: Embedded Discovery
"We didn't just interview contractors — we rode along with field techs on actual service calls. That's how we discovered they couldn't type on iPads in 100°F attics. Voice notes became the flagship feature."

### Differentiator #2: Scope Discipline
"At Week 4, we cut 12 planned features to protect the timeline. Gas tank tracking moved to Phase 2. Most startups fail because they try to build everything. We helped FieldSync focus."

### Differentiator #3: Integration Depth
"We didn't build 'Stripe added' — we built full Stripe Connect with split payments, tipping, and refund workflows. We didn't build 'QuickBooks compatible' — we built bi-directional sync. That depth became their sales differentiator."

### Performance Obsession
"94 Lighthouse score. 120ms API p95. 99.94% uptime. We load-test every endpoint to 10x expected capacity before shipping. We caught a Redis bottleneck at 400 concurrent users that would have crashed their dispatch board."

### ROI Story
"They paid $178K. Agencies quoted $350K-$420K. That's $172K-$242K saved before they made a single dollar. And they launched 6 weeks faster than agency timelines."

---

## For Portfolio Presentations

### The Problem Slide
"FieldSync's founders saw that small contractors were stuck paying $99-$299/month for software field techs hated. They had domain expertise from ServiceTitan and Uber — they knew the problem intimately."

### The Insight Slide
"The breakthrough came from watching, not asking. We embedded with 4 contractor companies and rode along on service calls. One tech trying to type job notes in a hot attic — that visual changed everything."

### The Build Slide
"We chose a PWA over native apps to avoid App Store delays and maximize code reuse. 42,000 lines of code across frontend and backend. 87% test coverage. Every API endpoint load-tested to 10x capacity."

### The Results Slide
"From kickoff to 500 users in 14 weeks. $34.5K MRR at Month 3. 4.2% churn. Series A closed at $8M. The MVP became the foundation for their entire fundraising narrative."

---

## Objection Handlers

### "This seems too fast — can quality really be good?"
"Week 9 to beta doesn't mean 9 weeks of hacking. We have 6-week approval gates. Design isn't done until it passes our internal UX review. Code isn't done until it passes 87% test coverage and 94 Lighthouse."

### "How do you handle offline field conditions?"
"We built IndexedDB sync with conflict resolution. Field techs can complete full job reports offline — photos, signatures, parts used. Data syncs when connectivity returns. We tested this in buildings with zero signal."

### "What about scalability for 500+ users?"
"The architecture handles 10x that load. PostgreSQL on Railway for ACID compliance. Redis for session caching. We load-tested to 5,000 concurrent connections before shipping."

---

## Metrics to Quote

- **$178K** total development cost
- **$172K-$242K** saved vs agency quotes
- **9 weeks** from kickoff to beta launch
- **14 weeks** from launch to 500 users
- **94 Lighthouse** score
- **120ms** API response time (p95)
- **99.94%** uptime over 6 months
- **87%** test coverage
- **42,000** lines of code
- **4.2%** churn vs 22% industry average
- **$34.5K** MRR at Month 3
- **$8M** Series A closed 4 months post-launch
