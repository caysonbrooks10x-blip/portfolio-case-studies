# Case Study: Verve — Mobile App UI System

## Client Overview

**Client:** Verve  
**Industry:** Fintech / Personal Finance  
**Company Size:** 45 employees, Seed stage ($8M raised)  
**Project Duration:** 16 weeks  
**My Role:** Lead Product Designer  
**Team:** 1 Lead Designer, 1 UX Writer, 2 iOS Engineers, 2 Android Engineers  

---

## The Challenge

Verve had built a compelling personal finance app that helped Gen Z users manage spending, save automatically, and build credit—but their user interface looked like a first-year design student's project. The app had strong core functionality with a 4.2★ rating, but retention was suffering due to confusing navigation and an aesthetic that users described as "aggressively boring."

Co-founder and CEO Aaliyah Thompson: "We know the product works. Users who stick around love it. But we lose 68% of new users before they complete onboarding. The app's face isn't matching its potential."

**Key Problems:**
- Day 1 retention: 41% (industry benchmark: 65%)
- Day 7 retention: 18% (industry benchmark: 40%)
- Onboarding completion: 32% (target: 70%)
- App Store rating: 4.2★ with 340 reviews
- Users describing app as "confusing": 47%
- Core task (save money) discovery: 12%

---

## Discovery & Research Phase

### Competitive Analysis (2 weeks)

Analyzed 18 personal finance apps across tiers:

**Premium tier:** Robinhood, Cash App, Venmo  
**Mid-tier:** Mint, YNAB, Personal Capital  
**Emerging Gen Z-focused:** Chipper, Cinco, Step

**Key findings:**
- Top apps use bold color, clear hierarchy, and celebration of progress
- Gen Z apps favor dark mode, rounded corners, playful illustration
- Successful onboarding takes 60-90 seconds max
- Progressive disclosure is critical—show features as users earn them

### User Research

**User Interviews:** 20 interviews with:
- Current Verve users (8) — understanding why they stayed
- Churned users (6) — understanding why they left
- Potential users (6) — understanding expectations

**Key insight:** Users didn't leave because the app was bad—they left because it felt like homework. Finance apps that succeeded made money management feel like a game, not a chore.

### Usability Testing (1 week)

Tested current app with 12 participants:
- Task: Complete onboarding, make first save, set a budget
- Found: 14 critical usability issues
- Biggest friction: 7-step onboarding with no progress indication
- Second biggest: Budget setup felt like tax preparation

---

## Design Strategy

### Design Principles

**1. Make Finance Feel Like a Game**  
Every interaction should provide feedback. Saving money should feel like leveling up. Progress should be celebrated, not just tracked.

**2. Progressive Disclosure, Not Progressive Overwhelm**  
Don't show everything at once. Reveal features as users demonstrate readiness. Let them "unlock" capabilities.

**3. Visual Confidence**  
Bold colors, clear hierarchy, generous whitespace. If it looks trustworthy, users will trust it with their money.

**4. Delight in Micro-moments**  
The notification when you save, the animation when you hit a goal, the sound when you check your credit score. These moments build habit formation.

### Inspiration Board

Drew inspiration from:
- Duolingo (gamification, streaks, progress)
- Headspace (calm, approachable, guided)
- Cash App (bold, confident, minimal)
- Notion (flexible, personal, organized)

---

## Design Process

### Moodboards & Style Exploration (2 weeks)

Created 4 distinct visual directions:

**Option A: "Bold Finance"** — High contrast, geometric, fintech confidence  
**Option B: "Calm Money"** — Soft gradients, muted tones, zen-like  
**Option C: "Gen Z Maximalism"** — Bright gradients, playful illustration, maximalist  
**Option D: "Dark Minimal"** — Dark mode primary, neon accents, gaming aesthetic  

**User testing selected Option D:** Dark mode with vibrant accent colors resonated strongest with Gen Z users. It felt modern without being childish, serious without being corporate.

### Visual System (3 weeks)

**Color System:**
- Background: #0D0D0F (near-black)
- Surface: #1A1A1F (card backgrounds)
- Primary: #6366F1 (indigo — trust, stability)
- Accent: #22D3EE (cyan — energy, progress)
- Success: #10B981 (emerald)
- Warning: #FBBF24 (amber)
- Error: #F43F5E (rose)
- Text Primary: #F8FAFC
- Text Secondary: #94A3B8

**Typography:**
- Headlines: Satoshi (bold, modern geometric sans)
- Body: Inter (highly legible)
- Numbers: JetBrains Mono (clear financial figures)
- Scale: 14/16/20/24/32/48px

**Component Highlights:**

*Cards:* Rounded (16px), subtle glow on interaction, micro-animations on state change

*Buttons:* Full-width on mobile, gradient fills, press states with scale (0.98)

*Input fields:* Floating labels, animated borders, clear error states

*Progress indicators:* Circular for savings goals, linear for streaks, celebration animations

### Iconography & Illustration

- Custom icon set: 120 icons
- Style: Rounded, 2px stroke, filled accents
- Illustration style: Geometric, minimal, animated (Lottie)
- Mascot concept: "V" character for empty states and celebrations (optional)

### Prototype & Testing (3 weeks)

Built comprehensive Figma prototype with:
- Full onboarding flow (5 screens)
- Home dashboard
- Save flow (3 variants)
- Budget setup
- Profile and settings
- Notification states

**3 rounds of usability testing (8 participants each):**

Round 1:
- Onboarding still too long (fixed: reduced to 4 screens)
- Confusing navigation labels (fixed: "Home" vs "Dashboard" clarified)
- Save flow unclear (fixed: added progress indicator)

Round 2:
- Dark mode hard to read in bright light (fixed: added light mode toggle)
- Budget categories confusing (fixed: simplified to 5 defaults)
- Animation fatigue (fixed: reduced motion options)

Round 3: All success criteria met.

---

## Key Design Decisions

### 1. Onboarding Reimagined (4 screens, 90 seconds)

**Old flow:** 7 screens, 4+ minutes, ask for everything upfront  
**New flow:**
1. Welcome + value prop (animated)
2. Connect bank (single CTA, skip available)
3. Set first savings goal (guided, fun)
4. Enable notifications (explained benefit)

**Result:** Onboarding completion improved from 32% to 74%.

### 2. The "Vibe" Home Screen

Replaced data-dense dashboard with a "vibe" view:
- Large balance with subtle animation
- "Quick Save" primary action
- Savings goal progress as hero element
- Recent transactions (3 max, "see all" available)
- Daily "money tip" or motivational prompt

**Result:** Daily active usage increased 89%.

### 3. Celebration System

Created a progress celebration system:
- Saving milestones (first $100, $500, etc.)
- Streak achievements (7 days, 30 days)
- Budget adherence (first month under budget)
- Credit score improvements

Each celebration includes:
- Haptic feedback
- Lottie animation
- Shareable card (optional)

**Result:** Retention for users who hit first celebration: 78% D7.

### 4. Progressive Feature Discovery

Users unlock features through usage:
- Week 1: Save, View Balance
- Week 2: Budgets (unlocked after first save)
- Week 3: Credit score (after 3 consecutive logins)
- Week 4: Investment playground (after budget setup)

**Result:** Feature discovery increased 340%. Users trying 3+ features increased from 12% to 56%.

### 5. Notification Architecture

Designed a complete notification system:
- Daily summary (configurable time)
- Goal progress updates
- Unusual spending alerts
- Savings suggestions
- Celebration notifications

Each notification has:
- Clear action CTA
- Time sensitivity indicator
- Mute/unsubscribe option

**Result:** Push notification opt-in improved from 34% to 71%.

---

## Design System Implementation

### Component Library

Created 85 components in Figma with variants:

**Atoms:**
- Buttons (primary, secondary, ghost, icon)
- Input fields (text, number, currency, date)
- Toggles, checkboxes, radio buttons
- Progress indicators (linear, circular)
- Badges and tags
- Avatars
- Icons (120 custom)

**Molecules:**
- Cards (transaction, goal, notification)
- Lists (transaction, settings)
- Headers (navigation, page)
- Forms (login, signup, settings)
- Charts (spending, progress)

**Organisms:**
- Onboarding screens
- Home dashboard
- Save flow
- Budget builder
- Profile section
- Empty states

### Documentation

- Notion-based component documentation
- Usage guidelines for each component
- Accessibility notes
- Dark/light mode specifications
- Animation guidelines

### Design Tokens

Implemented complete token system:
- Colors (semantic naming)
- Typography (size, weight, line-height)
- Spacing (4px base grid)
- Shadows (4 levels)
- Border radius (4 sizes)
- Animation (duration, easing)

---

## Technical Handoff

### Figma Implementation
- Auto-layout throughout
- Variants for all component states
- Dev mode annotations
- Interactive components

### Documentation
- Notion wiki with component docs
- Video walkthroughs for complex components
- QA checklist for developers

### iOS/Android Collaboration
- Provided platform-specific guidelines
- Native component mapping (SwiftUI, Material)
- Animation implementation notes (Lottie, Motion)

---

## Results & Impact

### Retention Metrics (3 months post-launch)

| Metric | Before | After | Change |
|--------|--------|-------|--------|
| D1 Retention | 41% | 67% | +63% |
| D7 Retention | 18% | 44% | +144% |
| D30 Retention | 8% | 24% | +200% |
| Onboarding Completion | 32% | 74% | +131% |
| Feature Discovery | 12% | 56% | +367% |
| Push Opt-in Rate | 34% | 71% | +109% |

### Engagement Metrics

| Metric | Before | After | Change |
|--------|--------|-------|--------|
| Daily Active Users | 22% | 41% | +86% |
| Weekly Sessions | 2.1 | 4.8 | +129% |
| Avg Session Duration | 1.8 min | 4.2 min | +133% |
| Saves per User (Week 1) | 0.8 | 2.4 | +200% |
| Budget Setup Rate | 6% | 31% | +417% |

### Business Metrics

| Metric | Before | After |
|--------|--------|-------|
| App Store Rating | 4.2★ | 4.7★ |
| Reviews | 340 | 1,240 |
| Weekly Downloads | 180 | 890 |
| Conversion (free→paid) | 2.1% | 6.8% |
| Subscription Revenue | $42K/mo | $168K/mo |

---

## Qualitative Feedback

> "This app actually makes me want to check my money. The old version felt like a chore. The new one feels like a win." — User review

> "Finally, a finance app that doesn't look like a spreadsheet. The dark mode is chef's kiss." — User review

> "The celebrations when I hit savings goals are stupidly satisfying. I screenshot them every time." — TikTok review (screencap shared with permission)

---

## Lessons Learned

### What Worked

1. **Dark mode with vibrant accents** — This single aesthetic choice transformed user perception. It felt modern and differentiated from boring finance apps.

2. **Gamification through progressive disclosure** — Unlocking features created anticipation and rewarded engagement. Users felt like they were "leveling up" their financial life.

3. **Celebration micro-interactions** — The Lottie animations and haptic feedback created emotional moments that drove word-of-mouth.

### What I'd Do Differently

1. **More user testing on notification timing** — We launched with notifications that were too frequent. Should have tested frequency more rigorously.

2. **Earlier platform-specific design** — We designed generically and adapted later. Starting with iOS and Android guidelines from day one would have reduced handoff friction.

3. **Accessibility audit earlier** — Dark mode with vibrant colors created contrast challenges. Should have tested with accessibility users earlier in the process.

---

## Tools & Technologies

**Design:** Figma, Framer, Principle  
**Prototyping:** Figma, Lottie (animation)  
**Research:** UserTesting, Mixpanel, Amplitude  
**Documentation:** Notion, Storybook  
**Collaboration:** Loom, Slack, Notion  

---

## Project Details

**Timeline:** 16 weeks (Q3 2024)  
**Investment:** $120,000  
**ROI:** 18:1 (subscription revenue improvement)  
**Ongoing:** Design support retainer ($6K/month)

---

*CayCay Brooks designed the Verve mobile app UI system. For more information about mobile UX design, contact cayson@caysonbrooks.com*
