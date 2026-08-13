# Blog Mobile Layout Shifts — dev spec
Site: nomadinternet.com · Priority 6 · High · Effort: Medium (2-5 days)

## Problem
Measured in a lab load on /blogs/countrynomad/content-delivery-network-cdn: the layout jumps while loading, causing mis-taps on the very buttons the funnel depends on.

## Evidence (from the live site)
> Lighthouse (mobile emulation, single synthetic run via DataForSEO): Cumulative Layout Shift 0.265 against a ‘good’ threshold of 0.1. Lab data, not real-user field data — confirms the defect class, not the field percentile.

## Current state
notes: Cumulative Layout Shift 0.265 (lab, mobile on /blogs/countrynomad/content-delivery-network-cdn)

## Required change
notes: Cumulative Layout Shift ≤ 0.1 (good)

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Cumulative Layout Shift ≤ 0.1 (good)
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_lab_cumulative_layout_shift_0_265_mobile_blog` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
