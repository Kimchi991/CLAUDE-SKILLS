# Client profile — FreshBro (men's intimate wash)

Standing rules + reusable-asset library for FreshBro. Load alongside `SKILL.md` (Workflow 1 / Ad mode)
and the roblox style pack on any FreshBro job. Started 2026-09-24.

## The product
- **FreshBro** — men's intimate wash. Matte black bottle, "FRESH:" in a mint outline box over bold
  white "BRO", "MEN'S INTIMATE WASH", scent "Morning Wood", icons: long-lasting freshness / deep
  cleanse / pH balance / odor care. Use the NEW packaging (black flip-cap, "FOR THE BOYS DOWN THERE").
- **LABEL LOCK:** the bottle reads exactly `FRESH: BRO`; never garble or rename. Composite the real
  label in post if it softens. On video, add the moving-image LABEL LOCK (no morph/warp/flicker).

## Workflow + styles
- This is **Workflow 1 (Ad mode)**: VO carries, characters are B-roll (no lip-sync, printed mouth /
  mouth at rest). Banana = the platform-safe stand-in; NEVER explicit anatomy (platform-safe comedy).
- 7 scripts (SRTs + mp3 in `WORK_ERIC/NOW/Sept24/`, 1-7 all present). Each script is built in 3 render
  styles for volume: **roblox → skeleton → real-human** = 21 videos.
  - **Line A (roblox): DONE + client-approved 2026-09-24** (all 7 built, bundled, submitted to brand).
  - **Line B (skeleton): NEXT.** Client wants the SAME words but a **DIFFERENT narrator voice** so the
    brand reads it as a new video. That means NEW skeleton-voice SRTs with new timing — the roblox
    timelines do NOT transfer; re-map clip lengths from the new SRTs. Beats/concepts stay identical.
    Skeleton style = the **PINK PORCELAIN skeleton** (glossy pink porcelain + kintsugi GOLD cracks,
    deep focus); skeleton roster refs already exist on Ghlen's end (do not rebuild sheets).
  - Line C (real-human): third pass.
- SRT QC (roblox VO): "zinc ricinoleate" mis-said on S2 ("risinolite"), S5 ("Risan Elite"), S6
  ("zinc resinate"). Ghlen fixing in post; does not affect visuals.

## Bundle + naming (locked)
- Library folder (`ASSETS/_FRESHBRO/<LINE>/`) keeps PURE concept IDs as stable masters (`A30.mp4`).
- The per-script COPY-PASTE bundle in `NOW/<batch>/S#_<style>_<line>/` is renamed to PLAY ORDER as
  `Clip##_<ID>.mp4` (zero-padded), copied DIRECTLY to the target name (never rename in place — a locked
  folder throws "device busy"). "bundle" = one routine: rename new exports to concept IDs → copy-direct
  to `Clip##_<ID>` play-order folder → emit the assembly timeline. If unsure which script/line, ASK.
- Extra locks carried every job: markers-only (no pronouns), banana in hand near chest never at hip,
  vary location per beat (never default to a bathroom), prop continuity lock (one hand every frame, any
  exit is a deliberate throw not a vanish), A36 application = dark silhouette behind frosted glass with
  the bottle hero on a ledge.

## Roster (locked references)
- `@CHARACTER` — casual roblox man (light-brown tousled hair, orange hoodie, navy pants, teal/white
  sneakers, beaded bracelet). Used in problem/product beats.
- `@Character_Formal` — the SAME man glowed up: neat formal side-part hair, charcoal suit, teal tie,
  dress shoes. Same identity/face, built from @CHARACTER. Used on the FIX + CTA payoff beats.
- `@CHARACTER2` — mature blonde roblox woman: balayage blonde hair, pearl earrings, dark burgundy
  V-neck long-sleeve top, tan wide-leg trousers, tan flats. Expression sheet has neutral / concerned /
  unhappy (NO disgust panel) — sell recoil via body language + concerned mouth + turning away. She has
  NO glow-up version; always use her reference as-is, expression-only changes.
- `@PRODUCT` — the FreshBro bottle (above).

### Skeleton roster (line B — PINK PORCELAIN)
- **`@CHARACTER` (skeleton, casual)** — ref sheet: `projects/refs/freshbro-skeleton-character-casual.jpeg`
  (source `WORK_ERIC/Create_character_reference_sheet_20260913233018.jpeg`). Pink porcelain skull-face
  with kintsugi GOLD crack veins, brown tousled hair + brown beard, large expressive eyes (white sclera,
  brown iris), grey t-shirt, navy jeans, exposed skeletal hands/feet. Sheet has front/3-4/side/back
  turnaround + expressions (neutral / happy / worried / cocky smirk / shocked) + gold-crack swatch.
- `@Character_Formal` (skeleton, formal) and `@CHARACTER2` (skeleton woman) — CONFIRMED: both exist and
  were used to render line B (formal on the glow-up/CTA/closer beats, wife on the recoil/two-shot beats).
  They live in Ghlen's Google Flow, NOT archived to disk/repo (only the casual sheet is). Pull them from
  Flow when reusing the skeleton line; Ghlen to export them into refs/ as
  freshbro-skeleton-character-formal.jpeg + freshbro-skeleton-character2-woman.jpeg to future-proof.

## Reusable-asset library — `ASSETS/_Freshbro/<LINE>/`
One folder per render style, SAME concept numbers mirror across them:
- `A` = roblox, `B` = skeleton, `C` = real-human.

**File naming:** `<LINE><NN>` with the same number for a concept's still and clip → `A30.png` (anchor)
+ `A30.mp4` (animation). The number is the CONCEPT (stable, pull by ID from any script), NOT play
order. Suffix `f` only if a concept needs both a casual and formal variant. Pure no-character plates
(ingredients, barrier) are one shared file across A/B/C. Per-script hooks live in 60-69 and are
script-specific (not cross-script connective tissue).

### Concept dictionary (range skeleton follows broll-library)
```
10 woman recoils / grossed out at the banana (two-shot)          [character]
11 man sheepish / defeated with the banana (solo)                [character]
12 banana goes toxic green / escalation, she bails               [character]
20 pH gauge gag: needle spikes 9-10 vs the healthy 5             [character + gauge]
21 good bacteria stripped / nuked by regular soap                [plate, shared]
22 skin barrier wrecked / chafe / dry-crack                      [plate, shared]
23 pH comparison gag (pool vs orange juice)                      [plate, shared]
24 alkaline → bad odor-bacteria bloom / swamp / stink            [plate, shared]  (distinct from 21: BAD bacteria thriving)
25 deodorant plugs / seals sweat-gland pores                     [plate, shared]
30 FreshBro product reveal, casual man presents                  [product + character]
31 FreshBro bottle hero (macro, no character)                    [product plate]
32 ingredients: fermented probiotics + zinc ricinoleate          [plate, shared]
33 ingredients: glycerin + aloe                                  [plate, shared]
34 ceramides rebuild / seal the skin barrier                     [plate, shared]
36 application: 5 seconds in the shower (dark silhouette)         [character + product]
40 GLOW-UP fix: formal man + clean banana + woman returns        [character, formal]
41 formal man solo, confident glow-up                            [character, formal]
50 CTA: formal man points to link + product hero                 [character, formal + product]
60-69 per-script hooks (dish soap / shampoo / deodorant / dumpster fog / etc.) [character, script-only]
```

### Per-script build map (line A roblox — all DONE 2026-09-24, play order)
Hook numbers: 60=S2 (ghosting) · 61=S3 (dish soap) · 62=S4 (shampoo) · 63=S5 (body wash) · 64=S6
(deodorant) · 65=S7 (dumpster fog); lettered a/b/c per beat.
- **S1 (pH/"her problem", 23.9s):** A10 · A20 · A12 · A30 · A40 · A50. (all built here)
- **S2 (ghosted/good bacteria, 33.8s):** 60a · 60b · A21 · 60c · A30 · A32 · A50.
- **S3 (dish soap, 38.8s):** 61a · 61b · A20 · A22 · A30 · A34 · A32 · A36 · A50.
- **S4 (shampoo, 26.3s):** 62a · 62b · 62c · A22 · A33 · A36 · A50.
- **S5 (body wash/pool-OJ, 41.8s):** 63a · A20 · 63b · A23 · A24 · A30 · 63c · A32 · A36 · A50.
- **S6 (deodorant, 46.9s):** 64a · 64b · A25 · 64c · A22 · A20 · A30 · A32 · A33 · A36 · A50.
- **S7 (dumpster fog, 69.7s):** 65a · 65b · 65c · 65d · 65e · 60c · A20 · A21 · A24 · A30 · 63c · A32 ·
  A36 · A50 · 65g.

**Open items:** A32 needs an 8s master (S3/S5/S6/S7 have ~6.3-8.1s ingredient windows; current is 6s);
A50 8s master for the longer CTA windows. Rebuild once, re-pull.

## Reuse rule
Build the recurring beats once (product reveal 30, glow-up 40, CTA 50, ingredient 32, pH 20), then PULL
them into scripts 2-7; only the per-script hook (60s) is a fresh build each time. Mirror to B/C for the
skeleton and real-human remakes using the same numbers.
