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
