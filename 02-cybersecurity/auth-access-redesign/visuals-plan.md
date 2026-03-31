# Visuals Plan — OmniBank Authentication & Access Control Redesign

## Executive Presentation Visuals

### Slide 1: Title Slide
**Visual:** Banking security-themed imagery with regulatory badges
**Content:** "OmniBank Authentication & Access Control Transformation" + your logo
**Style:** Professional, banking-appropriate, trust-inspiring

---

### Slide 2: The Regulatory Challenge
**Visual:** OCC/FDIC logo and examination finding summary
**Purpose:** Establish urgency and stakes
**Key findings:** No MFA, shared admin accounts, no PAM, no access certification

---

### Slide 3: Current State Assessment
**Visual:** Identity infrastructure diagram
**Components:** Three AD forests, multiple authentication systems, fragmented identity
**Purpose:** Illustrate complexity

---

### Slide 4: Zero-Trust Architecture
**Visual:** Zero-trust identity architecture diagram
**Components:** Okta IdP, CyberArk PAM, Saviynt governance, Splunk monitoring
**Purpose:** Show the target state

---

### Slide 5: Authentication Transformation
**Visual:** Before/after comparison
**Before:** Username/password only
**After:** Adaptive MFA with Okta Verify, biometrics, FIDO2
**Style:** Transformation visual

---

### Slide 6: Privileged Access Management
**Visual:** CyberArk PAM architecture diagram
**Components:** Credential vault, session recording, JIT access
**Purpose:** Show PAM implementation

---

### Slide 7: Access Governance
**Visual:** RBAC model diagram
**Components:** 847 roles, role assignment workflow, SoD enforcement
**Purpose:** Show role-based access control

---

### Slide 8: Regulatory Compliance Progress
**Visual:** Compliance scorecard
**Frameworks:** FFIEC, OCC, GLBA, SOX
**Status:** All marked "Compliant"
**Style:** Green checkmarks

---

### Slide 9: Account Takeover Reduction
**Visual:** Line chart showing ATO reduction
**Data:** 2,340 → 89 attempts/month
**Style:** Dramatic downward trend

---

### Slide 10: Business Impact
**Visual:** Three-column impact summary
**Columns:**
- Enforcement Avoided: $12M
- Fraud Reduction: 98%
- ROI: 79x
**Style:** Big numbers, confidence-inspiring

---

## Dashboard Mockups

### Identity Security Dashboard
**Visual:** Executive scorecard
**Components:**
- MFA Coverage: 100%
- PAM Status: All accounts managed
- Active Sessions: Monitoring
- ATO Attempts Blocked: Real-time counter

---

### Access Governance Dashboard
**Visual:** Access certification status
**Metrics:**
- Quarterly certifications: Complete
- Roles defined: 847
- Active users: 2,100
- SoD violations: 0

---

### Compliance Dashboard
**Visual:** Regulatory compliance status
**Frameworks:** FFIEC, OCC, GLBA, SOX
**Status:** All Compliant
**Last examination:** Passed with zero critical findings

---

## Architecture Diagrams

### Zero-Trust Identity Architecture
**Visual:** Technical architecture diagram
**Components:**
- Okta (IdP) → Applications (SAML/OIDC)
- CyberArk PAM → Privileged Systems
- Saviynt → Access Governance
- Splunk → Logging/Monitoring
- CrowdStrike → Endpoint
**Style:** Clean technical diagram

---

### PAM Architecture
**Visual:** CyberArk deployment diagram
**Components:**
- Credential vault
- Session manager
- Privileged threat analytics
- Application access manager
- Target connectors (Temenos, AWS, Windows)

---

### Authentication Flow
**Visual:** User authentication flow diagram
**Steps:**
1. User initiates login
2. Okta evaluates risk factors
3. Adaptive MFA triggered based on risk
4. Session established with token
5. Access logged to Splunk
**Style:** Numbered flow diagram

---

## Timeline Visualization

**Visual:** Gantt chart of 12-week engagement
**Phases:**
- Weeks 1-3: Assessment
- Weeks 4-6: Architecture Design
- Weeks 7-10: Implementation
- Weeks 11-12: Validation
**Style:** Color-coded by phase

---

## Process Flows

### Access Request Workflow
**Visual:** Flow diagram
**Steps:**
1. User requests access via ServiceNow
2. Manager approves
3. JIT access granted via CyberArk
4. Session recorded
5. Access automatically revoked
**Style:** Process flow

### Access Certification Workflow
**Visual:** Quarterly certification process
**Steps:**
1. Saviynt generates certification campaign
2. Managers review team access
3. SoD violations flagged
4. Violations remediated
5. Certification completed
**Style:** Process flow

---

## Infographic: The Cost of Inaction

**Visual:** Financial comparison
**Left side:** Engagement cost ($185K)
**Right side:**
- OCC enforcement action ($12M+)
- Monthly fraud losses ($180K)
- Regulatory fines ($1M-$50M)
**Style:** Dollar amounts, compelling contrast

---

## Tools and Methods Visual

**Visual:** Tool logos displayed
**Tools:**
- Okta (identity platform)
- CyberArk PAM (privileged access)
- Saviynt (access governance)
- Splunk (SIEM)
- CrowdStrike (endpoint)
- ServiceNow (workflow)
**Style:** Logo grid

---

## Social Media Graphics

### LinkedIn Post Image
**Visual:** Quote card with key stat
**Content:** "From 8 critical regulatory findings to zero in 12 weeks. OmniBank's authentication transformation."
**Style:** Clean, branded, professional

---

### Twitter/X Post Image
**Visual:** Infographic with key numbers
**Content:** $12M penalties avoided | 97% ATO reduction | 100% MFA | 79x ROI
**Style:** Bold numbers, minimal text

---

### Banking Security Stats Infographic
**Visual:** 4-panel stat infographic
**Stats:**
- 340,000 online banking users protected
- 1,200 privileged accounts managed
- 85 third-party vendors secured
- 847 RBAC roles defined

---

## Deliverable File Types

| Document | Visual Count | Primary Charts |
|----------|--------------|----------------|
| Gap Assessment | 10 | Architecture, compliance matrix |
| Architecture Design | 15 | Zero-trust diagrams, integration |
| Implementation Package | 8 | Configuration diagrams |
| Regulatory Documentation | 12 | Compliance evidence |
| Executive Summary | 10 | Before/after, business impact |

---

*All visuals should use OmniBank's color palette (with permission) or a professional banking security color scheme (navy blues, greens, with professional accents). Regulatory framework logos (OCC, FDIC, FFIEC) should be used appropriately.*
