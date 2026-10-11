# Saffron: Designing Calm, Transparent Order Tracking

*UX case study: post-order experience for a food delivery platform. October 2026. Evidence base: nine high-fidelity screens (S1, S3, S4, S6, S7, S10, S12, S13, S14).*

## 1. Executive Summary

**Problem.** After checkout, the user hands control to a restaurant and a rider. The dominant emotion is *anxiety under uncertainty*, not hunger. Most tracking screens answer "where is it?" but not "will it be late, why, and what can I do?"

**Solution.** Saffron's tracking flow combines a six-stage progress model, a *confidence-labelled ETA*, a traffic-aware route, rider-contact shortcuts, and a distinctive **"Let's wait here" calm space** that turns dead waiting time into a low-stress, occupied experience.

**Outcome targets (hypotheses to validate, not measured results):** fewer "Where is my order?" support contacts, fewer rider calls, higher post-delivery CSAT, and higher in-wait engagement with re-order surfaces.

## 2. Research and Key Insights

*Transparency note: no primary interview data was supplied with these files. The findings below draw on established UX and behavioural-psychology literature plus heuristic review of the screens. A primary-research plan is in Section 9.*

### 2.1 Theoretical foundations

| Principle | Source | Implication for tracking |
| --- | --- | --- |
| Visibility of system status | Nielsen's 10 Heuristics | Users must always see current state and next state |
| Occupied time feels shorter than unoccupied time | Maister, *The Psychology of Waiting Lines* | Give users something to do or look at while waiting |
| Uncertain waits feel longer than known, finite waits | Maister | A single ETA number is not enough; show certainty of the ETA |
| Goal-gradient effect | Hull / Kivetz et al. | Progress steppers raise motivation and patience as the end nears |
| Peak-end rule | Kahneman | The arrival moment disproportionately shapes the overall rating |
| Hick's law and Fitts's law | HCI fundamentals | Few, large, thumb-reachable actions at stressful moments |
| Anxiety reduction via control | Locus-of-control research | Offer actions (call, add note, report), not just information |

### 2.2 Key insights

1. **Anxiety peaks in three windows:** right after payment ("did it go through?"), mid-journey ("is it late?"), and at the doorstep ("where is the rider, how do I hand off safely?").
2. **Precision without confidence erodes trust.** A bare "18 min" that silently changes to "25 min" feels like a broken promise. Users trust *honest ranges and certainty signals*.
3. **Delay tolerance depends on explanation.** Users forgive late orders more when told *why* and *by how much*, and when offered choices.
4. **Repeated checking is a symptom of poor reassurance.** Users reopen the app, call the rider, or contact support when the screen does not settle their mind.
5. **Waiting is an engagement opportunity,** but only if it does not feel like upselling during a stressful moment.
6. **Doorstep handoff is a safety and trust moment** (delivery PIN, instructions, rider identity).

### 2.3 Competitive gap analysis (category patterns, qualitative)

| Capability | Typical category pattern | Saffron approach |
| --- | --- | --- |
| ETA | Single number | ETA + confidence badge (S6) |
| Delay explanation | Often a generic banner | Dedicated delay state with cause, impact, options (Section 4.4, proposed) |
| Waiting experience | Static map | Calm space and browse-while-waiting (S4, S7, S8) |
| Arrival | Push notification | Ambient "arriving soon" screen and a dedicated Arriving Now state (S10, S14) |
| Rider trust | Name and phone | Rating, plate number, PIN, delivery instruction (S14) |

## 3. Design Goals and Success Metrics

| Goal | Metric (to instrument) |
| --- | --- |
| Reduce anxiety | Post-order anxiety score (1 to 5 pulse), "Where is my order?" contact rate |
| Increase transparency | ETA accuracy (MAE), % sessions viewing live map |
| Support decisions in delays | Delay-state action rate (wait / note / contact), cancellation-after-delay rate |
| Enhance delight | Calm-space entry rate and dwell time, CSAT, repeat order within 7 days |

## 4. Proposed Solution

### 4.1 End-to-end journey (mapped to screens)

1. **Cart (S3):** review items, tax and fees, delivery, total, then Checkout.
2. **Payment success (S4):** confirmation, order summary, delivery address, live tracking status, primary CTA "Track my order".
3. **Tracking with exploration (S6):** the map sits behind a draggable sheet. A secondary layer lets users browse best sellers and offers while waiting.
4. **Ambient arrival teaser (S7):** "Your order will arrive soon. Tap anywhere to view live tracking."
5. **Core tracking (S10):** map, stepper, ETA, confidence, rider, order details, notes, safety.
6. **Calm-space entry (S12):** contextual chip "Let's wait here".
7. **Calm space (S13):** soothing games, shown as a coming-soon state.
8. **Arriving now (S14):** doorstep handoff state with PIN and instructions.

*Home (S1) anchors the mental model: persistent bottom navigation, cart and history icons in the header, and a personalised greeting.*

### 4.2 Core tracking screen anatomy (S10)

- **Live map (top \~33%):** traffic-aware dashed route, rider marker, restaurant and home pins, a LIVE indicator, and a legend chip with green, amber, red traffic dots.
- **Six-stage stepper:** Confirmed, Preparing, Picked up, On the way, Arriving, Delivered. Completed steps use check icons, the current step a filled node, future steps muted.
- **ETA block:** "ARRIVING IN 18 min" with a **High confidence** badge.
- **Real-time activity card:** "Aarav is on the way, View live updates", with expandable detail.
- **Action row:** Call Aarav (photo, rating 4.9), View order details (2 items, ₹684).
- **Full-width CTA:** "Add note for rider".
- **Utility row:** Share live tracking, Emergency help, Report an issue.
- **Bottom sheet:** "Go to home page", a graceful exit that preserves the live order.

### 4.3 Unique selling propositions

**USP 1: "Let's wait here" calm space (S12, S13).** The product treats waiting as an experience to design, not a gap to fill with ads. When the ETA is stable, a gentle floating chip appears (a pulsing audio-bar icon and the copy "A calm little space while Aarav gets closer"). It opens a soothing, low-stimulation mini-game space in a cool blue palette that contrasts with the warm orange of commerce. This applies Maister's *occupied time* principle while deliberately avoiding high-arousal gamification.

**USP 2: Confidence-labelled ETA (S10).** The ETA carries a certainty indicator ("High confidence"). Proposed tiers: High (±2 min), Medium (±5 min), Low (range display). This makes ETA uncertainty legible instead of hidden.

**USP 3: Ambient arrival choreography (S7, S14).** A full-screen "Your order will arrive soon" state and an Arriving Now state with a PIN and instruction recap move the app from monitoring to handoff readiness.

**USP 4: Browse-while-waiting layer (S6).** A "While your order is on the way" sheet repurposes dwell time for discovery (best sellers, offers, recommendations) without covering the live ETA, because the sheet header persists with "Arriving in 18 min".

### 4.4 Delay handling (proposed extension)

The supplied screens show on-time states. The brief explicitly requires delay comprehension and decisions, so the following state is specified to complete the system:

| Element | Specification |
| --- | --- |
| Trigger | Predicted ETA exceeds promised ETA by 5 minutes or more |
| Header | ETA turns amber; badge changes from High to Medium or Low confidence |
| Cause chip | Plain-language cause: "Heavy traffic on Old Madras Rd" or "Kitchen is busy" |
| Impact line | "+7 min. New arrival 8:45 pm" |
| Options (max 3) | **Keep waiting** (default), **Add a thank-you note or tip**, **Get help or cancel** with refund eligibility shown upfront |
| Compensation | Auto-applied credit disclosed before the user must ask |
| Stepper | Active node shows an amber ring; the stage that caused the delay is labelled |

The rule is that *every delay message answers three questions: why, how long, what can I do.*

## 5. Layout and Design Rationale

| Decision | Rationale | Evidence |
| --- | --- | --- |
| Map on top, sheet below | The map gives instant spatial reassurance; the sheet carries detail without leaving context | S10 |
| ETA as the largest text on the sheet | Highest-value information gets the highest visual hierarchy (Gestalt: figure/ground) | "18 min" in S10 |
| Stepper placed above the ETA | Gives macro-context (stage) before micro-context (minutes); supports the goal-gradient effect | S10, S14 |
| Large rounded cards and 44px+ touch targets | Fitts's law; one-handed use | Call and Note actions in S10 |
| Warm orange for commerce and action, green for success and status, cool blue for calm | Colour carries semantic meaning; the blue shift signals a mental mode change | S4 vs S13 |
| Two primary actions only on the doorstep screen | Hick's law under time pressure | "Call Aarav" CTA in S14 |
| Delivery PIN with explicit instruction "Share it only after receiving your order" | Prevents fraud and sets expectations | S14 |
| Rider identity (photo, name, rating, plate) | Builds trust and enables recognition at the door | S14 |
| Bottom sheet exit "Go to home page" | Non-destructive navigation; the order stays live | S10, S12, S13 |
| Consistent bottom-nav on home; single focused CTA on confirmation | Navigation when browsing, focus when transacting | S1, S4 |
| Typographic system: bold geometric sans for headlines, lighter weight for support text, uppercase tracked micro-labels | Clear scan paths and tonal hierarchy | "PAYMENT CONFIRMED", "ARRIVING IN" |

**Accessibility considerations:** colour is never the only carrier of meaning (stepper uses icons plus labels; traffic legend pairs colour with text "Traffic-aware route"); recommended minimum 4.5:1 contrast for body text; dynamic type support; VoiceOver and TalkBack labels such as "Step 4 of 6: On the way".

## 6. Micro-interactions

| # | Trigger | Behaviour | Purpose |
| --- | --- | --- | --- |
| 1 | Payment confirmed | Check icon scales in with a ring pulse; haptic *success* | Instant, bodily reassurance |
| 2 | Rider location update | Marker glides with eased interpolation along the route; no jumping | Preserves trust in "live" data |
| 3 | Rider marker idle | Soft radial pulse halo around the marker (visible in S12) | Signals real-time liveness |
| 4 | Stepper advance | Connector line fills left to right; node morphs from filled dot to check | Progress and goal-gradient reward |
| 5 | ETA change | Digits roll (odometer effect) and the confidence badge cross-fades | Draws attention to change without alarm |
| 6 | "Let's wait here" chip | Slides in from the left after ETA is stable for 30 seconds; the bars icon gently oscillates | Non-intrusive invitation |
| 7 | Calm-space open | Card expands from the chip with shared-element transition; the palette cross-fades warm to cool; the map softens behind it | Mode shift to calm |
| 8 | Sheet drag | Spring physics with a drag handle; rubber-banding at limits | Natural, controllable depth |
| 9 | Arriving soon screen | Three dots animate in a staggered breathing loop; tap anywhere to dismiss | Anticipation and easy exit |
| 10 | Arriving now | Haptic *notification*; the home pin pulses; the CTA is auto-promoted | Prompts the handoff |
| 11 | Real-time activity card chevron | Accordion expands with an ease-out curve | Progressive disclosure |
| 12 | Add note | Bottom sheet with quick-reply chips such as "Leave at the door" and "Call on arrival" | Faster than typing |

**Motion principles:** 200 to 300 ms for UI, 400 to 600 ms for emotional moments; ease-out for entrances, ease-in for exits; respect the *Reduce Motion* system setting.

## 7. High-Fidelity Screens

The nine screens supplied constitute the high-fidelity deliverable. Each is summarised with its UX purpose:

| ID | Screen | Purpose | Key UI evidence |
| --- | --- | --- | --- |
| S1 | Home | Discovery, entry to cart and history | Greeting "Good evening, Maya"; category chips; Best sellers; 30% OFF banner; "Recommended for you" |
| S3 | Cart | Pre-payment review | Quantity steppers, delivery slot "Today · 20:10", cost breakdown, lime "Checkout" CTA |
| S4 | Payment success | Close the transaction loop | "PAYMENT CONFIRMED", Order #SF2841, "On time" tag, address, "Track my order" |
| S6 | Track with explore | Use waiting time for discovery | "Slide down to track your order", "Arriving in 18 min", "Explore more while waiting" |
| S7 | Ambient arrival | Anticipation, minimal UI | "Your order will arrive soon" with "TAP ANYWHERE TO VIEW LIVE TRACKING" |
| S10 | Core tracking | Primary status screen | Stepper, ETA, High confidence, rider card, safety row |
| S12 | Tracking with wait chip | Contextual USP entry | "Let's wait here" chip over the utility row |
| S13 | Calm space | USP experience | "Soothing games coming soon" |
| S14 | Arriving now | Doorstep handoff | "Aarav has reached your building", delivery PIN 7392, "Leave at the door, please" |

## 8. Design QA Findings (Honest Audit)

Before handoff, these inconsistencies in the supplied screens should be resolved:

1. **Status bar overlap in S10 and S12.** The system time and 5G icons render on top of the "Confirmed" timeline labels. Apply a safe-area inset and move the stepper below it.
2. **Cart arithmetic in S3.** Mango lassi (₹120) at quantity 2 plus Broccoli lasagna (₹340) should sum to ₹580, but the subtotal shows ₹460, which only matches quantity 1. Fix either the quantity or the subtotal.
3. **Order continuity between S3 and S4.** The cart contains lassi and lasagna totalling ₹551, whereas the confirmation shows Chicken biryani and Raita from Dum Pukht Kitchen at ₹684. Use one consistent order dataset across the prototype.
4. **Content mismatch on S1.** "Masala idli" and "Paneer bowl" are labelled over a spring-roll and a sushi photo; "Berry toast" over lasagna. Align imagery with names for credibility.
5. **Placeholder state in S13.** "Soothing games coming soon" should be replaced by at least one working interaction (for example, a breathing orb or pebble-sorting game) before usability testing.
6. **Delay state absent** from the screen set (specified in Section 4.4; should be designed).
7. **Redundant ETA** in S10: "18 min" appears twice (headline and activity card). Keep one or differentiate (for example, show the clock time "8:38 pm").
8. **Header text on S14:** the helper line ("After delivery, you can view the proof photo…") sits tightly under the CTA; add spacing.

## 9. Validation Plan

| Method | Sample | Measure |
| --- | --- | --- |
| Moderated usability test (prototype) | 8 to 10 delivery users in Bangalore, Mumbai and Delhi NCR | Task success: find ETA, call rider, add a note, respond to a delay |
| Five-second test on S10 | 30 participants | Recall of ETA and stage |
| A/B test: confidence badge vs plain ETA | Live traffic, 2 weeks | Contact rate, CSAT |
| A/B test: calm chip vs none | Live traffic | Chip tap rate, dwell, re-order rate, any anxiety pulse score |
| Diary and survey study | 20 users | Emotional curve through the wait |
| Accessibility audit | WCAG 2.2 AA | Contrast, target size, screen reader order |

## 10. Risks and Mitigations

- **ETA confidence mislabelled:** calibrate against historical accuracy; display "High" only when error band is historically under 2 minutes.
- **Calm space seen as a gimmick:** ship one meaningful activity first; gate behind an opt-in tap, never auto-open.
- **Browse-while-waiting feels pushy:** keep it below the fold of the ETA; suppress it during delay states.
- **Battery and data use from live maps:** throttle updates when the app is backgrounded; use Live Activities and lock-screen widgets.

## 11. Technical Notes

- **Real-time layer:** WebSocket or server-sent events for rider location (every 3 to 5 s), with a fallback to polling.
- **ETA model:** blend of kitchen prep prediction, rider routing (traffic-aware), and historical variance, which yields both ETA and the confidence interval.
- **State machine:** `confirmed → preparing → picked_up → on_the_way → arriving → delivered`, plus a `delayed` modifier flag rather than a separate stage.
- **Platform integration:** iOS Live Activities and Android ongoing notifications mirroring the stepper and ETA.
- **Security:** delivery PIN generated per order, rate-limited verification, masked rider phone through a proxy number.

## 12. Conclusion

Saffron's tracking experience treats the wait as a designed experience: *clear status, honest certainty, a calm place to spend the time, and a safe, well-prepared handoff*. The confidence-labelled ETA and the "Let's wait here" calm space together form a defensible differentiator because they address the emotion behind the wait, not just its duration. Resolving the audit items in Section 8 and completing the delay state would make the system ready for usability validation and engineering handoff.
