# AGENTS.md

## Repo purpose (verified)
- This is a **Hexo** blog repository; content lives in `source/_posts/` and is published to GitHub Pages.
- `main` branch pushes trigger `.github/workflows/deploy.yml` to build and deploy.

## High-value paths
- `source/_posts/*.md`: blog posts (primary editable content).
- `_config.yml`: site/runtime behavior (URL, language, permalink, render rules).
- `scaffolds/post.md`: default front matter template for new posts.
- `.github/workflows/deploy.yml`: source of truth for CI deploy behavior.

## Commands (exact)
- Install deps: `npm ci` (matches CI) or `npm install`.
- Local preview: `npm run server` (serves at `http://localhost:4000`).
- Build static site: `npm run build` (outputs to `public/`).
- Clean generated output/cache: `npm run clean`.

## Deploy/release facts
- CI uses **Node 20** + `npm ci` + `npm run build`, then uploads `public/`.
- Prefer CI-based deployment via push to `main`.
- `npm run deploy` exists, but `_config.yml` has `deploy.type: ""`; do not assume one-command Hexo deploy is configured.

## Content conventions that matter
- Posts are Markdown files under `source/_posts/` with YAML front matter.
- Minimal scaffolded front matter is:
  - `title`
  - `date`
  - `tags`
- Existing posts may also include fields like `slug`; preserve them when editing.

## Gotchas
- `public/` is generated output; edit source files, then rebuild.
- `_config.yml` sets `future: true`; future-dated posts are rendered.
- `_config.yml` sets `updated_option: "mtime"`; file modification time affects updated timestamps.
