# Client profile — NovaMane

The single place for NovaMane's standing rules and locks. Load this alongside `broll-library.md` on any
NovaMane job. The library holds the clip inventory + identity specs; this holds the brand rules and the
per-video client shot notes. When a rule here and a scattered copy elsewhere disagree, THIS file wins.

## The product
- **NovaMane** — a micro-infusion hair-serum applicator (the blue version of the green AlphaInfuse).
- **Offer boilerplate** (recurs in every script): 24k gold micro-needles thinner than paper → open
  micro-channels → 18 actives past the scalp barrier into the follicle (copper peptides at double the old
  formula, adenosine, caffeine, pea-sprout extract, apple polyphenols) → hair-growth offense + hair-loss
  defense → 90 seconds every other day before bed → drug-free, no prescription, no pills → 180-day
  money-back guarantee → links below.

## Non-negotiable brand locks
1. **NovaMane on every surface, every generation.** Bottle AND box spell `NovaMane` (capital N, capital
   M). Never "NovaInfuse", never a competitor-looking or garbled word. Legal: avoids competitor-brand
   confusion. Add the LABEL LOCK (`video-format.md`) to every product/box still and animation, and
   override any "NovaInfuse" text printed on a reference image.
2. **No baked-in visual transitions.** No camera-flash, no whoosh/transition SFX, no throw-to-lens
   device. Straight cuts only; transitions/SFX are the editor's layer and this client wants none.
3. **Deep focus always.** Sharp front to back, no background blur / bokeh.
4. **Needle colour follows the VO** — clear by default, 24k GOLD when the script says gold. Gold product
   clips are tagged `-n` (skeleton) / `-g` (roblox).
5. **Serum colour:** NovaMane serum is LIGHT BLUE. A failing/generic serum in a demo is AMBER, never
   blue (keep the contrast).
6. **Regrowth reveal = a regulated results claim.** Any thin→full hair reveal MUST be (a) EARNED on
   screen — a transformation morph or a clear "N months later" time cue, never a hard thin→full cut (that
   also trips the hair-continuity rule) — and (b) carry the editor disclaimer `Dramatization. Results
   vary. With consistent use.` over the reveal. If a script's VO never claims regrowth (a permission or
   urgency closer), do NOT add a full-hair reveal unless the client signs off on it. No disclaimer, no
   reveal.
7. **Beard ads always SHOW the transformation, placed right AFTER the apply beat (user-locked 2026-09-14).**
   Every beard ad must give the viewer the patchy→full payoff, not end on the problem state. If the script
   already contains a progression/diary (e.g. S4's 90-day), that IS the transformation. If it does NOT (a
   problem→product→CTA script like S3), INSERT a patchy→full transformation MORPH (first-last-frame: START
   = the just-applied patchy state → END = full beard, identical framing/pose/light so only the beard
   changes) immediately after the application beat; the presenter then stays FULL through the closers (so
   the CTA closers pull the FULL clips, not patchy ones). This reveal is a regulated results claim, so
   rule #6 still governs it: carry the `Dramatization. Results vary. With consistent use.` disclaimer, and
   get client sign-off when the VO itself makes no results claim.

## Product refs (specs live in `broll-library.md` marker glossary)
- `@PRODUCT` — clear bottle, blue serum, clear micro-needle dome cap, label "NovaMane" +
  "micro-infusion system" + green power-button mark.
- `@NOVABOX` — white box, front reads `NovaMane`, lid tagline "WARNING: Things are about to get hairy"
  over follicle icons. (Older rows call it `@NOVAINFUSE` — same box, rebranded.)

## Characters
- **Roblox line** = `@ROBLUX` (male orange-hoodie avatar). THIN ref = approved S1 Flow-1 frame; FULL ref
  = approved turnaround. A female avatar, if ever built, tags roblox·hair clips `-w` (none exist yet).
- **Skeleton line** = `@SKELETON` (porcelain kintsugi skull; mustache lock + the verified phrase every
  clip). Identity ref FILES the user attaches: `A1` = THIN/balding, `A12` = FULL (not the library rows).

## Per-video client shots (build exactly as directed, flag risks, never silently drop)
| Script | Client-directed shot |
|---|---|
| Finasteride (side-effects) | limp banana + large firm banana = the E.D./libido gag; "hairline vs manhood" close |
| Finasteride + DHT (Script 4) | on "progress reverses", the roblox man's hair falls out (reuse C86) |

Client feedback is a lock edit, not a rebuild (`qc-deliver.md` revision loop). Obey the creative, flag a
risk in one line (legal / brand / a standing rule), let the user or client make the call.

## Open regen queue (box still reads NovaInfuse — fix to NovaMane)
S3 roblox C35g / C53g / C30g (flagged first), then S1 C35 / C53 / C30, S2 A30 / A31 / A31n / A33 / A53n.
Disk: `A31nn` is the box-fixed A31n (rename over it once the old render retires).

## Real-person test phase (video 1) — locked from client feedback 2026-09-12
The client is testing a REAL-PERSON (photoreal) creator for the Sept-11 women's scripts before scaling.
Rules for this phase:
- **Nail video 1 first (Script 4, postpartum testimonial), THEN volume.** Do not pre-build the other
  videos until the first is approved.
- **Build FRESH, NO reuse.** Disregard E-line pulls during the test; every clip is a fresh build until
  the real-person workflow is proven. (Reuse/library optimisation returns later.)
- **`@CHARACTER`** = the real-woman asset (ONE reference image, age tweaked in-prompt). Library line = `E`
  (real-person·hair). Do NOT use the roblox `@ROBLUXW`/`@ROBLUXWO` avatars for this batch (parked).
- **Thinner hair:** "THIN" alone renders too healthy. Use the explicit line — sparse, visible scalp at a
  widened part + temples, obvious temple patch, "reads thin at a glance," plus negatives `no thick/full/
  voluminous hair, no healthy density`.
- **Product:** use the clean `@PRODUCT` asset. Do NOT describe the product/label in prompts (the reference
  carries it — describing it causes garble). In clips, FREEZE the product (still, flat to camera, no
  rotation, no fingers over the label); render it as a re-lit 3D object in-scene (not a flat cutout);
  composite the real label in post if it still softens.
- **Format:** using the Veo/Flow sectioned template (`pipeline-reverse-engineer` skill), adapted to our
  SILENT B-roll (no dialogue/lip-sync, VO over post). Reference order: scene/identity first, product last.
- **VO:** female CLONED voice (ElevenLabs). Some lines render robotic (stability likely too high). API
  KEY stays LOCAL (env var / .gitignored .env a script reads) — never pasted in chat, never sent to me.
- **Pending automation:** a dead-space / pause remover for the VO. Order becomes VO -> remove pauses ->
  new SRT -> timeline (cutting pauses re-times everything).
- **Baby in frame — client-approved, DETAIL-framed only (updated 2026-09-16).** The client OK'd showing the
  baby for the Sept-15 real-person batch, but ONLY as a DETAIL — a foot/toes, a fist, a hand at the mouth, the
  head from side/back — NEVER a full infant front face. Frame on the body part plus the hair; keep the child
  partial and still. **Flow's minor-safety filter is a SEPARATE technical gate that client permission does NOT
  switch off:** it can still refuse or distort a baby render, and it trips on baby/nursery/crib wording even in
  negatives, so avoid those words and describe the safe scene directly. If Flow refuses, FALL BACK to baby-free
  staging (the danger shown on her own body: a strand cinched on her finger/lip, an empty car-seat harness, a
  tiny sock). The VO carries the context either way. (Superseded the prior hard "no baby in any frame" rule.)

_Started 2026-09-11 from brand feedback. Update when the client sends new rules._
