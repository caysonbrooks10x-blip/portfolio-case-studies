# Objection Handling — Authentication & Access Control Redesign

## Objection: "We're already compliant. We passed our last examination."

**Response:**
When was that examination? Regulatory requirements evolve. FFIEC guidance was updated in 2021 to emphasize multi-factor authentication, risk-based authentication, and privileged access management. Many banks are still operating under old examination standards.

OmniBank had passed their previous examination. But when the OCC updated their authentication guidance, OmniBank's controls no longer met the new standard. The next examination found critical deficiencies.

We recommend annual authentication control reviews to stay current with regulatory expectations.

---

## Objection: "Our core banking vendor handles authentication. That's their responsibility."

**Response:**
Your core banking vendor handles authentication for the core system — and they have their own security controls. But you're responsible for:

- How administrators access that system
- How your employees connect to the core banking network
- How you monitor and audit that access
- How third-party vendors connect to your systems

OmniBank's shared admin accounts for Temenos were their responsibility, not the vendor's. That's what the OCC cited.

---

## Objection: "MFA is too complex for our customers. We'll get complaints."

**Response:**
Customer experience concerns are valid — but modern MFA is far less intrusive than it used to be.

OmniBank's customers use Okta Verify push notifications — they just tap "Approve" on their phone. For most transactions, no MFA is needed at all. MFA only steps up for unusual activity.

Customer complaints about security are rare when you communicate the value clearly. "We're adding extra security to protect your money" resonates with customers.

OmniBank's customer satisfaction scores actually improved after MFA deployment — customers appreciated the added protection.

---

## Objection: "Our legacy systems can't support modern authentication."

**Response:**
Modern privileged access management solutions are designed specifically for legacy systems.

CyberArk PAM can vault credentials for any system — including Temenos. Administrators request access through a workflow, PAM provides temporary credentials, session is recorded, credentials are rotated. The core banking system sees a normal login. The vendor relationship remains intact.

OmniBank's Temenos administrators now have individual accounts, JIT access, and session recording — without any changes to Temenos itself.

---

## Objection: "We can't afford the downtime during implementation."

**Response:**
We design implementations to avoid disrupting banking operations.

OmniBank's MFA rollout happened in phases: administrators first, then retail banking users in waves. We ran parallel systems during transition. Banking operations continued without interruption.

For critical systems, we implement during maintenance windows. For less critical systems, we implement during normal hours. Your operations continuity is our priority.

---

## Objection: "Your competitor is quoting $60,000 less."

**Response:**
I've seen those quotes. Here's what often differentiates pricing:

Scope: Are they covering all channels (web, mobile, admin, vendor)? Are they implementing PAM or just recommending it?

Deliverables: Do they include implementation or just assessment and design? Do they provide regulatory-ready documentation?

Ongoing support: Do they help with your regulatory examination or just deliver a report?

OmniBank compared several firms. The lower quotes were for assessment only — no implementation, no PAM deployment, no examination support. We delivered a complete transformation, not just a report.

---

## Objection: "Our IT team can handle this. We don't need external help."

**Response:**
Your IT team is excellent at banking operations. But identity and access management is a specialized discipline — particularly for regulatory compliance.

OmniBank's IT team had strong technical skills but limited experience with FFIEC authentication guidance and OCC examination expectations. We brought both — technical expertise AND regulatory familiarity.

Think of us as an extension of your team, not a replacement. We do the heavy lifting on IAM transformation while your team maintains operations.

---

## Objection: "How do we know this will satisfy the regulators?"

**Response:**
We've guided 20+ banks through regulatory examinations. We know what examiners look for — and we build evidence packages that satisfy them.

OmniBank's examination response documented every control we implemented, with evidence of effectiveness. When the examiner asked about MFA, we had usage statistics, enrollment rates, and authentication logs. When they asked about privileged access, we had PAM session recordings and access request approvals.

Our documentation approach has a 100% regulatory acceptance rate.

---

## Objection: "We need to think about it / present to our board."

**Response:**
Absolutely — this is a significant investment and requires board-level discussion.

Here's what I'd suggest for your board: The OCC can impose civil money penalties of $1M to $50M per violation for BSA/AML and security violations. The average enforcement action against regional banks is $12M.

OmniBank's engagement cost $185,000. The enforcement penalties they avoided: $12M+. The annual fraud reduction: $2.1M. The math is compelling.

If you'd like, I can join a board call to answer technical and regulatory questions directly.

---

## Objection: "Let's wait until next quarter."

**Response:**
I hear you on budget timing. But the regulatory clock is already ticking.

OmniBank had 90 days from their examination to demonstrate corrective action. Every week of delay is a week closer to your next examination with unresolved findings.

What I can offer: if you scope now, we can begin within 2 weeks. That gives you implementation time before your next regulatory check-in.

---

*These objections represent real concerns prospects have. Responses should be adapted to your specific prospect's situation and tone adjusted to match your sales style.*
