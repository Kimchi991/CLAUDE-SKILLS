# B-ROLL LIBRARY — ALPHA INFUSE (and future jobs)

A running inventory of every distinct B-roll clip we have generated, so future scripts can REUSE
existing clips instead of rebuilding them.

## The reuse rule (client-approved)
- Reuse is allowed, but ONLY when it is a **direct concept match** — same beat, same lane, same hair
  state, nothing forced. Never jam a clip in just to save work.
- **Always tell the user** when a reuse is available, and name the clip.
- Near-matches are NOT reused silently. Mention them separately as "build fresh, but a similar clip
  exists (ID)" and let the user decide.
- B-rolls are silent, so a clip can sit under a different VO line as long as the on-screen action,
  lane, and hair state fit.

## How to use this file (every new script)
1. Build the beat/timeline from the SRT as normal.
2. For each beat, scan this inventory for a DIRECT match (compare: lane, hair state, and what the
   clip shows / its keywords).
3. In the timeline, mark matched beats `REUSE <ID>` and only BUILD the rest.
4. After generating anything new, ADD it to the inventory below (see "Adding new clips").

## Legend
- **Origin:** which script first generated the clip. `A` = Script 3 (needles / "90 days"),
  `B` = Script 2 (shampoo bottles), `C` = Script 1 (minoxidil / Turkey). New products get new
  letters (D, E, ...).
- **Lane:** CHAR = character performance · PLATE = science/mechanism plate · PROD = product/packaging.
- **Hair:** THIN (receding/patchy) · THIN-WET · EARLY (month 3 / baby hairs) · MID (day 60) ·
  FULL (payoff) · n/a (no character hair in frame).
- **Reuse:** HIGH = generic, reuses cleanly across ads · MED = reusable if context + hair state match
  · LOW = one-off, tied to a specific hook/joke/montage.

## Reference-frame rule (identity lock)
Use ONE character reference per anchor (the approved frame), never two competing character refs
(stacking causes gaunt/zombie drift). Golden identity frames:
- **@A1** = THIN/receding character (the thin-hair identity lock, used across all thin beats).
- **@A10** = Day-30 hair styling reference (EARLY).
- **@A12 / @B16** = FULL-hair character (the payoff identity lock).
Product refs (@PRODUCT applicator, @ALPHA box) are different subjects and are safe to attach
alongside a character ref.

---

## INVENTORY — distinct generated clips

### Origin A — Script 3 (needles / "90 days")
| ID | Beat / purpose | Lane | Hair | Len | Reuse | Keywords | Used in |
|---|---|---|---|---|---|---|---|
| A1 | Hook: stamps @PRODUCT dome to scalp at hairline, deadpan to lens | CHAR | THIN | 4s | MED | hook, stamp, applicator, thin identity anchor | S3 |
| A2 | Day-1 establishing, wide bathroom, apprehensive | CHAR | THIN | 4s | LOW | establishing, wide, day1 | S3 |
| A3 | Inspects applicator up close, skeptical squint | CHAR | THIN | 4s | LOW | inspect, applicator, skeptical | S3 |
| A4 | Macro: half-mm needles vs paper edge (scale) | PLATE | n/a | 4s | HIGH | needle macro, half-millimeter, scale | S3, S1(C6) |
| A5 | Stamps dome to crown, calm/relieved ("20 sec") | CHAR | THIN | 6s | HIGH | stamp, apply, press scalp, painless | S3, S2(B13) |
| A6 | Day-7 mirror, over-shoulder, unimpressed shrug | CHAR | THIN | 4s | MED | mirror, shrug, thin, no change | S3 |
| A7a | Science: needle opens micro-channels, actives descend | PLATE | n/a | 6s | HIGH | channels open, actives, absorption, mechanism | S3, S2(B11), S1(C7) |
| A7b | Science: actives feed follicle, channel closes | PLATE | n/a | 4s | HIGH | follicle, feed root, deposition, close | S3, S2(B12), S1(C8) |
| A8 | "Magic happens" lean-in, eyes pop wide | CHAR | THIN | 4s | MED | excited, lean-in, hype | S3 |
| A9a | Throws generic bottles AT lens (transition) | CHAR | THIN | 4s | MED | throw, dismiss competitors, transition | S3 |
| A9b | Science: barrier — generic bounces, ALPHA goes through | PLATE | n/a | 6s | MED | barrier, blocked vs through, contrast (SPOILS if ALPHA not yet introduced) | S3 |
| A10 | Day-30 selfie by window, part less visible | CHAR | EARLY | 4s | MED | day30, early, phone, part; Day-30 hair ref | S3 |
| A11 | Day-60 mirror, hand-sweep, fuller hairline | CHAR | MID | 6s | MED | day60, mid, hairline, mirror | S3 |
| A12 | Day-90 payoff on couch, confident | CHAR | FULL | 6s | HIGH | payoff, full, confident; FULL identity ref | S3 |
| A13 | Product hero: presents @PRODUCT + @ALPHA box | PROD | FULL | 8s | HIGH | product hero, device + serum supply, reveal | S3, S1(C14) |
| A14 | Ingredient plate: botanicals around bottle | PLATE | n/a | 4s | HIGH | ingredients, ginseng/rosemary/etc, botanical | S3, S1(C9) |
| A15 | Offense/defense cocky one-two stance | CHAR | FULL | 6s | MED | offense defense, two-in-one, cocky (FULL) | S3 |
| A16 | Waves off plain pill bottle, reassuring | CHAR | FULL | 4s | HIGH | no pills, reassurance, closer | S3, S2(B18) |
| A17a | Product + box plate, "120-day" badge space | PROD | n/a | 4s | HIGH | guarantee, 120-day, badge, product plate | S3, S2(B19), S1(C15) |
| A17b | Open-palm invite toward the link | CHAR | FULL | 6s | HIGH | links below, invite, soft CTA | S3, S2(B20), S1(C16) |
| A18 | Urgent lean-in CTA, direct point (closes loop) | CHAR | FULL | 6s | HIGH | urgent CTA, take action, close | S3, S2(B21), S1(C18) |

### Origin B — Script 2 (shampoo bottles)
| ID | Beat / purpose | Lane | Hair | Len | Reuse | Keywords | Used in |
|---|---|---|---|---|---|---|---|
| B1 | Hook: holds plain thickening-shampoo bottle, deadpan | CHAR | THIN | 4s | LOW | hook, shampoo bottle, "how many bottles" | S2 |
| B2 | Bottle 1: hand in WET hair, pleased then deflates | CHAR | THIN-WET | 6s | LOW | wet hair, fresh-shower, deflate | S2 |
| B3 | Bottle 3: staring at a clump of shed hair, shower | CHAR | THIN-WET | 6s | LOW | shedding, clump, shower, dismay | S2 |
| B4 | Bottle 7: sarcastic, holds fancy bottle, store aisle | CHAR | THIN | 6s | LOW | expensive bottle, sarcastic, aisle | S2 |
| B5 | Bottle 11: vanity mirror, part widening + see-through | CHAR | THIN | 8s | MED | mirror inspection, widening part, see-through | S2 |
| B7 | Bottle 20: slumped in a pile of empty bottles, defeated | CHAR | THIN | 6s | LOW | defeat, empties pile, $300 wasted | S2 |
| B8 | Pivot: "there isn't a number," direct-to-lens deadpan | CHAR | THIN | 4s | MED | direct address, pivot, deadpan, thin | S2 |
| B9 | Science: shampoo/topical sits on surface, never reaches follicle | PLATE | n/a | 6s | HIGH | topical fails, surface, rinse off, blocked | S2, S1(C3+C4) |
| B10 | Product intro: holds up @PRODUCT + box (still thin) | CHAR/PROD | THIN | 4s | HIGH | product intro, "the thing that does," thin reveal | S2, S1(C5) |
| B14 | Month 1: patient, "not much change," bedroom | CHAR | THIN | 6s | HIGH | month1, patient, no change yet | S2, S1(C11) |
| B15 | Month 3: baby hairs at hairline, hopeful | CHAR | EARLY | 6s | HIGH | month3, baby hairs, early regrowth | S2, S1(C12) |
| B16 | Month 5: full hair, standing hero, confident | CHAR | FULL | 6s | HIGH | month5, full payoff; FULL identity ref | S2, S1(C13) |

### Origin C — Script 1 (minoxidil / Turkey)
| ID | Beat / purpose | Lane | Hair | Len | Reuse | Keywords | Used in |
|---|---|---|---|---|---|---|---|
| C1 | Hook: holds minoxidil + shampoo, dead-serious warning | CHAR | THIN | 8s | LOW | hook, minoxidil, "before you spend," warning | S1 |
| C2 | "You need to realize," empty-handed direct-address turn | CHAR | THIN | 6s | MED | direct address, educational turn, thin | S1 |
| C10 | Offense/defense + no pills, dynamic stance (THIN) | CHAR | THIN | 8s | MED | offense defense + reassurance, thin version | S1 |
| C17 | CTA comparison: holds stamp, dismisses Turkey route, points down | CHAR/PROD | FULL | 8s | MED | CTA, Turkey vs stamp, comparison, full | S1 |

---

## Quick pick lists (fast lookup)

**Science/mechanism plates (HIGH):** A4 (needle macro), A7a (channels open), A7b (follicle feed),
B9 (topical fails on surface), A9b (barrier contrast — only after ALPHA is introduced).

**Product / packaging:** A13 (product hero, FULL), B10 (product intro, THIN), A17a (guarantee plate),
A14 (ingredient plate).

**Month timeline:** B14 (Month 1 THIN), B15 (Month 3 EARLY), A10 (Day-30 EARLY), A11 (Day-60 MID),
A12 (Day-90 FULL), B16 (Month-5 FULL).

**Closer (HIGH, FULL):** A16 (no pills), A17a (guarantee), A17b (links invite), A18 (urgent CTA).

**Application:** A5 (stamp to scalp, THIN).

---

## Adding new clips
When new clips are generated, append a row to the matching Origin section (or a new Origin letter for
a new product). Fill: ID, beat/purpose, lane, hair, length, reuse tag, keywords, and the scripts it is
used in. Bump reuse tag to HIGH once a clip has been reused cleanly in 2+ ads. Keep the quick-pick
lists in sync.

_Last updated: 2026-09-09. Covers ALPHA INFUSE Scripts 1-3._
