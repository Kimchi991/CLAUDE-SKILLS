# Flow Agent — Batch Generation Engine

The standard generation engine for Animation OS. A Google Flow agent (Nano Banana image models +
image-to-video) generates all anchors in one batch and animates them in the same session. Use this
every time there is a new script or product.

## Why the Flow agent
Verified capabilities (Nano Banana 2 / Pro in Google Flow, Pro/Plus tier):
- **Batch up to 100 images per turn**, all at once, labeled by shot number. Every anchor the script
  earns in one go, with variants to spare — count is never a tooling limit, so favor visual storytelling.
- **Up to 10 reference images per shot** — the `@CHARACTER` sheet + `@PRODUCT` + an anchor all fit.
- **Holds rules in memory** — paste the Master Lock + character/product rules once; it applies them to
  every later generation without re-pasting.
- **9:16 native**, single-shot regeneration, multiple variants per shot.
- **Image-to-video in the same session** (4 / 6 / 8 / 10s; Omni Flash up to 10s).
- Free of credit cost on the Pro/Plus tier — batch generously, do variants.

Two limits to design around:
- **Text/labels hallucinate.** Get the product shape and colors right; **composite the real label in
  post** (see `modules/product-truth-lock.md`).
- **It does not auto-anchor to the first result.** The **character sheet asset is the anchor** on
  every shot. Optionally, once shot 1 is perfect, tell it to also use that result as a reference for
  the rest (double lock).

## The core rule: identity lock, story-state variable
The character sheet is an **IDENTITY lock, not a pose lock.**
- **LOCK (never change, prevents drift):** face, eyes and their design, skull/bone structure,
  translucent body + glowing organs, proportions, render style.
- **VARY per shot (tells the story):** hairline / amount of hair, beard, expression. Follow each
  shot's `CURRENT STATE` line; do NOT copy the sheet's hairstyle.

Always send the agent this clarification once, so it stops treating the sheet as a frozen pose.

## Batch vs Chain (this decides drift and continuity)

**Batching all shots at once = independent rolls.** The agent does not tie shot N to shot N-1, so the
character, environment, and story-state re-roll slightly every image. Use batch ONLY for shots that
are genuinely independent (unrelated scenes, a variant set).

**For a continuous story, CHAIN instead:** generate one shot at a time, and feed each approved shot
back in as a reference for the next (on top of the character sheet + product). Each shot inherits the
real previous shot, so drift stops and the story flows — the room, lighting, and story-state (e.g. a
hair-loss arc) carry forward and change *gradually* instead of jumping.

```
character sheet → Shot 1 (approve) → use Shot 1 as reference for Shot 2 (approve)
→ use Shot 2 as reference for Shot 3 → ...
```

**World lock (do this for continuity):** pick ONE set (same room, surfaces, props, lighting), keep the
character in that space, and MOVE THE CAMERA rather than teleporting to a new environment each shot.
State the locked set at the top of the session and reference it every shot. Progress the story-state
(hair, beard) a little per shot so the transformation reads as continuous.

Chaining is slower (sequential approvals) but it is the only reliable way to get consistency AND a
continuous story. Reserve one-shot batching for independent shots or 3-variant picks.

## The reusable "meal"

**MESSAGE 1 — SETUP (paste once, attach the character sheet + product photo)**
```
Setup for this whole session. Attached: image 1 = @CHARACTER (character sheet), image 2 = @PRODUCT.
Use {Nano Banana Pro / 2}. Every output is 9:16 vertical. Hold this and apply it to every image:
STYLE: {the Style Pack's Master Style Lock, condensed}.
CHARACTER: always @CHARACTER. Identity locked: face, eyes, bone structure, translucent body + organs,
proportions, render. VARY per shot only the hair/beard/expression per the CURRENT STATE I give.
PRODUCT: when present match @PRODUCT exactly; get shape and colors right; small label text may garble,
I will composite the real label later. Competitor items are plain and unbranded.
Confirm you are holding this, then wait for my shot list.
```

**MESSAGE 2 — LOCK CLARIFICATION (the identity-lock-vs-story rule, above)**

**MESSAGE 3 — ANCHOR BATCH**
```
Generate these {N} anchors in one batch, 9:16, labeled. @CHARACTER identity locked, hair/beard/
expression per CURRENT STATE. Add @PRODUCT where noted.
1. CURRENT STATE: {hair/beard/emotion this beat}. ACTION: {one detailed action}. {scene}. {camera}.
2. ...
```

**MESSAGE 4 — VIDEO BATCH** (after anchors are approved)
```
Animate these anchors, one clip each, {4/6/8/10}s, 9:16. Motion only: {one camera move + one action}.
Generate no audio. Front-load the action, still tail. Clip N from anchor N: {motion}.
```

## Writing the anchor prompts (what "detailed" means)
Each anchor is story-driven, not "character stands holding X":
- **CURRENT STATE** line: the hair/beard/expression for this exact beat (the transformation arc).
- **ONE detailed action** that carries the beat's meaning (a visual metaphor, a reaction).
- **Scene** (real environment) + **camera** (shot + angle).
- Keep the arc visible across the batch (e.g. balding in shot 1, fully restored by the last shot).

## After the batch
- Review; regenerate any weak shot (single-shot regen) or pull the best of 3 variants.
- Optionally lock the best shot 1 as an extra reference for continuity.
- Move to the video batch, then composite labels + VO + captions + music in CapCut.
