# Filter FabJS — Filter Author Technique Index

**Reference corpus:** 52 online filters · native JSON v2 · library registry version 12 · snapshot 2026-11-05

**Pinned source:** [`anthonychimming/filter-fabjs-library`](https://github.com/anthonychimming/filter-fabjs-library/tree/2690dd83e904bc9e89e5e69b63388fc01f83156b) at commit `2690dd83e904bc9e89e5e69b63388fc01f83156b`. Each listed filter is published revision 2.

**Companion file:** [`FILTER_AUTHOR_REFERENCE_LIBRARY.json`](./FILTER_AUTHOR_REFERENCE_LIBRARY.json). It preserves complete native `definition` objects (four RGBA formulas, all controls and UI metadata, descriptions, tags, IDs, author and format fields), with separate technique annotations and source blob SHA.

> **Authoring note:** This is an example index, not an alternative syntax reference. Follow the application’s current `docs/FORMULA_REFERENCE.md`, parser/type checks and `WGSLCompiler.analyze()`; the corpus has not been runtime-parsed or render-tested in this extraction.

## How to use this index

1. Pick the **mathematical mechanism** closest to the requested effect, not just a similar-looking filter name.
2. Look up the filter’s `id` in the companion JSON and inspect `annotations.construction`, `annotations.authoringLesson`, `annotations.keyFunctions`, `definition.formulas` and `definition.controls`.
3. Recombine the techniques into an original filter; retain native float semantics, explicit control ranges, predictable alpha handling, and deterministic stateless functions where possible.
4. Validate the four expressions and controls with the shipping parser/IR, check CPU/WebGPU eligibility, then visually render representative source images and edge cases.

## Technique catalogue

### Image processing and detail (8)

| Filter | Mathematical construction | Useful functions |
|---|---|---|
| [Chromatic Neon Contour](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/chromatic-neon-contour.json) (`chromatic-neon-contour`) | Extracts contours from short- and long-radius source differences, then offsets and brightens channels. | `src()` |
| [Dynamic Contrast — Photographic Detail](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/dynamic-contrast-photographic-detail.json) (`dynamic-contrast-photographic-detail`) | Combines fine, medium and broader image-neighbourhood contrasts into a tonal detail treatment. | `cnv()`, `smoothstep()`, `srcLinear()` |
| [Editorial Ink — Cinematic Colour](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/editorial-ink-cinematic-colour.json) (`editorial-ink-cinematic-colour`) | Simplifies photograph tone planes, then adds selective black contours and ink shadow masses. | `cnv()`, `fract()`, `hash2()`, `smoothstep()` |
| [Levels / Midtone](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/levels-midtone.json) (`levels-midtone`) | Maps source channels through black/white endpoints and a normalized midtone bias curve. | `bias()`, `scl()`, `step()` |
| [Photoshop-Style Black and White](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/photoshop-black-and-white.json) (`photoshop-black-and-white`) | Converts source hues to grayscale using six colour-family luminance contributions. | `val()` |
| [Photoshop-Style Emboss](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/photoshop-emboss.json) (`photoshop-emboss`) | Uses two offset image samples to approximate a directional relief gradient around mid-gray. | `r2x()`, `r2y()`, `srcLinear()` |
| [Photoshop Style Exposure](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/photoshop-exposure.json) (`photoshop-exposure`) | Applies photographic exposure gain, offset and gamma correction in a bounded working domain. | `pow()` |
| [Photoshop Style Vibrance](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/photoshop-vibrance.json) (`photoshop-vibrance`) | Adjusts saturation selectively according to colourfulness and source-colour protection. | `smoothstep()`, `wrap()` |

### Colour grading and film (13)

| Filter | Mathematical construction | Useful functions |
|---|---|---|
| [Lomo CN 400 — Film Scan](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/lomo-cn400-film-scan.json) (`lomo-cn400-film-scan`) | Grades luminance-dependent colour saturation with controlled highlight/shadow response and fine grain. | `hash2()`, `smoothstep()`, `sqr()`, `valueNoise()` |
| [LomoChrome Color 92](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/lomochrome-color-92-balanced.json) (`lomochrome-color-92-balanced`) | Combines film colour biases, soft tonal compression, subtle image smoothing and fine grain. | `cnv()`, `gradient4()`, `hash2()`, `smoothstep()` |
| [LomoChrome Metropolis 100-400](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/lomochrome-metropolis-100-400.json) (`lomochrome-metropolis-100-400`) | Compresses saturation and highlights while preserving selective reds and cool shadow tint. | `hash2()`, `smoothstep()` |
| [LomoChrome Purple XR](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/lomochrome-purple-xr-spectrum-v2.json) (`lomochrome-purple-xr-spectrum-v2`) | Remaps selected foliage, sky, yellow and pink colour families to a false-colour film palette. | `gradient4()`, `hash2()`, `smoothstep()`, `valueNoise()` |
| [LomoChrome Turquoise 100-400](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/lomochrome-turquoise-100-400.json) (`lomochrome-turquoise-100-400`) | Produces hue-family false-colour shifts including warm-to-blue and cyan-to-warm remapping. | `hash2()`, `smoothstep()` |
| [Moon](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/moon-instagram-inspired.json) (`moon-instagram-inspired`) | Constructs monochrome film treatment with layered contrast, brightness, soft-light and shadow floor. | `sqrt()` |
| [Organic Film-Gate Leak](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/organic-film-gate-leak.json) (`organic-film-gate-leak`) | Synthesizes a warm edge-entering exposure gradient disturbed by seeded low-frequency fields. | `fbm()`, `gradient4()`, `hash2()`, `screen()` |
| [Complementary Split Toning](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/preset-13394d49-9343-4dbd-9e8a-7a3b0a8af922.json) (`preset-13394d49-9343-4dbd-9e8a-7a3b0a8af922`) | Uses complementary hue relationships and smooth tonal masks for split toning. | `cos()`, `smoothstep()` |
| [Pseudo Thermal Imaging](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/pseudo-thermal-imaging.json) (`pseudo-thermal-imaging`) | Converts windowed source luminance into a segmented or continuous false-colour thermal ramp. | `bias()`, `gradient4()`, `hash2()`, `smoothstep()` |
| [Redscale XR 120](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/redscale-xr-120.json) (`redscale-xr-120`) | Uses warm film-emulsion colour curves with selective cool recovery and seeded grain. | `gradient4()`, `hash2()`, `valueNoise()` |
| [Silver Gelatin Noir](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/silver-gelatin-noir.json) (`silver-gelatin-noir`) | Builds monochrome photographic toe, shoulder, tonal contrast and radial lens falloff. | `hash2()`, `perlin()`, `smoothstep()` |
| [Synthwave Signal - Neon Chromatic Grade](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/synthwave-signal-neon-chromatic-grade.json) (`synthwave-signal-neon-chromatic-grade`) | Grading through dual palette ramps with bandwise signal displacement and RGB detail offsets. | `cos()`, `gradient4()`, `hash2()`, `srcLinear()` |
| [Valencia](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/valencia-instagram-inspired.json) (`valencia-instagram-inspired`) | Layers a warm photo grade, vintage fade and contrast response. | `val()`, `ctl()` |

### Distortion, refraction and glitch (9)

| Filter | Mathematical construction | Useful functions |
|---|---|---|
| [Contrast Channel Offset](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/contrast-channel-offset.json) (`contrast-channel-offset`) | Detects local edges and conditionally applies channel-specific shift, invert or dropout. | `r2x()`, `r2y()`, `smoothstep()`, `src()` |
| [Kinetic Lines](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/kineticlines.json) (`kineticlines`) | Warps sampled source pixels along one axis using directionally oriented sine waves and source luminance. | `r2x()`, `r2y()`, `sin()`, `srcLinear()` |
| [Lens Distortion](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/lens-distortion.json) (`lens-distortion`) | Performs aspect-correct radial coordinate remapping with bilinear sampling and adjustable centre. | `sqr()`, `sqrt()`, `srcLinear()` |
| [Parametric Slice Glitch](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/parametric-slice-glitch.json) (`parametric-slice-glitch`) | Uses deterministic rectangular regions to displace source samples along a rotated axis. | `hash2()`, `r2x()`, `r2y()`, `srcWrap()` |
| [Pixel Melt](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/pixel-melt-original-colour.json) (`pixel-melt-original-colour`) | Pulls bright source regions into displaced strips with directional tails and staggered lane variation. | `hash2()`, `r2x()`, `r2y()`, `repeat()` |
| [Digital Block Glitch](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/preset-1e3c440b-225f-4591-ac39-04382389084b.json) (`preset-1e3c440b-225f-4591-ac39-04382389084b`) | Offsets source RGB samples using deterministic block-level hashes. | `hash2()`, `srcWrap()` |
| [Julia Fractal Displacement](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/preset-48af1931-c4ee-4515-a4cf-434e7e7a0f67.json) (`preset-48af1931-c4ee-4515-a4cf-434e7e7a0f67`) | Uses Julia escape fields as two displacement maps for source RGBA pixels. | `julia()`, `r2x()`, `r2y()`, `sin()` |
| [Rippled Glass Refraction](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/rippled-glass-refraction.json) (`rippled-glass-refraction`) | Offsets bilinear source samples using layered directional ripples and smooth drift noise. | `r2x()`, `r2y()`, `sin()`, `srcLinear()` |
| [Turbulent Displace](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/turbulent-displace.json) (`turbulent-displace`) | Displaces X and Y sample positions with two decorrelated low-frequency noise fields. | `srcLinear()`, `valueNoise()` |

### Halftone, print and engraving (7)

| Filter | Mathematical construction | Useful functions |
|---|---|---|
| [Carved Shadow Crosshatch](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/carved-shadow-crosshatch-v3.json) (`carved-shadow-crosshatch-v3`) | Builds tone-responsive directional hatch layers, ink shadow masses and transition-local gouge marks. | `fract()`, `hash2()`, `r2x()`, `r2y()` |
| [Chromatic Overprint — Two-Ink Press](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/chromatic-overprint-two-ink-press.json) (`chromatic-overprint-two-ink-press`) | Models two ink plates with halftone dot cells, registration offsets, paper grain and shadow reserves. | `bias()`, `circle()`, `hash2()`, `repeat()` |
| [Chromatic Signal Weave](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/chromatic-signal-weave.json) (`chromatic-signal-weave`) | Builds a repeating module sequence with staggered stripe tracks and palette ramps. | `gradient3()`, `gradient4()`, `hash2()`, `repeat()` |
| [Contour Flow Halftone](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/contour-flow-halftone.json) (`contour-flow-halftone`) | Displaces regular line phase with smoothed input luminance while tonal value controls ink width. | `fract()`, `r2x()`, `r2y()`, `smoothstep()` |
| [Ordered Dither Mono Pixel](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/gpu-ordered-dither-mono-pixel.json) (`gpu-ordered-dither-mono-pixel`) | Dithers pixelated luminance against an 8×8 Bayer ordered threshold field. | `src()` |
| [Scanline Engraving](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/scanline-engraving.json) (`scanline-engraving`) | Varies monochrome scanline width with luminance, with deterministic roughness and paper gaps. | `hash2()`, `repeat()` |
| [Wavy Halftone Lines](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/wavy-halftone-lines.json) (`wavy-halftone-lines`) | Uses smooth procedural wave phase and source luminance to vary black stripe thickness. | `fract()`, `perlin()`, `r2x()`, `r2y()` |

### Geometry, grids and patterns (8)

| Filter | Mathematical construction | Useful functions |
|---|---|---|
| [Concentric Circles](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/concentric-circles.json) (`concentric-circles`) | Uses periodic radial distance to create variable-width ring and gap bands. | `c2m()`, `repeat()`, `smoothstep()` |
| [Fragmented Photo Weave](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/fragmented-photo-weave.json) (`fragmented-photo-weave`) | Remaps staggered horizontal and vertical photo strips with tile-local displacement and fold highlights. | `checker()`, `fract()`, `grid()`, `hash2()` |
| [Mondrian Modular Grid](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/mondrian_modular_grid.json) (`mondrian_modular_grid`) | Builds a staged rectangular subdivision and partial T-junction grid with palette-controlled fills. | `fract()`, `hash2()`, `line()` |
| [Neon Flow Contours](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/neon-flow-contours.json) (`neon-flow-contours`) | Generates op-art ribbon bands by bending periodic stripes with layered sine waves. | `fract()`, `sin()`, `smoothstep()` |
| [Polka Dot Pattern](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/polka-dot-pattern.json) (`polka-dot-pattern`) | Builds a repeating two-colour dot array with controllable row stagger. | `circle()`, `repeat()` |
| [Red-Black Diagonal Plaid](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/preset-639acccc-8c0e-4233-b815-89c2eef9826d.json) (`preset-639acccc-8c0e-4233-b815-89c2eef9826d`) | Composes a red-black plaid grid with diagonal hatch regions and phase controls. | `cos()`, `fract()`, `repeat()`, `sin()` |
| [Tension Mesh](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/tension-mesh-grid.json) (`tension-mesh-grid`) | Bends a monochrome grid by seeded, smooth localized folds and pinch/spread fields. | `cos()`, `grid()`, `hash2()`, `radialGrad()` |
| [Tension Mesh - Chroma Checker](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/tension-mesh-rgb-checker.json) (`tension-mesh-rgb-checker`) | Deforms an analytic checker lattice using seeded folds and warp-dependent RGB misregistration. | `cos()`, `hash2()`, `radialGrad()`, `sin()` |

### Noise, fractals and procedural fields (2)

| Filter | Mathematical construction | Useful functions |
|---|---|---|
| [Nebula Starfield](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/nebula-starfield.json) (`nebula-starfield`) | Layers FBM, warped noise, ridged cloud structure, radial voids and deterministic stars. | `circle()`, `fbm()`, `gradient4()`, `hash2()` |
| [Difference Clouds](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/preset-082775b4-ab2c-43f2-9d99-5eaca56a8bd3.json) (`preset-082775b4-ab2c-43f2-9d99-5eaca56a8bd3`) | Generates smooth FBM clouds and difference-blends them with source channels. | `difference()`, `fbm()` |

### Mosaics and pixelation (5)

| Filter | Mathematical construction | Useful functions |
|---|---|---|
| [Adaptive Rounded Mosaic](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/adaptive-rounded-mosaic.json) (`adaptive-rounded-mosaic`) | Adaptive rounded-square cells subdivide where sampled local detail is high. | `hash2()`, `sdfBox()`, `sdfFill()`, `src()` |
| [Amiga Extra Half-Brite](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/amiga-ehb-32-plus-32.json) (`amiga-ehb-32-plus-32`) | Maps source imagery into a constrained RGB12 palette with a separate half-bright decision and dithering. | `hash2()`, `src()` |
| [Organic Low-Poly Facets](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/organic-low-poly-facets.json) (`organic-low-poly-facets`) | Builds a piecewise-linear triangular mesh with shared vertices and source-derived facet colours. | `fract()`, `hash2()`, `r2x()`, `r2y()` |
| [Photoshop-Style Crystallize](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/photoshop-crystallize.json) (`photoshop-crystallize`) | Maps pixels to irregular Voronoi cells and samples the source near feature points. | `sqr()`, `src()`, `worleyF1()` |
| [Studded Brick Mosaic](https://github.com/anthonychimming/filter-fabjs-library/blob/2690dd83e904bc9e89e5e69b63388fc01f83156b/source/studded-brick-mosaic.json) (`studded-brick-mosaic`) | Pixelates source colours into beveled square tiles with seams and raised stud masks. | `circle()`, `grid()`, `r2x()`, `r2y()` |

## Reusable technique patterns

| Need | Start with | Adaptation rule |
|---|---|---|
| Coherent source warping | `lens-distortion`, `rippled-glass-refraction`, `turbulent-displace` | Transform sample coordinates and preserve alpha with RGB |
| Structure-preserving procedural geometry | `organic-low-poly-facets`, `tension-mesh-grid`, `mondrian_modular_grid` | Build shared coordinate or subdivision rules before colour fills |
| Source-reactive print lines | `scanline-engraving`, `contour-flow-halftone`, `wavy-halftone-lines` | Keep line phase, image-derived tone response and ink coverage separate |
| Colour-family grading | `lomochrome-purple-xr-spectrum-v2`, `lomochrome-turquoise-100-400`, `photoshop-vibrance` | Gate remaps by source hue/chroma and tonal range |
| Bounded deterministic detail | `nebula-starfield`, `preset-082775b4-ab2c-43f2-9d99-5eaca56a8bd3` | Choose periodic/seamless noise where tiling is required; avoid sequential RNG for GPU work |
| Constrained image simplification | `gpu-ordered-dither-mono-pixel`, `amiga-ehb-32-plus-32`, `photoshop-crystallize` | Separate cell layout, tonal/palette quantization and dithering |
| Local contrast/detail | `dynamic-contrast-photographic-detail`, `chromatic-neon-contour`, `photoshop-emboss` | Specify sample radius, edge behaviour and highlight/shadow protection |
| Multi-field displacement | `preset-48af1931-c4ee-4515-a4cf-434e7e7a0f67`, `parametric-slice-glitch` | Bound expensive fractal iterations; prefer deterministic fragment fields |

## Engine and control reminders

- A native filter has four formulas, one each for R/G/B/A. Native channels and raw controls operate on `0..255`; noise, masks and normalized coordinate functions use other ranges.
- Controls are canonical `0..255` values even when the UI displays an authored range via `val(index, min, max)` and `controls[].ui` metadata. A filter may use up to ten controls.
- Preserve `a` when alpha should be unchanged. Spatial remapping normally needs the same geometry for alpha as for the colour channels.
- The current native formula reference marks `pow()`, `rnd()`, `rst()`, `get()`, `put()`, bitwise operations and legacy integer constructs as CPU-only. In particular, `photoshop-exposure` uses `pow()`; do not assume every online filter is GPU-compatible.
- Identical channel-independent expensive procedural calls may share GPU execution under the documented constraints; this is not guaranteed for guarded or channel-dependent expressions.
- **Source availability is not correctness certification.** Only the real parser, typed IR, capability analyzer and render tests can establish runnable output and parity.

## Source integrity and coverage

- Indexed 52 distinct filter IDs from the pinned registry; 52 are revision 2.
- Each complete `definition` is carried without formulas or controls being rewritten; entries include original source blob SHAs and pinned source links.
- The index uses **one primary category per filter** to avoid duplicate entries. Source `tags` and multiple `annotations.techniques` provide cross-category discovery.
- `annotations` are added authoring guidance. They are not original filter metadata and should not be fed to the application’s single-filter importer.

