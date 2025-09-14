# Modern Agile Manifesto — Static Pages on GitHub Pages

This is a tiny Jekyll site that serves a small set of rarely changing Markdown pages.
There is no blog, no RSS, and no theme bloat.

## What’s Here

- `index.md` — simple homepage using the default layout
- `pages/` — content pages
- `_layouts/default.html` — minimal HTML layout with a tiny header/nav
- `assets/css/custom.css` — optional custom styles
- `_config.yml` — lean config; no plugins or themes
- `.github/workflows/pages.yml` — GitHub Actions workflow to build and deploy

## Local Preview

```bash
brew install rbenv ruby-build
rbenv install 3.3.0 && rbenv local 3.3.0
eval "$(rbenv init - zsh)"   # load rbenv shims for this session
gem install bundler
bundle install
bundle exec jekyll serve --livereload
```

Open <http://127.0.0.1:4000/modern-agile-manifesto/>.

## Deployment

- Pushing to `main` runs the “Build and Deploy to Pages” workflow.
- Site URL: <https://kll.github.io/modern-agile-manifesto/>
- Relevant `_config.yml` settings in this repo:
  - `url: https://kll.github.io`
  - `baseurl: "/modern-agile-manifesto"`

## Add a Page

Create a Markdown file in `pages/` with front matter and a permalink, then link to it.

`pages/topic.md`:

```markdown
---
layout: default
title: Topic
layout: default
permalink: /topic/
---

Your content here in Markdown.
```

It will publish at <https://kll.github.io/modern-agile-manifesto/topic/>.

Navigation links are hard‑coded in `_layouts/default.html` — update that file to add/remove items in the header.

## Internal Links

Use `{{ "/path/" | relative_url }}` so links work both locally and on Pages (respects `baseurl`).

## License

MIT
