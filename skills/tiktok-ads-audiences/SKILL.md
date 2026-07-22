---
name: tiktok-ads-audiences
description: "When the user wants a deep dive on TikTok audience types — Custom Audiences (customer lists, website/app activity, engagement), Lookalike Audiences, and Smart+ automated targeting — including source quality, similarity/sizing tradeoffs, and refresh/decay timing. Triggers on 'lookalike audience', 'custom audience', 'smart+ targeting', 'audience source list', 'how big should my lookalike be', 'audience refresh', 'source audience decay', or 'which audience type should I use'. For structuring targeting decisions see tiktok-ads-audience-targeting; for excluding converters/overlap cleanup see tiktok-ads-exclusions and tiktok-ads-audience-overlap."
metadata:
  version: 1.0.0
---

# TikTok Ads — Audiences (Custom, Lookalike, Smart+)

You are a TikTok audience architect. Your job is to get the source data and sizing right before targeting strategy is even discussed — a targeting plan built on a low-quality source audience underperforms regardless of how well the funnel stages are structured.

## Before Starting

Get: what first-party data sources are available (customer list, Pixel/Events API events, SDK app events, engagement data), how large each source is, and how frequently they're currently refreshed (if at all).

## Custom Audiences

**Customer list.** Uploaded and matched via hashed PII. Quality depends on match rate — larger lists with clean email/phone data match better. Segment by recency and value where possible (e.g., "purchasers last 90 days" vs. "purchasers all-time") rather than one undifferentiated list.

**Website/app activity.** Built from Pixel and Events API events (ViewContent, AddToCart, InitiateCheckout, Purchase) or SDK app events. Requires the measurement foundation to actually be healthy — see `tiktok-ads-conversion-tracking` — a Custom Audience built on a broken Pixel is built on incomplete data.

**Engagement audiences.** Built from video views, profile visits, likes/comments/shares, or Spark Ads engagement. Often underused; this tier costs nothing to build and captures warm intent signal without needing site/app tracking at all.

## Lookalike Audiences

A Lookalike models new users similar to a source Custom Audience. Source quality matters more than any other variable:

| Source | Lookalike Quality |
|---|---|
| All-time purchasers | Strong — highest-intent, most specific signal |
| Purchasers, last 90 days | Strong — recent behavior, avoids stale patterns |
| Add-to-cart / checkout-initiated | Moderate — intent signal without confirmed conversion |
| All site visitors | Weak — too broad, dilutes the "similarity" the Lookalike is modeling |
| Video views / engagement only | Weak-to-moderate — better than visitors, still not purchase intent |

**Sizing.** A source audience that's too small produces an unstable, low-quality Lookalike; too large and it loses specificity. Prefer a moderately-sized, high-intent source (e.g., purchasers) over a large, low-intent one (e.g., all visitors) even if the resulting Lookalike is smaller.

## Refresh and Decay

Source audiences decay — a customer list or event-based audience from six months ago reflects a stale customer profile, especially for accounts with evolving products or seasonal customer bases. Refresh source audiences and their derived Lookalikes on a regular cadence (monthly for fast-moving accounts, quarterly at minimum) rather than setting them once and leaving them.

## Smart+ Automated Targeting

Smart+ removes manual audience definition and lets TikTok's system find users based on the optimization goal and available signal. It performs best with:
- A healthy measurement foundation (Pixel + Events API, good EMQ)
- Sufficient historical conversion volume for the system to model against
- A well-defined product/offer so creative and landing page match what the algorithm is optimizing toward

It performs worse in brand-new accounts with no conversion history, or where measurement gaps mean the system is optimizing on incomplete signal.

## Common Mistakes

**Building a Lookalike from a low-intent source because it's the largest list available.** A smaller, high-intent source (purchasers) almost always outperforms a larger, low-intent one (all visitors) as a Lookalike seed.

**Never refreshing source audiences.** Stale Lookalikes drift away from the account's actual current customer base, especially after a product line change or a shift in who's converting.

**Layering Smart+ on top of a broken measurement foundation.** Smart+ is only as good as its signal — fix the Pixel/Events API and EMQ before expecting it to outperform manual targeting.

**Treating engagement audiences as an afterthought.** They're free to build and often an underused mid-funnel layer between cold prospecting and hard retargeting.

## Related Skills

- `tiktok-ads-audience-targeting` — turning these audience types into a funnel-stage strategy
- `tiktok-ads-conversion-tracking` — the Pixel/Events API health that Custom Audiences and Smart+ depend on
- `tiktok-ads-exclusions` — excluding converters and overlapping segments
- `tiktok-ads-audience-overlap` — diagnosing self-competition between derived audiences
