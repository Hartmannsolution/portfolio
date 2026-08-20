# README_START

## Purpose

This document records the initial setup changes made to ensure the homepage renders your own content from `content/project.md`, and to add a subpages section with links.

## Changes Made

### 1) Homepage now renders `content/project.md`

- Updated homepage layout setting from `profile` to `custom`.
- File changed: `config/_default/params.toml`
- Change:
  - `[homepage].layout = "custom"`

Why:
- Blowfish's default `profile` homepage does not render the content from `content/project.md`.
- The `custom` layout allows us to inject a partial that explicitly loads that page.

### 2) Added custom homepage partial

- New file: `layouts/partials/home/custom.html`

What it does:
- Loads the page at `/project` using Hugo's page lookup.
- Renders the page title and full content on the site homepage.
- Shows a small fallback message if `content/project.md` does not exist.

### 3) Prepared `content/project.md` as a publishable content page

- Updated file: `content/project.md`

Changes:
- Added TOML front matter:
  - `title = "Project"`
  - `date = 2026-08-20`
  - `draft = false`
- Replaced placeholder outline with structured markdown sections.
- Added links to subpages:
  - `/subpages/subpage-one/`
  - `/subpages/subpage-two/`

### 4) Added a subpages folder with linked pages

- New folder: `content/subpages/`
- New files:
  - `content/subpages/_index.md`
  - `content/subpages/subpage-one.md`
  - `content/subpages/subpage-two.md`

What these provide:
- A section landing page (`_index.md`) for subpages.
- Two example subpages with content and backlinks to `/project/`.

### 5) Added menu links

- Updated file: `config/_default/menus.en.toml`

Added main menu entries:
- `Project` -> `pageRef = "project"`
- `Subpages` -> `pageRef = "subpages"`

Why:
- Provides top navigation access to the main project page and subpages section.

## Resulting Behavior

- Homepage (`/`) now renders the content from `content/project.md` through the custom Blowfish homepage partial.
- Header navigation includes:
  - Project
  - Subpages
- Subpages section is available at `/subpages/` with two linked child pages.

## Notes

- If you change the filename or path of `content/project.md`, update `layouts/partials/home/custom.html` accordingly.
- You can add more subpages by creating additional files under `content/subpages/`.
