---
name: route-planning
description: Route planning feature — single-day ride routes, AI generation, GPX, Strava saved routes, Trailforks MTB, and training plan integration
linear_refs: ["ETA-604", "ETA-606", "ETA-607", "ETA-615", "ETA-616", "ETA-603"]
last_updated: 2026-07-09
lifecycle: waxing
---

# Route Planning

## Status

Route planning shipped for multi-day bikepacking trips (Done — ETA-606). Single-day ride route planning is the current expansion. The underlying server infrastructure (BRouter for OSM-based road/gravel/MTB snapping) landed in PR #196. Trailforks MTB trail discovery is built but blocked on partner API credentials.

## What's done (ETA-606 — Done)

The full route planning spec has shipped:

- **Route search and discovery**: riders describe distance/time, start point, difficulty; generates 3–5 valid cycling routes shown on map
- **Auto-population from training sessions**: when opened from a session, distance, intensity, and location are pre-filled
- **Strava saved routes**: riders with Strava connected can see their saved Strava routes alongside Etapa-generated routes
- **AI route generation**: Claude-backed generation from current/specified start point; respects surface type, distance, difficulty; supports waypoint adjustment
- **Training plan integration**: from a scheduled session, rider taps to find/generate a matching route; session duration and intensity inform suggested distance and difficulty
- **Surface types**: road, gravel, MTB/trail
- **Difficulty levels**: aligned to rider level model (beginner, intermediate, advanced)
- **GPX import**: upload a GPX file to attach a route; app extracts track and surface breakdown
- **GPX export**: export any saved route via native share sheet (extends existing multi-day trip export)
- **Admin observability**: `route_searches` table logs searches; `GET /api/admin/route-searches` endpoint; visible in user detail Searches tab and top-level Routes admin page
- **Feature flag**: route planning gated behind `route-planning-enabled` PostHog flag; initial rollout to internal users

## Route data sources

- **GraphHopper or BRouter** (OSM-based, cycling-surface-aware): recommended for route generation — both self-hostable. BRouter confirmed in PR #196.
- **Strava saved routes**: surfaces user's own routes
- **bikepacking.com** (ETA-604 — In Review): display bikepacking.com routes, link to correct page — basic integration, details sparse

## Trailforks MTB (ETA-615 — Backlog, blocked)

A ready-to-enable server adapter exists (`server/src/lib/trailforks.js`, `GET /api/route-planning/mtb-trails`) but returns 503 without credentials.

**Blocker:** Trailforks uses a gated partner API — requires application + approval + commercial licensing + attribution ("Powered by Trailforks" required, link back, data licence).

**Remaining work once credentials obtained:**
1. Apply for Trailforks partner API access (App ID + Secret)
2. Set env vars on Railway (`TRAILFORKS_APP_ID`, `TRAILFORKS_APP_SECRET`)
3. Verify request shape + field names against live response
4. Add harness mock and route test
5. Wire MTB surface path: prefer real Trailforks trails, fall back to BRouter when no trail data
6. Client UI with required "Powered by Trailforks" attribution
7. Legal sign-off on data licence

**Legal consideration:** Trailforks data licensing may restrict storing/redistributing trail geometry — confirm cache vs live-fetch before building UI. Ties into broader legal review (see ETA-588).

## Saved trip map view (ETA-603 — In Review)

Saved trip view should show a map. No further detail in ticket.

## Open IA question

Route planning lives in a tab currently labelled "Goals." ETA-606 flags that as the tab grows to cover goals, events, trips, and routes, renaming it to "Planning" (or similar) may be warranted. **Decision not yet made.**

## Success metrics

- Routes saved per active user per week
- % of training sessions with a route attached
- Route-to-ride completion rate (sessions with route vs. sessions marked complete)
