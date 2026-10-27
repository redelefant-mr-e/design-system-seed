# Design System Seed

Neutral Figma foundations for new website design projects — typography, colour, size, and breakpoint layout — packaged so Cursor can spawn a fresh project and (optionally) a new Figma file.

**Live Figma file:** [Design System Seed](https://www.figma.com/design/LppbB3PEX7sB8zdKwHdIEE/Design-System-Seed)

## What’s in the seed

| Layer | Contents |
|---|---|
| **Colour** | Gray + status primitives → semantic `background` / `text` / `border` / `status` |
| **Typography** | Inter (body) + Source Serif 4 (display) as FONT_FAMILY variables; responsive type scale |
| **Size** | Spacing, radius, stroke |
| **Website** | Modes `desktop` / `tablet` / `mobile` — min/max width, hor padding, section pads |
| **Pages** | Cover · Foundations specimens · Layout container contract (1280 · 1080 · 400) |

Marketing components are **out of scope** for v1. Follow [docs/layout.md](docs/layout.md) when you add them later.

## Theme a project

1. Change primitive hex values in Colour (or re-point semantic aliases).
2. Change `font/family/body` and `font/family/display` — text styles follow.
3. Keep semantic names stable so components stay portable.

## Docs

- [docs/tokens.md](docs/tokens.md) — inventory and scopes
- [docs/layout.md](docs/layout.md) — breakpoints and container contract
- [docs/figma-recipe.md](docs/figma-recipe.md) — Plugin API steps to recreate the file
- [tokens/](tokens/) — portable JSON mirrors of Figma values

## Spawn a new project (Cursor skill)

Install the personal skill `design-system-seed` (`~/.cursor/skills/design-system-seed`). When you ask for a new website design project:

1. Creates a local folder (+ `git init`; GitHub via `gh` when asked)
2. Copies these docs/tokens into the project
3. If no Figma file is given: `whoami` → `create_new_file` → applies [docs/figma-recipe.md](docs/figma-recipe.md)
4. Writes `info.txt` with the new Figma URL
5. Stops at foundations (no invented brand or components)

## Provenance

Structure and layout contract distilled from Hybrid Solutions production Figma work, with brand values removed.
