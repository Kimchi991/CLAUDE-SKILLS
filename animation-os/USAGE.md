# Animation OS — How to Use This Skill

A step-by-step guide for the team. Animation OS turns a **product + script** into a short-form animated
**ad** (9:16, under ~60s), in any animation style, using one repeatable pipeline. This doc explains how
to run it start to finish, what you have to provide, and where the human decisions are.

If you only read one thing: **you drive, the skill directs.** It stops at gates and asks you to confirm
before spending generations. Never let it batch-run silently.

---

## 1. What it produces

The skill does NOT render images or video itself. It produces, in order:
1. A **script** (or adapts yours) in the swipe/ad voice.
2. A **timeline** mapping each voiceover line to a shot and a clip length.
3. **Anchor prompts** — copy-paste image prompts you run in ChatGPT or Google Flow to make the still
   "start frames."
4. **Animation prompts** — copy-paste image-to-video prompts you run in Omni Flash / Kling / Flow.
5. A **cut sheet** for assembling the clips against the voiceover in CapCut.

You do the generating and editing. The skill does the directing and the prompt-writing.

---

## 2. How to start it

- **Slash command:** `/animation-os` (once the skill is installed in your Claude).
- **Trigger phrases:** "make a skeleton ad", "roblox ad", "animation ad", "make an ad", or just paste a
  product page / script and say you want a video ad.

On boot it loads the safety filter (CONSTITUTION), then asks for your intake.

---

## 3. What you need to provide (intake)

Have these ready. Missing items are fine, the skill will tell you exactly what's missing.

| Input | Needed for | Notes |
|---|---|---|
| **Product** | everything | what you're selling |
| **Script** OR **SRT** | the timeline | see the SRT rule below |
| **Product photo** (`@PRODUCT`) | product shots | real label, composited in post |
| **Character** (`@CHARACTER`) | consistency | reuse if you already have one |
| **Style** | the look | skeleton / Roblox / etc, or let it recommend |

### The SRT rule (important)
**The AI cannot hear audio.** If you upload an mp3 voiceover, it can't read the timing from it. To get
real clip durations you must give it one of:
- an **SRT** file (best — has the exact start/end time of every line), or
- the **script text** (durations become estimates you fix in the edit).

**How to get an SRT fast:** in CapCut, drop your voiceover on the timeline → **Captions → Auto captions
→ Export SRT**. Paste that into the chat. (Or export timestamps from ElevenLabs where the VO was made.)

If you don't have an SRT yet, the skill will wait for it before setting the shot count and durations.

---

## 4. The pipeline (11 stages)

Stages marked ▲ are **human gates** — the skill stops and asks you.

```
1  Intake + Diagnose ▲      what you have, the audience, the mechanism, missing inputs
2  Angle + Hook ▲           the ad angle + the scroll-stopping hook
3  Script ▲                 written/adapted in the swipe voice
4  Review + Lock ▲          claim flags (health/money/results); you approve
5  Voice + Timing ▲         give the SRT; it becomes the ruler for shots + durations
6  Style Select ▲           pick the style pack (auto-recommend, you confirm)
7  Character + Hero ▲        ASK: is the character already made? reuse it, or build a sheet
8  Anchor Method ▲          ASK: storyboard (ChatGPT) or manual one-by-one anchors?
9  Anchor Images ▲          the still start-frame prompts (locked anchor format)
10 Video Clips              the image-to-video prompts (locked video format)
11 Assemble + QC + Deliver  cut to the SRT timeline, run the QC checklist, export
```

### Stage by stage, what happens

**1. Intake + Diagnose.** You give the product/script/refs. It works out the audience, the mechanism
(how the product works), and what's missing.

**2. Angle + Hook.** It picks the ad angle and a hook that stops the scroll in the first ~1.5s. The
first frame must be the most absurd/curious image of the whole ad, not a warm-up.

**3. Script.** It writes or adapts the script in the punchy ad voice. If you already have a locked
script, it uses yours, it won't rewrite it.

**4. Review + Lock (claims).** It flags regulated claims (health, money, results) for you to keep or
soften BEFORE anything is generated. This protects the ad account.

**5. Voice + Timing (the SRT).** You provide the SRT. It collapses the caption lines into **story beats**
(one idea = one shot). The number of beats = the number of anchors. Nothing is a fixed number, the SRT
decides. Each beat gets a clip length = the nearest Omni Flash step (4/6/8/10s) at or above the line's
length.

**6. Style Select.** It recommends a style pack and you confirm:
- health / internal-process → **x-ray skeleton** (shows what's happening inside the body)
- playful / meme → **roblox**
- wearable / identity → **dressed skeleton**
- default cinematic → **bare-bones skeleton**
The pack swap changes the entire look (for example, x-ray skeleton uses big expressive eyes; Roblox uses
small solid-black dot eyes).
> If you bring anchors/refs that already exist, it will STATE the style it sees and confirm it before
> generating, so it never puts the wrong style locks on your frames.

**7. Character + Hero.** It **asks first: "is the character already made?"**
- If YES → you attach it, it loads as `@CHARACTER`, and it skips building.
- If NO → it gives you a ChatGPT prompt to build a character sheet (turnaround + expressions), which
  becomes `@CHARACTER`.
The character must exist before the storyboard/anchors, because the board is drawn from it.

**8. Anchor Method.** It **asks: storyboard or manual?**
- **(A) Storyboard (ChatGPT)** — it gives you one prompt that draws all shots as a labeled grid, so you
  can eyeball the whole ad. You generate the board, then it extracts each panel into a clean frame one
  by one. Best for stylized looks (Roblox) and for planning.
- **(B) Manual one-by-one** — it skips the board and writes each anchor prompt directly, one at a time.
  Faster when the plan is already clear.

**9. Anchor Images.** The still "start frames," each in the **locked anchor format** (same full
structure every shot). You generate them. Rule: `A1` establishes the world; attach the approved `A1` as
`@WORLD` on later shots so the location stays identical.

**10. Video Clips.** For each approved still, it writes the **locked video (animation) format** prompt.
You run it in Omni Flash (or Kling/Flow) at the length from the timeline, generate long, and trim the
tail to the voiceover line in the edit.

**11. Assemble + QC + Deliver.** You drop the voiceover in CapCut first (it's the ruler), snap each clip
to its SRT window, trim the tail, then run the QC checklist. Captions, music, and SFX are your CapCut
craft, the skill does not prescribe them.

---

## 5. The two anchor methods in detail

### Method A — Storyboard through ChatGPT (recommended for Roblox)
1. The skill gives you a **storyboard prompt**: a portrait sheet of vertical 9:16 panels, one per beat,
   all using your attached character + product, with the milestone (e.g. balding → restored) baked in.
2. Set ChatGPT's image output to **portrait**, attach the character + product, run it.
3. Send the grid back. The skill checks consistency.
4. Say this exact line to start pulling the frames:
   > **alright lets use that storyboard, give me the exact frames one by one lets start with anchor 1
   > remove the number indicating the anchor number**
5. It fires one extraction prompt per panel (ChatGPT recreates that panel as a clean full 9:16 frame,
   grid number removed). Say **next** between each.

### Method B — Manual one-by-one
1. No board. The skill writes **A1** directly in the locked anchor format and you generate it.
2. Approve, then say **next**. It writes **A2** (attach A1 as `@WORLD`), and so on to the end.

Both end with the same result: a clean 9:16 start frame per beat, ready to animate.

---

## 6. The reference markers

You'll see these `@` tags in prompts. They mean "attach this image."
- `@CHARACTER` — the character sheet (identity lock). On every character shot.
- `@WORLD` — the approved first anchor (usually A1). Locks the room/background on later shots.
- `@PRODUCT` — the real product photo. On product shots only.
- `@A1`, `@A5`… — a specific approved anchor, used as the start frame for its animation.

---

## 7. The locked formats (do not shorten them)

Two prompt templates are locked. They are always produced in FULL, never compressed, even when making
many at once.
- **Anchor format** (`modules/anchor-format.md`) — the still-image prompt: identity lock, story-state,
  pose, world, camera, lighting, anchor requirements, negatives.
- **Video format** (`modules/video-format.md`) — the image-to-video prompt: `tags(reference)` → `@anchor`
  → `prompt` → Preserve line → "feel alive / actual personality" lines → **PRIMARY PERFORMANCE** →
  **CAMERA PERFORMANCE**.

If a prompt ever comes back stubby or merged, that's wrong, ask for the full format.

---

## 8. Timing and durations (why clips are the length they are)

- Clip length = the nearest Omni Flash step (**4 / 6 / 8 / 10s**) that is **≥ the voiceover line's
  length** from the SRT.
- Short punchy line → 4s. A longer product/mechanism beat → 6/8s. The spectacle (the transformation)
  gets the most room.
- The AI never makes a clip longer than its voiceover line (that just adds dead air). If you want longer,
  more cinematic beats, write fewer/longer lines in the script, that's a VO-pacing choice.
- Always generate long and **trim the tail** to the line in CapCut, never the intro (the action is
  front-loaded).

---

## 9. Product truth + safety (non-negotiable)

- **Real product:** use the real photo (`@PRODUCT`) and composite the real label in post. Models garble
  small text, so we keep the label area clean in the generation and add the real label in the edit.
- **Competitors:** always plain and unbranded, no logos, blank price tags.
- **Claims:** health/money/results claims get flagged at Stage 4. Keep them defensible before you lock.
- **Anti-hallucination:** keep text, screens, and UI out of the generated frame; reveal them in the
  edit.

---

## 10. QC checklist (before you deliver)

Run this on every shot (`modules/qc-deliver.md`):
- Identity holds every shot (face, eyes, build, materials).
- Style on-model (no style flip).
- The milestone state (hair/gut/teeth) matches the beat and reads in order.
- Real label composited, competitors unbranded, price tags blank.
- Each clip trimmed to its SRT window, total matches the VO.
- The hook stops the scroll with sound off.

### Client revisions
Client feedback is not a full rebuild. Turn each note into a **lock edit** (e.g. "brighter background" →
update the WORLD lock; "vary the poses" → update the pose rule), then regenerate ONLY the affected shots.
Approved shots that the note doesn't touch stay as they are.

---

## 11. A worked example (teeth-whitening, Roblox)

1. Intake: whitening pen, Roblox style, young audience.
2. Angle/Hook: "villain → main character"; open on a blocky guy's stained grin while people recoil.
3. Script: 9 punchy lines.
4. Claims: flag "lifts years of stains / in about a week."
5. SRT: paste it. It collapses to 9 beats; teeth milestone = yellow → white; durations 4–8s.
6. Style: Roblox (glossy plastic, small black-dot eyes, white marble bathroom).
7. Character: "already made" → load `@CHARACTER`.
8. Method: Storyboard (ChatGPT).
9. Run the storyboard prompt → say the extraction line → pull 9 frames.
10. Animate each frame with the locked video prompt at its length.
11. Cut to the SRT, run QC, deliver.

---

## 12. Common mistakes to avoid

- **Uploading only audio and expecting exact timing.** Give an SRT.
- **Letting it assume the style** on frames you already made. Confirm the style.
- **Accepting a compressed prompt.** The locked formats are always full.
- **Hardcoding "9 shots" or "everything 4s."** Counts and durations come from the SRT.
- **Baking real label text into the generation.** Composite it in post.
- **Building the storyboard before the character exists.** Character first.

---

## 13. File map (for maintainers)

- `SKILL.md` — the pipeline + non-negotiables (loaded first).
- `CONSTITUTION.md` — safety + platform-risk filter.
- `styles/` — one file per look (xray-skeleton, roblox, etc). Swap one in at Stage 6.
- `modules/` — the rule-books loaded per stage: `voice-timing`, `angle-library`, `hook-library`,
  `storyboard`, `consistency`, `anchor-format`, `video-format`, `motion-grammar`, `engagement`,
  `product-truth-lock`, `flow-agent`, `qc-deliver`.

Update this doc whenever the workflow changes.
