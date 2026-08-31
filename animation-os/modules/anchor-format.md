# Anchor Format

The locked structure for every anchor (still-image) prompt. Every anchor in an ad uses the SAME
section order and fullness, so the set stays consistent shot to shot. Do not compress some shots and
expand others. An anchor is a clean PRE-ACTION still, never animation.

## Attachments line (top of every anchor)
- `@CHARACTER` (the character sheet, identity lock) — always.
- `@WORLD` (the first approved anchor, e.g. `@A1`) — on every shot after the first, to lock the room.
- `@PRODUCT` (real product photo) — only on product shots.

## The template (fill every section, in this order)

```
Attach: @CHARACTER, @WORLD (approved A1), [@PRODUCT if a product shot].

Create ONE production-ready 9:16 vertical anchor frame, [role in the ad] and a START FRAME for
animation. [stop-scroll / funny note if the opener]. Do NOT make a storyboard, collage, split-screen,
or multiple views. No captions, text, or UI.

STYLE: [the Style Pack's condensed master lock].
CHARACTER: lock to @CHARACTER exactly [key identity items]. Do not redesign face/eyes/proportions.
SCALE & FRAMING: keep the exact head-to-body ratio, height, and build of @CHARACTER, do not stretch,
  shrink, or reproportion. Frame him at a CONSISTENT size across the ad, so he occupies about the same
  share of the vertical frame as the other shots, with his eye-line around the upper third. [shot size
  and how much of the body is in frame, e.g. medium = waist up, ~60% of frame height].
WORLD: the same [environment] as @WORLD, camera moved to a new angle, room unchanged.
HAIR / STATE: [the CURRENT STATE for this beat — the one thing that varies: hair/beard/expression arc].
EXPRESSION: [a specific, big, funny expression — never neutral; name the emotion].
PROP / PRODUCT: [the one prop or the real product; unbranded competitors; hide text — see below].
POSE (pre-action, completed): [the finished pose; the action is already done, NOT mid-motion].
COMPOSITION (photographic, not centered): [off-center / rule of thirds, negative space, depth — see
  motion-grammar]. Leave room for the planned move.
LIGHTING: [environmental + any motivated source].
CAMERA: 9:16 vertical, [shot size], stable, natural angle. No Dutch tilt, no fisheye, no extreme
  close-up or wide.
ANCHOR REQUIREMENTS: clean pre-action start frame, pose settled, body grounded, no motion blur, no
  transformation effect, no particles.
PLANNED ANIMATION MOVE (later, not this frame): [the camera move for the video step].
NEGATIVE: [three layers — character drift / world+camera / scene — plus shot-specific and the
  Style Pack negatives].
```

## Non-negotiable rules baked into the format

- **Pre-action start state.** The anchor is the exact frame the animation begins from. Show the pose
  ALREADY completed (already holding, already pointing), never mid-reach. See `consistency.md`.
- **Identity lock, story-state variable.** Only HAIR/STATE and EXPRESSION change shot to shot; identity
  is frozen (`consistency.md`).
- **Scale and framing lock.** Height, build, and head-to-body ratio stay identical to `@CHARACTER`, and
  the character is framed at a consistent size and eye-line across the ad. Height drift shot to shot is
  usually a FRAMING problem (he fills a different share of the frame), not just proportions, so fix
  both: lock proportions AND state the shot size / how much of him is in frame.
- **Photographic composition, not centered** (`motion-grammar.md`): off-center, depth, negative space.
- **Expression is specific and big** — name the emotion; a neutral face is a reject (`engagement.md`).
- **PLANNED ANIMATION MOVE is a note, not an instruction.** It records the video-step camera move so
  the still leaves room for it. It does NOT animate this frame.

## Anti-hallucination: hide text and screens, reveal in animation

Models garble text, labels, phone screens, and UI. Do not force them into the still:

- **Screens/phones:** face the screen AWAY from camera (show the back), or leave it off-frame. The
  character reacts to it. Reveal the screen LATER in the video (he turns it to camera), and composite
  any actual screen content in the edit, never generate it.
- **Real product labels:** get the shape and colors right from `@PRODUCT`; expect small label text to
  garble; composite the real label in post (`product-truth-lock.md`).
- **Competitor items:** plain, unbranded, no logo, no text. Price tags are blank (no numbers).
- **CTAs/buttons:** a simple shape only (e.g. a plain orange cart icon), no text; real text/stickers
  are added in the edit.

If a beat seems to need on-screen text, that text belongs in the edit (captions/overlays), not the
generated frame.
