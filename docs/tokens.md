# Tokens

Figma is the design source of truth. JSON under `tokens/` mirrors the live seed file for docs and future codegen.

## Collections

| Collection | Modes | Purpose |
|---|---|---|
| **Colour** | Default | Gray + status primitives → semantic `background` / `text` / `border` / `status` |
| **Typography** | desktop · tablet · mobile | Font families, font sizes, line heights |
| **Size** | Default | Spacing, radius, stroke |
| **Website** | desktop · tablet · mobile | Container min/max, horizontal padding, section vertical pads |

## Colour

- **Primitives** use broad scopes (`FRAME_FILL`, `SHAPE_FILL`, `TEXT_FILL`, `STROKE_COLOR`) so they can be remapped when theming.
- **Semantics** are aliases with narrow scopes:
  - backgrounds → `FRAME_FILL`, `SHAPE_FILL`
  - text → `TEXT_FILL`
  - borders → `STROKE_COLOR`
  - status accents → `SHAPE_FILL`, `TEXT_FILL`, `STROKE_COLOR`
- Theme a project by changing primitive hex values (or re-aliasing semantics). Do not hard-code brand colours on components.

See [tokens/colour.json](../tokens/colour.json).

## Typography

- `font/family/body` → **Inter** (Copy, Small)
- `font/family/display` → **Source Serif 4** (Heading)
- Text styles bind `fontFamily`, `fontSize`, and `lineHeight` to Typography variables.
- Copy styles use **-0.5px** letter-spacing.

Swap the pairing by editing the two FONT_FAMILY string variables — styles follow automatically.

See [tokens/typography.json](../tokens/typography.json).

## Size

Spacing scale `0…128`, radii `s/m/l/xl`, strokes `subtle/hairline/thick`.

See [tokens/size.json](../tokens/size.json).

## Website

Mode-aware layout tokens for marketing sites. Full contract in [layout.md](layout.md) and [tokens/website.json](../tokens/website.json).
