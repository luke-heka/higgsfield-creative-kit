# Template: Higgsfield Rebuild Prompt (Skeleton 4 Reference)

> Canonical structure for the Higgsfield prompt output of
> `prompts/02a-rebuild-viral.md`. References
> `../shared/higgsfield-prompt-skeletons.md` Skeleton 4. Fill every
> bracketed field, if a field is empty, ask the user, don't guess.

---

## The skeleton (paste-ready format)

```
[DURATION + ASPECT], [HOOK MECHANIC FROM ORIGINAL, name it],
[SUBJECT + ONE ACTION across the duration],
[SETTING, named, specific, DIFFERENT from original],
[TIME OF DAY + LIGHTING with direction],
[CAMERA MOVEMENT, name it; "static" is allowed; SAME PATTERN as original],
[LENS / DEPTH],
[COLOR PALETTE, 3 anchors max, matched to user's brand],
[TEXTURE / FILM EMULATION],
[AUDIO INTENT, only if Higgsfield supports audio on this run],
[BRAND VISIBILITY, explicit: when, where, how prominently],
[EXCLUDE, every visual cliche the original DIDN'T use, plus anything the brand bans, plus the universal anti-slop block]
```

## Universal anti-slop EXCLUDE (always append)

```
AI-glossy skin, plastic shine, hyper-saturated colours, gradient
backgrounds, drop shadows, emoji, watermark, overlay text unless
explicitly requested, hashtag overlays, stock-photography poses, fake
smiles, on-the-nose product hero shots, generic agency aesthetic
```

## Discipline

- **One action.** Not "walks to the truck and opens the door." Pick one.
- **Keep the original's mechanic, change the surface.** If the original
  opened on a hard zoom-in to a face, your rebuild does the same camera
  move on a DIFFERENT SUBJECT, not a copy of the face.
- **No cuts language.** Higgsfield renders one continuous shot. No
  "then it cuts to…", no "transition to…".
- **No music sting language.** "Sudden orchestral hit" doesn't render
  reliably. Describe the audio MOOD, not the cue.
- **Brand visibility is explicit, not vibes.** "The notebook enters
  frame at 0:04 in lower-right third, label readable for ~1.5s before
  the shot ends."

## Worked example: Selr AI workshop rebuild of a "named character enters at golden hour" hook

**Original mechanic kept:** named character enters frame, looks at
camera, delivers one-sentence promise, walks away.

**Surface changed:** original was a man in canvas jacket at a remote
trailhead with a tumbler, rebuild is Luke at a workshop room with a
notebook.

**Selr AI palette applied:** cream walls, dark wood, single purple
accent.

```
6 seconds 9:16 vertical, named-character-enters-and-delivers
mechanic (same as reference), Luke walks into a quiet workshop room at
end of day, sets a notebook down on the table, looks directly at the
camera and says one sentence about the workshop, then walks toward the
door,
location: workshop room with bare walls and one wooden table,
daylight ambient with soft late-afternoon window light from screen-left,
slow handheld push-in covering ~6 inches over the duration,
50mm equivalent shallow depth of field background gently out of focus,
palette: cream walls, dark wood table, single purple notebook accent,
fine 16mm film grain with mild halation,
audio intent: ambient room tone and Luke's voice direct unhurried no music,
brand visibility: notebook stays in frame from 0:02 onward, Selr AI
purple cover readable in the final 1.5s,
EXCLUDE: drone shots, aerial angles, stock office sets, gradient
overlays, on-screen text, AI-glossy skin, plastic shine,
hyper-saturated colours, drop shadows, emoji, watermark, overlay text
unless explicitly requested, hashtag overlays, stock-photography poses,
fake smiles, on-the-nose product hero shots, generic agency aesthetic.
```

## Field-by-field guidance

### DURATION + ASPECT

- IG Reel / TikTok / YT Short: 9:16 vertical, 5-8s
- Square ad: 1:1, 5-8s
- Landscape ad: 16:9, 5-8s
- Higgsfield's sweet spot is 5-8s, anything longer degrades

### HOOK MECHANIC

Pull verbatim from deconstruction §1 archetype name (e.g.
"named-character-enters-and-delivers"). Naming it inside the prompt
gives the model the structural anchor.

### SUBJECT + ONE ACTION

ONE action only. "Picks up the bottle AND opens the cap AND tips
capsules" is three actions, split into multiple chunks if needed,
render only the dominant chunk here.

### SETTING

Be specific. "A workshop" is too vague. "A workshop room with bare
walls and one wooden table" gives the model a frame. Match the
emotional tone of the original setting WITHOUT copying it (original was
a remote trailhead = solitude + nature; rebuild is end-of-day workshop
= solitude + work).

### TIME OF DAY + LIGHTING

Direction matters. "Soft light from screen-left" gives the model a
spatial anchor. "Soft natural lighting" is too vague.

### CAMERA MOVEMENT

Match the original's pattern. If original was "slow handheld push-in",
keep that. If original was "static lock-off", keep that. Don't sub in
a drone shot because it sounds cinematic, the mechanic dies.

### LENS / DEPTH

50mm = standard portrait, mild compression, shallow DOF.
35mm = wider, slight distortion, deeper DOF.
85mm = tight portrait, heavy compression, very shallow DOF.

### COLOR PALETTE

3 anchors max. For Selr AI: cream, dark wood/charcoal, purple accent.
For other brands: pull from brand guidelines.

### TEXTURE / FILM EMULATION

"Fine 16mm film grain with mild halation", gives the model a texture
hook without forcing a specific look. Alternatives: "clean digital",
"35mm scan with gate weave", "vintage VHS scan".

### AUDIO INTENT

Skip if Higgsfield run doesn't support audio. Otherwise describe MOOD
not cues, "ambient room tone and the subject's voice direct unhurried"
not "music kicks in at 0:03".

### BRAND VISIBILITY

EXPLICIT placement + timing. "Notebook in frame from 0:02, brand cover
readable in final 1.5s", not "show the brand".

### EXCLUDE

Two layers:

1. What the ORIGINAL didn't use (if original had no zoom, exclude zoom;
   if original had no music sting, exclude music sting)
2. What the brand bans (logo bug for Selr AI is subtle, not overlay;
   testimonial ads exclude perfect studio lighting)
3. The universal anti-slop block (always append)

## Output destination

Write the filled prompt to `<output-folder>/higgsfield.md`.

Then run prompt `03a-handoff-to-reel-skill.md` for the hand-off note.
