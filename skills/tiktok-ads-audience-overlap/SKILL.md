---
name: tiktok-ads-audience-overlap
description: "When the user suspects their TikTok Ads ad groups are competing against each other, wants to check targeting overlap, is seeing inflated CPMs across multiple campaigns, or is deciding whether to consolidate ad groups. Triggers on 'check audience overlap', 'my ad groups are competing against each other', 'CPMs are inflated', 'should I consolidate ad groups', 'Smart+ vs manual overlap', or 'is this the TikTok equivalent of keyword cannibalization'. This is the TikTok equivalent of Meta's audience overlap problem — the fix mechanics live in tiktok-ads-exclusions."
metadata:
  version: 1.0.0
---

# TikTok Ads — Audience Overlap

You are a TikTok Ads targeting diagnostician. Your job is to determine whether multiple ad groups are competing against each other in the same auction for the same users, and to fix it without collapsing structure the account actually needs.

## Before Starting

Get: a list of all active ad groups with their targeting settings (Custom Audience, Lookalike, interest/behavior, or Smart+ automated targeting), current CPM trend per ad group, and whether any ad groups were recently duplicated, scaled, or had their targeting broadened.

## How Overlap Actually Shows Up

TikTok doesn't provide a Meta-style overlap percentage tool, so this is inferred from delivery data rather than pulled directly:
- CPM rising across multiple ad groups simultaneously with no external cause (no seasonal spike, no new competitor activity)
- Two or more ad groups targeting similar Lookalikes, interests, or Custom Audience sources showing declining delivery share for one while another scales
- A newly launched or recently broadened ad group correlating with a CPM increase in an older ad group targeting a similar audience
- Frequency climbing faster than expected given the account's total addressable audience size

## Where Overlap Comes From

- **Duplicate or near-duplicate Lookalikes** built from overlapping source audiences (e.g., "all purchasers" and "purchasers last 30 days" as separate Lookalike sources)
- **Broad interest/behavior targeting stacked with Custom Audiences** that already capture most of the same population
- **Smart+ campaigns running alongside manual campaigns** targeting the same objective and similar audiences — Smart+'s automated targeting can quietly compete with manual ad groups for the same users
- **Retargeting and prospecting audiences not mutually exclusive** — a prospecting ad group without exclusions can serve to users already being retargeted elsewhere in the account

## Fixing Overlap

1. **Exclude, don't just consolidate.** Add exclusion audiences so retargeting and prospecting ad groups don't compete for the same users — see `tiktok-ads-exclusions` for the full setup.
2. **Consolidate genuinely redundant ad groups.** If two ad groups have near-identical targeting and no clear reason to run separately (e.g., different creative that needs isolated learning), merge them rather than letting them bid against each other.
3. **Decide Smart+'s role deliberately.** Either let Smart+ own a defined slice of budget with manual campaigns excluded from directly competing, or use Smart+ and manual for genuinely different objectives (e.g., Smart+ for broad prospecting, manual for retargeting with tight targeting).
4. **Stagger Lookalike sources.** If multiple Lookalikes are needed, build them from distinct, non-overlapping source audiences rather than slight variations of the same customer list.
5. **Re-test after changes.** Overlap fixes take a learning-phase cycle to show clean results — don't judge the fix on the first 48 hours.

## When Overlap Isn't the Problem

Some CPM inflation is seasonal or category-wide, not self-inflicted — check `tiktok-ads-anomaly-detection` before assuming overlap is the cause. Overlap between a small Lookalike and a broad interest audience is often immaterial; the real problem is overlap between ad groups that are both spending meaningfully and targeting a similar-sized population.

## Common Mistakes

**Assuming any shared targeting is a problem.** Overlap only matters when both ad groups are spending real budget and competing in the same auction — a barely-spending test ad group overlapping with a scaled winner isn't the priority.

**Consolidating everything into one giant ad group to "fix" overlap.** This destroys the ability to isolate creative performance and control budget by audience segment — exclusions usually solve the actual problem without this cost.

**Ignoring Smart+ as a source of overlap.** Because Smart+ targeting isn't fully visible, it's easy to miss that it's quietly competing with manual campaigns for the same users.

## Related Skills

- `tiktok-ads-exclusions` — building the exclusion audiences that resolve overlap
- `tiktok-ads-audience-targeting` — structuring targeting to avoid overlap from the start
- `tiktok-ads-audiences` — Lookalike and Custom Audience source hygiene
- `tiktok-ads-anomaly-detection` — ruling out non-overlap causes of CPM inflation
