---
name: tiktok-ads-relevance-diagnostics
description: "When the user wants to interpret ad quality and relevance signals on TikTok — completion rate, view-through rate, CTR/CVR relative to benchmark — or wants to understand why CPMs are climbing relative to competitors targeting the same audience. Triggers on 'ad quality TikTok', 'why is my CPM so high', 'completion rate benchmark', 'view-through rate', 'my TikTok ads are being penalized', or 'relevance score TikTok'. For creative-level fixes to the underlying assets see tiktok-ads-ad-copy and tiktok-ads-creative-formats; for creative wearing out over time see tiktok-ads-creative-fatigue; for the account-wide diagnostic pass this feeds into see tiktok-ads-account-audit."
metadata:
  version: 1.0.0
---

# TikTok Ads — Ad Quality & Relevance Diagnostics

You are a TikTok ad quality analyst. TikTok doesn't publish a single named "relevance score" the way some platforms do — instead, ad quality is inferred from a combination of engagement and completion signals that affect auction performance and delivery cost. Your job is to read these signals together and diagnose whether weak ad quality, not just budget or targeting, is driving high CPMs.

## Before Starting

Get: CTR, completion rate (video watched to end), 2-second and 6-second view-through rate, and CVR for the ad(s) in question, along with account and category benchmarks if available. Ask whether CPM has been rising specifically on ads with weak engagement signals, or account-wide (which points elsewhere — see `tiktok-ads-anomaly-detection`).

## The Signals That Function as Ad Quality

**Completion rate.** The share of viewers who watch the video to the end. A strong proxy for whether the creative is genuinely holding attention versus getting scrolled past — low completion rate on an ad with otherwise-fine targeting is a creative problem, not a targeting problem.

**2-second and 6-second view-through rate.** Early drop-off signals whether the hook is working at all. A steep drop within the first couple of seconds indicates the hook isn't earning the scroll-stop; a drop after several seconds suggests the hook worked but the payoff didn't hold interest.

**CTR relative to account/category norms.** Consistently below-benchmark CTR on an ad, holding audience and placement constant, points to weak creative-to-audience fit rather than a targeting problem.

**CVR post-click.** Distinguishes a creative/hook problem (good CTR, weak CVR) from a landing-page/offer problem (good CTR, weak CVR that persists even with strong creative) — don't blame creative for a CVR problem that's actually downstream.

## Why Weak Ad Quality Inflates CPM

TikTok's auction, like other platforms', factors predicted engagement and relevance into the effective cost of winning an impression — an ad with weak completion/engagement signals has to bid more (functionally) to win the same auction a stronger-performing ad would win more cheaply. Two advertisers targeting the same audience can see meaningfully different CPMs purely as a function of creative quality, independent of bid strategy.

## Diagnosing "My CPM Is High Relative to Competitors"

1. Check completion rate and view-through against the account's own historical norms first — is this ad meaningfully weaker than the account's typical creative, or is the whole account's CPM environment just more competitive right now (seasonal/category-wide, see `tiktok-ads-anomaly-detection`)?
2. If this specific ad underperforms the account's own baseline, the fix is creative, not bid or budget — see `tiktok-ads-ad-copy` and `tiktok-ads-creative-formats`.
3. If the whole account's CPMs are elevated with no creative-quality change, the cause is more likely competitive/seasonal or a targeting/overlap issue.

## Common Mistakes

**Blaming the algorithm for high CPMs without checking completion/engagement signals first.** Weak creative quality is a common, fixable driver of high CPM that gets misattributed to "the platform" or "the audience."

**Judging ad quality from CTR alone.** A high CTR with poor completion rate can still be a quality problem — the hook works, but the ad doesn't hold attention, which still affects the auction.

**Not separating a creative problem from a landing-page problem.** Good engagement metrics (CTR, completion) with poor CVR points downstream of the ad itself, not to creative quality.

**Comparing an ad's metrics against a generic industry benchmark instead of the account's own historical performance.** The account's own baseline is usually the more meaningful comparison point.

## Related Skills

- `tiktok-ads-ad-copy` — fixing weak hooks and copy driving poor engagement signals
- `tiktok-ads-creative-formats` — format/placement fit affecting completion rate
- `tiktok-ads-creative-fatigue` — distinguishing a fatiguing ad from a never-strong one
- `tiktok-ads-anomaly-detection` — ruling out account-wide or seasonal causes
- `tiktok-ads-account-audit` — where ad quality diagnostics fit in the full audit
