---
name: infrastructure-and-ops
description: Infrastructure and ops — feature flags, PostHog migration, admin dashboard, Sentry, version tracking, testing, and maintenance
linear_refs: ["ETA-455", "ETA-488", "ETA-494", "ETA-496", "ETA-497", "ETA-517", "ETA-590", "ETA-595", "ETA-596", "ETA-607"]
last_updated: 2026-07-09
---

# Infrastructure and Operations

## Feature flags (ETA-607 — Backlog)

**Current state:** Feature flags and remote config share one mechanism — the admin dashboard writes JSON to Supabase `reference.app_config`, merged server-side and consumed by `src/services/remoteConfig.js`.

**Proposed migration:** Move true on/off toggles (Group A: `features.*`) and the Strava allowlist rollout (Group B) to PostHog boolean flags / cohorts. Keep config *values* (pricing, copy, maintenance mode — Group D) and per-user entitlement overrides (Group C) in Supabase.

**Why PostHog for A/B:** PostHog SDK already integrated (`analyticsService.js`). Adds percentage rollouts and cohort targeting that the current dashboard can't do. PostHog free tier covers up to 1M events/month.

**Key constraints:**
- Offline-first contract must be preserved — `remoteConfig` is cache-first with synchronous fallbacks; PostHog RN SDK has local caching but must be bootstrapped to match
- Old store builds still read `features.*` and `stravaAllowed` from `/api/app-config` — dual-write/ramp required; server keeps emitting legacy flags indefinitely for old clients
- Server-side Strava gating: decide whether server calls PostHog SDK (keeps single `stravaAllowed` boolean on wire) or client evaluates directly

**Phasing:**
1. Define 5 Group A flags + Strava rollout flag in PostHog; shadow-only; compare against `app_config`
2. Flip `remoteConfig.getBool` to PostHog-first, `app_config` as fallback
3. Move Strava gating to PostHog cohort; retire allowlist edit path

**Admin UX impact:** Group A/B flag editing moves from `/dashboard/config` to PostHog UI.

## Admin dashboard

- **Impersonation** (ETA-517 — Backlog): admin functionality to impersonate any user account (for support/debugging)
- **App feedback into Slack** (ETA-494 — Backlog): route in-app feedback (currently a separate flow) into Slack for the team
- **Feature flags admin page** (ETA-607): see above

## Observability

- **Sentry** (ETA-496 — In Review): Sentry error tracking setup/configuration
- **Track app version** (ETA-497 — In Review): track which app version each user is on (important for managing old-client backward compat during rollouts)
- **Set up Rezonant** (ETA-488 — Backlog): Rezonant integration (product brain / ops tooling)

## Testing

- **E2E testing** (ETA-455 — Backlog): end-to-end test coverage
- **Penetration testing** (ETA-590 — Todo): Dark Moon penetration testing engagement — not yet started
- **Testing** (ETA-596 — Backlog): general test coverage; mentions test harness and per-CLAUDE.md testing rules

## Connectivity

- **Internet connection / no internet banner** (ETA-483, ETA-571 — In Review): show a banner when the device has no internet connection. Two tickets covering the same feature — likely one is original, one a follow-up.

## Maintenance

- **Maintenance** (ETA-595 — Todo): "Doesn't work" — likely refers to the maintenance mode config key in `app_config`; no detail recorded.
