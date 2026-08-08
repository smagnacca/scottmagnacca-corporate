# Changelog

All notable changes to the Scott Magnacca website will be documented in this file.

## [Unreleased] - 2026-08-08

### Added
- **Video Integration Scaffolding** (`index.html`, `assets/video/`): Complete infrastructure for background and hover videos across hero section and CLA Framework cards
  - **Hero background video** (35% opacity): `hero-sales-ai.mp4` with gradient scrim overlay ensures headline stays readable
  - **CLA Framework card overlays** (60% opacity): Three embedded videos (Curiosity, Lifelong Learning, Agility & Adaptability) fade in on hover with scrim effects — brighter, more visible
  - **Responsive behavior**: Desktop hover auto-play, mobile tap-to-toggle, all devices maintain aspect ratio
  - **Demo page** (`video-demo.html`): Standalone visual demonstration of video effects and scaffolding
  - **Video files** (3 of 6 generated): `hero-sales-ai.mp4` (2.5 MB), `cla-curiosity.mp4` (2.5 MB), `playbook-2026.mp4` (2.7 MB)

- **Antigravity Broll Background Sections** (Session 2, 2026-08-08):
  - **"The Challenge" section** (25% opacity): `broll-network-data.mp4` (1.6 MB) — Network/data visualization backdrop
  - **"Training Formats" section** (25% opacity): `broll-network-connect.mp4` (1.7 MB) — Network connectivity backdrop
  - **"Wage Premium Calculator" section** (25% opacity): `broll-circuit.mp4` (2.9 MB) — Circuit board/processing backdrop
  - All with dark gradient scrim overlays (::before pseudo-elements) for text readability
  - Autoplay, muted, looping; responsive sizing via `object-fit: cover`
  - Source: VIDEO-PRODUCTION-MASTER Antigravity library (watermark-free, web-optimized)

### Technical
- CSS video styling: `.video-background`, `.video-scrim` (gradient overlay), hover opacity transitions (0.4s ease)
- Z-index layering fixed: video (z-1), scrim (z-2), content (z-3) for proper visibility
- JavaScript video control: Hero auto-play on load, card hover/tap handlers with play/pause/reset logic
- File structure: `assets/video/` contains test videos + 3 final Gemini Veo renders
- **Status**: Full integration complete; 3 of 6 final videos in place; ready for remaining 3 videos

### Changed
- CLA card video opacity: 42% → 60% for better visibility and impact

### Next Steps (Pending)
- **Generate final 2 Gemini Veo videos** (when credits available):
  - `cla-learning.mp4` — Lifelong Learning card (education/mentorship focus)
  - `cla-agility.mp4` — Agility & Adaptability card (partnership/connection focus)
- Replace test videos in `assets/video/` with final renders
- Local preview: Verify background videos visible at 25% opacity (Problem, Formats, Wage Premium sections)
- Verify loop seams and hover effects across desktop (Chrome/Safari), tablet, mobile
- Screenshot proof (desktop 1280px, tablet 768px, mobile 375px) before pushing feature branch to GitHub
- Commit + push `feature/video-integration-v1` to GitHub
- Create PR to main branch with final verification screenshots

## [1.1.1] - 2026-07-20

### Added
- **Harvard Credential Verification Modal** (`index.html`): Interactive modal popup for the Harvard Verified credential badge in the About section
  - Click-to-open modal on credential badge (lines 3616-3619)
  - Modal displays verification code: `25LF-6G2C-RSA9`
  - Copy button with fallback support (Clipboard API + document.execCommand)
  - Direct link to Harvard's CeDiD validation site
  - CSS styling for modal overlay, styling (lines 856-905 in styles)
  - JavaScript functions: `openHarvardModal()`, `closeHarvardModal()`, `copyHarvardCode()` (lines 5262-5283)

### Technical
- Improved credential verification UX: visitors can now easily copy the verification code and paste it directly into Harvard's validation portal
- Deployed via manual Netlify CLI after GitHub Actions build failure (standard workaround)

## [1.1.0] - 2026-06-07

### Added
- **Interactive AI Case Study Page** (`anthropic-case-study.html`): A standalone, premium dark-themed interactive page displaying data from Anthropic's research on AI authorship and team velocity.
  - Interactive SVG Line Chart (AI Code Authorship growth from 3% to 82%).
  - CSS Animated Pillar Bar Chart (8x Development Velocity Scaling).
  - SVG Pictogram comparison (1x vs 4x Individual Output leverage).
  - Synchronized, delayed fade-in animations for section columns (Charts at 0.5s, "What the Data Means" at 9.5s, "How it Applies to Sales" and CTA at 19.5s).
- **Homepage CTA Section** (`index.html`): Added a "Research Spotlight" CTA section highlighting Anthropic's findings and linking directly to the new interactive case study.
- **Calculate Team Savings Button**: Centered at the bottom of the case study page, styled in bright blue, linking back to the team capacity calculator (`index.html#wage-premium`).

### Changed
- Styled references and links in **bright blue** (`#007AFF`) and removed the `(APA Format):` label.
- Customized bullet points and headers:
  - **What the Data Means**: Styled headers and list bullet icons in **bright blue** (`#007AFF`).
  - **How it Applies to Sales**: Styled headers and list bullet icons in **bright gold** (`#f5a623`).
