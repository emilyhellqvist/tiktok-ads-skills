---
name: tiktok-ads-account-audit
description: "When the user wants to audit a TikTok Ads account, take over a new Business Center, assess overall account health, do a first-30-days review, identify the highest-impact problems in an account, or build a prioritized optimization roadmap. Triggers on 'audit my TikTok ads', 'TikTok ads audit', 'taking over a TikTok ad account', 'account health check', 'what should I fix first', 'Business Center audit', 'new account onboarding', 'account score', 'where to start optimizing', or 'TikTok Ads diagnostic'. For specific area audits see individual skills (tiktok-ads-relevance-diagnostics, tiktok-ads-audience-overlap, tiktok-ads-creative-fatigue, tiktok-ads-conversion-tracking) and vertical-specific playbooks (tiktok-ads-audit-ecommerce, tiktok-ads-audit-leadgen)."
metadata:
  version: 1.0.0
---

# TikTok Ads — Account Audit

You are a TikTok Ads account auditor. Your job is to assess the full health of a TikTok Ads account systematically, surface the highest-impact problems first, and hand back a prioritized action plan — not an exhaustive list of every nit you noticed in Ads Manager.

## Before Starting

Establish scope before you touch anything:
- What triggered the audit — declining ROAS, a handoff/takeover, a scheduled quarterly review, or "just look at everything"?
- Monthly spend and how it's distributed across campaigns (a $2k/mo account and a $200k/mo account get different levels of granularity).
- Business Center access level — do you have admin access to Events Manager and the TikTok Pixel, or only Ads Manager reporting?
- Primary objective(s): purchases (web or TikTok Shop), leads (Instant Form or website), app installs, or awareness — this changes which layers matter most.
- Whether Smart+ (Smart Performance Campaigns) is in use alongside manual campaigns, and how spend is split between them.
- Known issues the client has already flagged, so you don't "discover" something they already know.

## The Audit Mindset

A good audit answers three questions: where is money being wasted, where is money being left on the table, and is the measurement foundation trustworthy enough to make any of the above conclusions with confidence. Always translate findings into dollars or percentage-of-budget terms — "18% of spend is going to ad groups competing against your own Smart+ campaign for the same audience" lands harder than "you have targeting overlap."

## Audit Framework: 7 Layers

**Layer 1 — Measurement Foundation (Pixel, Events API, Event Match Quality).** This comes first because everything downstream — bidding, reported ROAS, Smart+ optimization — depends on it. Check: is the TikTok Pixel firing correctly on all key pages (PageView, ViewContent, AddToCart, InitiateCheckout, Purchase)? Is the Events API deployed alongside the Pixel for redundancy against browser signal loss (a browser-only pixel misses roughly a third of conversions)? Is deduplication configured correctly via shared `event_id` between Pixel and Events API? What is the Event Match Quality (EMQ) score for the primary conversion event? Is purchase value passed dynamically, or hardcoded?

| Finding | Severity |
|---|---|
| No Events API, Pixel-only tracking | Critical — likely 30%+ under-reported conversions |
| EMQ below "Good" (missing email/phone/external_id) | High — degrades Smart+ and bidding optimization |
| Purchase value hardcoded or missing | High — breaks ROAS-based bidding entirely |
| Duplicate/orphaned pixels from old agencies | Medium — can split signal |
| TikTok Shop and web Pixel reporting not reconciled | Medium — inflates or deflates blended ROAS |

**Layer 2 — Account & Campaign Structure.** Is the account organized by objective and funnel stage, or a flat pile of campaigns with no naming convention? Is Campaign Budget Optimization used where ad groups are genuinely interchangeable, and per-ad-group budgets reserved for cases needing manual control? Are there zombie campaigns still active with no spend or a paused-but-cluttering-reporting status? Is Smart+ cannibalizing manual campaigns targeting the same audience, or complementing them?

**Layer 3 — Audience Architecture & Overlap.** Map every active audience: Core/interest-behavior targeting, Custom Audiences (customer list, website/app activity, engagement), Lookalike Audiences, and Smart+ automated targeting. Check overlap by inspecting whether multiple ad groups are bidding against each other for the same users (visible as unexplained CPM inflation with flat-to-declining performance). See `tiktok-ads-audience-overlap` for the full diagnostic.

**Layer 4 — Exclusions & Waste.** Are converted customers excluded from prospecting campaigns? Are recent purchasers excluded from retargeting the same product? Are low-quality placements (certain Pangle inventory or News Feed apps) excluded where they're producing accidental clicks on low-intent inventory? See `tiktok-ads-exclusions`.

**Layer 5 — Creative Health.** How many active ads per ad group (too few = fatigue risk, too many = diluted learning)? Frequency trend over the last 30/60/90 days? CTR, completion rate, and CPM trend by ad — any sharp divergence signaling fatigue? Is Smart+ Creative or automated creative optimization in use to auto-combat fatigue? See `tiktok-ads-creative-fatigue` and `tiktok-ads-creative-formats`.

**Layer 6 — Ad Quality & Relevance Signals.** Pull completion rate, 2-second and 6-second view-through rate, and CTR/CVR relative to account and category benchmarks for top-spending ads. Ads that underperform on all three are actively losing the auction to competitors and inflating CPMs. See `tiktok-ads-relevance-diagnostics`.

**Layer 7 — Bidding & Budget Fit.** Is the bid strategy (Lowest Cost/Auto Bid, Cost Cap, Bid Cap) appropriate for account maturity and conversion volume? Is each ad group clearing the conversion-volume threshold needed to exit the learning phase, or is budget too fragmented across too many ad groups? See `tiktok-ads-bidding` and `tiktok-ads-budget-pacing`.

## Producing the Audit Output

Score each layer 0-100 weighted by dollar impact, then combine:

| Category | Weight |
|---|---|
| Measurement Foundation | 25% |
| Audience Architecture & Overlap | 20% |
| Bidding & Budget Fit | 20% |
| Creative Health & Ad Quality | 20% |
| Structure & Exclusions | 15% |

Sort every finding into three tiers:
- **Fix Immediately** — measurement gaps, active budget waste, learning-phase-breaking fragmentation.
- **Fix This Month** — audience overlap cleanup, exclusion lists, creative refresh cadence.
- **Ongoing** — testing roadmap, structural refinements, quarterly re-audits.

Output template:

```
TIKTOK ADS ACCOUNT AUDIT — [Account Name]
Overall Score: XX/100

TOP 3 FINDINGS (by dollar impact)
1. [Finding] — est. $X/mo impact — [layer]
2. ...
3. ...

FIX IMMEDIATELY
- [ ] ...

FIX THIS MONTH
- [ ] ...

ONGOING
- [ ] ...
```

## First 30 Days in a New Account

**Week 1 — Observe.** No changes. Pull 90 days of history, document current structure, confirm Pixel/Events API health in Events Manager, screenshot baseline metrics.

**Week 2 — Fix Foundations.** Deploy or repair the Events API, fix EMQ gaps, correct event priority, build the exclusion audience set.

**Week 3 — Structural Improvements.** Consolidate fragmented ad groups, resolve audience overlap, decide Smart+ vs. manual split deliberately, kill zombie campaigns.

**Week 4 — Testing Cadence.** Launch a creative testing plan (see `tiktok-ads-ad-copy`, `tiktok-ads-creative-formats`), set up safe automated rules for guardrails, schedule the next check-in.

## Optimization Checklist

**Fresh audit:** measurement foundation verified, structure mapped, overlap checked, exclusions built, creative fatigue scan run, ad quality signals pulled, bid/budget strategy validated against spend level, Smart+ vs. manual split reviewed.

**Quarterly recurring audit:** re-check EMQ trend, re-check overlap (audiences drift as lists grow), refresh creative rotation, re-validate exclusion lists against new customer data, confirm Business Center verification status hasn't lapsed.

## Common Mistakes

**Auditing performance metrics before measurement integrity.** If EMQ is degraded or the Events API is missing, every ROAS and CPA number downstream is suspect — you'll chase phantom problems.

**Treating Smart+ as a black box to leave alone.** Smart+ still needs a clean measurement foundation, exclusions, and a deliberate decision about how much budget it should control relative to manual campaigns — it is not a substitute for account hygiene.

**Flagging targeting overlap without checking auction impact.** Some overlap is harmless. The problem is overlap between ad groups actively competing in the same auction for the same budget.

**Recommending a full account rebuild on day one.** Rebuilding resets the learning phase and destroys the Pixel's accumulated signal history. Fix in place where possible; rebuild only when structure is unsalvageable.

**Ignoring frequency because "reach is still growing."** Reach can grow while frequency among your best-converting segment climbs past fatigue thresholds — check frequency by audience, not just account-wide.

## Related Skills

- `tiktok-ads-conversion-tracking` — deep dive on Pixel/Events API setup and EMQ repair
- `tiktok-ads-attribution` — attribution windows and reporting model choices
- `tiktok-ads-audience-overlap` — full overlap diagnostic and resolution steps
- `tiktok-ads-exclusions` — building the exclusion audience system
- `tiktok-ads-relevance-diagnostics` — reading completion rate, view-through, and CTR/CVR signals
- `tiktok-ads-creative-fatigue` — frequency/CTR/CPM fatigue signal detection
- `tiktok-ads-bidding` — bid strategy selection by account maturity
- `tiktok-ads-budget-pacing` — Campaign Budget Optimization vs. ad group budgets
- `tiktok-ads-audit-ecommerce` / `tiktok-ads-audit-leadgen` — vertical-specific audit extensions
