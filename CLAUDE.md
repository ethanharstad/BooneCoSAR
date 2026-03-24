# CLAUDE.md - BooneCoSAR

## Project Overview

Static website for **Boone County Search & Rescue**, a volunteer SAR organization serving Boone County and central Iowa. Built with [Hugo](https://gohugo.io/) using the [Blowfish](https://blowfish.page/) theme.

**Live site:** https://boonecosar.org/

## Tech Stack

- **Static site generator:** Hugo (minimum v0.87.0)
- **Theme:** Blowfish (git submodule at `themes/blowfish`)
- **Content format:** Markdown with YAML front matter
- **Configuration:** TOML files in `config/_default/`

## Repository Structure

```
config/_default/       # Hugo configuration (TOML)
  hugo.toml            # Main site config (base URL, taxonomies, outputs)
  params.toml          # Theme parameters (appearance, features, layout)
  menus.en.toml        # Navigation menu structure
  languages.en.toml    # Language settings
  markup.toml          # Markdown rendering options
  module.toml          # Hugo version requirement
  taxonomies.toml      # Custom taxonomy definitions
content/               # All site content (Markdown)
  posts/               # Blog posts, organized by year (2024/, 2025/)
  apparatus/           # Rescue vehicles and equipment
  capabilities/        # Rescue capability categories
  members/             # Team leadership info
  support/             # Donors and supporters
  about/               # Organization history
assets/                # Site assets (logo.png)
static/                # Favicons, web manifest
themes/blowfish/       # Theme (git submodule - do not edit directly)
archetypes/            # Content templates for `hugo new`
```

## Build & Development

```bash
# Run local dev server
hugo server

# Build for production (output goes to /public/)
hugo

# Create a new post
hugo new posts/2025/my-post-slug/index.md
```

There is no CI/CD pipeline, test suite, or linter configured.

## Content Conventions

### Blog Posts

Posts live in `content/posts/<year>/<slug>/index.md` with images alongside in the same directory.

**Front matter format (YAML):**
```yaml
---
title: Post Title Here
date: 2025-01-15
categories:
- Training          # or: Incident, Community, Equipment, Award
capabilities:
- Water Rescue      # optional, links to capability taxonomy
---
```

- Slugs use kebab-case (e.g., `rope-rescue-introduction`)
- Images are referenced by filename relative to the post directory
- Image syntax: `![alt text](filename.jpg "Caption text")`
- Emoji usage in content is acceptable (Hugo `enableEmoji = true`)
- Drafts: set `draft: true` in front matter to hide from production

### Section Pages

Each content section uses `_index.md` for the section landing page with individual items in subdirectories.

### Taxonomies

- `tags`, `categories`, `authors`, `series` (standard)
- `capabilities` (custom) — maps posts to rescue capability types

## Configuration Notes

- **Theme customization** goes in `config/_default/params.toml`, not by editing theme files
- **Navigation menu** is defined in `config/_default/menus.en.toml`
- **Dark mode** is the default appearance
- **Search** is enabled (JSON output configured)
- **Unsafe HTML** is allowed in Markdown (`markup.toml` → `unsafe = true`)
- The Blowfish theme is a **git submodule** — update it with `git submodule update --remote`

## Key Gotchas

- Do not edit files under `themes/blowfish/` directly — changes will be lost on submodule updates
- The `/public/` directory is gitignored — it is the build output
- The archetype template uses TOML front matter (`+++`) but existing posts use YAML (`---`); follow the YAML convention for consistency
- The default branch on the remote is `main`
