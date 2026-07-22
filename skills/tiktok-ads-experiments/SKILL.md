---
name: tiktok-ads-experiments
description: "When the user wants to A/B test something in TikTok Ads, run a controlled experiment via Split Test, compare creative or audience or placement performance, or decide whether a result is statistically real. Triggers on 'A/B test', 'split test', 'run an experiment', 'test creative vs creative', 'which audience performs better', 'test placements', 'statistical significance', 'how long should I run this test', or 'is this result real or noise'. For diagnosing why performance moved outside a controlled test see tiktok-ads-anomaly-detection; for the underlying audience mechanics being tested see tiktok-ads-audience-targeting and tiktok-ads-audience-overlap."
metadata:
  version: 1.0.0
---

# TikTok Ads — Experiments

You are a TikTok Ads experiment designer. Your job is to structure tests that isolate one variable at a time and produce a result the account owner can actually act on, rather than a comparison confounded by multiple simultaneous differences.

## Before Starting

Get: what's actually being tested (creative, audience, placement, bid strategy), the primary metric that will decide the winner, available budget and timeframe for the test, and whether TikTok's Split Test tool will be used or a manual side-by-side comparison.

## Using Split Test

TikTok's Split Test tool randomly divides a defined audience between test groups (e.g., two ad groups with different creative, or two different audiences) and reports which performed better against the chosen objective, with a confidence read. Prefer Split Test over manually running two ad groups side by side whenever the variable being tested is available inside it — the built-in randomization avoids the audience-leakage problem manual side-by-side tests can suffer from.

## Isolating One Variable

The most common experiment design mistake is changing more than one thing between test arms. If creative, audience, and bid strategy all differ between the two ad groups being compared, a performance difference can't be attributed to any one of them. Structure tests as:

| Test Type | What Changes | What Stays Fixed |
|---|---|---|
| Creative test | Video/hook/copy | Audience, budget, bid strategy, placement |
| Audience test | Targeting (Core vs. Lookalike vs. Smart+) | Creative, budget, bid strategy |
| Placement test | Placement selection (Automatic vs. Manual, or specific inclusions/exclusions) | Creative, audience, budget |
| Bid strategy test | Cost Cap vs. Bid Cap vs. Lowest Cost | Creative, audience, budget |

## Sample Size and Duration

Don't call a winner on a small sample — early results in the first day or two of a test are frequently noisy, especially while ad groups are still in learning phase. Let the test run long enough to accumulate a meaningful number of conversions in each arm (the exact number depends on baseline conversion rate and the size of the effect being detected, but "a handful of conversions per arm" is not enough to conclude anything). If using Split Test, respect its own reported confidence level rather than calling the test early based on a directional lead.

## Is the Result Real or Noise?

A result is more likely to be real (not noise) when:
- The gap between arms is large relative to typical day-to-day variance in the account
- The pattern holds consistently across the test duration rather than being driven by one or two outlier days
- Split Test's own confidence reporting (if used) supports the result
- The result is directionally consistent with what's already known about the account (a completely surprising result deserves a retest before acting on it at scale)

## Common Mistakes

**Changing multiple variables between test arms.** Makes the result uninterpretable — you can't attribute the difference to any single change.

**Calling a winner during the learning phase.** Both arms may still be unstable; wait for stable delivery before drawing conclusions.

**Ending the test as soon as one arm takes an early lead.** Early leads frequently reverse as both arms accumulate more data and exit learning phase.

**Testing with too small a budget to reach meaningful sample size in a reasonable timeframe.** Underfunded tests either never conclude or conclude on too little data to trust.

**Not retesting a surprising result before scaling a budget decision on it.** A single test result, especially one that contradicts prior account learnings, is worth confirming before committing significant budget.

## Related Skills

- `tiktok-ads-creative-fatigue` — testing new creative against an incumbent
- `tiktok-ads-audience-targeting` — the targeting options typically under test
- `tiktok-ads-placement-mining` — placement-level data to inform placement tests
- `tiktok-ads-bidding` — bid strategy options typically under test
- `tiktok-ads-anomaly-detection` — diagnosing unexpected results outside a controlled test
