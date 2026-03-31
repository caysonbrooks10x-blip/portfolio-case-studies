# Objection Handling — Penetration Testing

## Objection: "We already have a vulnerability scanner."

**Response:**  
"Vulnerability scanners find known vulnerabilities—CVEs, missing patches, misconfigurations. They don't find the attack paths that real attackers use to chain vulnerabilities together.

Meridian Health had vulnerability scanning. It didn't find the Kerberoasting vulnerability that let us get Domain Admin. It didn't find the IDOR in the patient portal. It didn't show them that 37% of their employees would click a phishing link.

Automated scanning is necessary but not sufficient. Real attackers combine multiple medium findings into a critical compromise. We find those chains."

---

## Objection: "Our IT team does penetration testing."

**Response:**  
"In-house testing has a fundamental limitation: familiarity. Your IT team knows the systems intimately—which alerts fire, which patches are pending, where the workarounds are.

Real attackers don't have that knowledge. They approach your environment fresh, looking for what actually works.

We found things at Meridian Health that internal teams had walked past for years—not because they were incompetent, but because you can't see your own environment through an attacker's eyes.

Plus, in-house teams rarely have time to do thorough testing while maintaining operations."

---

## Objection: "We're not a target—nobody would attack us."

**Response:**  
"Healthcare is the #1 targeted industry for ransomware and data theft. Your patient data is worth 10-50x more than financial data on the dark web.

And it's not about being targeted specifically. Attackers use automated tools that scan the entire internet looking for vulnerable systems. You don't need to be Bank of America to get attacked—you just need to have an unpatched Exchange server or weak VPN.

Meridian Health was a mid-sized regional health system. They got attacked because they had patient data and weak security. That describes thousands of organizations."

---

## Objection: "We had a pen test two years ago."

**Response:**  
"Two years is an eternity in security time. Consider what changed at Meridian Health in just 18 months:

- They migrated to Azure cloud
- They deployed a new patient portal
- They acquired two smaller clinics
- They enabled remote work via VPN

Each of those changes introduced new attack surface. Their previous penetration test didn't cover any of it.

We recommend annual testing minimum, plus targeted assessments after major infrastructure changes."

---

## Objection: "We can't afford to be down during testing."

**Response:**  
"We design our testing to minimize operational impact. External testing is passive—no changes to your systems. Internal testing uses read-only techniques by default.

For anything that might cause disruption, we coordinate timing with your team and have emergency stop procedures.

Meridian Health's operations continued uninterrupted during our assessment. We scheduled sensitive tests during off-hours and had immediate escalation contacts."

---

## Objection: "What if you break something during testing?"

**Response:**  
"Professional penetration testing is designed to find vulnerabilities without causing damage. We use proof-of-concept techniques—demonstrating the vulnerability exists without exploiting it destructively.

We also have clear boundaries: nothing gets exfiltrated except small proof-of-concept data samples, nothing gets modified without explicit permission, and we have emergency stop procedures.

In 150+ engagements, we've never caused an unplanned system outage. We plan meticulously and coordinate with your team."

---

## Objection: "Our employees will be upset about the phishing test."

**Response:**  
"That's a common concern, and we handle it carefully.

First: we recommend warning employees that a phishing test will occur "sometime this quarter." This is both ethical and more realistic—real attackers don't announce themselves.

Second: we frame the phishing campaign positively. The goal is training, not punishment. We track improvement over time, not individual failures.

Third: for Meridian Health, we saw something remarkable. After seeing how sophisticated phishing could be, employees became more vigilant. Reports of suspicious emails actually increased. Security awareness became a team sport.

Organizations that handle it well see phishing susceptibility drop 70-90% within a year."

---

## Objection: "We're moving to the cloud soon—let's test after."

**Response:**  
"Moving to the cloud doesn't make you more secure by default. In fact, it often introduces new vulnerabilities until you learn the new platform's security model.

Meridian Health's Azure migration was ongoing when we tested. We found that their cloud configuration had its own issues—overly permissive identities, weak authentication, exposed development environments.

Testing before production deployment is ideal. But testing after—while you still have time to fix findings—is infinitely better than waiting until after a breach."

---

## Objection: "Your competitor is quoting less."

**Response:**  
"I've seen those quotes. Here's the difference:

A basic penetration test might include automated scanning and a vulnerability report. It might find 20 vulnerabilities and take two weeks.

Our red team engagement included:
- 8 weeks of testing across 5 attack vectors
- 6 specialized operators
- Real exploitation, not just scanning
- Attack chain analysis
- Social engineering with 340 targets
- Remediation support and re-testing

You're not paying for a report. You're paying to understand your actual risk and what to do about it. The difference in what we find—and what it prevents—is measured in millions."

---

## Objection: "We need to run this by our legal team."

**Response:**  
"Absolutely. We provide full legal documentation including:
- Statement of work with detailed scope
- Rules of engagement
- Liability limitations
- Professional liability insurance certificates
- Indemnification clauses

Our legal documentation has been reviewed and approved by healthcare organizations' general counsels across the country. We can have our legal team work directly with yours if needed.

Proper legal authorization is essential—it protects both parties and ensures your testing is documented for compliance purposes."

---

## Objection: "What if you find something really bad?"

**Response:**  
"That's exactly what you're paying for. Better to find critical vulnerabilities in a controlled test than have an attacker discover them.

When we find critical issues at Meridian Health, we immediately notify your emergency contact and stop testing that attack path until it's remediated. We don't want to create the very incident we're testing to prevent.

We also provide a preliminary report within 48 hours of finding critical issues. You don't have to wait for the final report to start fixing things."

---

## Objection: "We don't have budget until next fiscal year."

**Response:**  
"Understanding. But consider: the average cost of a healthcare data breach is $10.9M. If a breach occurs before your next fiscal year, that's not a budget problem—that's a existential problem.

We can structure payment across the engagement: 50% to start, 50% upon delivery. That spreads cost across fiscal periods.

Also: cyber insurance policies often cover penetration testing costs. Your policy might already have budget allocated."

---

*These objections represent common concerns. Responses should be adapted to your specific prospect's situation and regulatory environment.*
