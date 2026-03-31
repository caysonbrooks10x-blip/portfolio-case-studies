# Case Study: Meridian Health — High-Conversion Website Redesign

## Client Overview

**Client:** Meridian Health  
**Industry:** Healthcare / Telehealth Platform  
**Company Size:** 120 employees, Series A ($15M raised)  
**Project Duration:** 12 weeks  
**My Role:** Lead UX/UI Designer  
**Team:** 1 Lead Designer, 1 Copywriter, 2 Developers  

---

## The Challenge

Meridian Health had built a telehealth platform serving 45,000 patients, but their website was hemorrhaging potential patients. A Beautiful Soup analysis and user testing revealed why: the site looked like a 2015 hospital portal, loaded slowly, and made booking an appointment feel like navigating a bureaucratic maze.

**Key Problems:**
- Conversion rate: 2.1% (industry benchmark: 6.5%)
- Bounce rate: 78% (healthcare average: 55%)
- Mobile conversion: 0.8% (desktop was 3.4%)
- Average time on site: 47 seconds
- Appointment booking completion: 12% of visitors who clicked "Book" abandoned the flow

CEO Dr. Priya Sharma: "We're losing patients to competitors with inferior care but better websites. That needs to change yesterday."

---

## Discovery & Research Phase

### Stakeholder Interviews (2 weeks)

Conducted 8 interviews with:
- Executive team (CEO, CMO, CTO)
- Operations (patient coordinator lead)
- Marketing team
- Medical staff representatives

**Key insight:** The site had been built by a dev shop in 2019 and never updated. No one owned the UX.

### User Research

**User Interviews:** 16 interviews with current patients and prospects who had not converted.

**Primary personas identified:**
1. **Time-Pressed Parents** (34%) — Need quick appointments for sick children, value speed above all
2. **Chronic Condition Managers** (28%) — Research-heavy, need trust signals and detailed provider info
3. **First-Time Telehealth Users** (22%) — Anxious about technology, need reassurance and guidance
4. **Corporate Wellness Buyers** (16%) — B2B decision makers evaluating platform capabilities

### Competitive Analysis

Analyzed 12 healthcare and telehealth sites:
- Current leaders: Teladoc, Amwell, One Medical
- Regional competitors: 8 local health systems
- Direct non-healthcare competitors: 2 consumer platforms with healthcare aspirations (Amazon Clinic)

**Key differentiators of high-converting sites:**
- Clear value proposition above the fold
- Social proof at decision points
- Frictionless booking with minimal form fields
- Trust signals (credentials, reviews, security badges)
- Mobile-first design with thumb-friendly targets

### Technical Audit

- PageSpeed score: 34/100 (Poor)
- Mobile usability: Failed (interactions too close together)
- Core Web Vitals: All "Needs Improvement" or "Poor"
- Accessibility: 7 critical issues found

---

## Design Strategy

### Guiding Principles

**1. Friction is the Enemy**  
Every extra field, click, or wait loses patients. We would measure success by reduction in booking abandonment.

**2. Trust is Built in Seconds**  
Healthcare decisions are emotional. We needed to establish credibility immediately and reinforce it at every decision point.

**3. Mobile is Not an Afterthought**  
62% of their traffic was mobile, but it converted at 0.8%. We would design mobile-first and treat desktop as the secondary experience.

**4. Content Serves Conversion**  
Every piece of content had a job: either build trust, answer objections, or move toward booking.

---

## Design Process

### Information Architecture (1 week)

Rebuilt site structure from 23 pages to 12 pages with clearer hierarchy:

**New Architecture:**
- **Home** — Value prop, social proof, quick book
- **Services** — Condition-focused pages (not specialty-focused)
- **Providers** — Trust-building with real doctors
- **How It Works** — Reduce anxiety about telehealth
- **Pricing/Insurance** — Remove financial uncertainty
- **Book** — Frictionless 3-step flow
- **Resources** — Blog, FAQ, patient education

### Copywriting Collaboration

Worked with copywriter to establish:
- Voice: Warm but professional, never clinical
- Reading level: 8th grade (healthcare regulations require accessibility)
- Headline formula: Problem → Agitation → Solution
- CTA language: Action-oriented, benefit-focused

### Wireframing (2 weeks)

Created 45 wireframes across 8 breakpoints. Key innovations:

**Booking Flow Redesign:**
- Step 1: Select reason (3 tap choices max)
- Step 2: Choose provider or "first available"
- Step 3: Confirm with minimal form fields (name, DOB, insurance if applicable)

Previous: 11 form fields, 7 screens. New: 3 fields, 3 screens.

**Provider Cards:**
- Real photo (not stock)
- Name, specialty, rating
- Next available slot
- "Book this provider" CTA

### Visual Design (3 weeks)

**Color System:**
- Primary: #2563EB (trustworthy blue)
- Secondary: #059669 (health green)
- Accent: #F59E0B (attention/warmth)
- Neutrals: #1E293B (text), #F8FAFC (background)
- Error: #DC2626 (accessible red)

**Typography:**
- Headlines: Poppins (friendly, modern)
- Body: Inter (highly readable)
- Scale: 16/18/24/32/48/64px

**Component Highlights:**

*Hero Section:*
- Clear H1 with benefit-driven headline
- Subhead addressing main objection (cost/insurance)
- Primary CTA: "Book in 60 Seconds"
- Secondary CTA: "Check Your Insurance"
- Trust badges: HIPAA, 4.8★ rating, 45K patients

*Social Proof Section:*
- Patient testimonials with photos
- Star ratings from review platforms
- Press mentions
- Provider credentials

### Prototyping & Testing (2 weeks)

Built interactive Figma prototype with:
- All 12 page templates
- Complete booking flow
- Mobile and desktop breakpoints
- Loading and error states

**Usability Testing (3 rounds, 6 participants each):**

Round 1 Issues Found:
- Booking flow too long (fixed: reduced to 3 steps)
- Insurance verification unclear (fixed: added "verify later" option)
- Provider photos looked stock (fixed: required real photos)

Round 2 Issues Found:
- "How it Works" section too text-heavy (fixed: added icons/illustration)
- FAQ accordion confusing (fixed: clearer labels)
- Mobile nav buried book button (fixed: sticky CTA bar)

Round 3: All success criteria met.

---

## Key Design Decisions

### 1. The "Book in 60 Seconds" Hero

Removed the traditional "Learn More" -> "Services" -> "Book" funnel in favor of immediate booking access.

**Elements:**
- Large, prominent "Book Now" button
- Secondary "Check Insurance" for the hesitant
- Trust signals immediately visible
- No scrolling required to see booking option

**Result:** Homepage booking CTA clicks increased 340%.

### 2. Condition-Based Navigation

Instead of organizing by medical specialties (which patients often don't understand), organized by conditions patients would search:

- Cold & Flu
- Mental Health
- Chronic Care
- Women's Health
- Men's Health
- Preventive Care

**Result:** Pages per session increased from 1.2 to 3.8.

### 3. Minimal-Field Booking

Reduced booking form from 11 fields to 3:
1. Why do you need an appointment? (dropdown)
2. When do you want to be seen? (calendar picker)
3. Who should see you? (provider card or "first available")

Insurance and demographics collected post-booking via secure form.

**Result:** Booking abandonment dropped from 67% to 18%.

### 4. Progressive Trust Building

Layered trust signals throughout the journey:

**Awareness:** Homepage → "45,000 patients trust us"  
**Consideration:** Provider pages → Real doctor bios with video  
**Decision:** Booking page → HIPAA badge, secure form, "No surprise bills"  
**Post-Booking:** Confirmation → "Your provider will review your chart"

**Result:** Trust metric (survey: "I feel confident this service will meet my needs") improved from 52% to 84%.

### 5. Mobile-First Everything

Design decisions made for mobile first, then adapted for desktop:

- Tap targets: 48px minimum
- Sticky "Book Now" bar on mobile
- Thumb-zone optimized navigation
- Reduced animations for performance
- Simplified forms (date picker, not manual entry)

**Result:** Mobile conversion improved from 0.8% to 4.2%.

---

## Technical Implementation

### Performance Optimization

Worked with developers on:
- Image optimization (WebP, lazy loading)
- Code splitting
- CDN setup
- Caching strategy
- Critical CSS inlining

**PageSpeed Results:**
- Before: 34 → After: 89
- LCP: 4.2s → 1.8s
- FID: 340ms → 45ms
- CLS: 0.31 → 0.08

### Accessibility

- WCAG 2.1 AA compliance achieved
- Screen reader testing with VoiceOver and JAWS
- Color contrast ratios verified (all text 4.5:1 minimum)
- Focus states visible on all interactive elements
- Form labels properly associated

### A/B Testing Plan

Implemented 4-week A/B test on homepage:
- **Control:** Original design
- **Variant:** New design
- **Result:** +127% conversion (6.8% vs 2.1%)

---

## Results & Impact

### Quantitative Metrics (6 months post-launch)

| Metric | Before | After | Change |
|--------|--------|-------|--------|
| Conversion Rate | 2.1% | 6.8% | +224% |
| Mobile Conversion | 0.8% | 4.2% | +425% |
| Bounce Rate | 78% | 42% | -46% |
| Time on Site | 47 sec | 3.2 min | +308% |
| Booking Abandonment | 67% | 18% | -73% |
| Pages per Session | 1.2 | 3.8 | +217% |
| PageSpeed Score | 34 | 89 | +162% |

### Revenue Impact

| Category | Monthly | Annual |
|----------|---------|--------|
| Additional appointments | +1,240 | +14,880 |
| Revenue per appointment | $125 | — |
| **New annual revenue** | $155,000 | **$1.86M** |
| CAC reduction | -$42 | — |
| **CAC savings (projected)** | — | **$380K** |

**Total annual impact: $2.24M**

---

### Qualitative Feedback

> "The new site doesn't feel like a hospital. It feels like a product I'd actually want to use." — Patient testimonial

> "Our phone lines used to ring constantly with people who couldn't figure out how to book online. Now those calls are consult requests, not tech support." — Patient Coordinator Lead

> "We saw conversion improvements within the first week. The mobile experience alone paid for the redesign in 60 days." — Dr. Priya Sharma, CEO

---

## Lessons Learned

### What Worked

1. **Radical simplification of booking** — Removing fields we thought were necessary (insurance, demographics) and collecting them post-booking dramatically improved completion rates.

2. **Real content over stock everything** — Requiring real provider photos and patient testimonials created authenticity that stock photos can't match.

3. **Mobile-first was the right call** — Optimizing for mobile first forced us to prioritize ruthlessly, which benefited desktop too.

### What I'd Do Differently

1. **More provider involvement earlier** — Some providers were uncomfortable with their photos being so prominent. Involving them in the design process would have reduced friction.

2. **Plan for content migration** — We underestimated the time needed to move 3 years of blog content to the new structure.

3. **Longer A/B test** — 4 weeks was too short for a healthcare decision cycle. Would recommend 8 weeks minimum for future healthcare projects.

---

## Tools & Technologies

**Design:** Figma, Sketch, Adobe Photoshop  
**Prototyping:** Figma, InVision  
**Research:** UserTesting, Hotjar, Google Analytics  
**Copy:** Google Docs, Hemingway App  
**Development:** React, Next.js, Tailwind CSS  
**Testing:** BrowserStack, LambdaTest  
**CMS:** WordPress (headless)  

---

## Project Details

**Timeline:** 12 weeks (Q1 2024)  
**Investment:** $95,000  
**ROI:** 23:1  
**Ongoing:** Retainer for CRO optimization ($4K/month)

---

*CayCay Brooks redesigned the Meridian Health website. For more information about conversion-focused web design, contact cayson@caysonbrooks.com*
