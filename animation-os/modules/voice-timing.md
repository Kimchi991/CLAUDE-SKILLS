# Voice + Timing (Stage 5) — the SRT is the ruler

The whole visual plan hangs on real timing. This stage gets it and turns it into the map that every
later stage reads. Do this BEFORE storyboard, anchor count, or any duration.

## HARD REALITY — you cannot hear audio

Claude cannot transcribe or time an audio/video file. An uploaded mp3 is opaque. So never estimate
timestamps from a "normal speaking pace" — that guess is wrong and it poisons every duration downstream.
Instead, require one of:

1. **An SRT / caption file** (best — gives real per-line in/out times), or
2. **The pasted script text** (gives the words; durations stay estimates, trued in the edit).

How to get the SRT with no extra tools:
- **CapCut → Captions → Auto captions → Export SRT** (from the user's VO mp3), or
- **ElevenLabs** word/character timestamps (where the VO was generated).

If neither exists yet, **wait for it**. Do not build the board or counts on a guess.

## Turn the SRT into the beat map

The SRT is caption lines, not shots. Collapse it into **story beats**:

- **Merge** consecutive lines that describe the same idea and the same on-screen state into one beat.
- **Split** only when the visual STATE changes (new location, new prop, new hair stage, new emotion).
- The number of beats = the anchor count. **Never a fixed number** (see SKILL non-negotiable #9).

For each beat record: **beat in/out (from the SRT) · VO line(s) · visual state · the anchor it earns.**

## From beats to durations

- Each beat's length = its SRT out minus in.
- Clip length = the engine's nearest step **≥ the beat length** (Omni Flash 4/6/8/10s), generate long,
  trim the tail to the SRT window in the edit. A short line gets a short clip; that is correct.
- This map is the assembly timeline: `beat # · start · end · anchor · clip length · trim`.

## Hand-off

The beat map feeds:
- `storyboard.md` (how many panels, in order),
- `anchor-format.md` (one anchor per beat, with its CURRENT STATE),
- `video-format.md` (each clip's duration),
- `qc-deliver.md` (clips get trimmed back to these windows at QC).
