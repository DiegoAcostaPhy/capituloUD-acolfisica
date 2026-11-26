# CLAUDE.md

Read `BRIEF.md` before working on the site: it describes the pages, content and visual identity.

Website for the Capítulo Estudiantil UD de Acolfísica (student chapter), published on GitHub Pages.

## Stack

- Static site in plain HTML and CSS. No frameworks, build tools or dependencies.
- JavaScript is allowed only in `js/i18n.js` (language switch) and `js/theme.js` (light/dark theme switch).

## Styles

- Colors come only from `css/palette.css`. In `styles.css`, use its semantic tokens (`--color-*`), never hard-coded hex values.
- Load `palette.css` before `styles.css`.
- Logos in `assets/img/logos` are white: always place them on a dark or brand-gradient background.

## Internationalization

- Translatable elements use the `data-i18n` attribute.
- Translations live in `lang/es.json` and `lang/en.json`.
- Spanish is the default language and is written directly in the HTML; English is loaded from `lang/en.json`.

## Conventions

- Always use relative paths. Never start a path with `/`: the repository will be transferred to the chapter's GitHub organization, which changes the site's base URL.
- Write code comments, commit messages and documentation in English.
