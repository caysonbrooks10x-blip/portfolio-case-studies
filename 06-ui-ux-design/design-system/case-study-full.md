# Case Study: Stratos — Design System & Component Library

## Client Overview

**Client:** Stratos  
**Industry:** Enterprise SaaS / Project Management Platform  
**Company Size:** 450 employees, Series D ($120M raised)  
**Project Duration:** 20 weeks  
**My Role:** Lead Design Systems Designer  
**Team:** 2 Design Systems Designers, 1 Design Technologist, 1 Technical Writer  

---

## The Challenge

Stratos had grown rapidly from startup to enterprise software company over 6 years. What started as a nimble project management tool had evolved into a complex platform serving Fortune 500 companies with features for resource management, time tracking, billing, reporting, and workflow automation.

The problem: Their product had been built by 8 different product teams using 4 different design approaches, resulting in a fragmented user experience that enterprise customers called "confusing" and "dated."

**Key Problems:**
- 47 different button styles across the product
- 12 different modal patterns
- 4 different navigation systems within the same product
- UI inconsistency costing $2M+/year in support and training
- New feature development slowed by 40% due to design debt
- Enterprise deals lost to competitors with more cohesive UX
- NPS had declined from 52 to 38 over 18 months

---

## Discovery & Research Phase

### Product Audit (3 weeks)

Conducted comprehensive audit of all product surfaces:

**UI Component Audit:**
- Documented 340+ unique UI components
- Identified 47 button variants (should be 1)
- Found 12 modal patterns (should be 1)
- Catalogued 8 different form styles
- Mapped 4 different navigation systems

**Visual Inconsistency Analysis:**
- 23 different font sizes in use
- 18 different border radius values
- 34 different shadow styles
- 6 inconsistent color usages for same semantic meaning
- No documented spacing system

**Interaction Pattern Analysis:**
- 8 different ways to open a dropdown
- 12 different form validation patterns
- 6 different ways to confirm an action
- 4 different ways to handle errors

### Stakeholder Interviews (2 weeks)

Conducted 24 interviews across:
- Product teams (8)
- Engineering teams (6)
- Design team (4)
- Customer success (3)
- Enterprise customers (5)

**Key insight from engineers:** "Every sprint, we waste 20% of time rebuilding components that should already exist."

**Key insight from product:** "We can't ship features as fast as competitors because we have to rebuild basic UI every time."

**Key insight from customers:** "Stratos does everything we need, but it feels like five different products bolted together."

### Competitive Analysis (1 week)

Analyzed design systems from:
- Enterprise: Salesforce, Atlassian, SAP, ServiceNow
- Modern: Figma, Notion, Linear, Craft
- Open source: Material, Chakra, Ant Design

**Key findings:**
- Top design systems have 80-120 core components
- Most successful systems document tokens, components, and patterns
- Engineering-friendly handoff is as important as visual documentation
- Design systems reduce new feature development time by 30-50%

### Technical Assessment (1 week)

Evaluated current technical infrastructure:
- Component architecture: React, some Vue legacy
- Styling: CSS modules, some Tailwind, some styled-components
- Documentation: Confluence, some Storybook
- Design files: Sketch (old), Figma (in transition)

**Gap analysis:**
- No shared design tokens
- No component governance
- No clear ownership
- No versioning strategy

---

## Design Strategy

### Guiding Principles

**1. Incremental Migration, Not Big Bang**  
Enterprise products can't stop development for a redesign. The system must be built for gradual adoption.

**2. Engineering is Half the Audience**  
A design system that designers love but engineers can't use will fail. Every component must be buildable and maintainable.

**3. Documentation is a Product**  
The design system is only as valuable as its documentation. If developers can't find answers, they build their own.

**4. Governance, Not Control**  
The system must enable teams, not restrict them. Clear processes for contribution and exception handling.

### System Architecture

**Three-Layer System:**

**Layer 1: Design Tokens**
- Primitive values (colors, spacing, typography)
- Semantic tokens (surface, action, feedback)
- Theme adaptation (light/dark, brand)

**Layer 2: Components**
- Atoms (buttons, inputs, icons)
- Molecules (cards, lists, forms)
- Organisms (tables, modals, navigation)
- Templates (page layouts)

**Layer 3: Patterns**
- Navigation patterns
- Form patterns
- Data display patterns
- Feedback patterns

---

## Design Process

### Phase 1: Foundation (Weeks 1-6)

**Design Token System**

Defined comprehensive token architecture:

*Primitive Tokens:*
```
colors.blue.50: #EFF6FF
colors.blue.100: #DBEAFE
colors.blue.500: #3B82F6
colors.blue.600: #2563EB
colors.blue.700: #1D4ED8
```

*Semantic Tokens:*
```
colors.background.primary: {light: #FFFFFF, dark: #0F172A}
colors.background.surface: {light: #F8FAFC, dark: #1E293B}
colors.action.primary: colors.blue.600
colors.action.danger: colors.red.600
colors.text.primary: {light: #0F172A, dark: #F8FAFC}
```

*Typography Tokens:*
```
font.family.display: Inter
font.family.body: Inter
font.size.xs: 12px
font.size.sm: 14px
font.size.base: 16px
font.size.lg: 18px
font.size.xl: 20px
font.size.2xl: 24px
font.size.3xl: 30px
font.size.4xl: 36px
```

*Spacing Tokens:*
```
space.1: 4px
space.2: 8px
space.3: 12px
space.4: 16px
space.5: 20px
space.6: 24px
space.8: 32px
space.10: 40px
space.12: 48px
space.16: 64px
```

*Motion Tokens:*
```
duration.instant: 0ms
duration.fast: 100ms
duration.normal: 200ms
duration.slow: 300ms
duration.slower: 500ms
easing.default: cubic-bezier(0.4, 0, 0.2, 1)
easing.in: cubic-bezier(0.4, 0, 1, 1)
easing.out: cubic-bezier(0, 0, 0.2, 1)
```

**Component Inventory**

Starting from the 340 components found, rationalized to 85 core components:

*Atoms (32):*
- Button (7 variants)
- Input (4 variants)
- Select (2 variants)
- Checkbox, Radio, Toggle
- Badge, Tag, Chip
- Avatar, Icon
- Spinner, Skeleton
- Tooltip, Popover
- Divider, Progress

*Molecules (28):*
- Card, Empty State
- Form Group, Field Set
- List, List Item
- Menu, Context Menu
- Tabs, Accordion
- Alert, Banner, Toast
- Modal, Drawer
- Table primitives
- Pagination

*Organisms (25):*
- Data Table
- Form (multi-step)
- Navigation (sidebar, topbar)
- Header, Footer
- Filter Panel
- Search Bar
- Command Palette

### Phase 2: Component Design (Weeks 7-14)

**Button Component (Example)**

States: default, hover, active, focus, disabled, loading  
Variants: primary, secondary, ghost, danger  
Sizes: sm, md, lg  
Content: text, icon-only, icon+text

```
Button/
├── Button.tsx (component)
├── Button.stories.tsx (Storybook)
├── Button.test.tsx (tests)
├── Button.module.css (styles)
└── index.ts (exports)
```

**Documentation Template:**

Each component documented with:
- Overview and purpose
- When to use / when not to use
- Anatomy (labeled diagram)
- States (all 6+ states)
- Variants (all combinations)
- Behavior (interactions, keyboard nav)
- Accessibility (ARIA, focus management)
- Code examples (React, props table)
- Changelog

### Phase 3: Documentation (Weeks 15-18)

**Documentation Site Architecture:**

```
/
├── Getting Started/
│   ├── Introduction
│   ├── Installation
│   ├── Theming
│   └── Migration
├── Foundations/
│   ├── Colors
│   ├── Typography
│   ├── Spacing
│   ├── Motion
│   └── Icons
├── Components/
│   ├── Atoms/
│   ├── Molecules/
│   └── Organisms/
├── Patterns/
│   ├── Forms
│   ├── Navigation
│   ├── Data Display
│   └── Feedback
└── Resources/
    ├── Figma Kit
    ├── Code Kit
    └── Contributing
```

**Documentation Standards:**
- Every component: live examples, props table, code snippets
- Every pattern: when to use, examples, related components
- Migration guides from old patterns to new
- Video walkthroughs for complex components

### Phase 4: Rollout (Weeks 19-20)

**Migration Strategy:**

*Week 1-4 (Pilot):*
- 2 product teams adopt system
- Weekly feedback sessions
- Bug fixes and refinements

*Week 5-12 (Phased Rollout):*
- 2-3 teams per week adopt
- Training sessions for each team
- Office hours for questions

*Week 13-20 (Full Adoption):*
- All teams on system
- Legacy component deprecation begins
- Metrics collection

**Change Management:**
- "System Champions" in each product team
- Monthly system office hours
- Slack channel for questions
- Quarterly system roadmap

---

## Key Design Decisions

### 1. Tokens-First Architecture

Built the token system before any components. This ensured:
- Consistent visual language across all components
- Easy theming for white-labeling
- Simple dark mode implementation
- Brand customization capability

**Result:** Token changes propagate to 100+ components automatically.

### 2. Component API Consistency

Every component follows the same prop naming conventions:
- `variant` for visual style
- `size` for dimensions
- `disabled`, `loading`, `error` for states
- `onClick`, `onChange` for events

**Result:** Engineers can use any component without reading docs. Predictable API reduces cognitive load.

### 3. Multi-Framework Support

Built components that work in:
- React (primary)
- Vue (secondary, via wrapper)
- HTML (for emails, docs)

**Result:** System serves all teams regardless of tech stack.

### 4. Figma-to-Code Handoff

Created bidirectional sync between Figma and code:
- Design tokens in Figma sync to code
- Code component names match Figma
- Dev mode annotations in Figma

**Result:** Designer-developer handoff time reduced 60%.

---

## Results & Impact

### Adoption Metrics (6 months post-launch)

| Metric | Before | After | Change |
|--------|--------|-------|--------|
| Unique UI components | 340 | 85 | -75% |
| Button variants | 47 | 7 | -85% |
| Modal patterns | 12 | 1 | -92% |
| Navigation systems | 4 | 1 | -75% |
| New feature dev time | Baseline | -38% | -38% |
| Design QA time | Baseline | -52% | -52% |

### Business Impact

| Metric | Before | After |
|--------|--------|-------|
| NPS | 38 | 54 |
| Support tickets (UI) | 450/mo | 180/mo |
| Enterprise deal loss (UX) | 12/quarter | 3/quarter |
| Design system adoption | 0% | 100% |

### Financial Impact

| Category | Annual Savings |
|----------|---------------|
| Engineering time (40% reduction in UI rebuilds) | $1.8M |
| Support cost reduction (60% fewer UI issues) | $380K |
| Sales enablement (faster demo builds) | $120K |
| Reduced enterprise churn (3 fewer losses/quarter) | $840K |

**Total Annual Impact:** $3.14M  
**Design System Investment:** $280,000  
**ROI:** 11:1

---

## Case Study: Enterprise Migration

One enterprise customer, GlobalTech (45,000 employees), had been on Stratos for 3 years with extensive customization. The design system migration required:

1. **Custom theme development** (2 weeks) — Matched GlobalTech brand colors
2. **Component migration workshops** (4 sessions) — Trained their 12-person dev team
3. **Legacy pattern documentation** — Mapped old patterns to new system
4. **Phased rollout support** (3 months) — On-call for issues

**Outcome:** GlobalTech completed migration in 6 months. Their admin interface now matches their brand while using standard components. Maintenance cost reduced 60%.

---

## Lessons Learned

### What Worked

1. **Token-first approach** — Building tokens before components made everything downstream faster and more consistent.

2. **Engineering partnership** — Having engineers on the design systems team from day one prevented "design beautiful, engineering can't build" problems.

3. **Comprehensive documentation** — The documentation site became the most-used resource in the company. Engineers rarely needed to ask questions because answers were findable.

### What I'd Do Differently

1. **Start governance earlier** — We built the system before defining contribution processes. Should have established governance in week 1.

2. **Include content designers** — Our documentation was written by engineers and designers. Content designers would have made it more user-friendly.

3. **Plan for Figma Libraries earlier** — We built components before fully establishing the Figma component library. Should have synced these from the start.

---

## Tools & Technologies

**Design:** Figma, FigJam  
**Components:** React, TypeScript, CSS Modules  
**Documentation:** Storybook, Chromatic, Notion  
**Design Tokens:** Style Dictionary, Figma Tokens  
**Version Control:** GitHub  
**Handoff:** Figma Dev Mode, Storybook  

---

## Project Details

**Timeline:** 20 weeks (Q2-Q3 2024)  
**Investment:** $280,000  
**ROI:** 11:1  
**Ongoing:** Design systems team ($18K/month retainer)

---

*CayCay Brooks led the Stratos design system. For more information about design systems engagements, contact cayson@caysonbrooks.com*
