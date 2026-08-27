# Consistency System

The single most important production system. It is why the same character and product appear in every
shot. Two levers, used together, never one alone.

## 1. Reference leads

- Generate the **hero reference image** first (stage 8) and approve it before anything else.
- Every later shot **attaches the hero image** as a reference (`@CHARACTER`) and points back to it.
- The reference image carries the visual truth. This is more reliable than any text.

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
