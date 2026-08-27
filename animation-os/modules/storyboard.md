# Storyboard

The storyboard is drafted **grid-first** in GPT, and Animation OS's job at this stage is to
**construct the GPT storyboard prompt** for the user to run. Draft the whole board cheaply in one
image, then split it into strategic anchors. Never hand-generate one polished still per line.

## Pipeline position

```
SCRIPT LOCK + STYLE SELECT
        ↓
Claude CONSTRUCTS the GPT storyboard prompt   ← this stage
        ↓
Human runs it in GPT (image) → returns ONE storyboard grid
        ↓
Claude REVIEWS the grid + SPLITS it into strategic anchors
        ↓
CHARACTER BIBLE + HERO → ANCHOR IMAGES → VIDEO CLIPS
```

## Step 1 — Claude builds the GPT storyboard prompt

Before writing it, do the thinking the storyboard depends on:

1. **Break the script into visual story beats.** Favor strong visual storytelling: give every distinct
   story beat its own anchor, and use **as many anchors as the script earns** (the Flow agent batches
   up to 100, so count is never a tooling limit). Cut only true near-duplicates and redundant filler;
   never merge two distinct story beats into one. More detailed, story-driven shots beat fewer generic
   ones. Each anchor should advance the story or add a fresh visual, not restate the last one.
2. **Pull the short style line** from the chosen Style Pack (`styles/<style>.md`).
3. **Set the hero note** (same character every panel) and the world.
4. **Mark the layers** where a style is hybrid (e.g. `[S]` character on camera, `[X]` x-ray insert).

Then fill this template and hand it to the user:

```text
[GPT STORYBOARD PROMPT — paste into ChatGPT image]

Create ONE storyboard sheet image: a clean labeled grid of 9:16 vertical panels.

TITLE BAR: {PRODUCT} x {STYLE} — STORYBOARD

STYLE (every panel): {ONE-PARAGRAPH STYLE LINE from the Style Pack}. The SAME character in every
panel. {hybrid note if any: some panels are the character on camera, some are inserts of X}.

CHARACTER REFERENCE: put a small hero reference of the character in the top corner labeled
"HERO — use in every panel". Keep the same character, face, and proportions in all panels.

Draw these {N} panels in order. Label each with its number and its narration line, plus a one-line
action underneath:

1. "{VO line/phrase}" — {one clear action / composition}   {layer tag}
2. "{VO line/phrase}" — {one clear action}                 {layer tag}
... (one row per strategic beat) ...

RULES:
- Same character in every panel (this is the consistency anchor).
- Competitor/store-brand items are plain and unbranded — no real brand, no logos.
- This is a rough blueprint: keep it clean and readable.
- Only the small panel labels carry text; no captions inside the scene art.
```

Keep it draft-quality on purpose — this board is a Version-1 blueprint, not the final ad.

## Step 2 — Review the returned grid

When the user sends the grid back:

- Confirm the character holds across panels; **lock the grid's hero as `@CHARACTER`**.
- Flag draft artifacts to fix at FINAL generation (not by redoing the board): product color/label
  drift, burned-in text, duplicate background characters, wrong hair state.
- Note any weak panel to merge or restage.

## Step 3 — Split into strategic anchors (generation-ready)

Turn each approved panel into a generation prompt using the Style Pack's per-shot formula
(`[MASTER STYLE LOCK] + @CHARACTER + @PRODUCT_REFERENCE + scene + one action + camera + duration`),
with the real product **label lock** (`modules/product-truth-lock.md`) on product panels.

Map each anchor to the voiceover timeline: time range · VO lines · action · camera · which clip(s) it
drives. Anchor blocks longer than the model's max clip length split into two clips from the same anchor.
