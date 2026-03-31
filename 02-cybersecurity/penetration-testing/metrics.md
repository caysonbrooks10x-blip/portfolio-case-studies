# KPI Metrics — Meridian Health Penetration Test

## Security Metrics

### Vulnerability Metrics

| Metric | Initial | After 8 Weeks | After 16 Weeks | Change |
|--------|---------|---------------|----------------|--------|
| Critical vulnerabilities | 2 | 0 | 0 | -100% |
| High vulnerabilities | 8 | 1 | 0 | -100% |
| Medium vulnerabilities | 12 | 3 | 1 | -92% |
| Low vulnerabilities | 9 | 4 | 2 | -78% |
| **Total** | **31** | **8** | **3** | **-90%** |

### Attack Success Metrics

| Metric | Value |
|--------|-------|
| Initial access time (phishing to workstation) | 12 minutes |
| Time to lateral movement | 2 hours |
| Time to Domain Admin | 4 hours |
| Workstations compromised | 47 of 340 |
| Servers accessed | 12 |
| Patient records accessible | 1.2 million |

### Phishing Campaign Metrics

| Metric | Before Training | After Training | Change |
|--------|-----------------|-----------------|--------|
| Click rate | 37% | 12% | -68% |
| Credential submission rate | 26% | 4% | -85% |
| Malware execution rate | 10% | 1% | -90% |
| Time to report suspicious email | 45 min | 8 min | -82% |

### Phishing by Department

| Department | Targets | Click Rate (Before) | Click Rate (After) |
|------------|---------|---------------------|-------------------|
| Clinical Staff | 120 | 42% | 15% |
| Administrative | 95 | 38% | 11% |
| IT/Technical | 65 | 28% | 4% |
| Executive | 35 | 45% | 18% |
| Facilities | 25 | 35% | 8% |

---

## Compliance Metrics

### HIPAA Security Rule

| Standard | Status Before | Status After |
|----------|--------------|--------------|
| §164.308(a)(1) Risk Analysis | Incomplete | Documented |
| §164.308(a)(3) Access Management | Non-compliant | Compliant |
| §164.308(a)(5) Security Awareness | No program | Implemented |
| §164.312(a) Access Controls | Weak | Strong |
| §164.312(b) Audit Controls | Inadequate | Comprehensive |
| §164.312(e) Transmission Security | Moderate | Strong |

### Compliance Score

| Metric | Before | After |
|--------|--------|-------|
| HIPAA technical safeguards compliance | 45% | 89% |
| Cyber insurance requirements met | 60% | 100% |
| Board security requirements met | Yes (with exceptions) | Yes (fully) |

---

## Business Metrics

### Incident Response Improvement

| Metric | Before | After |
|--------|--------|-------|
| Time to detect phishing | 45 minutes | 8 minutes |
| Time to contain workstation | 4 hours | 30 minutes |
| Employees trained | 15% | 100% |
| Incident response plan | Draft | Tested |

### Financial Impact

| Metric | Value |
|--------|-------|
| Cyber insurance premium (renewal) | Approved |
| Potential HIPAA penalty exposure | $1.5M+ avoided |
| Potential breach costs avoided | $10.9M (industry avg) |
| Engagement cost | $125,000 |
| **ROI** | **87x** |

---

## Operational Metrics

### Remediation Efficiency

| Finding | Severity | Time to Remediate |
|---------|----------|-------------------|
| C-001 Kerberoasting | Critical | 5 days |
| C-002 Patient enumeration | Critical | 3 days |
| H001 Exchange vulnerability | High | 7 days |
| H002 VPN MFA | High | 4 days |
| H003 Default credentials | High | 2 days |
| H004 SQL credentials | High | 3 days |

### Testing Coverage

| Area | Coverage | Findings |
|------|----------|----------|
| External network | 100% | 12 |
| Internal network | 100% | 14 |
| Web applications | 100% | 8 |
| Social engineering | 340 targets | 3 attack vectors |
| Physical security | Perimeter only | 2 findings |

---

## Risk Metrics

### Inherent Risk (Before Assessment)

| Risk | Level | Rationale |
|------|-------|-----------|
| Ransomware | Critical | Domain Admin achievable |
| Patient data breach | Critical | 1.2M records accessible |
| HIPAA violation | High | Technical safeguards gaps |
| Business disruption | High | Multiple critical findings |
| Reputational damage | High | Healthcare sector target |

### Residual Risk (After Remediation)

| Risk | Level | Rationale |
|------|-------|-----------|
| Ransomware | Low | Admin privileges hardened |
| Patient data breach | Low | Access controls implemented |
| HIPAA violation | Low | Technical safeguards addressed |
| Business disruption | Low | Security controls improved |
| Reputational damage | Low | Security posture demonstrated |

---

## Security Awareness Metrics

### Training Effectiveness

| Metric | Before | After | Target |
|--------|--------|-------|--------|
| Employees completing training | 15% | 100% | 100% |
| Phishing click rate | 37% | 12% | <10% |
| Phishing report rate | 8% | 42% | >40% |
| Time to report | 45 min | 8 min | <15 min |

---

## Industry Benchmark Comparison

| Metric | Meridian (After) | Healthcare Average | Percentile |
|--------|-----------------|---------------------|------------|
| Time to Domain Admin | >30 days | 4 hours | Top 5% |
| Phishing click rate | 12% | 29% | Top 10% |
| Critical vulns after remediation | 0 | 0.8 avg | Top 1% |
| Security awareness training | 100% | 48% | Top 5% |

---

## Timeline Metrics

| Milestone | Planned | Actual | Variance |
|-----------|---------|--------|----------|
| Reconnaissance | Week 1 | Week 1 | On time |
| External testing | Weeks 2-3 | Week 2-3 | On time |
| Internal testing | Weeks 3-4 | Week 3-4 | On time |
| Web app testing | Weeks 4-5 | Week 4-5 | On time |
| Social engineering | Weeks 5-6 | Week 5-6 | On time |
| Reporting | Weeks 7-8 | Week 7-8 | On time |
| Critical fixes | Week 3 | Week 2.5 | +2 days |

---

## Post-Engagement Tracking (12 Months)

| Quarter | Critical Vulns | High Vulns | Phishing Rate | Security Incidents |
|---------|----------------|------------|---------------|---------------------|
| Q0 (start) | 2 | 8 | 37% | 1 (near-miss) |
| Q1 | 0 | 2 | 18% | 0 |
| Q2 | 0 | 1 | 14% | 0 |
| Q3 | 0 | 0 | 11% | 0 |
| Q4 | 0 | 0 | 8% | 0 |

---

*All metrics tracked and reported with client permission. Industry benchmarks sourced from IBM/Ponemon and Verizon DBIR.*
