# Logseq (UI-Enhanced Fork)

> A UI/UX-focused fork of [Logseq](https://github.com/logseq/logseq), the privacy-first, open-source knowledge management platform. This fork applies visual refinements to typography, color, spacing, and interaction design -- all core functionality remains identical to upstream.

## About This Fork

This repository is a fork of [logseq/logseq](https://github.com/logseq/logseq) based on Logseq DB v2.0.1 (commit `0d0d8b7f3`). It replaces Logseq's default Solarized-derived color system and ad-hoc styling with a cohesive, token-based design system inspired by Apple ecosystem applications.

**This fork does not add or remove any features.** Every change is confined to CSS, design tokens, and application icons. No application logic, data model, or plugin API behavior has been modified.

If you are looking for Logseq's core functionality, documentation, or feature requests, please visit the [upstream repository](https://github.com/logseq/logseq).

## What's Different

### 1. Neutral Gray-Blue Color System

Replaces Logseq's Solarized-derived palette (high-saturation cyan/teal hues) with a 12-step neutral gray-blue scale. All hues converge to 213-220 with saturation held between 5-22%, producing colors that appear nearly gray with a subtle cool undertone.

| | Upstream | This Fork |
|---|---------|-----------|
| Light background | `#ffffff` (pure white) | `#fafbfc` / `hsl(214, 12%, 98.5%)` |
| Dark background | `#002b36` (Solarized teal) | `#181a1e` / `hsl(220, 8%, 10.5%)` |
| Light text | `#433f38` (warm brown) | `hsl(210, 10%, 15%)` (cool dark gray) |
| Dark text | `#a4b5b6` (cyan-gray) | `hsl(210, 5%, 78%)` (neutral gray) |
| Link color (light) | `#106ba3` (saturated blue) | `hsl(213, 20%, 42%)` (muted gray-blue) |
| Borders | Fixed hex (`#ccc` / `#0e5263`) | Semi-transparent `rgba()` values that adapt to any background |
| Selection highlight | Opaque `#e4f2ff` | Semi-transparent `hsla(213, 50%, 70%, 0.2)` |

The dark mode completely eliminates the "too green" tint that has been a longstanding point of contention with Logseq's default theme.

### 2. Systematic Design Tokens

Introduces a token-based system covering four dimensions, replacing scattered hardcoded values throughout the CSS:

**Border radius** -- 4 levels:

| Token | Value | Usage |
|-------|-------|-------|
| `--ls-radius-xs` | 4px | Navigation buttons, inline code |
| `--ls-radius-sm` | 6px | Code blocks |
| `--ls-radius-md` | 10px | Modals, cards |
| `--ls-radius-lg` | 14px | Large panels |

**Shadows** -- 5 levels with dual-layer definitions (spread + focus), dark mode automatically increases opacity to compensate for reduced contrast:

| Token | Light mode example |
|-------|--------------------|
| `--ls-shadow-xs` | `0 1px 2px rgba(0,0,0,0.04), 0 1px 1px rgba(0,0,0,0.03)` |
| `--ls-shadow-md` | `0 4px 16px rgba(0,0,0,0.08), 0 2px 4px rgba(0,0,0,0.04)` |
| `--ls-shadow-lg` | `0 8px 32px rgba(0,0,0,0.12), 0 4px 8px rgba(0,0,0,0.06)` |

**Transitions** -- 3 duration tiers with Apple-style easing curves:

| Speed | Duration | Easing |
|-------|----------|--------|
| Fast | 120ms | `cubic-bezier(0.25, 0.1, 0.25, 1.0)` (default) |
| Normal | 200ms | Same, or spring variant for bounce effects |
| Slow | 350ms | `cubic-bezier(0.16, 1, 0.3, 1)` (spatial transitions) |

### 3. Typography Refinements

- **Font stack**: Extended to `Inter, -apple-system, BlinkMacSystemFont, 'SF Pro Text', system-ui, sans-serif` with proper Apple system font fallbacks
- **Rendering**: Subpixel antialiasing (`-webkit-font-smoothing: antialiased`) and `text-rendering: optimizeLegibility` applied globally
- **Heading tracking**: Title letter-spacing tightened to `-0.015em`, a characteristic Apple typography technique for large text

### 4. Interaction Polish

- **Header**: Box shadow replaced with a precise `1px solid` border-bottom, following recent macOS/iOS conventions for layer separation
- **Modal overlay**: Opacity reduced from 70% to 40% for a lighter, less intrusive backdrop
- **Scrollbars**: Background set to fully transparent; only the thumb is visible
- **All hardcoded color values** in component CSS migrated to CSS custom properties for consistent light/dark mode behavior

### 5. Application Icon

Custom icon following Apple Human Interface Guidelines:

- Apple squircle shape (continuous curvature, `rx/ry = 224` on 1024px canvas)
- White gradient background (`#ffffff` to `#f3f3f5`) with top highlight and bottom grounding shadow
- Dark `#1d1d1f` double-bracket `[[ ]]` symbol at 83% scale for proper negative space
- Fine gradient border (`#d4d4d8` to `#b8b8bc`, 1.5px)
- Generated in all platform formats: `.icns` (macOS), `.ico` (Windows), `.png` (Linux/Electron)

## Screenshots

Screenshots comparing upstream and this fork are planned. Check back for before/after comparisons of light mode, dark mode, and component details.

## Upstream Project

This fork is built on [Logseq](https://github.com/logseq/logseq) by the Logseq team. Logseq is a privacy-first, open-source platform for knowledge management and collaboration, with support for both Markdown file graphs and the newer database graph format.

- **Upstream repository**: [github.com/logseq/logseq](https://github.com/logseq/logseq)
- **Official website**: [logseq.com](https://logseq.com)
- **Based on version**: Logseq DB v2.0.1 (commit `0d0d8b7f3`)

If you find this fork useful, please also consider [starring the upstream repository](https://github.com/logseq/logseq) to support the original developers.

## Building from Source

Build steps are identical to the upstream Logseq project. Refer to the upstream guides:

- **macOS / Linux**: [Develop Logseq](https://github.com/logseq/logseq/blob/master/docs/develop-logseq.md)
- **Windows**: [Develop Logseq on Windows](https://github.com/logseq/logseq/blob/master/docs/develop-logseq-on-windows.md)

Quick start:

```bash
# Install dependencies
yarn install

# Start development mode
yarn dev

# Run tests
yarn test
```

## License

This project is licensed under the [GNU Affero General Public License v3.0](LICENSE.md), the same license as the upstream [Logseq](https://github.com/logseq/logseq) project.

Copyright (c) 2020-present Logseq, Inc. and contributors.
UI modifications copyright (c) 2026 Bo.

## Acknowledgments

This fork is built on the work of the [Logseq team](https://github.com/logseq) and its community of contributors. All credit for Logseq's architecture, functionality, and plugin ecosystem belongs to them.

Visual design inspiration drawn from [Apple Human Interface Guidelines](https://developer.apple.com/design/human-interface-guidelines/), [Things 3](https://culturedcode.com/things/), [Bear](https://bear.app/), and [Craft](https://www.craft.do/).
