# QC + Deliver (Stage 11) — the last gate, and the revision loop

The single checklist before an ad ships, plus how client feedback re-enters the pipeline without
redoing everything.

## Final QC checklist (run every shot before assembly)

- **Identity holds.** Same character every shot: face, eyes, build, proportions, materials, render.
  (`consistency.md`)
- **Style on-model.** Every shot is in the ONE chosen Style Pack — no style flip, no drift. (This is
  also caught earlier by the style-confirm gate; verify again here.)
- **Story-state correct per beat.** The variable (hair stage, beard, expression) matches the beat's
  planned CURRENT STATE. On a milestone ad, the hair arc reads: problem → change → result, in order.
- **Product truth.** Real brand only from `@PRODUCT`; label composited in post, not generated;
  competitors plain and unbranded; price tags blank. (`product-truth-lock.md`)
- **Anti-hallucination.** No garbled text, screens, logos, or UI baked into a frame.
- **Timing.** Each clip is trimmed to its SRT window (tail cut, not the intro). Total matches the VO.
  (`voice-timing.md`)
- **Hook.** The first 1–1.5s stops the scroll with sound off. (`engagement.md`)
- **Clean plates.** No motion blur carried from the anchor, no floating props, hands clean.

Fix anything that fails HERE, before delivery — never ship a known-bad shot.

## The revision loop (client / reviewer feedback)

Feedback is not a full rebuild. Turn each note into a **lock edit**, then re-run only what it touches.

1. **Read the notes into buckets:** world/background, pose/framing, character, product, pacing, claims.
2. **Update the lock, not the shot.** A world note ("bright white marble bathroom") edits the WORLD lock
   in the Style Pack / `@WORLD`; a pose note ("vary the poses, no hand-to-camera") edits the pose-variety
   rule. The lock change then applies to every regenerated shot, consistently.
3. **Re-enter the pipeline at the earliest affected stage:** world/style/pose → back to stage 6/7 then
   regenerate anchors (stage 9); a single wrong shot → regenerate just that anchor + its clip.
4. **Only re-run affected shots.** Approved shots that the note does not touch stay as they are.
5. **Re-run QC** on the changed shots before re-delivery.

Keep the locks (world, pose rule, character DNA, product) as the source of truth so the same feedback
never has to be applied by hand twice.

## Then: log to automate

After delivery, log every manual step (stage 5 SRT export, anchor extraction, trimming) so the
repeatable machinery can be automated later (see `ARCHITECTURE.md`).
