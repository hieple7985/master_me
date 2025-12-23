# Me-App-03: I-Need (Global-first)
 
 ## One-liner
 Proximity-based Need/Supply matching for events and venues (Android-first), designed to work without relying on Wi‑Fi.
 
 ## Target wedge (fastest path to revenue)
 Event organizers, coworking spaces, campus communities.
 
 ## Problem
 - Attendees want useful connections (help, resources, skills, opportunities) but matching is random.
 - Existing networking tools depend on Wi‑Fi/4G and do not work well in crowded venues.
 - Broadcast channels become spam without strong consent and trust.
 
 ## Solution
 Users create a short Need/Supply card (tags + one line). The app discovers nearby matches via Bluetooth and requires mutual consent before starting a conversation. Venues can run a verified “Venue Mode” session.
 
 ## Core product principles
 - Mutual consent by default.
 - Anti-spam first (rate limits, blocks, venue verification).
 - Offline-first experience at the venue; optional sync when online.
 
 ## MVP (Android-first)
 - Venue session join via Event QR (Venue Code).
 - Need/Supply cards:
   - pre-defined tags
   - optional one-line description
 - Nearby discovery using BLE (foreground-first for stability).
 - Match flow:
   - mutual accept
   - optional QR/NFC confirm handshake
 - Conversation (idea-only) or “contact exchange” after accept.
 - Anti-abuse:
   - rate limiting
   - block/report
   - no public broadcast wall in MVP

 ## Conversation scope (idea-only)
 The in-app “chat” is intentionally limited. It is not a messenger.
 - Allowed:
   - clarify the Need/Supply
   - agree on a quick next action
   - share contact optionally
 - Not building in MVP:
   - long chat history across days
   - media sharing
   - group chat
   - public channels
   - message forwarding

 ## Lightweight alternatives to full chat (recommended)
 - Quick replies (one-tap):
   - “I can help”
   - “I have this”
   - “Where are you?”
   - “Meet now”
   - “Not available”
 - Meet-now flow:
   - show a short-lived “meet code” or simple landmark prompt
   - optional countdown (e.g., 10 minutes)
 - Contact exchange (optional, after mutual accept):
   - share Telegram/WhatsApp/Email handle
   - share QR contact card
 - Auto-expiry:
   - conversations expire at the end of the venue session (hard cap: 12 hours)
   - keep only aggregated metrics for the venue report

 ## Minimal production requirements (even with idea-only chat)
 - Reliable mutual consent state machine (no ghost requests)
 - Rate limiting per device/session
 - Block/report that actually prevents re-contact
 - Session scoping (users only discover/match within a Venue Code)
 - Observability for pilots:
   - activation
   - match created
   - accept
   - quick reply sent
   - contact shared
 
 ## What NOT to build in MVP
 - Payments / escrow / dispute resolution.
 - Open public feed of nearby posts.
 - Fully automatic matching without consent.
 
 ## Pricing (early revenue)
 - Pilot (per event): $300–$1,500
 - Venue monthly (coworking/community): $200–$1,000/mo
 - Add-ons: on-site support, white-label branding, advanced reporting
 
 ## Success metrics (for pilots)
 - Activation: % users who create a card within 2 minutes.
 - Match rate: matches per 100 attendees per hour.
 - Helpful connection rate: % matches rated “useful”.
 
 ## Go-to-market (Global-first, cold outreach)
 Focus on places with high density and recurring events.
 
 ### Lead sources
 - Meetup.com (organizers)
 - Eventbrite (organizers)
 - LinkedIn (Event Manager, Community Manager, Partnerships)
 - Google Maps (coworking spaces, venues)
 
 ### CRM (simple spreadsheet)
 Columns:
 - Lead name
 - Type (event / coworking / agency / venue)
 - Channel (LinkedIn / email / Instagram / website)
 - Contact
 - Status (new / contacted / replied / call booked / proposal / won / lost)
 - Next step date
 - Notes
 - Pricing offered
 
 ### 2-week outreach cadence
 - Daily: 30–50 outreach messages
 - Week 1 targets:
   - 200–300 outreaches
   - 10–15 replies
   - 3–5 calls
 - Week 2 target:
   - 1 paid pilot
 
 ## Cold outreach templates (English)
 
 ### 1) Meetup / workshop organizer
 Hi {Name} — I saw you’re organizing {Event} on {Date}.
 We’re building an Android-first “proximity matching” tool that helps attendees match Need/Supply (help, resources, skills) on-site without relying on venue Wi‑Fi.
 Would you be open to a 15-min demo? We can run a paid pilot for {Event} and provide a post-event connection report.
 
 ### 2) Coworking / community manager
 Hi {Name} — coworking communities often have members who can help each other, but they don’t always meet the right people.
 We built a Venue Mode that lets members match Need/Supply on-site (Android-first) with mutual consent to avoid spam.
 Can I show you a 5-min demo and propose a small monthly pilot?
 
 ### 3) Event agency / production company
 Hi {Name} — we’re building a plug-in “engagement layer” for events: on-site Need/Supply matching + a post-event report.
 If you’re interested, we can discuss a pilot + a referral/white-label model.
 Are you available for a 15-min call this week?
 
 ### 4) Risk-reversal close (refund)
 If we run a pilot and don’t hit the success criteria we define together (activation + helpful matches), we’ll refund the pilot fee.
 
 ## Open source strategy (recommended)
 - Short term (0–6 weeks): keep focus on execution and pilots; do not open-source yet.
 - After first successful pilots:
   - open-source the protocol spec (how cards/handshakes are exchanged)
   - optionally open parts of the Android client
   - keep commercial moat closed: venue console, verification, analytics, anti-abuse tooling

 ## Chosen GTM wedge (do this first)
 Meetup/workshops with 50–300 attendees (Global-first).

 ## Default outbound settings (picked)
 - Region to start: Singapore (English-first), then expand to London and NYC
 - Target event size: 50–300 attendees
 - Pilot price to start: $500 per event
 - Payment terms: 50% upfront, 50% after the post-event report
 - Refund policy: 100% refund if we miss the agreed minimum success criteria

 ## 60-second pitch script (English)
 Hi [Name], I’m [Your Name]. I saw you’re running [Event Name] and I’m reaching out with a simple way to make networking more useful without relying on venue Wi‑Fi.
 
 We built an Android-first “proximity matching” tool where attendees create a short Need/Supply card (help, resources, skills, opportunities). The app detects nearby matches via Bluetooth and only opens a conversation after mutual consent, so it doesn’t become spam.
 
 For organizers, we run it as a Venue Mode session via a simple Event QR code, and after the event you get a lightweight report: activation rate, match rate, and how many connections were rated useful.
 
 I’d love to show you a 5-minute demo. If it’s a fit, we can run a paid pilot for your event for $500, with a full refund if we don’t hit the success criteria we define together. Would you have 15 minutes this week?

 ### Filled example (Singapore)
 Hi Alex, I’m Hiep. I saw you’re running the “AI Builders Meetup” in Singapore and I’m reaching out with a simple way to make networking more useful without relying on venue Wi‑Fi.
 
 We built an Android-first proximity matching tool where attendees create a short Need/Supply card (help, resources, skills, opportunities). The app detects nearby matches via Bluetooth and only opens a conversation after mutual consent, so it doesn’t become spam.
 
 For organizers, we run it as a Venue Mode session via a simple Event QR code, and after the event you get a lightweight report: activation rate, match rate, and how many connections were rated useful.
 
 I’d love to show you a 5-minute demo. If it’s a fit, we can run a paid pilot for $500, with a full refund if we miss the agreed minimum success criteria. Would you have 15 minutes this week?

 ## Pilot proposal template (copy/paste)
 ### Summary (filled default)
 We will run I-Need Venue Mode for an on-site meetup/workshop (50–300 attendees) to increase useful attendee connections without relying on Wi‑Fi.
 
 ### Scope
 - Android-first attendee experience
 - Join via Event QR (Venue Code)
 - Create Need/Supply card (tags + one line)
 - Nearby matching (BLE) with mutual accept
 - Post-event report
 
 ### Organizer requirements
 - Organizer shares Event QR on-site (projector/print/table tent)
 - A 30-minute setup call 1–3 days before the event
 
 ### Pricing (filled default)
 - Pilot fee: $500
 - Payment terms: 50% upfront, 50% after the post-event report
 
 ### Success criteria (filled default)
 - Activation rate: at least 35% of attendees create a card within 2 minutes
 - Match rate: at least 10 matches per 100 attendees per hour
 - Helpful connection rate: at least 25% of matches rated useful
 
 ### Refund clause (filled default)
 If we do not achieve the minimum success criteria above, we refund 100% of the pilot fee within 7 days.
 
 ### Data and privacy
 - We collect only what’s needed to operate the pilot and produce aggregated metrics.
 - No public broadcast wall; mutual consent required to connect.

 ## Week-1 outbound checklist (Global-first)
 ### Day 1
 - Build the lead sheet template (CRM columns above)
 - Collect 50 Meetup/Eventbrite leads in 1 city/topic
 - Send 30–50 messages (LinkedIn + email + event contact forms)
 
 ### Day 2
 - Collect 50 more leads
 - Send 30–50 messages
 - Follow up on all opens/replies within 12 hours
 
 ### Day 3
 - Collect 50 more leads
 - Send 30–50 messages
 - Book at least 1 call (offer 2 time slots)
 
 ### Day 4
 - Run 1–2 demos
 - Send proposal template to warmest leads
 - Collect 50 more leads
 
 ### Day 5
 - Follow up + close pilot with risk-reversal (refund)
 - Confirm event date, expected attendance, and success criteria
 
 ### Week-1 KPI targets
 - 200–250 total outreaches
 - 10–15 replies
 - 3–5 calls booked
 - 1 proposal sent to “hot” lead

 ## Name check: “I-Need”
 It’s understandable and on-theme, but it has brand risks:
 - It can read as generic and be hard to trademark/SEO.
 - It may be confused with “I need” as a phrase in search queries.
 
 If you keep it, consider using a stronger product descriptor in the tagline, e.g.:
 - I-Need Venue Mode
 - I-Need Nearby Matching
 
 Backup name directions (more brandable):
 - NeedNearby
 - MatchNeed
 - ProxiNeed
 - NeedLink
 
 Validation checklist (do before committing):
 - App Store / Play Store search for “I-Need” and close variants
 - Domain availability (prefer .com) and social handles
 - Trademark search in your target markets