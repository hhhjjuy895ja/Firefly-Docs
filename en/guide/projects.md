# Projects

Manage your personal projects via the content collection `src/content/projects/`. Each project is a `.md` / `.mdx` file whose **body is the project README**, rendered at the bottom of the detail page; the frontmatter fields drive the list card and the top of the detail page.

## Creating a Project

Create a `.md` or `.mdx` file under `src/content/projects/`.

- List page `/projects/`: card grid with status filter + name/description/tag search.
- Detail page `/projects/<slug>/`: cover (click to zoom via lightbox), status badge, project name, description, date/tags, external-link buttons, and the README body below.

## Frontmatter Fields

| Field | Type | Description |
|-------|------|-------------|
| `title` | `string` | Required. Project name. |
| `slug` | string | Optional, used just like an article. |
| `published` | `date` | Required. Publish/update date, e.g. `2025-10-01`. Used for sorting (with `order`). |
| `draft` | `boolean` | Optional, default `false`. Hides the page in production builds when `true`. |
| `order` | `number` | Optional. Manual sort weight, **higher sorts first**; falls back to `published` descending. |
| `description` | `string` | Optional. Card summary + detail description. |
| `image` | `string` | Optional. Cover. Supports full URL, public-root `/images/xxx.png`, and a relative path (relative to this file, e.g. `images/xxx.png`); hidden if empty. |
| `tags` | `string[]` | Optional. Tags. |
| `link` | `array` | Optional. External-link buttons: `{ label, icon, value }`. `icon` may be an astro-icon name (e.g. `fa7-brands:github`), an image URL, or left empty to use the first letter of `label`. |
| `status` | `string` | Optional. Project status, using a standard key (see below). |
| `lang` | `string` | Optional. Page language, e.g. `zh_CN`. |

## Status Keys (`status`)

`status` uses **standard keys**; the frontend shows a localized label and applies a per-status color + icon:

| key | Meaning |
|-----|---------|
| `planning` | Planning |
| `developing` | In Development |
| `published` | Published |
| `archived` | Archived |

Unknown or custom strings are shown as-is (neutral gray) and are excluded from the list page status filter.

## Example

````yaml
---
title: "Firefly"
slug: firefly
published: 2025-10-01
draft: false
order: 100
description: "A feature-rich open-source blog theme."
image: "images/firefly.avif"
status: "published"
tags:
  - Astro
  - Svelte
link:
  - label: "GitHub"
    icon: "fa7-brands:github"
    value: "https://github.com/CuteLeaf/Firefly"
  - label: "Docs"
    icon: "material-symbols:menu-book"
    value: "https://docs-firefly.cuteleaf.cn"
lang: ""
---

# Firefly

Firefly is a personal blog theme built on Astro and the Fuwari template.
````

## Sorting / Filter / Search

- **Sorting**: `order` descending (higher first) → `published` descending → title tiebreaker.
- **Status filter**: the list page header offers "All / each status" pills that filter by `status`.
- **Search**: the list page search box filters instantly by name, description, and tags, combined with the status filter.
