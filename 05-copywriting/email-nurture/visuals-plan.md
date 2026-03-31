# Visuals Plan: Email Nurture + Launch Sequence
## ArcLight Courses — Design & Timing Recommendations

---

## Email Design Philosophy

Email design should serve readability and conversion — not impress with graphics. For B2B professional education, the formula is:

**Clean > Creative**  
**Readable > Impressive**  
**Actionable > Beautiful**

Core principles:
- Mobile-first design (60%+ of opens on mobile)
- Single-column layouts for maximum readability
- Clear hierarchy: headline → subheadline → body → CTA
- Images that reinforce the message (not decorative)
- Minimal design elements that distract from the offer

---

## Template Structure

### Standard Email Layout

```
[HEADER: Logo + Campaign Name]
[PREHEADER: Preview text that extends subject line]
[HERO: Image or color block + headline]
[BODY: 1-2 paragraphs, white space between]
[SOCIAL PROOF: Quote or stat card if applicable]
[CTA: Single, prominent button]
[FOOTER: Unsubscribe, physical address, preferences]
```

### Width
- Desktop: 600-680px max
- Mobile: Full width (fluid)
- Line length: 60-75 characters (for readability)

---

## Typography

### Font Stack
- **Primary:** Inter, -apple-system, BlinkMacSystemFont, sans-serif
- **System fallback:** Arial, Helvetica, sans-serif
- **Body:** 16-18px (larger than typical for readability)
- **Headlines:** 24-32px, bold
- **CTA:** 16-18px, bold, uppercase optional

### Color Palette (Email Safe)

| Element | Color | Hex |
|---------|-------|-----|
| Background | White | #ffffff |
| Body text | Charcoal | #2d3748 |
| Headlines | Navy | #1a2744 |
| Links | Blue | #2563eb |
| CTA button | Gold #c9a227 or Green #22c55e | — |
| Footer text | Gray | #64748b |

---

## Image Guidelines

### Hero Images
- Width: 600px (display), responsive to mobile
- Height: 200-300px (keep file size low)
- Format: PNG or JPG, compressed
- File size: < 100KB per image

### Instructor Photos
- Circular crop: 120×120px
- Professional but approachable
- Consistent lighting and style across all emails

### Product/Course Screenshots
- Show actual course UI
- Add subtle shadow or border for definition
- Alt text required for accessibility

### Social Proof Cards
- Quote in larger font (18-20px)
- Attribution: Name, Title, Company
- Optional: Small photo (80×80px)
- Subtle background color to differentiate

---

## Button Design

### Primary CTA Button
- Background: Gold (#c9a227)
- Text: Navy (#1a2744), 16px, bold
- Border radius: 6px
- Padding: 16px 32px
- Width: Auto (or 100% on mobile)
- Minimum touch target: 44px height

### Secondary CTA (Text Link)
- Text color: Blue (#2563eb)
- Underline on hover
- Not competing with primary CTA

### Button Placement
- After first paragraph (above the fold on mobile)
- After body content (reinforcement)
- Never below the footer

---

## Send Time Recommendations

### Launch Sequence (Day-Specific)

| Email | Day | Send Time (EST) | Rationale |
|-------|-----|-----------------|-----------|
| All launch emails | — | 9:00 AM EST | Consistent cadence, best overall open rate |

### Behavioral Triggers

| Trigger | Send Time | Rationale |
|---------|-----------|-----------|
| Browse abandonment | 2 hours after trigger | Capture same-day intent |
| Cart abandonment | 24 hours after trigger | Let them sleep on decision |
| Re-engagement | 10:00 AM (their local time) | Klaviyo time zone automation |

### Segmentation
- **Morning people:** 7-9 AM local
- **Afternoon people:** 12-2 PM local
- **Evening people:** 6-8 PM local

Use Klaviyo's predicted gender/age for send time optimization.

---

## Subject Line Guidelines

### Length
- Desktop preview: 40-50 characters
- Mobile preview: 25-35 characters
- Subject + preview text together tell the full story

### Patterns That Work (For EdTech)

| Type | Example | Performance |
|------|---------|-------------|
| Curiosity | "The cloud job market just shifted" | +18% open vs. control |
| Specificity | "What $31K in salary increase looks like" | +22% open vs. control |
| Personal | "Your waitlist spot is waiting" | +15% open vs. control |
| Urgency | "48 hours left: Enrollment closes" | +31% open vs. control |
| Question | "Are you leaving money on the table?" | +12% open vs. control |

### A/B Testing Plan (Launch Sequence)
- Test 1: Curiosity vs. Specificity (Email 1-3)
- Test 2: Question vs. Statement (Email 4-6)
- Test 3: Urgency vs. Value (Email 15+)
- Minimum sample: 1,000 per variant before declaring winner

---

## Mobile Optimization Checklist

- [ ] Single column layout (no tables)
- [ ] Font size ≥ 16px for body
- [ ] CTA button ≥ 44px height
- [ ] Images with width="100%" for responsiveness
- [ ] Padding: 16px minimum on mobile
- [ ] No side-by-side layouts
- [ ] Preheader text visible on mobile
- [ ] Touch-friendly links (no <3px spacing)

---

## Image-to-Text Ratio

- **Google:** 60% text minimum (to avoid spam folder)
- **Outlook:** Images may be blocked by default
- **Recommendation:** Text-dominant emails (80%+ text)

Rule: Every image should have a purpose. If you can't explain why an image is there, remove it.

---

## Template Versions by Segment

### Buyers (High-Trust, Purchase History)
- More visuals (instructor, campus, community)
- Softer CTAs (refer a friend, leave a review)
- Referral incentives

### Non-Buyers (High-Engagement, No Purchase)
- Outcome-focused copy
- Social proof emphasis
- Risk reversal (guarantee)
- Testimonial-heavy

### Cold (Low/No Engagement)
- Re-engagement framing ("We miss you")
- New content ("Here's what's new")
- Stronger urgency ("Last chance")
- Clean, minimal design

---

## Testing Protocol

### Pre-Launch
- [ ] All emails rendered in 20+ clients (Litmus or Email on Acid)
- [ ] All links tested and functional
- [ ] UTM parameters verified
- [ ] Personalization tokens verified
- [ ] Unsubscribe link functional
- [ ] Physical address in footer (CAN-SPAM)

### Post-Launch
- [ ] Open rate tracked by ESP
- [ ] CTR tracked by ESP
- [ ] Revenue tracked by UTM
- [ ] Issues logged and addressed within 24 hours

---

## Tools for Email Design

- **Klaviyo** — Email builder (drag-and-drop)
- **Figma** — Hero image and graphic design
- **Litmus** or **Email on Acid** — Client testing
- **Canva** — Social and banner graphics
- ** Hemingway App** — Copy clarity

---

## Common Mistakes to Avoid

1. **Too many images** — Causes spam flags, slow load on mobile
2. **Tiny CTAs** — If I can't tap it easily, I won't
3. **Dark mode issues** — Test in both light and dark
4. **Link stacking** — Multiple CTAs close together create confusion
5. **Inconsistent send times** — Train your audience when to expect you

---

*Prepared by Cayson Brooks. For ArcLight Courses design and email team alignment.*
