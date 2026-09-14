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

## The Edit Bundle (play-order export for the editor — user-locked 2026-09-14)

After the clips pass QC and are renamed to their library IDs, build ONE edit-ready folder so the editor
never hunts for clips one by one across the ASSETS letter-folders. Run it the same way every script:

1. **Make the folder** next to the script's source: `<script folder>\<script name> - assets` (e.g.
   `Sept12\script 4 - assets`).
2. **COPY every TIMELINE SLOT into it, in play order, renamed `NN_ID`** — two-digit slot number +
   underscore + the clip's library ID: `01_hook`, `02_G30`, `03_A20n`, … `21_G52`. The `NN` is the
   assembly-timeline `#` (play order), so the files sort into edit sequence; the `ID` keeps identity
   traceable back to the library.
3. **Reused clips are DUPLICATED into each slot they play.** A clip that appears twice in the timeline
   gets two copies (e.g. `03_A20n` and `14_A20n`, `04_G36` and `17_G36`). The editor imports top to
   bottom and every slot is already filled — no manual re-ordering.
4. **COPY only, never move.** The originals in `ASSETS\<letter>` stay put and untouched; the bundle is a
   throwaway convenience copy. Use no-clobber so a re-run never overwrites. Pull clips are copied from
   their OWN letter-folder (A/C/…), builds from this script's folder.
5. **Optional:** copy the script's `N.mp3` (VO) and `N.srt` in too if the editor wants them beside the
   clips; ask, since they already live in the script folder.
6. **REBUILD into a NEW versioned folder, never delete-and-rebuild in place (locked 2026-09-15).** When a
   renumber or re-cut changes the play order, build the corrected bundle in a fresh sibling folder
   (`<script name> - assets v2`); do NOT `rm` the old one and rewrite it. The editor (CapCut) and Explorer
   hold imported clips open, so an in-place delete fails on the locked files and leaves a half-old /
   half-new mess (this happened on S3: 35 files where only 20 belonged). A new folder sidesteps the lock
   entirely; delete the stale folder later once the app releases it. Same reason: never copy INTO a bundle
   folder that is currently open in the editor.

The Edit Bundle is generated FROM the locked assembly timeline (`video-format.md`) — the timeline `#` and
`Clip` columns ARE the bundle's `NN_ID` filenames, so the two always agree. Regenerate the bundle if the
timeline changes.

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
