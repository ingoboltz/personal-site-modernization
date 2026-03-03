# Migration Status Audit (Retry)

## How this audit was produced

1. Attempted to fetch `codex-test-1` directly over HTTP/HTTPS.
2. Environment returned proxy `403` responses for both protocols.
3. Re-ran the migration assessment against the current local repository snapshot at `/workspace/personal-site-modernization`.

## What is already working in Astro

### Modern app foundation is in place
- Astro sandbox exists under `modern/` with standard scripts: `dev`, `build`, `preview`.
- Shared layout component (`LegacyShellLayout.astro`) reproduces legacy framing (logo/header/table shell + global color/link styles).

### Migrated routes currently available
The following Astro routes exist and render local content:
- `/`
- `/academic-record/`
- `/i-files/`
- `/i-files/africa`
- `/i-files/africa1`

### Legacy assets required by those routes are local
`modern/public/img/` already contains the key media needed by migrated routes (logo/spacer assets, world map image, transcript images, PDF assets), so these pages can render without reading assets from the root legacy site.

### Reliability/UX improvements already added
- `/i-files/` includes responsive client-side recalculation of image-map coordinates, so clickable map regions stay aligned when the world map scales on different viewport widths.

## What is still not migrated

### Migration coverage is still early
- Legacy HTML/PHP files outside `modern/`: **210**.
- Astro pages in `modern/src/pages`: **5**.
- Legacy content footprint remains concentrated in:
  - root entry files: **14**
  - `i-files/`: **194**
  - `photos/`: **2**

### Root-level legacy pages still pending Astro replacements
Pending pages include:
- `my_cv.html`
- `certificates.html`
- `certificate-tu.html`
- `certificate-bu.html`
- `thesis.html`
- `guestbook.html`
- `buch.html`
(plus legacy PHP/support files still present at root)

### Mixed modern/legacy navigation is still present
- Modern homepage still links to legacy `/i-files.html` instead of migrated `/i-files/`.

### Several modern pages still depend on legacy production domain URLs
The following modern pages still contain links to `https://www.ingoboltz.com`:
- `modern/src/pages/i-files/index.astro`
- `modern/src/pages/i-files/africa.astro`
- `modern/src/pages/i-files/africa1.astro`

This means these sections are still delegated to legacy content:
- Japan, Australia, Sporadic, Argentina sections
- Africa reports 2..8
- German Africa reports (`d-africa*`)
- Africa photos page

## Recommended migration sequence (next)

1. **Fix routing handoff first**
   - Update homepage link `/i-files.html` -> `/i-files/`.
2. **Complete Africa section**
   - Migrate `africa2..8` + `d-africa*` to local Astro pages.
3. **Migrate I-Files sibling sections**
   - Japan, Australia, Sporadic, Argentina/Weblog landing pages.
4. **Migrate root pages**
   - CV, certificates, thesis, guestbook, book page.
5. **Remove legacy domain dependency**
   - Delete `legacyBaseUrl` usage once local equivalents exist.
