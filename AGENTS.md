# Project: Personal Website (Jekyll + GitHub Pages)

## Status
Repo is an empty scaffold — no Jekyll files exist yet. The sections below are
the intended structure/conventions; follow them when scaffolding or adding content.

## Purpose
Professional personal-brand site for job and university applications.
Audience: recruiters, hiring managers, admissions committees.

## Stack
- Jekyll, built via GitHub Actions, deployed to GitHub Pages
- Plain CSS, no JS framework
- Collections: _projects, _achievements
- Personal info lives in _data/profile.yml — never hardcode bio/contact info in templates

## Adding content
- New project: add a file to _projects/ following the frontmatter schema in
  _projects/TEMPLATE.md
- New achievement: same pattern in _achievements/
- Do not touch _layouts/ or _includes/ when just adding content

## Design conventions
- Card-based, modern portfolio aesthetic
- Mobile-first, responsive

## Constraints
- Default username.github.io URL, no custom domain
- No blog/notes section — static pages only
- Keep dependencies minimal; must build cleanly on GitHub Actions
