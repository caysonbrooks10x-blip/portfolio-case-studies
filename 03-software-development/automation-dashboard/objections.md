# Prism Health — Objections & Responses

## Sales Objections

### "Our EHR vendors won't share data. How do you handle that?"

**Response:**
"We've integrated with Epic, Cerner, Allscripts, athenahealth, eClinicalWorks, and 9 others. Here's our approach:

1. **FHIR R4 (modern EHRs):** Epic, Cerner, and Allscripts support FHIR. We connect directly via OAuth 2.0.
2. **HL7 (legacy systems):** We build custom HL7 adapters for systems without FHIR.
3. **Direct database (read-only):** For systems with no API, we use read-only database connections.
4. **Flat file (last resort):** CSV exports from the EHR, ingested and processed.

We've never met an EHR we couldn't integrate with. If your vendor has data, we can access it."

---

### "Clinicians won't adopt another tool. They've seen this before."

**Response:**
"We heard this concern. Here's why adoption was 94% within 30 days:

**Key insight:** We automate work, not decisions. Nurses still make clinical judgments. We eliminate the data gathering that consumed 68% of their time.

**Proof:**
- 3 weeks of shadowing before writing code
- 12 care coordinators validated every feature
- Phased rollout (one network at a time)
- Training focused on time savings

The tool makes them more effective. That's adoption."

---

### "HIPAA compliance is a nightmare. We'll be in review for months."

**Response:**
"We build HIPAA-first, not HIPAA-at-the-end. Here's our approach:

**Architecture:**
- End-to-end encryption (at rest and in transit)
- Comprehensive audit logging for all PHI access
- Role-based access with care team scopes
- MFA for all clinical users

**Compliance:**
- We provide the BAA
- Security documentation package
- SOC 2 Type II certified infrastructure

**Proof:** We passed HIPAA audit on first submission. No findings. No remediation.

Your legal team reviews our security documentation. Our BAA is standard. This moves fast."

---

### "We need to see ROI before committing $380K."

**Response:**
"We can structure this:

**Phase 1 (Weeks 1-8):** Discovery + Patient 360 + 3 EHR integrations
**Phase 2 (Weeks 9-16):** Workflow engine + outreach + remaining integrations

You see working software at Week 8. You validate ROI before Phase 2 payment. If Phase 1 doesn't deliver value, you don't proceed.

This is how we de-risk healthcare projects. Show value early."

---

## Technical Objections

### "Real-time data across 14 EHRs will be slow. Our network can't handle it."

**Response:**
"We don't query EHRs in real-time for every dashboard load. Here's the architecture:

1. **Background sync:** Patient data syncs from EHRs every 15 minutes (configurable)
2. **Local cache:** Dashboard reads from our PostgreSQL, not the EHR
3. **Incremental updates:** We sync changes, not full records
4. **Escalation read-through:** If cache is stale (rare), we fetch fresh data

Result: Dashboard loads in under 2 seconds. Real-time enough for clinical workflows."

---

### "Our care coordinators work offline sometimes. Can this handle that?"

**Response:**
"Current version requires connectivity — it's a web app for network-connected workstations.

For offline, Phase 2 includes:
- Local SQLite cache for recently viewed patients
- Offline task queue
- Sync on reconnection

This adds 3-4 weeks to the timeline. Is offline a Week 1 requirement, or can it ship in Phase 2?"

---

### "How do you handle EHR downtime? We can't have care coordinators blocked."

**Response:**
"With a resilient architecture:

1. **Local cache:** All patient data cached locally
2. **Read-only fallback:** Dashboard works from cache during EHR downtime
3. **Read-only indicators:** coordinators see which data might be stale
4. **EHR status dashboard:** We show which EHRs are up/down
5. **Task queue:** Tasks requiring EHR writes queue until restored

We've tested this with simulated EHR outages. Coordinators continue working; writes queue automatically."

---

### "How do you ensure data quality across 14 EHRs?"

**Response:**
"With a data normalization layer:

1. **Schema mapping:** Each EHR has different field names, formats, codes. We map to a unified schema.
2. **Conflict resolution:** If Patient XYZ has different addresses in 3 EHRs, we show all 3 with source attribution.
3. **Master patient index:** We link records across EHRs to the same patient.
4. **Data quality scores:** We show confidence levels for each data element.

The dashboard shows you the data and its source. You make the clinical call."

---

## Timeline Objections

### "We need this in 12 weeks, not 16. Can you compress?"

**Response:**
"Options for compression:

**Option A (12 weeks):**
- Patient 360 + 7 EHR integrations
- Basic care plan templates (no automation rules)
- Email outreach only (no SMS/voice)
- Manual quality reports (not automated)

**Option B (14 weeks):**
- Full Patient 360
- All 14 integrations
- Basic care plans
- Email + SMS outreach
- Manual reporting

**Option C (16 weeks, full):**
- Everything in scope

What matters most: speed, integration count, or automation depth?"

---

### "We can't give you access to all 14 EHRs at once. Can you start with 3?"

**Response:**
"Yes — this is actually our recommendation:

**Phase 1 (Weeks 1-8):** 3 priority EHRs (e.g., Epic, Cerner, athena)
**Phase 2 (Weeks 9-14):** 7 more EHRs
**Phase 3 (Weeks 15-16):** Remaining 4 EHRs

We build the integration framework in Phase 1. Adding new EHRs in Phases 2-3 is faster (1-2 days per EHR vs 1-2 weeks).

This is how we handle EHR access constraints for every healthcare client."
