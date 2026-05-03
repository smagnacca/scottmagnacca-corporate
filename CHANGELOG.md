# Changelog — scottmagnacca-corporate

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
