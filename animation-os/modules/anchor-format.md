# Anchor Format

The locked structure for every anchor (still-image) prompt. Every anchor in an ad uses the SAME
section order and fullness, so the set stays consistent shot to shot. Do not compress some shots and
expand others. An anchor is a clean PRE-ACTION still, never animation.

**HARD RULE — never compress.** Emit the full template below verbatim for every anchor, even when
producing many in one message. Never shorten, merge, drop a section, or abbreviate "to save space" — a
stubby version is a reject. Output fewer anchors at a time instead of shortening the format. (Same guard
as `video-format.md` and non-negotiable #8.)

**Before emitting, run `modules/preflight-checklist.md`** — the pre-emit self-lint (fresh hook location,
one character ref, deep focus, correct label/serum/needle, slot-numbered with a real A/B/C/D letter).

## Attachments line (top of every anchor)
- **ONE character marker, named once, used everywhere** — always. The name is project-chosen and
  arbitrary (`@CHARACTER`, `@SKELETON`, `@KAI`, `@MASCOT` — whatever fits the job); the template below
  uses `@CHARACTER` as a generic stand-in for it. What matters is: pick exactly one and reuse it. Do NOT
  invent parallel markers for the same character (a name plus a `@HERO` plus a `@..._x`); multiple names
  for one identity is the #1 cause of character drift. Restate the itemized identity lock in the prompt
  body every time (see CHARACTER CONSISTENCY LOCK), never rely on the marker alone.
- **ONE character reference image per anchor — never stack two.** Attaching two competing character
  references for the same person (e.g. a base identity image AND an approved frame together) makes the
  generator average them and drift into an off-model, gaunt/wrong look. Once a clean frame is approved,
  make THAT single frame the character reference and drop the others. Product/world references are a
  different subject and are safe to attach alongside the one character reference.
- **World lock = attach the first approved anchor** (e.g. `@A1`) on every shot after the first, camera
  moved to a new angle, environment unchanged. One world, many camera positions.
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

These are style-agnostic concepts that made real ads land — they apply to any character, style, world,
or product. Every specific in parentheses is just an EXAMPLE from one shipped ad, never a fixed value;
swap it for whatever the current job uses. Apply the concepts on every anchor set unless the user
overrides.

- **Pose + shot variety, no repeats.** No two consecutive CHARACTER beats may share a shot size OR an
  angle OR a gesture. Rotate deliberately across the available vocabulary (close-up, hero low-angle,
  medium-wide, side profile, macro/high-angle, over-shoulder, etc.). One flat, repeated framing on
  every shot is a reject — it is what makes a set feel weak and off even when each frame is fine. Plan
  the whole set's shot map before writing prompts so variety is designed, not accidental.
- **State arc is the spine.** The one variable that changes shot to shot (whatever it is for this
  product — hair, skin, wear, health, mess, mood, progress, before/after) should PROGRESS across the ad
  into a payoff: problem state → mid-transition → resolved state. State the CURRENT STATE explicitly in
  every anchor and keep the arc monotonic (don't regress a beat). The transformation IS the story; a
  flat state across the ad wastes the format. (Not every ad is a transformation — when the angle isn't,
  the "arc" is just the consistent state; don't force one.)
- **Mechanism / insert beats stay in the character's OWN material world.** When a beat shows an internal
  or abstract mechanism, do NOT hard-switch to a foreign render. Render the insert in the SAME material
  language as the rest of the ad (whatever that style is), usually no character in frame, as a CLEAN
  base plate with open negative space for any post GFX layer the editor will add. Never bake the effect
  into the plate. This keeps one visual universe and hands post a clean canvas. (This is the general
  form of the x-ray-style pack's "transition into the insert, don't style-switch" rule.)
  - **Escape hatch — education-level science plates (client override).** When credibility matters more
    than stylistic unity (a real mechanism the ad is teaching), a dedicated SCIENTIFIC-VISUALIZATION
    look for the insert beats is correct, even if it departs from the character's material. Pick the
    fidelity the client wants: realistic medical viz, or a **stylized 3D hybrid** (a diagram's clarity
    and labels rebuilt with premium 3D depth). Either way it stays a CLEAN plate with open negative
    space for post GFX. If the client supplies a mechanism diagram, treat it as the TRUTH-LOCK for what
    the plate shows (attach it as a reference) and hold its exact steps.
  - **Teach by showing.** A science/mechanism plate must be genuinely educational — the viewer should
    LEARN the mechanism just by watching. Each plate visually advances ONE clear step of the process
    (open → deposit → feed → close; blocked-vs-through; etc.). It is a lesson, not decoration.
- **Split-anchor for fast beats.** One VO line can split into two rapid anchors (e.g. A1a / A1b) to make
  a punchy contrast open or a quick one-two. Each half is a full anchor in the locked format; the
  timeline table shows both with their portion of the shared line.
- **One strong world, camera does the work.** Lock one consistent-material environment and move the
  camera around it, rather than changing locations every shot. Cheap-looking variety comes from new
  angles in one strong world, not many weak worlds. (Multi-location ads are fine when the script needs
  them — the rule is "don't switch worlds for variety's sake," not "never change location.")
  - **Client-preferred variety.** Some clients explicitly want location AND pose variety (a
    day-in-the-life feel), not one room. That is fine: drop the single-world lock and give each beat
    its own fitting environment, but keep the CHARACTER and PRODUCT identity locked and vary poses
    deliberately (no repeated stance). To hold hair/identity continuity across changing locations,
    attach an already-approved frame as the character/hair reference on later beats instead of a world
    lock.
- **Throw-to-lens (or object-at-camera) transition.** A punchy way to cut between beats: the character
  hurls a prop straight AT the lens on the last beat of a clip, the object rushing to camera to wipe
  into the next shot (e.g. throwing dismissed competitor products into a mechanism plate). The ANCHOR
  obeys the pre-action rule — the prop is still IN HAND, arm cocked, not yet thrown — and the throw
  happens in the clip; leave open space toward the lens for the throw path.

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
- **Real product labels — two modes.** Default: get shape and colors right from `@PRODUCT`, expect small
  label text to garble, composite the real label in post (`product-truth-lock.md`). But when the
  product reference is clean and legible and the generator can hold text well, REPRODUCE the real label
  faithfully in-frame (name the exact words), and only touch it up in post if it garbles. Ask/confirm
  which the client wants; some prefer the label visible in the still and the clip.
- **Competitor items:** plain, unbranded, no logo, no text. Price tags are blank (no numbers).
- **CTAs/buttons:** a simple shape only (e.g. a plain orange cart icon), no text; real text/stickers
  are added in the edit.

If a beat seems to need on-screen text, that text belongs in the edit (captions/overlays), not the
generated frame.
