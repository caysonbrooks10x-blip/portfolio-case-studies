# Visuals Plan: Landing Page Rewrite
## Meridian Consulting — UX/Copy Alignment

---

## Design Principles

The visual design must serve the copy, not compete with it. Every design decision should support one goal: getting the visitor to read the next sentence and ultimately click the CTA.

---

## Page Architecture

### Desktop Layout (Recommended)

```
[NAV - Minimal, Logo + Phone Number Only]
[HERO - Full Width, Headline Left, Image Right]
[TRUST BAR - Logos of featured publications]
[PROBLEM - Centered, 2-column text]
[SOLUTION - Card layout, 3 features]
[OUTCOMES - Stats grid with large numbers]
[PROCESS - 3-step horizontal flow]
[SOCIAL PROOF - Quote cards with photos]
[PRICING - Centered with value summary]
[CTA - Full width, contrasting background]
[FOOTER - Minimal, trust elements]
```

### Mobile Layout (Priority)

```
[FIXED CTA BAR - Bottom of screen]
[HERO - Stacked, headline above image]
[TRUST BAR - Horizontal scroll logos]
[PROBLEM - Single column, large type]
[SOLUTION - Accordion or stacked cards]
[OUTCOMES - Vertical stats list]
[PROCESS - Stacked numbered steps]
[SOCIAL PROOF - Swipeable carousel]
[PRICING - Full width card]
[FINAL CTA - Above footer]
```

---

## Typography Recommendations

### Font Pairing

**Primary (Headlines):** Inter or SF Pro Display (700 weight)
- Clean, professional, high readability
- Numbers look authoritative in this font

**Secondary (Body):** Inter or SF Pro Text (400/500 weight)
- Consistent family maintains visual cohesion
- Excellent readability at small sizes

**Accent (CTAs, Stats):** Same family, higher weight
- Maintains hierarchy without mixed-font chaos

### Size Hierarchy

| Element | Desktop | Mobile |
|---------|---------|--------|
| H1 (Hero) | 56px | 36px |
| H2 (Section) | 40px | 28px |
| H3 (Subsection) | 28px | 22px |
| Body | 18px | 16px |
| CTA Button | 18px | 16px (min) |

### Line Height
- Headlines: 1.1 (tight)
- Body: 1.6 (comfortable reading)
- Stats: 1.0 (tight for impact)

---

## Color Palette

### Primary Palette

| Color | Hex | Usage |
|-------|-----|-------|
| Navy | #1a2744 | Primary backgrounds, H1 |
| White | #ffffff | Text on dark, backgrounds |
| Charcoal | #2d3748 | Body text |
| Slate | #64748b | Secondary text, captions |

### Accent Colors

| Color | Hex | Usage |
|-------|-----|-------|
| Gold | #c9a227 | CTAs, highlights, trust elements |
| Green (success) | #22c55e | Stats, checkmarks |
| Red (urgency) | #dc2626 | Only if testing urgency variants |

### CTA Button Styling

- Background: Gold (#c9a227)
- Text: Navy (#1a2744)
- Border radius: 8px
- Padding: 16px 32px
- Hover: Darken 10%, subtle shadow

---

## Imagery Guidelines

### Hero Image
- **Recommended:** Professional headshot of CEO or actual coaching session
- **Avoid:** Stock photos of handshakes, lightbulbs, or abstract concepts
- **Style:** Warm, human, authentic — not corporate sterile
- **Placement:** Right side (desktop), below headline (mobile)

### Section Backgrounds
- Problem section: Light gray (#f7fafc)
- Outcomes section: Navy (#1a2744) with white text
- Social proof: White with subtle shadow cards
- Pricing: Light warm (#fefdfb)

### Client Photos (Testimonials)
- Real photos required — no illustrations
- Professional but approachable
- Consistent sizing across all testimonial cards
- Consider adding company logo + title below photo

---

## Spacing & Layout

### Section Padding

| Section | Desktop (top/bottom) | Mobile (top/bottom) |
|---------|---------------------|---------------------|
| Hero | 120px / 80px | 60px / 40px |
| Problem | 100px / 100px | 60px / 60px |
| Solution | 80px / 80px | 50px / 50px |
| Outcomes | 100px / 100px | 60px / 60px |
| Process | 80px / 80px | 50px / 50px |
| Social Proof | 100px / 100px | 60px / 60px |
| Pricing | 100px / 100px | 60px / 60px |
| Final CTA | 80px / 80px | 50px / 50px |

### Max Content Width
- Desktop: 1200px centered
- Text blocks: 720px max (for readability)
- Stats grid: Flexible, 3-4 columns

---

## Mobile-Specific Considerations

### Fixed Bottom CTA Bar
- Sticky bar on mobile with primary CTA
- Only appears after scrolling past hero
- High contrast: Gold on Navy
- "Book Your Strategy Session →"

### Thumb Zone Optimization
- Primary CTAs in bottom 1/3 of viewport
- Phone number in header (tap-to-call)
- Form fields large enough for fat fingers (min 44px height)

### Load Speed
- Hero image: WebP format, max 200KB
- Avoid heavy parallax effects
- Lazy load below-fold images
- Target: < 3 second load on 4G

---

## A/B Test Visual Variants

### Headline Test (Currently Running)
- Control: White text on Navy background
- Variant B: Navy text on white background with gold underline

### CTA Button Test (Planned)
- Control: Gold background, Navy text
- Variant: White background, gold border, Navy text

---

## Implementation Checklist

- [ ] Hero image optimized (WebP, <200KB)
- [ ] All fonts self-hosted or Google Fonts CDN
- [ ] Mobile CTA bar implemented
- [ ] Stats section renders correctly on all sizes
- [ ] Testimonial cards have consistent height
- [ ] Form fields are 44px+ height on mobile
- [ ] Page load < 3s on mobile (PageSpeed Insights)
- [ ] All images have alt tags
- [ ] Color contrast meets WCAG AA standards
- [ ] Hotjar tracking code installed

---

## Recommended Tools

- **Figma** or **Sketch** — Design files
- **Webflow** or **WordPress** — Implementation
- **Hotjar** — Heatmaps and scroll analysis
- **Google PageSpeed Insights** — Load speed testing
- **Cloudflare** or **imgix** — Image optimization CDN

---

*Prepared by Cayson Brooks. For client use and implementation guidance.*
