# Prompt 03b, Pick a Testimonial Ad Treatment per Theme

You have `themes.md` from prompt 02b. For each theme, pick ONE of the
three discrete treatments. Don't blend.

## The three treatments (lifted from shared/higgsfield-prompt-skeletons.md Skeleton 5)

### A. Talking-head reconstruction

**Use when:**
- The quote is emotional ("this saved my business", "I finally feel
  heard")
- The customer's story carries the spot (the WHO matters as much as
  the WHAT)
- The brand is founder-led or relationship-driven

**Visual:** AI-rendered "customer" delivers the quote to camera.

**MANDATORY disclosure:** "Represents a customer profile, not a specific
person." On-screen, bottom-corner, full duration of the talking-head
shot. Non-negotiable for ethics + ad-platform compliance.

### B. Text-on-b-roll with VO

**Use when:**
- The quote is technical or feature-specific ("saves me 3 hours/week",
  "no overage fees", "private RSS works on every plan")
- The quote needs visual proof (the B-roll IS the proof)
- The product has a clear visual context (a desk, a stage, a workshop,
  a podcast booth)

**Visual:** Relevant B-roll (the customer's actual world), no people in
frame. Quote appears as on-screen text. VO reads the quote.

### C. Side-by-side before/after

**Use when:**
- The quote is about SWITCHING from another product
- The quote describes a broken process → fixed process
- There's a clear visual contrast (messy desk → clean desk, three tools
  → one tool, manual → automated)

**Visual:** Split-screen 50/50 (vertical for 9:16, horizontal for 16:9).
Left = before, right = after.

## Picking the treatment

For each theme in `themes.md`, apply this decision rule:

| Theme character | Treatment |
|---|---|
| Emotional, identity-based, "I needed someone in my corner" | **A** |
| Technical, measurable, "saves 3 hours/week" | **B** |
| Switching, comparison, "I came from X" | **C** |
| Multiple characters apply | Pick the dominant character. If genuinely tied, default to **B** (lowest risk, no disclosure burden) |

## Output schema

For each theme, write the treatment block:

```
# Treatment, <brand>

## Theme 1, "<theme name>"

**Treatment chosen:** A | B | C
**Reason:** 1 sentence, why this treatment fits this theme's character

**Pull-quote (verbatim, will be the spot's anchor):**

> "<quote>"
>
>, <attribution>

### 30-second ad script

**Hook (0-3s):**
<Open with the pull-quote OR a paraphrase of the hook line. If the
quote IS the hook, use it verbatim.>

**Setup (3-10s):**
<Sketch the customer's "before" world in 1-2 sentences. What was hard,
what was slow, what was missing.>

**Demonstration (10-22s):**
<Show or imply the product solving the customer truth. Concrete, not
abstract. If treatment A, the customer is speaking; if B, B-roll
shows the product in context; if C, the after side shows the resolution.>

**Payoff + CTA (22-30s):**
<The resolution line, usually a paraphrase of the customer's
"problems_solving" field. Soft CTA, "see how [brand] does it" or
"hear more customer stories at [URL]". No outcome guarantees, no
support promises.>

### Higgsfield video prompt (paste-ready, 5-8s segment)

See `higgsfield.md`, uses `../shared/higgsfield-prompt-skeletons.md`
Skeleton 5, treatment <A | B | C>.

### Disclosure (Treatment A only)

ON-SCREEN: "Represents a customer profile, not a specific person."
Position: bottom-right corner, full duration of talking-head shot.
Font: brand sans-serif, 70% opacity, ~14pt at 1080p9:16.

---

## Theme 2, "<theme name>"

(same shape)

---

## Theme 3, "<theme name>"

(same shape)
```

## Higgsfield prompt construction rules

For each chosen treatment, build the Higgsfield prompt by:

1. Loading the matching skeleton from
   `../shared/higgsfield-prompt-skeletons.md` Skeleton 5 (treatment A,
   B, or C)
2. Filling EVERY bracketed field, if a field is empty, ASK the user,
   don't guess
3. Appending the universal anti-slop EXCLUDE block from
   `../shared/higgsfield-prompt-skeletons.md` "Anti-Slop Inclusions"
4. For treatment A: explicitly add disclosure text to the
   brand-visibility field

## Universal rules (all three treatments)

- **Verbatim quotes only.** Never paraphrase customer language for the
  on-screen text or VO. Paraphrase is allowed ONLY for the hook tease,
  never for the quote itself.
- **5-8s for the Higgsfield render.** The full 30s ad is assembled
  downstream in `cinematic-ai-reels` (treatment A) or
  `motion-graphic-reels` (treatments B + C). Higgsfield generates the
  visual hero shot.
- **Brand visibility subtle.** Logo bug max, not overlay. Testimonial
  ads underperform when the brand mark dominates, let the quote do
  the work.
- **AU English** for all script text + on-screen text.
- **No em dashes.** Use commas, full stops, or colons.
- **Banned vocab list** still applies (game-changer, 10x, transform,
  level up, unlock, etc.).

## Output destination

Write to:

- `<output-folder>/treatment.md` (script + decision rationale)
- `<output-folder>/higgsfield.md` (one Higgsfield prompt per theme, separate sections)

Where `<output-folder>` is `~/board/_active/viral-replicator-<YYYY-MM-DD>/<brand>-reviews/`.

Then run prompt `03a-handoff-to-reel-skill.md` for the hand-off note.

## Sanity check before delivering

For each treatment block:

1. Read the hook out loud. Does it grab in 3s? If no → swap pull-quote.
2. Does the script paraphrase the customer anywhere outside the hook? If
   yes → restore verbatim.
3. Treatment A: is the disclosure text in the deliverable? If no → STOP
   and add it. Non-negotiable.
4. Does the CTA contain any outcome guarantee or support promise? If
   yes → swap to process language.
5. Is the brand visibility subtle (one logo bug max)? If no → tone down.

If all 5 pass, ship to step 5 (voice ship-gate via content-engine +
humanizer).
