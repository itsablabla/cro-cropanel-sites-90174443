# Unclear One-Time Fees — dev spec
Site: nomadinternet.com · Priority 9 · High · Effort: Low (0.5-2 days)

## Problem
One-time prices are listed without explanation, leaving the total cost ambiguous.

## Evidence (from the live site)
> A section heading reads “$0.00 (one-time)”.
> A section heading reads “$99.99 (one-time)”.

## Current state
notes: One-time prices without labels.

## Required change
notes: Add clear labels explaining what each one-time fee covers.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add clear labels explaining what each one-time fee covers.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_unclear_one_time_fee_disclosure` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
