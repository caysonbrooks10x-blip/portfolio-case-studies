# MealMoxie — Objections & Responses

## Sales Objections

### "React Native isn't as performant as native apps."

**Response:**
"For 95% of use cases, React Native is indistinguishable from native. Here's our track record:

- 60fps animations on all transitions
- 2.4s app launch time (native average: 2s)
- Google Maps integration via native components
- Stripe SDK via native bridge

The only place native wins is highly custom graphics (gaming, AR). Ordering food? React Native is the right choice. The code sharing alone saves $80K+."

---

### "We need to be in the App Store in 8 weeks."

**Response:**
"Here's what we can do in 8 weeks:

**Option A (8-week scope):**
- iOS app only
- No corporate dashboard
- Basic ordering (no split orders, no dietary filters)
- SSO in Phase 2

**Option B (10-week scope):**
- iOS + Android
- Basic ordering
- Dashboard in Phase 2

**Option C (12-week scope, full):**
- Both platforms
- Full feature set
- Corporate dashboard
- Beta with 3 partners

What matters more: speed to market, or feature completeness?"

---

### "How do you handle offline ordering?"

**Response:**
"Our architecture is offline-first:

1. **Order queue:** When connectivity drops, orders save to local storage with a pending status
2. **Smart sync:** When connectivity returns, orders sync automatically with conflict resolution
3. **User feedback:** Clear visual indicator shows order status — 'Order placed' vs 'Waiting for connection'
4. **Retry logic:** Failed orders retry 3x with exponential backoff

We tested this in 3 corporate offices with known WiFi issues. Zero lost orders."

---

### "We need SSO with Okta and Azure AD."

**Response:**
"We have Okta and Azure AD experience. Here's the implementation:

- **Okta:** SAML 2.0 SSO integration (tested with 2 enterprise clients)
- **Azure AD:** OAuth 2.0 + SAML 2.0 support
- **Timeline impact:** Adds 1 week to development
- **Testing:** We test in your Okta/Azure AD sandbox before launch

SSO is table-stakes for enterprise. We build it correctly from Day 1."

---

### "What if the restaurant doesn't have delivery?"

**Response:**
"Phase 1 scope: delivery-only restaurants. We filter by delivery capability via Google Places API.

Phase 2 (Months 4-6): Add pickup ordering. This is a different UX flow and POS integration.

Don't build pickup in Phase 1. It adds 3 weeks and splits your testing focus."

---

## Technical Objections

### "How do you handle real-time order tracking?"

**Response:**
"Three components:

1. **Driver location:** Google Places SDK for ETA calculations
2. **Order status push:** Firebase Cloud Messaging for real-time updates
3. **WebSocket fallback:** If push fails, polling every 30 seconds

The tracking experience: employee sees map with driver location, estimated arrival, and order status. Updates push in real-time."

---

### "Stripe Connect is complex for corporate billing. Walk us through it."

**Response:**
"For MealMoxie, we implemented a platform model:

1. **Corporate sets up Stripe:** They onboard as a platform customer
2. **Employees get virtual cards:** Each employee gets a virtual MealMoxie card
3. **Transactions split:** Restaurant gets 88%, MealMoxie gets 12%
4. **Monthly invoicing:** Corporations get a monthly invoice for all spending

This is standard for corporate meal platforms. We've done it before."

---

### "App Store review can take 4-6 weeks. How do you account for this?"

**Response:**
"We account for it in the timeline:

- Week 1-10: Development
- Week 11: TestFlight + Google Play Beta submissions
- Week 12: Bug fixes based on beta feedback
- Week 13-14: App Store review (parallel to corporate pilots)

The app is 'launched' at Week 12 — 3 corporate partners using it. Public App Store availability comes 2-3 weeks later.

This is how mobile launches work. You don't want to go public without beta feedback anyway."

---

### "How do you handle dietary restrictions and allergies?"

**Response:**
"We built a dietary preference system:

- **Employee sets preferences:** Vegan, vegetarian, halal, kosher, gluten-free, allergies
- **Restaurant filtering:** Google Places data + manual tagging
- **Menu item flags:** Restaurants flag items by dietary category
- **Warning system:** If an order contains an allergen, we warn before checkout

This isn't medical-grade — it's user-reported. We made that clear in the terms."

---

## Timeline Objections

### "Our Series A closes in 10 weeks. We need to demo before then."

**Response:**
"We can deliver a demo-able prototype at Week 6:

- Working login flow
- Restaurant browsing and search
- Basic ordering (no payment)
- Mock checkout

This is enough for a pitch meeting. Full payment integration ships at Week 12. We can fast-track this if your Series A depends on it."

---

### "We want to launch to our entire company on Week 12. Is that possible?"

**Response:**
"We strongly recommend against this. Here's why:

**Risk:** If there are issues, you get negative reviews that kill early momentum.

**Recommendation:**
- Week 12: Launch to 3 corporate partners (150 employees)
- Week 14: Public App Store
- Week 16: Open to any company

This is how Slack, Uber, and DoorDash launched. Internal beta first. Public launch second."

---

### "Can we add a feature mid-project?"

**Response:**
"Mid-project scope changes have three outcomes:

1. **Free (if we over-scoped):** We have buffer in the 12-week timeline
2. **Defer to Phase 2:** If it's not critical path, we document and build in Month 4
3. **Change order:** If it's a significant addition, we provide a separate quote

We track scope changes formally. You always know the impact on timeline and budget."
