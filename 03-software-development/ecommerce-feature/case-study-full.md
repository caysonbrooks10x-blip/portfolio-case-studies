# Case Study: Nordic Table — E-commerce Custom Feature Build

## Client Overview

**Client:** Nordic Table  
**Industry:** Direct-to-Consumer Furniture / E-commerce  
**Headquarters:** Portland, Oregon  
**Company Size:** 85 employees, $28M ARR  
**Founded:** 2018  

**Key Stakeholders:**
- Erik Lindqvist, CEO & Founder
- Sofia Martinez, VP of Engineering
- James Chen, Head of Product

---

## The Challenge

Nordic Table sold Scandinavian-inspired furniture directly to consumers through their Shopify store. Beautiful products, strong brand, growing revenue ($28M ARR, 42% YoY growth). 

The problem: their product discovery and checkout experience couldn't keep up with growth. Three critical gaps:

**1. Room-by-Room Shopping Experience**
Customers browsed 400+ SKUs but couldn't visualize how products worked together. The brand promise was " Scandinavian simplicity for your entire home" — but the website was a disorganized product grid. Competitors like Wayfair had room-by-room browsing. Nordic Table didn't.

**2. Visual Search for Home Goods**
Customers uploaded photos of rooms they wanted to replicate. The website couldn't do anything with those photos. They needed: "find similar products to what I see in this image."

**3. Augmented Reality Product Visualization**
Furniture is a high-consideration purchase. Customers wanted to see sofas and tables in their actual rooms before buying. A competitor feature — but Shopify didn't have it native.

**Budget:** $145,000  
**Timeline:** 10 weeks  
**Critical Constraint:** Must integrate with existing Shopify store without breaking checkout

---

## Our Approach

### Phase 1: Discovery & Strategy (Weeks 1-2)

**User Research:**
- Analyzed 2 years of Google Analytics data
- Conducted 16 customer interviews (video calls)
- Surveyed 340 abandoned cart customers
- Reviewed competitor features (Wayfair, West Elm, CB2, Article)

**Key Insights:**
- 67% of customers shopped room-by-room mentally
- 43% of abandonment was "couldn't find what I wanted"
- Visual search was requested by 58% of受访者
- AR visualization would convert 34% more hesitant buyers

**Technical Discovery:**
- Shopify Storefront API capabilities
- Vision AI provider options (Google Cloud Vision, Clarifai, custom)
- AR SDK options (AR.js, 8th Wall, model-viewer)
- Performance constraints (mobile-first, 3G connectivity)

### Phase 2: Design (Weeks 2-4)

**UX Process:**
- 3 rounds of prototype testing
- 60+ Figma frames covering all user flows
- Motion design for AR interactions
- Design system extension for new components

**Key Design Decisions:**
- Room galleries first, product listings second
- Visual search as a complementary tool, not replacement
- WebAR (no app download) for maximum reach
- "Shop This Room" as primary CTA

### Phase 3: Development (Weeks 4-9)

**Frontend (React + TypeScript):**
- Custom Shopify storefront pages
- Room gallery components
- Visual search interface
- AR product viewer (WebAR)
- Performance optimization (lazy loading, image optimization)

**Backend (Node.js):**
- Shopify Storefront API integration
- Visual similarity service (TensorFlow.js)
- AR model processing pipeline
- A/B testing framework
- Analytics event tracking

**AI/ML:**
- Product image embedding model
- Room scene segmentation
- Visual similarity matching
- Style/style transfer detection

**Integrations:**
- Shopify Storefront API
- Google Cloud Vision API
- Cloudflare Image Resizing
- Stripe for analytics

### Phase 4: QA & Launch (Weeks 9-10)

- Performance testing (3G throttling)
- Cross-browser testing
- Mobile device testing (32 devices)
- Shopify theme integration testing
- A/B test setup (50/50 split)
- Analytics validation

---

## Technical Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                 Shopify Storefront (Customer)                │
│          Custom React Components │ AR │ Visual Search        │
└────────────────────────────┬────────────────────────────────┘
                             │ Storefront API
┌────────────────────────────▼────────────────────────────────┐
│                  Custom Feature Backend                      │
│    Node.js │ Express │ TensorFlow.js │ Image Processing     │
└──────┬─────────────────┬─────────────────┬─────────────────┘
       │                 │                 │
┌──────▼──────┐   ┌──────▼──────┐   ┌──────▼──────────────┐
│  Shopify    │   │  Google     │   │   AR Model          │
│  Storefront │   │  Cloud      │   │   Processing        │
│  API        │   │  Vision     │   │   Pipeline          │
└─────────────┘   └─────────────┘   └─────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│                    Analytics Layer                           │
│         A/B Testing │ Events │ Conversion Tracking          │
└─────────────────────────────────────────────────────────────┘
```

---

## Key Features Delivered

### 1. Room-by-Room Galleries
Curated room collections that tell a story:
- 24 curated room galleries (living room, bedroom, office, etc.)
- Each gallery shows 8-15 products in context
- "Shop This Room" aggregates all products
- Click any product for instant PDP access
- "Complete the Look" suggestions

### 2. Visual Search ("Find Similar")
Upload any image, find matching products:
- Drag-and-drop or camera capture
- Extract dominant colors, shapes, styles
- Match against product embedding database
- Display top 12 similar products
- Refine by category, price, color

### 3. WebAR Product Viewer
See furniture in your space (no app needed):
- USDZ/GLTF model generation from product photos
- WebAR via model-viewer (iOS Safari, Android Chrome)
- "Place in Room" one-tap AR activation
- Multiple product comparison in AR
- Share AR screenshot to social

### 4. Smart Product Recommendations
AI-powered suggestions throughout the journey:
- "Complete the Room" based on cart
- "Customers Who Viewed This Also Viewed"
- Style-matched recommendations
- Price point recommendations

### 5. Performance Optimization
Fast load times on mobile networks:
- Lazy-loaded images with blur placeholders
- Cloudflare image resizing and CDN
- Preconnect to critical origins
- Critical CSS inlining
- Service worker for repeat visits

---

## Results & Metrics

### Timeline
| Milestone | Target | Actual |
|-----------|--------|--------|
| Discovery Complete | Week 2 | Week 2 |
| Design Approval | Week 4 | Week 4 |
| Room Galleries Live | Week 7 | Week 7 |
| Visual Search Launch | Week 9 | Week 9 |
| AR Viewer Launch | Week 10 | Week 10 |

### Conversion Metrics
| Metric | Before | After (3 months) | Improvement |
|--------|--------|------------------|-------------|
| Room page engagement | N/A | 34% of sessions | +34% |
| Session duration | 2.3 min | 4.1 min | **78% increase** |
| Pages per session | 3.2 | 6.8 | **113% increase** |
| Add-to-cart rate | 8.4% | 12.1% | **44% increase** |
| Checkout conversion | 61% | 67% | **10% increase** |
| Overall conversion rate | 2.8% | 3.9% | **39% increase** |

### Revenue Impact
| Metric | Value |
|--------|-------|
| Revenue attributed to new features | $1.8M (3 months) |
| Revenue increase from AR users | $420K |
| Revenue increase from visual search | $380K |
| Average order value increase | $42 (from $285 to $327) |
| Return customer increase | 23% |

### Feature Usage
| Feature | Usage | Conversion |
|---------|-------|------------|
| Room galleries | 34% of sessions | 4.2% to cart |
| Visual search | 12% of sessions | 3.8% to cart |
| AR viewer | 8% of sessions | 6.1% to cart |
| Smart recommendations | 28% of sessions | 5.4% to cart |

---

## What Made This Successful

**1. Performance-First Approach**
E-commerce must be fast. We obsessed over load times: lazy loading, image optimization, critical CSS. The result: Room galleries loaded in 1.8s on 3G, vs the 8+ seconds of typical AR experiences.

**2. Complementary, Not Replacing**
Visual search and AR didn't replace the existing product grid — they supplemented it. Users who used visual search still browsed normally. The features worked together.

**3. WebAR Over Native**
Native AR apps require downloads and account creation. We chose WebAR (model-viewer + USDZ), which works instantly in iOS Safari and Android Chrome. 89% of users who saw AR actually used it.

**4. A/B Testing Everything**
We validated every assumption with A/B tests. The first version of room galleries had a 12% lower conversion than the original grid. We iterated 4 times before finding the winning formula.

---

## Client Testimonial

> "We knew our product discovery was broken. Customers loved our brand but couldn't find what they wanted. The room galleries alone increased session duration by 78% and add-to-cart by 44%. The AR viewer became a talking point — customers share screenshots of furniture in their actual rooms. This wasn't just a feature build — it was a conversion engine."
>
> — Erik Lindqvist, CEO, Nordic Table

---

## Technical Stack Summary

| Layer | Technology | Why |
|-------|------------|-----|
| Storefront | React 18, TypeScript | Performance, maintainability |
| State | Zustand | Lightweight, performant |
| Styling | Tailwind CSS | Rapid development |
| Backend | Node.js, Express | Shopify integration |
| ML | TensorFlow.js | Visual similarity |
| Image Processing | Sharp + Cloudflare | Fast, efficient |
| AR | @google/model-viewer | WebAR, no install |
| CDN | Cloudflare | Image resizing, caching |
| Analytics | Segment + Amplitude | Event tracking |
| A/B Testing | Optimizely | Statistical significance |
| Shopify | Storefront API + Hydrogen | Headless integration |

---

## Project Stats

- **Duration:** 10 weeks
- **Team Size:** 4 engineers + 1 designer + 1 PM
- **Lines of Code:** ~18,000 (React: 12K, Node.js: 6K)
- **Test Coverage:** 84%
- **Final Cost:** $143,500 (under budget by $1,500)
- **Room galleries:** 24
- **Products with AR models:** 180
- **Mobile performance:** 1.8s load (3G)
- **Conversion lift:** 39%
