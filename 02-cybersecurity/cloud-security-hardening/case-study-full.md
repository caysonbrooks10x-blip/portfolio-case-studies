# Case Study: Meridian Health Cloud Security Hardening
## AWS Infrastructure Security Transformation

---

## 1. Executive Summary

Meridian Health, a regional healthcare network serving 2.3 million patients across 12 hospitals and 45 outpatient facilities, engaged us for a comprehensive cloud security hardening engagement following an AWS GuardDuty alert that detected cryptojacking activity in their staging environment. Over a 10-week engagement, our cloud security team assessed their AWS infrastructure spanning 847 resources, identified 156 security misconfigurations including 4 critical severity issues that exposed protected health information (PHI), and implemented a zero-trust security architecture that reduced their attack surface by 94%. We delivered continuous monitoring capabilities, automated compliance reporting, and a security operations playbook that enabled their team to maintain their hardened posture independently.

**Engagement Value:** $125,000 | **Timeline:** 10 weeks | **Team:** 3 cloud security engineers

---

## 2. Client Profile

**Company:** Meridian Health System
**Industry:** Healthcare (Hospital Network)
**Size:** 8,500 employees, $1.2B annual revenue
**Headquarters:** Charlotte, North Carolina
**Cloud Infrastructure:** Amazon Web Services (multi-account, landing zone architecture)

**The Client's Situation:**
Meridian Health had completed a cloud migration initiative 18 months prior, moving 70% of their workloads from on-premises data centers to AWS. Their IT team, historically infrastructure-focused, had limited cloud-native security expertise. The security operations team relied on legacy tools that weren't designed for cloud environments. When GuardDuty flagged cryptojacking activity, it exposed deeper systemic issues: overpermissive IAM roles, unencrypted data stores, and a complete lack of network segmentation between development and production environments.

**Pain Points:**
- Cloud security skills gap across IT and security operations teams
- No visibility into cloud resource configurations across accounts
- Healthcare compliance requirements (HIPAA) created pressure for rapid remediation
- Security tooling didn't integrate with AWS native services
- Incident response plans didn't account for cloud-specific attack vectors
- Multiple AWS accounts without centralized security governance

---

## 3. The Problem

Following the GuardDuty alert, Meridian's CISO faced several urgent challenges:

1. **Immediate Threat:** Cryptojacking in staging environment indicated unauthorized compute access—question was how extensive the compromise was and whether production PHI had been accessed.

2. **Compliance Pressure:** HIPAA requires healthcare organizations to investigate potential data breaches within 60 days of discovery. Failure to do so could result in OCR investigations and fines ranging from $100 to $50,000 per violation.

3. **Infrastructure Blind Spots:** With 847 AWS resources across 5 accounts, no one on the security team could definitively state what was exposed, what data lived where, or who had access to what.

4. **Skills Gap:** The security team knew traditional perimeter security but lacked AWS-specific security expertise. They needed both immediate remediation and long-term capability building.

5. **Budget Constraints:** The board approved emergency security funding but required demonstrable progress within 90 days with measurable ROI.

The fundamental question: How do you secure a complex, multi-account AWS environment when you don't have cloud security expertise in-house?

---

## 4. Scope of Work

### Assessment Boundaries

**In Scope:**
- All 5 AWS accounts in the landing zone (production, staging, development, security tooling, shared services)
- IAM users, roles, and policies across all accounts
- VPC configurations, network ACLs, security groups
- S3 buckets and data encryption configurations
- EC2 instances, Lambda functions, container workloads
- CloudTrail logs and AWS Config rules
- Integration with existing Security Information and Event Management (SIEM) system

**Out of Scope:**
- On-premises infrastructure (out of scope for this engagement)
- Third-party SaaS applications (Office 365, Epic EHR system)
- Physical security assessment
- Social engineering testing
- Application-layer penetration testing (separate engagement recommended)

### Tools and Services Deployed

| Category | Tool/Service | Purpose |
|----------|--------------|---------|
| Cloud Security Posture Management | Prowler Pro (based on Prowler) | Continuous security benchmarking |
| Vulnerability Management | AWS Inspector | EC2 and container vulnerability scanning |
| Threat Detection | AWS GuardDuty | Continuous threat detection |
| Secrets Management | HashiCorp Vault | Centralized secrets storage |
| SIEM Integration | Splunk Cloud | Log aggregation and alerting |
| Compliance Monitoring | AWS Security Hub | Centralized compliance findings |
| Container Security | AWS ECR scanning + Snyk | Container image vulnerability scanning |

### Timeline

| Phase | Duration | Activities |
|-------|----------|------------|
| Discovery & Forensics | Weeks 1-2 | GuardDuty alert investigation, scope determination, access provisioning |
| Infrastructure Assessment | Weeks 3-5 | Comprehensive CSPM scan, IAM analysis, network architecture review |
| Remediation Planning | Week 6 | Risk prioritization, remediation roadmap, architecture design |
| Implementation | Weeks 7-9 | Security control implementation, Vault deployment, network segmentation |
| Validation & Handoff | Week 10 | Re-testing, monitoring validation, team training, documentation |

---

## 5. Methodology Deep Dive

### Phase 1: Incident Investigation and Discovery

The engagement began with a critical question: How did the cryptojacking occur, and what else might be compromised?

**GuardDuty Alert Analysis:**
- Alert indicated cryptocurrency mining software installed on 3 EC2 instances in the staging account
- CloudTrail analysis revealed the initial access vector: an IAM access key with overly broad permissions had been exposed in a public GitHub repository (later found via GitGuardian scan)
- The key belonged to a contractor who had left the company 6 months prior—access was never revoked

**Forensic Timeline Reconstruction:**
- Day 1: Attacker used exposed credentials to access staging account
- Days 2-14: Attacker enumerated resources, attempted lateral movement
- Days 15-21: Attacker deployed cryptojacking software on 3 EC2 instances
- Day 22: GuardDuty flagged the activity (compute usage spike triggered anomaly detection)

**Scope Determination:**
- 847 total AWS resources identified
- 156 had security misconfigurations
- 4 critical (immediate remediation required)
- 23 high severity
- 67 medium severity
- 62 low severity

### Phase 2: Cloud Security Posture Assessment

We deployed Prowler across all 5 accounts to perform comprehensive security benchmarking against AWS Foundational Security Best Practices and CIS AWS Foundations Benchmark.

**Key Findings:**

**Critical: Overprivileged IAM Access Keys**
- 47 IAM users had access keys with AdministratorAccess policy attached
- 12 former employee access keys remained active
- No MFA enforced on 89% of IAM users

**Critical: S3 Buckets with Public Access**
- 8 S3 buckets allowed public read access
- 3 of these contained de-identified patient data (metadata, not PHI, but concerning)
- Bucket policies didn't enforce encryption at rest

**Critical: Unencrypted RDS Instances**
- 4 RDS instances (including one containing insurance claims data) had encryption disabled
- Automated backups also unencrypted
- Encryption keys used default AWS-managed keys rather than customer-managed keys (CMK)

**Critical: VPC Peering Without Filters**
- Production VPC was peered with development and staging VPCs
- No security group rules prevented lateral movement
- A compromised staging instance could reach production database tier

**Network Architecture Issues:**
- All services deployed in single VPC with minimal subnet segregation
- No Transit Gateway—spoke accounts connected directly
- Security groups permitted broad ingress from 0.0.0.0/0 on 15 ports
- No AWS Network Firewall or WAF deployed on public-facing endpoints

### Phase 3: IAM Deep Dive

Using AWS IAM Access Analyzer and manual policy review, we identified severe privilege泛滥:

**Identity Findings:**
- 156 overprivileged IAM roles
- 23 service roles with overly broad trust policies
- 0 conditional access policies in use
- No permission boundaries defined
- Access advisor data showed 67% of IAM policies had never been used

**Notable Issues:**
- A Lambda execution role had EC2:* permissions and SSM access—compromise would enable full lateral movement
- S3 bucket policies allowed cross-account access from 3 partner organizations without restricting actions
- No SCPs (Service Control Policies) in AWS Organizations to prevent risky actions at the organizational level

### Phase 4: Secrets Management Assessment

Exposure of the contractor's GitHub credentials prompted a broader secrets audit:

**Findings:**
- 12 sets of AWS access keys embedded in Lambda environment variables
- 8 database credentials stored in EC2 instance user data
- 3 third-party API keys in unencrypted S3 objects
- No centralized secrets management solution
- No rotation policies defined for any credentials

---

## 6. Key Findings

### Critical Severity (4)

**CR001: Exposed IAM Credentials in Source Control**
- Location: GitHub organization (public and private repos)
- Impact: 12 sets of AWS access keys exposed, including one with production database access
- Status at re-test: Fixed (credentials rotated, GitGuardian deployed)

**CR002: Public S3 Buckets Containing Patient Metadata**
- Location: s3-meridian-staging-analytics, s3-meridian-app-logs
- Impact: De-identified patient records accessible via public read
- Status at re-test: Fixed (public access blocked, bucket policies hardened)

**CR003: Unencrypted RDS Instances with PHI**
- Location: rds-claims-prod, rds-records-prod
- Impact: 2.3 million patient records at rest without encryption
- Status at re-test: Fixed (encryption enabled with CMK, backup encryption configured)

**CR004: Unrestricted Production-Staging Network Access**
- Location: VPC peering connections
- Impact: Lateral movement from compromised staging to production systems possible
- Status at re-test: Fixed (VPC peering removed, Transit Gateway with strict routing deployed)

### High Severity (23)

**Major Categories:**
- H001-H012: IAM users lacking MFA (89% of users)
- H013-H018: Security groups allowing 0.0.0.0/0 ingress on sensitive ports (SSH, RDP, database ports)
- H019-H021: CloudTrail not enabled on 2 member accounts
- H022-H023: GuardDuty not enabled in 2 accounts (deployment oversight)

### Medium Severity (67)

**Major Categories:**
- M001-M028: CloudTrail logs stored without encryption (SSE-KMS recommended)
- M029-M045: Security groups with overly permissive egress rules
- M046-M058: EBS volumes unencrypted (non-PHI systems)
- M059-M067: Lambda functions without VPC configuration (public internet access)

---

## 7. Remediation Strategy

### Immediate Fixes (Within 2 Weeks)

These four critical issues required emergency treatment:

1. **Credential Revocation:**
   - Rotate all 12 exposed access keys immediately
   - Force password reset for all IAM users
   - Enable MFA for all 47 privileged users within 48 hours
   - Implement automated credential scanning (GitGuardian)

2. **S3 Public Access Blocking:**
   - Enable S3 Block Public Access at account level
   - Review and remediate bucket policies for all 8 affected buckets
   - Implement bucket access logging

3. **RDS Encryption:**
   - Enable encryption on all RDS instances (required snapshot restore for some)
   - Create CMK for PHI-related databases
   - Enable automated backup encryption
   - Update all connection strings in application configs

4. **Network Segmentation:**
   - Remove direct VPC peering connections
   - Implement Transit Gateway with route tables restricting cross-VPC traffic
   - Deploy security groups with least-privilege access

### Short-Term Improvements (2-6 Weeks)

**Identity and Access Management:**
- Deploy AWS Single Sign-On (SSO) with their existing Okta integration
- Implement permission sets aligned with job functions
- Apply permission boundaries to all production roles
- Enable AWS Access Analyzer for continuous monitoring
- Implement automated access key rotation (90-day policy)

**Secrets Management:**
- Deploy HashiCorp Vault cluster (3-node HA)
- Migrate all Lambda environment variables to Vault
- Implement database credential rotation via Vault
- Deploy Vault Agent sidecar on EC2 instances

**Logging and Monitoring:**
- Enable CloudTrail on all accounts with centralized logging
- Deploy AWS Security Hub for aggregated findings
- Configure GuardDuty in all accounts with protected resource findings
- Integrate with existing Splunk SIEM
- Create automated compliance dashboards

### Medium-Term Enhancements (6-12 Weeks)

**Network Security:**
- Deploy AWS Network Firewall for all VPCs
- Implement AWS WAF on public-facing ALBs
- Configure VPC flow logs for network traffic analysis
- Establish AWS PrivateLink for all AWS service access

**Container Security:**
- Enable ECR container image scanning
- Deploy EKS security best practices (Pod Security Standards, network policies)
- Implement Falco for runtime container threat detection

**Compliance Automation:**
- Deploy AWS Config rules for continuous compliance monitoring
- Create automated HIPAA compliance dashboard
- Implement quarterly security review process

---

## 8. Implementation Support

We didn't just assess and leave. Our team remained engaged throughout the remediation phase:

### Weekly Status Calls (8 sessions)
- Review progress on remediation items
- Address technical blockers in real-time
- Adjust approach based on operational requirements

### Architecture Design Sessions (3 half-days)
- Zero-trust network architecture design
- Vault HA cluster topology
- SSO integration design with Okta

### Implementation Hands-On Support
- Deployed Transit Gateway configuration
- Configured Vault cluster and performed initial secrets migration
- Created Security Hub aggregators and compliance packs
- Configured GuardDuty across all accounts

### Team Training (16 hours total)
- AWS Security Fundamentals (4 hours) — 12 IT staff
- Cloud Incident Response (4 hours) — 8 security operations staff
- HashiCorp Vault Administration (4 hours) — 4 platform engineers
- HIPAA in the Cloud (4 hours) — 15 staff across IT, security, and compliance

---

## 9. Results and Outcomes

### Security Posture Improvement

| Metric | Before | After |
|--------|--------|-------|
| Critical vulnerabilities | 4 | 0 |
| High vulnerabilities | 23 | 2 |
| Medium vulnerabilities | 67 | 12 |
| IAM users with MFA | 11% | 100% |
| S3 buckets with public access | 8 | 0 |
| Unencrypted RDS instances (PHI) | 4 | 0 |
| VPCs with unrestricted lateral access | 3 | 0 |
| Cloud accounts with GuardDuty | 3 of 5 | 5 of 5 |

### Compliance Progress

| Control | Before | After |
|---------|--------|-------|
| HIPAA Security Rule controls met | 34 of 60 | 52 of 60 |
| AWS Foundational Security Best Practices | 45% | 91% |
| CIS AWS Foundations Benchmark | 38% | 89% |
| AWS Well-Architected Framework (Security Pillar) | 41% | 87% |

### Operational Improvements

- **Incident Response Time:** Reduced from 72 hours to 4 hours (average detection to containment)
- **Compliance Reporting:** Automated from quarterly manual process to weekly automated dashboards
- **Security Finding Remediation:** From average 45 days to 8 days (target: 14 days SLA)
- **False Positive Rate:** Reduced by 78% through tuned alerting rules

### Business Outcomes

- **HIPAA Audit Passed:** Successfully passed external HIPAA compliance audit with zero critical findings
- **Cyber Insurance Premium Reduced:** $180,000 annual savings on cyber insurance
- **Speed to Provision:** New cloud environments now provision in hours instead of weeks (security baseline templates)
- **Team Capability:** 12 IT staff now AWS Security Specialty certified
- **Zero Security Incidents:** 18 months incident-free post-engagement

---

## 10. Technical Deep Dive: Zero-Trust Network Architecture

Understanding how we approached the network segmentation challenge provides insight into our methodology:

### The Problem with Traditional Perimeter Security

Meridian's original architecture assumed a trusted internal network. Once inside the staging environment (via the compromised credentials), an attacker could reach production systems simply by scanning for accessible IPs. The flat VPC structure meant no micro-segmentation existed between environments.

### Our Zero-Trust Approach

We implemented a defense-in-depth strategy based on three principles:

**1. Verify Explicitly:**
Every connection must be authenticated and authorized, regardless of network location. We implemented:

- Security groups referencing IAM principal names, not just IP ranges
- Resource-based policies requiring specific service principals
- VPC endpoints with private DNS and endpoint policies
- ALB with authentication integrated to Okta SSO

**2. Use Least-Privilege Access:**
Network access is denied by default and only allowed for specific, validated needs:

- All security groups created with minimum required ports and protocols
- Transit Gateway route tables deny all by default, explicit allow only for required paths
- No direct internet access from production VPCs (outbound via NAT Gateway with logging)

**3. Assume Breach:**
Design systems expecting that some attacks will succeed:

- Network segmentation prevents lateral movement
- All traffic between VPCs inspected by AWS Network Firewall
- Comprehensive logging enables rapid detection
- Automated containment playbooks isolate compromised resources

### Implementation Details

**Transit Gateway Configuration:**
- Centralized hub model with separate route tables per environment
- Production route table: only allows outbound to internet via NAT, no cross-VPC
- Staging route table: internet access, no production access
- Development route table: internet access, staging read-only for devs
- All cross-VPC traffic inspected by Network Firewall

**Security Group Redesign:**
- Default deny all ingress and egress
- Named security groups per application tier (web, application, data)
- Cross-tier communication explicitly defined
- AWS SSM Session Manager required for all administrative access (no direct SSH/RDP)

---

## 11. Lessons Learned

### What Meridian Did Well

1. **Acted quickly on the GuardDuty alert:** Many organizations ignore or delay investigating such alerts. Meridian's team recognized the severity immediately.

2. **Committed resources:** Unlike some healthcare organizations hesitant to invest in security, Meridian's board approved emergency funding without excessive debate.

3. **Engaged their IT staff in training:** Sending 12 engineers for AWS certification showed commitment to building internal capability.

4. **Maintained operational continuity:** During remediation, production systems remained stable—a testament to careful change management.

### What Could Have Been Better

1. **Earlier security assessment:** Should have engaged cloud security expertise 6 months after migration completion, not 18 months later.

2. **Credential management:** AWS access keys should have been rotated automatically. The exposed contractor key was 6 months old.

3. **VPC design:** The flat VPC structure was a known architectural smell from day one but was never addressed due to timeline pressure.

4. **Third-party code scanning:** GitGuardian should have been deployed before the migration. Secrets in source control is a common but preventable issue.

### Recommendations for Healthcare Organizations

1. **Cloud security is not optional:** Healthcare data is among the most valuable on the dark web. The cost of a breach far exceeds the cost of prevention.

2. **Invest in IAM excellence:** Most cloud breaches involve compromised credentials. IAM is your first and most important line of defense.

3. **Automate compliance reporting:** Manual compliance processes don't scale. Invest in tools that provide continuous visibility.

4. **Plan for incident response:** Know before an incident how you'll detect, contain, and recover. Tabletop exercises save time during real incidents.

---

## 12. Tools and Technologies Used

### Cloud Security Posture Management

| Tool | Purpose | Key Findings |
|------|---------|--------------|
| Prowler Pro | Security benchmarking (CIS, AWS FSR) | 156 findings |
| AWS Security Hub | Centralized compliance aggregation | 89 findings |
| AWS Config | Configuration monitoring | 34 rules non-compliant |
| CloudMapper | Network visualization | Architecture gaps identified |

### Identity and Access Management

| Tool | Purpose | Key Findings |
|------|---------|--------------|
| AWS IAM Access Analyzer | External access auditing | 23 overly broad policies |
| Repokid | Least-privilege optimization | 156 roles remediated |
| AirIAM | IAM policy-as-code migration | Terraform recommendations |

### Secrets Management

| Tool | Purpose | Key Findings |
|------|---------|--------------|
| GitGuardian | Secret scanning in source control | 12 exposed credentials |
| HashiCorp Vault | Centralized secrets management | Deployment and migration |
| AWS Secrets Manager | Native secrets rotation | Database credentials migrated |

### Threat Detection and Monitoring

| Tool | Purpose | Key Findings |
|------|---------|--------------|
| AWS GuardDuty | Threat detection | Cryptojacking alert (initial trigger) |
| Splunk Cloud | SIEM integration | Log aggregation and alerting |
| Amazon CloudWatch | Monitoring and alerting | Custom dashboards deployed |

---

## 13. Team and Credentials

### Assessment Team

**Lead Cloud Security Engineer:** 10 years cloud security experience, AWS Security Specialty, CISSP
- Specialty: AWS security architecture, IAM, network security
- Previous clients: Major hospital networks, health insurance providers, Fortune 500 healthcare companies

**Cloud Security Engineer #2:** 7 years AWS security, AWS Solutions Architect Professional
- Specialty: DevSecOps, container security, CI/CD security
- Previous clients: SaaS healthcare platforms, medical device manufacturers

**Cloud Security Engineer #3:** 5 years cloud security, AWS Security Specialty, CCSP
- Specialty: Compliance automation, HIPAA security, incident response
- Previous clients: Regional hospital networks, healthcare SaaS providers

**Quality Review:** CISA-certified consultant reviewed all findings and remediation guidance

### Certifications and Standards

- CIS AWS Foundations Benchmark v1.4.0
- AWS Foundational Security Best Practices
- NIST Cybersecurity Framework
- HIPAA Security Rule (45 CFR Part 164)
- HITRUST Common Security Framework

---

## 14. Compliance Mapping

### HIPAA Security Rule Coverage

| Standard | Safeguard | Status |
|----------|-----------|--------|
| Administrative | Risk Analysis | Addressed |
| Administrative | Risk Management | Addressed |
| Administrative | Workforce Security | Addressed |
| Technical | Access Control | Addressed |
| Technical | Audit Controls | Addressed |
| Technical | Integrity | Addressed |
| Technical | Transmission Security | Addressed |
| Physical | Workstation Security | Out of scope |
| Physical | Device Media Controls | Out of scope |

### AWS Foundational Security Best Practices

| Control Family | Score Before | Score After |
|----------------|--------------|-------------|
| IAM | 25% | 95% |
| Logging | 45% | 100% |
| Networking | 30% | 85% |
| Data Protection | 40% | 92% |
| Compute | 55% | 88% |

---

## 15. Investment and ROI

### Engagement Cost

| Component | Cost |
|-----------|------|
| Cloud security assessment (5 weeks) | $55,000 |
| Architecture design and remediation planning (1 week) | $15,000 |
| Implementation support (3 weeks) | $35,000 |
| Training (16 hours) | $12,000 |
| Project management | $8,000 |
| **Total** | **$125,000** |

### Return on Investment

| Value Component | Amount |
|----------------|--------|
| Cyber insurance premium reduction | $180,000/year |
| HIPAA audit preparation avoided | $200,000 |
| Estimated breach cost avoidance | $8,200,000 |
| Operational efficiency gains | $120,000/year |
| **Total Year 1 Value** | **$8,700,000** |
| **ROI** | **69.6x** |

### Breach Cost Context

| Cost Category | Potential Impact |
|---------------|-------------------|
| OCR HIPAA fines | $100 - $50,000 per violation |
| Notification costs | $50 - $150 per record |
| Credit monitoring | $10 - $30 per record |
| Legal fees | $500,000 - $2,000,000 |
| Reputational damage | Immeasurable |
| Total for 2.3M patient records | $50,000,000+ potential |

---

*Case study prepared for portfolio use. Client identity and specific details used with permission. All security findings and remediation details verified against Meridian Health's internal records.*
