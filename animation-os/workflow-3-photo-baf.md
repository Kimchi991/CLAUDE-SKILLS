# Workflow 3 — Real-Person Photo Before/After (NovaMane "spam remake")

A **sub-mode / workflow** of animation-os. High-volume, real-person, PHOTO-only before/after ads that
remake the proven TikTok BaF format: a few static selfies + on-screen text + a trending/short sound +
a slow push-in. NO AI video, NO voiceover. The whole ad is stills assembled in CapCut.

> Client: NovaMane (men's beard + hair). Started 2026-09-23 from the client's BaF example set. Load
> alongside `projects/client-novamane.md` and `projects/broll-library.md`. When a rule here conflicts
> with a general animation-os default, the client's stated preference (captured here) wins for THIS
> format only.

Naming: the user calls this **Workflow 3**. Formal renaming of the other modes to "Workflow 1 / 2" in
`SKILL.md` MODE ROUTING is PENDING the user's mapping confirmation, do not renumber the routing table
until confirmed.

---

## WHAT IT IS (vs the other modes)
- Ad mode = one flagship animated VO ad. Spam mode (`spam-mode.md`) = short VIDEO before/after cuts.
- **Workflow 3 = PHOTO before/after.** Just stills. The "motion" is a CapCut Ken Burns push-in, never
  Veo/i2v. Reason: animating a photoreal face drifts the identity, which is fatal when the whole ad is
  one face and the point is "same guy, before vs after." Stills also cost no render credits and match
  the reference format (the examples are static photos with a push-in).

## THE FORMAT (per video)
Five aired shots, in this play order:
1. BEFORE 1 — car selfie, straight to camera.
2. BEFORE 2 — bathroom, angled ~10-15 deg to show hairline + jaw, eyes still on camera.
3. AFTER 1 — dressed well, straight to camera, smiling.
4. AFTER 2 — dressed well, DIFFERENT location from AFTER 1 (outdoors is the default contrast), angled
   ~10-15 deg, eyes on camera.
5. PRODUCT — NovaMane applicator/box in hand.

CapCut: 2 seconds per photo, slow push-in on each, straight cuts (NovaMane lock: no transitions/SFX),
captions in the native-TikTok font with a THICK black outline, the client's caption lines, the sound
he specifies (e.g. the LoZ file for the test).

## THE IDENTITY-ANCHOR METHOD (the #1 fix — do this every time)
Building the AFTER first as the anchor FAILED: a full beard hides the jaw/chin, so every thin-beard
BEFORE forced the model to invent a different jaw = identity drift across shots.

Correct method:
1. **Build a NEUTRAL IDENTITY ANCHOR first** (text-to-image, no ref): the guy with only LIGHT SHORT
   STUBBLE so the full jaw/chin/cheeks are visible, normal hairline, straight to camera, neutral. This
   image is NOT aired, it is only the reference.
2. **Attach that SAME anchor image to all 4 face shots.** Never swap it, never chain one generated
   shot into the next. Add the full beard for the afters, thin it (and recede the hairline where the
   script calls for it) for the befores. Because the anchor shows the real jaw, before and after sit
   on the same face.
3. Each guy's approved identity anchor is a reusable roster asset (see broll-library reuse system):
   future batches PULL him instead of regenerating.

## HARD LOCKS (bake into EVERY prompt — this is the anti-error checklist)
1. **SHARP DEEP FOCUS.** Background fully in focus, front to back. No blur, no bokeh, no shallow depth
   of field. Blurry backgrounds read as AI on selfies (client note) and it matches NovaMane's standing
   deep-focus lock. (Fixes: "why is the background still blurry.")
2. **EYE CONTACT.** Face looking directly into the camera lens with clear eye contact. Turned shots
   angle only ~10-15 deg with the face rotated BACK and eyes locked on the lens. Negatives every time:
   `no profile, no looking to the side, no looking away, no averted eyes, not looking off-camera, no
   downward gaze.` (Fixes: the head-turn made him look away.)
3. **BEFORE beard = genuinely undergrown.** Thin, wispy, sparse, bare skin between hairs, barely
   connecting. Push it hard or the pain point is undersold. Keep the hairline state per script (V1/V3
   recede; V2 hairline stays full). Hairlines were client-approved, do not change them.
4. **WARDROBE split.** BEFORE = plain white or grey crew-neck t-shirt. AFTER = polo or nice outfit.
   Sells the glow-up.
5. **LOCATIONS differ per shot**, and AFTER 2 differs from AFTER 1 (outdoors is the default). Before =
   car + bathroom; after = nice indoor + outdoors.
6. **PRODUCT label = NovaMane.** Attach `@PRODUCT`, freeze it, do not redraw the label, composite the
   real label in post. Negatives: never NovaInfuse or garbled. (NovaMane legal lock.)
7. **No baked text in the stills.** Captions are the CapCut layer. Full-bleed 9:16, no caption bar.
8. **DISCLAIMER (regulated claim).** Every before/after is a results claim. NovaMane's own rule wants
   `Dramatization. Results vary. With consistent use.` on the reveal. Confirm with the client/brand
   before PUBLIC posting; flag it, do not silently drop or add.

## PROMPT FORMAT (locked, sectioned — never flatten to prose)
Emit each shot in the SAME sectioned layout, every section, every shot:
`[shot description line]` then `IDENTITY:` / `STATE:` (befores/afters) / `POSE:` / `WARDROBE:` /
`LOCATION:` / `FOCUS:` / `NATURAL PHONE LOOK:` / `FULL-BLEED:` / `NEGATIVE:` / `OUTPUT:`. Label each
shot OUTSIDE the code block; the block is paste-ready only. (Fixes: "why is the prompt format
different.")

## TOOL
Photoreal stills in Flow image mode / Nano Banana Pro. NOT the cinematic-3D creator-os look, these
must read as amateur phone selfies. Assemble in CapCut.

## LESSONS (append over time)
- 2026-09-24, workflow created. Every item in HARD LOCKS above is a fix for a real error hit on the
  first NovaMane BaF test batch (blurry backgrounds, looking away on turns, identity drift from a
  full-beard anchor, before beards too full, AFTER 2 location too similar, prompt format drift). The
  neutral-stubble identity anchor is the single highest-leverage fix.
