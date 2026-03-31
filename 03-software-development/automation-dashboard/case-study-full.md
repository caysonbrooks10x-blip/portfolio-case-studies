# Case Study: Prism Health — Workflow Automation Dashboard

## Client Overview

**Client:** Prism Health Technologies  
**Industry:** Healthcare Technology  
**Headquarters:** Denver, Colorado  
**Company Size:** 540 employees, $120M ARR  
**Founded:** 2015  

**Key Stakeholders:**
- Dr. Amanda Foster, Chief Medical Officer
- Brian Holbrook, VP of Operations
- Christina Nguyen, Director of Clinical Informatics

---

## The Challenge

Prism Health operates a population health management platform for regional hospital networks. Their platform identified high-risk patients, coordinated care teams, and tracked outcomes for 2.3 million patients across 8 states.

The problem: their care coordination workflow was a mess. Nurses spent 4+ hours daily on manual tasks that should have been automated:

- Patient data scattered across 14 different EHR systems
- Care plans created manually in Word templates
- Appointment reminders sent via individual phone calls
- Quality metrics calculated in Excel spreadsheets
- Compliance reports compiled manually for CMS

**Current State:**
- 340 care coordinators
- 14 EHR integrations (all custom-built)
- 4+ hours manual work per coordinator daily
- 23% of care plans missing required elements
- CMS compliance audit findings: 12 in 2 years

**The Vision:**
Build a workflow automation dashboard that:
1. Unifies patient data from all 14 EHR systems
2. Automates care plan generation
3. Triggers automated outreach (SMS, email, calls)
4. Calculates quality metrics in real-time
5. Generates CMS compliance reports automatically

**Budget:** $380,000  
**Timeline:** 16 weeks  
**Critical Constraint:** HIPAA compliant, SOC 2 Type II certified infrastructure

---

## Our Approach

### Phase 1: Clinical Workflow Discovery (Weeks 1-3)

**Stakeholder Interviews:**
We spent 3 weeks embedded with care coordination teams:
- Shadowed 12 care coordinators across 4 hospital networks
- Interviewed 8 clinical managers
- Documented 47 distinct workflow steps
- Identified 12 automation opportunities

**Key Insights:**
- Care coordinators spent 68% of time on data gathering, not patient care
- Most "clinical decisions" were actually pattern matching (diabetes + hypertension + no recent A1C = outreach)
- Compliance failures came from forgotten follow-ups, not clinical errors
- The hardest part wasn't clinical — it was coordination across 14 EHR systems

### Phase 2: Architecture & Security Design (Weeks 3-5)

**Technical Architecture:**
- React 18 dashboard with real-time updates
- Node.js backend with FHIR R4 API
- PostgreSQL for structured data
- Elasticsearch for patient search
- Redis for session and workflow state
- Bull queues for background automation

**Security (Healthcare-Specific):**
- HIPAA BAA required
- SOC 2 Type II infrastructure
- End-to-end encryption (at rest and in transit)
- Audit logging for all PHI access
- Role-based access with care team scopes
- MFA for all clinical users

**Integrations:**
- 14 EHR systems via FHIR R4 where available
- Custom HL7 adapters for legacy systems
- Direct database connections (read-only) where FHIR unavailable

### Phase 3: Core Development (Weeks 5-12)

**Patient 360 View:**
- Unified patient timeline across all EHRs
- Risk stratification scoring
- Care gap identification
- Allergy and medication reconciliation
- Social determinants of health (SDOH)

**Care Plan Automation:**
- Template-based care plan generation
- Evidence-based guideline engine (ADA, AHA, NQF)
- Automated coding suggestions (CPT, ICD-10)
- Care team assignment workflow

**Workflow Engine:**
- Visual workflow builder
- Trigger-based automation rules
- Drag-and-drop task management
- Escalation rules
- SLA tracking

**Automated Outreach:**
- SMS via Twilio (appointment reminders)
- Email via SendGrid
- Voice calls via Twilio (high-priority)
- Patient portal notifications
- Batch outreach for campaign-style programs

**Reporting & Compliance:**
- Real-time quality dashboards
- HEDIS measure tracking
- Star Ratings optimization
- CMS reporting module
- Audit trail export

### Phase 4: Testing & Deployment (Weeks 13-16)

- Security audit (penetration testing)
- HIPAA compliance review
- EHR integration testing (14 systems)
- User acceptance testing (40 care coordinators)
- Staff training (2-hour sessions)
- Phased rollout: 1 network → 4 networks → all 8

---

## Technical Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    Care Coordinator Dashboard                 │
│              React 18 │ Real-time │ Role-based               │
└────────────────────────────┬────────────────────────────────┘
                             │ HTTPS
┌────────────────────────────▼────────────────────────────────┐
│                    API Gateway                               │
│         Node.js │ Express │ JWT │ FHIR R4 Compliance         │
│              HIPAA Audit Logging │ Rate Limiting             │
└──────┬─────────────────┬─────────────────┬───────────────────┘
       │                 │                 │
┌──────▼──────┐   ┌──────▼──────┐   ┌──────▼──────┐
│  Workflow   │   │  Outreach   │   │  Reporting  │
│   Engine    │   │   Engine    │   │   Engine    │
└──────┬──────┘   └──────┬──────┘   └──────┬──────┘
       │                 │                 │
┌──────▼─────────────────▼─────────────────▼──────┐
│              Data Layer                            │
│    PostgreSQL │ Elasticsearch │ Redis │ S3        │
└──────┬───────────────────────────────────────────┘
       │
┌──────▼───────────────────────────────────────────┐
│              EHR Integration Layer                 │
│   FHIR R4 Gateway │ HL7 Adapters │ DB Connectors │
└──────┬──────┬──────┬──────┬──────┬──────┬────────┘
       │      │      │      │      │      │
   [Epic] [Cerner] [Allscripts] [athena] [eCW] [...9]
```

---

## Key Features Delivered

### 1. Patient 360 Dashboard
The unified view care coordinators had been asking for:
- Cross-EHR patient timeline
- Real-time risk score (0-100)
- Care gap tracker
- Medication list with reconciliation status
- SDOH indicators (housing, food, transport)
- Recent interactions across all care settings

### 2. Care Plan Generator
Automated care plan creation based on:
- Diagnoses (ICD-10 codes)
- Recent lab values
- Medication adherence
- Past care encounters
- Evidence-based guidelines
- Care coordinator notes

Output: Complete care plan document, coded appropriately, ready for physician signature.

### 3. Workflow Automation Engine
Visual workflow builder with:
- Trigger-based rules (time, event, condition)
- Drag-and-drop task creation
- Automated assignment based on care team
- Escalation paths
- SLA alerts
- Workload balancing

### 4. Automated Outreach System
Multi-channel patient communication:
- **SMS:** Appointment reminders, medication refills, care gap notifications
- **Email:** Educational content, care plan summaries
- **Voice:** High-priority outreach, motivational interviewing
- **Portal:** Patient-facing task completion

### 5. Quality Metrics Dashboard
Real-time visibility into performance:
- HEDIS measure tracking
- Star Ratings metrics
- Quality bonus eligibility
- Gap closure rates
- Outreach effectiveness

### 6. Compliance Reporting
Automated CMS compliance:
- Real-time audit trails
- Automated documentation
- Report generation
- Pre-audit self-assessment

---

## Results & Metrics

### Timeline
| Milestone | Target | Actual |
|-----------|--------|--------|
| Discovery Complete | Week 3 | Week 3 |
| Security Approval | Week 5 | Week 6 |
| Core Dashboard | Week 10 | Week 11 |
| All 14 EHR Integrations | Week 14 | Week 14 |
| Full Deployment | Week 16 | Week 16 |

### Efficiency Metrics
| Metric | Before | After | Improvement |
|--------|--------|-------|-------------|
| Manual work/coordinator/day | 4+ hours | 45 min | **81% reduction** |
| Care plan completion time | 45 min | 8 min | **82% faster** |
| Care plan completeness | 77% | 98% | **21% increase** |
| Outreach volume/coordinator | 12/day | 85/day | **7x increase** |
| Appointment no-show rate | 23% | 11% | **52% reduction** |
| Compliance audit findings | 6/year | 1/year | **83% reduction** |

### Clinical Outcomes (6 months post-launch)
| Metric | Value |
|--------|-------|
| Patients with care plans | 340K → 890K |
| Care gap closure rate | 34% → 67% |
| A1C control (<8) | 61% → 74% |
| Blood pressure control | 58% → 71% |
| Patient satisfaction (CAHPS) | 3.2 → 4.1 |
| Care coordinator satisfaction | 2.8 → 4.4 |

### Financial Impact
| Metric | Value |
|--------|-------|
| Care coordinator productivity gain | $4.2M/year |
| Quality bonus earned (Year 1) | $3.8M |
| Reduced compliance penalties | $890K |
| Avoided headcount (20 roles) | $2.4M |
| **Total Year 1 Value** | **$11.3M** |

---

## What Made This Successful

**1. Clinical Validation at Every Step**
We didn't just build software — we embedded with care teams. Every feature was validated by the people who'd use it. The Patient 360 view came directly from hearing coordinators say "I wish I could see everything in one place."

**2. Automation That Respects Clinical Judgment**
We didn't try to replace clinical decisions. We automated the pattern-matching work (identify patients who need outreach) and left the clinical judgment to nurses. This was the key to clinician adoption.

**3. HIPAA-First Architecture**
We built security into every layer from Day 1, not bolted on at the end. This accelerated the compliance review and earned trust from Prism's legal team.

**4. Phased Rollout by Network**
We launched to one hospital network for 4 weeks before expanding. This caught 40 issues and prevented them from reaching all 8 networks simultaneously.

---

## Client Testimonial

> "Our care coordinators were drowning in manual work. They became nurses to care for patients, not to copy-paste data between 14 EHRs. This platform gave them back 3+ hours daily — and that time goes back into patient care. The ROI was obvious within 90 days."
>
> — Dr. Amanda Foster, CMO, Prism Health Technologies

---

## Technical Stack Summary

| Layer | Technology | Why |
|-------|------------|-----|
| Dashboard | React 18, TypeScript | Real-time, responsive UI |
| State | Redux Toolkit | Predictable state management |
| Backend | Node.js, Express | Reliability, async processing |
| Database | PostgreSQL | ACID compliance, HIPAA-friendly |
| Search | Elasticsearch | Patient search across EHRs |
| Cache | Redis | Session, workflow state |
| Queue | Bull | Background automation jobs |
| FHIR | FHIR R4 | Standard healthcare interoperability |
| HL7 | Custom adapters | Legacy EHR integration |
| SMS/Voice | Twilio | HIPAA-compliant communications |
| Email | SendGrid | Email automation |
| Storage | S3 | Document storage (encrypted) |
| Monitoring | Datadog, Sentry | APM, error tracking |
| Security | Auth0, Vault | MFA, secrets management |

---

## Project Stats

- **Duration:** 16 weeks
- **Team Size:** 9 engineers + 2 designers + 1 clinical consultant + 1 PM
- **Lines of Code:** ~62,000 (TypeScript)
- **Test Coverage:** 88%
- **Final Cost:** $378,000 (under budget by $2,000)
- **EHR integrations:** 14
- **HIPAA audit:** Passed first time
- **SOC 2:** Type II certified
- **Care coordinators deployed:** 340
- **Patients covered:** 2.3 million
