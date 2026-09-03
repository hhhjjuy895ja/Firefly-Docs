# Immersive Reading

Immersive Reading puts the post detail page into a focus, "PDF-like" reading mode: only the article card stays, centered, plus a persistent table-of-contents rail. The navbar, wallpaper, sidebars, footer, and all other distractions are hidden, with enter/exit controls at the bottom-right.

## Config File

`src/config/siteConfig.ts` → `siteConfig.post.immersiveReading`

## Configuration

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `enable` | `boolean` | `true` | Master switch. Set to `false` to not render the button |
| `defaultOn` | `boolean` | `false` | Whether to enter immersive reading automatically on post pages |
| `tocEnabled` | `boolean` | `true` | Whether the table-of-contents rail is shown in immersive reading |
| `tocPosition` | `"left" \| "right"` | `"left"` | Rail position |

## Usage

- A new "Immersive Reading" button appears at the bottom-right of the post page. Click to enter; click again or press `Esc` to exit and restore the previous scroll position.
- In immersive mode only the article card and the TOC rail (left or right) remain; the navbar, wallpaper, waves, gradient, sidebars, and footer are all hidden. The reading surface is always opaque regardless of wallpaper mode.
- The TOC rail stays open by default. Collapse/expand it via the "TOC toggle" button or the collapse button at the top-right of the rail; collapsing also releases the reserved space for the article.
- Immersive reading is **desktop-only** (viewport ≥ 1024px); the button is not shown on mobile.
- Hovering over the buttons shows a matching tooltip (enter/exit immersive reading, expand/collapse directory).

::: tip
Implementation: logic in `src/utils/immersive-reading-utils.ts`, styles in `src/styles/immersive-reading.css`, trigger button in `src/components/controls/ImmersiveReading.astro`, and the TOC rail in `src/components/controls/ImmersiveTOC.astro`.
:::

## Example

```ts
// src/config/siteConfig.ts
post: {
  immersiveReading: {
    enable: true,
    defaultOn: false,
    tocEnabled: true,
    tocPosition: "left",
  },
},
```
