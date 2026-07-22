# TikTok Ads Skills for Claude

21 skills that give Claude expert-level TikTok Ads knowledge — audit frameworks, creative-fatigue detection, audience/placement diagnostics, budget pacing, bid strategy, measurement setup, and more. Built to mirror the structure of [meta-ads-skills](https://github.com/emilyhellqvist/meta-ads-skills), adapted for TikTok's ad model (Smart+, Spark Ads/TopView/In-Feed, Pangle, TikTok Shop/GMV Max, Events API).

Companion setup guide: see the [Ultimate TikTok Ads Skills for Claude Desktop](https://github.com/emilyhellqvist/tiktok-ads-skills) setup guide for how to connect live TikTok Ads data to Claude Desktop before installing these skills.

## Install

**Option A — Claude Desktop (recommended):** Settings → Skills → Add, and add each folder inside `skills/` one at a time.

**Option B — npx (Claude Code):**
```bash
npx skills add emilyhellqvist/tiktok-ads-skills
```
Select all 21 skills when prompted, and choose Global scope.

## Skills

| Skill | What it covers |
|---|---|
| `tiktok-ads-account-audit` | Full 7-layer account health audit and first-30-days playbook |
| `tiktok-ads-ad-copy` | Hooks, captions, and copy frameworks by funnel stage |
| `tiktok-ads-anomaly-detection` | Diagnosing sudden CPM/CPA/ROAS moves |
| `tiktok-ads-attribution` | Attribution windows and reconciling TikTok vs. GA4 numbers |
| `tiktok-ads-audience-overlap` | Diagnosing and fixing ad groups competing against each other |
| `tiktok-ads-audience-targeting` | Core/Custom/Lookalike/Smart+ targeting strategy by funnel stage |
| `tiktok-ads-audiences` | Custom Audience and Lookalike source quality, sizing, refresh |
| `tiktok-ads-audit-ecommerce` | TikTok Shop, GMV Max, and catalog-specific audit extension |
| `tiktok-ads-audit-leadgen` | Instant Form vs. website forms, lead quality, CPL benchmarking |
| `tiktok-ads-automated-rules` | Safe automation patterns and guardrails |
| `tiktok-ads-bidding` | Lowest Cost / Cost Cap / Bid Cap selection and learning-phase mechanics |
| `tiktok-ads-budget-pacing` | Campaign Budget Optimization vs. ad-group budgets, sizing, reallocation |
| `tiktok-ads-conversion-tracking` | Pixel + Events API setup, deduplication, Event Match Quality |
| `tiktok-ads-creative-fatigue` | Frequency/CTR/completion-rate fatigue diagnosis and refresh cadence |
| `tiktok-ads-creative-formats` | Spark Ads, In-Feed, TopView, Collection formats and specs |
| `tiktok-ads-exclusions` | Exclusion audiences and placement exclusions |
| `tiktok-ads-experiments` | Split Test design and statistical validity |
| `tiktok-ads-placement-mining` | TikTok vs. Pangle vs. News Feed app placement analysis |
| `tiktok-ads-relevance-diagnostics` | Reading completion rate, view-through, and CTR/CVR as quality signals |
| `tiktok-ads-segmentation` | Device/placement/demographic/day-of-week breakdown analysis |
| `tiktok-ads-utm-generator` | UTM templates and GA4 reconciliation |

## License

MIT
