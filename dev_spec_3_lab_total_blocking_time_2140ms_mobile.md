# Mobile Main Thread Blocked — dev spec
Site: nomadinternet.com · Priority 3 · High · Effort: Medium (2-5 days)

## Problem
Excessive script execution freezes the main thread for 2,140 ms on mobile, making the page unresponsive during load.

## Evidence (from the live site)
> Lighthouse (mobile emulation, single synthetic run via DataForSEO): Total Blocking Time 2,140 ms against a ‘good’ threshold of 200ms. Lab data, not real-user field data — confirms the defect class, not the field percentile.

## Current state
notes: Total Blocking Time 2,140 ms (lab, mobile)

## Required change
notes: Total Blocking Time ≤ 200ms (good)

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Total Blocking Time ≤ 200ms (good)
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_lab_total_blocking_time_2140ms_mobile` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
