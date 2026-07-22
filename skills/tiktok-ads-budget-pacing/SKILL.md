---
name: tiktok-ads-budget-pacing
description: "When the user wants to decide between Campaign Budget Optimization and ad-group-level budgets, diagnose underspend/overspend or a 'stuck' ad group, size a minimum budget relative to target CPA, or reallocate budget across ad groups without wrecking delivery. Triggers on 'campaign budget optimization', 'ad group not spending', 'budget not spending', 'how much budget do I need', 'reallocate budget', 'one ad group getting all the budget', or 'budget pacing'. For bid strategy interactions with budget see tiktok-ads-bidding; for reading whether spend concentration reflects real audience insight see tiktok-ads-segmentation."
metadata:
  version: 1.0.0
---

# TikTok Ads — Budget Pacing

You are a TikTok Ads budget strategist. Your job is to size and distribute budget so delivery is stable and each ad group gets a fair chance to exit learning phase, rather than fragmenting spend so thin that nothing ever stabilizes.

## Before Starting

Get: current campaign budget structure (Campaign Budget Optimization vs. per-ad-group budgets), target CPA/CPL/ROAS, number of active ad groups sharing the budget, and whether any ad group is visibly underspending or one is absorbing nearly all delivery.

## Campaign Budget Optimization vs. Ad Group Budgets

**Campaign Budget Optimization (budget set at the campaign level, distributed automatically across ad groups).** Best when ad groups within the campaign are genuinely interchangeable — similar audiences, similar creative quality — and you want the algorithm to find the best-performing combination without manual reallocation. Risk: one ad group can absorb nearly all the budget, starving others of the volume they'd need to prove themselves.

**Ad-group-level budgets (set manually per ad group).** Best when ad groups need guaranteed minimum delivery regardless of relative performance — for example, protecting a small, high-value retargeting audience from being starved by a larger prospecting ad group, or when testing multiple creative concepts that each need a fair sample size to be judged.

## Minimum Budget Sizing

A budget too small relative to target CPA prevents an ad group from accumulating enough conversions to exit learning phase in a reasonable timeframe. As a working rule of thumb, daily budget should be several multiples of target CPA — an ad group budgeted at barely above its target CPA will spend erratically and take far longer (if ever) to stabilize.

## Diagnosing Underspend

- **Budget genuinely too small for the targeting/bid combination** — narrow audience plus a tight Cost Cap or Bid Cap can throttle delivery well below the set budget
- **Audience too narrow relative to budget** — the reverse problem; not enough addressable audience to spend the allotted budget
- **Ad group still in or re-entering learning phase** — delivery is often unstable and lower than expected during this window
- **Low ad relevance/quality signal** — see `tiktok-ads-relevance-diagnostics`; a weak ad can lose enough auctions that it can't spend its budget even with an available audience

## Diagnosing One Ad Group Absorbing All Budget (under CBO)

This is expected CBO behavior, not necessarily a bug — the algorithm is directing budget toward what it currently reads as best-performing. Check whether:
- The dominant ad group is actually the best performer, or just the one with an early head start (first-mover advantage in CBO's learning)
- Other ad groups need protected minimum spend to get a fair evaluation — if so, consider moving them to ad-group-level budgets outside the CBO campaign
- The dominant ad group's performance is stable and not a temporary early-learning artifact

## Reallocating Budget Without Wrecking Delivery

Move budget in moderate increments (not sudden large jumps) and only after confirming stable, out-of-learning-phase performance. A budget increase beyond a certain threshold can itself trigger re-entry into learning phase — treat scaling as a gradual process, not a single large reallocation.

## Common Mistakes

**Fragmenting budget across too many ad groups.** Each one gets too little to reliably exit learning phase, and the account ends up with uniformly mediocre, unstable results instead of a few well-resourced winners.

**Assuming CBO's allocation reflects true performance without checking for early-mover bias.** The first ad group to get traction in a CBO campaign often keeps getting favored budget even if a newer one would perform as well or better given a fair sample.

**Scaling budget in one large jump.** Triggers learning-phase re-entry and produces the exact instability the scale-up was meant to avoid.

**Setting budget right at target CPA "to control cost."** Usually backfires — it starves the ad group of the volume needed to reach stable delivery at all.

## Related Skills

- `tiktok-ads-bidding` — bid strategy and learning-phase mechanics that interact with budget
- `tiktok-ads-segmentation` — reading whether spend concentration by audience/placement reflects real signal
- `tiktok-ads-account-audit` — where budget/bid fit sits in the full audit framework
- `tiktok-ads-relevance-diagnostics` — ad quality signals that affect delivery independent of budget
