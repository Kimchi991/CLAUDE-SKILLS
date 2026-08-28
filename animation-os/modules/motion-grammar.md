# Motion Grammar

Cheap camera and motion moves that read as expensive. Video prompts do not need to be complicated —
one camera move + one subject action per clip. Front-load the action, leave a still tail for trimming.

## Camera is a per-beat choice, never a default

The camera move is a **creative decision motivated by the scene**, chosen fresh for every shot from
the vocabulary below. Do NOT default the same move (e.g. a push-in) onto every clip — same-move-every-
shot is what makes an ad read cheap. Premium B-roll picks the move that matches the emotional beat and
leaves room for the character action. This is `styles/*` camera language + directive §21 made concrete.

## The cinematic camera vocabulary

| Move | Feels | Choose it on a beat that… |
|---|---|---|
| **Static / locked-off** (tiny parallax only) | deadpan, confident, premium stillness | is comedic or a clean product hero — let the image sit; stillness sells the joke |
| **Slow push-in** (dolly) | intimacy, escalation, "take this seriously" | is a reveal, a turn, or the product moment |
| **Slow pull-out** | context, scale, "oh no it's worse" | exposes a bigger problem (irritation, shedding, the mess) |
| **Lateral track / slide** | depth via parallax = expensive look | is an energy beat, or moves focus between two things |
| **Tilt up / down** | discovery, hierarchy | travels scalp → face, or product → face |
| **Macro slow drift** | scientific, premium detail | is the x-ray follicle / blood-flow insert or a product macro |
| **Rack focus** | directs the eye, filmic | shifts attention product ↔ character inside one frame |
| **Snap-zoom** | punch, aggression | lands a punchline or a hard "it's over" |
| **Macro transition** (push a detail until it becomes something else) | connective, seamless | crosses from the outside problem to the inside cause (scalp → x-ray) |
| **Match cut / object wipe** | one-continuous-film feel | cuts on a shape or motion into the next beat |
| **Whip / match cut** | kinetic | jumps *into* an x-ray insert or a new scene |

Two character moves that stack under any camera: **oversized-prop reveal** (introduce the product as a
giant hero prop first) and **character attention** (eyes snap to targets or into lens; hands point at
the problem, then the product) — both guide the eye with no on-screen text.

## Expressive performance is mandatory (every clip)

A video clip is a performance, not a slowly-drifting still. **Every clip must carry a specific,
readable, characterful performance** — that is what keeps viewers watching. Enforce on every video
prompt:

- **Eyes act first.** Widen, dart, cross, half-lid, snap into lens, wink — the eyes carry the emotion
  of the beat. Never a blank, fixed stare.
- **Give the beat one clear emotion, played big.** Proud, delighted, smug, grossed-out, triumphant,
  cheeky — name it in the prompt and push it past subtle. A neutral/flat performance is a reject.
- **Micro-life throughout** (subordinate to the primary action): weight shift, head tilt, shoulder
  move, brow cock, jaw move — so the character never looks frozen.
- **Comedy/energy comes from behavior**, not slapstick chaos or random gestures. Motivated, appealing,
  readable.
- Still a **B-roll performance**: expressive face and body, but no speaking and no lip-sync — the VO
  carries the words.

Carry the anchor's expression forward and let it *play* — if the anchor is a smug cross-eyed grin, the
clip performs that grin (a proud chin-lift, an eye dart), it does not settle into a neutral face.

## Rules that keep it premium

- **One motivated move per shot.** Match the emotional beat; never move because the model can.
- **Leave animation room** in the anchor's framing for the move to travel.
- **Never** orbit, Dutch-angle, spin, fisheye, handheld-shake, or random drift (style-pack negatives).

- **The spectacle shot** gets the most motion — give the transformation moment (hair regrowing, the fix
  landing) room, physics, squash-and-stretch.

## Duration

- **Omni Flash 1.1 clips come only in 4 / 6 / 8 / 10s.** Pick the **nearest step ≥ the VO line**,
  generate long, **trim the tail to the VO in the edit**. Never round down. Gap goes in the tail, not
  the intro.
- **Prefer the shorter viable step** for held/comedic beats (less room to drift); spend 8/10s only on
  beats that need it (the transformation spectacle, a long product hero).
- **Omni Flash ignores per-second timestamps** — write the camera arc as ordered phases ("first… then…
  end"), not `0.0–1.0s` marks. Exact timing is fixed in the edit.
- **Generate no audio in the clip.**

Captions, audio, and SFX are the user's CapCut edit — the skill does not prescribe them. For hook and
cross-shot pacing, see `modules/engagement.md`.
