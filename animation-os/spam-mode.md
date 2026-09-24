# Spam Mode

A **sub-mode** of Ad mode, not a replacement. High-volume, short-form (20 to 30s) before/after
testimonial cuts, built for POSTING VOLUME (the NovaMane "most videos this month" bonus), not
per-video polish. Ruthless reuse of an existing character + B-roll library; minimal fresh builds per
video. Ad mode makes one flagship; Spam mode makes many, fast.

**It never changes the main workflow.** It adds a fast lane on top and INHERITS every Ad-mode lock
(NovaMane label lock, disclaimer on any reveal, deep focus, 9:16, one-marker identity lock, the
locked anchor/animation formats, mouth-at-rest B-roll). It cannot override a rule the flagship
pipeline depends on. Activates only when the user says "spam"; otherwise you are in Ad mode as always.

## The key difference from the flagship (learned from the client's BaF examples, 2026-09-18)
Spam videos are **trending sound + burned-in captions + visual storytelling. NO spoken voiceover.**
The example audio tracks were a trending song (Piano Man), not an ElevenLabs narration. So the
flagship's script -> ElevenLabs -> SRT -> cut-to-VO chain does NOT run here by default. There is no
VO, so there is no accent bug and no ElevenLabs step. The client's accent/music feedback was about
the flagship VO ads, a separate format.

- **Default lane = SILENT.** Trending audio bed + typed caption text per beat + B-roll cut to the
  song's energy. The story is told by the visuals and the on-screen text, not a narrator.
- **Optional lane = VO.** Only if the user explicitly wants a narrated spam cut: then, and only then,
  fall back to the flagship script -> ElevenLabs -> SRT -> timeline chain. Not the default.

## When to use
- The KPI is throughput (many posts) not one perfect ad.
- A proven character + B-roll library already exists to pull from (E-line real-person today; any
  letter later).
- The client wants short before/after / testimonial cuts to spam.
NOT for a product with no library yet (use Ad mode first to build one), NOT for the 60 to 90s
flagship scripts (those stay Ad mode).

## Two production lanes (pick one per batch, never mix inside a video)
- **AI creator (default).** Reuse the E-line character + existing B-roll. Fresh-build only the hook
  plus at most one story beat; everything else PULLS. Mouth-at-rest B-roll per the standing E-line
  rule (true lip-synced talking-head AI is a separate upgrade, not in this pipeline yet). Cheapest at
  scale.
- **Client-filmed.** The client records himself once; that real footage is the A-roll. We only CUT +
  CAPTION + drop in product B-roll pulled from the library. No i2v on the talking head. $0 footage,
  fastest turnaround, but it is the client on camera. Reuse the same takes across many cuts by
  swapping the hook + captions.

## The spam workflow (default silent lane)
1. **Pick a trending sound.** The audio bed sets the length and the cut rhythm (e.g. Piano Man in the
   client's example). Note its BPM / energy beats; cuts land on them.
2. **Storyboard the before/after story in beats**, cut to the song, ~5 to 7 beats over 20 to 30s.
3. **Write the caption text per beat** (the testimonial, TYPED on screen, punchy, one thought per
   card). This is the story, since there is no VO.
4. **Map beats to clips.** Most rows are PULL (grab an existing E-line clip); one or two are BUILD.
5. **Build only the fresh bits.** Anchor + animation prompts for the fresh HOOK (always) and maybe
   one new body beat, in the locked formats. User renders in Flow.
6. **Bundle.** Rename to library IDs, drop play-order clips in the spam folder.
7. **CapCut:** cut to the sound, burn word-by-word captions, add the disclaimer IF a reveal is shown,
   export. No music bed added on top (the trending sound IS the audio); no VO.

## The spam spine (~20 to 30s, 5 to 7 beats)
Reverse-engineered from the client's BaF examples. Same skeleton every video; only the hook + caption
text + sound change:
1. HOOK 0 to 3s — emotional cold open, FRESH every video, NEVER logged. Default caption format = the
   "thank-you letter" confession ("to the nurse who noticed my part before I said anything..."). Stops
   the scroll on emotion, not product.
2. PROBLEM PROOF 3 to 8s — shedding evidence (hand clump, comb pull, shower drain). PULL.
3. MECHANISM 8 to 16s — why it works + box/vials reveal (copper peptides, adenosine). PULL. NovaMane
   LABEL LOCK applies.
4. PAYOFF 16 to 22s — restored state / life-back moment. PULL, or a FRESH reveal. A reveal is a
   regulated claim: E45-style morph + `Dramatization. Results vary. With consistent use.`, never a
   hard thin->full cut.
5. CTA 22 to 27s — product hero, "linked below". PULL.
One idea per beat still holds (no holding a frame across a topic change).

## Reuse vs build (the ratio is the only thing that changes from Ad mode)
Not reuse-ONLY. Build where the eye lands, pull where it does not:
- **HOOK = always freshly built**, every video, never logged. This is what makes each post look like a
  different video instead of the same one 20 times.
- **Body (shedding, mechanism, product, CTA) = mostly PULLED** connective tissue.
- **Sprinkle a fresh body beat every few videos** so the batch does not feel cloned; that new clip
  then joins the library for later pulls. This is [[broll-build-forward]] dialed to volume, not
  switched off. Twenty near-identical cuts lose the bonus, they do not win it.

## Hook bank (the spam engine)
Volume comes from swapping the HOOK + caption text + trending sound over the SAME body spine. Rotate
angles so posts do not look identical:
- Thank-you letter ("to the [person] who told me...")
- POV text message / screenshot confession
- "Nobody warned me about month 4"
- "Things I wish I knew before GLP-1 / before the baby"
- Stitch / duet reaction to a shedding clip
- Literal before -> after reveal (regulated: carries the disclaimer)
Each hook is a fresh Flow build, tagged to the batch, never renamed into the library.

## Library hygiene
- Spam PULLS from the canonical library; it does not bloat it. Hooks are never logged (standing rule).
- A genuinely reusable NEW spam beat gets a normal library number; a one-off gets an E-o appendix ID,
  flagged NOREUSE.
- Bundles live in their own folder: `WORK_ERIC\NOW\<batch>\spam\NN - <angle>`, files `NN_ID.mp4` in
  play order (same bundle rule as Ad mode).

## Captions (the real bottleneck at volume)
The examples use burned-in word-by-word captions. That caption-burn is a manual CapCut step and is the
true throughput limit, not the B-roll. First thing to automate for spam (batch auto-caption + a saved
template).

## QC-lite (the spam bar)
Full `qc-deliver.md` is overkill at volume. Per cut check only: 9:16 + 30fps, first 1.5s hook lands,
identity not drifted, NovaMane label legible, caption sync, trending sound present, disclaimer present
IF a reveal is shown, file named. Skip the deep per-shot pass.

## Client notes (locked 2026-09-18)
- Spam cuts use a **trending sound**, not a music bed we add and not a VO. No ElevenLabs, no accent
  risk.
- The accent/no-music feedback belongs to the FLAGSHIP VO ads, not here. If a narrated spam cut is
  ever requested (optional VO lane), the accent fix is ElevenLabs Speech-to-Speech over the existing
  audio (preserves timing); API key stays LOCAL.

_Started 2026-09-18 from the NovaMane volume-bonus brief. Default silent lane (trending sound +
captions), VO optional. Two production lanes: AI-creator (E-line reuse) and client-filmed._
