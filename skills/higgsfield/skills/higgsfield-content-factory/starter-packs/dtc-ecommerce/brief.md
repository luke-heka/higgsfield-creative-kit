# DTC Ecommerce, Content Factory Brief

Preconfigured intake for direct-to-consumer brands ($25-$120 AOV). Edit the
variables, leave the structural defaults alone unless you know what you're
doing.

---

## Niche (preconfigured)

DTC ecommerce brands shipping a physical product (supplements, skincare,
apparel, food, accessories) with a $25-$120 AOV. Founder runs Shopify or
similar. Sells direct on Instagram + TikTok Shop. Customer is suspicious
of polished brand claims and wants real-people proof.

If your brand sits outside that window (luxury $500+, B2B, marketplace),
pause and ask for a custom niche before running the factory.

---

## Brand voice (DTC house voice, not Selr AI)

- Conversational. Like texting a friend who happens to use the product.
- Specific over clever. Names the product, the price, the ingredient.
- Quiet authority over hype. "Here's what it does" beats "you won't believe".
- Founder-led when possible. "I made this because..." builds trust faster
  than agency copy.
- Light humour OK, never sarcasm.
- US English is the default for this pack (DTC is US-skewed). Swap to AU
  English by setting `language: en-AU` in the variables block.

---

## Variables to edit

Fill these in before running the factory. Everything in `{{...}}` gets
swapped automatically across the 40 carousels.

```yaml
brand_name: "{{BRAND_NAME}}"
brand_handle: "{{IG_HANDLE}}"
product_name: "{{PRODUCT_NAME}}"
category: "{{CATEGORY}}"               # supplement / skincare / apparel / food / accessory
hero_benefit: "{{HERO_BENEFIT}}"       # one sentence, the single reason people buy
price: "{{PRICE}}"                     # e.g. "$45/month" or "$89 one-time"
aov_threshold: "{{FREE_SHIP_OVER}}"    # e.g. "$75"
founder_name: "{{FOUNDER_NAME}}"
founder_origin_story: "{{ONE_SENTENCE_FOUNDING_STORY}}"
ingredient_or_mechanism: "{{KEY_INGREDIENT_OR_HOW_IT_WORKS}}"
target_concern: "{{CUSTOMER_PAIN}}"    # e.g. "afternoon energy crash", "bumpy skin"
before_pain: "{{BEFORE_STATE}}"        # what customer dealt with before
after_result: "{{AFTER_STATE}}"        # what changed (avoid medical claims)
language: en-US                        # en-US default, en-AU if AU brand
```

---

## Batch size

Default: 5 carousels per batch, 8 batches = 40 carousels over 60 days.

If this is your first run, start with 1 batch (5 carousels), review the
output, then commit to the full 60-day calendar.

---

## Carousel templates per slot

The factory picks templates per idea card. For DTC, the rotation is
weighted toward proof and demos, not abstract education.

| Template | Frequency | When used |
|----------|-----------|-----------|
| `carousel-tips` | 30% | "5 things to look for in a {{category}}" |
| `carousel-myth-bust` | 20% | "Stop believing {{common_myth}} about {{category}}" |
| `carousel-case-study` | 20% | Customer transformation with permission + receipts |
| `carousel-cheat-sheet` | 15% | Quick reference (e.g. ingredient glossary) |
| `carousel-stack-reveal` | 15% | "Here's the morning routine that fixed {{target_concern}}" |

Reel-cover and metaphor-explainer aren't used for DTC, they don't convert
on product-led feeds.

---

## Industry defaults (don't edit unless you have data saying otherwise)

- **Hashtag pack** (rotated per post): `#tiktokshopfinds`, `#productreview`,
  `#smallbusiness`, `#unboxing`, `#{{brand_handle}}`, plus one category tag
  like `#skintok`, `#supptok`, `#mensgrooming`.
- **CTA pattern**: "Tap the link in bio for {{price}}" or
  "Comment '{{keyword}}' for the link". Never "shop now" buttons in copy.
- **No medical claims**: never use "cures", "treats", "fixes", "guaranteed
  results". Use "supports", "made for", "designed to help with".
- **No stock B-roll references** in any supporting image prompt.
- **Founder-shot aesthetic**: vanity counter, kitchen, bathroom, natural
  light, no studio. The supporting image prompts in `prompts.md` enforce
  this.

---

## Kill criteria

Stop the factory and reconfigure if:

- You're selling a regulated category (Rx, alcohol, CBD in restricted
  states), platform rules need a separate review.
- Your AOV is over $200 (different objection set, different content
  strategy, use the coach starter pack or a custom brief).
- You don't have a real customer transformation to use for at least one
  case-study slot. Don't fabricate one.

---

## How to invoke

```
/higgsfield-content-factory dtc-ecommerce
```

Then approve each batch at the gate. The factory will not auto-advance.
