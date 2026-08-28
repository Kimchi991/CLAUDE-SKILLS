# Engagement

The retention layer. A clean ad that nobody watches past second two is a failure. This module makes the
ad *hold* — it governs the hook, captions, cut rhythm, audio, and hook-variant testing. Apply it across
stages 2, 7, 10, and 11; it never overrides the Constitution or the claim flags.

## 1. The hook (first 1–1.5 seconds) — the only second that matters

Most viewers decide to keep watching in the first ~1.5s. Engineer the opening for that, not for story.

- **The first frame is a stop-scroll, not a warm-up.** It must show the most absurd / curious / high-
  contrast image of the whole ad — the payoff of the visual joke, not the setup. A1 already does this
  (goofy roller); protect it. If the opening frame is calm or generic, the ad is dead on arrival.
- **Open a loop in the first line.** The VO's first sentence should raise a question the viewer needs
  answered ("this is how you look using those…"). Visual + VO both create the itch.
- **No logos, no slow intros, no brand bumper.** Nothing that reads as "an ad" in the first 2s.
- **Motion or a face in frame one.** A living, expressive character beats an empty environment.

## 2. Kinetic captions (added in the edit — never baked into the generation)

Word-by-word captions are the single biggest retention lever on short-form. Non-negotiable on every ad.

- **Style:** one or two words at a time, dead-center or lower-third, **bold sans, heavy black stroke /
  drop shadow**, high contrast, large. Pop/scale each word on its syllable (karaoke style).
- **Sync to the VO word**, not the sentence. The emphasized word gets a bigger pop or a color hit.
- **Match the VO exactly.** Captions are the same words as the voiceover — no paraphrasing.
- **Never generate captions inside the video model** (it garbles text); always burn them in CapCut.
- Keep them clear of the safe-area (TikTok UI covers the bottom ~15% and right edge).

## 3. Retention cut-rhythm (the edit)

- **A visual change every ~1.5–2.5s.** New anchor, punch-zoom, caption hit, or SFX — the frame must
  keep changing or attention drops. This is why anchors get animated *and* cut, not held.
- **Punch-zoom on the emphasized VO word** (a quick scale bump), synced to the beat.
- **Hard cuts by default**; save a whoosh/match-cut for the x-ray transition and the product reveal.
- **Speed up into the CTA.** Fastest cuts in the last 20% for urgency; slow a beat on the payoff frame.
- **Front-load energy.** The biggest visual move belongs in the first shot, not saved for the end.

## 4. Audio + SFX layer (assembled separately, never in the clip)

Clips are generated silent. Sound is built in the edit and it is half the engagement.

- **VO** carries the words (ElevenLabs), mixed on top.
- **A bed track** — low, trend-aware, non-distracting — under the whole ad. Swap to whatever audio is
  trending on the target platform that week; keep it legally usable for ads.
- **Punch SFX on the beats:** a whoosh into the x-ray insert, a soft ding/shine on the Keeps reveal, a
  record-scratch or thud on the store-brand "but be careful," a pop on each caption if it fits.
- **Never** put dialogue, music, or SFX inside the generation prompt — audio is a separate layer.
- Duck the bed track under the VO so every word is intelligible.

## 5. Hook-variant testing (the biggest free multiplier)

The same ad lives or dies on its opening. Always produce **3 different hooks** for the same body.

- Vary **the first 1–2s only**: a different opening visual gag, or a different opening VO line, over the
  identical rest of the ad. (E.g. the roller gag vs. a cold "your hairline is losing a war" vs. a
  direct "stop wasting money on this.")
- Ship all three; keep the winner by retention/CTR; reuse that hook shape next time.
- This is cheaper than making three ads and outperforms polishing one.

## Engagement QC (before delivery)

- Does the **first frame** stop the scroll on its own, with sound off?
- Is there a **visual change at least every ~2.5s**?
- Are **captions** present, synced to the VO word, inside the safe-area?
- Is the **CTA** unmistakable in the last 3s (spoken + on-screen + faster cuts)?
- Do you have **3 hook variants** to test?
- Sound **off** test: does the ad still make sense from visuals + captions alone?
