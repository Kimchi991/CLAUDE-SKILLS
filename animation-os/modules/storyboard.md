# Storyboard

The storyboard is drafted **grid-first** in GPT, and Animation OS's job at this stage is to
**construct the GPT storyboard prompt** for the user to run. Draft the whole board cheaply in one
image, then split it into strategic anchors. Never hand-generate one polished still per line.

**This stage is optional — ASK the anchor method first** (SKILL stage 8). Two ways to reach the
anchors:
- **(A) Storyboard method** — build the grid here, then extract each panel one by one (Step 4). Best
  for planning the whole ad at once and for stylized looks (e.g. Roblox in ChatGPT).
- **(B) Manual one-by-one** — skip the board entirely; write each anchor prompt directly in the locked
  `anchor-format.md` and generate one at a time. Faster when the visual plan is already clear.
Only run the rest of this module when the user picks (A).

## Pipeline position

```
SCRIPT LOCK + STYLE SELECT + SRT (beat count) + CHARACTER SHEET (@CHARACTER must already exist)
        ↓
Claude CONSTRUCTS the GPT storyboard prompt, attaching @CHARACTER   ← this stage
        ↓
Human runs it in GPT (image) → returns ONE storyboard grid
        ↓
Claude REVIEWS the grid + SPLITS it into strategic anchors
        ↓
ANCHOR IMAGES → VIDEO CLIPS
```

The **character sheet is a prerequisite**, not a later step: the board is drawn FROM the attached
`@CHARACTER`, so build the hero (stage 7) before this stage (8).

## Step 1 — Claude builds the GPT storyboard prompt

**Never hardcode the panel count** (it is not 16, or any fixed number). Get the VO **SRT first**
(Stage 5 voice + timing), map each spoken line/beat to a visual state, and let that mapping decide how
many panels `N` is. If there is no SRT yet, wait for it before building the board. `N` is the count the
SRT earns, nothing more.

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
[GPT STORYBOARD PROMPT — paste into ChatGPT image, ATTACH THE CHARACTER SHEET (+ PRODUCT if any)]

Create ONE PORTRAIT storyboard sheet (tall overall). Lay out {N} numbered panels in a grid. EACH
individual panel MUST be a VERTICAL 9:16 portrait frame, clearly TALLER than it is wide (like a phone
screen), NOT landscape and NOT square. Thin gutters between panels, a small number in each panel's
top-left corner. Compose every shot for a vertical frame (headroom above, full pose top to bottom).

TITLE BAR: {PRODUCT} x {STYLE} — STORYBOARD

STYLE (every panel): {ONE-PARAGRAPH STYLE LINE from the Style Pack}. {hybrid note if any: some panels
are the character on camera, some are inserts of X}.

CHARACTER: use the ATTACHED character as the exact character in every panel — same face, eyes,
proportions, and design. Do not invent a new character.

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

**Always end the storyboard-prompt delivery with the next-step handoff line**, verbatim, so anyone
running the workflow (not just the author) knows exactly what to say next to continue into the frames:

> alright lets use that storyboard, give me the exact frames one by one lets start with anchor 1 remove the number indicating the anchor number

When the user sends that line back (after the board is generated and approved), go to Step 4 and fire
the per-anchor extraction prompts one at a time.

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

Also tell the user to set the ChatGPT image output to **portrait (2:3 or 9:16)** so the sheet has room
for tall vertical panels.

## Step 4 — Extract each panel as a standalone anchor frame (ChatGPT route)

When the storyboard is approved and the user wants the anchors made in ChatGPT (not Google Flow), the
board is not cropped — ChatGPT **recreates** each panel as a clean, full-frame 9:16 still. This is the
per-anchor generation for the ChatGPT route.

Trigger: the user says something like **"use that storyboard, give me the exact frames one by one,
start with anchor 1, remove the number."** Then fire ONE extraction prompt per anchor, in order, one at
a time (wait for approval / "next" between each). Each prompt:

- Attaches the approved storyboard sheet + `@CHARACTER` (+ `@PRODUCT` on product panels).
- Says: recreate PANEL N as ONE full-frame vertical 9:16 image; **remove the panel number, gutters,
  borders, and any text**; fill the whole frame with that one shot only.
- Restates that panel's exact content (location, camera framing/angle, pose, hair state, expression) so
  the regenerate stays on-model.
- Repeats the Style Pack locks (identity, world, product-truth, render) and the START-FRAME rule (clean,
  settled pose, no motion blur, no particles, no captions).

The output is the anchor frame for that beat, fed straight into the matching animation prompt later.
