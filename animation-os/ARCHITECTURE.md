# Animation OS — Architecture & Business Context

The living design record. This is the "why" behind the skill; `SKILL.md` is the "how".

## The pivot

The project moved away from photorealistic AI-avatar frame production toward a **repeatable, scalable
AI advertising machine** using viral animation formats (skeleton, x-ray, Roblox, 3D, cartoon, anime).

- **Old priority:** photorealism → identity → reference fidelity → motion realism.
- **New priority:** speed → repeatability → automation → cost efficiency → creative quality → sales.

Realism is no longer the goal unless a specific format calls for it. Cartoon/Roblox/skeleton formats do
not need photorealistic humans, which is exactly what makes them automation-friendly and cheap.

## The core principle

Do not think "make an AI video." Think "build a repeatable advertisement production system." Evaluate
every step by: how repetitive is it, can Claude handle it, can it be API/MCP-connected, can it be
batched, how cheaply/quickly can one ad (and variations) be produced, will the architecture support
other formats.

## Format-agnostic architecture

Separate the **creative format** from the **production pipeline**:

```
FORMAT (swappable): Skeleton · X-Ray · Roblox · Anime · 3D · Cartoon · …
PIPELINE (fixed):   Product → Research → Angle → Script → Storyboard → Character →
                    Image Prompts → Image Gen → Video Prompts → Video Gen → Edit → Ad
```

Only the format layer changes. This is the whole design: `SKILL.md` is the pipeline; `styles/` are the
formats; `modules/` are the creative libraries that keep each ad fresh.

## Business model

Find/adapt viral formats → produce initial ads quickly → give brands ~2 free sample ads → paid trial if
interested → raise quality once paid → automate the process → reuse across formats.
Early production optimizes for speed, volume, good-enough quality, strong hooks, clear product
integration, brand-safe messaging. Do not over-polish an unpaid sample.

## Model & tool strategy

Do not force one model. For cartoon/animated ads prioritize cost, speed, consistency, ease of
automation, then quality. Start cheap (Seedance, Kling, Omni Flash); escalate only when the cheap model
fails. Veo is not required for cartoon formats. Use whichever aggregator is easiest for the operator.

## Development roadmap (phases)

1. Understand the skeleton workflow · 2. **Test the Roblox hair-loss ad** · 3. Choose the easiest
image/video platform · 4. Complete ONE ad end to end · 5. Document every manual step · 6. Identify
bottlenecks · 7. Automate high-value bottlenecks · 8. Connect APIs/MCP · 9. Reusable per-format
automation · 10. Expand formats · 11. Prepare for high-volume Q4 production.

**Prove the manual workflow before automating.** First make one complete ad, then automate the
machinery (pipeline stages 5, 8–11). Target readiness: early September for Q4.

## Human-in-the-loop (never removed)

Automation removes repetitive labor, not creative judgment. Humans stay for: script claims, brand
safety, creative direction, product accuracy, final visual selection, QC, and deciding when an
AI concept is bad.

## Principles carried over (still valuable)

Reference consistency · asset consistency · product continuity · version control · minimal unnecessary
changes · QC · reusable assets and prompts · deterministic workflows · do not guess missing information
· do not overcomplicate production.

## Principles dropped for stylized ads

Photorealistic skin · realistic human anatomy · human motion realism · Veo-level realism — none are
imposed on skeleton/Roblox/cartoon formats.

## Change log

- **Animation OS (this build):** integrated Creator-OS orchestration + Skeleton Ads director into one
  format-agnostic ad machine; added Style Packs (bare-bones/x-ray/dressed skeleton, Roblox, anime +
  template), creative modules (angle, hook, motion grammar, storyboard, consistency, product truth-lock),
  Roblox Story mode, the reference-leads-text consistency system, strategic-anchor discipline,
  storyboard-first, product label lock, and the build-first-automate-later roadmap.
