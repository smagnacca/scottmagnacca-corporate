# Complete Asset Library Reference for ScottMagnacca.com

This document catalogs ALL available video and image assets you can use for scottmagnacca.com from two major projects.

---

## 🎬 VIDEO ASSETS

### 1. "Why Professional Help Matters" Project Videos
**Location:** `/Users/scottmagnacca/ClaudeProjects/Why Professional Help Matters_The Human Premium in the Age of AI website/assets/video/`  
**Status:** Already copied to `assets/video-library/` (see VIDEO-LIBRARY-CATALOG.md)

| Video | Size | Best For |
|-------|------|----------|
| `broll-advisor.mp4` | 1.2M | Team training, consultation scenarios |
| `broll-ai.mp4` | 437K | AI technology references |
| `broll-author.mp4` | 210K | Thought leadership, speaking |
| `broll-team.mp4` | 1.2M | Team collaboration, methodology |
| `broll-contact.mp4` | 162K | Connection, handshake moments |
| `cta-handshake.mp4` | 634K | Call-to-action, booking |

---

### 2. VIDEO-PRODUCTION-MASTER Project
**Location:** `/Users/scottmagnacca/ClaudeProjects/VIDEO-PRODUCTION-MASTER/`  
**Total Videos:** 505  
**Total Size:** ~11GB

#### High-Quality Segment Videos (for repurposing)
Located in `broll/` — Professional production quality, excellent for framework/methodology:
- `intro_opening.mp4` (44M) — Opening sequence, brand intro
- `segment_1_content.mp4` (38M) — Core content, concepts
- `segment_2_middle.mp4` (44M) — Middle narrative, development
- `segment_3_development.mp4` (47M) — Advanced concepts
- `segment_4_core.mp4` (36M) — Deep-dive, mastery

**Use For:** Background context videos, methodology sections, training narrative

#### Delivered Final Videos
Located in `delivered-videos/` — Finished, production-ready:
- `Video_1_Sales_Self-Sabotage.mp4` (42M) — Sales psychology concept
- `Video_3_AI_Collaboration.mp4` (51M) — AI + human collaboration

**Use For:** Case studies, principle explanations, full-length educational content

#### Quick CTA Videos
Located in `assets/` — Short, snappy endcard/CTA:
- `cta-endcard.mp4` (226K) — Call-to-action endcard (optimized size)

**Use For:** Hero section CTA, footer, booking section

#### 2026 Babson Summer Course Promo
Located in `2026-babson-summer-course-promo/` (9.5GB, 25+ subfolders)
- Multiple versions of each day's content
- Processing variations (final, video-only, audio-corrected versions)
- **Best for:** Educational, course-like content

---

## 🖼️ IMAGE ASSETS

### 1. VIDEO-PRODUCTION-MASTER Image Library
**Total Images:** 1,037  
**Location:** `/Users/scottmagnacca/ClaudeProjects/VIDEO-PRODUCTION-MASTER/assets/` and subdirectories

**Asset Types Available:**
- SVG icons (vectors, infinitely scalable)
- PNG graphics (transparent backgrounds)
- JPG photographs (team, office, professional)
- Illustrated graphics and diagrams

**Popular Subfolders:**
- `assets/graphics/` — Branded graphics, overlays
- `assets/icons/` — SVG icons for UI
- `effects-library/` — Visual effects, textures
- `2026-babson-summer-course-promo/` — Course graphics, slides

---

## 📋 Integration Quick Reference

### Small, Mobile-Friendly Videos
These are READY TO USE (already in `assets/video-library/`):
- ✅ broll-ai.mp4 (437K)
- ✅ broll-author.mp4 (210K)
- ✅ broll-contact.mp4 (162K)
- ✅ broll-advisor.mp4 (1.2M)
- ✅ broll-team.mp4 (1.2M)
- ✅ cta-handshake.mp4 (634K)
- ✅ cta-endcard.mp4 (226K from VPM)

**Action:** Copy any from `assets/video-library/` to `assets/video/` and integrate into `index.html`

### Medium Videos (1–2 min educational content)
Available in VIDEO-PRODUCTION-MASTER but NOT YET COPIED (files are 40–50MB):
- Delivered videos (Video_1, Video_3)
- Segment videos from `broll/` (44M each)

**Action:** Copy when needed, may require compression for web/mobile

### Large/Archive Videos
In VIDEO-PRODUCTION-MASTER but optimized for different use cases:
- Babson course content (full course library)
- Raw footage, working versions
- Multiple production iterations

**Action:** Reference as backup/archive; compress before web use

---

## 🎯 Recommended Next Steps

### Phase 1: Quick Wins (Ready Now)
1. Copy `cta-endcard.mp4` from VPM to `assets/video/`
2. Use `broll-advisor.mp4` for team training section
3. Use `broll-contact.mp4` to replace or enhance CLA Framework "Connection" card

### Phase 2: Refresh Hero/CTA (Medium Effort)
1. Consider `cta-handshake.mp4` for main booking button
2. Test `broll-team.mp4` in methodology section

### Phase 3: Advanced Content (Longer Videos)
1. Compress + resize delivered videos if adding educational/case study section
2. Pull from Babson course promo for training framework

---

## 🔧 Technical Notes

### File Sizes
- **Web-optimized:** <1MB (mobile-friendly, instant load)
  - Current: `cta-endcard.mp4` (226K) ✅ Perfect
  - From library: Most <2M ✅ Good
  
- **Standard web:** 1–5MB (fast load, good quality)
  - From library: `broll-*.mp4` (437K–1.2M) ✅ Ideal
  
- **Full quality:** 30–50MB+ (requires compression for web)
  - From VPM: Segment videos, delivered videos ⚠️ Compress before use

### Video Format Compatibility
All videos are `.mp4` (H.264 codec), compatible with:
- ✅ Modern browsers (Chrome, Safari, Firefox, Edge)
- ✅ Mobile devices (iOS, Android)
- ✅ Current CSS/JS infrastructure on scottmagnacca.com

### Compression Guide (if needed)
```bash
# To compress 40MB video to 2–3MB web version:
ffmpeg -i input.mp4 -vf scale=1280:720 -c:v libx264 -preset fast -crf 28 -c:a aac -b:a 128k output.mp4
```

---

## 📂 File Structure Reference

```
/Users/scottmagnacca/ClaudeProjects/
├── scottmagnacca-corporate/
│   ├── assets/video/              # Active videos (hero + CLA cards)
│   ├── assets/video-library/      # "Why Professional Help Matters" copies
│   └── ASSET-LIBRARY-REFERENCE.md # This file
│
├── Why Professional Help Matters.../
│   └── assets/video/              # Original source (7 videos)
│
└── VIDEO-PRODUCTION-MASTER/       # 505 videos + 1037 images
    ├── broll/                     # High-quality segment videos (5 files)
    ├── delivered-videos/          # Finished videos (2 files)
    ├── assets/                    # CTA + graphics (226K video + images)
    └── 2026-babson-summer-course-promo/  # Course library
```

---

## ⚡ Quick Copy Commands

```bash
# Copy CTA endcard from VPM
cp /Users/scottmagnacca/ClaudeProjects/VIDEO-PRODUCTION-MASTER/assets/cta-endcard.mp4 \
   /Users/scottmagnacca/ClaudeProjects/scottmagnacca-corporate/assets/video/

# Copy entire broll folder (if needed for reference)
cp -r /Users/scottmagnacca/ClaudeProjects/VIDEO-PRODUCTION-MASTER/broll/ \
      /Users/scottmagnacca/ClaudeProjects/scottmagnacca-corporate/assets/vpm-broll-reference/
```

---

## 📊 Asset Inventory Summary

| Source | Type | Count | Size | Ready? |
|--------|------|-------|------|--------|
| Why Professional Help Matters | Videos | 7 | 4.2M | ✅ YES (copied) |
| VIDEO-PRODUCTION-MASTER | Videos | 505 | 11GB | ⚠️ Selective (compress as needed) |
| VPM | Images | 1037 | - | ✅ YES (on disk) |

---

**Last Updated:** 2026-08-08  
**Current Branch:** `feature/video-integration-v1`  
**Status:** Ready to integrate additional assets as needed
