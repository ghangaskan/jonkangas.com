# Bible Reading Tracker Builder

A self-contained HTML tool for building and printing a 66-book, 1,189-chapter Bible reading tracker.

## Publish
Upload these files to the same web folder:

- `index.html` — the builder and source code
- `readme.md` — maintainer notes
- `help.md` — short user help
- `LICENSE` — full GPLv3 text for downloadable/distributed copies

No server code, framework, database, package manager, or CDN is required.

The Help drawer links directly to `index.html`, `readme.md`, and `help.md`. Its GPL link points to the official GNU page: https://www.gnu.org/licenses/gpl-3.0.html

## Current language packs
The builder includes UI text and 66-book names for:

- English (`en`)
- Spanish (`es`)
- Simplified Chinese (`zh`)
- Hindi (`hi`)
- French (`fr`)
- Arabic (`ar`)
- Bengali (`bn`)
- Portuguese (`pt`)
- Russian (`ru`)
- Urdu (`ur`)

Arabic and Urdu UI controls use right-to-left direction. The printable chapter grid remains left-to-right so the layout engine stays predictable. Book titles can still render right-to-left.

Translations are first-pass language packs. Native-speaker review is recommended before describing them as editorially final.

## Architecture

The file is deliberately one page, but the JavaScript is organized by responsibility:

1. **Data** — canonical books, languages, paper sizes, presets.
2. **Configuration** — defaults, migration, local save, import/export, share links.
3. **Book layout** — title measurement and chapter-row geometry.
4. **Book flow** — measure whole books and assign contiguous books to columns. Books never split.
5. **Rendering** — build books, text boxes, and page DOM.
6. **Printing** — calculate physical paper fit separately from screen preview zoom.
7. **Builder UI** — Configure and Help drawers, controls, sliders, row maps, and selected-book overrides.

The Help drawer is built into the page and follows the UI language.

A `MAINTAINER MAP` is also embedded in the HTML above the main JavaScript functions. Every named function has a short `Purpose:` comment.

## Bug-finding guide

- Wrong saved value: configuration or UI binding.
- Wrong chapter layout inside one book: layout engine.
- Wrong book in a column: book measurement / book flow.
- Screen right, print wrong: print sizing.
- Book title overlaps chapters: title measurement / first-row start.
- Language label missing: `UI_TEXT` pack; missing UI keys fall back to English.
- Wrong translated book name: `LANGUAGES` pack; canonical chapter counts are separate.

## Compatibility

The current storage key is versioned. v1.1 reads v1.1, v1.0, and supported earlier saved configurations and normalizes them to the current structure.

## v1.1 additions

- Configurable special chapter marks for any book/chapter.
- Open-center Unicode mark presets suitable for checking off by hand.
- Per-mark size, opacity, show-number, and vertical optical nudge controls.
- Positive vertical nudge moves the mark up; control range is -4 to +4 px.
- Preset optical nudges for the included symbols.
- Section row-start tools are visually separated from special chapter marks.

Shared links and exported JSON should be treated as public configuration data. Do not put private information in a tracker config if the link or file will be shared.

## Release checklist

- Open with a clean browser profile.
- Test English plus at least one long-title language.
- Test Arabic or Urdu direction.
- Confirm 66 books and 1,189 chapter boxes.
- Test Letter and A4/Legal print preview.
- Test auto-balanced columns.
- Test one per-book row-map override.
- Export and re-import a config.
- Open a copied share link.
- Review non-English wording with native speakers when possible.

## Licensing

Bible Reading Tracker Builder is released under the **GNU General Public License v3.0 or later (GPL-3.0-or-later)**.

The source includes an SPDX identifier, copyright notice, no-warranty notice, and a link to the official GNU GPL page:
https://www.gnu.org/licenses/gpl-3.0.html

For downloadable or redistributed copies, keep the included `LICENSE` file with the program.
