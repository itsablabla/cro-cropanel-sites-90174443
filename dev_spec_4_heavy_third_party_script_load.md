# Heavy Third-Party Scripts — dev spec
Site: nomadinternet.com · Priority 4 · High · Effort: Medium (2-5 days)

## Problem
The homepage loads 65 scripts, which is the usual root cause of slow interaction readiness on mobile.

## Evidence (from the live site)
> Measured on the live homepage: 33 inline and 32 external <script> tags, 403 KB of HTML.

## Current state
notes: 65 scripts, 403 KB HTML

## Required change
notes: Audit third-party tags, defer non-critical scripts, and remove duplicated analytics or marketing pixels.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Audit third-party tags, defer non-critical scripts, and remove duplicated analytics or marketing pixels.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_heavy_third_party_script_load` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
