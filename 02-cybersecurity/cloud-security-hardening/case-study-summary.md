# Meridian Health Cloud Security Hardening — Executive Summary

## The Engagement

Meridian Health, a regional healthcare network serving 2.3 million patients across 12 hospitals, engaged us following an AWS GuardDuty alert that detected cryptojacking activity in their staging environment. Over 10 weeks, our team of three cloud security engineers assessed their multi-account AWS infrastructure and uncovered 156 security misconfigurations—including 4 critical issues exposing protected health information.

## The Challenge

- 2.3 million patients, $1.2B annual revenue, 847 AWS resources
- No cloud security expertise in-house
- HIPAA compliance pressure requiring rapid remediation
- Cryptojacking incident indicated potential for deeper compromise
- Multiple AWS accounts without centralized security governance

## The Solution

We conducted a comprehensive cloud security engagement:
- GuardDuty alert forensic investigation
- Multi-account CSPM assessment (Prowler, Security Hub)
- IAM deep-dive and least-privilege remediation
- Zero-trust network architecture redesign
- HashiCorp Vault deployment for secrets management
- HIPAA compliance automation and dashboards

## Key Findings

**156 total security misconfigurations identified:**
- 4 Critical (exposed credentials, public S3, unencrypted PHI RDS)
- 23 High severity
- 67 Medium severity
- 62 Low severity

**Critical issues included:**
- Exposed IAM credentials in public GitHub repositories
- Public S3 buckets containing patient metadata
- Unencrypted RDS instances with 2.3M patient records
- Unrestricted VPC peering enabling lateral movement

## The Outcome

| Metric | Before | After |
|--------|--------|-------|
| Critical vulnerabilities | 4 | 0 |
| IAM users with MFA | 11% | 100% |
| S3 buckets with public access | 8 | 0 |
| HIPAA controls met | 34 of 60 | 52 of 60 |
| CIS AWS Benchmark compliance | 38% | 89% |

**Results:**
- HIPAA compliance audit passed with zero critical findings
- $180,000 annual cyber insurance premium reduction
- 18 months incident-free post-engagement
- 12 IT staff AWS Security Specialty certified
- Zero-trust architecture reducing attack surface by 94%

**Investment:** $125,000 | **Timeline:** 10 weeks | **Team:** 3 engineers

---

*Engagement Value: Demonstrated 69x ROI through avoided breach costs and operational savings.*
