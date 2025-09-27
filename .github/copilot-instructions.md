<!-- .github/copilot-instructions.md: Guidance for AI coding agents working on this repository -->
# Copilot instructions — my-app (Vite + React template)

This file contains concise, actionable notes to help an AI coding agent be immediately productive in this repository.

High-level summary
- Minimal React app bootstrapped with Vite. Main entry: `src/main.jsx`. Root component: `src/App.jsx`.
- Build tool & dev server: Vite (`vite` in `package.json` scripts). HMR is enabled by default.
- Linting: ESLint configured; run with `npm run lint`.

Essential commands (from `package.json`)
- Dev server (fast local development with HMR): `npm run dev` (runs `vite`).
- Build production bundle: `npm run build` (runs `vite build`).
- Preview production build: `npm run preview` (runs `vite preview`).
- Lint code: `npm run lint` (runs `eslint .`).

Important files and what they show
- `index.html` — Vite HTML entry, contains the `#root` element the app mounts into.
- `src/main.jsx` — app bootstrap; uses `createRoot` and wraps `App` with `StrictMode`.
- `src/App.jsx` — main UI component; shows common project conventions (JSX, CSS imports, asset imports).
- `src/*.css` — global and component styles. CSS is imported directly in JS modules.
- `vite.config.js` — Vite config; check this for any platform-specific plugin or aliasing (small template may not add aliases).
- `package.json` — dependency list (React 19, Vite) and scripts; use this as source of truth for build/test commands.

Project-specific patterns and conventions
- ESM + React 19: files use ES modules (package.json has `type: "module"`).
- Assets: static SVGs in `src/assets` are imported as modules (e.g., `import reactLogo from './assets/react.svg'`). Vite will handle them.
- Absolute `/vite.svg` import is used in `App.jsx` for a file placed in `public/` — treat `/` paths as Vite public root.
- CSS: global CSS files are imported from JS entry points (no CSS modules in this template).
- No TypeScript by default. There are `@types/*` devDependencies but source is plain JSX. Treat types as optional unless TS is introduced.

Developer workflow notes
- Use `npm install` (or `npm ci` if CI lockfile fidelity is required) to install dependencies. The repository includes a `package-lock.json`.
- On Windows (PowerShell), commands are the same as POSIX: `npm run dev` etc. When combining commands, use `;`.
- Linting: run `npm run lint` to surface ESLint issues; this template uses `eslint` and `@eslint/js` with React plugins. Fix only relevant files.

Common edits an AI might make and expectations
- Add a new component: create `src/components/Name.jsx` and import into `src/App.jsx` or `src/main.jsx`. Follow existing JSX style (default export). Add a matching CSS file if needed.
- Add assets: put them under `src/assets` for module imports or under `public/` for root-relative imports (use `/filename.ext`).
- Add dependencies: update `package.json` and run `npm install`. Keep versions conservative; prefer existing devDependency patterns (e.g., plugin versions pinned).

Integration points & external dependencies
- React and ReactDOM are primary runtime deps. Vite provides dev/build tooling.
- No backend or API integration is present in the template. If adding one, document the API shape and tests.

Examples from this repo (use these to infer patterns)
- Mounting point: `createRoot(document.getElementById('root')).render(...)` in `src/main.jsx`.
- Asset import: `import viteLogo from '/vite.svg'` (public root) and `import reactLogo from './assets/react.svg'` (module asset).
- State hook usage: `const [count, setCount] = useState(0)` in `src/App.jsx`.

When editing, prefer minimal, local changes
- Avoid large refactors in one PR. Keep changes localized to a few files.
- Preserve `package.json` scripts unless adding new developer-facing scripts.

What not to assume
- There is no test runner configured (no `test` script). Do not add tests without also adding a test config and devDependencies.
- No backend or environment variables are configured; avoid referencing process.env keys without adding .env docs and a safe fallback.

If you change build config
- Update `vite.config.js` and `package.json` together if necessary, and ensure `npm run build` still succeeds locally.

Follow-up and feedback
- If any sections are unclear or you want more detail (for example, how to add TypeScript, or where to wire API calls), tell me which area to expand and I'll iterate.
