---
name: pre-launch-readiness
description: "Pre-launch checklist \u2014 legal compliance (UK GDPR, health data,\
  \ Strava ToS), TestFlight review, pricing, and App Store preparation"
linear_refs:
- ETA-486
- ETA-488
- ETA-491
- ETA-542
- ETA-586
- ETA-587
- ETA-588
- ETA-590
- ETA-591
- ETA-596
- ETA-597
last_updated: 2026-06-24
lifecycle: null
---

# Pre-Launch Readiness

## Legal (ETA-588 — Todo, partially done)

### Already shipped
- ToS + Privacy Policy rewritten to match real app functionality (full sub-processor list, Strava/photos/location, health-data basis, retention/transfer, free-trial/auto-renew, statutory liability carve-out)
- Account-deletion erasure bug fixed — photos/videos purged from Supabase Storage on delete
- Consent capture added: ToS/Privacy clickwrap + 16+ age gate at sign-up; health-data consent before first plan
- Solicitor brief committed at `docs/legal/tos-privacy-review-2026-06.md`
- ICO registration done (~£52/yr)
- `LEGAL_VERSION = 2026-06-18` — re-prompts existing users to re-accept on next launch (visible event; time releases around it)

### P0 blockers (must clear before public launch)
- [ ] Solicitor sign-off on ToS + Privacy Policy (hand over committed review doc as brief)
- [ ] Confirm health-data (special-category) consent meets UK GDPR Art. 9 / Data (Use and Access) Act 2025
- [ ] Confirm 16+ age gate / Children's Code position is sufficient
- [ ] Documented US data-transfer mechanism (UK–US Data Bridge / IDTA / SCCs) for Anthropic, Perplexity, Railway
- [ ] Resolve Strava API terms compliance — Strava's terms restrict AI use

### P1 (before / at launch)
- [ ] Subscriptions: App Store/Play auto-renewal disclosures + UK DMCC subscription rules
- [ ] App Store / Play "data safety" + AI-generated-content disclosures match policy
- [ ] Fill Etapa Ltd company number + registered office into published policies
- [ ] Confirm Apple/Google/Tide accounts held by Etapa Ltd (not personally); professional-indemnity insurance

### Recommended legal services
Sprintlaw UK or Jonathan Lea Network for fixed-fee review. Brief: review ToS + Privacy, advise on UK GDPR (incl. health/special-category, DUAA 2025), DMCC subscription rules, and Strava terms. Budget ~£1,000–2,000. See ETA-588 for full options list.

**Note:** Trailforks integration (ETA-615) also requires legal sign-off on data licence + attribution before launch.

## TestFlight / Closed Beta

- **TestFlight review** (ETA-591 — In Review): TestFlight submission in review process
- **TestFlight feedback** (ETA-597 — In Review): collecting and actioning feedback from TestFlight testers

## Email verification (ETA-586 — In Review)

Email verification flow needed (no detail recorded).

## Pricing

Pricing is being actively discussed (ETA-594, ETA-600 — In Review). No public price or model has been decided and recorded in these tickets. Pricing config exists in `app_config` as a `pricing_config` value (server-driven).

## App Store preparation

- Screenshots and descriptions (ETA-42, ETA-587 — Backlog / In Review): assets needed for App Store + Play Store submission
- "Data safety" and AI-generated content disclosures must match the privacy policy (legal requirement)

## Penetration testing (ETA-590 — Todo)

Dark Moon penetration testing engagement — not yet started.
