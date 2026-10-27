# Layout

Neutral website layout rules distilled from production design-system work. Brand-agnostic.

## Showcase viewports

Always show breakpoints side by side:

| Mode | Showcase width |
|---|---|
| desktop | **1280** |
| tablet | **1080** |
| mobile | **400** |

These are artboard/showcase widths — not the same as CSS media queries. Container **min/max** tokens define the live content range.

## Container contract

1. Outer **section** fills the breakpoint frame.
2. Inner **`container`** uses:
   - horizontal sizing **FILL**
   - bound `Website/min width`
   - bound `Website/max width`
   - content padding from `Website/hor padding` (left/right)
3. Set the **Website** collection mode (`desktop` / `tablet` / `mobile`) on each breakpoint variant so those variables resolve.

```
Breakpoint frame (1280 | 1080 | 400)
  └─ Section (FILL, section/pad/* vertical)
       └─ container (FILL + min/max width + hor padding)
            └─ content
```

## Section vertical padding

Always bind to Website tokens (mode-aware):

| Size | desktop | tablet | mobile | Use |
|---|---|---|---|---|
| **L** | 128 | 96 | 80 | Signature moment only |
| **M** | 96 | 80 | 64 | Default for every section |
| **S** | 64 | 48 | 40 | Strips / compact bands |

## Gaps

Side-by-side splits need an explicit gutter (`itemSpacing`). Prefer at least `spacing/64` on desktop. Do not rely on `SPACE_BETWEEN` alone — columns can collapse.

## Surfaces

Alternate with semantic fills for pacing:

- `background/default`
- `background/subtle`
- `background/inverse`

Keep one job per section. Components come later; this seed only ships the layout specimen on **02 Layout**.
