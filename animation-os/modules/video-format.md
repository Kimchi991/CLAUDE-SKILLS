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

## PERFORMANCE ENERGY — two lanes (never ship plain motion)

The engagement lives in the PERFORMANCE, not the camera. These ads use rigid, mostly locked cameras
(reference-accurate), so if the character also moves gently the shot reads DEAD. The #2 recurring
failure (after format drift) is writing "subtle / faint / minimal / not frantic" on a CHARACTER beat and
flattening the vibe. Every clip is one of two lanes — decide the lane first, then write the performance
for it:

- **CHARACTER lane (any character/hero is on screen acting):** big, snappy, EXAGGERATED cartoon energy.
  Never "subtle." Build the beat as **anticipation → snap → small overshoot → a punchy hold** (classic
  cartoon timing). The EYES do the acting: widen, dart, roll, double-take, deadpan down the lens. Add a
  sharp head/body accent (cock back, recoil, lean in). Cocky, comedic, meme-native attitude. Snappy and
  exaggerated but controlled, not slapstick chaos. This is where retention comes from — a plain
  character beat is a REJECT.
- **PLATE lane (x-ray science shot, product hero, or any beat whose motion is a CapCut GFX layer):**
  keep the base motion clean and minimal ON PURPOSE, because the glow/particles/tags/inset are added in
  post. Here "subtle" is correct. Leave clean space for the post effect; do not bake effects in.

Camera stays reference-accurate in BOTH lanes: mostly locked, with at most a quick punch-in on the
accent for a character beat. The energy is the character, not a busy camera. (See `engagement.md` and
`motion-grammar.md`.)

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

[One line naming the beat's intent + the LANE (character = big/snappy; plate = clean base for post GFX).]

Begin already in the anchor pose, [the settled starting pose].

For the first beat, ANTICIPATION: [CHARACTER lane = a quick sharp anticipation, eyes snap wide / head
cocks; PLATE lane = a faint settle only].

[Then, the main action: CHARACTER lane = one big EXAGGERATED cartoon move with snappy timing
(anticipation → snap → small overshoot), the eyes doing the acting; PLATE lane = minimal base motion
only, the effect is added in post. One clear motivated beat.]

[Finally, the HOLD: CHARACTER lane = land on a punchy deadpan / attitude hold; PLATE lane = settle
still, leaving clean space for the post effect.]

Sell all emotion through [the eyes / the printed MOUTH and BIG body language — per the style pack]. Keep
the identity locked ([e.g. eyes stay small solid-black dots; or x-ray eyes stay large + expressive,
never empty sockets]). On a CHARACTER beat the motion is big, snappy, and exaggerated (never subtle);
every movement still has a clear motivation, controlled, not slapstick chaos.

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

## CLIP LENGTH — compute per beat, NEVER default to 4s

The `[4/6/8/10]-second` in the template is a PLACEHOLDER to compute, never a value to type as-is.
Writing "4-second" on every clip is a recurring failure (right after format drift and plain motion).
Before writing a single animation prompt, do this for EACH anchor, from the SRT:

1. Take the beat's real VO span = (end timestamp of its last SRT line) − (start timestamp of its
   first SRT line). Split-anchor beats (e.g. A1a / A1b sharing one SRT line) use the portion of the
   line each covers.
2. Pick the **nearest allowed step ≥ that span from the current engine's set.** For Omni Flash that set
   is 4 / 6 / 8 / 10s (4.9s → 6s, 6.7s → 8s, 8.2s → 10s); a different engine uses its own steps, so read
   the chosen engine's set and snap to it. Never round down. The engine's minimum step is only correct
   when the span is genuinely ≤ it (it is the floor, not the default).
3. If the span is longer than the engine's max step, the anchor drives **two clips** from the same
   anchor (`storyboard.md` Step 3), not one over-long clip.
4. Write that exact number into the clip's opening line. A set of prompts that are all the minimum
   length is a REJECT — a correct set has a MIX of lengths unless every beat truly runs under the floor.

Show the SRT timeline table (anchor · VO window · span · generate · trim) BEFORE the prompts, so the
lengths are auditable and the user can catch a wrong one.

## ASSEMBLY TIMELINE — LOCKED OUTPUT FORMAT (client-locked, do not change)

When the user asks for "the timeline," output the final assembly in EXACTLY this format every time —
same columns, same order, no substitutions. This is the editing deliverable (clip → VO map + where each
cut lands); captions, VO sync, SFX, and fine trim are the user's CapCut craft.

Header line (one line, above the table):
`S<n> assembly timeline (<render style> · <product> · <needle color if relevant> · <total>s) — verbatim VO per clip, in play order:`

Table columns, in this exact order — `| # | Clip | In-Out | VO (verbatim) | Hair | Do |`:
- **#** — slot number in play order, starting at 1.
- **Clip** — the final library ID for that slot (e.g. C63, A20n, A35n); `hook` for the unlogged hook.
- **In-Out** — the clip's VO window in SECONDS with 2 decimals, from the SRT (e.g. `4.03-11.10`).
- **VO (verbatim)** — the EXACT SRT text for that clip's cue(s), in quotes; multiple cues joined with
  ` / `. Never paraphrase or summarize the VO here — verbatim only.
- **Hair** — the hair state for the beat (FULL, FULL+spot, mild thin, mod thin, receding + hat, THIN),
  or `n/a` for no-character plates.
- **Do** — `build` for a new render, `pull` for a reuse of an existing library clip.

After the table, an `Editing notes:` block: per-slot trims, any clip SHORTER than its VO window (flag
it), reuse callouts, and any split-anchor note. Keep it to notes that affect the edit.

**HAIR-STATE CONTINUITY (check on EVERY timeline).** Hair state must not flip between ADJACENT clips
unless the VO earns a transition (an age arc, a before/after, a regrowth timeline). Assign each slot's
Hair by looking at its NEIGHBOURS, never in isolation. In particular, the CTA / payoff tail runs on the
confident FULL-hair presenter clips (links / guarantee / urgent-CTA closers are logged FULL), so any
closer or CTA beat BUILT to sit among them must be FULL too — a THIN closer right after a FULL guarantee
clip flips the hair full->thin on the last shot and reads as a continuity error. Rule: when a BUILD lands
between/after PULLS, match the neighbouring clips' hair state unless the script explicitly shows the
change. Scan the Hair column top to bottom before delivering and flag any unearned flip.

## Engine rules baked into the format

- **Omni Flash 1.1 clips are 4 / 6 / 8 / 10s only.** Pick the nearest step **≥ the beat's VO length**
  from the SRT, generate long, trim the tail to the VO window in the edit. Never round down, never
  default to 4s (see "CLIP LENGTH" above).
- **Omni Flash ignores per-second timestamps** — write the camera arc as ordered phases ("first...
  then... finally"), never `0.0-1.0s` marks.
- **Duration comes from the SRT beat length**, not from a default. A short VO line gets a short clip;
  that is correct, not an error. Only lengthen a clip if the user asks.
- **No audio in the clip.** VO, music, SFX, and captions are the user's CapCut edit.
- **One camera move + one performance per clip.** The move is a per-beat creative choice
  (`motion-grammar.md`), never the same move on every shot.

## LABEL / TEXT STABILITY (any clip showing a real label or text)

Text is stable in a still but MORPHS in video — letters warp, scramble, re-spell, or flicker frame to
frame. On any product or label clip, add a **LABEL LOCK**:

- Name the exact wording in the prompt (e.g. `"ALPHA" / "INFUSE" / "Micro Infusion System"`) and state
  it must stay STABLE, sharp, and UNCHANGED for the whole clip.
- Forbid morph/warp/scramble/re-spell/flicker of the letters in the negatives.
- Keep the labeled face TOWARD camera — allow only a slight rotate that never turns the text away, so
  the label stays readable and constant. Big spins that hide and re-reveal the label invite garbling.
- This is the moving-image counterpart to the still-frame label rule in `anchor-format.md`.

## FEATURE / IDENTITY DRIFT LOCK (atypical or "missing" features)

Image-to-video weights the START FRAME heavily, then DRIFTS toward its training prior over the later
frames. So any feature that CONTRADICTS the model's prior tends to get "completed" mid-clip — a
plain text negative controls frame 1 but weakens as motion is extrapolated. The classic case: a
character with a jaw/chin beard but NO mustache — the model's face prior says "bearded face has a
mustache," so it grows one mid-animation. Same failure for any deliberately absent or unusual trait
(a scar that vanishes, an asymmetry that self-corrects, a missing feature the model adds back).

To hold it, use all three (a negative alone is not enough):
1. **Unambiguous start frame.** Fix it in the ANCHOR first — make the contradicted region read clearly
   (e.g. a clean bare upper lip with a visible GAP between beard and mouth). A clean start frame gives
   the model no seed to grow.
2. **A hold-every-frame clause** in the animation prompt (a rule, not just a negative): name the
   feature and state it stays EXACTLY as the start frame for the ENTIRE clip, at every frame, and must
   not appear/grow/spread/change.
3. **Minimize motion in that region.** The more an area is re-rendered, the more the prior leaks in.
   If the performance does not require moving it (e.g. a never-talking character's mouth), say that
   region stays still.

This is the same class of fix as the LABEL LOCK. Character-specific specifics (which features a given
character has or lacks) belong in that project's character bible, not here.

## Transition devices (motion that cuts for you)

- **Throw-to-lens / object-at-camera.** End a clip with the character hurling a prop straight AT the
  lens; the object rushing to camera fills and blurs the frame as a wipe into the next shot. The anchor
  held the prop in hand (pre-action); the throw lives here in the clip. Great for dismissing something
  (competitors, pills) straight into a mechanism plate or the next beat.

## Where the pieces come from

- Identity/world/product locks: the chosen Style Pack (`styles/*`) + `consistency.md` +
  `product-truth-lock.md`.
- Camera vocabulary and expressive-performance rules: `motion-grammar.md`.
- Which anchor covers which VO line and the clip's duration: the SRT timeline (`storyboard.md` Step 3,
  stage 5 voice + timing).
