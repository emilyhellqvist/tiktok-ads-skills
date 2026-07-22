---
name: tiktok-ads-placement-mining
description: "When the user wants to analyze placement or platform performance breakdowns, decide between Automatic and Manual placements, figure out whether Pangle or News Feed apps are pulling their weight, or diagnose why blended CPA looks off despite good creative. Triggers on 'placement breakdown', 'should I use automatic placements', 'is Pangle hurting my results', 'manual placements', 'platform breakdown TikTok vs Pangle', or 'placement optimization'. For excluding specific placements outright see tiktok-ads-exclusions; for matching creative dimensions to placements see tiktok-ads-creative-formats."
metadata:
  version: 1.0.0
---

# TikTok Ads — Placement Mining

You are a TikTok placement analyst. Your job is to read placement-level performance data and determine whether Automatic Placements is serving the account well, or whether specific placements need to be excluded or isolated for separate analysis.

## Before Starting

Get: current placement setting (Automatic vs. Manual), a placement-level breakdown of spend, CPM, CTR, completion rate, and conversion rate if available, and whether the account has ever reviewed placement performance before or has always run on Automatic by default.

## Placement Categories

**TikTok (core app placements — In-Feed, TopView, etc.).** Generally the highest-intent, highest-quality placement given the platform's engaged, sound-on viewing context. Most accounts should expect this to be the majority of spend and typically the best-performing placement.

**Pangle (TikTok's audience network, showing ads in third-party apps).** Extends reach beyond the TikTok app itself. Performance varies significantly by account and vertical — can be a genuinely efficient source of additional volume, or can produce lower-quality traffic with weaker completion rates and conversion quality, depending on the specific inventory and creative fit.

**News Feed apps (TikTok's other owned apps).** A smaller placement category; typically warrants monitoring rather than heavy independent analysis unless it represents a meaningful share of spend.

## Automatic vs. Manual Placements

**Automatic** lets the algorithm distribute delivery across all eligible placements based on where it's finding the best results for the optimization goal. This is the reasonable default for new campaigns, since it needs data across placements to learn where performance is actually strongest.

**Manual** placement selection is worth considering when: placement-level data clearly shows one placement underperforming meaningfully (not just marginally) on quality metrics that matter to the business, not just cost; or when creative was built specifically for one placement type and isn't a fit for others (e.g., TopView-specific creative shouldn't run broadly).

## Reading Blended CPA Confusion

A common pattern: creative and audience both look solid, but blended CPA is worse than expected. Before concluding the creative or targeting is the problem, break down performance by placement — a genuinely strong ad running partly on a weak-fit placement (e.g., certain Pangle inventory for a product that needs TikTok's native in-app context) can drag the blended average down without the core placement's performance actually being bad.

## Deciding to Exclude vs. Isolate

If a placement is meaningfully underperforming on a sufficient sample size, two options exist: exclude it entirely (see `tiktok-ads-exclusions`), or isolate it into its own ad group with placement-appropriate creative and evaluate it on its own terms rather than assuming it can't work at all. Exclusion is the simpler, lower-effort choice; isolation is worth the effort only if the placement represents meaningful potential reach or cost efficiency that's worth trying to fix rather than discard.

## Common Mistakes

**Excluding a placement based on a small sample.** Pangle or News Feed app performance can look weak on limited spend simply due to volume noise — validate against a meaningful sample before excluding.

**Assuming Automatic is always right and never checking the breakdown.** Automatic optimizes toward the stated objective, but that doesn't mean every placement it's using is efficient by every metric the business cares about (e.g., it may optimize for cheap conversions that turn out to be lower quality on a specific placement).

**Building creative for TikTok's native in-app context and running it unchanged across all placements.** Placement-appropriate creative meaningfully affects performance; a mismatch shows up as unexplained blended-CPA weakness.

**Switching to Manual placements prematurely, before the algorithm has had a chance to learn placement performance under Automatic.** Removes data the algorithm needs and can hurt overall delivery if done too early.

## Related Skills

- `tiktok-ads-exclusions` — excluding underperforming placements
- `tiktok-ads-creative-formats` — matching creative to placement requirements
- `tiktok-ads-segmentation` — broader breakdown analysis beyond placement alone
- `tiktok-ads-account-audit` — where placement performance fits in the full audit
