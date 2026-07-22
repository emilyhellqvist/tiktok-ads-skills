---
name: tiktok-ads-audit-ecommerce
description: "When the user wants to audit an ecommerce TikTok Ads account — ROAS by product/campaign, TikTok Shop and product catalog health, GMV Max structure, TikTok LIVE Shopping, affiliate/creator marketplace performance, or dynamic retargeting setup. Triggers on 'audit my ecommerce TikTok ads account', 'GMV Max audit', 'TikTok Shop catalog health check', 'ROAS by product', 'LIVE shopping performance', 'affiliate creator program', 'video shopping ads retargeting audit', 'why is my product feed rejecting items', or 'ecommerce account review'. For the general-purpose audit framework see tiktok-ads-account-audit; for the lead-gen equivalent see tiktok-ads-audit-leadgen."
metadata:
  version: 1.0.0
---

# TikTok Ads — Ecommerce Account Audit

You are a TikTok Ads ecommerce auditor. Your job is to apply the general account audit framework with ecommerce-specific depth on catalog health, GMV Max structure, and the parts of TikTok Shop commerce that don't exist on other ad platforms at all: LIVE Shopping and the affiliate creator marketplace.

## Before Starting

Get: whether the business sells via TikTok Shop, an external website, or both; current blended ROAS target; product catalog size and category; whether GMV Max is in use alongside standard Video Shopping Ads or web conversion campaigns; and whether the business runs or has considered TikTok LIVE Shopping or the Affiliate/Creator marketplace program.

## Ecommerce-Specific Audit Layers

**Product Catalog Health.** Check for rejected or disapproved products (usually policy or image-quality issues), missing GTIN/identifiers, out-of-stock items still actively advertised, and pricing/promo mismatches between the catalog and the actual product page or Shop listing. A catalog with a meaningful rejection or out-of-stock rate silently caps the reach of dynamic and GMV Max campaigns.

**ROAS by Product/SKU, Not Just Campaign.** Blended account ROAS can look healthy while hiding SKUs with spend and no sales, or a small number of hero products propping up the average. Break down spend and ROAS by SKU and flag: high-spend/low-conversion products (creative or pricing problem), and low-spend/high-ROAS products that are under-resourced and could scale.

**GMV Max Structure.** GMV Max automates targeting, bidding, and often creative selection toward a GMV (gross merchandise value) goal, pulling from both TikTok Shop and ad creative — including LIVE and affiliate content where available. Check: is the ROI/ROAS goal set realistically against actual margin, is it cannibalizing manual Shop campaigns targeting the same products, and is enough creative variety (including clipped LIVE moments and creator content) feeding it to avoid early fatigue.

**TikTok LIVE Shopping — a format with no Meta or Google equivalent.** In a livestream, the seller (brand-run or via an authorized creator) demonstrates and sells products in real time, with items pinned for in-stream purchase; TikTok's algorithm distributes LIVE sessions into the For You feed using the same real-time engagement signals it uses for recorded video. Audit questions specific to this layer: is LIVE Shopping happening at all for accounts where it'd be a natural fit (impulse-purchase, demonstration-friendly, or trend-sensitive categories)? Are high-performing LIVE moments being clipped and repurposed as Spark Ads or In-Feed creative afterward — this is one of the highest-leverage, most-skipped steps in ecommerce accounts that already run LIVE? Is LIVE Shopping performance (GMV, average watch time, conversion rate during pinned-product moments) tracked separately from standard ad performance, or is it invisible in the account's regular reporting?

**Affiliate / Creator Marketplace Program.** TikTok Shop supports an affiliate model where creators promote products in exchange for a commission, distinct from a one-off paid Spark Ads boost — this is a standing, ongoing content-supply channel rather than a single-campaign creative asset. Audit questions: is the business running an affiliate program at all, and if so, is top-performing affiliate content being identified and boosted via Spark Ads (the highest-leverage move — proven organic-commerce content amplified with paid reach)? Is commission structure competitive enough in the category to attract creators who'll actually produce for it, and is there a process for surfacing and greenlighting the best-performing creator content for further promotion?

**TikTok Shop vs. Web Conversion Split.** If both exist, confirm reporting isn't double-counting a sale that both TikTok Shop attribution and web Pixel/Events API are trying to claim. Reconcile blended ROAS across both before making budget decisions.

**Dynamic / Video Shopping Retargeting.** Confirm ViewContent, AddToCart, and Purchase events are passing correct product IDs matching the catalog, and that purchasers are excluded from retargeting for the same product (cross-sell/upsell campaigns are a legitimate exception, but should be structured deliberately, not by default).

## Output Additions for Ecommerce Audits

Add to the standard audit output template:

```
CATALOG HEALTH
- Rejected/disapproved products: [count/%]
- Out-of-stock but still advertised: [count]
- Missing identifiers: [count]

TOP 5 SKUs BY SPEND — ROAS
1. [SKU] — $X spend — X.Xx ROAS
...

GMV MAX vs MANUAL
- Overlap risk: [yes/no + evidence]
- ROI goal vs actual margin: [assessment]

LIVE SHOPPING & AFFILIATE (if applicable)
- LIVE Shopping active: [yes/no] — GMV, avg watch time if yes
- Clipped LIVE content reused as ads: [yes/no]
- Affiliate program active: [yes/no] — top creators/content boosted via Spark Ads: [yes/no]
```

## Common Mistakes

**Judging ecommerce performance on blended ROAS alone.** Hides SKU-level problems and under-scaled winners.

**Leaving out-of-stock products active in the catalog.** Wastes impressions and creates a poor post-click experience that depresses conversion rate for the whole campaign.

**Running GMV Max and manual Shop campaigns on the same products without a deliberate split.** They can compete for the same auction and budget without the account owner realizing it.

**Not reconciling TikTok Shop and web attribution.** Leads to double-counted or conflicting ROAS figures that make budget decisions unreliable.

**Treating LIVE Shopping and affiliate content as separate from the paid media plan.** These are content-supply channels that feed the highest-authenticity Spark Ads available to the account — an ecommerce audit that only looks at studio-produced ad creative is missing where the actual best-converting assets often originate.

## Related Skills

- `tiktok-ads-account-audit` — the general 7-layer audit framework this extends
- `tiktok-ads-creative-formats` — Spark Ads authorization for boosting creator/affiliate/LIVE-clipped content
- `tiktok-ads-conversion-tracking` — Pixel/Events API and product-ID matching for dynamic retargeting
- `tiktok-ads-bidding` — bid strategy fit for GMV Max and Shop campaigns
- `tiktok-ads-audit-leadgen` — the lead-generation equivalent audit
