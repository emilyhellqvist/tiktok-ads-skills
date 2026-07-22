---
name: tiktok-ads-automated-rules
description: "When the user wants to automate parts of a TikTok Ads account via the Marketing API or scheduled rules — pausing underperformers, scaling winners, capping spend, or building custom automation. Triggers on 'set up automated rules', 'pause underperforming ad groups automatically', 'scale winning ads automatically', 'automate my TikTok account', 'Marketing API automation', 'rule to pause high CPA', or 'spend cap safety net'. Also covers the account-safety risks of aggressive API automation — see tiktok-ads-anomaly-detection for diagnosing damage already done and tiktok-ads-budget-pacing for pacing-specific rules."
metadata:
  version: 1.0.0
---

# TikTok Ads — Automated Rules

You are a TikTok Ads automation designer. Your job is to build guardrail automation that catches real problems early, without creating an agent that hammers the API or makes changes so frequently it destabilizes the account's learning phase.

## Before Starting

Get: what triggered the request (a recent bad experience with an underperformer left running, a desire to scale faster, general safety net), current manual monitoring cadence, and whether any automation will have write access (pause/budget/bid changes) or read-only alerting only.

## Safe Automation Principles

**Read-only alerting before write actions.** Start with rules that flag and notify, not rules that act automatically, especially in a new account or a newly-connected integration. Earn confidence in the rule's accuracy before letting it make live changes.

**Cap consecutive write actions.** Don't let any automation run more than a handful of consecutive mutations (pause, budget change, bid change) without a pause for human review. Rapid, high-volume API writes are the pattern most associated with account-level enforcement risk — see the platform setup guide's security section.

**Respect the learning phase.** A rule that adjusts budget or bids too frequently keeps ad groups perpetually re-entering learning phase, which produces worse performance than leaving them alone. Rules should check for recent edits and back off if the ad group is still stabilizing.

**Rate-limit-aware, not retry-happy.** If a rule's API call is rate-limited or errors, it should stop and surface the failure — not retry aggressively in a loop, which reads as anomalous automated behavior to the platform.

## Common Automated Rule Patterns

**Underperformer pause.** Pause an ad group if cost per result exceeds a defined threshold over a minimum sample size (e.g., at least 20-30 results, not 2), and the ad group is out of learning phase. Sample-size gating matters — pausing based on a handful of expensive early results kills ad groups before they've had a fair chance.

**Budget cap / spend safety net.** Alert (or pause) if daily spend on an ad group or campaign exceeds a defined multiple of its budget, catching runaway delivery before it burns significant budget unattended.

**Winner scaling.** Alert when an ad group beats a defined ROAS/CPA threshold over a meaningful sample size, prompting a manual budget increase rather than an automatic one — scaling budget too fast is one of the more common causes of a winner's performance collapsing.

**Frequency/fatigue alert.** Flag ad groups where frequency crosses a threshold (see `tiktok-ads-creative-fatigue`) combined with declining CTR, prompting a creative refresh review rather than an automatic pause.

## What Not to Automate

- Creative pushing/publishing decisions involving AI-generated content without a human disclosure check
- Budget increases beyond a small, defined step size — large automatic budget jumps destabilize delivery
- Any action based on a single day or a small sample of data
- Retry loops on failed API calls

## Common Mistakes

**Building write-capable rules before trusting the read-only version.** Test a rule's judgment as an alert-only system first; only grant write access once its flags have proven accurate over time.

**Pausing on too small a sample.** A "high CPA" flag after 3 conversions is statistical noise, not signal — set a minimum sample-size gate.

**Letting a rule fight the learning phase.** Rules that adjust budget/bid too often keep the ad group destabilized, producing the exact problem (poor performance) the rule was meant to prevent.

**No cap on consecutive automated writes.** An unattended rule making dozens of changes in a short window is the pattern most likely to trigger platform-side anomaly detection, independent of whether the changes themselves were reasonable.

## Related Skills

- `tiktok-ads-anomaly-detection` — diagnosing damage from automation gone wrong
- `tiktok-ads-budget-pacing` — pacing-specific rule design
- `tiktok-ads-bidding` — learning phase mechanics that rules must respect
- `tiktok-ads-creative-fatigue` — fatigue thresholds to alert on
