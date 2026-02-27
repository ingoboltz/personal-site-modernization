# Local Dev (Modern Sandbox) — Windows Guide

This guide is for working on the Astro sandbox in `modern/` without touching legacy root pages.

## 1) Quick start (Windows)

1. Open this repo in **VS Code**.
2. Open **PowerShell** in VS Code.
3. Go to the Astro sandbox:

```bash
cd modern
```

4. Install dependencies:

```bash
npm install
```

5. Start the dev server:

```bash
npm run dev
```

6. Open the URL shown in terminal (usually `http://localhost:4321`).

---

## 2) If `localhost:4321` is unreachable

Try these checks in order:

1. Confirm the dev server is still running in your terminal.
2. Open the exact URL printed by Astro (it may differ from `4321`).
3. Restart the server:

```bash
# Stop server with Ctrl+C
npm run dev
```

4. Force a host/port explicitly:

```bash
npm run dev -- --host 0.0.0.0 --port 4321
```

5. Try both URLs in browser:
   - `http://localhost:4321`
   - `http://127.0.0.1:4321`
6. If still blocked, check Windows Firewall/VPN/proxy and retry.

---

## 3) Where manually copied binary assets go

All manually copied legacy binaries must go here:

- `modern/public/img/`

After copying, Astro serves them as `/img/<filename>`.

Examples used by current migrated pages:

- `img/spc.gif`
- `img/logo.gif`
- `img/ingo_face.jpg`
- `img/tu-diploma.jpg`
- `img/bu-transcript.gif`
- `img/diploma.pdf`
- `img/compare.jpg`

---

## 4) Current Codex PR workaround (no binary files)

Codex PRs for this repo should not include new binary files.

Workaround:

1. In code, reference legacy assets by `/img/...` paths in Astro pages.
2. In PRs, update docs to list **exact filenames** that must be copied manually.
3. After pulling PR locally, copy required binaries from legacy `img/` into `modern/public/img/`.
4. Verify page rendering locally before merge.

---

## 5) Safe PR workflow for this repo (codex-test-1)

Use this flow for safe, low-risk changes:

1. Create/use branch `codex-test-1`.
2. Make only scoped changes requested in the task.
3. Do **not** edit legacy root files unless explicitly requested.
4. If a migrated page needs binaries, document manual copy steps in this file.
5. Run local checks (`npm run dev`, page smoke test, optional `npm run build`).
6. Commit with a focused message.
7. Open PR with:
   - What changed
   - What was not changed
   - Manual asset copy list (if needed)
   - Test results and any environment limitations

---

## 6) Local test checklist before continuing migration

Use this short checklist per page:

- [ ] Dev server starts from `modern/` (`npm run dev`).
- [ ] Target route loads (for example `/academic-record/`).
- [ ] No broken images/files in browser.
- [ ] Required binaries are present in `modern/public/img/`.
- [ ] Page matches legacy look/structure closely (no redesign).
- [ ] Console has no obvious page errors.
- [ ] (Optional) `npm run build` completes.
- [ ] Docs updated if any manual binary copy is required.

---

## 7) Build output location

When build succeeds:

```bash
npm run build
```

Output is generated in:

- `modern/dist/`
