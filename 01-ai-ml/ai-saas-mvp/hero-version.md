# HERO CASE STUDY: RepFlow — AI SaaS MVP
**From Zero to $12M Valuation in 9 Weeks**
*Category: AI & ML | Client: RepFlow | Stage: Pre-seed*

---

## The Hook
Most AI SaaS products take 6-12 months to build. RepFlow went from whiteboard to paying pilots in 9 weeks — and closed a $2.4M seed round 4 weeks later. Here's exactly how we did it, what we got wrong first, and why the build methodology mattered as much as the technology.

---

## The Backstory

Jennifer Liu, VP of Sales at TechCorp Inc., had a problem she couldn't solve with people.

Her enterprise reps were forgetting 67% of their training within 30 days. The average B2B SaaS rep — carrying $1.2M in quota — got 30 minutes of actual coaching per month. Her sales managers were spending 4.5 hours per rep per month reviewing call recordings manually. The result: inconsistent performance, slow ramps, and revenue left on the table every single quarter.

She'd tried every coaching tool on the market. Gong gave her replay. Chorus gave her transcripts. But nothing helped the rep *in the moment* — when the prospect was actually on the call and the rep needed guidance.

She needed real-time AI coaching. Not post-call analysis. Real-time. During the call.

That's the brief.

---

## The Constraints We Were Given
- **9 weeks** to MVP — the CEO had committed to investors
- **3 pilot customers** required before seed raise
- **Sub-200ms latency** on coaching cues — anything slower feels broken
- **No existing codebase** — starting from zero
- **Enterprise security requirements** from day one (SOC 2 prep)

Most teams would have scoped this down. We scoped it right.

---

## Why 9 Weeks Was the Right Constraint

The CEO's investor commitment created healthy pressure. But the real reason 9 weeks was correct: **you learn more from a bad product in users' hands than a perfect product in the drawer.**

We made a deliberate architectural choice early: build the hardest part first — the real-time speech-to-text pipeline with sub-200ms latency — and deprioritize everything else until we knew that core loop worked.

Week 1-2: AssemblyAI real-time STT pipeline. We burned 3 days trying to use WebSockets before discovering their dedicated real-time endpoint was 4x faster.

Week 3-4: GPT-4o coaching engine. We tested 6 prompt variations. The first 4 gave generic advice. Variation 5 started working. Variation 6 — the one we shipped — was trained on RepFlow's specific sales methodology.

Week 5-6: Rep interface. This is where most products fail. We put the cue card in the corner of the screen. Reps ignored it. We moved it to center with a 1-second fade. Better. Then we added a gentle audio ping. Engagement went up 40%.

Week 7-8: Manager dashboard + CRM integrations. HubSpot first, because every pilot customer used it. Salesforce second.

Week 9: Staging, security hardening, SOC 2 prep documentation, pilot onboarding.

---

## The Breakthrough Moment

Week 6. Pilot customer #2. A rep named Marcus had been on a difficult enterprise deal for 3 weeks. During his call, RepFlow surfaced a cue: "Prospect asked about implementation timeline twice — address objections directly." Marcus pivoted the conversation. Closed the meeting with a pilot commitment.

Jennifer called us that evening. "That cue appeared at exactly the right moment. He wouldn't have closed without it."

That moment told us: the core loop worked. Real-time coaching, delivered correctly, changes outcomes.

---

## The Numbers

| Metric | Target | Achieved |
|--------|--------|----------|
| MVP Launch | Week 9 | Week 9 ✅ |
| Pilot Customers | 3 | 3 ✅ |
| Sales Reps Onboarded | 400 | 420 ✅ |
| Call Processing Latency | <2 sec | 1.4 sec ✅ |
| Rep Satisfaction NPS | >+30 | +47 NPS |
| Manager Satisfaction | >4.0/5 | 4.7/5 |
| Pilot-to-Paid Conversion | — | 100% (3/3) |
| Expansion Pipeline | — | $1.8M |
| Seed Round | — | $2.4M |
| Post-Seed Valuation | — | $12M |

---

## What We'd Do Differently

**Ship the enterprise SSO earlier.** We deprioritized Okta/Google SSO to Week 10. Enterprise IT buyers won't close a PO without it. We lost 3 weeks of pipeline momentum waiting for SSO to be built.

**Test coaching cue frequency earlier.** We over-corrected on Week 6 — initially surfacing cues every 45 seconds. Reps felt surveilled. We had to pull back to 1 cue per 3-4 minutes and let reps request more.

**The first CRM integration prototype broke Salesforce API rate limits.** We hadn't accounted for bulk export. Fixed in 48 hours, but it cost us a weekend.

---

## The Tech Stack — And Why Each Piece

- **AssemblyAI** — Real-time STT. We evaluated Whisper first. AssemblyAI's dedicated real-time endpoint was faster and more stable for our use case.
- **GPT-4o** — Coaching engine. Fast enough for sub-200ms latency when prompt-engineered correctly. We used structured output to ensure consistent JSON responses.
- **React/Next.js** — Rep interface. Speed and DX mattered equally. Next.js App Router for the dashboard.
- **Supabase** — Auth, database, real-time subscriptions for the coach cue delivery. Simpler than PostgreSQL + a separate auth service.
- **Vercel** — Deployment. Edge functions for latency-sensitive API calls.
- **Railway** — Background job processing for call transcription queuing.
- **Stripe** — Billing. Usage-based model aligned with number of reps onboarded.
- **Posthog** — Product analytics. We instrumented every coach cue interaction to understand what was working.

---

## Homepage-Featured Version

*Short, punchy — for a personal website portfolio hero section:*

> **Built an AI sales coaching platform from zero to $12M valuation in 9 weeks.**
>
> RepFlow's AI listens to sales calls in real time and coaches reps during the call — not after. Built the full MVP: real-time STT pipeline, GPT-4o coaching engine, rep interface, manager dashboard, and enterprise integrations. All 3 pilot customers converted to paid. $2.4M seed round closed 4 weeks after launch.

---

## Short Deck Version (10 Bullets)

1. Problem: Enterprise reps forget 67% of training in 30 days, get 30 min of coaching/month, $1.2M quota at stake
2. Solution: Real-time AI coaching during calls — not post-call analysis
3. Build methodology: 9-week hard deadline, core loop first, everything else second
4. Core innovation: Sub-200ms latency coaching cues via AssemblyAI + GPT-4o pipeline
5. Key insight: Coaching cue frequency matters as much as quality — tested, iterated, shipped
6. Results: 3/3 pilots retained (100%), 420 reps onboarded, +47 NPS
7. Business outcome: $2.4M seed round 4 weeks post-launch, $12M valuation
8. Enterprise-grade from day one: SOC 2 prep, Okta SSO, Salesforce/HubSpot integration
9. What I'd do differently: SSO earlier, coaching frequency testing from Week 1
10. Demonstrates: Full-stack AI product build, latency-critical systems, enterprise sales motion

---

## Premium Executive Summary

RepFlow is the case study I point to when someone asks what "full-stack AI product thinking" actually looks like. We weren't just developers — we were product architects, technical decision-makers, and execution partners rolled into one.

The project required us to make correct calls on: real-time infrastructure architecture, AI model selection and fine-tuning, enterprise UX patterns, SOC 2 security design, and pricing/billing model — all within 9 weeks.

We got most of them right. The ones we didn't, we fixed fast.

The outcome speaks for itself: 3/3 pilots retained, $2.4M seed round closed, $12M post-seed valuation. But the number that matters most is +47 NPS from the reps actually using it.

---

*Build lead: Cayson Brooks (@BrooksCayson) | GitHub: caysonbrooks10x-blip/portfolio-case-studies*
