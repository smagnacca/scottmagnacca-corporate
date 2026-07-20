# Changelog

All notable changes to the Scott Magnacca website will be documented in this file.

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
