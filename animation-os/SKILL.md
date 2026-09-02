---
name: animation-os
description: >
  Flexible AI ad-production system that turns any product, offer, or script into a short-form animated
  advertisement in any viral animation style (bare-bones skeleton, x-ray skeleton, dressed skeleton,
  Roblox, anime, cartoon mascot, 3D claymation, and more). One repeatable pipeline, swappable Style
  Packs. Use whenever the user wants to make an animated product ad, a skeleton ad, a Roblox ad, a
  "what happens if you" progression ad, turn a product link/brief/script into a video ad, storyboard an
  ad, generate character or product image prompts, or write video prompts synced to a voiceover. Trigger
  on "skeleton ad", "roblox ad", "animation ad", "make an ad", "animation os", a pasted product page or
  script, or any faceless animated advertisement task. Strictly 9:16 short-form by default.
---

# Animation OS

A format-agnostic machine for producing short-form animated **advertisements**. It turns
`Product + Angle + Style → Script → Visual Plan → Images → Video Clips → Ad`, as fast, cheap, and
repeatably as possible. The pipeline never changes; the **creative format snaps in** as a Style Pack.

**What this is NOT:** a single-style workflow, and not an autonomous agent. It is a production
playbook. State lives in the conversation and the files the user brings (script, VO, references), not
in the model.

**Default output:** 9:16 vertical, short-form (under ~60s), one voiceover carrying the ad, animated
characters as B-roll.

---

## BOOT (run on load, in order)

```
1. Read  CONSTITUTION.md   → the safety + platform-risk + brand-safe filter (always in force)
2. Read  the request       → product? script? references? which style?
3. STYLE-CONFIRM GATE ▲     → if existing anchors/refs are brought in, STATE the detected style and
                              CONFIRM it before generating. A wrong style poisons every prompt after it.
4. Route through THE PIPELINE, stopping at each creative gate for human review
```

Do not skip step 1. Health, beauty, supplement, money, and results claims get flagged before lock.

---

## THE PIPELINE (same for every style)

Stop at the **creative gates** (marked ▲). Never batch-run silently.

```
1  INTAKE + DIAGNOSE ▲   product/script/refs → audience, mechanism, missing inputs
2  ANGLE + HOOK ▲         pick the angle (modules/angle-library) + hook (modules/hook-library)
3  SCRIPT + HOOK ▲        write/adapt in the swipe voice; open a loop; earn the product with a turn
4  REVIEW + LOCK ▲        human checks claims + platform-risk; approve; VO becomes source of truth
5  VOICE + TIMING ▲       get the VO SRT/script FIRST (you cannot hear audio, modules/voice-timing);
                        collapse SRT lines → beats → the timeline. The SRT sets beat count + durations.
6  STYLE SELECT ▲         pick a Style Pack (styles/) — auto-recommend, human confirm
7  CHARACTER BIBLE + HERO ▲ lock the DNA; build a CHARACTER SHEET (ChatGPT) and load it as the
                        `@CHARACTER` asset (reference leads, text supports). MUST exist before storyboard —
                        the board is drawn FROM the attached sheet (modules/consistency)
8  STORYBOARD ▲           Claude BUILDS the GPT storyboard prompt (attaching @CHARACTER) → human runs it
                        in GPT → grid back → Claude reviews + splits into STRATEGIC ANCHORS (modules/storyboard)
9  ANCHOR IMAGES ▲        PICK A ROUTE, then anchor-format.md + @CHARACTER (identity locked) + @PRODUCT
                        + per-beat CURRENT STATE (hair/beard/expression vary):
                        9a FLOW    = Google Flow batch/chain (modules/flow-agent): FAST batch to explore,
                                     DETAILED chain to deliver (world-lock)
                        9b CHATGPT = recreate each storyboard panel as a full 9:16 frame, number removed
                                     (modules/storyboard Step 4) — better for stylized looks like Roblox
10 VIDEO CLIPS            SEPARATE step: animate each anchor with the LOCKED video format
                        (modules/video-format, emit in FULL) + motion-grammar; Omni Flash 4/6/8/10s taken
                        from the SRT beat; B-roll only; chain last frame for continuity
11 ASSEMBLE + QC + DELIVER assemble to the SRT timeline; run the QC checklist (modules/qc-deliver);
                        client feedback re-enters via the revision loop at stage 6/9; export; log to automate
        ↓
(VARIANT: re-run STYLE SELECT only, to produce a second sample in a different look)
```

Stages 5 and 9 to 11 are pure machinery, identical every time — the parts worth automating later.
The ▲ stages stay human.

---

## MODE ROUTING

| The user wants… | Mode |
|---|---|
| An animated product **ad** (default) | **Ad mode** — run the pipeline above, characters are B-roll, VO carries |
| A viral Roblox **story** (rich vs poor, funny, mystery...) | **Story mode** — see `roblox-story.md`, characters SPEAK, 6 to 8 scenes |
| Just a storyboard / concept board | run stages 1 to 7, hand off the board |
| Just image or video prompts (has a script/style already) | jump to stage 8 or 10 with the locked style |

Ad mode and Story mode are different: in **ads nobody speaks** (VO carries); in **stories characters
speak** (no narrator). Never mix the two rule sets.

---

## STYLE PACKS (the flexible layer — `styles/`)

Each pack is self-contained: a Character Bible template, a render/style lock line, its own negatives,
and default world notes. Snap one into stage 6 and the whole pipeline adapts. Load exactly one per ad.
Add a new style by copying `styles/_TEMPLATE.md` — never hardcode a style into the pipeline.

Shipped packs: `bare-bones-skeleton` · `xray-skeleton` · `dressed-skeleton` · `roblox` · `anime`
(plus the template for cartoon mascot, claymation, LEGO, felt, pixel, and anything new).

Auto-recommend the strongest style for the product, then let the user confirm or override:
health/body/internal-process → **x-ray skeleton**; wearable/identity → **dressed skeleton**;
playful/meme → **roblox**; cooking/lifestyle/process → **anime**; default cinematic → **bare-bones**.

---

## CREATIVE MODULES (`modules/`) — load the relevant one per stage

| Module | Use at | Gives |
|---|---|---|
| `angle-library.md` | stage 2 | proven ad angles; never default to one arc |
| `voice-timing.md` | stage 5 | you can't hear audio: require an SRT; collapse lines → beats → durations |
| `hook-library.md` | stage 2 to 3 | scroll-stopping hook templates |
| `motion-grammar.md` | stage 10 | cheap camera/motion moves that read expensive |
| `engagement.md` | stages 2, 8, 10, 11 | retention layer: hook, kinetic captions, cut-rhythm, audio/SFX, 3 hook variants |
| `storyboard.md` | stage 8 | grid-first (attach @CHARACTER), then split into strategic anchors |
| `anchor-format.md` | stage 9 | the locked anchor-prompt template; same structure every shot; anti-hallucination (hide text/screens) |
| `video-format.md` | stage 10 | the locked animation-prompt template; emit in FULL verbatim, never compress |
| `consistency.md` | stages 7 to 9 | reference + DNA + current-state; identity lock vs story variable |
| `flow-agent.md` | stages 8 to 10 | the Google Flow batch engine (all anchors + video in one session) |
| `product-truth-lock.md` | any product shot | real-brand label lock, composite the label in post |
| `qc-deliver.md` | stage 11 | final per-shot QC checklist + the client-revision loop (feedback → lock edits) |

---

## THE NON-NEGOTIABLES (every style)

1. **Reference leads, text supports.** The hero image anchors continuity; the DNA text reinforces it.
   Never rely on text alone, never rely on the image alone.
2. **Story-driven anchors.** Favor rich visual storytelling: give every distinct story beat its own
   anchor and use as many as the script earns (no fixed count, the Flow agent batches up to 100). Cut
   only true near-duplicates; motion carries the fast cuts within a shot. Detailed, story-advancing
   shots beat fewer generic ones.
3. **Product truth-lock.** Real brand = real reference image + verbatim label text. Never invent
   packaging, logos, or label text. Composite a real label in post when the model garbles it.
4. **Platform-risk review before lock.** Flag regulated claims (health, money, results) for the human.
5. **B-roll characters in ads.** Nobody speaks; the VO carries. Characters speak only in Story mode.
   Every clip still carries an expressive, engaging performance (`modules/engagement.md`,
   `modules/motion-grammar.md`) — and the first 1–1.5s must stop the scroll. The skill owns the
   timeline (which clip covers which VO line + durations); caption styling, audio, and SFX are the
   user's CapCut edit.
6. **Cheap model first.** Start with the fast, cheap generator; only escalate when it actually fails.
7. **Human in the loop.** Automation removes repetitive labor, never creative judgment.
8. **Locked formats are emitted in FULL, verbatim.** The anchor prompt (`anchor-format.md`) and the
   animation prompt (`video-format.md`) always use their complete locked template with every section,
   whether producing one or many. NEVER compress, merge sentences, drop sections, or abbreviate "to save
   space" — a stubby version is a reject. Output fewer at a time instead of shortening the format. This
   is the #1 recurring failure; guard it every time.
9. **Nothing is hardcoded to a count.** Anchor/panel/clip counts and clip durations come from the SRT
   beat mapping, never a fixed number. Get the SRT first, map beats, then build.

---

## BUILD-FIRST, AUTOMATE-LATER

Prove the manual workflow by making one complete ad. Then log every manual step (stage 11), find the
bottlenecks, and automate the machinery (stages 5, 8 to 11) via API/MCP. Do not build automation before
the manual flow works. See `ARCHITECTURE.md` for the business context and roadmap.
