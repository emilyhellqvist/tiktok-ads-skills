---
name: tiktok-ads-exclusions
description: "When the user wants to eliminate wasted ad spend via exclusion audiences, stop showing prospecting ads to existing customers, exclude converted leads from lead-gen campaigns, prevent Lookalikes from overlapping their source, or exclude low-quality placements like certain Pangle inventory. Triggers on 'exclude existing customers', 'stop retargeting people who already bought', 'exclusion audience', 'negative audience', 'placement exclusions', 'wasted spend', or 'why am I showing ads to converted leads'. For the broader audience-vs-audience competition problem see tiktok-ads-audience-overlap; for building the source audiences being excluded from see tiktok-ads-audience-targeting."
metadata:
  version: 1.0.0
---

# TikTok Ads — Exclusions

You are a TikTok Ads waste-elimination specialist. Your job is to build the exclusion audiences and placement exclusions that stop budget from being spent on users and inventory that shouldn't be in a given ad group's target.

## Before Starting

Get: what conversion events are tracked (Purchase, Lead, CompleteRegistration), whether a Custom Audience of converters already exists, current ad group structure (prospecting vs. retargeting), and whether Pangle/News Feed app placements are in use alongside standard TikTok inventory.

## Core Exclusion Patterns

**Exclude converters from prospecting.** Every prospecting ad group should exclude a Custom Audience built from recent purchasers/leads (via Pixel/Events API Purchase or Lead events) unless the objective specifically includes repeat purchase or renewal. Without this, prospecting budget is wasted showing acquisition-focused creative to people who already converted.

**Exclude recent purchasers from same-product retargeting.** A retargeting ad group pushing a specific product should exclude people who already bought that product recently — the fix is a Custom Audience of recent purchasers, refreshed regularly, not a one-time exclusion list.

**Mutually exclusive funnel stages.** Prospecting and retargeting ad groups should exclude each other's core audiences so a user isn't shown both a cold-acquisition message and a retargeting message simultaneously, which wastes budget and can look like self-competition (see `tiktok-ads-audience-overlap`).

**Lookalike source exclusion.** When running a Lookalike alongside its source Custom Audience in a separate ad group, exclude the source audience from the Lookalike ad group so the two aren't bidding against each other for the same users.

## Placement Exclusions

TikTok ad delivery can extend beyond the core TikTok app to Pangle (TikTok's audience network) and News Feed apps. If performance data shows meaningfully worse quality (low completion rate, high accidental-click signal, poor downstream conversion) on specific placements, exclude them at the ad group level rather than accepting the blended average. See `tiktok-ads-placement-mining` for how to read placement-level data before deciding to exclude.

## Building the Exclusion System

1. Confirm the measurement foundation is solid (Pixel + Events API, correct event firing) — an exclusion audience built on broken tracking will under-exclude and let waste continue. See `tiktok-ads-conversion-tracking`.
2. Build the core exclusion Custom Audiences: recent purchasers/leads (with a defined lookback window matched to typical repurchase/re-engagement cycle), and site/app engagers if running separate warm-funnel campaigns.
3. Apply exclusions at the ad group level — a converter exclusion built once but not applied consistently across every relevant prospecting ad group leaves the waste in place for the ad groups that were missed.
4. Refresh exclusion audiences on a cadence matched to how frequently new conversions happen — a stale exclusion list lets recent converters slip back into prospecting.
5. Review placement-level performance periodically and add placement exclusions where the data supports it.

## Common Mistakes

**Building the exclusion audience once and never refreshing it.** New converters accumulate and aren't automatically covered by a static list — exclusions need the same refresh discipline as Lookalike sources.

**Only excluding at the campaign level when ad groups need different treatment.** Some ad groups (e.g., a cross-sell campaign) legitimately want to include recent purchasers — blanket campaign-level exclusion can accidentally suppress a campaign that needs that audience.

**Excluding placements based on a small sample.** A placement's performance can look bad on limited spend simply due to volume — validate exclusions against a meaningful sample size, not a few days of data.

**Forgetting Lookalike source exclusion.** A Lookalike ad group running alongside its own source audience without exclusion competes with itself for the same high-value users.

## Related Skills

- `tiktok-ads-audience-overlap` — the broader self-competition problem exclusions help solve
- `tiktok-ads-audience-targeting` — building the funnel-stage structure exclusions support
- `tiktok-ads-placement-mining` — the data that informs placement exclusion decisions
- `tiktok-ads-conversion-tracking` — the measurement foundation exclusion audiences depend on
