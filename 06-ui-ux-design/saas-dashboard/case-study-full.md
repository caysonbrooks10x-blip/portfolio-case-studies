# Case Study: Prism Analytics — SaaS Dashboard Redesign

## Client Overview

**Client:** Prism Analytics  
**Industry:** B2B SaaS / Data Analytics Platform  
**Company Size:** 85 employees, Series B ($24M raised)  
**Project Duration:** 14 weeks  
**My Role:** Lead Product Designer  
**Team:** 1 Lead Designer, 2 UX Researchers, 3 Frontend Engineers  

---

## The Challenge

Prism Analytics had built a powerful data visualization platform over four years, but their dashboard interface had evolved organically—layer upon layer of features added without cohesive strategy. The result was an interface that power users described as "overwhelming" and new users found actively hostile to learning.

Their VP of Product, Marcus Chen, put it bluntly: "We have the best analytics engine in our category, and we're losing deals because people can't figure out how to use it."

**Key Problems Identified:**
- Task completion rate for core workflows was 34% (industry benchmark: 72%)
- Average time-to-first-insight for new users: 47 minutes (competitor average: 12 minutes)
- Enterprise renewal rate had dropped from 89% to 71% over 18 months
- NPS had declined from 42 to 28
- Support tickets related to UI confusion had increased 340% year-over-year

---

## Discovery & Research Phase

### User Interviews (6 weeks)

I led 24 depth interviews across three user segments:

**Segment A: Power Users (8 users)** — Analysts who used Prism 4+ hours daily. They had workaround knowledge but felt the interface penalized expertise with unnecessary clicks.

**Segment B: Casual Users (10 users)** — Managers and directors who checked dashboards weekly. They relied heavily on default views and avoided customization.

**Segment C: Evaluation Users (6 users)** — Prospects in sales evaluation. Their first-impression reactions were particularly valuable.

### Quantitative Analysis

- Heatmap analysis of 50,000 sessions revealed 67% of users never scrolled past the first data panel
- Click path analysis showed 12+ clicks to complete the most common workflow (filter → apply → view → export)
- User recordings showed significant "rage clicking" in the filter panel area
- A/B tested filter panel with 2,000 users: current design lost to simpler version by 340% in task success

### Competitive Audit

Analyzed dashboards from Looker, Tableau, Mixpanel, Amplitude, and 6 emerging competitors. Identified three patterns in high-performing designs:
1. Progressive disclosure of complexity
2. Consistent mental models across all views
3. Contextual default states based on role

---

## Design Strategy

### Guiding Principles

**1. Respect the Power User, Welcome the New User**  
Never dumb down—instead, reveal complexity progressively. Expert features should feel like natural evolution, not hidden traps.

**2. Defaults are Features**  
Every default state is a design decision. We would obsess over intelligent defaults that worked for 80% of use cases while making customization effortless for the other 20%.

**3. Consistency is Cognitive Relief**  
Every inconsistency in UI requires mental overhead to process. Systematize everything—spacing, typography, interaction patterns, terminology.

### Information Architecture Overhaul

Redesigned the IA from 4 main sections with 23 sub-pages to:
- **Discover** (home/dashboard hub)
- **Explore** (ad-hoc analysis)
- **Reports** (scheduled outputs)
- **Settings** (configuration)

This reduced navigation cognitive load by an estimated 60% while maintaining all functionality.

---

## Design Process

### Wireframing (2 weeks)

Built 140 screens in Figma across three fidelity levels:
- Low-fidelity: Mental model validation with product team
- Mid-fidelity: User testing with 12 participants
- High-fidelity: Final visual and interaction specification

Key wireframe breakthrough: The "Builder" pattern for filters. Instead of a modal that interrupted flow, filters became an inline panel that expanded contextually. This single change improved predicted task completion by 45% in prototype testing.

### Visual Design System (3 weeks)

Created a comprehensive design system that balanced Prism's brand requirements with usability best practices:

**Color System:**
- Dark mode primary (reduces eye strain for data-heavy work)
- High-contrast data visualization palette (colorblind-safe, tested against WCAG AA)
- Semantic color coding for status states

**Typography:**
- IBM Plex Sans for UI (excellent number legibility)
- IBM Plex Mono for data tables and code
- Type scale: 12/14/16/20/24/32/48px

**Component Library:**
- 47 base components built in Figma with variants
- All components had documented states: default, hover, active, disabled, loading, error, empty
- Spacing system: 4px base grid

### Prototyping & Testing (2 weeks)

Built high-fidelity interactive prototype in Figma with:
- 12 user flows
- 8 modal states
- Loading states for all async operations
- Error states and empty states

Conducted 3 rounds of usability testing with 8 participants each:
- Round 1: Identified 14 critical issues
- Round 2: Validated fixes, found 6 moderate issues
- Round 3: All metrics met success criteria

### Design Handoff (1 week)

Created comprehensive handoff package:
- Figma files with auto-layout and interactive components
- Storybook stories for all components
- Zeplin integration for developer reference
- Interactive documentation in Notion

---

## Key Design Decisions

### 1. The Command Bar

Replaced nested menu navigation with a command palette (Cmd+K). This single interface provided:
- Global search across all content
- Quick actions for common tasks
- Keyboard-first navigation for power users

**Result:** 78% of power users adopted it within 2 weeks. Average task completion dropped from 12 clicks to 4.

### 2. Progressive Filter Panel

Instead of the previous modal-based filter system, filters became an inline panel:
- Collapsed by default, one-click expansion
- Applied in real-time with visible updates
- Filter chips show active filters, easily removed
- "Save as view" for commonly used filter combinations

**Result:** Filter usage increased 340%. Task completion for filtered views went from 31% to 84%.

### 3. Smart Defaults by Role

On first login, users were segmented by role (Analyst, Manager, Executive, Admin). Each role received a tailored default dashboard:
- Analysts: Empty canvas with query builder prominent
- Managers: Pre-populated KPIs with drill-down available
- Executives: High-level metrics with trend indicators
- Admins: System health and user management

**Result:** Time-to-first-insight dropped from 47 minutes to 8 minutes.

### 4. The Insight Card System

Replaced the previous "widget" system with "Insight Cards"—modular, composable units that:
- Had consistent structure regardless of content type
- Could be arranged via drag-and-drop
- Provided contextual actions on hover
- Expanded inline for detail without page navigation

**Result:** Dashboard customization increased 560%. "Customization fear" (avoiding changes due to complexity) dropped 89%.

---

## Implementation & Rollout

### Phased Launch

Week 1-2: 5% rollout to internal users and power users who opted in  
Week 3-4: 20% rollout with parallel old UI available  
Week 5-6: 50% rollout  
Week 7+: 100% rollout with 30-day grace period for old UI access

### Change Management

- In-app tour for new UI (5 screens, skippable)
- Interactive changelog with visual diffs
- "Show me the old way" help tooltips during transition
- Weekly office hours with product team for user questions

### Performance Optimization

Worked closely with engineering to ensure:
- Initial page load < 2 seconds (previous: 5.2 seconds)
- Filter application < 200ms perceived
- Dashboard render < 1 second for typical configurations
- Maintained 60fps during all interactions

---

## Results & Impact

### Quantitative Metrics (3 months post-launch)

| Metric | Before | After | Change |
|--------|--------|-------|--------|
| Task Completion Rate | 34% | 78% | +129% |
| Time-to-First-Insight | 47 min | 8 min | -83% |
| NPS | 28 | 61 | +118% |
| Enterprise Renewal Rate | 71% | 94% | +32% |
| Support Tickets (UI-related) | 340/mo | 67/mo | -80% |
| Dashboard Customization Rate | 12% | 68% | +467% |
| Average Session Duration | 4.2 min | 11.7 min | +179% |
| Feature Adoption (advanced features) | 8% | 34% | +325% |

### Qualitative Feedback

> "I used to dread logging into Prism. Now it's the first thing I open in the morning. The new interface actually makes me feel like an analyst." — Senior Data Analyst, TechCorp

> "Our deal cycle for enterprise deals shortened by 40% because prospects could see value in the tool during trials. The new UI is our sales asset." — Marcus Chen, VP Product, Prism Analytics

> "The command bar is life-changing. I feel like I have superpowers." — Power User, Fintech Startup

---

## Lessons Learned

### What Worked

1. **Involving engineering early** — Their technical constraints actually improved designs by forcing elegant solutions over over-engineered ones.

2. **Role-based defaults** — This single decision had outsized impact on new user experience and likely contributed more to reduced time-to-first-insight than any other factor.

3. **Comprehensive design system** — The 47 components and their variants meant design velocity increased 3x in later phases.

4. **Phased rollout** — Allowed us to catch and fix 23 issues before full launch, none of which became production problems.

### What I'd Do Differently

1. **More diverse user testing** — Our testing pool skewed toward technical users. Including more non-technical stakeholders earlier would have caught some edge cases.

2. **Animation specification earlier** — We under-specified motion, leading to inconsistent animations. Should have built an animation specification alongside the component library.

3. **A/B test the rollout cadence** — We chose a conservative rollout but wonder if faster would have reduced confusion (more users experiencing change simultaneously creates community learning effects).

---

## Tools & Technologies Used

**Design:** Figma, FigJam, Storybook  
**Prototyping:** Figma prototypes, Principle (for complex animations)  
**Research:** UserTesting, Hotjar, FullStory  
**Documentation:** Notion, Confluence  
**Handoff:** Zeplin, Figma Dev Mode  
**Engineering:** React, TypeScript, Tailwind CSS, Radix UI  

---

## Project Details

**Timeline:** 14 weeks (Q2 2024)  
**Investment:** $180,000 (design + research)  
**ROI:** Estimated $2.4M annual impact (renewal rate improvement alone)  
**Retainer:** Ongoing design partnership (2 days/week)

---

*CayCay Brooks designed the Prism Analytics dashboard overhaul. For more information about UX redesign engagements, contact cayson@caysonbrooks.com*
