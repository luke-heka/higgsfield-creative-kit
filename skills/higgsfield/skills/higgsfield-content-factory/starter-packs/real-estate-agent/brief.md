# Real Estate Agent, Content Factory Brief

Preconfigured intake for solo real estate agents and small teams running
local listing + buyer-rep work. Built for the AU market by default (2-3%
seller commission, free buyer rep). Edit the variables, leave the
structural defaults alone unless you have data saying otherwise.

---

## Niche (preconfigured)

Solo real estate agent or small team (2-4 agents) in a defined geographic
patch, typically one or two suburbs of an Australian city. Lists
properties in the $400K-$2M range. Sells the agent as a local expert,
not the agency brand. Customer is a suspicious local who sees the same
listing photos on every feed and can't tell who's actually competent.

If you're in the US or post-NAR market, this pack still works but check
the compliance notes in the brief, buyer-rep language has shifted.

If you're a property investor educator (not a licensed agent), use the
coach starter pack when shipped, the content angle is different.

---

## Brand voice (Real estate house voice, not Selr AI)

- Local-first. Names the suburb, the street pattern, the recent sale.
- Confident but not pushy. The agent reads as the calm expert at a
  Saturday open, not the closer.
- Data-anchored. "Median is $1.18M, days-on-market 23, last comp was 12
  Smith Street at $1.22M" beats "market is hot".
- Honest about constraints. "This one sold over reserve because the
  block backs onto reserve land, that's the only reason" beats vague
  market hype.
- AU English. "Suburb" not "neighbourhood", "kerbside" not "curbside",
  "agency" not "brokerage", "vendor" not "seller", "settlement" not
  "closing".

---

## Variables to edit

Fill these in before running the factory. Everything in `{{...}}` gets
swapped automatically across the 40 carousels.

```yaml
agent_name: "{{AGENT_NAME}}"
agency: "{{AGENCY_NAME}}"               # e.g. "Ray White Burleigh"
suburb: "{{PRIMARY_SUBURB}}"            # the one suburb you own
secondary_suburbs: "{{SECONDARY_LIST}}" # 1-3 nearby, comma-separated
state: "{{STATE}}"                      # QLD / NSW / VIC / etc
price_band: "{{PRICE_RANGE}}"           # e.g. "$800K-$1.4M"
typical_property_type: "{{PROPERTY_TYPE}}" # 3-bed house / unit / townhouse / acreage
USP: "{{USP}}"                          # e.g. "20 years in {{suburb}}, off-market network"
lead_magnet: "{{LEAD_MAGNET}}"          # e.g. "Last 5 sales on your street"
lead_magnet_keyword: "{{KEYWORD}}"      # e.g. "STREET" for "DM 'STREET' to get the report"
booking_link: "{{APPRAISAL_LINK}}"
recent_comp_address: "{{RECENT_SALE}}"  # one real recent sale, with permission to reference
language: en-AU
compliance_jurisdiction: AU             # AU / US-post-NAR / NZ
```

---

## Batch size

Default: 5 carousels per batch, 8 batches = 40 carousels over 60 days.

If you're launching a new patch (just moved suburbs or new agency),
compress to 2 batches of 5 = 10 introductory carousels over 14 days.
Set `batches: 2` in the brief override before invoking.

---

## Carousel templates per slot

The factory picks templates per idea card. For real estate, the rotation
is weighted toward price-anchored local data and behind-the-scenes
expertise (not abstract market commentary).

| Template | Frequency | When used |
|----------|-----------|-----------|
| `carousel-case-study` | 30% | "What $X got in {{suburb}} last week" or recent sale walkthrough |
| `carousel-tips` | 25% | "5 things to check before bidding in {{suburb}}" |
| `carousel-cheat-sheet` | 20% | Suburb fact card (median, DOM, school zone, growth) |
| `carousel-myth-bust` | 15% | "Stop believing {{property_myth}}" |
| `carousel-mistakes` | 10% | "5 things first-home buyers in {{suburb}} get wrong" |

Stack-reveal, metaphor-explainer, and reel-cover aren't used for real
estate carousels, they don't convert against the local-expert framing.

---

## Industry defaults (don't edit unless you have data saying otherwise)

- **Hashtag pack** (rotated per post): `#{{suburb}}realestate`,
  `#{{city}}property`, `#realestateaustralia`, `#firsthomebuyer`,
  `#propertyinvestor`, `#justlisted`, plus one method/branded tag.
- **CTA pattern**: "DM '{{lead_magnet_keyword}}' for {{lead_magnet}}"
  or "Book a free 15-minute appraisal at {{booking_link}}". Never
  generic "thinking of selling, DM me", that demotes on TikTok.
- **No market predictions you can't back with data** (ACL compliance
  risk in AU). Anything in the "prices about to do X" hook pattern
  needs a primary source cited in the caption.
- **No vendor private info**: never disclose price expectations,
  motivation to sell, or personal circumstances on video.
- **CASA drone rule (AU)**: any aerial shot over private property
  needs written owner permission. The supporting image prompts in
  `prompts.md` avoid drone-over-property by default, use ground-level
  framing or licensed top-down map overlay.
- **Real recent sales only**: case-study slots need a real recent
  comparable sale with permission to reference. Don't fabricate.

---

## Kill criteria

Stop the factory and reconfigure if:

- You don't have a defined geographic patch (one or two suburbs you own),
  the local-SEO framing collapses. Pick a patch first.
- You have no recent sale to reference for the first case-study slot,
  drop case-study from the first batch and pick it up in batch 03.
- You're in a US post-NAR jurisdiction where buyer-rep language has
  shifted, the CTAs need a manual rewrite, ask for a US-post-NAR brief
  override.
- The agency you work for has a content compliance review process,
  feed the 40 captions through their review before scheduling.

---

## How to invoke

```
/higgsfield-content-factory real-estate-agent
```

Then approve each batch at the gate. The factory will not auto-advance.
