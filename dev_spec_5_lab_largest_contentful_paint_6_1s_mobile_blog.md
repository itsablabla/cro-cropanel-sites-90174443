# Slow Blog LCP Mobile — dev spec
Site: nomadinternet.com · Priority 5 · High · Effort: Medium (2-5 days)

## Problem
Measured in a lab load on /blogs/countrynomad/content-delivery-network-cdn: the page's main content takes this long to appear on a mid-range phone; most visitors have bounced long before.

## Evidence (from the live site)
> Lighthouse (mobile emulation, single synthetic run via DataForSEO): Largest Contentful Paint 6.1 s against a ‘good’ threshold of 2500ms. Lab data, not real-user field data — confirms the defect class, not the field percentile.

## Current state
notes: Largest Contentful Paint 6.1 s (lab, mobile on /blogs/countrynomad/content-delivery-network-cdn)

## Required change
notes: Largest Contentful Paint ≤ 2500ms (good)

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Largest Contentful Paint ≤ 2500ms (good)
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_lab_largest_contentful_paint_6_1s_mobile_blog` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 315,206 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; duration depends on traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
