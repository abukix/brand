# colors

A single family gradient. Three anchor colors. Everything else derives.

## The family gradient

Three hues, evenly spaced around the warm end of the spectrum:

| Token | Hex | 256-color | Terminal ANSI | Where |
|---|---|---|---|---|
| `--accent-purple` | `#a855f7` | `135` | `\033[38;5;135m` | Primary: level markers, wordmark first + fourth letter, headers |
| `--accent-pink` | `#ec4899` | `205` | `\033[38;5;205m` | Secondary: subtitle text, wordmark second + fifth letter, links |
| `--accent-orange` | `#f97316` | `208` | `\033[38;5;208m` | Tertiary: rocket art, wordmark third + sixth letter, warnings |

Reading left-to-right, cycled through the wordmark:

```
   a       b       u       k       i       x
purple   pink   orange   purple   pink   orange
#a855f7  #ec4899  #f97316  #a855f7  #ec4899  #f97316
```

## Support colors

| Token | Hex | Purpose |
|---|---|---|
| `--bg` | `#0a0a0f` | Page background (dark default) |
| `--bg-elevated` | `#141420` | Card / callout background |
| `--ink` | `#fafafa` | Body text |
| `--ink-muted` | `#a1a1aa` | Secondary text, timestamps, metadata |
| `--border` | `#27272a` | Subtle dividers |
| `--success` | `#22c55e` | Nominal / orbit-achieved state |
| `--warn` | `#eab308` | Caution state |
| `--error` | `#ef4444` | Abort / mission-failed state |

## Terminal / bash

The `bootstrap.sh` launch sequence uses these exact ANSI codes:

```bash
PURPLE='\033[38;5;135m'
PINK='\033[38;5;205m'
ORANGE='\033[38;5;208m'
GREEN='\033[38;5;42m'
YELLOW='\033[38;5;220m'
RED='\033[38;5;196m'
```

## Web (Tailwind 4 `@theme`)

In `/root`'s `src/styles/base.css`:

```css
@theme {
  --color-accent-purple: #a855f7;
  --color-accent-pink:   #ec4899;
  --color-accent-orange: #f97316;

  --color-bg:            #0a0a0f;
  --color-bg-elevated:   #141420;
  --color-ink:           #fafafa;
  --color-ink-muted:     #a1a1aa;
  --color-border:        #27272a;
}
```

Generates Tailwind utilities: `bg-accent-purple`, `text-ink-muted`, `border-border`, etc.

## Gradients

The signature `abukix` gradient is a linear left-to-right sweep through the three anchors:

```css
background: linear-gradient(90deg,
  var(--color-accent-purple) 0%,
  var(--color-accent-pink) 50%,
  var(--color-accent-orange) 100%);
```

Use sparingly:
- Section-header underlines
- Wordmark background on marketing surfaces
- Loading progress bars

## What NOT to do

- Do not introduce a fourth anchor color. Three is the identity.
- Do not use the gradient as a full background. It's an accent, not a wallpaper.
- Do not use `--success` (green) for accents. It's reserved for state.
- Do not swap the order. Purple → pink → orange is directional; reversing it looks off.

## References

- [`identity.md`](identity.md): the voice these colors accompany
- [`typography.md`](typography.md): the type these colors color
- [`wordmark/`](wordmark/): the wordmark rendered in gradient
