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

## Rules that keep it premium

- **One motivated move per shot.** Match the emotional beat; never move because the model can.
- **Leave animation room** in the anchor's framing for the move to travel.
- **Never** orbit, Dutch-angle, spin, fisheye, handheld-shake, or random drift (style-pack negatives).

## Rhythm rules

- **Sync every visual hit to the emphasized voiceover word.** You already have the VO timing.
- **Hard cuts by default.** Pace and action-matching drive the edit; save fancy transitions for a
  reason.
- **Slow down on the pain beats, speed up on the CTA.** Fastest cuts at the end for urgency.
- **The spectacle shot** — give the one transformation moment (hair regrowing, the fix landing) room
  and the most motion. Physics, squash-and-stretch, particles.

## Duration + audio

- **Omni Flash 1.1 clips come only in 4 / 6 / 8 / 10s.** Pick the **nearest step ≥ the VO line**,
  generate long, and **trim the tail to the VO in the edit**. Never round *down* — an undershoot
  leaves the line uncovered. Plan any gap into the clip's tail, never the intro.
- **Prefer the shorter viable step for held/comedic beats.** The longer the clip, the more room the
  model has to drift identity or invent unwanted motion. Only spend 8/10s on beats that truly need it
  (the transformation spectacle, a long product hero).
- **Omni Flash does not obey per-second timestamps.** It reads overall motion intent, not a timeline.
  Write the camera arc as ordered phases ("first… then… end"), not `0.0–1.0s` marks. Exact timing is
  fixed in the edit against the VO, not in the prompt.
- **Generate no audio in the clip.** No dialogue, VO, music, or SFX — audio is assembled separately.
- Characters are **B-roll**: they may react, gesture, interact with the product, but they do not speak.

## Captions (added in edit, never in the prompt)

Single-word or two-word, dead-center, bold sans with a heavy black stroke, popping/scaling on each
syllable (karaoke style). Never bake text into the generated footage.
