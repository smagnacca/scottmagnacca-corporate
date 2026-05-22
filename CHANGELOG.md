# Changelog — scottmagnacca-corporate

---

## 2026-05-22 — Add 3Cs Comparative Analysis Charts (commits `9bd1e53`→`0a9385c`)

**What changed:**
- Added `3cs-charts-clean.png` — comparative analysis graphs (+38%, +215%, +64%) below the 3Cs framework cards in `#framework` section
- Used Python/Pillow to remove Gemini AI sparkle watermark; required 3 passes to catch all antialiased stray pixels
- 8-line HTML insert in `index.html` at line ~2832, centered 960px max-width, rounded corners, `reveal` scroll animation

**Deploy:** `state=ready` at 2026-05-22T22:58:01Z — live at https://scottmagnacca-corporate.netlify.app

### Work Distribution
| | Actual |
|---|---|
| Local | ~72% (Pillow image editing, git) |
| Token-based | ~26% (planning, HTML edit) |
| Internet/API | ~2% (Netlify deploy) |

---

## 2026-05-20 — Babson Strip Book Cover Update (commit `6846284`)

**What changed:**
- Replaced `babson-scott-feature.jpg` with full book cover `Cover.png` (full title "Storyselling in The Age of AI" now visible)
- Rebuilt right-side element as an HTML card: cover image + 3-line caption below
- Sized both left (Babson magazine) and right (book cover) images to 108px wide for visual balance

**Deploy:** `state=ready` at 2026-05-20T01:12:08Z — live at https://scottmagnacca-corporate.netlify.app

### Work Distribution
| | Actual |
|---|---|
| Local | ~70% |
| Token-based | ~30% |
| Internet/API | ~5% (Netlify deploy) |

---

## 2026-05-19 — UI Tweaks, Pill Fix, Form Fix & Sequential Stats (commits `8908d91`→`87aff68`)

### Work Distribution
| | Estimate | Actual |
|---|---|---|
| Local | ~80% | ~88% |
| Token-based | ~18% | ~10% |
| Internet/API | ~2% | ~2% |

**Local work:** File edits (index.html, CHANGELOG.md), git commits/pushes, Playwright preview screenshots (8), curl form test, Netlify CLI env:set, token file lookups, lock file cleanup
**Token-based:** Code generation for 7 changes, bug diagnosis (NaN pill, sequential count-up), planning
**Internet/API:** Netlify deploy API status checks, live form endpoint test (`POST /.netlify/functions/contact-form`)
**Delta:** Local higher than estimated — SendGrid key was in `~/.claude/tokens/` so no manual steps needed; all QA ran in local preview server

---

## 2026-05-19 — UI Tweaks, Pill Fix & Form Fix (commits `8908d91` + pending)

### UI Changes
- **Hero text:** "with AI + Narrative Intelligence" full gold (including "with" word)
- **Visit counter:** `localStorage` increments Leaders Trained by +1–3 and tracks visits per session
- **Stat pill fix:** "$1B+ Client Value Generated" → static "Over $1 Billion in Sales Generated" (fixed NaN bug)
- **Bridge line:** Bounce-in animation on scroll reveal
- **Quote:** Center-aligned, smaller font, flows as single paragraph (no line breaks)
- **Format cards:** Sequential green glow pulse border (cards fire in order: Workshop → Keynote → Deep Dive → Custom)
- **Formats-note:** Thicker gold border, more visible

### Form Fix
- **Root cause:** `SENDGRID_API_KEY` was missing from Netlify environment
- **Fix:** Key located in `~/.claude/tokens/.sendgrid_token` and injected via Netlify CLI
- **Verified:** Live `POST /.netlify/functions/contact-form` returns `{"success":true}`
- **Behavior:** Submissions write to Google Sheet (`Discovery_Calls` tab) and email scott.magnacca1@gmail.com

---

## 2026-05-19 — Babson Magazine Feature Strip (commit `fd8e177`)

Added a small credibility strip between the "About Scott" section and FAQ.

- **New section:** Subtle gold-bordered strip with green glow pulse (matches book cover glow in About section)
- **Left:** Babson Magazine Spring 2026 cover thumbnail
- **Middle:** Pull-quote with bold key phrase + "Babson College Faculty" and "MBA '92" pills
- **Right:** Article clipping of Scott's book feature from Graduate News, Notes & Nods
- **Images added:** `babson-magazine-cover.jpg`, `babson-scott-feature.jpg` (extracted from PDF)
- **Deploy note:** GitHub Actions CI broken (googleapis dependency issue pre-existing since May 3). Deployed via local `netlify deploy --prod` after installing function deps locally.

---

## 2026-05-03 — About Section Animations & Book Cover Fix (3 Changes)

**Commits:** `88d769c` + `e8fcc59` — Badge animations, wage premium border polish, and book display

### 1. Wage Premium Explainer — Pulsing Gold-Green Border
Added emphasis to the "What Is the Wage Premium?" section with a dynamic glowing border:
- **Border:** 3px solid gold (#f5a623) with `pulseGoldGreen` animation (alternates gold ↔ green every 2s)
- **Effect:** Draws attention to key value-definition content; matches framework card styling
- **CSS:** Applied `animation: pulseGoldGreen 2s ease-in-out infinite;` to `.wage-premium-explainer`

### 2. Credential Badges — Staggered Fade-In with Pulse on Appearance
Transformed badge animations to trigger after the "About Scott" bio typewriter completes:
- **Default state:** Badges hidden (`opacity: 0`)
- **Trigger:** After bio typewriter finishes, badges fade in sequentially at 1-second intervals (top-left → bottom-right)
- **Animation:** Each badge pulses once (scale 1 → 1.08 → 1) as it appears
- **Implementation:** New `credBadgePulse` keyframe; added `.badge-animate` class triggered by JavaScript after `animateBoldsToGreen()`
- **Effect:** Choreographed entrance sequence for credential badges; no jarring automatic animations

### 3. Book Cover Image — Fixed Top Cutoff & Added Amazon Button
Fixed the book cover display in the wage premium results section:
- **Image fix:** Set explicit height (165px); changed `object-fit: contain` → `object-fit: cover` with `object-position: top center`
- **Result:** Full book cover now displays without clipping the top
- **Amazon button:** Added small gold button below book cover linking to https://a.co/d/01EE7EdH (opens in new tab)
- **Styling:** Gold background (#f5a623), rounded corners, smooth transitions to match page design

---

## 2026-05-03 — Value Prop Requirements Polish & Animation Sync (2 Changes)

**Commits:** `553bd14` + `04eaeae` — Requirements section refinements and animation timing

### 1. Requirements Section Headers — Visual Hierarchy
Added descriptive sub-headers to elevate copy clarity and visual structure:
- **Left column (avoid):** "You Won't Need to" — bold red text (`#ff4444`) above "Hire new people"
- **Right column (get):** "Immediate impact" — bold white text above "No new hires"
- **CSS:** New `.requirement-header` + `.requirement-header-text` classes with fade-in animation
- **Spacing:** Added 32px top margin to `.value-prop-sentence` for visual separation between requirements grid and CTA

### 2. Animation Sync — Requirements Trigger After Typewriter Completes
Transformed scroll-trigger animations into typewriter-synchronized sequence:
- **Before:** Requirements animated on scroll (independent of hero copy)
- **After:** Requirements wait for hero typewriter to complete ("...days, not quarters."), then pause 1s, then animate
- **Implementation:** Added `window.typewriterComplete` flag set when typewriter finishes; `initValuePropTimeline()` polls flag and starts animations 1s later
- **Effect:** Cohesive, choreographed entrance sequence across hero + value prop sections; no jarring independent animations

---

## 2026-05-03 — Broaden Appeal & Visual Enhancements (6 Changes)

**Commit:** `fd542ab` — "feat: broaden site appeal by removing sales-specific language and add visual enhancements"

### 1. Terminology Shift — "Sales" Removed (16 instances)
Replaced sales-specific language with broader professional terminology to expand appeal beyond sales teams:
- **Hero:** "AI Sales Training" → "AI Training" | "Equip Your Sales Team" → "Equip Your Team"
- **Title tag:** "AI Sales Training for Corporate Teams" → "AI Training for Corporate Teams"
- **Bio:** "AI Sales Strategist" → "AI Strategist" (2 instances)
- **Impact quote:** "Most sales teams running 2015 playbook" → "Most teams running 2015 playbook"
- **Stats:** "AI-skilled sales professionals" → "AI-skilled professionals" | "AI-ready sales capabilities" → "AI-ready capabilities"
- **Framework intro:** "For sales professionals, this isn't optional" → "For professionals, this isn't optional"
- **Format cards:** "AI sales workshop" → "AI workshop" | "sales kickoffs" → "kickoffs" | "sales team offsites" → "team offsites" | "sales leadership retreats" → "leadership retreats"
- **Testimonials:** "Our sales team left" → "Our team left" | "VP of Sales" → "VP"

### 2. Core Value Prop Reframe
- **"The Modern Sales Gap" → "The Modern Skills Gap"** (line 2455)
  - Signals broader value to non-sales audiences (executives, marketing, ops, product leaders)

### 3. Agility & Adaptability Copy — Elevated Language
- **Old:** "Sales is a conversation, not a script..."
- **New:** "Connection and persuasion is a conversation, not a script..."
  - Removes sales-specific framing; emphasizes universal communication principle

### 4. Framework Cards — Bold Gold/Green Pulsing Border (NEW)
Added visual emphasis to the three 3Cs principle cards:
- **CSS:** `.framework-card { border: 6px solid #f5a623 !important; animation: pulseGoldGreen 2s ease-in-out infinite; }`
- **Animation:** `@keyframes pulseGoldGreen` alternates border color between gold (#f5a623) and green (#22c55e) with 15px glow
- **Effect:** Draws eye to methodology; makes framework section visually distinct

### 5. GUARANTEE Section — Green Pulsing Border (NEW)
Added persuasive commitment statement below Training Formats:
```html
<div class="formats-guarantee reveal">
  <h3>GUARANTEE</h3>
  <p>If you don't walk away from our course session with at least three deployable client stories 
  and immediately actionable Practical AI skills, your enrollment is free. No fluff. No "go practice 
  and come back." You leave the workshop with a story you can use on your next meeting this week — guaranteed.</p>
</div>
```
- **CSS:** `.formats-guarantee { border: 4px solid #22c55e; animation: pulseGreen 2s infinite; background: rgba(34, 197, 94, 0.05); }`
- **Animation:** Green pulsing border (intensity varies 0.6s → 0.9s opacity)
- **Placement:** Right after formats-note, before CTA button
- **Impact:** High-confidence, risk-reversal value signal

### 6. Book Cover Display Fixed
- **Issue:** Top of book cover image was being clipped in the wage-premium results section
- **Fix:** Added CSS properties to `.gift-cover`:
  - `display: block;` — ensures proper rendering
  - `object-fit: contain;` — displays full image without crop
  - Added `overflow: visible;` to `.gift-cover-wrap`
- **Result:** Full book cover now visible (previously top 20% was cut off)

---

## 2026-05-02 — Repo Established as Canonical, Auto-Deploy Wired, Wage Section Upgraded

**This is the first changelog entry. Going forward, all corporate landing-page work happens in this repo.** Prior edits were happening in `code-cowork-2026-7-marketing-outreach/landing-page/` and pushed to live via manual `netlify deploy`. That path is now deprecated.

### A. Wage Premium section — copy + visual upgrades
Added between the existing 3Cs framework section and Training Formats:

- **3-4-3 explainer block** above the calculator with three sub-headings:
  - **What Is the Wage Premium?** (3 sentences) — additional income from repositioning as high-leverage, AI-fluent professional
  - **Why It Matters** (4 sentences) — 30–50% earning-potential gap, AI widening the indispensable-vs-useful divide
  - **How Practical AI Skills Help You Earn It** (3 sentences) — AI fluency + storyselling = 1.5x unlock
- **Free-gift framing** in the unlocked results stage:
  - Thank-you copy: "As a thank-you for sharing your email, we'd like to send you a free gift — the first chapter of Scott's book, *Storyselling in the Age of AI*."
  - Storyselling **book cover image** with animated **gold pulsing glow** (`giftGoldPulse` keyframe, 2.6s loop)
  - Placed above the existing Download Chapter 1 CTA
- New CSS classes: `.wage-premium-explainer`, `.wpe-heading`, `.gift-block`, `.gift-thanks`, `.gift-cover-wrap`, `.gift-cover` (mobile breakpoint at 768px)

### B. Repo sync from marketing-outreach
- rsync'd full `landing-page/` contents into this repo (excluded `node_modules`)
- Reset local main to origin/main first (content was identical, just different SHAs from prior divergence)
- All assets brought over: book-cover, buffett carousel images, format thumbnails, headshot, hero
- Netlify function `contact-form.js` + its package.json brought over
- Added `.gitignore` for node_modules / .netlify / logs
- Sync commit: `04d5b76`

### C. Auto-deploy pipeline (the big infrastructure win)

**Problem:** Netlify site `scottmagnacca-corporate` (ID `5374582f-f39a-44c6-9bb6-dd0f04b80bb0`) had `repo_url` set but no `deploy_key_id` configured. Pushes to GitHub did NOT trigger Netlify builds. Every deploy required manual `netlify deploy --prod` from terminal.

**First attempt — build hook:** Created Netlify build hook (`69f66e4e85e009fa07cca87c`) and a GitHub Action that POSTed to it. Failed because Netlify still tried to clone the repo from its end and the SSH host key wasn't configured. Build hook still exists but is unused.

**Final solution — direct CLI deploy from Action:**
- Created encrypted GitHub Actions secret `NETLIFY_AUTH_TOKEN` via API (used pynacl + GitHub repo public key for sealed-box encryption)
- New workflow `.github/workflows/netlify-deploy.yml`:
  - Trigger: push to `main`
  - Steps: checkout → install netlify-cli → install function deps from `netlify/functions/package.json` → `netlify deploy --prod --dir=. --site=<id>`
  - Uses `${COMMIT_SHA:0:7}` for single-line deploy message
- **End-to-end verified:** push `0f649f8` → Action conclusion `success` → Netlify state `ready` → live site content match confirmed

**Result:** No more `netlify deploy` from terminal. Just `git push origin main` and it goes live.

### D. Project documentation
- **`CLAUDE.md`** (new) — single source of truth for this repo. Contains:
  - Project info, GitHub repo, Netlify site ID, live URL
  - Deploy method (auto via Action)
  - **Mandatory Hermes/Ollama local-first protocol** for all major changes (per global `~/.claude/CLAUDE.md` §20)
  - Pre-Flight Cost Alert format that must be issued before multi-step work
  - Session start + session end checklists

### Commits this session
- `04d5b76` — sync from marketing-outreach landing-page
- `71d838c` — add CLAUDE.md and first workflow attempt (build hook)
- `6774d77` — switch to direct Netlify CLI deploy
- `0f649f8` — fix function deps install + single-line deploy message

### Status
✅ All live. Auto-deploy verified. Repo is now the canonical home.

### Next
- Any corporate landing-page change → edit here → `git push origin main` → done
- Major changes must follow the Hermes/Ollama protocol in CLAUDE.md
