# Local Dev (Modern Sandbox)

This repository now includes a separate Astro sandbox in the `modern/` folder.
It is isolated from the legacy site files in the repo root.

## 1) Install dependencies (Windows)

1. Open **VS Code** in this repository.
2. Open **Terminal** (PowerShell or Command Prompt).
3. Run:

```bash
cd modern
npm install
```

## 2) Start local dev server

From inside `modern/` run:

```bash
npm run dev
```

Astro will print a local URL (usually `http://localhost:4321`).
Open that URL in your browser.

## 3) Build the site

From inside `modern/` run:

```bash
npm run build
```

## 4) Where built files appear

After build completes, output files are generated in:

- `modern/dist/`

That folder is the static build output for the modern sandbox.

## 5) Preview the migrated homepage

The Astro sandbox homepage now reproduces the legacy homepage structure and styling.

1. Start the dev server from `modern/`:
   ```bash
   npm run dev
   ```
2. Open the local URL Astro prints (typically `http://localhost:4321`).
3. You should see the migrated homepage at `/`.

Notes:
- Legacy homepage assets are referenced from `modern/public/` paths.
- Binary image assets are not committed; copy them manually as shown in section 6.
- The original legacy files in the repo root are unchanged.

## 6) Manual image files to copy (required)

Binary image files are intentionally **not** committed in this sandbox.
To render the migrated homepage exactly, copy these files from the legacy site into `modern/public/img/`:

- `img/spc.gif`
- `img/logo.gif`
- `img/ingo_face.jpg`

Example (from repository root):

```bash
mkdir -p modern/public/img
cp img/spc.gif img/logo.gif img/ingo_face.jpg modern/public/img/
```

