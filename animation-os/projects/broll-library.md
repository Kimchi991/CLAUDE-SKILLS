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

## Naming convention (generation -> rename)
Anchors are generated in Google Flow named `1..N` per video, then RENAMED to the library ID after
approval so they drop into the inventory. Every script build ships a rename map (`Flow 1 -> C60`, ...).
The hook (Flow `1`) is the exception: hooks are never renamed and never logged (always fresh).

## Letter = topic x render style
| Letter | Topic | Render style |
|---|---|---|
| A | Hair | Skeleton (@SKELETON porcelain) |
| B | Teeth | Skeleton |
| C | Hair | Roblox (@ROBLUX) |
| D | Teeth | Roblox |

New combinations get new letters. `A`+`C` share the HAIR dictionary; `B`+`D` share the TEETH dictionary.

## Number = fixed concept (strict within a topic)
- The number is a fixed concept within its topic, so `A21`==`C21` concept (same beat, different render).
- **Per-style copies:** each render style keeps its own clip, so a Roblox video uses `C21`, not `A21`,
  even for a no-character plate.
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
47-49 (reserve)
50 no-pills reassurance
51 links-below invite (soft CTA)
52 urgent CTA / take action
53 guarantee / 180-day window CTA
59 legal / disclaimer end-card (branded, baked text)
60 count: 1 product, not enough (counting-format problem)
61 count: 3 products stacked
62 count: 6 / trend-chasing, still nothing
```

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
  orange sneakers, beaded bracelet on right wrist. THIN ref = the approved S1 Flow-1 frame (receding).
  FULL ref = the original approved turnaround (full hair) = the payoff/identity for concept 45/46.
- `@PRODUCT` (Novamane applicator) = clear glass mini bottle, BLUE serum, clear textured micro-needle
  DOME cap of CLEAR/transparent micro-needles (NOT gold, NOT metal); label "NOVAMANE" + "micro-infusion
  system" with a small green circular power-button mark. Always spell the label in-prompt to stop
  hallucination.
- `@NOVAINFUSE` (Novamane box) = white box, lid reads "WARNING: Things are about to get hairy" over
  small hair-follicle icons, holds blue vials + the applicator.
- `@APPLYPOSE` = the standard applying-pose reference for concept 36 (locks the same apply pose across
  all Novamane videos).

**Hair - Skeleton line (@SKELETON):**
- `@SKELETON` = glossy pale-pink PORCELAIN hard-shell face, kintsugi GOLD cracks, lower face exposed
  skull with FULL teeth (no lips), large hazel/amber eyes + brows, ash-blonde/brown hair w/ faded sides,
  short beard JAW/CHIN ONLY, exposed spine at collar, plain grey crew tee, pale-pink skeletal porcelain
  arms/hands. THIN ref = A10; EARLY = A41/A42; FULL = A45.
- **@SKELETON UPPER-LIP / MUSTACHE LOCK (recurring failure — apply on EVERY @SKELETON anchor and
  animation).** i2v drifts to the "bearded face = mustache" prior and grows a mustache mid-clip. Beat it
  with the physical framing, not a soft negative: the lower face is an EXPOSED PORCELAIN SKULL, so there
  is NO fleshy upper lip and NO philtrum skin — the zone between the nose and the top teeth is smooth
  hard porcelain/bone that CANNOT grow hair. The beard is ONLY on the jaw/chin below the mouth. In the
  anchor, state that zone is bare porcelain and add "no mustache/hair/stubble between nose and teeth" to
  negatives. In the animation, add a per-frame MUSTACHE LOCK naming the zone, hold it identical every
  frame, and keep the mouth/upper-lip region STILL (he never talks). This is the FEATURE/IDENTITY DRIFT
  LOCK from `modules/video-format.md`, made concrete for this character.
- `@PRODUCT` (ALPHA applicator), `@ALPHA` (ALPHA box) for the ALPHA line; `@SPRAY` (their-health amber
  spray). Product truth-locks per `product-truth-lock.md`.

**Teeth - Skeleton line:** `@ENAMIO` (pouch), `@GUM` (tan chicle pieces).

---

## INVENTORY

### Letter C — Novamane (hair · roblox)
| ID | Beat / purpose | Lane | Hair | Len | Reuse | Keywords | Used in |
|---|---|---|---|---|---|---|---|
| C23 | Scalp barrier: topical beads on surface, never reaches follicle | PLATE | n/a | 8s | HIGH | barrier, topical fails, surface, blocked | S1 |
| C30 | Product intro: lifts @PRODUCT, hopeful pivot | PROD | THIN | 4s | HIGH | product intro, novamane reveal, hope | S1 |
| C32a | 18-actives overview: bottle + orbit of ingredients | PLATE | n/a | 4s | HIGH | 18 actives, formula, orbit plate | S1 |
| C32b | Hero actives: copper-peptide chain, adenosine, caffeine, pea sprout | PLATE | n/a | 8s | HIGH | hero ingredients, copper peptide chain, macro | S1 |
| C35 | Offense/defense cocky stance, applicator forward | CHAR | THIN | 8s | MED | offense defense, cocky, floor failures + box tower | S1 |
| C36 | Application: dome to hairline, nightly routine (pose @APPLYPOSE) | PROD | THIN | 4s | HIGH | apply, stamp, before bed, pose-locked | S1 |
| C50 | No prescription/no pills, waves off pill bottle | CHAR | THIN | 6s | HIGH | no pills, reassurance, topical only | S1 |
| C51 | Links-below soft CTA, casual lean, chin-nod down | CHAR | FULL | 4s | HIGH | links below, soft CTA, casual | S1 |
| C52 | Urgent CTA lean-in + point to lens (closes loop) | CHAR | FULL | 6s | HIGH | urgent CTA, point, take action | S1 |
| C53 | 180-day guarantee, presents @PRODUCT + @NOVAINFUSE, badge space | PROD | FULL | 8s | HIGH | guarantee, 180-day, badge, box stack | S1 |
| C60 | Count 1: single serum, unimpressed, filler | CHAR | THIN | 8s | MED | counting, 1 product, minoxidil doubt | S1 |
| C61 | Count 3: juggling 3 products, fake "boss" confidence | CHAR | THIN | 8s | MED | counting, 3 products, stacked routine | S1 |
| C62 | Count 6: slumped, trendy peptides, still nothing | CHAR | THIN | 8s | MED | counting, 6 products, defeat, feed | S1 |

Identity frames: THIN = approved S1 Flow-1 frame; FULL (concept 45/46) = the approved @ROBLUX turnaround.

### Letter A — Hair · skeleton (migrated from ALPHA scripts; see crosswalk)
| ID | Beat / purpose | Lane | Hair | Len | Reuse | Keywords | Used in |
|---|---|---|---|---|---|---|---|
| A10 | Thin establishing / day-1 (THIN identity ref) | CHAR | THIN | 4s | MED | establishing, thin identity | ALPHA S3 |
| A11 | Shedding clump in shower | CHAR | THIN-WET | 6s | HIGH | shedding, clump, shower | ALPHA S2 |
| A12 | Mirror inspection, widening part / see-through | CHAR | THIN | 8s | MED | mirror, widening part, see-through | ALPHA S2 |
| A13 | Defeat, slumped in pile of empties | CHAR | THIN | 6s | LOW | defeat, empties pile | ALPHA S2 |
| A14 | "here's the problem" direct-address pivot | CHAR | THIN | 4s | MED | direct address, pivot, deadpan | ALPHA S2 |
| A16 | Offense-no-defense realization (thin) | CHAR | THIN | 8s | MED | offense no defense, thin | ALPHA S1 |
| A18 | "magic happens" hype lean-in | CHAR | THIN | 4s | MED | hype, lean-in | ALPHA S3 |
| A19 | Throws competitor bottles at lens (transition) | CHAR | THIN | 4s | MED | throw, dismiss, transition | ALPHA S3 |
| A20 | Needle macro vs paper edge (scale) | PLATE | n/a | 4s | HIGH | needle macro, half-mm, scale | ALPHA S3, S1 |
| A21 | Science: micro-channels open, actives descend | PLATE | n/a | 6s | HIGH | channels open, actives, absorption | ALPHA S3, S2, S1 |
| A22 | Science: actives feed follicle, channel closes | PLATE | n/a | 4s | HIGH | follicle feed, deposition, close | ALPHA S3, S2, S1 |
| A23 | Science: topical sits on surface, never reaches | PLATE | n/a | 6s | HIGH | topical fails, surface, rinse off | ALPHA S2, S1 |
| A24 | Science: barrier — generic bounces, ALPHA through | PLATE | n/a | 6s | MED | barrier, blocked vs through (spoils pre-intro) | ALPHA S3 |
| A30 | Product intro: holds @PRODUCT + box (still thin) | PROD | THIN | 4s | HIGH | product intro, thin reveal | ALPHA S2, S1 |
| A31 | Product hero: @PRODUCT + @ALPHA box reveal | PROD | FULL | 8s | HIGH | product hero, device + supply | ALPHA S3, S1 |
| A32 | Ingredient plate: botanicals around bottle | PLATE | n/a | 4s | HIGH | ingredients, botanical | ALPHA S3, S1 |
| A33 | Guarantee / badge plate (product + box) | PROD | n/a | 4s | HIGH | guarantee, 120-day, badge | ALPHA S3, S2, S1 |
| A35 | Offense/defense cocky one-two stance (full) | CHAR | FULL | 6s | MED | offense defense, two-in-one, cocky | ALPHA S3 |
| A36 | Stamp dome to scalp, painless application | CHAR | THIN | 6s | HIGH | stamp, apply, press scalp | ALPHA S3, S2 |
| A40 | Month-1 patient, "not much change" | CHAR | THIN | 6s | HIGH | month1, no change yet | ALPHA S2, S1 |
| A41 | Month-3 baby hairs at hairline (EARLY ref) | CHAR | EARLY | 6s | HIGH | month3, baby hairs, early | ALPHA S2, S1 |
| A42 | Day-30 selfie by window (Day-30 ref) | CHAR | EARLY | 4s | MED | day30, early, phone, part | ALPHA S3 |
| A43 | Day-60 mirror, fuller hairline | CHAR | MID | 6s | MED | day60, mid, hairline | ALPHA S3 |
| A44 | Month-5 full, standing hero | CHAR | FULL | 6s | HIGH | month5, full payoff | ALPHA S2, S1 |
| A45 | Day-90 payoff on couch (FULL identity ref) | CHAR | FULL | 6s | HIGH | payoff, full, confident | ALPHA S3 |
| A46 | CTA comparison, dismisses Turkey route, points down | CHAR | FULL | 8s | MED | CTA, comparison, full | ALPHA S1 |
| A50 | Waves off pill bottle, reassuring | CHAR | FULL | 4s | HIGH | no pills, reassurance | ALPHA S3, S2 |
| A51 | Open-palm invite toward the link | CHAR | FULL | 6s | HIGH | links below, invite, soft CTA | ALPHA S3, S2, S1 |
| A52 | Urgent lean-in CTA, direct point | CHAR | FULL | 6s | HIGH | urgent CTA, close | ALPHA S3, S2, S1 |

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
| A-o5 | "you need to realize" educational turn (near-match A14) | CHAR | THIN | ALPHA S1 |

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
**Hair science plates:** A20 (needle macro), A21 (channels open), A22 (follicle feed), A23/C23 (topical
fails), A24 (barrier). Roblox copies: C23.
**Hair product/ingredient:** A30/C30 (intro), A31 (hero), A32/C32a/C32b (ingredients), A33/C53 (guarantee),
C36 (apply, pose-locked).
**Hair timeline/payoff:** A40 (month1), A41 (month3 EARLY), A42 (day30), A43 (day60), A44/A45 (full).
**Closers:** A50/C50 (no pills), A51/C51 (links), A52/C52 (urgent CTA), A46 (full CTA payoff).
**Counting format (roblox):** C60 (1), C61 (3), C62 (6).

## Adding new clips
Append a row to the matching Letter section using the topic dictionary; put hooks nowhere (never logged)
and one-off jokes in the Appendix. Bump a reuse tag to HIGH once a clip reuses cleanly in 2+ ads. Keep
the quick-pick lists in sync.

_Last updated: 2026-09-10. Scheme: topic x render + fixed concept. Logged: Novamane S1 (Letter C),
ALPHA S1-3 migrated (Letter A). Pending: Enamio (B), their-health folds into A._
