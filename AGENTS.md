# Project: Personal Website (Jekyll + GitHub Pages)

## Status
Site is scaffolded and deployed via GitHub Actions to armangb1.github.io.
`_data/profile.yml` still has `[TODO]` placeholders (bio, GPA values). The
Projects/Achievements collections are empty; placeholder entries and
TEMPLATE.md schemas exist only locally (gitignored, not deployed).

## Stack
- Jekyll, built via GitHub Actions, deployed to GitHub Pages
- Plain CSS, no JS framework
- Collections: _projects, _achievements
- Personal info lives in _data/profile.yml — never hardcode bio/contact info in templates

## Commands
- Local dev server: `bundle exec jekyll serve` (serve at http://localhost:4000)
- Build (matches CI): `bundle exec jekyll build`
- Gemfile pins `github-pages ~> 232`; commit `Gemfile.lock` for reproducible builds.
  Dependencies install locally via `bundle config set --local path vendor/bundle`
  (vendor/ and .bundle/ are gitignored).

## Adding content
New project entry: add `_projects/<slug>.md` with frontmatter
`title`, `description` (card summary), `date` (YYYY-MM-DD, controls sort order),
`tech` (list of tags), optional `link`/`image`/`tags`. The `layout` is applied
automatically by _config.yml defaults — do not set it. Same schema for
`_achievements/<slug>.md` (with `date` and optional `category`).
Local reference: `_projects/TEMPLATE.md` and `_achievements/TEMPLATE.md` are
gitignored (kept on disk as a starting point only).
- Do not touch _layouts/ or _includes/ when just adding content
- Collection dirs are not tracked by git when empty; create them when adding the
  first entry.

## Gotchas
- `exclude` in _config.yml replaces Jekyll's defaults, so keep the full list
  (vendor/, Gemfile*, AGENTS.md, TEMPLATE.md) or build output leaks files.
- `.gitignore` excludes TEMPLATE.md and placeholder-* entries so they never ship.
- github-pages' default plugins auto-publish any frontmatter-less root file
  (AGENTS.md). That is why it is excluded.
- No `_posts/` directory — no blog/notes section, static pages only.
- baseurl is "" (username.github.io). If this repo is served under a project path,
  set `baseurl: "/<repo-name>"` in _config.yml.

## Design conventions
- Card-based, modern portfolio aesthetic
- Primary accent #2b6cb0; accent soft #ebf0f7; text #1e293b; muted #64748b
- Mobile-first, responsive

## Constraints
- Default username.github.io URL, no custom domain
- Keep dependencies minimal; must build cleanly on GitHub Actions
