# Inconsistent Pricing Display — dev spec
Site: nomadinternet.com · Priority 8 · High · Effort: Medium (2-5 days)

## Problem
The same plans show conflicting monthly prices across pages, undermining trust in the stated cost.

## Evidence (from the live site)
> Prices shown on the page: $99.95 /month $129.95 /month $99.95/Mo $99.95 /month $129.95 /month $99.95
> Prices shown on the page: $99.95 /month $129.95 /month $99.95/mo $0.00 $99.95 $99.99

## Current state
notes: Conflicting prices for the same plan across pages.

## Required change
notes: Standardize the displayed monthly price across all pages.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Standardize the displayed monthly price across all pages.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_pricing_inconsistency_across_pages` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
