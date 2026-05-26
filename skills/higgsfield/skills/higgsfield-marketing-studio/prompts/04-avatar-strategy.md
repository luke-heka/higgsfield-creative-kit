# Prompt 04. Avatar Strategy

Step 4 (called inline before Step 3 if avatar is undecided). Goal: pick
the right avatar for the campaign so the ad doesn't look like every
other Marketing Studio output on the platform.

---

## The saturation problem

Higgsfield ships ~30 pre-built default avatars. Marketing Studio defaults
to the library. As more people use Marketing Studio, the same 30 faces
appear in everyone's ads. By month 6 of using defaults, your ad is
visually indistinguishable from your competitor's.

**Rule:** never use a default avatar for a campaign that ships to paid.

Exception: throwaway internal tests, A/B variant fillers, internal Slack
demos.

---

## The avatar ladder

Pick the lowest-friction option that meets the campaign's authenticity
bar.

### Tier 1, Custom mint via text prompt (recommended default)

- Click **Create** under the Avatars panel in Marketing Studio.
- Choose **Generate from text** (NOT upload).
- Describe the avatar in plain language:

```
Woman in her early 40s, light brown hair shoulder length, warm friendly
smile, natural makeup, wearing a cream knit jumper, looks like a
real-life Australian wellness brand founder, not a model, not
overly polished.
```

```
Man in his late 30s, short dark hair with stubble, athletic but not
gym-ripped, wearing a plain grey t-shirt, looks like a real Sydney
tech-startup founder, natural skin texture, no glasses.
```

- Cost: ~50 credits (one-time per avatar).
- Time: 60 seconds.
- Output: avatar appears in your avatar library, available across all
  Marketing Studio formats.

**Voice rules in avatar prompts:**

- No em dashes.
- Banned vocab: "game-changer", "10x", "crushing it", "killing it",
  "secret sauce", "level up", "unlock", "transform".
- Plain physical description + occupation/vibe analogy.
- No outcome language ("this avatar will convert 10x" → no).

### Tier 2, Soul ID (repeat campaigns, same face every week)

When the same on-camera face must persist across multiple campaigns:

- Promote the Tier 1 custom mint to a Soul ID via `higgsfield-soul`.
- Soul ID locks the face permanently, same avatar appears in Marketing
  Studio, direct Seedance, Cinema Studio, and any other Higgsfield
  surface.
- Cost: +200 credits to mint the Soul ID (one-time).
- Best for: brand spokesperson character, founder personal brand,
  recurring testimonial face.

### Tier 3, Founder Soul ID (founder's actual face)

- Founder provides 5-10 reference photos (varied angles, lighting,
  expressions).
- Use `higgsfield-soul` setup flow.
- Output: digital twin of the founder, usable across all surfaces.
- Best authenticity bar in the stack, the founder genuinely appears in
  the ad without needing to film themselves.
- Cost: ~300 credits for Soul ID training.
- **Consent requirement:** the founder must explicitly consent. See
  `higgsfield-soul` for the consent template. Never train a Soul on a
  real person's face without written permission.

### Tier 4, Default avatar (last resort, throwaway only)

- Marketing Studio → Avatars → pick from library.
- Cost: 0 (already in your account).
- Acceptable only for: cheap_test iterations that won't ship to paid.

---

## Decision tree

```
Will this avatar appear in a campaign that ships to paid traffic?
├── No (internal test, cheap iteration) → default (Tier 4)
└── Yes:
    Will the same face need to appear across multiple campaigns?
    ├── No (one-off campaign) → custom mint (Tier 1)
    └── Yes:
        Is this the founder's actual face?
        ├── No (brand spokesperson character) → Soul ID from custom mint (Tier 2)
        └── Yes → Founder Soul ID with consent (Tier 3)
```

---

## Avatar consistency rules

Once you pick an avatar, lock it for the entire stitch:

- Same avatar dropdown selection for clips 1, 2, 4 (UGC, Tutorial,
  Product Review).
- Clip 3 (Unboxing) is hands-only, no face, so avatar choice doesn't
  matter for that clip. Marketing Studio will use the same skin tone /
  vibe to keep visual continuity.
- Clip CTA (5s, direct Seedance), same avatar must be selected in the
  Seedance avatar dropdown.

Switching avatars mid-stitch produces a face swap in the middle of the
final ad. Hard fail. If you must change avatars, restart from clip 1.

---

## Save the avatar decision

Append to `<output>/00-brief.md`:

```markdown
## Avatar

**Tier:** <1 / 2 / 3 / 4>
**Method:** <custom_mint | soul_id | founder_soul_id | default>
**Avatar name in library:** <name>
**Mint prompt (if Tier 1):** <verbatim text prompt used>
**Soul ID slug (if Tier 2/3):** <slug>
**Consent recorded (if Tier 3):** <YYYY-MM-DD, signed by <name>>
**Credit cost:** <n>
```

---

## Output

- Updated `<output>/00-brief.md` with avatar block.
- Avatar visible in Marketing Studio's avatar dropdown.

Return to `prompts/03-multi-format-stitch.md` to start the render loop.
