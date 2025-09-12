# Manifesto — Static Pages on GitHub Pages

This is a tiny Jekyll site that serves a small set of rarely changing Markdown pages. There is no blog, no RSS, and no theme bloat.

## What’s Here
- `index.md` — simple homepage using the default layout
- `pages/about.md` — example content page
- `_layouts/default.html` — minimal HTML layout with a tiny header/nav
- `assets/css/custom.css` — optional custom styles
- `_config.yml` — lean config; no plugins or themes
- `.github/workflows/pages.yml` — GitHub Actions workflow to build and deploy

## Local Preview
```bash
brew install rbenv ruby-build    # macOS; or use asdf
rbenv install 3.3.0 && rbenv local 3.3.0
gem install bundler
bundle install
bundle exec jekyll serve --livereload
```
Open http://127.0.0.1:4000/manifesto/ if you’ve set `baseurl: "/manifesto"` locally. Otherwise visit http://127.0.0.1:4000/.

## Deployment
- Pushing to `main` runs the “Build and Deploy to Pages” workflow.
- Site URL: https://kll.github.io/manifesto/
- Relevant `_config.yml` settings in this repo:
  - `url: https://kll.github.io`
  - `baseurl: "/manifesto"`

## Add a Page
Create a Markdown file in `pages/` with front matter and a permalink, then link to it.

`pages/principles.md`:
```markdown
---
layout: default
title: Principles
permalink: /principles/
---

Your content here in Markdown.
```
It will publish at `https://kll.github.io/manifesto/principles/`.

Navigation links are hard‑coded in `_layouts/default.html` — update that file to add/remove items in the header.

## Internal Links
Use `{{ "/path/" | relative_url }}` so links work both locally and on Pages (respects `baseurl`).

## License
MIT or your preferred license.
