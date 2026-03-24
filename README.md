# Boone County Search & Rescue

Website for [Boone County Search & Rescue](https://boonecosar.org/), a 501(c)(3) nonprofit volunteer organization serving Boone County and central Iowa. Founded in the 1960s, the team provides technical rescue services including water rescue and recovery, rope rescue, swiftwater rescue, and ground search operations.

## Tech Stack

- [Hugo](https://gohugo.io/) — static site generator (v0.87.0+)
- [Blowfish](https://blowfish.page/) — Hugo theme (git submodule)

## Getting Started

### Prerequisites

- [Hugo](https://gohugo.io/installation/) v0.87.0 or later

### Setup

```bash
# Clone with submodules
git clone --recurse-submodules https://github.com/ethanharstad/BooneCoSAR.git
cd BooneCoSAR

# If already cloned without submodules
git submodule update --init --recursive
```

### Development

```bash
# Start the local dev server
hugo server

# Build for production
hugo
```

The site will be available at `http://localhost:1313/`.

## Adding Content

### New Blog Post

```bash
hugo new posts/2025/my-post-slug/index.md
```

Place any images in the same directory as the post's `index.md`. Posts use YAML front matter:

```yaml
---
title: Post Title
date: 2025-01-15
categories:
- Training
capabilities:
- Water Rescue
---
```

### Content Sections

| Section | Path | Description |
|---------|------|-------------|
| Posts | `content/posts/` | Blog posts organized by year |
| Capabilities | `content/capabilities/` | Rescue capability categories |
| Apparatus | `content/apparatus/` | Vehicles and equipment |
| Members | `content/members/` | Team leadership |
| Support | `content/support/` | Donors and supporters |
| About | `content/about/` | Organization history |

## Configuration

Site configuration lives in `config/_default/`:

| File | Purpose |
|------|---------|
| `hugo.toml` | Base URL, taxonomies, outputs, pagination |
| `params.toml` | Theme appearance, features, layout options |
| `menus.en.toml` | Navigation menu structure |
| `languages.en.toml` | Language settings |
| `markup.toml` | Markdown rendering options |

## Contact

- Seth McCrea — <smccrea@boonecounty.iowa.gov>
- Chris Hayes — <chayes@boonecounty.iowa.gov>
- [Facebook](https://www.facebook.com/profile.php?id=100057368750076)
