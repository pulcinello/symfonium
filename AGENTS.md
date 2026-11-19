# AGENTS.md — symfonium

Custom themes and icon sets for [Symfonium](https://symfonium.app/), an Android music player.

## What this repo contains

- **Custom themes**: JSON color themes for Symfonium's interface.
- **Icon sets**: custom icons for Symfonium's interface elements.

## Target app version

We target the **latest Symfonium app (version > v12)**. String templates must use the
**v12 template syntax** (the currently documented one) — pre-v12 template syntax is not
applicable.

## Key domain knowledge

### Custom themes

- Themes are JSON files setting individual colors throughout the UI, imported via
  **Settings → Interface → Theme, font and colors → Default color source: Custom theme → Import**.
- Color roles follow **Material Design 3** naming. A practical authoring workflow:
  [Material Theme Builder](https://material-foundation.github.io/material-theme-builder/)
  → export **Material Theme (JSON)** → import into Symfonium → optionally re-export from
  Symfonium for a smaller Symfonium-native theme file.
- Some roles have specific uses in Symfonium that differ from their generic Material
  Design meaning — check the
  [theme color mapping](https://docs.symfonium.app/wiki/other/theme-colors-documentation/)
  when adjusting colors.
- Themes can also be created/edited in-app (RGB/HSL per role) and renamed, exported, or
  deleted from the theme management dialog.
- [Symfonium Styles](https://styles.symfonium.app/) is the moderated sharing catalog.
  When importing a theme from it, use the downloaded JSON **without editing its contents**.
  Uploading a theme requires a clear name, description, and at least one screenshot.

### String templates (v12)

Used for Now Playing strings and album/artist subtitles. Full reference:
[custom string template v12](https://docs.symfonium.app/wiki/other/symfonium-custom-string-template-v12/).
Essentials:

- `%field%` placeholder; empty/missing field → nothing shown. `%lb%` = line break
  (`\n` only inside `{ ... }` blocks).
- `{ ... }` conditional block: shown only if its **first** placeholder matches (a
  non-empty field or a true `%|condition%`). Put required spaces inside the block,
  e.g. `{ by %artist%}`.
- Conditions: `%field|cond%` with operators `==`, `!=`, `+=` (contains), `-=`
  (not contains), `>`, `<`, `==empty`, `!=empty`, `bpm[]"0".."100"` (inclusive range).
  Combine with `&&` / `||` and parentheses. Literals in quotes; `empty` is reserved.
  Unquoted `track` means the field, `"track"` the literal text.
- Inline formatting markup: `**Bold**`, `__Underline__`, `~~Strike~~`, `//Italics//`,
  `^^CAPS^^`.
- Localized labels via `string.*` placeholders, e.g. `%string.hires%`, `%string.lossless%`,
  `%string.hires.lossless%`, `%string.track.one%`.
- Now Playing extras: `\t` splits a template into aligned segments (left/center/right),
  `\o` applies a selective protection overlay, `next.*` refers to the next queue item
  (e.g. `%next.title%`, `%next.chapter.title%`), `chapter.*` / `chapter.all.*` fields for
  audiobooks, and `bool1`..`bool5` toggleables bindable to custom-string toggle actions.
- Field lists differ per context (Now Playing, album subtitle, artist subtitle) — use
  only fields valid for the context the template lives in.

### Configurable interface (context)

Nearly everything in the UI is configurable in-app: home top icon/shortcuts/overview
rows, library shortcuts, bottom tabs, now playing styles and dynamic (artwork) colors,
list styles and column counts. All colors come from themes. Feature requests belong on
the [Symfonium forum](https://support.symfonium.app/c/feature-requests/8).

## Official docs

- [Configurable interface](https://docs.symfonium.app/wiki/other/symfonium-configurable-interface/)
- [Custom themes](https://docs.symfonium.app/wiki/other/symfonium-custom-themes/)
- [Theme colors documentation](https://docs.symfonium.app/wiki/other/theme-colors-documentation/) (color role → interface mapping)
- [Custom string template v12](https://docs.symfonium.app/wiki/other/symfonium-custom-string-template-v12/)
- [Symfonium Styles](https://styles.symfonium.app/) (theme/icon sharing catalog)

## Agent skills

### Issue tracker

Issues and specs are tracked as GitHub issues in `pulcinello/symfonium` via the `gh` CLI. See `docs/agents/issue-tracker.md`.

### Triage labels

Default five-role vocabulary: `needs-triage`, `needs-info`, `ready-for-agent`, `ready-for-human`, `wontfix`. See `docs/agents/triage-labels.md`.

### Domain docs

Single-context: `GLOSSARY.md` at the repo root, ADRs in `docs/adr/`. See `docs/agents/domain.md`.
