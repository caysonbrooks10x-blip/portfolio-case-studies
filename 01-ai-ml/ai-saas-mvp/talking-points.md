# Talking Points: RepFlow — AI SaaS MVP Build

## Opening Hook

"RepFlow came to me with a pitch deck and a vision. Nine weeks later, they had a fully functional product, 3 enterprise pilot customers, 420 users, and a $2.4M seed round at a $12M valuation. That's what happens when you combine a strong founding team, a clear market insight, and relentless execution focus."

## Problem Articulation

- "Enterprise sales reps generate $1.2M annually on average — yet they receive about 30 minutes of coaching per month. That's a massive asset being underutilized due to lack of bandwidth."
- "67% of sales training is forgotten within 30 days. The $12B annual US sales training investment is largely ineffective."
- "Existing call intelligence tools (Gong, Chorus) only analyze calls after they end. By then, the moment to coach has passed."
- "Sales managers spend 4.5 hours per rep per month reviewing calls manually — time that doesn't scale as teams grow."

## Solution Highlights

- "Real-time speech-to-text using AssemblyAI's streaming API — 45ms audio capture to text, speaker diarization included."
- "GPT-4o coaching engine detecting objections (7 categories, 23 subtypes), sentiment shifts, talk-ratio issues, and buying signals in real-time."
- "Sub-200ms cue delivery — faster than human perception. Reps see coaching cues without missing a beat in conversation."
- "Post-call AI summaries generated in 90 seconds — executive summary, performance scorecard, sentiment timeline, follow-up recommendations."
- "Manager dashboard showing team coaching priorities, individual rep trends, and call library with AI annotations."
- "HubSpot and Salesforce integration — automatic call logging, AI summary attachment, deal risk scoring."

## Results & Proof Points

- "9 weeks from kickoff to pilot launch — on time, on budget."
- "420 sales reps onboarded across 3 enterprise customers."
- "1.4 second call processing latency — beat our 2-second target."
- "+47 NPS from pilot participants — far exceeding our +30 target."
- "4.7/5 manager satisfaction score."
- "$2.4M seed round closed 4 weeks post-pilot."
- "$12M post-seed valuation."

## Technical Credibility

- "AssemblyAI for real-time speech-to-text — best-in-class accuracy, streaming API with speaker diarization."
- "GPT-4o for coaching engine — structured prompts, objection taxonomy, adaptive cue frequency."
- "WebSocket for real-time cue delivery — 20ms end-to-end delivery latency."
- "Supabase for database, auth, and real-time subscriptions."
- "Vercel and Railway for deployment — auto-scaling infrastructure."
- "Pre-warmed GPT-4o connections and local cue caching for latency optimization."

## Why This Matters for Prospects

- "AI SaaS is different from AI services. The product has to work flawlessly from day one because customers are paying for ongoing value, not project completion."
- "Real-time systems have no margin for error. 200ms latency feels instantaneous. 500ms feels broken. We obsessed over latency from day one."
- "Enterprise features are not optional for B2B SaaS. Building SOC 2 prep, SSO, and RBAC into the MVP enabled enterprise sales immediately."

## Lessons Learned Highlights

- "Real-time latency is a product problem, not just technical — every 100ms slower reduces effectiveness 15%."
- "Build enterprise-ready from day one — SOC 2 prep, SSO, RBAC added 2 weeks but enabled enterprise deals."
- "First 3 customers define your product — select for feedback willingness, not just revenue."
- "AI summaries must be perfect before launch — users forgive imperfect real-time cues, not imperfect written summaries."

## Closing / CTA

- "Building an AI SaaS product? I offer complimentary 30-minute MVP scoping sessions for qualified founders."
- "The difference between a successful MVP and a failed one is often 2 weeks of polish at the end. Don't ship broken."
