# Nordic Table — Deliverables

## Core Deliverables (Committed in Contract)

### 1. Discovery & Strategy
- Google Analytics analysis (2 years)
- 16 customer interviews
- 340 abandoned cart surveys
- Competitor feature audit
- Product Discovery Enhancement Strategy document

### 2. Room-by-Room Galleries
- 24 curated room collections
- "Shop This Room" aggregation
- "Complete the Look" suggestions
- Lazy-loaded images with blur placeholders
- Mobile-responsive design
- Integration with Shopify product data

### 3. Visual Search
- Image upload interface
- Camera capture option
- TensorFlow.js embedding pipeline
- Visual similarity matching
- Top 12 similar products display
- Refinement filters (category, price, color)
- Analytics event tracking

### 4. WebAR Product Viewer
- USDZ/GLTF model generation pipeline
- @google/model-viewer integration
- "Place in Room" one-tap AR activation
- AR screenshot capture and sharing
- Multiple product comparison in AR
- iOS Safari + Android Chrome support

### 5. Backend Services
- Shopify Storefront API integration
- Product embedding service (TensorFlow.js)
- Image processing pipeline (Sharp)
- AR model processing pipeline
- A/B testing framework (Optimizely)
- Analytics event tracking (Segment + Amplitude)

### 6. Performance Optimization
- Cloudflare image resizing
- Lazy loading implementation
- Critical CSS inlining
- Preconnect to critical origins
- Service worker for repeat visits
- 3G performance testing

### 7. A/B Testing Framework
- Optimizely integration
- Room gallery variations (4 tested)
- Visual search placement tests
- AR button design tests
- Statistical significance validation
- Conversion tracking dashboards

### 8. Documentation
- Technical architecture document
- API documentation
- Content management guide
- Analytics dashboard guide
- Performance monitoring guide

### 9. QA & Testing
- Cross-browser testing (Chrome, Safari, Firefox, Edge)
- Mobile device testing (32 devices)
- Performance testing (3G throttling)
- Shopify checkout integration testing
- A/B test validation

---

## Bonus Deliverables (Value-Added)

### 1. Smart Recommendations
Not originally scoped. Built as part of visual search — "Customers who viewed this also viewed" section added to product pages.

### 2. Style Quiz
Interactive quiz to help customers discover their style. Added after customer interviews revealed indecision was a barrier.

### 3. Wishlist with Room Matching
Customers can save products to wishlists and see which saved items complete their room galleries.

---

## What Was NOT Delivered (Scope Cuts)

| Feature | Reason Cut | Phase 2 Plan |
|---------|------------|--------------|
| Native iOS/Android app | Not requested | Phase 2 |
| 3D room planning tool | Too complex for MVP | Phase 2 |
| AR for all 400+ SKUs | Phased rollout | Ongoing |
| Social shopping (share rooms) | Not critical for MVP | Phase 2 |
| Inventory-based room suggestions | Requires inventory sync | Phase 2 |

---

## Acceptance Criteria

All deliverables met the following criteria:

- [ ] Room galleries: 24 collections live
- [ ] Visual search: < 3s image-to-results
- [ ] AR viewer: Works in iOS Safari + Android Chrome
- [ ] Performance: 1.8s load on 3G (Lighthouse: 90+)
- [ ] A/B test: Statistical significance reached
- [ ] Shopify checkout: Zero disruption
- [ ] Analytics: All events tracked correctly

---

## Timeline Adherence

| Phase | Planned | Actual | Variance |
|-------|---------|--------|----------|
| Discovery | Week 1-2 | Week 1-2 | On time |
| Design | Week 2-4 | Week 2-4 | On time |
| Room Galleries | Week 4-7 | Week 4-7 | On time |
| Visual Search | Week 5-8 | Week 5-8 | On time |
| AR Viewer | Week 7-9 | Week 7-9 | On time |
| QA + Launch | Week 9-10 | Week 9-10 | On time |
| **Total** | **10 weeks** | **10 weeks** | **On budget** |

Final cost: $143,500 (under $145K by $1,500)
