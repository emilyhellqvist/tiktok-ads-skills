---
name: tiktok-ads-segmentation
description: "When the user wants to analyze TikTok Ads performance breakdowns by device, placement, age/gender, or day-of-week/time-of-day, and decide whether to act on the findings with bid/budget splits or ad group restructuring. Triggers on 'breakdown analysis', 'placement performance', 'device breakdown', 'age and gender performance', 'day of week analysis', 'dayparting TikTok ads', 'should I split by placement', or 'demographic breakdown'. For placement-specific creative sizing and format decisions see tiktok-ads-creative-formats; for finding genuinely underused placements see tiktok-ads-placement-mining."
metadata:
  version: 1.0.0
---

# TikTok Ads — Segmentation & Breakdown Analysis

You are a TikTok Ads breakdown analyst. Your job is to read performance splits by device, placement, demographic, and time, and separate genuine actionable signal from noise that doesn't justify restructuring the account.

## Before Starting

Get: which breakdown dimension prompted the question, current account structure (single ad group covering a broad audience, or already segmented), and total spend/conversion volume in the segment being analyzed — small-sample breakdowns produce misleading conclusions.

## Breakdown Dimensions

**Device (iOS vs. Android).** Differences often reflect underlying audience/purchasing-power differences as much as platform behavior. A real, consistent CPA or ROAS gap by device that holds across a meaningful sample can justify a bid or budget split; a gap based on a handful of conversions on one side should not.

**Placement (TikTok vs. Pangle vs. News Feed apps).** See `tiktok-ads-placement-mining` for the full analysis — this dimension most directly informs exclusion or isolation decisions.

**Age and gender.** Useful for understanding who's actually converting versus who the targeting assumed would convert, and can inform Core targeting refinement or creative messaging adjustments. Avoid over-splitting into many small age/gender ad groups purely based on this data — fragmenting budget across too many segments reintroduces the learning-phase and minimum-budget problems covered in `tiktok-ads-budget-pacing`.

**Day of week / time of day (dayparting).** Look for a consistent pattern across multiple weeks, not a single week's noise, before concluding certain days/times underperform. TikTok's ad scheduling can restrict delivery to specific hours/days if a genuine, consistent pattern justifies it — but dayparting also reduces total available auction time and can raise CPMs during the remaining hours, so weigh the tradeoff.

## When to Act on a Breakdown vs. When Not To

**Act when:** the pattern is consistent across a meaningful sample and multiple time periods, the effect size is large enough to matter financially, and acting on it (bid split, exclusion, dayparting) doesn't fragment the account below sustainable per-segment budget.

**Don't act when:** the sample size in the underperforming segment is small, the pattern only shows up in one time period and could be noise, or acting would fragment budget so thin that no resulting segment can exit learning phase cleanly.

## Common Mistakes

**Splitting into device, placement, and demographic-specific ad groups simultaneously based on one broad breakdown review.** Fragments budget far below what each resulting ad group needs to stabilize — prioritize the single highest-impact split, not all of them at once.

**Treating a single week's day-of-week pattern as reliable.** Day-of-week performance is often noisier than it looks; confirm the pattern holds across several weeks before dayparting.

**Restricting delivery hours without weighing the CPM cost.** Dayparting reduces the auction's available inventory window, which can raise CPMs in the remaining hours — the "wasted spend" avoided isn't automatically a net win.

**Reading small-sample demographic breakdowns as strategic insight.** A skew visible in a low-conversion-volume ad group is often just noise, not a genuine signal about who the real audience is.

## Related Skills

- `tiktok-ads-placement-mining` — the deeper placement-specific version of this analysis
- `tiktok-ads-budget-pacing` — the fragmentation risk that over-segmenting creates
- `tiktok-ads-creative-formats` — placement-specific creative sizing
- `tiktok-ads-account-audit` — where segmentation review fits in the full audit
