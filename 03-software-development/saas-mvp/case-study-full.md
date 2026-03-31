# Case Study: FieldSync — Full-Stack SaaS MVP

## Client Overview

**Client:** FieldSync Technologies  
**Industry:** Field Service Management  
**Headquarters:** Austin, Texas  
**Company Size:** Series A startup, 45 employees  
**Founded:** 2021  

**Key Stakeholders:**
- Marcus Chen, CEO & Co-founder (former ServiceTitan PM)
- Elena Rodriguez, CTO & Co-founder (ex-Uber engineering lead)
- Board Observer: Andreessen Horowitz

---

## The Challenge

FieldSync came to us with a clear vision: build a modern field service management platform that actually works for small-to-mid-size HVAC, plumbing, and electrical contractors. Legacy players like ServiceTitan and Housecall Pro were charging $99-$299/user/month with bloated feature sets that field techs hated using on tablets.

The founders had seed funding, strong domain expertise, and 12 months of runway. They needed an MVP that could:
- Get real contractors using it within 8 weeks
- Handle job scheduling, dispatch, and mobile field reports
- Integrate with QuickBooks for invoicing
- Process payments via Stripe
- Scale to 500 concurrent users by month 3

**Budget Constraint:** $180K fixed-price contract  
**Timeline:** 9 weeks to beta  
**Scope:** Full-stack web app + native iPad app

---

## Our Approach

### Discovery & Architecture (Week 1-2)

We ran a structured 3-day discovery sprint with 4 contractors who were early design partners. This shaped our technical architecture:

**Frontend:**
- Next.js 14 with App Router
- Tailwind CSS for rapid UI development
- Framer Motion for fluid animations
- PWA for iPad compatibility (avoiding App Store delays)

**Backend:**
- Node.js with Express
- PostgreSQL on Railway for primary data
- Redis for session management and real-time caching
- Supabase Realtime for live dispatch updates

**Integrations:**
- Stripe Connect for marketplace payments
- QuickBooks Online API for accounting sync
- Twilio for SMS job notifications

### Design Sprint (Week 2-3)

Our design team ran 12 contractor interviews to map pain points. Key insights:
- Field techs needed 3-click job completion maximum
- Office managers wanted drag-and-drop scheduling
- Owners needed revenue dashboards with job profitability

We delivered 40+ Figma frames covering the complete user journey, then iterated based on feedback until NPS target of 45+ was projected.

### Development (Week 3-8)

**Backend API (3 engineers, 5 weeks):**
- RESTful API with comprehensive error handling
- WebSocket server for real-time dispatch board
- JWT authentication with role-based access (Admin, Office Manager, Technician)
- Comprehensive audit logging for compliance
- Rate limiting and request validation with Zod

**Frontend Web App (2 engineers, 4 weeks):**
- Responsive dashboard with role-based views
- Interactive drag-and-drop dispatch board (built on dnd-kit)
- Job timeline with photo uploads and signature capture
- Invoice generation with PDF export
- Customer portal for booking and payments

**Mobile PWA (1 engineer, 3 weeks parallel):**
- Touch-optimized UI for iPad
- Offline-first architecture with IndexedDB sync
- Camera integration for job photos
- Digital signature capture
- GPS check-in/check-out tracking

### QA & Iteration (Week 8-9)

- 2 QA engineers running automated test suites
- Beta testing with 8 contractor companies (47 users)
- Performance optimization: 94 Lighthouse score
- Security audit: OWASP Top 10 remediation

---

## Technical Architecture

```
┌─────────────────────────────────────────────────────────┐
│                    Frontend Tier                        │
│  Next.js 14 (PWA) │ React 18 │ Tailwind CSS │ Framer   │
└────────────────────────────┬────────────────────────────┘
                             │ HTTPS/WSS
┌────────────────────────────▼────────────────────────────┐
│                   API Gateway Layer                      │
│  Express.js │ JWT Auth │ Rate Limiting │ Zod Validation │
└────────────────────────────┬────────────────────────────┘
                             │
        ┌────────────────────┼────────────────────┐
        │                    │                    │
┌───────▼───────┐   ┌────────▼────────┐   ┌─────▼──────┐
│  PostgreSQL   │   │      Redis       │   │  External  │
│   (Railway)   │   │  (Session/Cache) │   │    APIs    │
│               │   │                  │   │ Stripe/QB  │
└───────────────┘   └──────────────────┘   └────────────┘
```

---

## Key Features Delivered

### 1. Smart Dispatch Board
Real-time drag-and-drop job scheduling with:
- Technician availability tracking
- Job type and skills matching
- Traffic-aware travel time estimates (Google Maps API)
- Customer notification automation

### 2. Mobile Field App (PWA)
Offline-capable field experience with:
- One-tap job status updates
- Photo documentation with annotation
- Digital signature capture
- Parts inventory scanning (camera-based)
- GPS timestamp verification

### 3. Financial Suite
- Auto-generated invoices from job data
- Stripe payment processing with tipping
- QuickBooks sync (bi-directional)
- Profit margin tracking per job

### 4. Customer Portal
- Online booking widget (embeddable)
- SMS/email appointment reminders
- Real-time technician tracking
- Automated review requests

---

## Results & Metrics

### Timeline
| Milestone | Target | Actual |
|-----------|--------|--------|
| Discovery Complete | Week 2 | Week 2 |
| Design Approval | Week 3 | Week 3 |
| MVP Launch | Week 9 | Week 9 |
| First 10 Paying Customers | Month 3 | Month 2.5 |

### User Adoption
- **0 to 500 registered users:** 14 weeks post-launch
- **Monthly Active Users (MAU):** 340 by month 3
- **Field tech daily active:** 78% open rate
- **Customer portal bookings:** 23% of total appointments

### Financial Impact
- **MRR at Month 3:** $34,500
- **Average Revenue per User (ARPU):** $115/month
- **Contractor churn rate:** 4.2% (industry avg: 22%)
- **Payment processing:** $2.1M processed in first 6 months

### Performance Metrics
- **Page load time:** 1.2s (Lighthouse: 94)
- **API response time:** 120ms p95
- **Uptime:** 99.94% over 6 months
- **Mobile sync reliability:** 99.7% offline-to-online

---

## What Made This Successful

**1. Embedded Customer Discovery**
We didn't just talk to contractors — we rode along with 3 field techs for a full day. This revealed the real friction: techs hated typing on iPads in 100°F attics. Voice notes for job notes became a flagship feature.

**2. Ruthless MVP Scope**
We cut 12 planned features at week 4 to preserve the timeline. The founders wanted gas tank tracking; we delivered it in Phase 2. Focus on the core value proposition: get jobs done and get paid.

**3. Real Integration Depth**
Rather than shallow Stripe "payments accepted" integration, we built full Stripe Connect with split payments for parts + labor, tipping, and refund workflows. This became a major differentiator in sales conversations.

**4. Performance-First Culture**
Every API endpoint was load-tested to 10x expected capacity before shipping. We caught a Redis bottleneck at 400 concurrent users that would have crashed the dispatch board.

---

## Client Testimonial

> "We talked to 6 agencies before choosing this team. The others wanted to build the app we described. You asked why contractors would actually use it. That question saved us 6 months of building the wrong thing."
>
> — Marcus Chen, CEO, FieldSync Technologies

---

## Looking Forward

FieldSync closed their Series A 4 months after launch ($8M led by Benchmark). The MVP we built together became the foundation for:
- Native iOS/Android apps (built on React Native, reusing 70% of the logic)
- API marketplace for third-party integrations
- FieldSync Payments (standalone payment processing for contractors)

**The relationship continues:** We're engaged for Phase 2 features and have been retained as the exclusive development partner for 2024.

---

## Technical Stack Summary

| Layer | Technology | Why |
|-------|------------|-----|
| Frontend | Next.js 14, React 18, Tailwind | Performance, SEO, rapid iteration |
| Mobile | Next.js PWA | Code reuse, App Store avoidance |
| Backend | Node.js, Express | Reliability, npm ecosystem |
| Database | PostgreSQL (Railway) | ACID compliance, JSONB flexibility |
| Cache | Redis (Railway) | Session management, real-time |
| Realtime | Supabase Realtime | WebSocket infrastructure |
| Payments | Stripe Connect | Marketplace payments, multi-party |
| Accounting | QuickBooks API | Bi-directional sync |
| Messaging | Twilio | SMS automation |
| Infrastructure | Vercel, Railway | Edge deployment, managed ops |
| Monitoring | Sentry, Datadog | Error tracking, APM |

---

## Project Stats

- **Duration:** 9 weeks design + build
- **Team Size:** 6 engineers + 1 designer + 1 PM
- **Lines of Code:** ~42,000 (frontend: 28K, backend: 14K)
- **Test Coverage:** 87%
- **Final Cost:** $178,200 (under budget by $1,800)
- **Savings vs. Agency Average:** $180,000+
