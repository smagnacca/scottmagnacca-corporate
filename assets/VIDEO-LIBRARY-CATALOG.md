# Video Library — Reusable Content from "Why Professional Help Matters"

All videos from the "Why Professional Help Matters" project have been copied to `assets/video-library/` for potential reuse on scottmagnacca.com.

## Available Videos

### B-Roll / Background Videos

| Video | Size | Type | Content | Potential Use for ScottMagnacca.com |
|-------|------|------|---------|-------------------------------------|
| **broll-advisor.mp4** | 1.2M | B-roll | Professional advisor/mentor in action | Team training, consultation scenarios |
| **broll-ai.mp4** | 437K | B-roll | AI technology, screens, digital tools | AI training content, tech references |
| **broll-author.mp4** | 210K | B-roll | Author/expert speaking, presenting | Speaker intro, thought leadership |
| **broll-chapter.mp4** | 218K | B-roll | Book chapters, reading, narrative | Framework storytelling |
| **broll-contact.mp4** | 162K | B-roll | Contact moments, handshakes, connection | CLA Framework: Connection principle |
| **broll-team.mp4** | 1.2M | B-roll | Team collaboration, group dynamics | Team training, methodology |

### CTA / Interactive Videos

| Video | Size | Type | Content | Potential Use |
|-------|------|------|---------|-----|
| **cta-handshake.mp4** | 634K | CTA | Handshake, agreement, partnership | Call-to-action, booking moments |

---

## Recommendations for ScottMagnacca.com

### ✅ High Relevance
- **broll-advisor.mp4** — Advisor/mentor in action → Perfect for training scenarios, consultation framing
- **broll-team.mp4** — Team collaboration → Excellent for "methodology" or "training formats" sections
- **broll-contact.mp4** — Connection/handshake → Could replace or enhance CLA Framework "Connection" principle
- **cta-handshake.mp4** — Partnership handshake → Perfect for "Book Discovery Call" or main CTA sections

### ⚠️ Moderate Relevance
- **broll-ai.mp4** — AI tech references → Fits AI training narrative (smaller file, good quality)
- **broll-author.mp4** — Speaking/presenting → Could work for thought leadership sections

### ⏸️ Lower Relevance
- **broll-chapter.mp4** — Book-specific content → Less aligned with scottmagnacca.com branding

---

## How to Use

1. **Reference locally**: Browse videos in `assets/video-library/`
2. **Copy to production**: When ready to use, move video to `assets/video/` and update `index.html`
3. **No file size limit**: All files are <1.3M (mobile-friendly)
4. **Loop-ready**: All are pre-formatted for seamless loop playback

---

## Integration Path

To use any video from this library:

```bash
# 1. Copy video to production folder
cp assets/video-library/broll-advisor.mp4 assets/video/

# 2. Add to index.html where needed:
# Example: <video autoplay muted loop playsinline>
#           <source src="assets/video/broll-advisor.mp4" type="video/mp4">
#         </video>

# 3. Apply CSS opacity + scrim (same as CLA cards)
# 4. Test and verify
```

---

## Notes

- All videos from "Why Professional Help Matters" project (August 2026)
- Same quality/format as current production videos
- Can be used as-is or modified with ffmpeg if different aspects needed
- Consider brand consistency when selecting (both projects have similar visual language)

---

**Last updated:** 2026-08-08 session  
**Status:** Ready for integration when needed
