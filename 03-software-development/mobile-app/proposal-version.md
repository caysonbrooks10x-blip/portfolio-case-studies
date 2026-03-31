# MealMoxie MVP — Proposal Version

## Executive Summary

MealMoxie is building the mobile meal benefit platform that corporate employees actually want to use. Current solutions require 48-hour catering orders or clunky stipend cards. MealMoxie gives employees a daily credit to order from any nearby restaurant in real-time — with the admin controls corporations need.

We propose a 12-week, fixed-price engagement to build a production-ready MVP: React Native app (iOS + Android), corporate dashboard, and core integrations.

---

## Scope of Work

### Phase 1: Validation & Architecture (Weeks 1-2)

**User Research:**
- 24 corporate employee interviews
- 8 HR director surveys
- Competitor analysis (DoorDash for Business, Cash App, Rally)
- 3 key differentiators identified

**Technical Decisions:**
- React Native (Expo) — 70% code sharing iOS/Android
- Node.js backend
- PostgreSQL + Redis
- Stripe Connect for corporate billing

### Phase 2: Design (Weeks 3-4)

- 40+ Figma frames covering complete user journey
- Design system with 120+ components
- 3 rounds of usability testing
- Animated micro-interactions

### Phase 3: Development (Weeks 5-10)

**Mobile App (iOS + Android):**
- Expo-managed React Native
- TypeScript throughout
- Redux Toolkit state management
- Google Places integration
- Stripe React Native SDK
- Offline order queueing
- Push notifications (Firebase)
- Real-time order tracking

**Backend API:**
- Express.js REST API
- PostgreSQL (Railway)
- Redis for sessions and caching
- Algolia restaurant search
- Stripe Connect webhooks
- Twilio SMS

**Corporate Dashboard:**
- Next.js web app
- Role-based access (Admin, Finance, Manager)
- Budget analytics
- Employee management

### Phase 4: QA & Launch (Weeks 11-12)

- 8-device test matrix
- Closed beta with 3 corporate partners
- TestFlight + Google Play Beta
- 48-hour bug squash
- Production deployment

---

## Investment

**Fixed Price: $195,000**

| Phase | Deliverable | Investment |
|-------|-------------|------------|
| Validation | User research, technical decisions | $22,000 |
| Design | Figma system, prototype, testing | $32,000 |
| Mobile App | iOS + Android (70% shared) | $78,000 |
| Backend API | Core API, integrations | $35,000 |
| Dashboard | Admin, Finance, Manager views | $18,000 |
| QA + Launch | Testing, beta, deployment | $10,000 |

**Payment Schedule:**
- 30% upon signing
- 30% at Week 4 milestone
- 40% upon final delivery

---

## Timeline

| Week | Milestone |
|------|-----------|
| 1-2 | Validation, architecture |
| 3-4 | Design approval |
| 5-8 | Core development |
| 9-10 | Features complete |
| 11 | QA, bug fixes |
| 12 | Beta launch |

---

## Key Differentiators

**Real-Time Ordering:** No 48-hour advance notice. Browse, order, eat — in under 30 seconds.

**Offline-First:** Corporate WiFi is unreliable. Orders queue locally and sync when connected.

**Corporate Controls:** Per-employee limits, category restrictions, real-time budget alerts.

**Code Sharing:** 70% shared code between iOS and Android. Ship both platforms for the price of one.

---

## ROI for MealMoxie

- **Development savings:** $80K+ vs building iOS and Android separately
- **Time savings:** 4 weeks faster vs native development
- **Quality:** 82% test coverage, 4.7 App Store rating
- **Scalability:** Architecture handles 10x expected load

---

## Next Steps

1. **Kickoff call** — Align on success metrics
2. **User research recruitment** — We help source interview participants
3. **Week 1:** Validation sprint begins

---

*Proposal valid 30 days. Timeline contingent on stakeholder availability.*
