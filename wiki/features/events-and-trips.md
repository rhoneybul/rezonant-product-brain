---
name: events-and-trips
description: Events and trips — website events page, event-triggered plan generation, event readiness tracking, and traffic acquisition
linear_refs: ["ETA-550", "ETA-584", "ETA-603", "ETA-605", "ETA-626", "ETA-627"]
last_updated: 2026-07-09
source_refs: ["sources/sessions/b2685f82-c4fd-4bad-a406-c36a3afa4b95.md"]
---

# Events and Trips

## Events on the website (ETA-584 — In Review)

Known issues / improvements flagged:
- Include cross-training events (not just pure cycling) — cycling can be used as part of the training
- Filter bug: selecting "UK" still shows European events
- Make all event/trip cards the same height; reduce image size
- "Show more" button: only show if there are actually more events, and add a loading indicator during refresh

## Drive traffic to events page (ETA-550 — In Review)

Acquisition levers under consideration: SEO, AEO (Answer Engine Optimisation), Google Ads.

## Event-triggered plan generation (ETA-627 — Backlog)

**User story:** A visitor browsing events should be able to trigger plan generation from an event, to explore what training for it would look like.

**Acceptance criteria:**
- Each event card on `events.html` has an active "Build a training plan" button (currently exists but wired to nothing — activate it)
- "Get your guide with Etapa" CTA on individual `event.html` pages opens the same plan config flow (currently marked "coming soon" — remove disabled state and wire up)
- Both CTAs open a modal overlay without navigating away from the page
- Modal shows event name, date, and discipline pre-filled
- Modal is mobile-responsive (375px+ viewport)

This is a key acquisition loop: visitor sees an event they care about → immediately sees what training looks like → converts to account.

## Event readiness tracking (ETA-626 — Backlog / Maybe Later)

**Concept:** Based on sessions completed and the training plan, show riders a score of how "event ready" they are.

**Triage outcome (session b2685f82):** Assessed via the /maybe-later skill. Assessment: good idea, natural fit — but requires a defined readiness metric, session-completion + Strava data aggregation against the plan, event association, and new UI. Moved to Backlog with rationale recorded. Not being actively built.

**Dependencies when prioritised:** plan overview (ETA-583), Strava activity progress (ETA-562), events/trips infrastructure.

## Drop-off analysis (ETA-605 — In Review)

Track where users are dropping off or not fully engaging with features. No specific tooling decision recorded.
