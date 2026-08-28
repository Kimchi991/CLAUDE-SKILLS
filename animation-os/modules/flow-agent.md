# Flow Agent — Anchor Image Engine

An image-generation engine for Animation OS: a Google Flow agent (Nano Banana models) generates the
anchor images. It is ONE option for stage 9, not the only one, and it is used for **images, not
video** — video clips are generated separately (see below and `modules/motion-grammar.md`).

## Why the Flow agent
Verified capabilities (Nano Banana 2 / Pro in Google Flow, Pro/Plus tier):
- **Batch up to 100 images per turn**, all at once, labeled by shot number. Every anchor the script
  earns in one go, with variants to spare — count is never a tooling limit, so favor visual storytelling.
- **Up to 10 reference images per shot** — the `@CHARACTER` sheet + `@PRODUCT` + an anchor all fit.
- **Holds rules in memory** — paste the Master Lock + character/product rules once; it applies them to
  every later generation without re-pasting.
- **9:16 native**, single-shot regeneration, multiple variants per shot.
- Free of credit cost on the Pro/Plus tier — generate generously, do variants.

It *can* also do image-to-video, but in Animation OS **video is a separate step** (the user animates
the approved anchors in the Flow UI, Kling, Seedance, or any image-to-video tool). Keep the agent for
the anchor images.

Two limits to design around:
- **Text/labels hallucinate.** Get the product shape and colors right; **composite the real label in
  post** (see `modules/product-truth-lock.md`).
- **It does not auto-anchor to the first result.** The **character sheet asset is the anchor** on
  every shot. Optionally, once shot 1 is perfect, tell it to also use that result as a reference for
  the rest (double lock).

## The core rule: identity lock, story-state variable
See `modules/consistency.md` — the sheet is an IDENTITY lock, not a pose lock: freeze identity, vary
hair/beard/expression per the CURRENT STATE line. Flow-specific: send the agent this clarification
ONCE at session start, or it treats the sheet as a frozen pose and copies its hair every shot.

## Faithful frame reproduction (storyboard → frames)

The reliable way to turn an approved storyboard into clean standalone frames that match it exactly.
It uses Flow's input types: **`:base`** makes the model treat an image's layout/composition/edges as
the structural foundation (stays very close to it); **`:reference`** feeds identity/style. Do NOT feed
the whole 20-panel sheet and ask for all frames — the model searches the sheet and reinvents each shot
(that is the drift). Instead:

1. **Crop each panel** from the storyboard into its own standalone image and upload it.
2. **Panel 1:** generate with `panel1.png:base` + `@CHARACTER:reference`. Prompt: *"Render this exact
   frame in {style}. Keep identity locked to the @CHARACTER reference; match the pose, composition,
   framing, hair state, and action of the base image exactly. 9:16."* One at a time.
3. **Approve Panel 1** — it becomes the **environment lock**.
4. **Panels 2 to N:** `panelN.png:base` + `@CHARACTER:reference` + `panel1_result:reference` (locks the
   room, lighting, materials). Add `@PRODUCT:reference` on product panels. Same prompt structure.

Rules the agent confirmed: `:base` drives composition/pose, `:reference` drives identity; state
explicitly *"keep identity locked to the @CHARACTER reference, match the pose and layout of the base"*
so identity wins; generate one at a time; reuse the first approved shot as a style reference to lock
the world. This is the highest-fidelity path — use it when the storyboard is the source of truth.

## Two modes: FAST and DETAILED (pick per job)

**FAST mode — batch.** Generate all anchors in one turn (up to 100). Quick, cheap, great for a first
pass, a rough sample to show a brand, or independent shots and variant sets. Trade-off: the agent does
not tie shot N to shot N-1, so the character, environment, and story-state re-roll slightly every
image (some drift, no true continuity). Fine when the shots do not need to feel like one flowing scene.

**DETAILED mode — chain.** Generate one shot at a time, and feed each approved shot back in as a
reference for the next (on top of the character sheet + product), under a world lock. Each shot
inherits the real previous shot, so drift stops and the story flows — the room, lighting, and
story-state (e.g. a hair-loss arc) carry forward and change *gradually*. Slower (sequential approvals)
but the only way to get consistency AND a continuous story. Use it for the real, deliverable ad.

Rule of thumb: **FAST to explore and pitch, DETAILED to deliver.**

```
character sheet → Shot 1 (approve) → use Shot 1 as reference for Shot 2 (approve)
→ use Shot 2 as reference for Shot 3 → ...
```

**World lock (do this for continuity):** pick ONE set (same room, surfaces, props, lighting), keep the
character in that space, and MOVE THE CAMERA rather than teleporting to a new environment each shot.
State the locked set at the top of the session and reference it every shot. Progress the story-state
(hair, beard) a little per shot so the transformation reads as continuous.

## The reusable "meal" (anchor images)

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

**MESSAGE 3a — FAST mode (batch)**
```
Generate these {N} anchors in one batch, 9:16, labeled. @CHARACTER identity locked, hair/beard/
expression per CURRENT STATE. Add @PRODUCT where noted.
1. CURRENT STATE: {hair/beard/emotion this beat}. ACTION: {one detailed action}. {scene}. {camera}.
2. ...
```

**MESSAGE 3b — DETAILED mode (chain, one at a time)**
```
We are building ONE continuous scene, so do NOT batch. Locked set: {the world lock}. Keep the
character in that set and MOVE THE CAMERA between shots. Generate one shot at a time; after I approve
each, use THAT approved image as an added reference for the next, with @CHARACTER and @PRODUCT.
Progress the hair a little each shot. Confirm, then I send shot 1.
Shot 1: CURRENT STATE: {...}. ACTION: {...}. CAMERA: {...}. 9:16.
```

Video is a **separate step**, not part of this meal. Animate the approved anchors in an image-to-video
tool, using `modules/motion-grammar.md` (one motivated camera move + one action per clip, no audio;
chain the last frame forward when continuity matters).

**Video engine (this project): Omni Flash 1.1** (Gemini image-to-video). Feed it one approved anchor
as the start frame. Constraints that shape every video prompt:
- **Durations 4 / 6 / 8 / 10s only** — pick the nearest step ≥ the VO line, generate long, trim to VO.
- **No timestamp control** — it reads overall motion intent, not a per-second timeline; write the
  camera arc as ordered phases, not `0.0–1.0s` marks.
- **No audio.** Other image-to-video tools (Flow UI, Kling, Seedance) remain valid alternatives.

## Writing the anchor prompts (what "detailed" means)
Each anchor is story-driven, not "character stands holding X":
- **CURRENT STATE** line: the hair/beard/expression for this exact beat (the transformation arc).
- **ONE detailed action** that carries the beat's meaning (a visual metaphor, a reaction).
- **Scene** (real environment) + **camera** (shot + angle).
- Keep the arc visible across the batch (e.g. balding in shot 1, fully restored by the last shot).

## After the batch
- Review; regenerate any weak shot (single-shot regen) or pull the best of 3 variants.
- Optionally lock the best shot 1 as an extra reference for continuity.
- Then animate the approved anchors in a separate image-to-video step, and composite labels + VO +
  captions + music in CapCut.
