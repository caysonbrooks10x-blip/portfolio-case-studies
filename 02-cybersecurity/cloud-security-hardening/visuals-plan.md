# Visuals Plan — Meridian Health Cloud Security Hardening

## Executive Presentation Visuals

### Slide 1: Title Slide
**Visual:** Healthcare-themed cybersecurity imagery
**Content:** "Meridian Health Cloud Security Transformation" + date + your logo
**Style:** Professional, healthcare-appropriate color palette (blue/white with security accents)

---

### Slide 2: The Situation
**Visual:** Timeline showing cloud migration vs security capability growth
**Purpose:** Illustrate the security-velocity gap in healthcare cloud adoption
**Key dates:** Migration start, GuardDuty alert, engagement start

---

### Slide 3: Infrastructure Overview
**Visual:** Multi-account AWS architecture diagram
**Components:** 5 accounts (production, staging, development, security tooling, shared services)
**Annotations:** Show resource counts per account and data flows

---

### Slide 4: Methodology
**Visual:** Five-phase process diagram with icons
**Phases:**
1. Incident Investigation (magnifying glass + shield)
2. Cloud Security Posture Assessment (radar/scan)
3. Remediation Planning (clipboard)
4. Implementation Support (wrench/gear)
5. Validation & Training (checkmark + graduation cap)
**Style:** Clean infographic with arrows showing flow

---

### Slide 5: The Incident
**Visual:** Attack timeline diagram
**Stages:** Credential exposure → Access → Enumeration → Lateral movement → Cryptojacking deployment → Detection
**Purpose:** Show how the initial compromise occurred

---

### Slide 6: Vulnerability Breakdown (Donut Chart)
**Visual:** Donut chart showing vulnerability distribution by severity
**Segments:** Critical (4), High (23), Medium (67), Low (62)
**Style:** Red/Orange/Yellow/Green color coding

---

### Slide 7: Critical Findings Detail
**Visual:** Four-panel layout, one per critical vulnerability
**Each panel:**
- Vulnerability name
- Attack vector diagram
- Affected resources count
- Status indicator (Fixed)

---

### Slide 8: IAM Security Transformation
**Visual:** Before/after comparison
**Before:** 47 users with AdminAccess, 12 former employees with active keys, 11% MFA coverage
**After:** 0 overprivileged users, all former employees removed, 100% MFA
**Style:** Red X → Green checkmark transformation

---

### Slide 9: Network Architecture Transformation
**Visual:** Flat VPC → Zero-trust segmentation diagram
**Before:** Single VPC, all environments flat, unrestricted peering
**After:** Transit Gateway hub, segmented environments, strict routing
**Purpose:** Show the zero-trust architecture redesign

---

### Slide 10: Compliance Progress
**Visual:** Progress bars for each compliance framework
**Frameworks:** HIPAA (57%→87%), CIS AWS (38%→89%), AWS FSR (45%→91%)
**Style:** Green progress bars showing improvement

---

### Slide 11: Business Impact
**Visual:** Three-column impact summary
**Columns:**
- HIPAA Audit: Passed ✅
- Cyber Insurance: $180K savings
- ROI: 69.6x
**Style:** Big numbers, confidence-inspiring

---

## Dashboard Mockups

### Security Posture Dashboard
**Visual:** Executive security scorecard
**Components:**
- Overall Security Score: 92/100 (was 39/100)
- Risk Level: Medium (was Critical)
- Open Vulnerabilities: 32 (was 156)
- HIPAA Compliance: 87% (was 57%)
- Days Since Incident: 540+
- Accounts Protected: 5 of 5

---

### Compliance Dashboard
**Visual:** Real-time HIPAA compliance tracking
**Sections:**
- Administrative safeguards (progress bar)
- Physical safeguards (N/A for cloud)
- Technical safeguards (progress bar)
- Top 10 findings requiring attention
- Audit history and trend

---

### Vulnerability Trends Dashboard
**Visual:** Line chart tracking vulnerability counts over time
**Lines:** Critical, High, Medium, Low over 18 months
**Period:** Pre-assessment through current
**Style:** Time series with downward trend highlighted

---

## Architecture Diagrams

### Before: Flat VPC Architecture
**Visual:** Single VPC diagram showing:
- All subnets in one VPC
- VPC peering connections (red lines)
- Public access points
- Lack of segmentation

### After: Zero-Trust Architecture
**Visual:** Hub-and-spoke with Transit Gateway
**Components:**
- Transit Gateway as central hub
- Separate VPCs per environment (production, staging, development)
- AWS Network Firewall at hub
- Security groups referencing IAM principals
- VPC endpoints for AWS services

---

## Infographic: The Cost of Inaction

**Visual:** Financial comparison infographic
**Left side:** Cost of engagement ($125K)
**Right side:**
- Average healthcare breach cost ($10.37M)
- HIPAA OCR fines ($100-$50K per violation)
- Cyber insurance premium increase ($50K+)
- Breach notification costs ($50-$150 per record)
**Style:** Dollar amounts, compelling contrast

---

## Process Flow: How the Attack Worked

**Visual:** 6-panel comic-style attack narrative
**Panel 1:** "Contractor pushes code to GitHub" (accidental key exposure)
**Panel 2:** "Attacker finds exposed credentials"
**Panel 3:** "Access staging environment"
**Panel 4:** "Enumerate resources, find gaps"
**Panel 5:** "Deploy cryptojacking software"
**Panel 6:** "GuardDuty detects anomaly"
**Style:** Simplified, clear, non-technical audience friendly

---

## Tools and Methods Visual

**Visual:** Tool logos displayed with findings count
**Tools:**
- Prowler (156 findings)
- GuardDuty (1 critical alert)
- Security Hub (89 findings)
- IAM Access Analyzer (23 findings)
- GitGuardian (12 exposed keys)
**Style:** Logo grid with finding badges

---

## HIPAA Mapping Visual

**Visual:** HIPAA Security Rule categories with status
**Categories:**
- Administrative (addressed)
- Physical (N/A)
- Technical (addressed)
**For each:** Implementation status, key controls

---

## Timeline Visualization

**Visual:** Gantt chart of engagement
**Phases:**
- Weeks 1-2: Incident Investigation
- Weeks 3-5: Assessment
- Week 6: Planning
- Weeks 7-9: Implementation
- Week 10: Validation
**Style:** Color-coded by phase

---

## Training Photos/Requirements

| Visual | Description | Source |
|--------|-------------|--------|
| Training session | AWS security fundamentals | On-site or stock |
| Certification | Staff AWS certification | Provided |
| Architecture | Zero-trust network design | Created |
| Dashboard | Security posture dashboard | Created |

---

## Social Media Graphics

### LinkedIn Post Image
**Visual:** Quote card with key stat
**Content:** "From 156 security misconfigurations to 32 in 10 weeks. Meridian Health's cloud security transformation."
**Style:** Clean, branded, professional

---

### Twitter/X Post Image
**Visual:** Infographic with key numbers
**Content:** 4→0 Critical vulns | $180K savings | 69x ROI | HIPAA Passed
**Style:** Bold numbers, minimal text

---

### Infographic: Healthcare Cloud Security Stats
**Visual:** 4-panel stat infographic
**Stats:**
- Healthcare data: 10-50x more valuable than financial data
- Average breach cost: $10.37M
- HIPAA fines: Up to $50K per violation
- 94% attack surface reduction achieved

---

## Technical Diagrams for Final Report

### Multi-Account Architecture
**Full technical architecture with:**
- All 5 AWS accounts
- AWS Organizations structure
- Transit Gateway attachments
- Security service integration
- Identity flow

### Vault Architecture
**HashiCorp Vault topology showing:**
- 3-node HA cluster
- AWS KMS integration
- Secrets engines
- Authentication methods
- Integration points

---

## Deliverable File Types

| Document | Visual Count | Primary Charts |
|----------|--------------|----------------|
| Incident Report | 8 | Attack timeline, scope |
| Assessment Report | 15 | Vulnerability breakdown, compliance |
| Architecture Docs | 12 | Network diagrams, Vault topology |
| Executive Summary | 8 | Before/after, business impact |
| Training Materials | 6 | Process flows, checklists |

---

*All visuals should use Meridian Health's color palette (with permission) or a professional healthcare cybersecurity color scheme (blues, whites, with red/orange for warnings and green for success).*
