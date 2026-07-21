---
name: strava-whoop-integrations
description: Strava and WHOOP third-party integrations — status, rollout gating, Android gap, and roadmap
linear_refs: ["ETA-28", "ETA-562", "ETA-585", "ETA-601", "ETA-614", "ETA-623", "ETA-624", "ETA-625"]
last_updated: 2026-07-08
lifecycle: waxing
---

# Strava & WHOOP Integrations

## Strava

### Current state
Strava integration exists and is **gated by an allowlist** (server-side `strava_allowlist` + `strava_access.mode`). The rollout allowlist currently holds ~5 seeded email addresses. The feature flag (`features.stravaSync.enabled`) controls global access.

**Android gap:** Strava is not yet available on Android (ETA-601 — Backlog, user-reported). The integration appears iOS-only at present.

### What's live
- Strava activity sync
- Strava sessions shown on week view (ETA-583 plan: integrate Strava sessions in week view in chronological order)
- Strava saved routes surfaced in route planning (see route-planning article)

### Roadmap
- **Show progress over time in Strava** (ETA-562 — In Progress): surfacing training progress data via Strava; implementation is in progress as of July 2026
- **Strava MCP ideation** (ETA-585 — Backlog): exploratory — using Strava as an MCP data source
- **PostHog rollout migration** (ETA-607): the email-allowlist-based Strava gating is a candidate for migration to a PostHog cohort/percentage rollout, replacing the manual `strava_allowlist` DB-edit flow

### Blocked item (historic)
ETA-28 ("Strava integration") has been In Review since May 2026 — "Waiting on Strava." This likely refers to Strava API partner approval. The existing integration may be working with approved credentials; ticket may be stale.

---

## WHOOP

### What's live
- **Sync completed gym/strength sessions to WHOOP** (ETA-623 — Done, shipped 2026-07-08): when a rider completes a gym/strength session in Etapa, it is pushed to WHOOP as a workout via the WHOOP API
- **WHOOP integration (ETA-614 — In Review)**: broader integration ticket; details sparse

### Roadmap
- **Whoop morning check-in** (ETA-624 — Todo): pull morning recovery/readiness data from WHOOP to inform the coach's daily guidance
- **User message after activity** (ETA-625 — Todo): send a coach message or prompt after an activity is completed (likely linked to WHOOP recovery data context)

### Decision
Etapa is actively building out the WHOOP integration to close the recovery-data gap that Strava alone can't fill. Gym session sync shipped first; morning readiness check-in is the next logical step.
