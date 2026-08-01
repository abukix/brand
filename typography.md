# typography

Two families, one purpose.

## The families

### JetBrains Mono Variable

- **Where:** code blocks, terminal output, the abukix wordmark, module identifiers (`ascent`, `crag`, `vantage`, etc.), any monospaced UI.
- **Why:** distinct code ligatures (`->`, `=>`, `!=`, `>=`), high x-height at small sizes, wide language coverage. Free and open-source (Apache 2.0).
- **Weight range:** 100-800 (variable axis).
- **Get it:** ships with the `bootstrap` script; also available at [jetbrains.com/lp/mono](https://www.jetbrains.com/lp/mono/).

### Inter Variable

- **Where:** body copy, headlines, all sans-serif UI, marketing surfaces.
- **Why:** the modern web-native sans-serif. Excellent hinting at every size, huge weight range, matches Vercel / Linear / GitHub feel.
- **Weight range:** 100-900 (variable axis).
- **Get it:** [rsms.me/inter](https://rsms.me/inter/) or `@fontsource-variable/inter`.

## How they combine

- **Wordmark (`abukix`):** JetBrains Mono, weight 400, letter-cycled through the family gradient.
- **Body:** Inter Variable, weight 400 for prose, 500 for emphasis, 600 for section headers.
- **Inline code:** JetBrains Mono Variable, weight 400. Never mix inline code with bold: the mono treatment is already the emphasis.
- **Terminal + rocket theme (`bootstrap.sh`):** JetBrains Mono, driven by the user's terminal.

## Fallback stack

Both families use OS-native fallback for the sub-second-first-paint window:

```css
font-family:
  'Inter Variable',
  ui-sans-serif,
  system-ui,
  -apple-system,
  BlinkMacSystemFont,
  'Segoe UI',
  Roboto,
  sans-serif;
```

```css
font-family:
  'JetBrains Mono Variable',
  ui-monospace,
  SFMono-Regular,
  Menlo,
  Consolas,
  monospace;
```

The `-apple-system` and `BlinkMacSystemFont` values are the standard web mechanism for rendering in the OS system font on the respective platform. Public CSS, not vendor-locked.

## What NOT to do

- Do not add a third family. Two is the rule.
- Do not use JetBrains Mono for body copy. It's a monospaced font, and long-form reading in mono is fatiguing.
- Do not use Inter for the wordmark. The wordmark is monospaced discipline; that's the identity.
- Do not swap in "similar" fonts. IBM Plex Mono is not JetBrains Mono. Roboto is not Inter.

## References

- [`colors.md`](colors.md): the palette these typefaces sit on
- [`identity.md`](identity.md): the voice these typefaces set
- [`wordmark/`](wordmark/): the wordmark rendered
