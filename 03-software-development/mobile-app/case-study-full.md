# Case Study: MealMoxie — Mobile App MVP

## Client Overview

**Client:** MealMoxie Inc.  
**Industry:** Food Tech / Consumer Mobile  
**Headquarters:** Los Angeles, California  
**Company Size:** 8 employees, $2.1M seed funding  
**Founded:** 2023  

**Key Stakeholders:**
- Priya Sharma, CEO & Co-founder (former Uber Eats GM)
- Daniel Park, CTO & Co-founder (ex-Square engineering)
- Alex Rivera, Head of Product

---

## The Challenge

MealMoxie's thesis was simple but powerful: corporate meal benefits are broken. Companies spend millions on catering, food stipends, and meal allowances — and the experience is terrible. Catering orders require 48-hour advance notice. Stipends get spent on groceries randomly. No one knows what's left in their budget.

Priya had seen this firsthand at Uber Eats: companies wanted flexible, immediate meal benefits, and existing solutions couldn't deliver.

The vision: a mobile app where employees get a daily meal credit, order from any nearby restaurant in real-time, and managers get a dashboard showing utilization and spend.

**The catch:** They had $2.1M in seed funding, needed to launch in 12 weeks to hit a critical corporate partnership milestone, and had never built a mobile app before.

**Technical Requirements:**
- iOS and Android (React Native)
- Real-time ordering (under 30-second checkout)
- Corporate dashboard for admins
- SSO integration (Okta, Azure AD)
- Stripe for corporate billing
- Location-based restaurant discovery

**Budget:** $195,000  
**Timeline:** 12 weeks to beta  

---

## Our Approach

### Week 1-2: Validation Sprint

Before writing code, we validated assumptions:

**User Research:**
- Interviewed 24 corporate employees about meal benefits pain
- Surveyed 8 HR directors about administration challenges
- Analyzed competitor apps (Cash App, DoorDash for Business, Rally)
- Identified 3 key differentiators: real-time ordering, universal restaurant support, budget controls

**Technical Discovery:**
- Evaluated React Native vs Flutter vs Native
- Chose React Native for code sharing (iOS + Android from one codebase)
- Designed offline-first architecture for poor connectivity
- Mapped Stripe corporate billing complexity

**Decision:** React Native with a backend API. 70% code reuse between platforms was the key driver.

### Week 3-4: Design

**UX Process:**
- 3 rounds of usability testing with corporate employees
- 40+ Figma frames covering complete user journey
- Design system with 120+ components
- Animated micro-interactions for delight

**Key UX Decisions:**
- One-tap reordering from favorite restaurants
- Visual budget tracker always visible
- Corporate card integration for seamless checkout
- Push notifications for order status

### Week 5-10: Development

**Mobile App (React Native):**
- Expo for faster iteration and easier builds
- TypeScript throughout
- Redux Toolkit for state management
- React Navigation for routing
- Stripe React Native SDK
- Google Places API for restaurant discovery
- Geolocation for nearby restaurants

**Backend (Node.js):**
- Express.js REST API
- PostgreSQL on Railway
- Redis for session and order caching
- Firebase Cloud Messaging for push notifications
- Twilio for SMS order confirmations
- Algolia for restaurant search

**Corporate Dashboard (React Web):**
- Next.js for SEO and performance
- Recharts for analytics visualizations
- Role-based access (Admin, Finance, Manager)

**Integrations:**
- Okta SSO (SAML 2.0)
- Azure AD (OAuth 2.0)
- Stripe Corporate Billing
- Restaurant POS integrations (Toast, Square)

### Week 11-12: QA & Launch

- Internal testing team (8 devices)
- Closed beta with 3 corporate partners (150 users)
- Performance optimization (app size, launch time)
- TestFlight and Google Play Beta deployment
- 48-hour bug squash marathon

---

## Technical Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    Mobile App (React Native)                │
│            iOS + Android (70% shared codebase)              │
└────────────────────────────┬────────────────────────────────┘
                             │ HTTPS + REST + WSS
┌────────────────────────────▼────────────────────────────────┐
│                     API Gateway                              │
│              Express.js │ JWT │ Rate Limiting               │
└──────┬────────────────────┬────────────────────┬───────────┘
       │                    │                    │
┌──────▼──────┐   ┌─────────▼─────────┐  ┌──────▼────────┐
│  PostgreSQL  │   │      Redis        │  │   Firebase    │
│   (Railway)  │   │  (Orders/Sessions) │  │    (Push)     │
└─────────────┘   └───────────────────┘  └───────────────┘

       ┌────────────────────┬────────────────────┐
       │                    │                    │
┌──────▼──────┐   ┌─────────▼─────────┐  ┌──────▼────────┐
│   Stripe    │   │   Algolia         │  │   Google      │
│  (Billing)  │   │  (Restaurant      │  │   Places      │
│             │   │   Search)          │  │  (Location)   │
└─────────────┘   └───────────────────┘  └───────────────┘

┌─────────────────────────────────────────────────────────────┐
│              Corporate Dashboard (Next.js)                   │
│                   Admin │ Finance │ Manager                  │
└─────────────────────────────────────────────────────────────┘
```

---

## Key Features Delivered

### 1. Real-Time Ordering
- Browse nearby restaurants with real-time ETAs
- One-tap reorder from favorites
- Custom dietary filters (vegan, gluten-free, halal)
- Split-item ordering for teams
- Real-time order tracking with driver location

### 2. Daily Meal Credit Wallet
- Visual balance indicator (never overspend)
- Rollover settings (daily/weekly/monthly)
- Multi-currency support for global teams
- Spending history with receipt photos
- Automatic tax calculation

### 3. Corporate Dashboard
- Budget utilization heat maps
- Employee spending reports
- Restaurant preference analytics
- Invoice management and reconciliation
- SSO integration (Okta, Azure AD)

### 4. Smart Suggestions
- AI-powered restaurant recommendations based on:
  - Past orders
  - Dietary preferences
  - Team preferences (for group orders)
  - Time of day patterns

### 5. Manager Controls
- Set per-employee spending limits
- Restrict restaurant categories
- Approve high-value orders
- Real-time budget alerts

---

## Results & Metrics

### Timeline
| Milestone | Target | Actual |
|-----------|--------|--------|
| Validation Complete | Week 2 | Week 2 |
| Design Approval | Week 4 | Week 4 |
| iOS App Beta | Week 10 | Week 10 |
| Android App Beta | Week 11 | Week 11 |
| Corporate Beta | Week 12 | Week 12 |

### User Acquisition (First 6 Months)
| Metric | Month 1 | Month 3 | Month 6 |
|--------|---------|---------|---------|
| Corporate partners | 3 | 12 | 34 |
| Registered employees | 150 | 2,400 | 8,900 |
| MAU | 89 | 1,680 | 6,200 |
| Orders per month | 312 | 8,400 | 31,000 |

### Financial Metrics
| Metric | Month 3 | Month 6 |
|--------|---------|---------|
| GMV (Gross Merchandise Value) | $142K | $890K |
| Platform take rate | 12% | 14% |
| Revenue | $17K | $125K |
| Average order value | $24.50 | $28.70 |
| Corporate retention | 100% | 97% |

### App Performance
| Metric | Target | Achieved |
|--------|--------|----------|
| App launch time | < 3s | 2.4s |
| Checkout time | < 30s | 22s |
| Crash rate | < 1% | 0.3% |
| App Store rating | 4.5+ | 4.7 |
| Push notification open rate | > 40% | 52% |

---

## What Made This Successful

**1. Realistic Timeline Management**
We cut 4 features at Week 6 to protect launch. Catering scheduling and multi-team orders moved to Phase 2. Focus on the core loop: browse, order, eat.

**2. React Native Code Sharing**
70% code sharing between iOS and Android. When we fixed a bug on one platform, it was fixed on both. This accelerated development by an estimated 4 weeks.

**3. Corporate Beta Program**
We recruited 3 corporate partners for closed beta. Their feedback identified 47 bugs and 12 UX improvements before public launch. This saved us from negative reviews that would have killed early momentum.

**4. Offline-First Architecture**
Corporate environments have terrible WiFi. We built offline order queueing — orders sync when connectivity returns. This was a key differentiator vs. competitors.

---

## Client Testimonial

> "We had 12 weeks and a $2M seed round to build something that took Uber Eats 2 years. We didn't just need a development team — we needed a partner who understood mobile, could make hard scope decisions, and could launch. We got all three."
>
> — Priya Sharma, CEO, MealMoxie

---

## Technical Stack Summary

| Layer | Technology | Why |
|-------|------------|-----|
| Mobile | React Native (Expo) | Code sharing, faster iteration |
| Language | TypeScript | Type safety across platforms |
| State | Redux Toolkit | Predictable state management |
| Navigation | React Navigation | Standard RN navigation |
| Backend | Node.js, Express | Reliability, npm ecosystem |
| Database | PostgreSQL (Railway) | ACID, JSONB flexibility |
| Cache | Redis | Order sessions, real-time data |
| Search | Algolia | Fast restaurant search |
| Location | Google Places | Restaurant discovery |
| Payments | Stripe Connect | Corporate billing, split payments |
| Push | Firebase Cloud Messaging | Cross-platform notifications |
| SMS | Twilio | Order confirmations |
| Dashboard | Next.js | SEO, performance |
| Analytics | Mixpanel | User behavior tracking |

---

## Project Stats

- **Duration:** 12 weeks
- **Team Size:** 5 engineers + 1 designer + 1 PM
- **Code sharing:** 70% (iOS + Android)
- **Lines of Code:** ~38,000 (mobile: 26K, backend: 12K)
- **Test Coverage:** 82%
- **Final Cost:** $193,500 (under budget by $1,500)
- **App Store rating:** 4.7 (first 500 ratings)
- **Corporate partners (launch):** 3
- **Corporate partners (Month 6):** 34
