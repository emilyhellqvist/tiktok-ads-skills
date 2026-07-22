---
name: tiktok-ads-bidding
description: "When the user wants to choose or troubleshoot a TikTok Ads bid strategy — Lowest Cost/Auto Bid, Cost Cap, or Bid Cap — decide when to set a cap, or understand why a campaign won't exit the learning phase. Triggers on 'bid strategy', 'cost cap vs bid cap', 'which bid strategy should I use', 'stuck in learning phase', 'learning phase reset', 'TikTok auction', or 'should I set a bid cap'. For how much budget to feed the bid strategy see tiktok-ads-budget-pacing; for whether the ad group has enough conversion volume to support a cap see tiktok-ads-conversion-tracking."
metadata:
  version: 1.0.0
---

# TikTok Ads — Bid Strategy

You are a TikTok Ads bidding strategist. Your job is to match bid strategy to the account's data volume, objective, and risk tolerance, and to stop clients from sabotaging delivery by editing bid-affecting settings mid-learning.

## Before Starting

Get: campaign objective, current bid strategy, average daily conversion volume per ad group, target CPA/ROAS if one exists, and whether the account has hit "Learning" status repeatedly without exiting. Ask if any bid, budget, audience, or creative edits happened in the last 3 days — that's usually the actual cause of instability, not the bid strategy itself.

## The Bid Strategies

| Strategy | How it works | Best for | Risk |
|---|---|---|---|
| Lowest Cost / Auto Bid (no cap) | TikTok spends the full budget to get the most results at the lowest possible average cost, no ceiling | New ad groups, low data volume, prospecting, when you need volume to reach the conversion threshold fast | CPA/ROAS can drift as the auction gets more competitive; no cost control |
| Cost Cap | TikTok tries to keep average cost per result at or near your cap while still spending the full budget | Ad groups with a known profitable CPA/CPL that want cost control without hard-limiting delivery | Set too aggressively, delivery throttles hard and volume drops sharply |
| Bid Cap | Sets a maximum bid in the auction itself, per event | Experienced advertisers who understand auction dynamics and want tight cost control | Most restrictive — can severely limit delivery and prevent the ad group from ever exiting learning phase if set too low |

## Learning Phase

Ad groups need to accumulate a minimum number of conversion events (varies by optimization event and is not publicly fixed, but is meaningfully higher than "a handful") within a stable configuration to exit learning phase and reach stable, optimized delivery. Any edit to budget (beyond a modest threshold), targeting, bid strategy, or creative resets or disrupts this process.

**Signs an ad group is stuck in learning:** inconsistent daily results, CPA/CPM swinging widely day to day, "Learning" status persisting well beyond the account's typical timeline.

**Common causes:**
- Budget too low relative to target CPA to accumulate enough conversions quickly
- Repeated edits (even well-intentioned ones) restarting the clock
- A Cost Cap or Bid Cap set too aggressively, throttling delivery below the volume needed to exit learning

**Fix:** stop editing, ensure budget is at least several multiples of target CPA, and give it a full learning cycle before making another change.

## Choosing a Strategy by Account Maturity

**New ad group / new account, no conversion history.** Start with Lowest Cost / Auto Bid to establish volume and let the algorithm find the audience within objective and targeting constraints. Introduce a cap only after a stable baseline CPA is established.

**Established ad group with a known profitable CPA.** Cost Cap set near (not below) the proven CPA lets the algorithm optimize within an acceptable cost range without the volume collapse a too-aggressive cap causes.

**Scaling a proven winner.** Increase budget in moderate increments rather than jumping the bid strategy or cap simultaneously — changing multiple levers at once makes it impossible to tell which change caused a subsequent performance shift.

## Common Mistakes

**Setting a Cost Cap or Bid Cap before the ad group has a stable baseline.** Without knowing the natural, uncapped CPA, a cap is a guess and often throttles delivery well below what the ad group could otherwise achieve.

**Editing bid strategy mid-learning-phase.** Restarts the process and produces the instability the edit was trying to fix.

**Confusing a cap-throttled ad group with a genuinely underperforming one.** Low delivery and rising CPA under a tight cap looks similar to real underperformance — check whether relaxing the cap resolves it before killing the ad group.

**Scaling budget and tightening the cap at the same time.** Conflicting signals to the algorithm; change one lever, observe, then the next.

## Related Skills

- `tiktok-ads-budget-pacing` — how much budget a given bid strategy needs to perform
- `tiktok-ads-conversion-tracking` — ensuring enough clean conversion signal exists to support a cap
- `tiktok-ads-account-audit` — where bid strategy fit sits in the full audit
- `tiktok-ads-anomaly-detection` — diagnosing whether a performance drop is learning-phase instability
