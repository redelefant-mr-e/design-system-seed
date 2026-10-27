# Figma recipe

Plugin-API oriented steps the Cursor skill follows when spawning a new foundations file. Load `figma-use` (and `figma-generate-library` for foundations) before every `use_figma` call. Load `figma-create-new-file` before `create_new_file`.

## 0. Create file

1. `whoami` → pick a plan with Full seat → `planKey`
2. `create_new_file` with `fileName`, `planKey`, `editorType: "design"`
3. `create_session` with returned `file_key`
4. Reuse `sessionId` on subsequent file tools

## 1. Variable collections

Create in order:

### Colour (`Default` mode)

1. Primitive colors (gray scale, white/black, accent, status) with broad scopes.
2. Semantic aliases (`background/*`, `text/*`, `border/*`, `status/*`) with narrow scopes.
3. Opacity floats (`opacity/disabled`, `opacity/overlay`).

Values: [tokens/colour.json](../tokens/colour.json).

### Size (`Default` mode)

Spacing `0…128`, `radius/*`, `stroke/*`. Values: [tokens/size.json](../tokens/size.json).

### Typography (modes: `desktop`, `tablet`, `mobile`)

1. `font/family/body` = Inter, `font/family/display` = Source Serif 4 (`FONT_FAMILY`).
2. `size/*` and `line-height/*` floats per mode.
3. Verify fonts with `figma.listAvailableFontsAsync()` before binding. Source Serif 4 styles use `SemiBold` / `ExtraBold` (no space); Inter uses `Semi Bold` / `Extra Bold`.

Values: [tokens/typography.json](../tokens/typography.json).

### Website (modes: `desktop`, `tablet`, `mobile`)

`min width`, `max width`, `hor padding`, `section/pad/L|M|S`. Values: [tokens/website.json](../tokens/website.json).

**Always set `variable.scopes` explicitly** — never leave `ALL_SCOPES`.

## 2. Text styles

Create Heading (display font), Copy, and Small styles. Bind each to:

- `fontFamily` → body or display var
- `fontSize` → matching size var
- `lineHeight` → matching line-height var

Copy letter-spacing: `-0.5` px.

## 3. Pages

| Page | Content |
|---|---|
| **Cover** | Seed name, how to theme (swap primitives / font vars) |
| **01 Foundations** | Colour swatches, type specimens, spacing/radius |
| **02 Layout** | Three frames 1280 / 1080 / 400 with Website mode set; section + container contract |

One `use_figma` call per page (set `currentPage` once). Append to auto-layout **before** setting `layoutSizing* = 'FILL'`.

## 4. Stop

Foundations only. Do not invent brand colours or marketing components unless the user asks. Write the Figma URL into the project `info.txt` / README.
