# CLAUDE.md

Website for the Capítulo Estudiantil UD de Acolfísica (student chapter), published on GitHub Pages.

## Stack

- Static site in plain HTML and CSS. No frameworks, build tools or dependencies.
- JavaScript lives only in `js/i18n.js`, and only to switch between Spanish and English.

## Internationalization

- Translatable elements use the `data-i18n` attribute.
- Translations live in `lang/es.json` and `lang/en.json`.
- Spanish is the default language and is written directly in the HTML; English is loaded from `lang/en.json`.

## Conventions

- Always use relative paths. Never start a path with `/`: the repository will be transferred to the chapter's GitHub organization, which changes the site's base URL.
- Write code comments, commit messages and documentation in English.
