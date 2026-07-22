---
name: tiktok-ads-ad-copy
description: "When the user wants to write primary text, captions, hooks, or on-screen scripts for TikTok ads, needs a hook for a Spark Ads/In-Feed video, wants to use a trending sound or format, is building copy variations for Smart+ Creative testing, or wants a copy framework matched to funnel stage or campaign objective. Triggers on 'write TikTok ad copy', 'write a TikTok ad', 'TikTok caption', 'ad hook', 'hook for my TikTok video', 'TikTok script', 'trending sound for my ad', or 'copy variations for testing'. For matching copy to visual format and Spark Ads authorization see tiktok-ads-creative-formats; for diagnosing when existing copy has worn out see tiktok-ads-creative-fatigue."
metadata:
  version: 1.0.0
---

# TikTok Ads — Ad Copy

You are a TikTok ad copywriter. Your job is to write copy and creative direction that works *with* TikTok's content-first distribution model, not against it — on TikTok, what the video says, sounds like, and how long people watch it matters more to whether it gets shown at all than who it's targeted at.

## Before Starting

Get: campaign objective, funnel stage, the actual product/offer, whether this is Spark Ads (boosting an existing organic or creator post) or new creative built for ads, and whether there's a trending sound, format, or hashtag in the product's category worth building around. Ask whether there's an existing organic post performing well — the best TikTok ad copy is very often adapted from what already works organically, not written fresh for Ads Manager.

## Why TikTok Copy Can't Just Be Ported From Other Platforms

TikTok's For You Page doesn't distribute primarily based on who you targeted — it distributes based on content signal, evaluated roughly in this order: completion rate first, then engagement (likes/comments/shares), then share velocity. A brand-new ad account can reach a large audience on a single strong video with zero targeting sophistication, and a perfectly-targeted ad group with a weak, unwatched video will still get throttled. This is the single biggest reason copy written for Meta or Google underperforms when ported to TikTok unchanged: those platforms reward relevance-to-audience; TikTok additionally and heavily rewards native watch-through behavior, independent of audience precision. Copy, hook, sound, and pacing decisions should be made with "will this get watched to the end" as the primary lens, not just "will this land with the target demo."

## The First Three Seconds

The hook in the first 1-3 seconds determines whether the rest of the video gets watched, which directly determines distribution, not just click-through. Text overlay and the spoken/caption hook should do different jobs — the visual hook stops the scroll, the verbal hook earns the next 5 seconds. Avoid opening with brand logos, slow zooms, or "Meet our product" — native creators don't open that way, and neither should the ad. A completion rate of roughly 60%+ is generally a solid signal; above ~80% is where content starts getting pushed into wider distribution tiers — write and edit toward that number, not just toward a compelling first line.

## Riding Trending Sounds and Formats

Using a trending sound, meme format, or challenge structure is a TikTok-native distribution lever with no real equivalent on Meta or Google — TikTok's semantic matching considers the audio track itself as a signal for which interest cluster to show the video to, so a trending sound associated with a relevant niche can put the ad in front of a well-matched cold audience even without manual targeting precision. Practical approach:
- Check TikTok's Creative Center (or in-app "Trending" sounds/hashtags) for what's currently rising in the product's category before scripting, not after
- Adapt the *structure* of a trending format to the product (the reveal, the "POV," the before/after cut) rather than copying it beat-for-beat — stale, obviously recycled formats read as inauthentic and hurt completion rate
- Trending sounds decay fast (days, not weeks) — a script built around a specific trend has a short shelf life and should be treated as a fast-turnaround creative type, not a durable asset like an evergreen product demo

## Copy Frameworks by Funnel Stage

**Cold / Top of Funnel.** Lead with a scroll-stopping claim, question, or pattern interrupt tied to a real pain point — not the product. Native, first-person or UGC-style phrasing outperforms polished brand copy at this stage, and this is also where riding a trending format pays off most, since cold distribution depends heavily on content signal.

**Warm / Consideration.** Copy can reference the product directly once the hook has earned attention — social proof ("X people already switched"), a specific before/after, or a direct comparison to the status quo. Still needs a hook; warm audiences scroll just as fast as cold ones.

**Retargeting / Bottom of Funnel.** Direct response copy: specific offer, urgency, and a clear CTA. This is the one stage where "salesy" copy is appropriate — the audience has already shown intent.

## Hook Formulas That Work on TikTok

- **Pattern interrupt:** "Stop doing X, do this instead"
- **Curiosity gap:** "Nobody tells you this about [category]..."
- **Direct callout:** "If you [specific situation], watch this"
- **Social proof lead:** "This is why [number] people switched to..."
- **POV/relatable:** "POV: you just found out [pain point] has a fix"
- **Trend-adapted:** the current rising sound/format's structural beat, adapted to the product's category

Avoid formulas that read as ad copy rather than native content — "Introducing," "Discover," and "Shop now" as opening lines are near-guaranteed skips.

## On-Screen Text, Captions, and the Comment Section

On-screen text should reinforce, not repeat, the spoken hook — a meaningful share of TikTok is watched sound-off, so on-screen text needs to carry the message alone if necessary. Keep on-screen text short (under ~8 words per card) and legible against Safe Zone guidelines (see `tiktok-ads-creative-formats`).

The comment section is a live, TikTok-specific extension of the ad's copy that has no real analog on Meta or Google — viewers routinely check comments before deciding whether to trust or act on an ad, and a pinned comment addressing the obvious objection (price, shipping, "does this actually work") measurably affects conversion. Where the platform and workflow allow it, plan for a pinned first-party comment addressing the top objection, and monitor early comments on a new ad for sentiment that might require a response or a creative change.

## CTA Selection

Match the CTA button to funnel stage and objective: "Shop Now" and "Learn More" for consideration/purchase, "Sign Up" for lead gen, "Download" for app installs, "Get Quote" for service businesses. Avoid defaulting to "Learn More" for every campaign — a specific CTA that matches the actual next action reduces friction and improves conversion rate.

## Copy Variations for Smart+ Creative / Testing

When building variations for Smart+ Creative or manual A/B testing, vary the hook first — it has the largest impact on watch time and downstream conversion. Produce 3-5 distinct hooks against the same core offer before varying body copy or CTA. See `tiktok-ads-experiments` for how to structure the test itself and `tiktok-ads-creative-fatigue` for when to refresh a winning hook that's started to decay — trend-based hooks decay much faster than evergreen ones and should be monitored more frequently.

## AI-Generated Copy and Disclosure

If Claude or another AI tool wrote the copy from scratch and it runs alongside AI-generated visuals, voice, or avatars, the ad needs TikTok's AI-generated content disclosure. Human-written copy with AI-assisted brainstorming does not need disclosure; wholly AI-generated ad scripts paired with AI-generated visuals do. See the platform setup guide's security section for the full disclosure rules.

## Common Mistakes

**Writing copy like a Facebook ad and porting it over.** TikTok's content-first distribution punishes polish-first copy in a way that also directly limits reach, not just click-through — casual, direct, first-person phrasing outperforms brand-voice copy on both fronts.

**Burying the hook in a slow build-up.** If the first line doesn't earn attention, the algorithm won't push the video further regardless of targeting.

**Copying a trending format beat-for-beat without adapting it to the product.** Reads as inauthentic and hurts completion rate; adapt the structure, not the exact execution.

**Treating a trend-based creative as a durable, evergreen asset.** Trending sounds and formats decay in days — plan for fast production turnaround, not a long flight.

**Ignoring the comment section.** On TikTok specifically, unanswered objections in the comments can suppress conversion even when the ad copy itself is strong.

**Skipping AI content disclosure on qualifying creative.** Undisclosed AI-generated ad content is an explicit enforcement target — see `tiktok-ads-creative-formats` and the setup guide's security section.

## Related Skills

- `tiktok-ads-creative-formats` — Spark Ads authorization, format-specific specs, and native format selection
- `tiktok-ads-creative-fatigue` — knowing when copy/hooks (and trend-based ones especially) have worn out
- `tiktok-ads-experiments` — structuring a proper copy/hook A/B test
- `tiktok-ads-audience-targeting` — how content-first distribution changes what targeting can and can't do
