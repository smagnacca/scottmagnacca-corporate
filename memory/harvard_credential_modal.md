---
name: harvard_credential_modal
description: Interactive modal for Harvard credential verification with copy button
metadata:
  type: project
---

## Harvard Credential Verification Modal (2026-07-20)

**Added to index.html:** Click-to-open modal for the Harvard Verified credential badge in the About section.

**Implementation details:**
- HTML: Lines 3616-3619 (click trigger on credential badge), Lines 3626-3638 (modal markup)
- CSS: Lines 856-905 (modal styling, animations, responsive design)
- JavaScript: Lines 5262-5283 (openHarvardModal, closeHarvardModal, copyHarvardCode functions)

**Verification code:** `25LF-6G2C-RSA9`

**Features:**
- Click badge → modal opens with overlay fade-in
- Copy button saves code to clipboard (with fallback: document.execCommand if Clipboard API unavailable)
- Success feedback: "Copy" → "Copied!" button state change
- Direct link to Harvard's CeDiD validation portal (https://cecredential-validation.tlt.harvard.edu/)
- Keyboard accessible: Enter key triggers modal open/close
- Close button (×) and click-outside-modal both close it

**Why:** Credential verification UX improvement — visitors can now easily copy the code and paste it into Harvard's verification tool without manual typing.

**Live:** Deployed 2026-07-20 via manual Netlify CLI (GitHub Actions build failed; workaround: `netlify deploy --prod --dir=. --site=5374582f-f39a-44c6-9bb6-dd0f04b80bb0` after `npm install --prefix netlify/functions`)
