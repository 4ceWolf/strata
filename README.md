# Strata — a generative depth studio

A single self-contained HTML file. No build, no dependencies, no network. Open it and it runs.

```bash
xdg-open ~/Projects/strata/index.html
# or, if you want it served:
cd ~/Projects/strata && python3 -m http.server 5480   # → http://localhost:5480
```

## What it is

A deterministic generative-art studio. Everything is seeded — the same seed always produces the same piece. Nine engines, six palette systems, and post-processing, with a filmstrip of nearby seeds and a gallery wall to browse.

**Engines** — `Orbs` (depth spheres), `Strata` (layered ridges + haze), `Flow` (flow-field ribbons), `Lattice` (node network), `Radial` (concentric tick rings), `Halftone` (modulated dot grid), `Waves` (interference ripples), `Moiré` (rotated line grids), `Terrain` (perspective wireframe), `Cover` (typographic cover — title/artist with objects occluding the text).

**Palettes** — Spectrum, Monochrome, Duotone, Triad, Ember, Glacier, plus a hue/saturation control.

**Cover text** — Title, Artist and an Objects count. The `Cover` engine draws the text first, then the objects on top, so they occlude it.

**Post** — grain, vignette, and a real bloom pass (blurred additive self-composite).

## Controls

| Key | Action |
| --- | --- |
| `R` | Reroll seed |
| `S` | Save PNG (rendered at 2048×2048) |
| `F` | Fullscreen |
| `G` | Gallery wall (24 pieces, click to open) |
| `Space` | Jump to a random seed |
| `←` / `→` | Step the seed |

The filmstrip under the canvas shows nine nearby seeds — click one to jump to it. **Auto-evolve** advances the seed on a timer.

## Notes

- Deterministic via `mulberry32` + value-noise (`fbm`) seeded from the piece seed.
- No external assets: the "grain" is a procedurally generated noise tile.
- PNG export re-renders at 2048 from the same seed, so exports match the preview.
