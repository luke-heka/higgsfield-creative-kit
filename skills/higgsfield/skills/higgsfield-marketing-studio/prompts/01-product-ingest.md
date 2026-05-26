# Prompt 01. Product Ingest

Step 1 of the Marketing Studio orchestration. Goal: load the product into
Marketing Studio cleanly so the no-prompt generation has a rich brief to
work from.

---

## Pre-flight check

Before pasting any URL:

1. Open the product URL in a browser tab. Eyeball the landing page.
2. Confirm the page has at least 3 of:
   - Product name + brand
   - Hero image (preferably on white or lifestyle)
   - Price
   - Long-form description (2+ paragraphs)
   - Benefits/features block (bullets)
   - Social proof (reviews, ratings)
3. If only name + price + thumbnail show, the scrape will fail or
   produce a generic ad. Find a richer URL (often the brand's main PDP
   not an Amazon listing) or use the manual product entry path.

---

## Paste + wait

In Marketing Studio:

1. Click the **Product** tab.
2. Click **Product** on the right-hand panel.
3. Paste the URL.
4. Click **Load**.
5. Wait 2-3 minutes. Marketing Studio scrapes + indexes the page in the
   background. The product card appears on the left when ready.

Do not click Generate yet. Confirm the card first.

---

## Confirm the card

The loaded product card should show:

- Correct product name
- Correct hero image
- Price
- A scraped short description (1-2 lines)
- Benefits as bullets if the page had them

**If anything is wrong:**

- Wrong name / image → wrong URL hit, try the canonical PDP URL.
- Card never loads after 5+ minutes → scrape failed. Hard refresh the
  browser. If still failing, switch to manual product entry (upload
  product image + paste benefits as a text block).

Screenshot the loaded card to `<output>/00-product-card.png` so the
artifact survives the session.

---

## Save the intake

Write `<output>/00-brief.md`:

```markdown
# Marketing Studio Intake

**Date:** <YYYY-MM-DD>
**Product URL:** <URL>
**Product name (as scraped):** <name>
**Price:** <price>
**Benefits scraped:** <bullet list, copy from Marketing Studio card>

**Campaign goal:** <awareness | conversion | retention>
**Format mix:** <list of 5 clips>
**Avatar:** <default | custom_mint | soul_id_<name>>
**Iteration tier:** <cheap_test | full_stitch>
**Output folder:** <path>

**Voice gate:** content-engine + humanizer required on caption + CTA + on-screen text.
**Slop blocklist active:** game-changer, 10x, crushing it, killing it, secret sauce, level up, unlock, transform.
**Punctuation:** no em dashes.
```

This file is the source of truth for the rest of the run. Every later
prompt reads it.

---

## Common ingest failures

| Symptom | Fix |
|---------|-----|
| Card shows generic name like "Untitled" | Landing page had no clear product name. Use manual entry. |
| Price field empty | Scraper missed it. Add manually in the card editor. |
| Hero image is a logo not the product | Page used a sticky header logo. Use a different URL or upload a product hero image manually. |
| Benefits list is empty | Page had no bullet structure. The auto-generated ad will be weaker, consider re-writing the product page first OR proceed and expect to re-shoot. |
| "Scrape blocked" error | Page has bot protection (Cloudflare, etc.). Manual entry only path. |

---

## Output

Once the card is loaded and confirmed:

- `<output>/00-product-card.png` (screenshot)
- `<output>/00-brief.md` (intake transcript)

Proceed to `prompts/02-format-selection.md`.
