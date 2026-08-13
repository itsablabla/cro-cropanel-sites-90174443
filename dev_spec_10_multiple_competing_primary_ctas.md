# Competing Primary CTAs — dev spec
Site: nomadinternet.com · Priority 10 · Medium · Effort: Medium (2-5 days)

## Problem
Each page presents several equally prominent CTAs, creating ambiguity about which action advances the conversion funnel.

## Evidence (from the live site)
> 7 distinct calls to action compete on the same page: “CHECK COVERAGE”, “CHECK IF IT WORKS AT MY ADDRESS”, “SEE MY OPTIONS”, “GET STARTED”, “START CHAT”, “SEE WHAT I QUALIFY FOR”, “CHECK MY COVERAGE”.
> 5 distinct calls to action compete on the same page: “CHECK COVERAGE”, “Learn More”, “Watch on”, “SEE WHAT I QUALIFY FOR”, “CHECK MY COVERAGE”.

## Current state
cta: Multiple CTAs; notes: Multiple equally prominent CTAs on each page.

## Required change
cta: Single primary CTA; notes: Designate one primary CTA and de-emphasize secondary ones.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Designate one primary CTA and de-emphasize secondary ones.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_multiple_competing_primary_ctas` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 1,941,808 visitors per variant to detect a 2.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
