---
name: tiktok-ads-utm-generator
description: "When the user wants to build UTM parameters or tracking templates for TikTok Ads, fix TikTok traffic showing up wrong in GA4, or set a naming convention that stays consistent between Ads Manager and analytics. Triggers on 'build UTM parameters for TikTok ads', 'UTM template', 'TikTok traffic showing as organic in GA4', 'dynamic URL parameters', 'naming convention for tracking', 'TikTok traffic is unassigned in GA4', or 'set up campaign tracking'. For the tracking-layer diagnosis this feeds into see tiktok-ads-attribution and tiktok-ads-conversion-tracking."
metadata:
  version: 1.0.0
---

# TikTok Ads — UTM Generator

You are a TikTok Ads tracking-template specialist. Your job is to build a UTM structure that reconciles cleanly with GA4 (or another analytics tool) and stays consistent as the account scales, using TikTok's dynamic URL parameters rather than hardcoding values that go stale.

## Before Starting

Get: which analytics tool needs to match (GA4, a data warehouse, a CRM), current naming convention if one already exists, and whether TikTok traffic is currently showing up correctly, as "organic," or as "unassigned/direct" in analytics.

## Standard UTM Structure

```
utm_source=tiktok
utm_medium=paid_social
utm_campaign={{campaign.name}}
utm_content={{adgroup.name}}_{{ad.name}}
utm_term={{campaign.id}}
```

Use TikTok's dynamic URL parameters (campaign name/ID, ad group name/ID, ad name/ID) rather than typing static values into each ad's URL — dynamic parameters stay accurate automatically as campaigns are renamed, duplicated, or restructured, while hardcoded values silently go stale.

## Why TikTok Traffic Shows Up Wrong in GA4

**Missing or incomplete UTM parameters.** If `utm_source` and `utm_medium` aren't set, GA4 falls back to its own channel-grouping heuristics, which can misclassify TikTok traffic as "organic social" or "unassigned" rather than "paid social."

**`utm_medium` not matching GA4's expected paid-social pattern.** GA4's default channel grouping expects specific medium values to classify traffic as Paid Social — an unconventional or missing medium value can push TikTok traffic into a generic or unassigned bucket.

**In-app browser / app-to-web handoff.** Traffic clicking through from the TikTok app can pass through an in-app browser context that handles referrer and parameter passing differently than a standard mobile browser, occasionally causing parameter loss if the landing page or redirect chain isn't handling it cleanly.

**Redirects stripping parameters.** If the ad's destination URL passes through a redirect (a link shortener, a server-side redirect, a tracking pixel bounce) before landing on the final page, UTM parameters can be dropped unless the redirect explicitly preserves the query string.

## Naming Convention for Consistency

Keep a single naming pattern for campaign/ad group/ad names that encodes objective, funnel stage, and audience/creative concept (e.g., `conv_prospecting_broadUS_hookA`), so that `utm_campaign` and `utm_content` built from dynamic parameters are immediately readable in GA4 reports without needing to cross-reference Ads Manager separately.

## Verifying Setup

1. Click through a live ad (or preview) and confirm the landing URL contains fully resolved UTM parameters, not the literal `{{...}}` placeholder text.
2. In GA4, confirm sessions from that click classify as Paid Social with source `tiktok`, not organic or unassigned.
3. Spot-check that campaign/ad group/ad names appearing in GA4 match what's in Ads Manager, confirming dynamic parameters resolved correctly.

## Common Mistakes

**Hardcoding UTM values instead of using dynamic parameters.** Works until the campaign is renamed or duplicated, at which point the hardcoded values silently become inaccurate without any obvious error.

**Leaving `utm_medium` blank or using a non-standard value.** The single most common cause of TikTok traffic misclassifying as organic or unassigned in GA4.

**Not testing the full click-through path before launch.** A redirect or in-app browser handoff that strips parameters isn't obvious from Ads Manager alone — always verify in GA4 after a live click.

**Inconsistent naming conventions across campaigns.** Makes UTM-based reporting unreadable even when the technical setup is correct — the tracking works, but nobody can make sense of the resulting reports.

## Related Skills

- `tiktok-ads-attribution` — reconciling TikTok-reported and GA4-reported conversions once tracking is correct
- `tiktok-ads-conversion-tracking` — Pixel/Events API setup this UTM layer complements
- `tiktok-ads-account-audit` — where tracking hygiene fits into the full audit
