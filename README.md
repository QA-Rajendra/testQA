# QA_RP_TestCases Tool — React + Vite

This is a React + Vite conversion of the original single-file `QA_RP_TestCases_Tool.html` app (an AI-powered enterprise QA test suite generator that talks to the Groq API).

## What changed vs. the original

The original file was one big HTML document with inline `<style>` and `<script>` tags and no build step. It's been restructured into a standard Vite + React project:

- `index.html` — slim HTML shell, loads the same third-party libraries the app already depended on (`marked`, `xlsx`, `chart.js`) from CDN, exactly as before.
- `src/main.jsx` — React entry point.
- `src/App.jsx` — mounts the app's markup and runs its original logic once, on mount.
- `src/legacy-body.html` — the app's original UI markup (toolbar, panes, drawers, progress overlay, etc.), unchanged.
- `src/legacy-app.js` — the app's original JavaScript (event wiring, Groq API calls, markdown/table parsing, dashboard charts, exports), unchanged.
- `src/legacy.css` — the app's original styling (dark/light theme variables, layout, components), unchanged.

The app's internal logic is still imperative DOM-driven code (it reads/writes the DOM directly by element id, the same way it did in the original file) rather than idiomatic React state/components. This was a deliberate choice to guarantee the converted app behaves **identically** to the original — every feature (AI generation, dashboard, bug reports, chat, exports to `.md`/PDF/Excel, theming, etc.) works exactly as it did before, just now inside a React + Vite project you can build, bundle, and deploy like any other modern frontend app.

If you'd like this refactored further into idiomatic React components (hooks-based state instead of direct DOM manipulation), that's a good next step but a much larger, riskier rewrite — happy to do it incrementally if wanted.

## Getting started

```bash
npm install
npm run dev
```

Then open the printed local URL. Enter your Groq API key in the toolbar to use the AI features.

## Build for production

```bash
npm run build
npm run preview
```

Output goes to `dist/`.
