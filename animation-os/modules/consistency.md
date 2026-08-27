# Consistency System

The single most important production system. It is why the same character and product appear in every
shot. Two levers, used together, never one alone.

## 1. Reference leads

- Generate the **hero asset** first (stage 8) and approve it before anything else. Prefer a full
  **character sheet** over a single hero image: a production sheet with a turnaround (front / 3-4 /
  side / back), an expressions row, and detail callouts (eyes, hands, hair) plus color swatches.
  ChatGPT is strong at character sheets; build it there.
- **Load that character sheet as an ASSET inside the generation tool** (e.g. Google Flow) and
  reference it as `@CHARACTER` in every shot. The sheet gives the model the character from every
  angle and expression, so it drifts far less than a single pose does.
- Every later shot **points back to the asset**. The reference carries the visual truth, more
  reliably than any text.

## 2. Text reinforces (DNA + current state)

Attach the reference AND restate the character in every prompt. Two parts:

- **CHARACTER DNA** — the full, unchanging appearance, pasted verbatim into every prompt. Never write
  "same character" or "same outfit"; always rewrite the whole description. Cover: build, head/face,
  eyes, hair, clothing + colors, shoes, accessories, material, render style. End with what it is NOT
  (e.g. "not realistic, not Pixar").
- **CURRENT STATE** — the one-line description of what changes at this beat (hairline density, beard,
  emotion, wardrobe change). This is the ONLY thing that varies between shots.

```
[CHARACTER DNA — verbatim, every prompt]
CURRENT STATE: [the one thing different this beat]
ACTION: [what the character is doing — an action moment, never a mannequin pose]
```

## Identity lock, story-state variable

The character sheet / hero asset is an **identity lock, not a pose lock**. Freeze the identity
(face, eyes, bone/build, materials, proportions, render) so it never drifts, but deliberately **vary
the story-state per beat** (hairline, beard, wardrobe change, expression) via the CURRENT STATE line.
The variation IS the story: a hair-loss ad must show him balding early and restored late. Tell the
generation tool this explicitly, or it copies the sheet's pose/hair every shot and the ad has no arc.

## Why it drifts (and the fixes)

- **Blocky vs realistic flip** → a competing style word ("cinematic", "Pixar") is fighting the
  reference. Delete it. Say "match the exact style of the attached reference. Do not restyle."
- **Random beard / wardrobe** → not pinned by CURRENT STATE. State it explicitly per beat.
- **Reference not attached** → text alone is not enough. Always attach the hero.

## Generation discipline

- Run **3 variants** per anchor, pick the cleanest for consistency.
- One anchor, one action. Never let one anchor silently cover two different actions.
- Tag ambiguous look-alike anchors explicitly (`@A4a` vs `@A4b`) and restate the tag in every prompt.
- Generate one shot at a time until the recipe is proven, then batch.
