# Case Study: Meridian Health Penetration Test
## Red Team Assessment of Healthcare Platform

---

## 1. Executive Summary

Meridian Health, a digital health platform serving 1.2 million patients across 47 clinics, engaged us for a comprehensive penetration test following new HIPAA compliance requirements and a board mandate for annual offensive security testing. Over an 8-week engagement, our red team conducted external, internal, and social engineering assessments against their infrastructure, discovering 31 vulnerabilities including 2 critical severity issues that could have enabled complete network compromise and patient data exfiltration. We delivered detailed technical reports, an executive briefing, and remediation verification. The result: complete remediation of critical findings, improved security awareness company-wide, and successful HIPAA compliance attestation.

**Engagement Value:** $125,000 | **Timeline:** 8 weeks | **Team:** 6 operators

---

## 2. Client Profile

**Company:** Meridian Health  
**Industry:** Healthcare Technology  
**Size:** 340 employees, $28M ARR  
**Headquarters:** Denver, Colorado  
**Tech Stack:** Epic EMR integration, .NET (backend), React (patient portal), Microsoft SQL Server, Azure cloud infrastructure

**The Client's Situation:**  
Meridian Health had experienced a near-miss when an employee reported a phishing email that had successfully compromised one workstation before being contained. While no patient data was accessed, the incident revealed that their security awareness and technical controls were insufficient for their risk profile. Their CISO had recently joined from a Fortune 100 company and was implementing more rigorous security practices, including annual penetration testing as required by their cyber insurance policy.

**Pain Points:**
- Recent phishing incident created urgency
- Cyber insurance renewal required documented pen test
- HIPAA compliance audit in 4 months
- Siloed IT/security teams with limited communication
- Legacy systems coexisted with modern cloud infrastructure

---

## 3. The Problem

Meridian Health's leadership faced multiple converging pressures:

1. **Regulatory Compliance:** HIPAA required technical safeguards assessment, and their upcoming compliance audit needed documented security testing results.

2. **Cyber Insurance Renewal:** Their insurer required proof of annual penetration testing and specified minimum scope requirements.

3. **Board Mandate:** Following the phishing incident, the board had approved security budget but demanded measurable improvement demonstrated through testing.

4. **Internal Silos:** IT operations, security, and development teams had different priorities and limited coordination on security matters.

5. **Legacy Complexity:** Medical devices and legacy systems couldn't be patched regularly but were on the same network as modern systems.

The fundamental question: How vulnerable is Meridian Health to a real attacker, and where should they focus remediation resources?

---

## 4. Scope of Work

### Assessment Boundaries

**In Scope:**
- External network (public-facing infrastructure)
- Internal network (Azure-hosted systems)
- Patient portal (web application)
- Staff email and collaboration tools (Microsoft 365)
- VPN and remote access infrastructure
- Social engineering (phishing simulation)
- Physical security (external building access)

**Out of Scope:**
- Medical devices and clinical equipment
- Epic EMR core system (vendor-managed)
- Business associates (third-party connections)
- Denial of service testing

### Testing Types

| Test Type | Approach | Duration |
|-----------|----------|----------|
| External Network Assessment | Black box simulation of external attacker | 2 weeks |
| Internal Network Assessment | Assuming initial foothold via phishing | 2 weeks |
| Web Application Testing | Authenticated and unauthenticated testing | 1 week |
| Social Engineering | Phishing campaign + physical assessment | 2 weeks |
| Report and Remediation Support | Documentation and verification | 1 week |

### Timeline

| Phase | Duration | Activities |
|-------|----------|------------|
| Reconnaissance | Week 1 | OSINT, network mapping, target research |
| External Assessment | Weeks 2-3 | External network testing, VPN analysis |
| Internal Assessment | Weeks 3-4 | Internal network, assume breach scenario |
| Web Application Testing | Week 4-5 | Patient portal, staff applications |
| Social Engineering | Weeks 5-6 | Phishing simulation, physical testing |
| Reporting | Weeks 7-8 | Documentation, executive briefing |

---

## 5. Methodology Deep Dive

### Phase 1: Reconnaissance

We began with open-source intelligence gathering to understand Meridian Health's attack surface:

**Domain and DNS Analysis:**
- Identified 23 public IP ranges
- Discovered 47 subdomains including dev/staging environments exposed
- Found 12-year-old abandoned subdomains still pointing to active infrastructure

**Employee OSINT:**
- LinkedIn analysis: 340 employees identified across 6 departments
- Email pattern discovery: firstinitiallastname@meridianhealth.com
- Public presentations and job postings revealed internal system names

**Leaked Credential Hunting:**
- 3 compromised credentials found in breach databases
- None still active, but demonstrated employee password hygiene issues

**Technology Fingerprinting:**
- Cloud infrastructure: Azure US West region confirmed
- Email: Microsoft 365 confirmed
- Web technologies: ASP.NET, React, jQuery identified

### Phase 2: External Network Assessment

Our external testing simulated a dedicated attacker with no internal access:

**Vulnerability Scanning:**
- Nessus scan identified 156 vulnerabilities across external-facing systems
- 23 critical/high severity findings
- Notable: Unpatched Exchange server (CVE-2021-26855 - ProxyLogon)

**VPN Analysis:**
- Fortinet VPN with outdated firmware
- Password-based authentication (no MFA)
- 12 user accounts with weak passwords identified via OSINT

**Web Application Discovery:**
- Staging environment accessible at staging.meridianhealth.com
- Development API at api-dev.meridianhealth.com
- SSL/TLS configuration issues on 3 applications

**Key Finding: Development Environment Access:**
The staging environment used default credentials (admin/admin123) and contained a fully functional copy of the patient portal with anonymized but realistic patient data. This provided a beachhead for further testing.

### Phase 3: Internal Network Assessment

We conducted internal testing assuming an attacker had gained initial access via phishing:

**Initial Access Simulation:**
- Compromised a workstation via simulated phishing payload
- Used C2 framework to establish persistence
- Began lateral movement analysis

**Active Directory Analysis:**
- 4,200 objects in AD including users, computers, and groups
- 12 privileged accounts with excessive permissions
- Password policy: minimum 8 characters, no complexity requirements
- 47 accounts with "Do Not Expire" password flag

**Lateral Movement:**
- Service accounts with plaintext password storage in memory
- Pass-the-hash viable across 80% of workstations
- Domain admin session available from 14 non-admin workstations

**Key Finding: Domain Admin Accessible:**
Using Kerberoasting techniques, we extracted and cracked TGS tickets for service accounts. One account had Domain Admin privileges and a weak password. Total time from initial foothold to Domain Admin: 4 hours.

**Key Finding: Database Access:**
The SQL Server admin used the same password across development and production. Production database containing patient records was accessible with administrative credentials.

### Phase 4: Web Application Testing

**Patient Portal Assessment:**
- Unauthenticated scanning with Burp Suite
- Authenticated testing with test patient account
- 8 vulnerabilities identified

**Critical Finding: Patient Data Enumeration:**
The patient portal's appointment lookup feature accepted sequential MRN (Medical Record Numbers) without rate limiting or validation. An attacker could enumerate all patient MRNs and access:
- Patient names
- Appointment history
- Provider names
- Partial diagnosis information

**Other Findings:**
- IDOR in prescription refill feature
- CSRF on profile update
- Weak session token generation
- No account lockout on failed logins

### Phase 5: Social Engineering

**Phishing Campaign:**
We designed a targeted phishing campaign using the "Security Alert" theme:

**Campaign Setup:**
- Crafted emails mimicking IT department communications
- Used Azure-hosted phishing landing page (HTTPS)
- Included brand logos and convincing language

**Targets:** 340 employees across all departments

**Results:**
- 127 clicks (37%)
- 89 form submissions (26%)
- 34 malware execution confirmations (10%)
- First credential captured: 12 minutes after launch

**Department Breakdown:**
| Department | Click Rate | Submission Rate | Executions |
|------------|------------|-----------------|------------|
| Clinical Staff | 42% | 31% | 14% |
| Administrative | 38% | 27% | 11% |
| IT/Technical | 28% | 18% | 4% |
| Executive | 45% | 38% | 8% |

**Physical Security Assessment:**
External building perimeter:
- Badge tailgating possible at main entrance
- Unlocked server room window (ground floor)
- Laptop with patient data left in conference room (overnight)

### Phase 6: Privilege Escalation and Persistence

From the initial phishing compromise:

**Lateral Movement Achievements:**
- 47 workstations compromised
- 12 servers accessed
- 4 database servers accessible
- Complete Active Directory database extracted

**Data Access Potential:**
- Patient records database: 1.2 million patient records
- Financial systems: billing and payment data
- HR systems: employee PII and benefits data

**Persistence Mechanisms:**
- 8 different persistence techniques demonstrated
- Modified existing services for backdoor access
- Created local administrator accounts
- Established C2 channels through legitimate Azure services

---

## 6. Key Findings

### Critical Severity (2)

**C-001: Domain Privilege Escalation via Kerberoasting**
- CVSS Score: 9.8
- Service account with Domain Admin privileges vulnerable to Kerberoasting
- Attacker with domain user access could become Domain Admin
- Impact: Complete Active Directory compromise

**C-002: Patient Data Enumeration in Portal**
- CVSS Score: 9.1
- Sequential MRN allowed enumeration of all patient records
- No rate limiting or access control
- Impact: Mass disclosure of patient health information

### High Severity (8)

- H001: Unpatched Exchange Server (ProxyLogon vulnerability)
- H002: VPN without multi-factor authentication
- H003: Default credentials on staging environment
- H004: SQL Server credentials reused across environments
- H005: Excessive Active Directory privileges
- H006: Weak password policy (8 char, no complexity)
- H007: Plaintext password storage in service accounts
- H008: No session timeout on patient portal

### Medium Severity (12)

- M001-M012: Including TLS misconfigurations, missing security headers, excessive log permissions, legacy protocols enabled

### Low Severity (9)

- L001-L009: Information disclosure, verbose error messages, outdated SSL certificates

---

## 7. Remediation Strategy

### Immediate Actions (Within 48 Hours)

These findings required emergency response:

1. **Reset all Domain Admin passwords**
   - Immediately expired and reset service account passwords
   - Implemented 20+ character complex passwords

2. **Patch or isolate Exchange Server**
   - Applied emergency patches
   - Implemented URL rewrite rules as temporary mitigation

3. **Enable MFA on VPN**
   - Azure MFA integration
   - Certificate-based authentication for medical devices

### Critical Fixes (Within 2 Weeks)

**Kerberoasting Mitigation:**
- Removed excessive privileges from service accounts
- Implemented Managed Service Accounts
- Enabled AES encryption for TGS tickets
- Added monitoring for Kerberoasting activity

**Patient Portal Hardening:**
- Implemented rate limiting on MRN lookup
- Added access validation and logging
- Implemented account lockout policies
- Added anomaly detection for unusual access patterns

### Short-Term Improvements (1-3 Months)

**Password Policy Overhaul:**
- Increased minimum length to 14 characters
- Enabled complexity requirements
- Implemented 90-day rotation for privileged accounts
- Enabled "Smart Password Lockout"

**AD Security Hardening:**
- Removed excessive group memberships
- Implemented Tiered Admin model
- Restricted admin logins to secure workstations
- Enabled Credential Guard

**Security Awareness Program:**
- Quarterly phishing simulations
- Security awareness training required for all staff
- Immediate notification process for suspicious emails
- Department-specific training based on simulation results

---

## 8. Implementation Support

### Emergency Response Workshop
- 4-hour session with IT and security teams
- Walked through each critical finding
- Developed incident response playbook
- Established communication protocols

### Remediation Tracking
- Weekly calls for 6 weeks
- JIRA integration for tracking
- Risk-based prioritization framework
- Escalation process for blockers

### Re-Testing
- Full re-test of critical and high findings
- Phishing campaign re-run to measure training effectiveness
- Verification of compensating controls

---

## 9. Results and Outcomes

### Vulnerability Resolution

| Severity | Initial | After 8 Weeks | After 16 Weeks |
|----------|---------|---------------|----------------|
| Critical | 2 | 0 | 0 |
| High | 8 | 1 | 0 |
| Medium | 12 | 3 | 1 |
| Low | 9 | 4 | 2 |

### Phishing Campaign Results (Before/After Training)

| Metric | Before Training | After Training | Improvement |
|--------|-----------------|----------------|--------------|
| Click rate | 37% | 12% | -68% |
| Submission rate | 26% | 4% | -85% |
| Malware executions | 10% | 1% | -90% |
| Time to report | 45 min avg | 8 min avg | -82% |

### Security Posture Improvement

| Metric | Before | After |
|--------|--------|-------|
| Time to Domain Admin (if compromised) | 4 hours | >1 month |
| Patient data exposure risk | Critical | Low |
| Phishing success rate | 37% | 12% |
| Patched critical vulnerabilities | 0% | 100% |
| MFA coverage | 15% | 94% |

### Compliance Outcomes
- HIPAA compliance audit: Passed
- Cyber insurance renewal: Approved
- Board security report: Positive assessment
- Joint Commission IT requirements: Satisfied

---

## 10. Technical Deep Dive: Kerberoasting Attack

### Understanding the Attack

Kerberoasting exploits a feature of Kerberos authentication: service accounts have Service Principal Names (SPNs), and users can request TGS (Ticket Granting Service) tickets for those SPNs. These tickets are encrypted with the service account's password hash.

If the password is weak or guessable, an attacker can:
1. Request TGS tickets for target service accounts
2. Extract them from memory or network traffic
3. Offline crack them using GPU acceleration

### What We Found at Meridian Health

Meridian Health used service accounts for automated processes. One account—svc_backup—had Domain Admin privileges (a misconfiguration from a 2019 migration). The account password was "Backup2019!"—meeting their 8-character minimum but easily crackable.

### Exploitation Steps

1. **Initial access:** Phishing gave us a domain user account
2. **Reconnaissance:** Found the svc_backup account SPN
3. **TGS Request:** Requested TGS ticket for svc_backup
4. **Extraction:** Extracted ticket from memory using Mimikatz
5. **Cracking:** GPU-based cracking broke the password in 3 hours
6. **Persistence:** Used service account to access Domain Admin

### The Fix

We recommended Managed Service Accounts (MSAs), which:
- Automatically rotate passwords
- Cannot use NTLM authentication
- Are managed by Active Directory

For the svc_backup account specifically:
- Removed Domain Admin privileges
- Created separate account for backup functions
- Implemented least-privilege access model

---

## 11. Lessons Learned

### What Meridian Did Well

1. **Employee reporting:** The original phishing incident was reported quickly—employees were already trained to be suspicious
2. **Incident response:** Initial containment was fast once the phishing was identified
3. **Executive buy-in:** Leadership supported security investments after the incident
4. **Documentation:** IT team maintained good asset inventory

### What Could Have Been Better

1. **Privilege management:** Service accounts had never been audited
2. **Patch management:** Legacy systems were exempted without compensating controls
3. **Network segmentation:** Medical devices and workstations on same network segment
4. **Password hygiene:** No password manager adoption, leading to weak password reuse

### Industry-Specific Insights

Healthcare organizations face unique challenges:
- Legacy medical devices cannot be patched
- Clinical workflows prioritize usability over security
- Staff phishing susceptibility is higher (stress, distraction)
- Data sensitivity requires more granular access controls

---

## 12. Tools and Technologies Used

### Reconnaissance

| Tool | Purpose | Key Findings |
|------|---------|--------------|
| Amass | Subdomain enumeration | 47 subdomains |
| theHarvester | Email and employee OSINT | 340 employee profiles |
| Hunter.io | Email pattern discovery | Validated email schema |
| LeakCheck | Credential breach checking | 3 exposed credentials |
| Shodan | Internet-facing asset analysis | 156 exposed services |

### External Testing

| Tool | Purpose | Key Findings |
|------|---------|--------------|
| Nessus Professional | Vulnerability scanning | 156 vulnerabilities |
| Burp Suite Professional | Web application testing | 12 web vulns |
| Nmap | Network mapping | 23 live hosts |
| CrackMapExec | Lateral movement | Domain admin access |
| Responder | LLMNR/NBT-NS poisoning | Credential capture |

### Internal Testing

| Tool | Purpose | Key Findings |
|------|---------|--------------|
| BloodHound | AD attack path analysis | Excessive privileges mapped |
| Mimikatz | Credential extraction | Plaintext passwords |
| Rubeus | Kerberoasting | svc_backup vulnerability |
| PowerSploit | Post-exploitation | 47 workstations accessed |
| CrackMapExec | Lateral movement | Pass-the-hash viable |

### Social Engineering

| Tool | Purpose | Key Findings |
|------|---------|--------------|
| Gophish | Phishing campaign | 127 clicks, 89 submissions |
| Evilginx2 | Credential harvesting | Session cookie theft |
| MetaSploit | Payload generation | 34 malware executions |
| lockpicking | Physical assessment | Badge tailgating, window access |

---

## 13. Team and Credentials

### Red Team

**Team Lead (Red Team Lead):** OSCP, OSCE, CRTE
- 14 years penetration testing experience
- Former US Army cyber operations
- Healthcare sector specialist

**Senior Operator #1:** OSCP, OSEP, CRTO
- 10 years experience
- Active Directory exploitation specialist
- Led 80+ red team engagements

**Senior Operator #2:** OSCP, CRTO
- 8 years experience
- External network assessment specialist
- Web application testing expert

**Operator #3:** eCPTX, PNPT
- 5 years experience
- Social engineering specialist
- Physical security assessments

**Operator #4:** OSCP
- 4 years experience
- Internal network testing
- PowerShell and C# development

**Consultant (Quality Review):** CISSP, CISM
- 18 years security experience
- HIPAA compliance specialist
- Executive briefing expertise

---

## 14. Compliance Mapping

### HIPAA Security Rule Coverage

| Standard | Assessment Coverage | Findings |
|----------|---------------------|----------|
| §164.308(a)(1) - Security Management | Addressable specifications assessed | C-002, H006 |
| §164.308(a)(3) - Workforce Security | Technical testing of access controls | C-001, H005, H007 |
| §164.308(a)(5) - Security Awareness | Phishing simulation results | Social eng. findings |
| §164.312(a) - Access Control | Technical testing of authentication | C-002, H008 |
| §164.312(b) - Audit Controls | Logging and monitoring gaps | M004, M007 |
| §164.312(e) - Transmission Security | TLS configuration issues | M001, M002 |

### NIST CSF Alignment

| Category | Subcategory | Findings |
|----------|-------------|----------|
| Protect (PR.AC) | Authentication | C-001, C-002, H002, H006 |
| Protect (PR.DS) | Data Security | H003, H004, H007 |
| Detect (DE.CM) | Networks, Email | Phishing findings |
| Respond (RS.AN) | Analysis | M004, M007 |

---

## 15. Investment and ROI

### Engagement Cost

| Component | Cost |
|-----------|------|
| Reconnaissance and OSINT | $12,000 |
| External network assessment | $18,000 |
| Internal network assessment | $32,000 |
| Web application testing | $18,000 |
| Social engineering | $25,000 |
| Reporting and briefing | $15,000 |
| Project management | $5,000 |
| **Total** | **$125,000** |

### Risk Reduction Value

| Risk | Potential Impact | Mitigation Value |
|------|------------------|------------------|
| Patient data breach | $4.75M (per 2023 IBM avg) | Breach avoided |
| HIPAA penalty | $1.5M per violation | Compliance achieved |
| Cyber insurance | Coverage denial risk | Renewal approved |
| Business disruption | $2.3M (healthcare avg) | Incident response improved |
| Reputational damage | Incalculable | Brand protected |

---

## 16. Testimonials and Feedback

### CISO, Meridian Health

> "This penetration test was eye-opening. We thought we had reasonable security, but seeing our own environment attacked—watching how quickly a single phishing email could lead to complete network compromise—changed how everyone at Meridian thinks about security. The team didn't just find vulnerabilities; they helped us understand how real attackers think. The remediation support was equally valuable. Eight weeks later, we're in a fundamentally different position."

### CEO, Meridian Health

> "Our board required documented security testing, and I expected a checklist exercise. Instead, we got a comprehensive assessment that exposed real gaps in our security posture. The team's ability to explain technical findings in business terms was impressive. We allocated additional budget for remediation immediately. The cyber insurance renewal was approved without pushback, and we passed our HIPAA audit. I'd recommend this approach to any healthcare organization serious about security."

---

## 17. Future Recommendations

### Immediate (0-3 Months)
1. Implement Just-in-Time admin access
2. Deploy network segmentation (micro-segmentation for medical devices)
3. Implement endpoint detection and response (EDR)
4. Enhance logging and SIEM integration

### Medium-Term (3-6 Months)
1. Privileged Access Workstation (PAW) deployment
2. Identity Threat Detection and Response (ITDR)
3. Zero Trust Architecture assessment
4. Medical device security program

### Long-Term (6-12 Months)
1. Full Zero Trust implementation
2. Security Orchestration and Automation (SOAR)
3. Continuous red teaming (adversary simulation)
4. Cyber insurance cyber range training

---

## 18. Re-Test Results

### Re-Test Scope
Four weeks after initial findings, we conducted re-testing of all critical and high findings.

### Results

| Finding ID | Original Severity | Status | Notes |
|------------|-------------------|--------|-------|
| C-001 | Critical | **Fixed** | MSAs implemented, monitoring enabled |
| C-002 | Critical | **Fixed** | Rate limiting, anomaly detection active |
| H001 | High | **Fixed** | Exchange fully patched |
| H002 | High | **Fixed** | MFA enforced on all VPN access |
| H003 | High | **Fixed** | Credentials rotated, monitoring added |
| H004 | High | **Fixed** | Environment separation implemented |
| H005 | High | **Partially Fixed** | Tiered admin in progress |
| H006 | High | **Fixed** | Password policy enforced |
| H007 | High | **Fixed** | LSA protection enabled |
| H008 | High | **Fixed** | Session timeout implemented |

### Phishing Re-Test Results

| Metric | Initial | Re-Test | Change |
|--------|---------|---------|--------|
| Click rate | 37% | 12% | -68% |
| Submission rate | 26% | 4% | -85% |
| Executions | 10% | 1% | -90% |

---

## 19. Appendix

### Indicators of Compromise (IOCs)
Full IOC list provided in accompanying `ioc-list.csv`

### Exploit Proof of Concept Scripts
Custom exploit code provided in `exploit-scripts/` (sanitized, educational purposes)

### Remediation Playbook
Detailed remediation procedures in `remediation-playbook.pdf`

### Attack Path Diagrams
BloodHound exports and attack path visualizations in `attack-paths/`

---

## 20. Contact and Next Steps

### Engage For Your Penetration Test

This case study demonstrates our red team approach: realistic attacks, comprehensive findings, and actionable remediation.

**Our Penetration Testing Services:**
- External network penetration testing
- Internal network assessments (assume breach)
- Web application security testing
- Social engineering (phishing, physical)
- Red team operations (full adversary simulation)

**Contact:**  
[Your Information]

---

*Case study prepared for Meridian Health engagement (Q4 2024). All company information used with permission. Specific vulnerabilities and techniques adapted for confidentiality.*
