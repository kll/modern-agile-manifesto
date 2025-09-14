# AGENTS.md — Guidance for Coding Agents

Purpose: Keep this Jekyll site minimal, consistent, and easy to maintain.
Follow these conventions when editing or adding files.

## Scope

- Applies to the entire repository unless a more nested AGENTS.md overrides it (none exist today).
- Do not edit build output in `_site/` — it is generated.

## Stack

- Static site built with Jekyll 4.x on Ruby 3.1–<4.0.
- Markdown engine: Kramdown; syntax highlighting: Rouge.
- No themes, no plugins. Keep dependencies minimal.

## Run Locally

- Prereqs: Ruby (via `rbenv`/`asdf`) and Bundler.
- Commands:
  - `rbenv install 3.3.0 && rbenv local 3.3.0` (or a 3.1–<4.0 Ruby per `Gemfile`)
  - `gem install bundler`
  - `bundle install`
  - `bundle exec jekyll serve --livereload`
- Base URL: If `baseurl: "/modern-agile-manifesto"` is set, open
  `http://127.0.0.1:4000/modern-agile-manifesto/`; otherwise
  `http://127.0.0.1:4000/`.

## Deployment

- Push to `main` triggers the GitHub Actions Pages workflow.
- Live site: `https://kll.github.io/modern-agile-manifesto/`.
- Respect `_config.yml` values: `url` and `baseurl` must remain consistent with the Pages URL.

## Project Layout

- `index.md` — home page using `layout: default`.
- `pages/` — additional content pages; each page must set front matter.
- `_layouts/default.html` — minimal HTML layout and hard‑coded nav; update here to add/remove links.
- `assets/` — static assets like CSS; prefer small, scoped changes in `assets/css/custom.css`.
- `_config.yml` — lean config; avoid adding plugins or themes.
- `_site/` — generated output; never commit manual edits here.

## Authoring Content

- Create pages in `pages/` with YAML front matter:

  ```yaml
  ---
  layout: default
  title: Page Title
  permalink: /page-slug/
  ---
  ```

- Permalinks: start and end with `/` (e.g., `/about/`).
- Internal links: always use `{{ "/path/" | relative_url }}` so links work locally and on Pages.
- Markdown: use fenced code blocks (```), headings in sentence case, and short paragraphs.
- Blog posts: This site is “pages only.” Do not add `_posts` content unless explicitly requested.

## HTML/Liquid Conventions

- Keep `_layouts/default.html` minimal; avoid adding global JS or large CSS. No analytics/trackers.
- Navigation is hard‑coded; ensure the correct `aria-current="page"` logic remains intact.
- Use built‑in Liquid filters (`relative_url`, `escape`) already present; do not add custom plugins.

## Style & Formatting

- Follow `.editorconfig` (UTF-8, LF, 2‑space indent, trim trailing whitespace;
  Markdown keeps trailing spaces off by default).
- Follow `.markdownlint.yml` (120‑char line limit for prose, final newline, minimal inline HTML).
- File naming: lowercase with hyphens; avoid spaces.
- Keep diffs small and focused; prefer incremental changes over broad refactors.

- Never disable style/lint rules via comments
  (e.g., `<!-- markdownlint-disable ... -->`, `eslint-disable`). Rules are meant to be
  followed. Fix content to comply or open a PR to adjust config with clear rationale;
  do not suppress violations inline.

## Accessibility & UX

- Maintain semantic HTML and logical heading order.
- Ensure link text is descriptive; avoid “click here”.
- Keep color contrast acceptable; avoid hard‑coding low‑contrast colors.

## What Not To Do

- Don’t add Jekyll plugins, themes, or third‑party JS without explicit approval.
- Don’t edit `_site/` or commit generated artifacts.
- Don’t break `baseurl` awareness; always use `relative_url` for internal links and assets.
- Don’t use inline rule suppressions for linters/formatters (no `markdownlint-disable`, no `eslint-disable`).

## Quick Checks Before PR

- Builds locally with `bundle exec jekyll serve` (no warnings/errors).
- All internal links work with and without `baseurl`.
- Markdown and layout changes respect the style rules above.
