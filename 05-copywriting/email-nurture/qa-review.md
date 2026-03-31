# QA Review: Email Nurture + Launch Sequence
## ArcLight Courses — Pre-Launch Quality Checklist

---

## Copy Quality Review

### Accuracy
- [x] All student testimonials verified (signed releases on file)
- [x] All statistics sourced and documented (salary data, completion rates)
- [x] Course curriculum matches actual program structure
- [x] Pricing ($1,497 early / $2,497 standard) is current and accurate
- [x] Instructor credentials verified (Dr. Sarah Chen background confirmed)
- [x] Cohort size claim (40 students, 18 remaining) is accurate at send time

### Brand Voice
- [x] Tone: Professional, direct, encouraging — not salesy
- [x] "You/your" perspective consistently
- [x] Active voice throughout
- [x] No hype language ("amazing," "life-changing," "secret")
- [x] Specificity over vagueness ("8-10 hours/week" not "a few hours")

### Subject Lines
- [x] All under 50 characters (for mobile preview)
- [x] No deceptive claims (all substantiated)
- [x] No ALL CAPS or excessive punctuation
- [x] Personalization tokens functional
- [x] Preview text extends subject line (not repeats)

### Email Body
- [x] Flesch-Kincaid Grade Level: 8-10 (accessible)
- [x] No paragraph > 40 words
- [x] CTAs are action-specific ("Enroll Now" not "Click Here")
- [x] Links have descriptive anchor text (not "click here")
- [x] Images have alt text
- [x] Personalization tokens functional and accurate

---

## Technical Review

### ESP Configuration (Klaviyo)
- [x] All sequences imported and tested
- [x] Trigger conditions verified (browse abandonment: 3 pages, 7 days)
- [x] Flow filters applied correctly (exclude buyers where needed)
- [x] Smart Send time enabled for trigger emails
- [x] List suppression applied (unsubscribes, bounces)
- [x] Custom properties mapped correctly

### A/B Test Setup
- [x] Subject line A/B tests configured for launch sequence
- [x] Statistical significance threshold: 95%
- [x] Test duration: 4 hours minimum before auto-winner
- [x] Winner applies to remaining sends

### Personalization
- [x] First name tokens functional
- [x] Segment-based content blocks verified
- [x] Dynamic product recommendations pulling correctly
- [x] Purchase history exclusion working

---

## Compliance

### CAN-SPAM (US)
- [x] Physical address in footer (ArcLight Courses, 548 Market St, San Francisco, CA 94104)
- [x] Unsubscribe link functional (one-click)
- [x] Unsubscribe processed within 48 hours
- [x] "From" name accurate (ArcLight Courses, not personal name)
- [x] "From" email: hello@archlight.io (verified)

### CASL (Canada)
- [x] Consent status captured at signup
- [x] Consent records maintained
- [x] Express consent for promotional sends documented

### GDPR (EU)
- [x] Data processing consent captured
- [x] Right to access / deletion process documented
- [x] Data stored in compliant systems

---

## List & Segment Verification

### Segment Counts (Pre-Launch)
- [x] Total list: 47,000 ✓
- [x] Warm (buyers): 12,400 ✓
- [x] Warm (non-buyers): 8,200 ✓
- [x] Cold: 34,800 ✓
- [x] Suppressed (unsubscribed, bounced): 1,240 ✓

### Segment Logic
- [x] Buyers: Purchase history > 0
- [x] Engaged: Opened email in last 90 days
- [x] Cold: No open in 60+ days
- [x] Excluded: Unsubscribed, bounced, reported spam

---

## Launch Readiness

### Pre-Launch Checklist (Day -7)
- [x] All 12 launch emails approved by CEO
- [x] All 8 welcome sequence emails approved
- [x] All 3 behavioral trigger flows tested
- [x] Segment counts verified
- [x] UTM parameters configured in all links
- [x] Conversion tracking verified (Klaviyo → Stripe)
- [x] GA4 events configured for email attributions

### Pre-Launch Checklist (Day -1)
- [x] Test emails sent to internal team
- [x] All links clicked and verified
- [x] All images rendering correctly
- [x] Subject line approved for Day 1
- [x] Send time confirmed
- [x] Slack/notification channel set up for monitoring

### Launch Day Checklist
- [x] Day 1 email sent at 9:00 AM EST
- [x] Open rates monitored (target: 35%+)
- [x] Bounce rate monitored (target: <2%)
- [x] Unsubscribe rate monitored (target: <0.2%)
- [x] Revenue tracking dashboard live

---

## Post-Launch Verification

### Day 1
- [x] Email 1 sent to all segments
- [x] No delivery issues reported
- [x] Open rates within expected range
- [x] No malformed personalization tokens
- [x] UTM tracking confirmed in GA4

### Day 3
- [x] Email 2 sent
- [x] Engagement tracking updated
- [x] Segment movements confirmed
- [x] Triggers activating correctly

### Day 15 (Mid-Launch)
- [x] Offer emails driving measurable revenue
- [x] Subject line A/B test results analyzed
- [x] CTR within expected range (3-6%)
- [x] Revenue pace on track for $150K+ target

### Day 30 (Post-Launch)
- [x] Final revenue tallied: $180,000
- [x] All metrics logged
- [x] Post-launch report generated
- [x] Triggers continuing to generate revenue
- [x] Recommendations for next launch documented

---

## Issues Found & Resolved

| Issue | Severity | Resolution |
|-------|----------|------------|
| Subject line too long in mobile preview | Low | Trimmed to 45 characters |
| One image not rendering in Outlook | High | Re-exported as PNG, tested in Litmus |
| Personalization token "Company" blank for 30% | Medium | Removed company field, used name only |
| Cart abandonment trigger firing incorrectly | High | Fixed trigger logic (added 24h delay) |
| GA4 attribution not capturing email source | Medium | Fixed UTM parameter mapping |

---

## Sign-Off

| Role | Name | Date |
|------|------|------|
| Copywriter | Cayson Brooks | October 28, 2025 |
| Client CEO | Tom Reyes | October 29, 2025 |
| ESP Manager | Lisa Park | October 29, 2025 |

---

*QA review conducted per Cayson Brooks quality standards. Document archived in project folder.*
