# Pre-flight checklist (self-lint before you hit send)

Run this SILENTLY before emitting any **anchor**, **animation**, or **timeline**. It is not the final
render QC (`qc-deliver.md`, which runs after generation) — this catches the *authoring* drift that
otherwise comes back as a user correction. Every item below is a mistake that actually happened and had
to be fixed. Scan the relevant block, fix, then send.

**FORMAT RE-READ GATE (first thing, always).** Do NOT emit an anchor/animation format from memory. RE-OPEN
`anchor-format.md` (anchors) or `video-format.md` (animations) and copy from its verbatim template + worked
example — ESPECIALLY after a context compaction, which paraphrases the format and is the root cause of the
recurring "that's not even our prompt format" correction. Memory drifts; the file is the source of truth.

## MULTI-PROMPT LAYOUT — LOCKED (copy-paste hygiene, user-locked 2026-09-13)

When emitting MORE THAN ONE prompt (anchors or animations) in a message, use this EXACT layout so each is
clean to paste into Flow:
- **Label OUTSIDE the code block** — a bold heading line ABOVE each block, e.g. `**SLOT 1 · E80 ·
  @CHARACTER_THIN · THIN**` (add a short italic note if useful). NEVER put the slot/ID label, a banner, or
  a counter INSIDE the code block.
- **Code block = paste-ready text ONLY** — the fenced block contains exactly what goes into Flow and
  nothing else: `tags(reference)` → … → `OUTPUT…` (anchor) or `tags(reference)` → `@[ANCHOR]` → `prompt` →
  … (animation). No headers, no meta, no counters inside.
- **Divider between entries** — a horizontal rule (`────────────`) between consecutive prompts, OUTSIDE the
  blocks, for the eye only.
- Why: the label used to sit inside the block, so copying the block pasted the label too and the entries
  ran together. This keeps every copy target pure.

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
- [ ] **Slot-numbered, letter-correct** — `@SLOT#`, a real library letter A/B/C/D/E, NO scratch letter
      (no M, no borrowed D). (`broll-library.md`)
- [ ] **Full-bleed framing** — FULL-BLEED line present; NO "reserve / leave-empty a caption strip" wording
      (it paints a solid bar); border / margin / inset / letterbox in the negatives. (`anchor-format.md`)
- [ ] **New line / ID sanity** — if this is a NEW library line, it is FORMALIZED in `broll-library.md`
      (letter + dictionary + reserved block) BEFORE any file is named. Before assigning a number, CHECK the
      concept dictionary: same number = same concept within that line's namespace; a demographic-specific
      beat goes in its reserved block, a no-character science plate in the 20s. Never borrow a number that
      already means something else (this is how E26/E60/E70 collided).

## Before emitting ANIMATIONS
- [ ] **Re-opened `video-format.md`** and copied from its template + worked example — NOT from memory.
- [ ] **Full locked template, verbatim** — every section + the `=====` rules, never compressed. Output
      FEWER prompts rather than a shortened format. (`video-format.md`)
- [ ] **Lane chosen + written** — CHARACTER = big/snappy/exaggerated, eyes act (never "subtle"); PLATE =
      clean base for post GFX.
- [ ] **Clip length computed from the SRT**, nearest engine step ≥ the beat span, never defaulted to 4s;
      a correct set has a MIX of lengths.
- [ ] **CLIP DENSITY / VO match (client-locked 2026-09-14)** — one clip per DISTINCT script idea; the shot
      matches what the VO says at that moment. SPLIT any clip whose VO window covers 2+ ideas or runs over
      ~8s; NEVER "generate long and hold the tail" across a topic change (the stuck-frame retention killer
      the client flagged). Scan each clip's VO against its shot: if the shot would still be up when the
      topic changes, split it. (`video-format.md` → CLIP DENSITY)
- [ ] **HAIR STATE LOCK** every clip; **LABEL LOCK** on any product/text clip; **MUSTACHE LOCK** on every
      skeleton clip (mouth still, he never talks).
- [ ] **Slot number matches its timeline slot** (same number in anchor, animation, and timeline).
- [ ] **Reference = the beat's OWN anchor** (`@E62` / `@hook` / `@E44`), NOT the character/identity ref
      (`@CHARACTER_THIN`); consistent across the whole set. A morph also attaches the FULL end frame.
      (`video-format.md`)

## Before emitting a TIMELINE
- [ ] **Locked format** — header line + `| # | Clip | In-Out | VO (verbatim) | Hair | Do |` + Editing
      notes. **The PLAN / MAPOUT uses this SAME format** — never an ad-hoc "VO cues" / invented-column
      planning table. (`video-format.md`)
- [ ] **In-Out from the SRT** (2 decimals); **VO verbatim** (never paraphrased), cues joined with ` / `.
- [ ] **HAIR-STATE CONTINUITY scan** — read the Hair column top to bottom; flag any unearned flip. A
      CTA/closer built among the FULL payoff pulls must be FULL (no full→thin on the last shot).
- [ ] **Reuse flagged** — every `pull` named; near-matches flagged, not silently reused; `MISSING` clips
      never offered.
- [ ] **Build vs pull counted**, dependency notes (plates built in another script must exist first).
- [ ] **Client shots present** where the brief demanded them (e.g. banana gag, hair-fall).

## The 7 rules I keep breaking (memorise)
1. Hooks: fresh location, never a bathroom.
2. Hair state: never flip full→thin on the last shot.
3. Format: never compress the locked anchor/video template (and never improvise a substitute — re-read the
   locked module if unsure).
4. Numbering: slot number end-to-end; letters A/B/C/D/E only, never a scratch letter; FORMALIZE a new line
   before naming files, and check the concept dictionary before assigning a number.
5. Labels: `NovaMane` on every surface; serum blue, generic amber.
6. Skeleton: the exact mustache phrase, every time.
7. Framing: full-bleed, never reserve/leave-empty a caption strip (it paints a solid bar).
