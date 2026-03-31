# Visuals Plan: RepFlow — AI SaaS MVP Build

## Primary Hero Visual

### 1. Rep Coaching Interface Mockup
**Format:** App UI mockup  
**Dimensions:** 1440×900 (desktop), 390×844 (mobile)  
**Content:** 
- Sales rep laptop/phone screen during active call
- Subtle coaching cue card appearing: "You're talking 72% — aim for 40%"
- Customer sentiment indicator showing neutral → positive shift
- Minimal, non-distracting design

**Design notes:** Clean SaaS product aesthetic, subtle animations for cue appearance, professional color palette. Navy (#1a1a2e) primary, teal (#00d4aa) for positive cues, amber for neutral, coral for urgent.

---

## Supporting Visuals

### 2. System Architecture Diagram
**Format:** Technical architecture  
**Dimensions:** 1200×800  
**Content:**
- Audio input (Zoom, Teams, phone)
- AssemblyAI STT processing
- GPT-4o coaching engine
- WebSocket delivery
- Rep interface output
- Manager dashboard
- CRM integrations

**Design notes:** Clean technical diagram, icon-based, minimal text, labeled data flows.

---

### 3. Latency Pipeline Visualization
**Format:** Flow diagram with timing  
**Dimensions:** 1000×600  
**Content:**
- 5 stages in pipeline with ms timings
- AssemblyAI → NLP → GPT-4o → WebSocket → Rep screen
- Total: 180ms (<200ms target)
- Visual: stage-by-stage breakdown

**Design notes:** Data visualization style, clean timing labels, progress flow arrows.

---

### 4. Manager Dashboard Mockup
**Format:** Web app mockup  
**Dimensions:** 1200×800  
**Content:**
- Team performance overview
- Individual rep cards with coaching scores
- Call library with AI annotations
- Coaching conversation thread

**Design notes:** Professional B2B SaaS dashboard, clean data visualization, card-based layout.

---

### 5. Post-Call Summary Mockup
**Format:** Mobile/email notification mockup  
**Dimensions:** 800×600  
**Content:**
- Summary card showing: call duration, key moments, performance score
- Sentiment timeline mini-chart
- Top coaching points
- Next steps checklist

**Design notes:** Clean summary layout, scannable format, actionable items highlighted.

---

### 6. Timeline / Roadmap Graphic
**Format:** Gantt/timeline  
**Dimensions:** 1200×400  
**Content:**
- 9-week project timeline
- Phases: Discovery, Infrastructure, STT, Coaching, Frontend, Integrations, QA, Launch
- Key milestones marked

**Design notes:** Clean project timeline, milestone markers, phase colors.

---

### 7. Pilot Results Dashboard
**Format:** Data visualization  
**Dimensions:** 1000×600  
**Content:**
- 3 customer logos
- Key metrics: NPS +47, 420 reps, 4.7/5 satisfaction
- Timeline from MVP to seed close

**Design notes:** Results-focused, clean data cards, professional palette.

---

### 8. Startup Metrics Transformation
**Format:** Before/after visualization  
**Dimensions:** 800×500  
**Content:**
- Concept → MVP → Pilot → Seed
- Valuation progression: $0 → $12M
- Key milestones on timeline

**Design notes:** Startup growth narrative visualization, milestone markers.

---

## Social Media Assets

### 9. LinkedIn Post Header
**Format:** Social graphic  
**Dimensions:** 1200×627  
**Content:**
- Bold: "$12M valuation. 9 weeks."
- Subtext: "Built RepFlow from concept to seed round"
- Logo: brooksai

**Design notes:** High contrast, bold numbers, professional startup aesthetic.

---

### 10. Case Study PDF Cover
**Format:** Document cover  
**Dimensions:** 8.5×11  
**Content:**
- Title: "How RepFlow Built a $12M AI SaaS in 9 Weeks"
- Product name and logo
- Hero metrics
- Cayson Brooks branding

---

## Design System Reference

### Color Palette
| Usage | Color | Hex |
|-------|-------|-----|
| Primary | Dark navy | #1a1a2e |
| Secondary | Slate | #4a5568 |
| Accent positive | Teal | #00d4aa |
| Accent neutral | Amber | #f59e0b |
| Accent negative | Coral | #ff6b6b |
| Background | Off-white | #f7fafc |
| Text primary | Near-black | #1a202c |
| Text secondary | Gray | #718096 |

### Typography
- Headlines: Inter Bold, 28–48px
- Body: Inter Regular, 16px
- Data/Metrics: SF Mono or Inter Mono, 24–48px
- Labels: Inter Medium, 12–14px

### SaaS Product Specific
- Clean, minimal interfaces
- Subtle animations
- Professional iconography
- Data-dense but scannable

---

## Mockup Generation Tools

1. **Product UI mockups:** Figma, Plasmic, or custom React components
2. **Architecture diagrams:** Whimsical, Miro, draw.io
3. **Timeline graphics:** Timeline JS, or custom HTML/CSS
4. **Metrics visualizations:** Chart.js, Obsidian, Flourish
5. **Social graphics:** Canva, Figma
