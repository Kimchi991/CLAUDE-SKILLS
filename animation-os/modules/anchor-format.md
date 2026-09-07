# Anchor Format

The locked structure for every anchor (still-image) prompt. Every anchor in an ad uses the SAME
section order and fullness, so the set stays consistent shot to shot. Do not compress some shots and
expand others. An anchor is a clean PRE-ACTION still, never animation.

**HARD RULE — never compress.** Emit the full template below verbatim for every anchor, even when
producing many in one message. Never shorten, merge, drop a section, or abbreviate "to save space" — a
stubby version is a reject. Output fewer anchors at a time instead of shortening the format. (Same guard
as `video-format.md` and non-negotiable #8.)

## Attachments line (top of every anchor)
- **ONE character marker, named once, used everywhere** (e.g. `@SKELETON`) — always. Do NOT invent
  parallel markers for the same character (`@CHARACTER` + `@HERO` + `@SKELETON_x`); multiple names for
  one identity is the #1 cause of character drift. Pick one, restate the itemized identity lock in the
  prompt body every time (see CHARACTER CONSISTENCY LOCK), never rely on the marker alone.
- **World lock = attach the first approved anchor** (e.g. `@A1`) on every shot after the first, camera
  moved to a new angle, room unchanged. One world, many camera positions.
- `@PRODUCT` (real product photo) — only on product shots, with the truth-lock (`product-truth-lock.md`).

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

- **Pre-action start state, never post-action.** The anchor is the settled frame the animation begins
  from, right BEFORE the beat's motion happens. The character is in a held, settled pose (already
  holding the prop, hand already raised), never mid-motion and never showing the action already done.
  Concretely: a "throw" beat shows the object STILL IN HAND, arm cocked, about to throw, never the
  object airborne or gone; a "flick/toss it away" beat shows it held, not tumbling out of frame; a
  "wink" beat shows both eyes open. The motion itself belongs to the clip (`video-format.md`), not the
  still. See `consistency.md`.
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
- **NEVER talking. B-roll only.** Characters in ads never speak and never lip-sync — the VO carries
  (non-negotiable #5). Every anchor's EXPRESSION keeps the mouth/jaw in its natural RESTING position
  (closed, or the resting skeletal grin), NOT an open mid-speech shape. Put "not talking, no open-mouth
  speech, no lip-sync" in the negatives of every anchor. Emotion is sold through the eyes, brows, head,
  and body, never a talking mouth. This carries into the clip (`video-format.md`): B-roll, no speaking.

## Production-proven rules (locked from shipped, client-approved ads)

These are the concepts that made real ads land. Apply them on every anchor set unless the user
overrides.

- **Pose + shot variety, no repeats.** No two consecutive CHARACTER beats may share a shot size OR an
  angle OR a gesture. Rotate deliberately: close-up, hero low-angle, medium-wide, side profile,
  macro/high-angle. Flat waist-up eye-level on every shot is a reject — it is what makes a set feel
  weak and off even when each frame is fine. Plan the whole set's shot map before writing prompts so
  variety is designed, not accidental.
- **State arc is the spine.** The one variable that changes shot to shot (hair, wear, health, mess,
  progress) should PROGRESS across the ad into a payoff: problem state → mid-transition → resolved
  state. State the CURRENT STATE explicitly in every anchor and keep the arc monotonic (don't regress
  a beat). The transformation IS the story; a flat state across the ad wastes the format.
- **Science / mechanism beats are stylized macro PLATES in the character's OWN material world.** When a
  beat shows an internal mechanism, do NOT hard-switch to a different render (e.g. a blue x-ray).
  Render the insert (scalp, gut, follicle, bloodstream) in the SAME material language as the character
  (here: glossy porcelain), no character in frame, as a CLEAN base plate with open negative space for
  the post GFX layer (pulse, shield, wave, particles). Never bake the effect into the plate. This keeps
  one visual universe and hands post a clean canvas.
- **Split-anchor for fast beats.** One SRT line can split into two rapid anchors (A1a / A1b) to make a
  punchy contrast open or a quick one-two. Each half is a full anchor in the locked format; the
  timeline table shows both with their portion of the shared line.
- **Single premium world, camera does the work.** Lock one clean, well-lit, consistent-material
  environment and move the camera around it, rather than changing rooms. Cheap-looking variety comes
  from new angles in one strong world, not many weak worlds.

## Expanded section order (the proven, fuller template)

The template above is the minimum. The shipped-ad version adds these labeled sections, and this fuller
order is preferred when the user works section-by-section:

`tags(reference)` → `prompt` → **FRAME [X] ONLY + no-multiples guard** → **CHARACTER CONSISTENCY LOCK**
(itemized, one bullet per identity trait) → **STORY STATE** (the current arc state) → **STORY PURPOSE**
(what this beat sells) → **SHOT SIZE / ANGLE** → **COMPOSITION (engaging)** (off-center, depth, leave
room for the move) → **ENVIRONMENT** → **EXPRESSION** (named, big, mouth at rest) → **LIGHTING** →
**PLANNED ANIMATION MOVE** (note only) → **NEGATIVE** (character drift / world+camera / scene +
shot-specific) → **OUTPUT** (one 9:16 still, clean pre-action start frame). Plate beats drop CHARACTER/
EXPRESSION and say "no character in frame, clean plate for post GFX."

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
