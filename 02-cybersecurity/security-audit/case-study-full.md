# Case Study: NovaPay Security Audit
## Complete Web Application Security Assessment

---

## 1. Executive Summary

NovaPay, a Series B fintech startup processing $40M in monthly transactions, engaged us for a comprehensive web application security audit following a near-miss data incident involving a misconfigured API endpoint. Over a 6-week engagement, our team of four security engineers conducted a thorough assessment of their React/Node.js platform, uncovering 47 vulnerabilities including 3 critical severity issues that could have enabled account takeover and unauthorized transaction execution. We delivered a prioritized remediation roadmap, implemented automated security scanning in their CI/CD pipeline, and trained their development team on secure coding practices. The result: zero critical vulnerabilities at re-test, 94% of medium issues resolved, and a demonstrable shift in the company's security culture.

**Engagement Value:** $78,000 | **Timeline:** 6 weeks | **Team:** 4 engineers

---

## 2. Client Profile

**Company:** NovaPay  
**Industry:** Financial Technology (Payments Processing)  
**Size:** 85 employees, $12M ARR  
**Headquarters:** Austin, Texas  
**Tech Stack:** React (frontend), Node.js/Express (API), PostgreSQL (database), AWS (infrastructure)

**The Client's Situation:**  
NovaPay had experienced rapid growth, scaling from 50K to 500K users in 18 months. Their engineering team had grown from 8 to 32 developers, but security practices hadn't kept pace. A routine code review had uncovered an API endpoint that failed to validate user session tokens properly—a vulnerability that could have allowed any authenticated user to access any other user's transaction history. While caught before exploitation, this incident triggered investor concern and a mandatory security review as part of their Series C due diligence.

**Pain Points:**
- Security was reactive, not proactive
- No formal secure development lifecycle
- API endpoints had never been systematically tested
- Compliance requirements from enterprise customers were increasing
- Development team lacked security training

---

## 3. The Problem

Following the near-miss incident, NovaPay's leadership faced several urgent challenges:

1. **Investor Pressure:** Their Series C investors required proof of security maturity before closing, with a 90-day deadline.

2. **Enterprise Sales Blocked:** Three prospective enterprise clients had security questionnaires that NovaPay couldn't satisfy—particularly around API security and data protection practices.

3. **Technical Debt:** The engineering team had taken shortcuts to meet product deadlines, and no one had a complete picture of the attack surface.

4. **Team Morale:** Developers were anxious about security and needed guidance, not blame. Leadership wanted to turn security into an enabler, not a blocker.

5. **Regulatory Exposure:** As a payments company handling card data, NovaPay needed PCI DSS compliance. A breach could result in fines exceeding $500K and loss of payment processing privileges.

The fundamental question: Where were the real vulnerabilities, and how should they be fixed in a prioritized, efficient manner that wouldn't block product development?

---

## 4. Scope of Work

### Assessment Boundaries

**In Scope:**
- Public-facing web application (app.novapay.io)
- Mobile API (REST endpoints, /api/v1/* and /api/v2/*)
- Authentication and session management systems
- Payment processing integration (Stripe)
- User dashboard and reporting features
- Internal admin portal (limited to security assessment)
- CI/CD pipeline security

**Out of Scope:**
- Physical security assessment
- Social engineering testing (phishing, pretexting)
- Denial of service testing
- Third-party vendor security (Stripe, AWS)
- Source code review of proprietary ML fraud detection algorithms

### Assessment Methodology

We employed a hybrid assessment approach combining:

1. **Automated Scanning:** OWASP ZAP, Burp Suite Professional, and Snyk for static/dynamic analysis
2. **Manual API Testing:** Custom scripts targeting their REST endpoints, including authentication bypass and IDOR scenarios
3. **Source Code Review:** Manual review of authentication modules, payment handling, and data access layers
4. **Architecture Review:** Evaluation of security controls, encryption implementation, and access control models

### Timeline

| Phase | Duration | Activities |
|-------|----------|------------|
| Discovery | Week 1 | Scope finalization, access provisioning, automated scanning setup |
| Manual Testing | Weeks 2-3 | API security testing, authentication analysis, business logic flaws |
| Code Review | Week 3-4 | Deep-dive into critical code paths, secure code review |
| Reporting | Week 5 | Vulnerability documentation, risk rating, remediation guidance |
| Remediation Support | Week 6 | Developer training, prioritization workshop, re-test planning |

---

## 5. Methodology Deep Dive

### Phase 1: Reconnaissance and Mapping

We began with comprehensive asset discovery to understand NovaPay's attack surface:

- **API Fingerprinting:** Identified 127 distinct API endpoints across v1 and v2
- **Authentication Mapping:** Documented 4 different authentication mechanisms across different system components
- **Data Flow Analysis:** Traced how user credentials, session tokens, and payment data moved through the system

A critical finding emerged immediately: NovaPay's API used three different token validation approaches depending on the endpoint—a recipe for inconsistency and bypass.

### Phase 2: Automated Vulnerability Scanning

We ran three parallel scanning tracks:

**OWASP ZAP (DAST):**
- Baseline scan: 12 medium findings, 3 high findings
- Full AJAX scan: Identified 2 additional endpoints not discovered in initial crawl
- API scan: Found 8 parameter tampering possibilities

**Burp Suite Professional:**
- Active scanning: 23 findings, including 4 critical
- Sequencer: Session token randomness issues detected
- Intruder: Mass enumeration attacks possible on certain endpoints

**Snyk (SCA + SAST):**
- 156 dependency vulnerabilities identified
- 12 with known exploits
- 3 critical severity

### Phase 3: Manual API Security Testing

This is where we found the most critical issues. Our manual testing uncovered:

**Authentication Bypass in /api/v1/users/profile:**
- The endpoint retrieved user profile data using a user_id parameter from the request body, but failed to validate that this ID matched the authenticated session
- Any logged-in user could fetch any other user's full profile, including email, phone, and partial payment card numbers

**JWT Validation Weakness:**
- The system accepted the "none" algorithm in JWT tokens
- Tokens signed with HS256 could be forged if the secret key was brute-forced (we confirmed it wasn't, but the algorithm should be RS256)

**Broken Rate Limiting:**
- Login endpoint had rate limiting by IP, but the API gateway forwarded X-Forwarded-For headers without validation
- Attackers could bypass rate limiting by spoofing IP addresses

**IDOR in Transaction History:**
- GET /api/v2/transactions/{transaction_id} returned transaction details including merchant name, amount, and card last 4 digits
- No ownership validation—any user could access any transaction by guessing IDs

### Phase 4: Source Code Review

Access to the codebase revealed additional issues invisible to external testing:

**Payment Card Data Handling:**
- Full card numbers were being logged in plaintext to application logs
- PCI scope was unnecessarily broad—decryption should happen in a separate tokenization service

**Session Management:**
- Sessions were not invalidated on password change
- Concurrent session limits were not enforced
- Idle timeout was 24 hours (far too long for a financial application)

**Secret Management:**
- AWS API keys stored in environment variables in code
- Database passwords in plaintext config files
- No secrets management solution (HashiCorp Vault recommended)

### Phase 5: Threat Modeling

We conducted a half-day threat modeling session with NovaPay's engineering leads, using STRIDE methodology to identify attack scenarios:

| Threat Category | Scenario | Impact |
|-----------------|----------|--------|
| Spoofing | JWT forgery via algorithm confusion | Account takeover |
| Tampering | Parameter pollution in transaction API | Unauthorized transactions |
| Repudiation | Lack of audit logging for admin actions | Compliance failure |
| Information Disclosure | IDOR in transaction history | Data breach |
| Denial of Service | API rate limit bypass | Service unavailability |
| Elevation of Privilege | Privilege escalation in admin portal | Full system access |

---

## 6. Key Findings

### Critical Severity (3)

**CVE-CANDIDATE-001: Authentication Bypass via Parameter Tampering**
- Location: /api/v1/users/profile
- CVSS Score: 9.4 (Critical)
- An attacker with a valid account could access any user's full profile, including partial payment card data
- Status at re-test: **Fixed**

**CVE-CANDIDATE-002: JWT Algorithm Confusion**
- Location: Authentication middleware
- CVSS Score: 8.6 (Critical)
- System accepted "none" algorithm in JWT, enabling token forgery
- Status at re-test: **Fixed**

**CVE-CANDIDATE-003: Arbitrary Transaction Access**
- Location: /api/v2/transactions/{id}
- CVSS Score: 8.2 (Critical)
- Insecure Direct Object Reference allowed access to any transaction via ID enumeration
- Status at re-test: **Fixed**

### High Severity (7)

- H001: Missing rate limiting on sensitive endpoints
- H002: Insufficient session timeout configuration
- H003: Card data logged in plaintext
- H004: Missing security headers (X-Frame-Options, CSP)
- H005: Credential enumeration possible on login
- H006: Password reset token entropy too low
- H007: Admin portal accessible from same authentication as user portal

### Medium Severity (18)

- M001-M018: Including CSRF on state-changing operations, missing input validation,敞開XML external entity (XXE) in document upload, inadequate error messages

### Low Severity (19)

- L001-L019: Information disclosure via debug endpoints, missing HTTP security headers, weak password policy notifications

---

## 7. Remediation Strategy

### Immediate Fixes (Within 2 Weeks)

These three critical issues required emergency treatment:

1. **Authentication Bypass Fix:**
   - Implement session-to-user binding validation
   - Add authorization checks to all data retrieval endpoints
   - Deploy fix: within 48 hours

2. **JWT Hardening:**
   - Remove "none" algorithm support
   - Migrate from HS256 to RS256
   - Implement token expiration validation
   - Deploy fix: within 72 hours

3. **Transaction Access Control:**
   - Add ownership validation to all transaction endpoints
   - Implement UUID-based transaction IDs to prevent enumeration
   - Deploy fix: within 1 week

### Short-Term Improvements (2-6 Weeks)

**API Security:**
- Implement consistent authentication middleware across all endpoints
- Add rate limiting with proper IP validation (trust X-Real-IP header only from load balancer)
- Deploy request validation middleware (Joi/schema validation)

**Session Management:**
- Reduce session timeout to 30 minutes of inactivity
- Implement concurrent session limits (max 3 simultaneous)
- Add session invalidation on password change

**Logging and Monitoring:**
- Remove card data from all application logs
- Implement centralized log management (ELK stack)
- Add alert thresholds for anomalous API behavior

### Medium-Term Enhancements (6-12 Weeks)

- Implement secrets management (HashiCorp Vault)
- Deploy Web Application Firewall (AWS WAF)
- Establish security champion program within engineering
- Conduct developer security training

---

## 8. Implementation Support

We didn't just hand over a report and disappear. Our team remained engaged during the remediation phase:

### Weekly Status Calls (4 sessions)
- Review progress on remediation items
- Prioritize blockers
- Adjust timeline based on development capacity

### Developer Training (8 hours)
- Secure coding workshop for all 32 engineers
- Top 10 API security vulnerabilities (OWASP)
- Secure authentication patterns
- PCI DSS fundamentals

### Code Review Support
- Security review of all remediation code changes
- Approval gate before production deployment

### Re-Testing
- Full re-scan of all critical and high findings
- Verification of fixes
- Final security assessment report

---

## 9. Results and Outcomes

### Vulnerability Resolution

| Severity | Initial Count | After 6 Weeks | After 12 Weeks |
|----------|---------------|---------------|----------------|
| Critical | 3 | 0 | 0 |
| High | 7 | 2 | 0 |
| Medium | 18 | 6 | 1 |
| Low | 19 | 8 | 3 |

### Security Posture Improvement

**Before Engagement:**
- No formal vulnerability assessment on record
- Security incidents handled reactively
- Enterprise security questionnaires went unanswered
- Engineering team avoided security discussions

**After Engagement:**
- Zero critical vulnerabilities
- 89% of high/medium issues resolved
- Completed enterprise security questionnaires for 3 prospects
- Engineering team actively requesting security reviews
- Security champion nominated in each squad

### Compliance Impact
- PCI DSS gap assessment completed
- Ready for PCI DSS Level 4 compliance attestation (previously out of scope)
- Enterprise customer security questionnaires satisfied

### Business Outcomes
- Series C closed successfully ($18M raised)
- Enterprise deal with HealthCare Inc. unlocked ($2.4M ARR potential)
- Zero security incidents in 12 months post-engagement
- Developer productivity improved—security no longer a blocker

---

## 10. Technical Deep Dive: Critical Authentication Bypass

Understanding how the authentication bypass worked is instructive for understanding the broader pattern of issues found:

### The Vulnerability

The user profile endpoint (`GET /api/v1/users/profile`) was designed to return the profile of the currently authenticated user. The authentication middleware correctly validated the JWT token and extracted the user ID. However, the endpoint accepted an optional `user_id` query parameter:

```
GET /api/v1/users/profile?user_id=12345
Authorization: Bearer <jwt_token_for_user_67890>
```

If `user_id` was provided, the endpoint used it directly instead of the authenticated user's ID. The authentication middleware ran first, establishing the user's identity, but the profile endpoint ignored this and used the parameter value.

### The Exploit

A malicious user (user 67890) could request:
```
GET /api/v1/users/profile?user_id=12345
Authorization: Bearer <jwt_token_for_user_67890>
```

And receive user 12345's profile, including:
- Full name, email, phone number
- Date of birth
- Last 4 digits of payment card
- Billing address

### The Fix

We recommended a simple defense-in-depth approach:

1. **Remove the parameter entirely:** The endpoint should only return the authenticated user's profile
2. **Add explicit authorization checks:** Even if a user_id parameter exists, validate it matches the authenticated session
3. **Input validation:** If user_id is provided but doesn't match, return 403 Forbidden, not the wrong user's data
4. **Audit logging:** Log all profile access with both the accessor and the accessed user IDs

NovaPay implemented all four recommendations, and the fix was deployed within 48 hours.

---

## 11. Lessons Learned

### What NovaPay Did Well

1. **Caught the issue internally:** Their code review process, while informal, had improved enough to catch the near-miss
2. **Responded quickly:** Once leadership understood the risk, they moved decisively
3. **Invested in training:** Sending all engineers to security training signaled that security was everyone's responsibility
4. **Maintained momentum:** Unlike many companies, they didn't let remediation slide after the initial urgency faded

### What Could Have Been Better

1. **Earlier engagement:** A security audit before hitting 500K users would have been cheaper and less risky
2. **Threat modeling earlier:** Their architecture had evolved without formal threat assessment
3. **Secrets management:** Should have implemented Vault at Series A, not as a remediation item
4. **API governance:** No central ownership of API security meant different teams implemented auth differently

### Recommendations for Other Startups

1. **Treat security debt like technical debt:** Track it, prioritize it, pay it down
2. **Security champions:** Identify one engineer per team who owns security for that domain
3. **Automated scanning in CI/CD:** Catch vulnerabilities before they reach production
4. **Security questionnaires as a forcing function:** Use enterprise customer requirements to justify security investments

---

## 12. Tools and Technologies Used

### Vulnerability Assessment

| Tool | Purpose | Key Findings |
|------|---------|--------------|
| Burp Suite Professional | Web proxy, active scanning, API testing | 23 vulnerabilities |
| OWASP ZAP | Automated DAST scanning | 15 vulnerabilities |
| Snyk | Software composition analysis | 156 dependency issues |
| Nuclei | Custom vulnerability templates | 8 infrastructure issues |
| Postman | API endpoint testing | Authentication bypasses |

### Code Review

| Tool | Purpose | Key Findings |
|------|---------|--------------|
| GitHub Advanced Security | SAST, secret scanning | 12 code-level issues |
| Semgrep | Custom security rules | 8 pattern matches |
| GitGuardian | Secret detection | 4 exposed credentials |
| SonarQube | Code quality and security | 23 issues |

### Infrastructure Assessment

| Tool | Purpose | Key Findings |
|------|---------|--------------|
| Prowler | AWS security benchmarking | 15 AWS misconfigurations |
| ScoutSuite | Multi-cloud assessment | 12 findings |
| AWS Config | Compliance rules | 8 non-compliant resources |

---

## 13. Team and Credentials

### Assessment Team

**Lead Security Engineer:** 12 years experience, OSCP, CEH
- Specialty: Web application security, API testing
- Previous clients: Fortune 500 financial services, major healthcare providers

**Security Engineer #2:** 8 years experience, GWAPT
- Specialty: Authentication systems, session management
- Previous clients: E-commerce platforms, SaaS companies

**Security Engineer #3:** 5 years experience, eCPTX
- Specialty: Infrastructure security, cloud (AWS/GCP)
- Previous clients: Startups, media companies

**Security Consultant (Lead):** 15 years experience, CISSP, CISM
- Specialty: Security program development, compliance
- Role: Quality review, executive liaison

### Certifications and Standards

- OWASP Testing Guide v4.2
- NIST Cybersecurity Framework
- PCI DSS Requirements and Security Assessment Procedures
- ISO/IEC 27001:2013 (selected controls)

---

## 14. Compliance Mapping

### OWASP Top 10 2021 Coverage

| OWASP Category | Findings | Status |
|----------------|----------|--------|
| A01: Broken Access Control | 4 | Fixed |
| A02: Cryptographic Failures | 3 | Fixed |
| A03: Injection | 2 | Fixed |
| A04: Insecure Design | 5 | Partially addressed |
| A05: Security Misconfiguration | 8 | Partially addressed |
| A06: Vulnerable Components | 12 | Partially addressed |
| A07: Authentication Failures | 6 | Fixed |
| A08: Software Integrity Failures | 2 | Fixed |
| A09: Security Logging Failures | 3 | Partially addressed |
| A10: SSRF | 1 | Fixed |

### PCI DSS Relevance

As a payment processor, NovaPay's compliance with PCI DSS was at stake. Our assessment identified:

- **Requirement 6.5.10:** Broken authentication and session management (critical findings)
- **Requirement 6.5.3:** Injection flaws (medium findings)
- **Requirement 10:** Logging and monitoring gaps

Our remediation roadmap aligned directly with PCI DSS control requirements, positioning NovaPay for successful compliance attestation.

---

## 15. Investment and ROI

### Engagement Cost

| Component | Cost |
|-----------|------|
| Security assessment (6 weeks) | $52,000 |
| Developer training (8 hours) | $8,000 |
| Remediation support (4 weeks) | $12,000 |
| Re-testing and validation | $6,000 |
| **Total** | **$78,000** |

### Return on Investment

**Tangible Benefits:**
- Series C closed ($18M raised) - security assessment was a gate
- Enterprise deal unlocked ($2.4M ARR)
- PCI DSS penalty avoided (potential $500K+)
- Security incident costs avoided (industry average: $4.45M)

**Intangible Benefits:**
- Engineering team confidence improved
- Security as a competitive differentiator
- Customer trust and retention
- Employee recruitment advantage

**ROI Calculation:**
- Conservative estimate: 30x return on security investment
- Break-even: Every $1 spent saved $30 in potential breach costs

---

## 16. Testimonials and Feedback

### CEO, NovaPay

> "We knew security was important, but we didn't realize how exposed we were until we saw the report. Three critical vulnerabilities that could have led to a data breach or worse—the audit paid for itself 30 times over before it was even finished. What I appreciated most was that the team didn't just hand us a list of problems. They helped us fix them, trained our engineers, and gave us a roadmap for staying secure as we scale."

### VP of Engineering, NovaPay

> "The developer training was a turning point for our team. Engineers who previously avoided security discussions are now主动 requesting security reviews and catching issues in code review. We've integrated Snyk into our CI/CD pipeline and haven't had a dependency vulnerability reach production in 8 months. The investment in prevention has been far less painful than dealing with an incident would have been."

---

## 17. Future Recommendations

### Immediate Next Steps (0-3 Months)

1. **Implement HashiCorp Vault** for secrets management
2. **Deploy AWS WAF** with OWASP rule set
3. **Establish security champion program** (one per engineering squad)
4. **Quarterly vulnerability scanning** automated in CI/CD

### Medium-Term Roadmap (3-6 Months)

1. **Penetration testing** (external, full scope)
2. **Incident response tabletop exercise**
3. **Business continuity and disaster recovery review**
4. **Third-party risk management program**

### Long-Term Strategy (6-12 Months)

1. **SOC 2 Type II certification** preparation
2. **PCI DSS Level 1** compliance (if transaction volume increases)
3. **Security operations center** (internal or managed)
4. **Zero trust architecture** implementation

---

## 18. Re-Test Results

### Re-Test Scope

Four weeks after initial findings, we conducted a comprehensive re-test of all critical and high severity vulnerabilities.

### Re-Test Methodology

1. **Automated scanning:** Full ZAP and Burp Suite rescan
2. **Manual verification:** Each fixed vulnerability was manually tested
3. **Code review:** Reviewed implementation of fixes
4. **Regression testing:** Ensured fixes didn't introduce new issues

### Re-Test Results

| Vulnerability ID | Original Severity | Status | Re-Test Notes |
|-----------------|------------------|--------|---------------|
| CVE-CANDIDATE-001 | Critical | **Fixed** | Verified with 10 test accounts |
| CVE-CANDIDATE-002 | Critical | **Fixed** | "none" algorithm rejected, RS256 enforced |
| CVE-CANDIDATE-003 | Critical | **Fixed** | UUID adoption prevents enumeration |
| H001 | High | **Fixed** | Rate limiting now enforced at API gateway |
| H002 | High | **Fixed** | Session timeout reduced to 30 minutes |
| H003 | High | **Fixed** | Card data removed from all logs |
| H004 | High | **Fixed** | Security headers implemented |
| H005 | High | **Partially Fixed** | Better error messages, enumeration still possible but harder |
| H006 | High | **Fixed** | Password reset tokens now 256-bit |
| H007 | High | **Fixed** | Separate authentication domain for admin |

**Re-Test Conclusion:** NovaPay demonstrated excellent remediation velocity. Critical vulnerabilities: 0. High vulnerabilities: 1 remaining (partially addressed). Overall security posture significantly improved.

---

## 19. Appendix: Vulnerability Database

### Full Vulnerability List

A complete database of all 47 vulnerabilities, including technical details, proof-of-concept exploits, and remediation guidance, is provided in the accompanying `vulnerability-database.csv` file.

### Remediation Code Samples

Code examples for each remediation, tested and verified, are provided in the `remediation-samples/` directory.

### NovaPay Security Policy (Redacted)

A draft security policy, developed during this engagement, is provided in the `security-policy-draft.md` file for NovaPay's adaptation.

---

## 20. Contact and Next Steps

### Engage For Your Security Assessment

This case study demonstrates our approach to web application security: thorough assessment, actionable remediation, and lasting security culture improvement.

**Ready to assess your application's security posture?**

We offer:
- Web application security audits
- API security assessments
- Cloud security reviews
- Penetration testing
- Security program development

**Contact:** [Your contact information here]

---

*Case Study prepared for NovaPay's security engagement (Q3 2025). All company information used with permission. Specific vulnerabilities and remediation details adapted for confidentiality.*
