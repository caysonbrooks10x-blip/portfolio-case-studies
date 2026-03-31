# Nordic Table — Objections & Responses

## Sales Objections

### "Shopify already has apps for room galleries and AR. Why custom build?"

**Response:**
"Three reasons we custom-built:

1. **Performance:** Shopify apps add 4-8 seconds of load time. We delivered 1.8s. That's the difference between 89% AR usage and 12%.
2. **Brand fit:** Generic apps don't match Nordic Table's aesthetic. Custom-built matches exactly.
3. **Integration depth:** Apps work around Shopify. We built on the Storefront API — native integration, zero checkout risk.

The $145K investment beat the ROI of any Shopify app by 10x."

---

### "Our customers aren't technical. They won't use AR."

**Response:**
"We thought the same thing. The data says otherwise:

- 89% of users who saw the AR button actually used it
- Average AR session: 2.4 minutes
- 23% of AR users shared screenshots to social
- AR users had 34% higher conversion rate

The barrier to AR has collapsed. iOS Safari and Android Chrome support WebAR natively. No app download, no account. It just works."

---

### "Can this scale to our full catalog? We have 400+ SKUs."

**Yes — we built the pipeline for scale:**

- **Image upload:** 5 minutes per product (photos + metadata)
- **AR model generation:** Automated from product photos
- **Embedding updates:** Nightly batch job
- **New room galleries:** 2 days to create

We onboarded 180 products in 3 weeks. The remaining 220 can be added in 4 weeks."

---

### "We're worried about Shopify checkout breaking."

**Response:**
"We tested extensively. Here's our approach:

1. **Storefront API only:** We read products, never touch checkout
2. **Theme extension:** New components added without modifying core theme
3. **Custom checkout:** None — all standard Shopify checkout
4. **Rollback:** If anything breaks, disable the app with one click

Zero checkout disruption. Verified on launch."

---

## Technical Objections

### "How does visual search work? Is it accurate?"

**Response:**
"TensorFlow.js with product embeddings:

1. **Training:** We embed all product images into a vector space using ResNet50
2. **Query:** User uploads an image (room photo, Pinterest, etc.)
3. **Matching:** Extract embedding, find nearest neighbors in product space
4. **Ranking:** Combine similarity score with popularity, recency

Accuracy: 78% of visual search users click a result. That's higher than text search."

---

### "AR models are expensive to create. How do you handle 400+ products?"

**Response:**
"Two approaches depending on product type:

**Furniture (sofas, tables, chairs):**
- We generate 3D models from product photos using photogrammetry
- Cost: $0 (automated)
- Time: 5 minutes per product

**Complex products (beds with intricate headboards):**
- Manual 3D modeling required
- Cost: $50-150 per model
- We did 180 products in 3 weeks

For the remaining 220 SKUs, we can phase: high-margin products first, catalog over 8 weeks."

---

### "3G performance is critical for our mobile customers. How do you ensure speed?"

**Response:**
"We obsessed over performance. Here's the stack:

- **Cloudflare image resizing:** Serve optimized images per device
- **Lazy loading:** Images load as user scrolls
- **Blur placeholders:** Perceived load time < 0.5s
- **Critical CSS:** Inline above-fold styles
- **Preconnect:** Establish connections early
- **Service worker:** Cache repeat visits

Results: 1.8s on 3G throttling (Lighthouse: 92). Tested on actual 3G in Portland, Seattle, and Denver."

---

### "We want A/B testing to validate these features. Is that built in?"

**Response:**
"Yes — we implemented a full A/B testing framework:

- **Room galleries vs. grid:** Tested 4 variations before finding winner
- **Visual search placement:** Hero vs. search page vs. product page
- **AR button style:** Tested 3 designs

We used Optimizely for statistical significance. All tests reached 95% confidence before decisions."

---

## Timeline Objections

### "We need this for Q4 holiday season. Can you compress to 8 weeks?"

**Response:**
"Options for compression:

**Option A (8 weeks):**
- 12 room galleries (not 24)
- Visual search only on mobile (not desktop)
- AR on top 50 products (not 180)
- Basic A/B testing (manual)

**Option B (10 weeks, full):**
- Everything in scope
- Full A/B framework
- All 180 AR products

For holiday season, I'd recommend 10 weeks with phased launch: room galleries at Week 8, visual search + AR at Week 10."

---

### "Can we launch room galleries first, then visual search and AR later?"

**Response:**
"Yes — this is actually our recommendation.

**Week 8:** Room galleries live (biggest conversion driver)
**Week 10:** Visual search launch
**Week 12:** AR viewer launch

This lets you validate each feature and iterate based on data. We can phase the contract accordingly."
