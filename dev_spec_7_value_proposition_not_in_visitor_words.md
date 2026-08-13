# Generic Value Proposition — dev spec
Site: nomadinternet.com · Priority 7 · Medium · Effort: Low (0.5-2 days)

## Problem
The hero headline promises reliability but does not articulate why Nomad is better than alternatives in terms customers use.

## Evidence (from the live site)
> The page's main headline reads “Reliable Internet That Works Anywhere in the U.S”.

## Current state
h1: Reliable Internet That Works Anywhere in the U.S.; notes: Generic reliability claim.

## Required change
h1: No Contracts. Works Where Cable Won't.; notes: Include specific customer benefit.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Include specific customer benefit.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_value_proposition_not_in_visitor_words` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
