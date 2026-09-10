# B-ROLL LIBRARY

A running inventory of every distinct B-roll clip we have generated, keyed by a stable ID so future
scripts can REUSE an existing clip instead of rebuilding it, and so identities survive across sessions.
This file is the durable memory: chat does not persist, this committed file does.

## The reuse rule (client-approved)
- Reuse is allowed, but ONLY on a **direct concept match** — same beat, same lane, same hair state,
  nothing forced. Never jam a clip in just to save work.
- **Always tell the user** when a reuse is available, and name the clip.
- Near-matches are NOT reused silently. Mention them as "build fresh, but a similar clip exists (ID)".
- B-rolls are silent, so a clip can sit under a different VO line as long as the on-screen action, lane,
  and hair state fit.
- **A `MISSING` reuse tag means the render is NOT on disk** (lost or never moved into the ASSETS folder).
  Do NOT offer it as a reuse; rebuild it if a script needs that beat. Currently missing: A16, A-o5 (ALPHA
  S1). A46 is NO LONGER missing — rebuilt as the Nova-S4 closer. Verified against `D:\WORK_ERIC\ASSETS\A`
  and `...\C` on 2026-09-11.

## Naming convention (generation -> rename) — SLOT-NUMBERED, one number per clip
Number every clip by its **TIMELINE SLOT** — the position it holds in the final assembly (slot `1..N`
in play order, pulled/reused clips included). Use that ONE number end-to-end: the anchor, the animation
(`@SLOT14`), and the timeline row all carry the SAME slot number for the same clip. Generate the NEW
builds in Google Flow named by their slot (gaps are fine where pulled clips sit between builds, e.g.
`1,2,3,4,5,6,14,19`), then RENAME to the library ID after approval. Every script build ships a rename map
(`slot 2 -> A63`, ...). Hooks are never renamed and never logged.
- **HOOK LOCATION — always fresh, creative, unique (never the default bathroom mirror).** The hook is the
  scroll-stopper; every hook must look distinct and visually interesting, matched to the script's theme
  (e.g. car rear-view mirror, gym locker room, pharmacy aisle, barbershop) — NOT the same generic bathroom
  every time. Recurring failure: defaulting the hook to a bathroom. Pick a setting the script earns.
- **NEVER use a separate build-order `1..N` sequence.** It collides with the slot numbers: a build called
  "7" that lands at timeline slot 14, while slot 7 is a DIFFERENT pulled clip, is exactly the confusion
  to avoid. The slot number is the single source of truth from generation through the edit.

## Letter = topic x render style
| Letter | Topic | Render style |
|---|---|---|
| A | Hair | Skeleton (@SKELETON porcelain) |
| B | Teeth | Skeleton |
| C | Hair | Roblox (@ROBLUX) |
| D | Teeth | Roblox |

New combinations get new letters. `A`+`C` share the HAIR dictionary; `B`+`D` share the TEETH dictionary.

**ONLY A / B / C / D are ever valid letters — there are exactly four folders.** Never invent a scratch
or placeholder letter (no `M`, and never borrow `D` as a temp label) even for scripts that aren't built
yet. Roblox·hair is ALWAYS `C`. When several look-alike scripts are in flight at once, assign real
letter+number IDs up front and **reserve a number block per script** so they can't collide (e.g. within
`C`: 70-74 graveyard, 75-77 minoxidil, 80-89 finasteride, 90-99 serum-demo). A placeholder letter is a
guaranteed rename headache later — don't create one.

### Reserved ID blocks (anti-collision registry)
Reserve a number block per script BEFORE assigning any IDs, so parallel in-flight builds never grab the
same number. Current `C` (roblox·hair) reservations:
| Block | Script / cluster | Status |
|---|---|---|
| C10-C59 | ALPHA + Novamane core concepts (dictionary) | built (mixed) |
| C60-C62 | counting format (Nova S1) | built |
| C63-C67 | age-decline arc (Nova S3) | built |
| C70-C74 | gimmick graveyard (S5) | RESERVED, not built |
| C75-C77 | minoxidil delivery (S7) | built |
| C81-C89 | finasteride side-effects | built |
| C90-C99 | serum-tracking demo (S6) | built |
| C100-C109 | DHT / masculinity (Script 4) | building |
**Next free C block: C110+.** Skeleton (`A`) mirrors the same dictionary numbers on the A-line. Update
this table the moment a new script starts — it is the single guard against the M/D collision mess.

## Number = fixed concept (strict within a topic)
- The number is a fixed concept within its topic, so `A21`==`C21` concept (same beat, different render).
- **Per-style copies (character + product shots only):** for beats where the render shows — character
  and product-hero shots — each render style keeps its own clip (a Roblox video uses `C35`, not `A35`).
- **No-character plates are SHARED across render lines.** A science/mechanism plate (no character) looks
  the same whatever the ad's character is, so it is REUSED across the skeleton and roblox lines, not
  copied per-style (e.g. the gold plates A20n/A21n serve BOTH the skeleton S2 and the roblox S3 ads).
- **Roblox rig is stiff — favor close-ups and small, contained motions** for roblox character beats
  (a hand press, an eye act), not big full-body action; frame tight so the motion needed is minimal.
- **Product variants within a letter.** When two products share a letter (ALPHA and Novamane are both
  hair·skeleton = A), a product-showing clip gets a product suffix so it doesn't overwrite the other's:
  `-n` = Novamane skeleton (A-line), `-g` = Novamane GOLD-needle roblox (C-line). Product-free beats stay
  plain and shared.
- **Open-ended:** not capped at 50; a full family continues into the next free block.
- **Hooks are never logged.** One-off / LOW-reuse non-hook beats live in the Appendix as `<Letter>-o<n>`
  (NOREUSE), and do not consume a concept number.

### Range skeleton
| Range | Family |
|---|---|
| 10-19 | Problem / decline (character) |
| 20-29 | Science / mechanism plates (no character) |
| 30-39 | Product / ingredient / packaging |
| 40-49 | Timeline / payoff (character, progressing state) |
| 50-59 | Closers / CTA / legal |
| 60-89 | Overflow (a full family continues here) |
| 90-99 | Misc / experimental |

### HAIR concept dictionary (A skeleton / C roblox)
```
10 thin establishing / THIN identity anchor      [THIN identity ref]
11 shedding clump, shower
12 mirror inspection, widening part / see-through
13 defeat / pile of empties
14 "here's the problem" direct-address pivot
15 skeptical inspect / product doubt
16 offense-no-defense realization (thin)
17 wet-hair disappointment (product let-down)
18 hype / anticipation lean-in
19 throw-to-lens transition (dismiss competitors)
20 needle macro / scale
21 channels open, actives descend
22 follicle feed, channel closes
23 topical fails on surface (shampoo sits)
24 barrier contrast (blocked vs through)
25 follicle lifecycle decline stages (healthy->dormant)  [25a-e]
26 dormant-vs-gone fork
27 hair-cycle + 3 intervention points
28 ingredient-mechanism revival (minox/dutas/cetirizine) [28a-c]
29 DHT binds / hormone silently shrinks follicle
30 product intro (character holds product+box, thin)
31 product hero (device + serum supply reveal)
32 ingredient plate (18 actives around bottle)          [32a overview, 32b hero detail]
33 guarantee / badge plate
34 product intro in-world (spray, white marble)
35 combine / offense+defense resolved (cocky)
36 application / use beat (stamp/spray to scalp)         [pose-lock @APPLYPOSE for the roblox line]
37 (reserve)
38 quiz / licensed-provider review beat
39 find-your-stage / urgency ("which stage are you")
40 month-1 / early no-change (patient, thin)
41 month-3 baby hairs (EARLY)                            [EARLY identity ref]
42 day-30 selfie (EARLY)                                 [Day-30 ref]
43 day-60 mirror (MID)
44 month-5 full hero (FULL)
45 day-90 payoff (FULL)                                  [FULL identity ref]
46 full-hair CTA payoff flip
47 reduced shedding / less fallout (early improvement)
48 smug "if only they knew" full flex
49 (reserve)
50 no-pills reassurance
51 links-below invite (soft CTA)
52 urgent CTA / take action
53 guarantee / 180-day window CTA
54 quick-routine reassurance (90 sec / no pills / no surgery)
59 legal / disclaimer end-card (branded, baked text)
60 count: 1 product, not enough (counting-format problem)
61 count: 3 products stacked
62 count: 6 / trend-chasing, still nothing
63 age-decline stage 1: earliest (full + tiny crown spot)
64 age-decline stage 2: mild thinning
65 age-decline stage 3: moderate thinning (oils)
66 age-decline stage 4: receding + hat ("hat guy")
67 age-decline stage 5: significant loss / resolve
70 gimmick graveyard: rosemary oil          (S5 graveyard — planned, NOT built)
71 gimmick graveyard: castor oil            (S5 graveyard — planned, NOT built)
72 gimmick graveyard: purple shampoo        (S5 graveyard — planned, NOT built)
73 gimmick graveyard: $500 red-light helmet (S5 graveyard — planned, NOT built)
74 gimmick tally: thousands wasted / part wider (S5 graveyard — planned, NOT built)
75 minoxidil squeeze/rub-in, "feel productive"
76 delivery-problem thesis ("not the product's fault")
77 closer: "you just never bought the door" (door = the micro-channel)
81 side-effect banana gag (limp vs firm)     [finasteride, CLIENT-DIRECTED]
82 open-the-label side effects (libido / E.D. / motivation)
83 don't-feel-normal-again-after-stopping
84 prescription-required trap
85 dermatologist / subscription / drug-in-chart-forever
86 progress-fades: hair falls out            [finasteride, CLIENT-DIRECTED]
87 try-everything-else vs a mountain of side effects
88 closer: "hairline vs manhood" (pays off the banana gag)
89 "works, unlike tiktok snake oils"
90 serum demo: minute-1 sits on surface (plate)
91 serum demo: minute-2 spreads / spills to forehead (plate)
92 serum demo: minute-10 dries on top (plate)
93 serum demo: hour-8 on the pillowcase (character)
94 serum demo: almost none reaches the follicle (plate)
95 multiply by every serum you've bought (character)
96 "your life and a laundry problem" — stained pillowcases (character)
97 "now watch": gold micro-needle opens a channel (plate)
98 "it goes down": NovaMane micro-infusion, blue serum descends (plate)
99 closer: "wrong direction, not wrong ingredients"
```
Serum-demo failing serum = AMBER/generic; NovaMane = LIGHT BLUE. 70-74 (graveyard) reserved but not yet
rendered — no inventory rows until built.

### TEETH concept dictionary (B skeleton / D roblox)
Same range skeleton; Enamio-derived. To be logged from the Enamio D-set when migrated. Families: 10-19
enamel erosion / sensitivity / staining; 20-29 remineralization / nano-hydroxyapatite plates; 30-39
pouch + gum product/ingredient; 40-49 enamel-restore payoff; 50-59 closers/legal.

## Marker glossary (identity locks)
Use ONE character reference per anchor (never stack two character refs -> drift). Product/world refs are
different subjects and attach alongside safely.

**Hair - Roblox line (@ROBLUX):**
- `@ROBLUX` = blocky Roblox-style avatar, matte toy-plastic; light-tan skin, simple friendly Roblox
  face, light-brown tousled hair, orange hoodie w/ small teal chest logo, dark navy pants, teal/white/
  orange sneakers, beaded bracelet on right wrist. THIN ref = the approved S1 Flow-1 frame (receding),
  or the age-32 frame C67 for the S3 arc. FULL ref = the original approved turnaround (full hair) =
  concept 45/46 payoff.
- `@PRODUCT` (NovaMane applicator) = clear glass mini bottle, BLUE serum, clear textured micro-needle
  DOME cap, label "NovaMane" + "micro-infusion system" with a small green circular power-button mark.
  **LABEL LOCK (legal — client rule):** the bottle MUST read exactly `NovaMane` (capital N, capital M)
  in EVERY generation, still and animation; never "NovaInfuse", never a competitor-looking or garbled
  word. Spell it in-prompt every time and add the LABEL LOCK from `video-format.md`. **Needle color
  follows the script's VO:** CLEAR by default (S1, VO silent on color); GOLD (24k) when the VO says "gold
  needles" (S2, S3, S4). Gold product clips are tagged `-n` (skeleton) / `-g` (roblox).
- `@NOVABOX` (NovaMane box; older rows/refs call this `@NOVAINFUSE` — same box, now rebranded) = white
  box, front reads `NovaMane` prominently, lid keeps the tagline "WARNING: Things are about to get hairy"
  over small hair-follicle icons, holds blue vials + the applicator. **LABEL LOCK: the box says
  `NovaMane`, NOT "NovaInfuse"** — override the printed word on the reference image; regen any delivered
  clip whose box still reads NovaInfuse.
- `@APPLYPOSE` = the standard applying-pose reference for concept 36 (identity + the hand-to-hairline
  apply pose; drop its background, set a fresh location). Locks the same apply pose across all Novamane
  videos. Roblox apply beats read best as a CLOSE-UP (stiff rig).

**Hair - Skeleton line (@SKELETON):**
- `@SKELETON` = glossy pale-pink PORCELAIN hard-shell face, kintsugi GOLD cracks, lower face exposed
  skull with FULL teeth (no lips), large hazel/amber eyes + brows, ash-blonde/brown hair w/ faded sides,
  short beard JAW/CHIN ONLY, exposed spine at collar, plain grey crew tee, pale-pink skeletal porcelain
  arms/hands. THIN ref = A10; EARLY = A41/A42; FULL = A45. Reference @A1 (the past stamp hook) for
  identity + a stamping pose, dropping its background for a fresh location.
- **@SKELETON identity reference FILES (user attachments — NOT library clip IDs).** The two go-to
  hair-state reference images the user attaches in Flow are named `A1` and `A12` on the user's disk:
  `A1` = THIN / balding state (receding blonde, bottle-holding frame), `A12` = FULL / thick-hair state
  (fuller blonde, couch frame). **NAME COLLISION — do not confuse these with the library rows** `A1`
  (old hook, not logged) or `A12` (mirror-inspection clip). When the user says "use A1 / A12 as
  reference," they mean these two identity frames. Take identity + hair state ONLY; DROP the bottle,
  the couch, and both backgrounds, set a fresh location. Mapping is A1=THIN, A12=FULL (verified with
  the user 2026-09-10). Use for any skeleton beat needing a locked thin-vs-full contrast (e.g. age arcs).
- **@SKELETON UPPER-LIP / MUSTACHE LOCK (recurring failure — apply on EVERY @SKELETON anchor and
  animation).** i2v drifts to the "bearded face = mustache" prior and grows a mustache mid-clip. Beat it
  with the physical framing, not a soft negative: the lower face is an EXPOSED PORCELAIN SKULL, so there
  is NO fleshy upper lip and NO philtrum skin — the zone between the nose and the top teeth is smooth
  hard porcelain/bone that CANNOT grow hair. The beard is ONLY on the jaw/chin below the mouth. In the
  anchor, state that zone is bare porcelain and add "no mustache/hair/stubble between nose and teeth" to
  negatives. In the animation, add a per-frame MUSTACHE LOCK naming the zone, hold it identical every
  frame, and keep the mouth/upper-lip region STILL (he never talks). This is the FEATURE/IDENTITY DRIFT
  LOCK from `modules/video-format.md`, made concrete for this character.
  - **PROVEN EXACT PHRASE (user-verified — paste verbatim on every @SKELETON anchor AND animation):**
    `no making of mustache, do not anything on the characters face`
    Keep the wording exactly as-is (rough grammar included); this literal string is what reliably
    suppresses the mustache in generation. Add it alongside the porcelain-skull framing above.
- `@PRODUCT` (ALPHA applicator), `@ALPHA` (ALPHA box) for the ALPHA line; `@SPRAY` (their-health amber
  spray). Product truth-locks per `product-truth-lock.md`.

**Teeth - Skeleton line:** `@ENAMIO` (pouch), `@GUM` (tan chicle pieces).

## Novamane client standing rules (locked from brand feedback 2026-09-10)
> Master copy: **`projects/client-novamane.md`** — load it alongside this file on any NovaMane job.
- **The product is NovaMane.** Every product surface — bottle AND box — spells `NovaMane` in EVERY
  generation. Kill "NovaInfuse" everywhere (legal: avoid competitor-brand confusion). Apply the LABEL
  LOCK on every product/box still and animation.
- **No baked-in visual transitions for this client.** No camera-flash, no whoosh/transition SFX, no
  throw-to-lens device (that was `A19`). Straight cuts only; transitions/SFX are the editor's layer and
  this client wants none.
- **Regen queue (box still reads NovaInfuse):** S3 roblox C35g / C53g / C30g (flagged by client first),
  then S1 C35 / C53 / C30, S2 A30 / A31 / A31n / A33 / A53n. S4 inherits the fix once A31n / A53n regen.

---

## INVENTORY

### Letter C — Novamane (hair · roblox)
| ID | Beat / purpose | Lane | Hair | Len | Reuse | Keywords | Used in |
|---|---|---|---|---|---|---|---|
| C14 | Reveal pivot: "nobody tells you", phony serums never worked, floor failures | CHAR | THIN | 8s | MED | pivot, phony serums, thousands wasted | S3 |
| C23 | Scalp barrier: topical beads on surface, never reaches follicle | PLATE | n/a | 8s | HIGH | barrier, topical fails, surface, blocked | S1, S3 |
| C30 | Product intro: lifts @PRODUCT, hopeful pivot (clear) | PROD | THIN | 4s | HIGH | product intro, novamane reveal, hope | S1 |
| C30g | Product intro (GOLD needles): "novomine built for this" | PROD | THIN | 4s | MED | product intro, gold, novomine | S3 |
| C32a | 18-actives overview: bottle + orbit of ingredients | PLATE | n/a | 4s | HIGH | 18 actives, formula, orbit plate | S1 |
| C32b | Hero actives: copper-peptide chain, adenosine, caffeine, pea sprout | PLATE | n/a | 8s | HIGH | hero ingredients, copper peptide chain, macro | S1, S3 |
| C35 | Offense/defense cocky stance (clear) | CHAR | THIN | 8s | MED | offense defense, cocky, floor + box | S1 |
| C35g | Offense/defense cocky stance (GOLD) | CHAR | THIN | 6s | MED | offense defense, gold, floor + box | S3 |
| C36 | Application: dome to hairline (clear, pose @APPLYPOSE) | PROD | THIN | 4s | HIGH | apply, before bed, pose-locked | S1 |
| C36g | Application (GOLD, CLOSE-UP, pose @APPLYPOSE) | PROD | THIN | 4s | MED | apply, gold, close-up, before bed | S3 |
| C50 | No prescription/no pills, waves off pill bottle (clear) | CHAR | THIN | 6s | HIGH | no pills, reassurance | S1 |
| C50g | No prescription/no pills (GOLD) | CHAR | THIN | 6s | MED | no pills, gold | S3 |
| C51 | Links-below soft CTA, casual lean (clear) | CHAR | FULL | 4s | HIGH | links below, soft CTA, casual | S1 |
| C51g | Links-below soft CTA (GOLD) | CHAR | FULL | 4s | MED | links below, gold | S3 |
| C52 | Urgent CTA lean-in + point (clear) | CHAR | FULL | 6s | HIGH | urgent CTA, point | S1 |
| C52g | Urgent CTA lean-in + point (GOLD) | CHAR | FULL | 4s | MED | urgent CTA, gold | S3 |
| C53 | 180-day guarantee, @PRODUCT + @NOVAINFUSE (clear) | PROD | FULL | 8s | HIGH | guarantee, 180-day, box | S1 |
| C53g | 180-day guarantee (GOLD) | PROD | FULL | 8s | MED | guarantee, gold, box | S3 |
| C60 | Count 1: single serum, unimpressed, filler | CHAR | THIN | 8s | MED | counting, 1 product, minoxidil doubt | S1 |
| C61 | Count 3: juggling 3 products, fake "boss" confidence | CHAR | THIN | 8s | MED | counting, 3 products, stacked | S1 |
| C62 | Count 6: slumped, trendy peptides, still nothing | CHAR | THIN | 8s | MED | counting, 6 products, defeat | S1 |
| C63 | Age 22: full hair + tiny crown spot, dismissive | CHAR | FULL+spot | 8s | MED | age22, thin spot, decline | S3 |
| C64 | Age 25: mild thinning, TikTok shampoo fails | CHAR | mild-thin | 8s | MED | age25, shampoo, decline | S3 |
| C65 | Age 28: oily, rosemary/pumpkin oil, still hoping | CHAR | mod-thin | 10s | MED | age28, oils, decline | S3 |
| C66 | Age 30: receding + hat, "hat guy" | CHAR | receding | 6s | MED | age30, hat, decline | S3 |
| C67 | Age 32: significant loss, resolve (S3 THIN ref) | CHAR | THIN | 8s | MED | age32, resolve, decline | S3 |
| C75 | Minoxidil squeeze/rub-in, "feel productive" | CHAR | THIN | 6s | MED | minoxidil, apply, productive | S7 |
| C76 | Delivery-problem thesis, "not the product's fault" | CHAR | THIN | 4s | MED | delivery problem, fair | S7 |
| C77 | Closer: "you just never bought the door" (GOLD) | CHAR | FULL | 4s | MED | door, closer, gold | S7 |
| C81 | Side-effect banana gag (limp vs firm) — CLIENT | CHAR | THIN | 4s | MED | banana, E.D., side effect | Fin |
| C82 | Open-the-label side effects (libido/E.D./motivation) | CHAR | THIN | 8s | MED | side-effect label, finasteride | Fin |
| C83 | Don't-feel-normal-again after stopping | CHAR | THIN | 6s | MED | not normal, after stopping | Fin |
| C84 | Prescription-required trap (Rx slip) | CHAR | THIN | 6s | MED | prescription, rx trap | Fin |
| C85 | Dermatologist / subscription / drug-in-chart-forever | CHAR | THIN | 8s | MED | chart forever, subscription | Fin |
| C86 | Progress fades: hair falls out — CLIENT | CHAR | THIN→falling | 6s | MED | hair fall-out, progress fades | Fin |
| C87 | Try-everything-else vs mountain of side effects | CHAR | THIN | 8s | MED | try everything else | Fin |
| C88 | Closer: "hairline vs manhood" (GOLD, pays off banana) | CHAR | FULL | 6s | MED | manhood, closer, gold | Fin |
| C89 | "Works, unlike tiktok snake oils" (GOLD) | CHAR | THIN | 6s | MED | snake oils, tiktok, gold | Fin |
| C90 | Serum demo min-1: sits on surface (AMBER, SHARED plate) | PLATE | n/a | 4s | HIGH | serum demo, surface, amber | S6, S7 |
| C91 | Serum demo min-2: spreads/spills to forehead (AMBER) | PLATE | n/a | 6s | HIGH | serum demo, spread, spill | S6 |
| C92 | Serum demo min-10: dries on top (AMBER, SHARED plate) | PLATE | n/a | 8s | HIGH | serum demo, dries, residue | S6, S7 |
| C93 | Serum demo hour-8: on the pillowcase | CHAR | THIN | 6s | MED | pillow stain, wake up | S6 |
| C94 | Serum demo: almost none reaches follicle (SHARED plate) | PLATE | n/a | 4s | HIGH | none reaches, gap, follicle | S6, S7 |
| C95 | Multiply by every serum you've bought (SHARED) | CHAR | THIN | 6s | HIGH | multiply, every serum, crowd | S6, S7 |
| C96 | "Your life and a laundry problem" (stained pillowcases) | CHAR | THIN | 6s | MED | laundry problem, stains | S6 |
| C97 | "Now watch": gold needle opens a channel (SHARED plate) | PLATE | n/a | 4s | HIGH | now watch, needle, channel | S6 |
| C98 | "It goes down": micro-infusion, BLUE serum descends (SHARED) | PLATE | n/a | 8s | HIGH | goes down, blue, micro-infusion | S6, S7 |
| C99 | Closer: "wrong direction, not wrong ingredients" (GOLD) | CHAR | FULL | 4s | MED | wrong direction, closer, gold | S6 |

Identity frames: THIN = approved S1 Flow-1 frame (or C67 for the S3 arc); FULL (concept 45/46) = the
approved @ROBLUX turnaround.
Note: the box-corrected regen of A31n is on disk as `A31nn` (NovaMane box). Rename it over A31n once the
old NovaInfuse render is retired. The old THIN S6 closer is on disk as `Dx` (superseded by C99) — delete.

### Letter A — Hair · skeleton (ALPHA + Novamane skeleton)
| ID | Beat / purpose | Lane | Hair | Len | Reuse | Keywords | Used in |
|---|---|---|---|---|---|---|---|
| A10 | Thin establishing / day-1 (THIN identity ref) | CHAR | THIN | 4s | MED | establishing, thin identity | ALPHA S3 |
| A11 | Shedding clump in shower | CHAR | THIN-WET | 6s | HIGH | shedding, clump, shower | ALPHA S2 |
| A12 | Mirror inspection, widening part / see-through | CHAR | THIN | 8s | MED | mirror, widening part, see-through | ALPHA S2 |
| A13 | Defeat, slumped in pile of empties | CHAR | THIN | 6s | LOW | defeat, empties pile | ALPHA S2 |
| A14 | "here's the problem" direct-address pivot | CHAR | THIN | 4s | MED | direct address, pivot, deadpan | ALPHA S2 |
| A15n | Day-1 skeptical inspect of GOLD needles (Novamane) | CHAR | THIN | 6s | MED | inspect, gold needles, day one | Nova-S2 |
| A16 | Offense-no-defense realization (thin) — ⚠️ FILE MISSING (not on disk) | CHAR | THIN | 8s | MISSING | offense no defense, thin | ALPHA S1 |
| A18 | "magic happens" hype lean-in | CHAR | THIN | 4s | MED | hype, lean-in | ALPHA S3 |
| A19 | Throws competitor bottles at lens (transition) | CHAR | THIN | 4s | MED | throw, dismiss, transition | ALPHA S3 |
| A20 | Needle macro vs paper edge (ALPHA, half-mm) | PLATE | n/a | 4s | HIGH | needle macro, scale | ALPHA S3, S1 |
| A20n | GOLD needle vs paper scale (macro, SHARED plate) | PLATE | n/a | 4s | HIGH | gold needle, scale, macro | Nova-S2, S3 |
| A21 | Science: micro-channels open, actives descend (ALPHA) | PLATE | n/a | 6s | HIGH | channels open, absorption | ALPHA S3, S2, S1 |
| A21n | GOLD micro-channels, blue serum to follicle (SHARED plate) | PLATE | n/a | 8s | HIGH | gold channels, feed, absorption | Nova-S2, S3 |
| A22 | Science: actives feed follicle, channel closes | PLATE | n/a | 4s | HIGH | follicle feed, close | ALPHA S3, S2, S1 |
| A23 | Science: topical sits on surface, never reaches | PLATE | n/a | 6s | HIGH | topical fails, surface | ALPHA S2, S1 |
| A24 | Science: barrier — generic bounces, product through (ALPHA green) | PLATE | n/a | 6s | MED | barrier, blocked vs through | ALPHA S3 |
| A24n | Barrier: generic bounces, BLUE NovaMane through (SHARED plate) | PLATE | n/a | 6s | HIGH | barrier, blue, wall, through | Nova-S4, S7 |
| A30 | Product intro: holds @PRODUCT + box (thin) | PROD | THIN | 4s | HIGH | product intro, thin reveal | ALPHA S2, S1 |
| A31 | Product hero: @PRODUCT + @ALPHA box reveal | PROD | FULL | 8s | HIGH | product hero, device + supply | ALPHA S3, S1 |
| A31n | Product hero "power of novomine" (GOLD) | PROD | FULL | 4s | MED | product hero, gold, novomine | Nova-S2 |
| A32 | Ingredient plate: botanicals around bottle (ALPHA) | PLATE | n/a | 4s | HIGH | ingredients, botanical | ALPHA S3, S1 |
| A32n | 18 actives + GOLD needles plate (Novamane) | PLATE | n/a | 4s | MED | 18 actives, gold, formula | Nova-S2 |
| A33 | Guarantee / badge plate (product + box) | PROD | n/a | 4s | HIGH | guarantee, badge | ALPHA S3, S2, S1 |
| A35 | Offense/defense cocky one-two stance (full) | CHAR | FULL | 6s | MED | offense defense, cocky | ALPHA S3 |
| A35n | Offense/defense one-two, THIN + GOLD applicator (Novamane) | CHAR | THIN | 4s | MED | offense defense, gold, thin | Nova-S4 |
| A36 | Stamp dome to scalp, painless (ALPHA) | CHAR | THIN | 6s | HIGH | stamp, apply, press scalp | ALPHA S3, S2 |
| A36n | Application (GOLD, bedroom side-profile, Novamane) | PROD | THIN | 4s | MED | apply, gold, side profile | Nova-S2 |
| A40 | Month-1 patient, "not much change" | CHAR | THIN | 6s | HIGH | month1, no change yet | ALPHA S2, S1; Nova-S2 |
| A41 | Month-3 baby hairs at hairline (EARLY ref) | CHAR | EARLY | 6s | HIGH | month3, baby hairs, early | ALPHA S2, S1; Nova-S2 |
| A42 | Day-30 selfie by window (Day-30 ref) | CHAR | EARLY | 4s | MED | day30, early, phone | ALPHA S3 |
| A43 | Day-60 mirror, fuller / less see-through | CHAR | MID | 6s | MED | day60, mid, hairline | ALPHA S3; Nova-S2 |
| A44 | Month-5/6 full, standing hero ("so thick") | CHAR | FULL | 6s | HIGH | month6, full payoff, social | ALPHA S2, S1; Nova-S2 |
| A45 | Day-90 payoff on couch (FULL identity ref) | CHAR | FULL | 6s | HIGH | payoff, full, confident | ALPHA S3 |
| A46 | Closer: "youngest your hairline will ever be" (age callback) | CHAR | THIN | 6s | MED | closer, age callback, youngest | Nova-S4 |
| A47 | Reduced shedding relief (comb, few strands) | CHAR | THIN | 6s | MED | reduced shedding, relief, month2 | Nova-S2 |
| A48 | Smug "if only they knew" full flex | CHAR | FULL | 4s | MED | smug, flex, rookies | Nova-S2 |
| A50 | Waves off pill bottle, reassuring (ALPHA) | CHAR | FULL | 4s | HIGH | no pills, reassurance | ALPHA S3, S2 |
| A50n | No pills / no doctor (GOLD, Novamane) | CHAR | FULL | 4s | MED | no pills, gold, no doctor | Nova-S2 |
| A51 | Open-palm invite toward the link | CHAR | FULL | 6s | HIGH | links below, invite, soft CTA | ALPHA S3, S2, S1; Nova-S2 |
| A52 | Urgent lean-in CTA, direct point | CHAR | FULL | 6s | HIGH | urgent CTA, close | ALPHA S3, S2, S1; Nova-S2 |
| A53n | 180-day guarantee (GOLD, box, Novamane) | PROD | FULL | 8s | MED | guarantee, gold, box | Nova-S2 |
| A54n | 90 sec / no pills / no surgery ease (GOLD) | CHAR | FULL | 6s | MED | quick routine, no surgery, gold | Nova-S2 |
| A63 | Age 22: full hair + tiny crown spot, dismissive (skeleton) | CHAR | FULL+spot | 8s | MED | age22, thin spot, decline | Nova-S4 |
| A64 | Age 25: mild thinning, TikTok shampoo fails (skeleton) | CHAR | mild-thin | 8s | MED | age25, shampoo, decline | Nova-S4 |
| A65 | Age 28: oily, rosemary/pumpkin oil, still hoping (skeleton) | CHAR | mod-thin | 8s | MED | age28, oils, decline | Nova-S4 |
| A66 | Age 30: receding + hat, "hat guy" (skeleton) | CHAR | receding | 8s | MED | age30, hat, decline | Nova-S4 |
| A67 | Age 32: significant loss, resolve (skeleton THIN ref) | CHAR | THIN | 6s | MED | age32, resolve, decline | Nova-S4 |

### Letter B — Teeth · skeleton (Enamio)
Pending migration: the Enamio D-set was built but never logged. To be reconstructed from the transcript
into the teeth dictionary (enamel problem / remineralization plates / pouch+gum / restore payoff).

### Letter D — Teeth · roblox
Reserved (no clips yet).

### Appendix — one-offs (NOREUSE)
| ID | Beat | Lane | Hair | From |
|---|---|---|---|---|
| C-o1 | "none reach follicle" bridge (counting -> barrier) | CHAR | THIN | Novamane S1 |
| A-o1 | Skeptical inspect of applicator | CHAR | THIN | ALPHA S3 |
| A-o2 | Day-7 mirror, unimpressed shrug (near-match A40) | CHAR | THIN | ALPHA S3 |
| A-o3 | Bottle-1 wet hair, pleased then deflates | CHAR | THIN-WET | ALPHA S2 |
| A-o4 | Sarcastic expensive bottle, store aisle | CHAR | THIN | ALPHA S2 |
| A-o5 | "you need to realize" educational turn — ⚠️ FILE MISSING (near-match A14) | CHAR | THIN | ALPHA S1 |

---

## Crosswalk (old ID -> new ID)
Old scheme keyed clips by which script made them (A=ALPHA S3, B=ALPHA S2, C=ALPHA S1). Hooks not logged.
```
A1  -> (hook, not logged; identity role -> A10)   A2  -> A10   A3  -> A-o1
A4  -> A20   A5  -> A36   A6  -> A-o2   A7a -> A21   A7b -> A22   A8  -> A18
A9a -> A19   A9b -> A24   A10 -> A42   A11 -> A43   A12 -> A45   A13 -> A31
A14 -> A32   A15 -> A35   A16 -> A50   A17a-> A33   A17b-> A51   A18 -> A52
B1  -> (hook, not logged)   B2  -> A-o3   B3  -> A11   B4  -> A-o4   B5  -> A12
B7  -> A13   B8  -> A14   B9  -> A23   B10 -> A30   B14 -> A40   B15 -> A41   B16 -> A44
C1  -> (hook, not logged)   C2  -> A-o5   C10 -> A16   C17 -> A46
```

## Quick-pick lists
**Hair science plates (SHARED across lines):** A20 (needle macro), A21/A22 (channels/feed), A23/C23
(topical fails), A24 (barrier). GOLD plates: A20n (gold needle scale), A21n (gold channels feed), A24n
(blue barrier). Serum-demo plates (SHARED): C90 (min-1 surface), C92 (min-10 dries), C94 (none reaches),
C97 ("now watch" channel opens), C98 ("it goes down"). Serum color: amber = generic fail, blue = NovaMane.
**Hair product/ingredient:** A30/C30/C30g (intro), A31/A31n (hero), A32/A32n/C32a/C32b (ingredients),
A33/C53/C53g (guarantee), C36/C36g/A36n (apply, pose-locked @APPLYPOSE).
**Hair timeline/payoff:** A40 (month1), A41 (month3 EARLY), A42 (day30), A43 (day60), A44/A45 (full),
A47 (reduced shedding), A48 (smug flex).
**Closers:** A50/C50/C50g/A50n (no pills), A54n (quick routine), A51/C51/C51g (links), A52/C52/C52g
(urgent CTA), A46 (full CTA payoff).
**Counting format (roblox):** C60 (1), C61 (3), C62 (6).
**Age-decline arc:** roblox C63 (22) → C64 (25) → C65 (28) → C66 (30 hat) → C67 (32); skeleton A63 → A67.
**Finasteride/DHT set (roblox):** C81 (banana), C82 (label), C83 (not normal), C84 (Rx trap), C85 (chart
forever), C86 (hair fall), C87 (try else), C88 (manhood closer), C89 (snake oils).
**Serum-demo set (roblox):** C90-C99 (see dictionary); character beats C93 (pillow), C95 (multiply), C96
(laundry), C99 (wrong-direction closer).

## Adding new clips
Append a row to the matching Letter section using the topic dictionary; put hooks nowhere (never logged)
and one-off jokes in the Appendix. Product-showing Novamane clips take `-n` (skeleton) / `-g` (gold
roblox); no-character plates are shared across lines. Bump a reuse tag to HIGH once a clip reuses cleanly
in 2+ ads. Keep the quick-pick lists in sync.

_Last updated: 2026-09-11. Scheme: topic x render + fixed concept (four letters only: A/B/C/D). Logged:
Novamane S1 (C), S2 (A, -n gold), S3 (C, -g gold + age-decline), S4 (A skeleton: age arc A63-67, A35n,
A46, A24n blue barrier), finasteride (C81-89), serum-demo S6 (C90-99), minoxidil S7 (C75-77). Reserved,
NOT built: graveyard S5 (C70-74). Pending: Enamio (B), their-health folds into A. Cleanup on disk:
A31nn (box-fixed A31n) and Dx (old THIN S6 closer, superseded by C99)._
