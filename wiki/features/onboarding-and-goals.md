---
name: onboarding-and-goals
description: Onboarding flow, goals screen, AI bike fit, and profile data capture
linear_refs: ["ETA-177", "ETA-491", "ETA-492", "ETA-513", "ETA-515", "ETA-516", "ETA-598", "ETA-599"]
last_updated: 2026-06-22
---

# Onboarding and Goals

## Onboarding flow

### Injuries / conditions field (ETA-177 — Canceled)
A proposal to ask users about existing injuries during onboarding was **canceled**. No reason recorded; likely considered too heavy for the onboarding funnel at this stage.

### Free-text field loses entered text (ETA-491 — In Review)
Bug: free-text field in onboarding loses previously entered text. Needs fixing to avoid frustrating early users who are typing detailed context.

### Age gate / consent
The legal review (ETA-588) added a 16+ age gate and health-data consent prompt. Onboarding must enforce this before plan generation. See legal article.

### Birthday registration (ETA-598 — In Review)
Capture user's birthday in-app. Likely supports the age gate and potentially personalisation.

### Attribution ("Where did you hear about us") (ETA-599 — In Review)
Capture marketing attribution source during onboarding.

## Goals

### Goal searches broken (ETA-492 — In Review)
Goal searches were not returning results properly — likely a backend query issue. Status: In Review.

### Simplify goals screen (ETA-513 — In Review)
Goals screen is too complex; simplification needed. No further detail.

### Simplify goals + records (ETA-516 — In Review)
Combine goals and records screens into a simpler unified view.

## AI bike fit (ETA-515 — In Review)
AI bike fit flow should be simplified. No further detail in ticket.

## Open question

The "Goals" tab in the bottom navigation currently serves goals, events, trips, and (now) routes. As the tab grows, renaming to "Planning" has been discussed (see route-planning article). This also affects how the goals/records section is framed.
