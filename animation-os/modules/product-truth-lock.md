# Product Truth-Lock

Real, labeled products are truth-locked. Product consistency is a hard production requirement, and
label drift is the #1 failure to avoid.

## Rules

- If the product is a **real brand** and a reference image is available: use the real reference. Do
  NOT generate the packaging from prose.
- Never invent packaging, logos, label text, brand marks, or proportions.
- Do not redesign shape, colors, cap/dropper, or label layout. Do not duplicate the product.
- The product must look identical in every shot it appears in. Reject any frame that changes it.
- For a "cheaper alternative" comparison, use a **generic unbranded** product — never a fake
  near-match of a real competitor.
- If a product becomes a recurring asset across ads, save a **locked reusable product reference**.

## Locking the label TEXT

Image models cannot reliably render dense small text. Three levers, used together:

1. **Attach the real photo** as a reference (`@PRODUCT_REFERENCE`). This does most of the work.
2. **State the label verbatim** in the prompt — every word, in order, with exact casing:

```
Reproduce the label EXACTLY as in the attached reference. Do not change, add, remove, translate,
or misspell any word. The label reads, word for word: "<line 1>"; "<line 2>"; … Keep the exact
fonts, sizes, colors, and line breaks.
```

3. **Frame the product large and front-on** with flat light so the text has enough pixels. Small or
   angled = garbled.

## The reliable fix

Even with all three, the model will occasionally garble dense text. For a real brand's hero shots,
**generate the bottle clean and composite the real label in post** (CapCut / Photoshop). This is what
pro brand ads do, and it is faster than re-rolling ten times fighting the model for text.

## QC checklist (before delivery)

- [ ] Product exact visual identity preserved wherever visible
- [ ] Label text correct and unchanged, or composited from the real label
- [ ] No duplicated or warped product, no invented branding
- [ ] Generic competitor stays blank (no fake brand)
