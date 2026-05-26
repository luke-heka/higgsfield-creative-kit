# Template: Testimonial Ad Three-Treatment Dispatcher (Skeleton 5 Reference)

> Canonical structure for `prompts/03b-testimonial-ad-treatment.md` output.
> References `../shared/higgsfield-prompt-skeletons.md` Skeleton 5. Pick
> ONE treatment per theme, don't blend.

---

## Decision rule

| Theme character | Treatment |
|---|---|
| Emotional, identity-based, "I needed someone in my corner" | **A: Talking-head reconstruction** |
| Technical, measurable, "saves 3 hours/week" | **B: Text-on-b-roll with VO** |
| Switching, comparison, "I came from X to Y" | **C: Side-by-side before/after** |
| Multiple characters apply | Pick the dominant. If genuinely tied, default to **B** (lowest risk, no disclosure burden) |

---

## Treatment A: Talking-head reconstruction

**Visual:** AI-rendered "customer" delivers the verbatim quote to camera.

**MANDATORY:** On-screen disclosure text "Represents a customer profile,
not a specific person", bottom-corner placement, full duration of the
talking-head shot. Non-negotiable for ethics + ad-platform compliance.

### Higgsfield prompt skeleton (Skeleton 5A)

```
[DURATION] [ASPECT, usually 5-8s 9:16],
[SHOT TYPE, usually medium close-up],
an [AGE BAND, GENDER if relevant] [ROLE DESCRIPTOR, "podcast producer in their 40s"]
sitting in [CONTEXTUAL SETTING, "a sunlit home office with a microphone
barely visible at frame edge"],
speaking to camera with [EMOTIONAL REGISTER, "calm, slightly tired,
certain"], one continuous take,
[LIGHTING, usually soft, side-key, practical],
[CAMERA, usually static or 2-inch slow drift],
[LENS / DEPTH, 50mm portrait, shallow DOF],
palette: [3 ANCHORS, calm/grounded],
texture: [SUBTLE FILMIC],
audio: customer voice delivering the verbatim quote
"[VERBATIM QUOTE]" in a natural unhurried pace,
on-screen disclosure: "Represents a customer profile, not a specific
person" small bottom-right corner,
EXCLUDE: AI-glossy skin, plastic shine, over-acted expressions,
stock-photo poses, fake smiles, dramatic lighting, studio backdrop,
perfect studio lighting, lower-third graphics with brand logo,
on-screen captions covering the face, hyper-saturated colours, gradient
backgrounds, drop shadows, emoji, watermark, overlay text unless
explicitly requested, hashtag overlays, generic agency aesthetic
```

### Field-by-field discipline

- **AGE BAND + GENDER:** match the customer demographic loosely. Don't
  impersonate the actual reviewer.
- **ROLE DESCRIPTOR:** match the reviewer's role from `raw-reviews.json`
  but generalise. "Podcast producer in their 40s" not "Sarah, 42, host
  of [show name]".
- **CONTEXTUAL SETTING:** the customer's actual work context. Match
  to the review's `problems_solving` field, if they talked about
  internal podcasts, set in an office. If indie hosting, set in a home
  studio.
- **EMOTIONAL REGISTER:** match the quote's tone. "I needed someone in
  my corner" = calm, slightly tired, certain. "Don't punish me for
  growing" = quietly frustrated, then resolved.

### Disclosure ENFORCEMENT

If the disclosure text is missing from the prompt OR the deliverable,
STOP. Add it. Re-deliver. There are no exceptions to this rule, it's
both an ethics requirement (you're not impersonating a real person)
and an ad-platform requirement (Meta + TikTok + YouTube all reject
AI-rendered testimonials without disclosure).

---

## Treatment B: Text-on-b-roll with VO

**Visual:** Relevant B-roll (the customer's actual world), NO people in
frame. Quote appears as on-screen text. VO reads the quote.

### Higgsfield prompt skeleton (Skeleton 5B)

```
[DURATION] [ASPECT, usually 5-8s 9:16],
[SHOT TYPE, wide or close-up b-roll matching the customer's world],
[ENVIRONMENT, the customer's actual context: a podcast studio / a
marketing team's open office / a workshop bench],
[SUBJECT, what's in frame, NOT a person speaking],
[CAMERA MOVEMENT, slow drift or static],
[LIGHTING, natural, practical],
on-screen text: "[VERBATIM QUOTE, ≤14 words, large type, lower third or center]",
attribution text: "[NAME], [ROLE], [COMPANY SIZE]", smaller type,
palette: [3 ANCHORS, brand palette],
texture: [filmic, soft],
audio intent: low ambient room tone, no music or a single sustained pad,
VO reading the verbatim quote in a calm grounded voice,
EXCLUDE: motion graphics, kinetic typography, animated lower-thirds,
stock footage looks, drop shadows on type, AI-glossy skin, plastic
shine, hyper-saturated colours, gradient backgrounds, emoji,
watermark, hashtag overlays, stock-photography poses, fake smiles,
generic agency aesthetic
```

### Field-by-field discipline

- **ENVIRONMENT:** the customer's actual work context, not a stock
  office. If the review says "we run on WordPress", the environment is
  a laptop with WordPress open, not "an office".
- **SUBJECT:** never a person speaking. The point of B treatment is to
  let the QUOTE carry the spot. Subjects: tools in use, screens, hands,
  product close-ups, ambient context.
- **on-screen text:** ≤14 words. If the quote is longer, trim or split
  across two B treatment cuts. Don't shrink the font to fit.
- **VO:** the VO is added in POST in the downstream reel skill. The
  Higgsfield prompt notes the audio INTENT but doesn't generate the VO.

---

## Treatment C: Side-by-side before/after

**Visual:** Split-screen 50/50. Vertical split for 9:16. Horizontal split
for 16:9. Left = before, right = after.

### Higgsfield prompt skeleton (Skeleton 5C)

```
[DURATION] [ASPECT, usually 6-8s 9:16],
split-screen 50/50 vertical,
LEFT side: [THE "BEFORE" WORLD, visually messier, dimmer, more friction.
Be specific: "a desk piled with three different tools open on a laptop,
harsh overhead light"],
RIGHT side: [THE "AFTER" WORLD, visually cleaner, calmer, fewer
elements. "Same desk, single tool open, soft window light"],
both halves are static or have matched slow drift,
on-screen labels: "Before" and "After" in small understated type at top
corners,
palette: same across both halves to keep visual continuity (colour
tells the story, not the palette),
texture: filmic,
audio intent: voiceover delivers the verbatim quote
"[VERBATIM QUOTE]" in calm grounded voice,
EXCLUDE: dramatic lighting changes between halves, wipe transitions,
harsh comparison overlays, "vs." text in giant type, motion graphics,
kinetic typography, AI-glossy skin, plastic shine, hyper-saturated
colours, gradient backgrounds, emoji, watermark, hashtag overlays,
stock-photography poses, fake smiles, generic agency aesthetic
```

### Field-by-field discipline

- **LEFT / RIGHT:** the visual contrast does the work. Don't rely on
  the labels, they're confirmation, not content.
- **palette continuity:** use the SAME palette across both halves. The
  difference is in the COMPOSITION (cluttered vs clean), not the
  colour. If the palette also shifts (muted before, brand-saturated
  after), the viewer reads it as "filter applied", not "real change".
- **labels:** "Before" / "After" in small understated type at top
  corners. Not giant "vs." text in the middle.
- **VO:** added in POST. Higgsfield prompt notes the audio intent.

---

## Universal rules (all three treatments)

- **Verbatim quotes only.** Never paraphrase customer language for
  on-screen text or VO. Paraphrase only allowed for the hook tease,
  never for the quote itself.
- **5-8s for the Higgsfield render.** Full 30s ad is assembled
  downstream in `cinematic-ai-reels` (A) or `motion-graphic-reels`
  (B + C).
- **Brand visibility subtle.** Logo bug max, not overlay. Testimonial
  ads underperform when the brand mark dominates.
- **AU English** for all text + on-screen text + script.
- **No em dashes.** Use commas, full stops, or colons.
- **Banned vocab list** applies, see SKILL.md "Voice + Style Constraints".

---

## Sanity check before delivering each treatment

1. Read the hook out loud. Does it grab in 3s? If no → swap pull-quote
   for a better one from the supporting quotes.
2. Does the script paraphrase the customer anywhere outside the hook?
   If yes → restore verbatim.
3. **Treatment A only:** is the disclosure text in the Higgsfield prompt
   AND in the deliverable? If no → STOP and add it. Non-negotiable.
4. Does the CTA contain any outcome guarantee or support promise? If
   yes → swap to process language ("see how it runs" not "here's how
   to get X result").
5. Is the brand visibility subtle (one logo bug max)? If no → tone down.

If all 5 pass, ship to voice ship-gate (content-engine + humanizer).

## Output destination

Write to:

- `<output-folder>/treatment.md` (decision + script for each theme)
- `<output-folder>/higgsfield.md` (one filled Higgsfield prompt per theme)
