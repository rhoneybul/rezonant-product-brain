---
name: training-sessions
description: "Session management \u2014 gym logging, strength exercises, scheduling,\
  \ persistence bugs, coach notes, and plan overview"
linear_refs:
- ETA-560
- ETA-562
- ETA-565
- ETA-566
- ETA-568
- ETA-569
- ETA-570
- ETA-572
- ETA-573
- ETA-574
- ETA-575
- ETA-577
- ETA-578
- ETA-579
- ETA-580
- ETA-582
- ETA-583
- ETA-495
- ETA-507
- ETA-560
last_updated: 2026-06-17
lifecycle: waxing
---

# Training Sessions

## Status

A large cluster of session-related work landed in mid-June 2026 as the team iterated on the gym/strength and scheduling UX through beta testing. Most tickets are "In Review."

## Gym / Strength session UX

These items were raised together (ETA-573–ETA-579) as a batch of logged beta feedback:

- **Rest timer between sets** (ETA-573) — ensure a rest timer runs between strength sets
- **Show sets vertically** (ETA-575) — logged set data should display in a vertical list, not an inline sentence
- **Mark done without logging weights** (ETA-577) — marking a set done without entering data should not auto-log zeroes
- **Edit after logging — no strikethrough** (ETA-574) — editing a logged item should not apply a strikethrough style
- **More core exercises + equipment labels** (ETA-578) — expand core exercise library; each exercise should state required equipment (bench, box, dumbbell, bodyweight)
- **Background timers** (ETA-579) — unclear whether background timers are running correctly; needs investigation
- **Delete session buggy** (ETA-582) — deleted sessions reappear; fix requires reliable server-side + client-side + local-storage deletion. Restore from settings also considered.
- **Cross-activity type sessions** (ETA-560) — coach chat should be able to create non-cycling session types (e.g. "give me a 30-minute swim on this day")

## Scheduling and persistence

- **Session changes don't persist over refresh** (ETA-565) — gym session changes lost on reload; must be persisted
- **Session persistence across devices** (ETA-566) — scheduling made on simulator may not carry over to real device
- **Persist activity changes** (ETA-570) — any change to an activity must be saved
- **Drag to reschedule** (ETA-568) — once a session is scheduled, rider should be able to drag it to a different day
- **Edit session time** (ETA-569) — easier time-editing for swim sessions in particular
- **Session replacement unreliable** (ETA-507) — replacing sessions (especially trainer intervals) is unreliable; repro not yet confirmed with screenshots
- **Scheduling bug (calendar)** (ETA-495) — early beta: new session wasn't added to calendar and calendar didn't show scheduled sessions; JSON output of session expected on schedule

## Coach notes

- **Cache coach notes** (ETA-572) — coach notes are regenerated on every activity load, incurring LLM cost and latency; they should be generated once, stored, and only regenerated on demand

## Session loading performance

- **Slow session structure load** (ETA-580) — fetching training pacing/structure is either very slow or fails; user-reported in beta. Root cause unknown.

## Plan overview

- **Plan overview (ETA-583):** The plan overview screen should show:
  - Strava-recorded distance clearly overlaid on the plan graph
  - Which sessions were done vs. skipped for past weeks
  - Strava sessions interleaved in week view (in chronological order)
  - Remove "open full week view" button — adds no value

## Open questions

- Restore-from-settings for deleted sessions: good UX but adds state complexity — decision pending
- Background timer implementation details unclear
- **Keyboard obscures input fields** (ETA-608 — Backlog): keyboard popup blocks scroll to text input (e.g. body weight); user cannot see input field or required format. Affects all text inputs. iOS 26.5 / v1.6.4.
