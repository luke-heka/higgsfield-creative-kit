# Influencer Outreach DM: Structural Template (AU-Adapted)

This is the SHAPE of a good DM, not a fill-in-the-blank. Every actual
DM should sound human and reference something specific from the
creator's recent work.

AU-adapted: no US influencer norms ("let's hop on a call",
"excited to connect"). Direct, dry, AU voice. Treats the creator as
a peer, not a transaction.

## The 5-Beat Shape (Max ~70 Words)

1. **Earned opener**, one specific thing from their recent content.
   Cite a post, a series, a phrase they used. NOT "love your stuff".
2. **Why we're a fit (one line)**, connect their audience or POV to
   one specific thing about the brand. No CV-dump.
3. **The ask, concrete**, what we want them to make. Format + length
   + posting window.
4. **What's in it for them**, comp framework, product, exclusivity, or
   distribution. Specific numbers or specific items, NOT "compensation
   TBD".
5. **The easy out**, one line that gives them a clean way to say no.
   Reduces friction, increases reply rate.

## What NOT to Do

- **Don't open with "Hey [first name]!"**, screams template.
- **Don't list 5 deliverables.** ONE ask.
- **Don't promise "exposure"**, they have more than you.
- **Don't include a tracking link in the first DM.**, looks like spam.
- **Don't use "we'd love to partner"**, means nothing.
- **Don't say "let's hop on a quick call"**, they haven't said yes.
- **Don't use "synergy", "passion", "vibes", "collab"**, agency-speak.
- **Don't use hashtags.**, DMs aren't posts.
- **Don't use emojis** unless the creator's voice clearly uses them.
- **Don't sign off "Selr AI Team"**, sign with the human's name.

## AU-Specific Voice Rules

- Direct, dry, no hype.
- "Worth a chat?" not "Excited to connect!"
- "Happy to send the brief" not "We'd love to hop on a call"
- "Cheers" or "Thanks" at sign-off. Never "Best!" with exclamation.
- "G'day" only if the creator's content uses AU vernacular, otherwise
  it reads as forced.
- Australian English where it matters (colour, optimise, organisation,
  realised, metre).
- No US-influencer "amazing / incredible / game-changing" stack.

## Example DM (Selr AI, Micro-Tier AU Operator-Creator)

> "Saw your March LinkedIn series on the bookkeeper-resignation pattern
> in AU SMBs, the second post in particular (the one about handing the
> install to your ops manager instead of replacing the hire) is the
> closest read I've seen to how the operators in our workshop room
> actually think.
>
> We run a hands-on workshop in Melbourne on June 12, 12 operators in
> the room install one working AI workflow by 5pm. Would you write a
> short LinkedIn text post on what you'd install if you came along?
> 800-1500 chars, posted between June 5-11. $XXX flat plus a free seat
> if you want to attend.
>
> If it's not a fit, no worries, figured I'd ask directly.
>
> Cheers, Luke"

## Example DM (Selr AI, Nano-Tier Skool Member / Workshop Alumni)

> "Saw your retro post on the Brisbane workshop day, the bit where
> you said it was the first AI training that didn't make you feel like
> a beginner. That's the exact line we're working into the Melbourne
> push.
>
> Quick ask: 30-day check-in Reel on the install still running, tag
> @selr__ai, posted any time in the next two weeks. No comp, you've
> already got the install. Just an ask.
>
> Skip it if you've moved past the topic, no problem.
>
> Cheers, Luke"

## Example DM (Selr AI, Micro-Tier AU Founder-Creator with US Audience)

> "The thread you ran two weeks ago on AI consultants charging for
> outputs not hours, the third tweet (the one about the AU agency that
> dropped to a fixed-scope $X price and 3x'd close rate) lit up our team
> Slack.
>
> We run a workshop in Melbourne on June 12 for AU SMB operators
> installing AI themselves, 12 in the room. Would you write an 8-12
> tweet thread from your perspective as a peer who's watched the
> consultant-to-installer shift? $XXX flat, full creative control.
>
> If the timing doesn't suit, no worries.
>
> Cheers, Luke"

## DM Length Reference

| Tier | Target word count | Why |
|------|-------------------|-----|
| Macro | 60-80 words | Macros get hundreds of DMs; brevity respects their time |
| Micro | 60-100 words | Slightly longer is OK to establish credibility |
| Nano | 50-70 words | Often alumni / community members, be quick, they know the brand |

## Voice Gate (Before Sending)

Run every DM through:

1. `content-engine`, strip slop, support promises, drop-in invites,
   outcome guarantees, em dashes, AU/US English mismatch.
2. `humanizer`, strip signs-of-AI-writing patterns.

If the DM has any of:

- "Hi [name]!" → re-write opener with specific recent-work reference
- "Love your content" → re-write with specific recent-work reference
- "We'd love to partner" → cut the line
- "Let's hop on a quick call" → cut the line
- "Compensation TBD" → name the comp specifically
- Em dash → replace with comma or full stop
- "transform" / "10x" / "game-changer" → cut and rewrite
- Personal-life reference (yours) → cut
- "Come say hi at the workshop" → cut (Selr no-drop-in rule)
- Refund / guarantee language → cut

## Per-DM Format (How to Save in Stage 6 Output)

```markdown
### DM: @handle (Tier: micro, Platform: IG)

[The actual DM text, ready to send. 60-100 words. Voice-graded. No
template fill.]
```

## Auto-Send Rule

**This skill never auto-sends DMs.** All DMs get written to:

1. Stage 6 output file (`06-influencer-army.md`)
2. Notion campaign page (via `Notion:create-page`)

The user sends DMs from their own account, on their own time, from their
own device, so they don't trigger platform spam filters and so Luke's
voice is genuinely his.

Sister rule to the canonical "show Luke before any blast" hard rule.

## See Also

- Hewitt's original `outreach-dm.md` (in
  `/tmp/hewitt-higgsfield-skills/skills/cmo-agent/templates/`), this
  template is the AU-adapted Selr-anchored variant.
