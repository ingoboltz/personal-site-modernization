# CODEX Migration Plan (No-Design-Change)

## 1) Current Site Inventory

### Main HTML/PHP entry points (repo root)
- `index.html` (homepage)
- `i-files.html` (hub to travel/journal sections)
- `my_cv.html`, `certificates.html`, `certificate-tu.html`, `certificate-bu.html`, `thesis.html`, `guestbook.html`, `buch.html`
- Legacy root PHP files also present (`CHANGELOG.php`, `CREDITS.php`, `COPYRIGHT.php`, `phptest_off.php`)

### Content folders
- `i-files/` (largest section: Africa/Japan/Australia reports, print pages, generated photo subpages)
- `photos/` (photo assets and gallery pages)
- `i-files/gate5/` (legacy map/diagram mini-site)

### CSS
- Single stylesheet: `formate.css` at repository root

### Image/media folders
- `img/` (shared UI images, logos, documents, some audio files)
- `photos/` (travel images + thumbnails)
- additional media files under subfolders like `photos/australia/`, `photos/argentina/`

### JavaScript
- Minimal JS footprint:
  - `i-files/gate5/locate_utils.js`
  - Inline scripts inside existing HTML pages (legacy behaviors + analytics snippets)

---

## 2) Modernization Risk Checklist

Use this checklist before and during migration:

- [ ] **Relative link correctness**
  - Verify links are valid from each page location (root pages vs nested `i-files/*`).
- [ ] **Absolute path assumptions**
  - Check links that start with `/...` still resolve when previewing locally.
- [ ] **Case sensitivity mismatches**
  - Normalize/verify references like `.jpg` vs `.JPG` for Linux/macOS correctness.
- [ ] **Missing local assets**
  - Identify files referenced by HTML that do not exist in repo.
- [ ] **Legacy external dependencies**
  - Note HTTP-only third-party scripts or endpoints that may fail in local preview.
- [ ] **Duplicate pages with parallel extensions**
  - Track `.htm` and `.html` duplicates to avoid drift.
- [ ] **Image-heavy pages**
  - Confirm all thumbnails/full-size image references survive copy/build steps.
- [ ] **Non-HTML artifacts referenced by pages**
  - Validate PDFs/RTFs/docs linked from content pages.
- [ ] **Encoding/charset consistency**
  - Preserve current legacy encodings and avoid accidental content re-encoding.
- [ ] **No visual drift rule**
  - Compare before/after screenshots for representative pages.

---

## 3) Phased Migration Plan (Preserve Exact Look & Feel)

### Phase 0 — Baseline lock
1. Capture baseline screenshots of key pages (`index.html`, `i-files.html`, 1–2 deep content pages).
2. Run a link/assets scan and save report.
3. Record a simple manifest of current file layout.

### Phase 1 — Static build scaffold (no transforms)
1. Add a modern static build tool in **copy-only mode** (passthrough assets + HTML as-is).
2. Build output to `dist/` with identical relative structure.
3. Add local commands for build + preview.

### Phase 2 — Reliability checks
1. Add automated broken-link + missing-asset checks.
2. Add case-sensitivity checks for file references.
3. Keep a short allowlist for intentional external URLs.

### Phase 3 — Path integrity fixes only
1. Fix clearly broken relative/absolute paths.
2. Restore or document unavailable legacy targets.
3. Re-run checks and verify no visual changes.

### Phase 4 — Optional maintainability (still no design/content changes)
1. Introduce shared includes/templates for repeated header/nav/footer blocks.
2. Ensure rendered HTML preserves current structure and styling behavior.
3. Keep all file names/URLs stable unless explicitly approved.

### Definition of done for each phase
- Build passes.
- Link/assets checks pass (or known exceptions documented).
- Manual visual comparison shows no appearance change.

---

## 4) Suggested First Code Task (Small + Reversible)

**Task:** Add a minimal static build scaffold that only copies existing files to `dist/` (no HTML/CSS/JS edits).

Why this first:
- Very low risk.
- Fully reversible (remove config + lockfile if needed).
- Immediately gives repeatable local preview/build workflow.

Acceptance criteria:
- Running build produces `dist/` with the same folder structure for current static files.
- Opening `dist/index.html` looks the same as current root `index.html`.
- No existing source files are modified.
