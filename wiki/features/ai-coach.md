---
name: ai-coach
description: "AI coach chat \u2014 quality flags, cross-activity session creation,\
  \ coach persona, weekly check-in, and skills roadmap"
linear_refs:
- ETA-560
- ETA-572
- ETA-593
- ETA-617
- ETA-621
- ETA-625
last_updated: 2026-07-06
---

# AI Coach

## Overview

Etapa surfaces an AI coach (named personas e.g. "Sophie") via a chat interface (`coach_chat` surface). The coach can answer training questions, adjust the plan, and (roadmap) create new session types.

## Quality flag — wrong information (ETA-621 — Done)

A user-flagged response was filed: the coach gave incorrect information about a user's schedule (cited a "standing adventure ride" that apparently wasn't scheduled for that day). Ticket closed as Done.

**Implication:** The coach relies on plan context passed at prompt time. Incorrect context → incorrect advice. Monitoring of AI flags should be ongoing; each flag surfaces on the admin dashboard.

## Cross-activity type sessions (ETA-560 — In Review)

Riders should be able to request non-cycling sessions through coach chat — e.g. "give me a 30-minute swim on this day" — and have that activity created and appear in the weekly calendar view. Currently the app supports multiple activity types in the plan but the coach chat may not be able to create them dynamically.

## Coach notes caching (ETA-572 — In Review)

Coach notes are regenerated on every activity load, burning LLM tokens and adding latency. **Fix:** generate once, store server-side, allow manual regeneration. This is both a cost and a UX issue.

## Weekly check-in (ETA-593 — In Review)

Weekly check-in feature. No detail in ticket; likely a recurring coach-initiated prompt asking about the week's training, fatigue, and adjustments.

## Post-activity messaging (ETA-625 — Todo)

Send a coach message or prompt after a rider completes an activity. Details sparse; likely connects to WHOOP recovery data when available.

## Skills — plan review skill (ETA-617 — Backlog)

Build a skill to check people's plans (proactively review training plans). No detail on what "checking" entails — may mean quality-checking generated plans for overtraining, rest day balance, etc.

## Principle

Coach responses depend entirely on the plan context injected at prompt time. Any discrepancy between the coach's stated facts and the actual plan is a context-injection bug, not a model hallucination. Priority fix: ensure plan context passed to coach is always fresh and accurate.

## Superseded — coach as companion (ETA-459 — Canceled)

An earlier concept: the coach would proactively expand the rider's horizons during weekly check-ins — suggesting new goals, events, communities, and YouTube/Instagram inspiration. This was **canceled**. Weekly check-in (ETA-593) and post-activity messaging (ETA-625) remain but are narrower — focused on training adjustment, not content curation.
