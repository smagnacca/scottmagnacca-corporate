---
name: video_integration_project
description: Video integration scaffolding for hero background and CLA Framework card overlays — test phase complete, awaiting final Gemini Veo renders
metadata:
  type: project
---

## Video Integration — Project Status

**Start Date:** 2026-08-08  
**Current Phase:** Integration Complete + 50% Videos Generated  
**Branch:** `feature/video-integration-v1` (local commits only, not pushed to GitHub)  
**Latest Update:** CLA card video opacity optimized to 60% for better visibility

---

## What's Built ✅

### Hero Section (35% opacity background video)
- **Location:** `index.html` line 2947
- **Structure:** `<section id="hero">` with background video element positioned absolutely
- **Video:** `assets/video/hero-sales-ai.mp4` (test video 2.4 MB, will be replaced with final render)
- **Content:** "Your Story Will." headline sits on top at z-index: 10
- **Scrim:** Gradient overlay `linear-gradient(135deg, rgba(10, 22, 40, 0.6)...)` keeps text readable
- **CSS:** `.video-background { opacity: 0.35; object-fit: cover; }`
- **Behavior:** Auto-play on page load, muted, looping, responsive

### CLA Framework Cards (42% opacity hover overlays)
- **Location:** `index.html` lines 3260–3310
- **Structure:** Three cards (Curiosity, Lifelong Learning, Agility & Adaptability)
- **Videos:** 
  - `assets/video/cla-curiosity.mp4` (958 KB test video)
  - `assets/video/cla-learning.mp4` (2.5 MB test video)
  - `assets/video/cla-agility.mp4` (958 KB test video)
- **Z-Index Layering:**
  - Video at z-index: 1 (opacity: 0.42 on hover)
  - Scrim overlay at z-index: 2 (keeps text readable)
  - Card content (icon, title, text) at z-index: 3
- **Hover Behavior (desktop):** Video fades in smoothly (0.4s transition)
- **Tap Behavior (mobile):** Toggle play/pause via touch detection
- **CSS:** `.card:hover video { opacity: 0.42; transition: opacity 0.4s ease; }`

### Demo Page ✅
- **File:** `video-demo.html` (standalone, self-contained)
- **Purpose:** Visual proof of video scaffolding before full-site integration
- **Shows:** Hero 35% opacity background, three CLA cards with 42% opacity overlays on hover, gradient scrim effects, z-index layering
- **Status:** Working correctly with test videos

---

## Current Assets

```
assets/video/
├── hero-sales-ai.mp4        (2.4 MB) — Test/reference, ready to swap
├── cla-curiosity.mp4        (958 KB) — Test/reference, ready to swap
├── cla-learning.mp4         (2.5 MB) — Test/reference, ready to swap
└── cla-agility.mp4          (958 KB) — Test/reference, ready to swap
```

All videos are currently **visible and playing** with opacity/scrim effects applied.

---

## Visual Effects Applied

| Section | Video | Opacity | Scrim | Interaction |
|---------|-------|---------|-------|-------------|
| Hero | Background | 0.35 | Yes | Auto-play on load |
| CLA: Curiosity | Overlay | 0.42 | Yes | Hover→play (desktop), tap→toggle (mobile) |
| CLA: Learning | Overlay | 0.42 | Yes | Hover→play (desktop), tap→toggle (mobile) |
| CLA: Agility | Overlay | 0.42 | Yes | Hover→play (desktop), tap→toggle (mobile) |

---

## Remaining Work

### Phase 2: Final Video Generation & Swap
**Timeline:** User action — depends on Gemini Veo render time

1. **Generate Videos in Gemini Veo** (user action)
   - Prompts location: `prompts/SCOTTMAGNACCA-VIDEO-PROMPTS.md`
   - Total: 6 videos (1 hero + 1 playbook + 4 CLA framework micros)
   - Targets: ~300KB max per section video, ~120–150KB per micro
   - Expected: Seamless loop, no watermarks/overlays, native 16:9 aspect ratio

2. **Replace Test Videos** (Claude action)
   ```
   cp <final-hero> assets/video/hero-sales-ai.mp4
   cp <final-curiosity> assets/video/cla-curiosity.mp4
   cp <final-learning> assets/video/cla-learning.mp4
   cp <final-agility> assets/video/cla-agility.mp4
   ```

3. **Verify Locally** (Claude action)
   - Start dev server: `python3 -m http.server 8000`
   - Test loop seams: Watch 2–3 complete cycles of each video for smooth crossfade
   - Test hover effects: Desktop (mouseenter/mouseleave), mobile (tap-to-toggle)
   - Responsive check: Desktop (1280px), tablet (768px), mobile (375px)
   - Screenshot proof: Full-page, viewport-specific

4. **Deploy to GitHub** (user approval)
   - Squash/rebase local commits on `feature/video-integration-v1`
   - Push to GitHub
   - Create PR to main with screenshots and testing notes
   - Merge after approval

---

## Important Notes

- **No push to main yet** — All work is local on feature branch
- **Videos are muted + autoplay** — Browser autoplay policy requires both; add audio track separately if needed
- **Loop quality matters** — Gemini Veo should render seamless loops; if visible seams, re-render with ffmpeg crossfade recipe
- **File size limits** — If final videos exceed 300KB, compress via ffmpeg or re-render at lower bitrate
- **Opacity + scrim** — These settings are finalized and won't change; any video can be swapped in without CSS updates
- **Responsive scaling** — Videos maintain aspect ratio via `aspect-ratio: auto` and `object-fit: cover`

---

## Code Changes Summary

| File | Changes |
|------|---------|
| `index.html` | Added video CSS (lines 341–410), hero video element (line 2949), card video elements (3 cards), video control JavaScript (end of file) |
| `assets/video/` | New directory with 4 test videos (placeholder for final renders) |
| `video-demo.html` | New standalone demo page showing video effects in isolation |

**Local commits:** 1 commit (not pushed)
- Message: "Add video integration scaffolding: hero background + CLA Framework hover videos"

---

## How to Test Locally (Quick Checklist)

- [ ] Start server: `python3 -m http.server 8000` in repo root
- [ ] Open `http://localhost:8000/video-demo.html` to see effects in isolation
- [ ] Or open `http://localhost:8000/index.html` to see full-site integration
- [ ] Hover over CLA cards on desktop → video should fade in (0.4s)
- [ ] On mobile, tap cards → video plays/pauses
- [ ] Watch 2–3 video loops to verify smooth seams (no stuttering)
- [ ] Resize browser to tablet/mobile → videos scale responsively
- [ ] Take screenshots (desktop, tablet, mobile) before final push

---

## Next Action

**Waiting for:** User to generate final videos in Gemini Veo using prompts file  
**Then:** Swap test videos → verify locally → push to GitHub with approval

Status: 🟢 Ready for video swap phase
