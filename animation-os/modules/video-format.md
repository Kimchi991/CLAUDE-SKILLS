# Video Format (the locked animation-prompt template)

The canonical structure for every animation (image-to-video) prompt. Like `anchor-format.md` locks the
still, this locks the clip. **Emit it in FULL, verbatim, every time** — one prompt or sixteen. Never
compress, merge sentences, drop a section, or "save space." Format drift is the #1 recurring failure;
this file is the guard.

## HARD RULE — never compress

- **Always output the full template below**, with all sections and the blank lines between them, even
  when producing many prompts in one message. A stubby, merged, or bulleted version is a REJECT.
- Keep the section headers with the `=====` rules exactly as written.
- If space feels tight, output fewer prompts, never a shortened format. Ask the user to continue rather
  than abbreviating.

## The template (fill the brackets, keep everything else)

```
tags(reference)

@[ANCHOR]

prompt

Create a [4/6/8/10]-second vertical 9:16 image-to-video B-roll shot from the attached [ANCHOR] anchor.

The attached [ANCHOR] image is the EXACT starting state.

Preserve [the style-pack identity lock in full: character identity, face/eyes, materials, hair STATE for
this beat, wardrobe, the exact prop/product, the environment/world, lighting, depth of field, and grade].

The animation should feel alive, physical, [comedic/emotional as fits the beat], and naturally captured
inside a premium stylized [style] render, NOT an in-game screenshot.

The character should feel like an actual personality rather than a static 3D model.

==================================================
PRIMARY PERFORMANCE
==================================================

[One line naming the beat's intent.]

Begin already in the anchor pose, [the settled starting pose].

For the first moment, give the shot a tiny amount of natural idle life: [a subtle weight shift / small
head + shoulder move].

[Then... the main action, written as ordered phases, one clear motivated beat at a time.]

[Finally... he settles into the closing pose.]

Sell all emotion through [the eyes / the printed MOUTH and BIG body language — per the style pack]. Keep
the identity locked ([e.g. eyes stay small solid-black dots; never widened]). Every movement has a clear
motivation, not frantic, not slapstick.

This is a B-roll performance only: expressive face and body, but no speaking and no lip-sync.

==================================================
CAMERA PERFORMANCE
==================================================

Use a subtle cinematic camera move built from small phases rather than one constant movement.

First, [starting framing + the initial subtle move].

Then, [the main move — push-in / lateral track / macro drift / rack focus, chosen for the emotion].

Finally, [the settle], ending on a [closer/stable] framing.

No dialogue, no lip-sync, no music, no captions, no on-screen text. B-roll only.
```

## Engine rules baked into the format

- **Omni Flash 1.1 clips are 4 / 6 / 8 / 10s only.** Pick the nearest step **≥ the beat's VO length**
  from the SRT, generate long, trim the tail to the VO window in the edit. Never round down.
- **Omni Flash ignores per-second timestamps** — write the camera arc as ordered phases ("first...
  then... finally"), never `0.0-1.0s` marks.
- **Duration comes from the SRT beat length**, not from a default. A short VO line gets a short clip;
  that is correct, not an error. Only lengthen a clip if the user asks.
- **No audio in the clip.** VO, music, SFX, and captions are the user's CapCut edit.
- **One camera move + one performance per clip.** The move is a per-beat creative choice
  (`motion-grammar.md`), never the same move on every shot.

## Where the pieces come from

- Identity/world/product locks: the chosen Style Pack (`styles/*`) + `consistency.md` +
  `product-truth-lock.md`.
- Camera vocabulary and expressive-performance rules: `motion-grammar.md`.
- Which anchor covers which VO line and the clip's duration: the SRT timeline (`storyboard.md` Step 3,
  stage 5 voice + timing).
