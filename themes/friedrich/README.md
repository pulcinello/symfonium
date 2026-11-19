# friedrich

A dual-identity theme for [Symfonium](https://symfonium.app/) (app version > v12): **indigo
night, green day**. The dark scheme is deep indigo with soft periwinkle accents — quiet,
legible, easy on the eyes at night. The light scheme is a green Material day scheme with deep
green actions, pale green containers, and a teal tertiary. Both live in one file; the app's
Theme mode decides which one you see.

## Preview

| Night | Day |
| ----- | --- |
| ![friedrich in dark mode](screenshots/dark.png) | ![friedrich in light mode](screenshots/light.png) |

## Import

1. Copy `friedrich.json` to your device.
2. In Symfonium: **Settings → Interface → Theme, font and colors**.
3. Under **Default color source**, select **Custom theme**.
4. In the **Custom theme** section, select **Import** and choose `friedrich.json`.

While evaluating the theme, turn off **Now playing color source** / dynamic artwork colors —
they override theme colors on the playback screen.

## Palette

### Night (dark scheme)

| Hex | Role in the theme |
| ------- | ----------------- |
| `#2a2a38` | Darkest tier — bottom sheets, deep wells |
| `#333344` | Base surface (background) |
| `#4a4a60` | Raised fills — top bar, dialogs, active row |
| `#55556a` | Subtle fills — dropdowns, snackbars; search bar & selections |
| `#c9c9d1` | Secondary text |
| `#ffeeee` | Primary text |
| `#aabbdd` | Periwinkle — logo, primary actions, active icons, switches, play-overlay icon, separators |
| `#c3cee6` | Periwinkle (pale) — mix cards |
| `#8fb08a` / `#a3c49d` | Sage — tertiary accents, drag-and-drop controls |
| `#c97a7e` / `#d98f92` | Rose — errors and warnings |

### Day (light scheme)

| Hex | Role in the theme |
| ------- | ----------------- |
| `#f7fbf2` | Base surface (background) |
| `#ffffff` → `#f1f5ec` → `#ebefe7` → `#e5e9e1` → `#e0e4db` | Surface ladder (lowest → highest) |
| `#181d18` / `#424940` | Primary / secondary text |
| `#727970` / `#c1c9be` | Borders / active-row fill |
| `#36693e` | Green (deep) — logo, primary actions, play-overlay icon, separators |
| `#b7f1b9` | Green (pale) — mix cards |
| `#b8ccb5` | Green (mid) — search bar, selected chips, nav pill |
| `#39656c` / `#bdeaf3` | Teal — tertiary accents, drag-and-drop controls |
| `#ba1a1a` / `#ffdad6` | Red — errors and warnings |

### Reserved (unused in both schemes)

| Hex | Family |
| ------- | ------ |
| `#b493b8` / `#c9a9cd` | Mauve |
| `#d0b483` / `#e0c79a` | Gold |

## Role mapping

The two schemes have distinct identities; each role is mapped per scheme.

| Role | Night | Day |
| ---- | ----- | --- |
| `surface` | `#333344` | `#f7fbf2` |
| `surfaceContainerLowest` | `#2a2a38` | `#ffffff` |
| `surfaceContainerLow` | `#333344` | `#f1f5ec` |
| `surfaceContainer` | `#3e3e52` ᵈ | `#ebefe7` |
| `surfaceContainerHigh` | `#4a4a60` | `#e5e9e1` |
| `surfaceContainerHighest` | `#55556a` | `#e0e4db` |
| `surfaceVariant` | `#4a4a60` | `#dde5d9` |
| `onSurface` | `#ffeeee` | `#181d18` |
| `onSurfaceVariant` | `#c9c9d1` | `#424940` |
| `outline` | `#83839c` ᵈ | `#727970` |
| `outlineVariant` | `#4a4a60` | `#c1c9be` |
| `primary` / `onPrimary` | `#aabbdd` / `#333344` | `#36693e` / `#ffffff` |
| `primaryContainer` / `onPrimaryContainer` | `#c3cee6` / `#333344` | `#b7f1b9` / `#1d5128` |
| `secondary` / `onSecondary` | `#aabbdd` / `#333344` | `#36693e` / `#ffffff` |
| `secondaryContainer` / `onSecondaryContainer` | `#55556a` / `#ffeeee` | `#b8ccb5` / `#3a4b3a` |
| `tertiary` / `onTertiary` | `#8fb08a` / `#333344` | `#39656c` / `#ffffff` |
| `tertiaryContainer` / `onTertiaryContainer` | `#a3c49d` / `#333344` | `#bdeaf3` / `#1f4d54` |
| `error` / `onError` | `#c97a7e` / `#1c1c28` ᵈ | `#ba1a1a` / `#ffffff` |
| `errorContainer` / `onErrorContainer` | `#d98f92` / `#333344` | `#ffdad6` / `#93000a` |

ᵈ = derived tone in the night scheme; every other value is a palette value as-is. Two notes:
`secondary`/`onSecondary` carry the **logo color** of each scheme (periwinkle at night, deep
green by day) — the play-overlay triangle always matches the big logo and the mini-player
play button, and stays visible over its scheme's cover scrim. In the day scheme,
`secondaryContainer` additionally sits one step deeper than the standard container tone so the
search bar stays visible against header bands.

## Contrast (WCAG 2.2)

Every text pairing in both schemes passes **AA** (4.5:1) or better; most pass **AAA** (7:1).

| Pairing | Night | Day |
| ------- | ----- | --- |
| `onSurface` / `surface` | 11.02:1 | 16.32:1 |
| `onSurfaceVariant` / `surface` | 7.52:1 | 8.87:1 |
| `onSurface` / `surfaceContainerHighest` | 6.47:1 | 13.27:1 |
| `onPrimary` / `primary` | 6.40:1 | 6.47:1 |
| `onPrimaryContainer` / `primaryContainer` | 7.83:1 | 7.21:1 |
| `onSecondary` / `secondary` | 6.40:1 | 6.47:1 |
| `onSecondaryContainer` / `secondaryContainer` | 6.47:1 | 5.49:1 |
| `onError` / `error` | 5.27:1 | 6.46:1 |
| `onErrorContainer` / `errorContainer` | 4.89:1 | 7.24:1 |

Functional borders (`outline`) meet the 3:1 non-text threshold (3.35:1 night, 4.28:1 day).
Deliberate exceptions: night borders on the highest containers sit at 2.0–2.8:1; the
active-row highlight is intentionally quiet in both schemes (1.44 / 1.62:1) — the playing row
is also identified by playback icons, never by color alone.

## Notes

- The file carries both schemes in Symfonium's compact format (27 color roles); the app's
  Theme mode decides which one applies.
- To share on [Symfonium Styles](https://styles.symfonium.app/), first import the theme and
  re-export it from Symfonium — the catalog requires files exported by the app, plus a name,
  description, and at least one screenshot.
