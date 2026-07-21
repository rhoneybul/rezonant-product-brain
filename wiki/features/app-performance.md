---
name: app-performance
description: App performance improvements — lazy loading, home screen speed, session structure load time, and calendar navigation
linear_refs: ["ETA-474", "ETA-563", "ETA-580"]
last_updated: 2026-06-16
---

# App Performance

## Home screen lazy loading (ETA-563 — In Review)

**Problem:** Home screen loads all activities at once, causing slow initial render.

**Fix:** Only load the current week's activities on initial render; load remaining weeks lazily when the user scrolls or toggles. Goal is to improve perceived performance on app open.

## Session structure loading (ETA-580 — In Review)

Training pacing/structure either fails to load or takes too long to appear (user-reported in beta). Root cause not yet identified.

## Calendar "today" navigation (ETA-474 — In Review)

Tapping "today" in the calendar should navigate to the current day. Currently unclear if this works correctly.

## Principle

Performance issues cluster around data-heavy screens (home screen, session detail). Lazy loading and server-side caching of generated content (coach notes — ETA-572) are the two complementary levers being pursued.
