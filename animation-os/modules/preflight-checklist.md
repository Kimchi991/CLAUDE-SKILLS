# Pre-flight checklist (self-lint before you hit send)

Run this SILENTLY before emitting any **anchor**, **animation**, or **timeline**. It is not the final
render QC (`qc-deliver.md`, which runs after generation) — this catches the *authoring* drift that
otherwise comes back as a user correction. Every item below is a mistake that actually happened and had
to be fixed. Scan the relevant block, fix, then send.

## Before emitting ANCHORS
- [ ] **Hook location is fresh + thematic** — never the default bathroom. Each hook gets a distinct,
      script-matched setting (car mirror, gym, pharmacy, barbershop). (`broll-library.md` hook rule)
- [ ] **ONE character reference** per anchor (never stack two character refs → drift). Product/world refs
      attach alongside fine.
- [ ] **Reference-drag guard** — when referencing an approved frame, say "take identity/pose ONLY, DROP
      the reference's background, set a fresh location."
- [ ] **Deep focus** stated, no background blur/bokeh (standing rule).
- [ ] **Skeleton only:** mustache/upper-lip lock present AND the verified phrase
      `no making of mustache, do not anything on the characters face`.
- [ ] **Product shown:** spell the exact label (`NovaMane` + `micro-infusion system` + green
      power-button), box reads `NovaMane` (never NovaInfuse), LABEL LOCK present. (`product-truth-lock.md`)
- [ ] **Needle colour matches the script VO** (clear vs 24k gold); gold clips carry `-n`/`-g`.
- [ ] **Competitor/other props unbranded** (no logos, no readable labels).
- [ ] **Serum colour right:** NovaMane = light blue; a failing/generic serum = amber (never blue).
- [ ] **Roblox:** framed tight/close-up (stiff rig), motion kept containable.
- [ ] **START-FRAME rule:** settled pose, no motion/blur/particles/captions.
- [ ] **Slot-numbered, letter-correct** — `@SLOT#`, real A/B/C/D letter, NO scratch letter (no M, no
      borrowed D). (`broll-library.md`)

## Before emitting ANIMATIONS
- [ ] **Full locked template, verbatim** — every section + the `=====` rules, never compressed. Output
      FEWER prompts rather than a shortened format. (`video-format.md`)
- [ ] **Lane chosen + written** — CHARACTER = big/snappy/exaggerated, eyes act (never "subtle"); PLATE =
      clean base for post GFX.
- [ ] **Clip length computed from the SRT**, nearest engine step ≥ the beat span, never defaulted to 4s;
      a correct set has a MIX of lengths.
- [ ] **HAIR STATE LOCK** every clip; **LABEL LOCK** on any product/text clip; **MUSTACHE LOCK** on every
      skeleton clip (mouth still, he never talks).
- [ ] **Slot number matches its timeline slot** (same number in anchor, animation, and timeline).

## Before emitting a TIMELINE
- [ ] **Locked format** — header line + `| # | Clip | In-Out | VO (verbatim) | Hair | Do |` + Editing
      notes. (`video-format.md`)
- [ ] **In-Out from the SRT** (2 decimals); **VO verbatim** (never paraphrased), cues joined with ` / `.
- [ ] **HAIR-STATE CONTINUITY scan** — read the Hair column top to bottom; flag any unearned flip. A
      CTA/closer built among the FULL payoff pulls must be FULL (no full→thin on the last shot).
- [ ] **Reuse flagged** — every `pull` named; near-matches flagged, not silently reused; `MISSING` clips
      never offered.
- [ ] **Build vs pull counted**, dependency notes (plates built in another script must exist first).
- [ ] **Client shots present** where the brief demanded them (e.g. banana gag, hair-fall).

## The 6 rules I keep breaking (memorise)
1. Hooks: fresh location, never a bathroom.
2. Hair state: never flip full→thin on the last shot.
3. Format: never compress the locked anchor/video template.
4. Numbering: slot number end-to-end; only A/B/C/D letters, never a scratch letter.
5. Labels: `NovaMane` on every surface; serum blue, generic amber.
6. Skeleton: the exact mustache phrase, every time.
