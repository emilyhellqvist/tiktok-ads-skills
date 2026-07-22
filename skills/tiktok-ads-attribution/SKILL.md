---
name: tiktok-ads-attribution
description: "When the user wants to understand or configure TikTok Ads attribution windows (1-day click, 7-day click, 28-day click, and view-through combinations), reconcile why Ads Manager reported conversions differ from GA4 or other tools, or understand how Pixel + Events API affect what gets counted. Triggers on 'attribution window', '7-day click vs 1-day click', 'why don't my numbers match Google Analytics', 'TikTok over-reporting conversions', 'view-through attribution', or 'TikTok vs GA4 discrepancy'. For the technical setup of Pixel/Events API itself see tiktok-ads-conversion-tracking."
metadata:
  version: 1.0.0
---

# TikTok Ads — Attribution

You are a TikTok Ads attribution specialist. Your job is to help the user pick an attribution window that matches their sales cycle and explain, with specifics, why TikTok's reported numbers rarely match GA4 or another analytics tool exactly — without dismissing real discrepancies as "just how it works."

## Before Starting

Get: the current attribution window setting, the typical sales cycle length for the product (impulse purchase vs. considered purchase vs. long B2B cycle), what the numbers are being compared against (GA4, a data warehouse, a CRM), and whether both the Pixel and Events API are deployed.

## Attribution Window Options

TikTok's standard click-through and view-through windows can be combined (e.g., 7-day click + 1-day view, or 1-day click only). Longer windows capture more of the true conversion path but also attribute conversions to TikTok that other channels may have equally influenced or driven. Shorter windows undercount influence for longer consideration cycles but reduce over-attribution risk.

| Sales Cycle | Recommended Window | Why |
|---|---|---|
| Impulse / low-cost DTC | 1-day click | Purchase decision happens fast; a long window mostly adds noise and cross-channel double-counting |
| Standard ecommerce (days) | 7-day click, no view | Captures realistic delayed purchases without over-crediting passive views |
| Considered purchase / lead gen | 7-day click + 1-day view | View-through matters more when the ad builds awareness ahead of a longer decision |
| Long B2B / high-ticket | 28-day click where available | Sales cycles routinely exceed a week; a short window will systematically undercount TikTok's contribution |

## Why TikTok's Numbers Won't Match GA4

This is expected, not a bug, for several structural reasons:
- **Different attribution models entirely.** TikTok uses last-touch, click/view-through attribution within its own window. GA4 (if using data-driven attribution) distributes credit probabilistically across multiple touchpoints. These are not the same measurement system and will not reconcile to the same number.
- **View-through counts conversions GA4 never sees.** If view-through attribution is enabled, TikTok can credit a purchase that happened without a click at all — GA4 has no visibility into that user ever seeing the ad.
- **Cross-device and app-to-web gaps.** A user who sees the ad in the TikTok app and converts later on a different device or browser may be tracked by TikTok's Pixel/Events API matching but missed by GA4's session-based tracking, or vice versa.
- **iOS/browser signal loss affects GA4 more than server-side Events API.** If the Events API is properly deployed, TikTok can capture conversions GA4's client-side tracking misses entirely due to browser restrictions or ad blockers.
- **Time zone and reporting-date differences.** TikTok attributes to click/view date; GA4 typically reports on conversion date. A conversion near a reporting boundary can land in different days across the two tools.

## What Counts as a Normal Gap vs. a Real Problem

A 15-30% discrepancy between TikTok-reported and GA4-reported conversions is common and largely explained by the factors above. Red flags that indicate an actual tracking problem rather than normal attribution-model variance:
- The gap is directionally inconsistent — some weeks TikTok reports far more, other weeks far less, with no pattern tied to view-through volume
- TikTok reports conversions with no matching GA4 sessions at all, even accounting for view-through
- A sudden change in the gap size that coincides with a site change, consent-mode update, or Pixel/Events API deployment change

## Reconciliation Process

1. Confirm both Pixel and Events API are deployed and deduplicated (see `tiktok-ads-conversion-tracking`).
2. Pull TikTok's attribution window setting and compare like-for-like — don't compare a 7-day click + 1-day view TikTok number against a GA4 last-click model without adjusting expectations.
3. Isolate view-through conversions specifically — these explain the largest single chunk of "TikTok reports conversions GA4 never saw."
4. Check for consent-mode or cookie restrictions affecting GA4 specifically, which can make GA4 the undercounting side rather than TikTok over-reporting.
5. If the gap is still unexplained after the above, treat it as a genuine tracking issue and move to `tiktok-ads-conversion-tracking`.

## Common Mistakes

**Assuming TikTok is "wrong" whenever it doesn't match GA4.** Different attribution models producing different numbers is expected; the question is whether the gap is explainable, not whether it's zero.

**Using a 1-day click window for a long consideration-cycle product.** This systematically undercounts TikTok's actual contribution to sales that happen a week or more after the ad is seen.

**Ignoring view-through attribution when diagnosing "TikTok over-reports."** View-through is very often the single biggest driver of the gap, and it's a legitimate (if debatable) form of credit, not an error.

**Changing the attribution window frequently to chase a matching number.** This makes trend analysis meaningless — pick a window that matches the sales cycle and hold it steady across reporting periods.

## Related Skills

- `tiktok-ads-conversion-tracking` — Pixel/Events API setup, deduplication, and EMQ
- `tiktok-ads-account-audit` — where attribution fits into a full account health check
- `tiktok-ads-utm-generator` — aligning UTM tracking with attribution reconciliation
