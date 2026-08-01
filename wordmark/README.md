# wordmark

The `abukix` wordmark rendered in SVG.

## Files

*(SVG files port in v0.1.1. This directory is a placeholder pending the actual wordmark authoring pass.)*

Planned files:

| File | Purpose |
|---|---|
| `abukix-gradient.svg` | Primary wordmark, letter-cycled through the family gradient |
| `abukix-mono.svg` | Monochrome variant, for single-color contexts (dark ink on light bg, or vice versa) |
| `abukix-og.svg` | Open Graph preview image (1200×630) |
| `abukix-mark-gradient.svg` | The `▲` mark alone, gradient-filled: avatar / hero use (spec below) |
| `abukix-favicon.svg` | The `▲` mark alone, flat purple: favicon / small-size / terminal use |
| `abukix-avatar.png` | 1024×1024 raster export of `abukix-mark-gradient.svg`, dark bg: social profile pictures (X, LinkedIn, GitHub, Instagram, YouTube, TikTok, Threads) |
| `abukix-favicon.png` | 32×32 and 64×64 raster exports of `abukix-favicon.svg`, transparent bg: site favicons |

## Rendering rules

### 1. Letter-cycle the gradient

The wordmark is `abukix` in JetBrains Mono, weight 400. Each letter takes one of the three anchor colors, cycled:

```
   a       b       u       k       i       x
purple   pink   orange   purple   pink   orange
```

See [`colors.md`](colors.md) for the exact hex values.

### 2. Never bold, never italic

The wordmark is one weight, one style. Weight 400 regular. Never bold. Never italic. Never underlined.

### 3. Minimum clear space

Minimum clear space around the wordmark equals the height of the letter `x` (the wordmark's own x-height). No text, logo, or graphic inside that margin.

### 4. Minimum size

- Screen: 96px wide minimum.
- Print: 24mm wide minimum.

Below these sizes, use the `▲` mark alone (favicon variant).

### 5. Background

- Prefer dark backgrounds (`--bg` = `#0a0a0f`). The gradient reads best on dark.
- On light backgrounds, use the mono variant (dark ink), not the gradient variant.

### 6. What NOT to do

- Do not recolor. The gradient is the identity.
- Do not skew, rotate, distort, or add drop-shadows.
- Do not add outlines.
- Do not composite with other logos in a way that implies partnership.
- Do not put the wordmark on a photograph or busy background.

## The `▲` mark

The triangle character (`▲`) is the standalone mark, the one icon used everywhere a full wordmark doesn't fit. It appears:
- As the favicon (32×32, single color)
- As level markers in `bootstrap.sh` output
- Above the rocket art in the launch sequence
- As the avatar mark (spec below): the standalone icon spec for `github.com/abukix`, all seven social accounts, and every site favicon

Always purple (`#a855f7`) when used as a level marker. On the rocket art and the avatar mark it cycles through the gradient (see `bootstrap.sh` line ~68).

### Mark geometry

- A single upward-pointing equilateral triangle, drawn as a clean vector path, not the literal Unicode `▲` glyph.
- Centered in a square canvas. The triangle occupies roughly the middle 60% of canvas width, leaving ~20% clear space on each side.
- The padding is deliberate: most social platforms (X, LinkedIn, GitHub) crop avatars into a circle. The triangle must clear that crop without touching the edge.

### Mark color: gradient variant (avatar / hero use)

Linear gradient, top-left to bottom-right (135°), three stops: same gradient as every other mark in the family (module icons, `root`'s banner `id="mark"` gradient):

```css
background: linear-gradient(135deg,
  var(--color-accent-purple) 0%,
  var(--color-accent-pink) 50%,
  var(--color-accent-orange) 100%);
```

### Mark color: monochrome variant (favicon / small sizes / terminal)

Flat `#a855f7` (purple only), per the level-marker rule above. Use below 96px, matching wordmark rule 4.

### Mark background

- Dark canvas (`--bg` = `#0a0a0f`), rounded corners at ~15% of canvas size, matching the `rx="10"` convention on existing 64×64 module icons.
- Also produce a transparent-background variant: a dark square on a dark page (GitHub's dark theme, X's dark mode) reads as a hole without one.

### Mark: what NOT to do

- Do not composite the mark with any other shape. No hexagons, no circuit motifs, no cube clusters. This is the one icon.
- Everything in wordmark rule 6 (no skew, no rotation, no distortion, no drop-shadows, no outlines) applies to the mark too.

## Repo logos (README headers)

Every repo in the `abukix` umbrella (`abukix`, `basecamp`, `brand`, `homelab`, `learnix`, `root`, `bootstrap`) uses the same small, centered logo in its `README.md` header. No wide banners, no per-repo taglines baked into the image itself.

**Pattern:** `<reponame>` in JetBrains Mono, weight 400, fill is the same continuous `id="brand"` diagonal gradient (`135deg`, purple 0% → pink 50% → orange 100%) already used on `basecamp`'s and `root`'s big display text and every module icon, not discrete per-letter colors. Plain text, no cursor block, no trailing punctuation.

**Canvas:** dark background (`--bg` = `#0a0a0f`), rounded corners (`rx="24"`), height `150`, width sized to the name (`60px` left padding + `~34px` per character + `60px` right padding).

**File location:** `assets/banner.svg` for repos that already used that filename (`abukix`, `basecamp`, `root`, `learnix`, kept for compatibility with existing references), `assets/logo.svg` for repos that didn't have one yet (`brand`, `homelab`, `bootstrap`).

**What NOT to do:**
- Do not add a tagline, description, or second color scheme inside the logo itself. That content lives in the README's prose below it, not the image.
- Do not use discrete letter-cycling colors for repo logos. That treatment is reserved for the literal `abukix` wordmark (see above). Repo logos use the continuous gradient sweep instead, to match what's already shipped on `basecamp`/`root`.
- `root`'s logo displays as `/root` (matching its brand name everywhere else in prose), not the literal repo folder name `root`. Every other repo's logo matches its repo name exactly.

## References

- [`typography.md`](typography.md): JetBrains Mono, the wordmark's typeface
- [`colors.md`](colors.md): the gradient the wordmark carries
- [`identity.md`](identity.md): the discipline the wordmark represents
