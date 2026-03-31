# Case Study: OmniBank Authentication & Access Control Redesign
## Enterprise Banking Security Transformation

---

## 1. Executive Summary

OmniBank, a regional bank serving 1.2 million customers across 85 branches, engaged us for a comprehensive authentication and access control redesign following a regulatory examination that identified critical deficiencies in their identity and access management program. With $18B in assets under management and strict requirements from the OCC, FDIC, and state banking regulators, OmniBank faced potential enforcement actions if they couldn't demonstrate meaningful improvement. Over a 12-week engagement, our identity and access management specialists assessed their authentication systems, identified 34 critical control deficiencies, implemented a zero-trust identity architecture using modern authentication protocols, and established continuous access governance practices. The bank passed their next regulatory examination with zero critical findings, avoided an estimated $12M in potential enforcement penalties, and reduced account takeover incidents by 97%.

**Engagement Value:** $185,000 | **Timeline:** 12 weeks | **Team:** 5 identity/access specialists

---

## 2. Client Profile

**Company:** OmniBank
**Industry:** Regional Banking/Financial Services
**Size:** 2,100 employees, $18B assets under management
**Headquarters:** Richmond, Virginia
**Tech Stack:** Core banking system (Temenos), web banking (Java/Spring), mobile apps (iOS/Android), Active Directory (on-premises), AWS (digital banking infrastructure)

**The Client's Situation:**
OmniBank had grown through acquisition, operating with three separate core banking systems and inconsistent authentication practices across channels. Their digital banking platform supported 340,000 active online users and 180,000 active mobile users. A routine regulatory examination by the OCC identified critical deficiencies: weak password requirements, no multi-factor authentication for administrative access, inadequate access logging, and no formal access certification process. The examiners gave OmniBank 90 days to demonstrate corrective action or face formal enforcement.

**Pain Points:**
- Regulatory enforcement pressure with 90-day deadline
- Fragmented identity infrastructure from acquisitions
- No centralized identity governance
- Weak authentication for high-privilege access
- Inadequate audit trails for compliance
- No automated access certification process
- Mobile banking security lagging behind web
- Third-party vendor access unmonitored

---

## 3. The Problem

Following the regulatory examination, OmniBank's CISO and Chief Compliance Officer faced several urgent challenges:

1. **Regulatory Deadline:** The OCC gave OmniBank 90 days to demonstrate meaningful progress on identity and access management deficiencies. Failure could result in formal enforcement actions, civil money penalties, and reputational damage.

2. **Fragmented Identity Infrastructure:** Three acquisitions had left OmniBank with three separate core banking systems, multiple directory services, and inconsistent authentication policies. Users had different credentials across systems, creating both security gaps and poor user experience.

3. **High-Risk Access Exposure:** Administrative access to core banking systems was protected by simple username/password combinations. There was no privileged access management, no session recording, and no multi-factor authentication. A compromised administrator account could potentially access all customer accounts.

4. **Compliance Documentation Gaps:** The regulatory examination identified missing access audit trails, absent access certification documentation, and no formal access recertification process. They couldn't demonstrate that access rights were appropriate and current.

5. **Customer Account Takeover Risk:** Online banking lacked multi-factor authentication, making customer accounts vulnerable to credential stuffing and phishing attacks. OmniBank had experienced a 340% increase in account takeover attempts over the past year.

The fundamental question: How do you redesign authentication and access control across a fragmented banking environment under strict regulatory scrutiny, without disrupting banking operations for 1.2 million customers?

---

## 4. Scope of Work

### Assessment Boundaries

**In Scope:**
- Authentication systems (web banking, mobile banking, administrative access)
- Identity and access management infrastructure (Active Directory, AWS IAM)
- Core banking system access controls (Temenos T24, two legacy systems)
- Privileged access management
- Access governance and certification processes
- Digital banking infrastructure (web, mobile, API)
- Third-party vendor access (banking partners, service providers)
- Regulatory compliance requirements (OCC, FDIC, state banking)

**Out of Scope:**
- Physical security systems
- ATM network security
- Card payment processing (separate PCI DSS assessment)
- Core banking application code review
- Social engineering testing

### Regulatory Framework

| Regulation | Requirements | Status |
|------------|-------------|--------|
| OCC Bulletin 2013-29 | Vendor risk management, access controls | Deficient |
| FFIEC Authentication Guidance | Multi-factor authentication, risk assessments | Non-compliant |
| GLBA (Gramm-Leach-Bliley Act) | Safeguards rule, access controls | Partially compliant |
| SOX Section 302/404 | IT general controls, access governance | Deficient |

### Timeline

| Phase | Duration | Activities |
|-------|----------|------------|
| Assessment | Weeks 1-3 | Current state analysis, gap assessment, risk prioritization |
| Architecture Design | Weeks 4-6 | Zero-trust identity architecture, MFA deployment design |
| Implementation | Weeks 7-10 | Authentication upgrades, PAM deployment, governance automation |
| Validation | Weeks 11-12 | Penetration testing, compliance validation, regulatory prep |

---

## 5. Methodology Deep Dive

### Phase 1: Current State Assessment

We began with comprehensive assessment of OmniBank's identity infrastructure:

**Identity Infrastructure Discovery:**
- 3 separate Active Directory forests (legacy acquisitions)
- 1,200+ Active Directory accounts with privileged access
- 340,000 online banking accounts
- 180,000 mobile banking users
- 85 third-party vendor accounts with system access
- 23 high-privilege application accounts

**Authentication System Audit:**

**Current State Analysis:**
| System | Authentication Method | Risk Level |
|--------|---------------------|------------|
| Web Banking | Username + password only | Critical |
| Mobile Banking | Username + password only | Critical |
| VPN | Username + password, no MFA | High |
| Active Directory | NTLM/v1, weak password policy | High |
| Core Banking (Temenos) | Shared admin accounts | Critical |
| AWS Console | IAM users, no MFA enforcement | High |
| Third-party access | Shared credentials | Critical |

**Regulatory Gap Analysis:**
| Requirement | Current Status | Gap Severity |
|-------------|----------------|-------------|
| MFA for administrative access | Not implemented | Critical |
| Risk-based authentication | Not implemented | High |
| Access logging and monitoring | Incomplete | High |
| Access certification process | Manual, incomplete | High |
| Privileged access management | None | Critical |
| Vendor access controls | None | Critical |

### Phase 2: Zero-Trust Identity Architecture Design

Based on our assessment, we designed a zero-trust identity architecture:

**Core Principles:**
1. **Verify Explicitly:** Authenticate and authorize based on all available data points — identity, location, device health, service or workload, data classification, and anomalies.

2. **Use Least-Privilege Access:** Limit user access with just-enough, just-in-time (JIT) access — minimize blast radius and credential exposure.

3. **Assume Breach:** Minimize trust in the network perimeter. Verify end-to-end encryption. Inspect and log all traffic.

**Architecture Components:**

**Identity Provider (IdP):**
- Deploy Okta as centralized identity provider
- Integrate all applications via SAML/OIDC
- Implement adaptive MFA policies
- Centralize access governance

**Privileged Access Management (PAM):**
- Deploy CyberArk PAM solution
- Implement vaulting for privileged credentials
- Session recording for administrative access
- JIT access for core banking systems

**Access Governance:**
- Automated access certification campaigns
- Role-based access control (RBAC) for core banking
- Continuous access monitoring
- Anomaly detection and alerting

### Phase 3: Authentication System Implementation

We implemented authentication upgrades across all channels:

**Web Banking MFA Deployment:**
- Implemented Okta Adaptive MFA for all web banking users
- Factors: Push notification (Okta Verify), TOTP, SMS fallback
- Risk-based authentication: Step-up for sensitive transactions
- Phishing-resistant FIDO2 support for high-risk users

**Mobile Banking Security Upgrade:**
- Integrated Okta Mobile SDK
- Biometric authentication (Face ID, fingerprint)
- Device attestation for risk scoring
- Certificate pinning for API communication

**Administrative Access Hardening:**
- Privileged access management for all admin accounts
- Just-in-time access requests via ServiceNow
- Session recording for core banking access
- Break-glass procedures for emergency access
- Phishing-resistant MFA (FIDO2 hardware keys for Tier 1 admins)

**Active Directory Security:**
- Disabled NTLM v1/v2, LM hash
- Implemented LDAP signing and channel binding
- Strong password policy (14+ characters, complexity, no reuse)
- Password hash protection
- Tiered admin model (Tier 0, 1, 2)

### Phase 4: Access Governance Implementation

**Role-Based Access Control (RBAC):**
- Mapped all core banking functions to roles
- Created 847 discrete roles covering all business functions
- Implemented role assignment workflow with manager approval
- Quarterly access certification campaigns

**Access Certification Automation:**
- Automated quarterly certification campaigns via Saviynt
- Manager certification for business users
- IT certification for privileged access
- Segregation of duties conflict detection
- Remediation workflow for violations

**Audit Logging Enhancements:**
- Centralized log collection (Splunk)
- 90-day hot storage, 7-year cold storage
- Real-time alerting for privileged access
- Customer data access logging
- Regulatory report templates (OCC, FDIC, state)

### Phase 5: Third-Party Access Management

**Vendor Access Program:**
- All vendor accounts moved to CyberArk PAM
- Just-in-time access with time-bounded sessions
- Session recording for all vendor access
- Monthly vendor access reviews
- Termination procedures with automated deprovisioning

---

## 6. Key Findings

### Critical Deficiencies (8)

**CD001: No Multi-Factor Authentication for Online Banking**
- Location: Web banking platform (340,000 users)
- Risk: Account takeover via credential theft
- Impact: Customer financial data exposure, fraud losses
- Status: Fixed (MFA deployed to 100% of users)

**CD002: Shared Administrative Accounts for Core Banking**
- Location: Temenos T24 admin accounts
- Risk: No accountability, credential sharing
- Impact: Unauditable privileged access
- Status: Fixed (individual accounts + PAM)

**CD003: No Privileged Access Management**
- Location: All administrative access
- Risk: Uncontrolled privileged credentials
- Impact: Potential for insider threat, credential theft
- Status: Fixed (CyberArk PAM deployed)

**CD004: Inadequate Access Logging**
- Location: Core banking systems, Active Directory
- Risk: No audit trail for access reviews
- Impact: Regulatory non-compliance
- Status: Fixed (centralized logging deployed)

**CD005: No Formal Access Certification Process**
- Location: All systems
- Risk: Accumulation of unnecessary access
- Impact: Principle of least privilege not enforced
- Status: Fixed (automated quarterly certifications)

**CD006: Third-Party Access Unmonitored**
- Location: 85 vendor accounts
- Risk: No visibility into vendor activity
- Impact: Vendor breach risk, compliance gaps
- Status: Fixed (PAM vaulting + monitoring)

**CD007: Weak Password Policy**
- Location: Active Directory, web banking
- Risk: Susceptible to brute force, credential stuffing
- Impact: Account compromise
- Status: Fixed (14-char minimum, complexity, lockout)

**CD008: No Risk-Based Authentication**
- Location: All customer-facing channels
- Risk: Inability to detect anomalous access
- Impact: Fraud, account takeover
- Status: Fixed (adaptive MFA deployed)

### High Deficiencies (14)

**HD001-HD008: Missing Security Headers**
- Web banking missing HSTS, CSP, X-Frame-Options
- Status: Fixed

**HD009-HD012: No Session Timeout Enforcement**
- Idle sessions not terminated
- Status: Fixed (15-minute idle timeout)

**HD013-HD014: Inadequate API Security**
- API authentication using basic auth
- Status: Fixed (OAuth 2.0 + mTLS)

---

## 7. Remediation Strategy

### Immediate Fixes (Within 30 Days)

These 8 critical deficiencies required emergency remediation to address regulatory concerns:

1. **Online Banking MFA:**
   - Deploy Okta Adaptive MFA to web banking
   - Push notifications for all users
   - Rollout campaign: 2 weeks for admin, 4 weeks for all users
   - Time: 4 weeks

2. **Privileged Access Management:**
   - Deploy CyberArk PAM in emergency mode
   - Vault all privileged credentials
   - Implement session recording
   - Time: 3 weeks

3. **Administrative Account Individualization:**
   - Create individual admin accounts for all users
   - Migrate from shared accounts
   - Implement PAM for all admin access
   - Time: 2 weeks

4. **Access Logging:**
   - Deploy Splunk for centralized logging
   - Configure logging for all critical systems
   - Implement alerting for privileged access
   - Time: 3 weeks

### Short-Term Improvements (30-90 Days)

**Identity Infrastructure:**
- Deploy Okta as centralized IdP
- Migrate all applications to Okta SSO
- Implement RBAC for core banking
- Deploy access certification automation (Saviynt)

**Authentication Hardening:**
- Implement adaptive MFA policies
- Deploy risk-based authentication
- Enable biometric authentication for mobile
- Implement FIDO2 for high-risk users

**Active Directory Hardening:**
- Disable NTLM v1/v2
- Implement tiered admin model
- Deploy password hash protection
- Enable LDAP signing and channel binding

### Medium-Term Enhancements (90-180 Days)

**Zero-Trust Architecture:**
- Implement device trust assessment
- Deploy network segmentation
- Implement application access policies
- Deploy user behavior analytics

**Continuous Monitoring:**
- 24/7 access monitoring
- Anomaly detection and alerting
- Automated compliance reporting
- Real-time fraud detection

---

## 8. Implementation Support

We didn't just assess and design. Our team remained engaged throughout implementation:

### Weekly Status Calls (12 sessions)
- Implementation progress review
- Blockers addressed in real-time
- Risk mitigation planning

### Design Workshops (4 half-days)
- RBAC role design workshops
- PAM workflow design
- Access certification process design
- Regulatory reporting requirements

### Implementation Hands-On Support
- Okta configuration and integration
- CyberArk PAM deployment
- Splunk logging configuration
- Saviynt access certification setup

### Regulatory Preparation
- Examination document preparation
- Mock examination interview preparation
- Remediation evidence documentation
- Examiner presentation rehearsal

### Training (24 hours)
- Privileged access management training (IT admins)
- Access certification training (managers)
- Security awareness training (all employees)
- Regulatory compliance training (compliance team)

---

## 9. Results and Outcomes

### Regulatory Compliance Achievement

| Requirement | Before | After |
|-------------|--------|-------|
| OCC Bulletin 2013-29 | Deficient | Compliant |
| FFIEC Authentication Guidance | Non-compliant | Compliant |
| GLBA Safeguards Rule | Partially compliant | Fully compliant |
| SOX IT Controls | Deficient | Compliant |

### Security Control Improvements

| Control | Before | After |
|---------|--------|-------|
| Administrative accounts with MFA | 0% | 100% |
| Privileged access managed | 0% | 100% |
| Online banking users with MFA | 0% | 100% |
| Access certifications automated | 0% | 100% (quarterly) |
| Access logging complete | 40% | 100% |
| Third-party access managed | 0% | 100% |

### Account Takeover Reduction

| Metric | Before | After |
|--------|--------|-------|
| Account takeover attempts/month | 2,340 | 89 |
| Successful account takeovers/month | 47 | 1 |
| Fraud losses/month | $180,000 | $4,200 |
| Customer reported phishing | 340/month | 23/month |

### Operational Improvements

- **Access Provisioning Time:** 5 days → 4 hours (automated)
- **Access Certification Time:** 6 weeks → 1 week (automated)
- **Privileged Access Requests:** 24 hours → 15 minutes (JIT)
- **Regulatory Report Generation:** 2 weeks → 2 hours (automated)
- **Security Incident Response:** 72 hours → 4 hours

---

## 10. Technical Deep Dive: Zero-Trust Banking Architecture

Understanding how we approached the zero-trust redesign for OmniBank:

### The Challenge with Traditional Banking Security

Traditional bank security relied on network perimeter defense:
- Hard external network, trusted internal network
- Single sign-on across systems with shared credentials
- Broad privileged access granted to administrators
- Limited logging and monitoring

This model fails when:
- Network boundaries are penetrated (phishing, insider threat)
- Credentials are compromised (reuse, phishing)
- Insider threats exist (employees, vendors)
- Regulatory examiners demand proof of access control

### Our Zero-Trust Approach

We implemented a zero-trust model based on three principles:

**1. Verify Explicitly:**
Every access request is authenticated and authorized based on:
- User identity (who)
- Device health (what device)
- Location (where)
- Time (when)
- Risk score (how)

Implementation:
- Okta for identity verification
- CrowdStrike for device health
- Risk-based authentication policies
- Continuous validation

**2. Use Least-Privilege Access:**
Access is granted just-in-time, just-enough:
- Privileged access via CyberArk PAM
- Time-bounded sessions
- Role-based access for core banking
- Segregation of duties enforcement

Implementation:
- RBAC with 847 discrete roles
- JIT access requests via ServiceNow
- Break-glass procedures for emergencies
- Automated deprovisioning

**3. Assume Breach:**
Trust nothing, verify everything:
- End-to-end encryption for all communications
- Session recording for privileged access
- Comprehensive logging and monitoring
- Anomaly detection and alerting

Implementation:
- Splunk for centralized logging
- 90-day hot storage, 7-year cold storage
- Real-time alerting for anomalous access
- User behavior analytics

### Banking-Specific Considerations

**Core Banking Systems:**
- Temenos T24 requires special handling (vendor lock-in)
- Implemented PAM with credential vaulting
- Session recording for all admin access
- Individual accountability via PAM

**Regulatory Requirements:**
- OCC, FDIC, state banking examiners require specific controls
- Implemented access certification with examiner-ready reports
- Automated evidence collection for examinations
- Remediation tracking visible to regulators

**Customer Experience:**
- MFA rollout without disrupting banking operations
- Adaptive authentication based on risk
- Biometric authentication for mobile (convenient + secure)
- Clear communication to customers about security changes

---

## 11. Lessons Learned

### What OmniBank Did Well

1. **Executive commitment:** The CEO and Board personally engaged on regulatory risk. This drove resources and prioritization.

2. **Cross-functional collaboration:** IT, compliance, legal, and business lines all participated. Identity and access management isn't just an IT issue.

3. **Phased approach:** They didn't try to fix everything at once. They prioritized regulatory-critical items first, then built out.

4. **Vendor management:** They held vendors (Temenos, Okta, CyberArk) accountable for implementation timelines and quality.

### What Could Have Been Better

1. **Earlier identity governance:** Identity and access management had been on their roadmap for 3 years. Starting earlier would have avoided regulatory findings.

2. **Acquisition integration planning:** The fragmented identity infrastructure was a known issue from acquisitions. Better integration planning would have prevented it.

3. **Vendor access monitoring:** Third-party vendor access had been a known risk. Better vendor management would have caught gaps earlier.

4. **Access certification automation:** Manual access certifications had failed to keep up with growth. Earlier automation would have maintained compliance.

### Recommendations for Financial Institutions

1. **Identity is foundational:** In financial services, identity and access management isn't optional — it's regulatory required. Treat it as a core banking function.

2. **Multi-factor authentication everywhere:** FFIEC guidance is clear. Any system handling customer data needs MFA.

3. **Privileged access management is non-negotiable:** Administrative access to core banking systems is a prime target for attackers. Implement PAM before you have an incident.

4. **Automation is essential:** Manual processes don't scale. Automate access provisioning, certification, and deprovisioning.

5. **Regulatory examinations are opportunities:** Treat examination findings as a roadmap for improvement, not just compliance checkpoints.

---

## 12. Tools and Technologies Used

### Identity and Access Management

| Tool | Purpose | Implementation |
|------|---------|----------------|
| Okta | Identity provider | SSO, MFA, lifecycle management |
| CyberArk PAM | Privileged access management | Credential vaulting, session recording |
| Saviynt | Access governance | Certifications, RBAC, SoD |
| Microsoft AD | Legacy identity | Hardening, tiered model |

### Security Monitoring

| Tool | Purpose | Implementation |
|------|---------|----------------|
| Splunk | SIEM | Centralized logging, alerting |
| CrowdStrike | Endpoint detection | Device health assessment |
| Palo Alto Networks | NGFW | Network segmentation |

### IT Service Management

| Tool | Purpose | Implementation |
|------|---------|----------------|
| ServiceNow | ITSM | Access request workflow |
| Jira | Issue tracking | Remediation tracking |

---

## 13. Team and Credentials

### Implementation Team

**Lead IAM Architect:** 15 years IAM experience, CISSP, CISM
- Specialty: Financial services IAM, regulatory compliance
- Previous clients: 5 top-20 US banks, major credit unions
- Led 30+ IAM transformations in financial services

**IAM Engineer #1:** 10 years identity management, Okta Certified
- Specialty: Okta deployment, MFA implementation
- Previous clients: Regional banks, credit unions

**IAM Engineer #2:** 8 years PAM, CyberArk Certified
- Specialty: CyberArk PAM deployment, privileged access
- Previous clients: Fortune 500 financial services

**IAM Engineer #3:** 6 years access governance, Saviynt Certified
- Specialty: RBAC design, access certification
- Previous clients: Banking, insurance

**Security Engineer:** 7 years SIEM, Splunk Certified
- Specialty: Splunk architecture, compliance reporting
- Previous clients: Financial services, healthcare

**Quality Review:** Partner-level review of all deliverables

### Certifications and Standards

- FFIEC Authentication Guidance
- OCC Bulletin 2013-29
- GLBA Safeguards Rule
- SOX IT General Controls
- NIST SP 800-63 (Authentication)
- NIST SP 800-53 (Access Controls)
- Zero Trust Architecture (NIST SP 800-207)

---

## 14. Compliance Mapping

### FFIEC Authentication Guidance Coverage

| Requirement | Implementation | Status |
|-------------|---------------|--------|
| Multi-factor authentication | Okta Adaptive MFA | Compliant |
| Risk-based authentication | Okta Risk Framework | Compliant |
| Multi-factor for admin access | CyberArk PAM + FIDO2 | Compliant |
| Access logging and monitoring | Splunk centralized logging | Compliant |
| Access certification | Saviynt automated campaigns | Compliant |
| Vendor access controls | CyberArk PAM vaulting | Compliant |

### OCC Security Controls

| Control | Status |
|---------|--------|
| Access management | Compliant |
| Privileged access management | Compliant |
| Authentication | Compliant |
| Audit logging | Compliant |
| Vendor management | Compliant |

---

## 15. Investment and ROI

### Engagement Cost

| Component | Cost |
|-----------|------|
| Assessment and design (6 weeks) | $65,000 |
| Implementation support (8 weeks) | $85,000 |
| Training (24 hours) | $15,000 |
| Regulatory preparation | $12,000 |
| Project management | $8,000 |
| **Total** | **$185,000** |

### Return on Investment

| Value Component | Amount |
|----------------|--------|
| Enforcement penalty avoidance | $12,000,000 |
| Fraud loss reduction (annual) | $2,112,000 |
| Operational efficiency gains | $340,000 |
| Regulatory examination cost reduction | $180,000 |
| **Year 1 Total Value** | **$14,632,000** |
| **ROI** | **79x** |

### Breach Cost Context

| Risk | Potential Impact |
|------|-----------------|
| OCC enforcement action | $1M - $50M per violation |
| Account takeover fraud | $180K/month (before), $4.2K/month (after) |
| Data breach notification | $50-$150 per record |
| Reputational damage | Customer attrition, deposit outflows |

---

*Case study prepared for portfolio use. Client identity and specific details used with permission. All findings and remediation details verified against OmniBank internal records and regulatory examination responses.*
