# Project brief: Capítulo Estudiantil UD de Acolfísica website

This file describes what the website must contain and how it should look.
Both agents (Gemini in Antigravity and Claude Code) must read it before working on the site.
Items marked **TBD** are still to be defined; use placeholders for them.

## 1. Why this site exists

The chapter is joining the **International Association of Physics Students (IAPS)**.
The IAPS application form asks for the chapter's website, so having one is a requirement.

**Current goal:** a complete skeleton of the whole site. Every page and section exists,
with placeholder content where real content is missing, and the language switch and the
light/dark theme switch work. Real content will be filled in later.

## 2. About the chapter

- **Name:** Capítulo Estudiantil UD de Acolfísica (student chapter of Universidad Distrital Francisco José de Caldas).
- **Parent organization:** Acolfísica, the Colombian Association of Physical Sciences (Asociación Colombiana de Ciencias Físicas). The chapter runs activities at Universidad Distrital on Acolfísica's behalf.
- **Founded:** July 4, 2025.
- **Governance:** the chapter has statutes that define its positions and how people are elected to them.
- **Board:** President, Vice President, Secretary, Treasurer.
- **Departments** (each with a Coordinator, a Vice Coordinator and a list of members):

  | Spanish name | English name |
  | --- | --- |
  | Departamento de Divulgación Científica | Science Outreach Department |
  | Departamento Académico | Academic Department |
  | Departamento de Proyección Profesional | Professional Development Department |
  | Departamento de Política Científica | Science Policy Department |

- Each department organizes its own events, designs their flyers and publishes them on social media.
- **Social media:** Instagram [@capitudestudiantil](https://www.instagram.com/capitudestudiantil/) (confirmed). Facebook, X (Twitter) and YouTube also exist; their URLs are **TBD**.

## 3. Pages (site map)

All pages share the same header (logo, navigation, language switch, theme switch) and footer
(social links, contact, logos of the chapter, Acolfísica and Universidad Distrital).
Keep all pages as flat files in the repository root.

| File | Page | Content |
| --- | --- | --- |
| `index.html` | Home | Hero with chapter name and tagline; short "who we are"; cards linking to the four departments; latest events; call to action to join |
| `about.html` | About us | Mission, vision, short history (founded July 4, 2025), relationship with Acolfísica, IAPS membership, link to the statutes (PDF in `assets/docs/`) |
| `team.html` | Team | Board first, then each department with its coordinator, vice coordinator and members. One profile card per person |
| `departments.html` | Departments | Overview of the four departments, each linking to its own page |
| `department-outreach.html` | Science Outreach | Description, coordinators, members, events organized by this department |
| `department-academic.html` | Academic | Same structure |
| `department-professional.html` | Professional Development | Same structure |
| `department-policy.html` | Science Policy | Same structure |
| `events.html` | Events | All past and upcoming events, newest first, each with its flyer, title, date, place, organizing department and description |
| `join.html` | Join us | Short text on how to join, plus the chapter's Google Form embedded in the page (iframe), so it can be filled in without leaving the site |

### Profile card (team member)

Photo, full name, role (position or "Member"), department, program (e.g. Physics, Physics Teaching),
optional short bio and optional links. Use placeholder photos and names for now.
Real data will come from the chapter's member list; only people who agree will be published.

### Event card

Flyer image (portrait, roughly 4:5, as published on Instagram), title, date, place,
organizing department (shown as a tag that links to the department page), short description,
and an optional link to the Instagram post or recording.
Department pages show only their own events.

### How event images are organized

Each department has its own folder for event flyers:

```text
assets/img/events/
├── outreach/
├── academic/
├── professional/
└── policy/
```

File names: `YYYY-MM-DD-short-name.jpg`, lowercase, no spaces or accents
(e.g. `2025-11-12-velandia-black-holes.jpg`). The folder tells which department organized the event;
the date in the name orders events. When new flyers are added, an agent creates the matching event card
on `events.html` and on the department page.

### Placeholder events for the skeleton

Use these real past events as sample content (dates and departments to be confirmed):

| Event | Speaker | Notes |
| --- | --- | --- |
| Talk: "Movimiento de partículas con espín alrededor de un agujero negro en un halo de materia oscura" | Padre Nelson Velandia, SJ, PhD in Physics | Universidad ECCI, Crisanto Luque building, November 12 |
| Call for student talks: "Tu trabajo merece audiencia" | — | Physics students share their thesis projects |
| Student talk series: "La Física se pone en escena" | e.g. Zaudí Gómez, "El rol del efecto Casimir como modelo físico para la organización de membranas lipídicas" | Talks by students about their research |
| Talk series "Hablemos de Física", second talk: "Experiencia en el lanzamiento de Artemis II desde el Centro Espacial Kennedy" | Mauricio Medina Montañez, astronomer, Planetario Yawa (Cali) | With Rato Astronómico; April 22 |
| Debate contest "Ley Nuclear Colombiana" (forum "Átomos para la vida") | — | Hybrid, May 20; organized with Acolfísica and other groups |
| Film forum: "Brazil" | — | Cine foro |

## 4. Languages

- Spanish is the default language and is written directly in the HTML.
- English translations live in `lang/en.json`; `lang/es.json` mirrors the Spanish text.
- Every visible text uses a `data-i18n` key. A button in the header switches ES/EN and remembers the choice (localStorage).
- Department names, page titles, buttons and the footer must all be translated.

## 5. Visual identity

The chapter has no formal color palette yet, but its flyers share a clear style. The site must follow it.

**What the flyers look like:**

- Deep space backgrounds: dark navy and indigo, with stars or particle dust.
- Gradients from indigo to violet and purple, with magenta/pink highlights; some flyers add teal/cyan.
- White text on dark backgrounds.
- Titles in an elegant serif typeface (in capitals); names and dates in a bold geometric sans-serif.
- Logos always present: the chapter logo (a unicorn with the bra-ket ⟨φ|φ⟩), the Acolfísica logo (multicolor "ACol física") and the Universidad Distrital crest.

**What the site must do:**

- **The three logos are white.** They must always sit on a dark or colored background (deep navy, indigo or violet), never on white. In both themes the header and footer use a dark violet/navy background so the logos are visible.
- **Light theme by default:** white page background, with the flyers' colors used for the header, footer, accents, links, buttons and tags.
- **Dark theme as an option:** deep navy background, inspired by the flyers. A switch in the header changes theme and remembers the choice; the first visit follows the system preference.
- **The color palette is already defined in `css/palette.css`**, sampled from the flyers: four scales (`violet`, `indigo`, `teal`, `space`, steps 50–950), a brand gradient for header/footer/hero, and semantic tokens (`--color-bg`, `--color-text`, `--color-link`, `--color-primary`, `--color-accent`, …) for the light theme and for `[data-theme="dark"]`. Always use the semantic tokens in `styles.css`; never hard-code hex colors. All text/background pairs in the tokens meet WCAG AA.
- Load `css/palette.css` before `css/styles.css` on every page.
- Fonts: a serif for headings and a sans-serif for body text. Google Fonts are allowed.
- Space or particle motifs can be used as subtle backgrounds (e.g. the hero), never behind long text.
- Must work well on mobile phones; most visitors arrive from Instagram.

## 6. Technical rules

- Static site: HTML and CSS, no frameworks or build tools. Published with GitHub Pages from `main`.
- JavaScript only for the language switch (`js/i18n.js`) and the theme switch (`js/theme.js`).
- Relative paths only, never starting with `/`: the repository will be transferred to the chapter's GitHub organization.
- Images in `assets/img/`: `logos/` (white logos of the chapter, Acolfísica and Universidad Distrital), `team/` (member photos), `events/<department>/` (flyers). PDFs in `assets/docs/`.
- Code comments, commit messages and documentation in English.

## 7. Reference

- Layout reference: https://udpuj.github.io/simposio-centenario-schr-dinger/ (navy header with logos, horizontal navigation, language button, Google Form embedded in the registration page).

## 8. Still to define (TBD)

- URLs for Facebook, X and YouTube, and a contact email.
- Mission and vision: the texts exist; use placeholder text until they are added.
- Which department organized each event, and the exact dates (flyers will be added to the department folders).
- The Google Form embed link for `join.html`.
- Member data and consent for publishing names and photos.
- Confirmation that the Acolfísica and Universidad Distrital logos may be used on the site.
