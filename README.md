# Markuxt Template

A Markdown-first **research institute / lab website** template, built with [Nuxt 3](https://nuxt.com/) and [@markuxt/markuxt](https://github.com/markuxt/markuxt).

Clone this template to spin up a multilingual (English / 简体中文) site for your lab in minutes — members, publications, projects, positions, and news, all authored in Markdown.

> **Get started:** Click the green **Use this template** button at the top of this repository on GitHub, then follow the Quick Start below.

---

## Features

- **Markdown-first content** — add members, news, publications, projects, and positions as `.md` files
- **Multilingual** — English and Simplified Chinese out of the box (extensible)
- **Configurable navigation & member categories** — define header/footer nav and the member groups entirely in `nuxt.config.ts`
- **Rich Markdown** — Mermaid diagrams and LaTeX/KaTeX math render natively
- **Co-located assets** — images/videos live next to their Markdown
- **Themeable** — the Seaside palette is plain CSS custom properties; override tokens in `styles/_tokens.css`
- **Static deployment** — `pnpm generate` → deploy to GitHub Pages or any static host

## Tech Stack

- [Nuxt 3](https://nuxt.com/) + TypeScript
- [@markuxt/markuxt](https://github.com/markuxt/markuxt) — provides layouts, pages, components, and content transformers
- [@nuxt/content](https://content.nuxt.com/) v2 — Markdown content management
- [@nuxtjs/i18n](https://i18n.nuxtjs.org/) — internationalization
- [@icon-park/vue-next](https://github.com/bytedance/IconPark) — UI icons

## Quick Start

> **Prerequisites:** Node.js 20+ and [pnpm](https://pnpm.io/).
>
> `@markuxt/markuxt` is published to the GitHub npm registry. Your local/CI environment must be able to authenticate to `npm.pkg.github.com` (a `GITHUB_TOKEN` with `read:packages` is enough).

```bash
# 1. After creating a repo from this template, clone it:
git clone https://github.com/<you>/<your-repo>.git
cd <your-repo>

# 2. Install dependencies
pnpm install

# 3. Start the dev server
pnpm dev
```

Open <http://localhost:3000>. Every content section ships with a visible, commented **demo** — a Demo Member, a Welcome news post, a Demo Project, a Demo Publication, and a Demo Position — so each page renders out of the box. Use them as worked examples, then replace them with your own content.

## Project Structure

```bash
├── plugins/
│   └── icons.ts             # Global icon component registration
├── src/
│   ├── i18n/                # UI string translations (en.json, zh-CN.json)
│   ├── members/             # Team member profiles (Markdown)
│   ├── news/                # News articles (Markdown)
│   ├── positions/           # Open positions (Markdown)
│   ├── projects/            # Projects (Markdown)
│   ├── publications/        # Publications (Markdown)
│   └── public/images/       # Static images (logo, carousel, favicon)
├── styles/                  # Design tokens + main stylesheet (overrideable)
├── nuxt.config.ts           # Site configuration (see below)
└── package.json
```

## Customizing Your Site

Almost everything site-specific lives in two places: **`nuxt.config.ts`** (structure/config) and **`src/i18n/*.json`** (text). The codebase is full of `TODO:` comments marking placeholders — search for them to find everything to replace.

### 1. Brand text & UI strings — `src/i18n/`

Replace placeholder values in `en.json` and `zh-CN.json`:

```jsonc
"site.title": "Your Lab Name - Your University",   // → your real title
"nav.brand": "Your Lab Name",                      // → your lab name
"footer.director": "Dr. Your Name",                // → your director
```

> **Keep all keys** — they are the markuxt contract. Change values only, in both locale files.

### 2. Site config — `nuxt.config.ts`

```ts
appConfig: {
  markuxt: {
    logo: { src: '/images/logo.png' },            // → your logo
    navigation: [ /* header/footer links + route guard */ ],
    contact: {
      email: 'contact@your-lab.edu',               // → your email
      externalUrl: 'https://your-university.edu',  // → your institution
    },
    carousel: { images: [ /* your photos */ ] },
    researchAreas: [ /* homepage feature cards */ ],
    members: {
      // Define your member groups here — there are no built-in defaults.
      categories: [
        { key: 'staff', labelKey: 'members.staff' },
        { key: 'research-students', labelKey: 'members.researchStudents' },
        { key: 'research-assistants', labelKey: 'members.researchAssistants' },
        { key: 'alumni', labelKey: 'members.alumni' },
      ],
    },
  },
}
```

This template uses the **Seaside** palette. The look is driven entirely by CSS custom properties — override colors, fonts, and spacing in `styles/_tokens.css` (and site-level tweaks in `styles/_theme.css`). Other palettes (Forest, Sunset, Slate) are separate template repositories, not a config flag.

### 3. Images — `src/public/images/`

Replace the placeholders with your own:

- `logo.png` — default logo + demo avatar placeholder
- `team.jpg` — default carousel image
- `favicon.png` — site favicon
- `default.jpg` — legacy placeholder (no longer referenced by default)

Reference them as `/images/<file>` (e.g. `/images/your-logo.png`).

### 4. Fine-tune design tokens — `styles/_tokens.css`

You can override colors, fonts, spacing, and other tokens directly:

```css
:root {
  --color-primary: #0a2540;
  --font-display: 'Fraunces', serif;
  /* ... */
}
```

### 5. Content — `src/`

Add Markdown files under the matching directory. Each directory has a `readme.md` documenting its frontmatter and a commented **demo** file as a worked example. Schemas are in **Feature reference** below; see **[CONTRIBUTING.md](CONTRIBUTING.md)** for the full content guide.

---

## Feature reference

### Content types

All content is authored as Markdown with YAML frontmatter, one file per item. Each directory under `src/` has a hidden `readme.md` documenting its full schema and a visible demo file.

| Directory                 | Type                  | Listing page                      | Detail page                  |
|---------------------------|-----------------------|-----------------------------------|------------------------------|
| `src/members/<category>/` | Team profiles         | `/members`                        | `/members/<category>/<name>` |
| `src/news/`               | News / announcements  | `/news`                           | `/news/<slug>`               |
| `src/publications/`       | Papers                | `/publications` (grouped by year) | `/publications/<slug>`       |
| `src/projects/`           | Projects              | `/projects`                       | `/projects/<slug>`           |
| `src/positions/`          | Open positions        | `/positions`                      | `/positions/<slug>`          |

#### **Member**

```yaml
---
name: Jane Doe            # Required — display name
role: Assistant Professor # Optional — shown on the card
title: PhD                # Optional — academic title
email: jane@your-lab.edu  # Optional
scholar: https://scholar.google.com/... # Optional — profile URL
orcid: 0000-0000-0000-0000              # Optional
image: assets/jane.webp   # Optional — co-located photo or /images/...
category: staff           # Required — must match a configured category (see below)
order: 1                  # Optional — sort within category (lower = earlier)
interests: [Robotics, Control Theory]   # Optional — shown as chips
---
```

#### **News**

```yaml
---
title: Launching our new website   # Required
date: 2025-06-01                   # Required — drives ordering
tags: [announcement, website]      # Optional
description: A short summary       # Optional — used in lists/previews
---
```

#### **Publication**

```yaml
---
title: Decentralized Swarm Coordination # Required
authors:                                 # Required — "LastName, FirstName"
  - Doe, John
authors_orcid:                           # Optional — parallel to authors; null = none
  - 0000-0000-0000-0000                  # Matches a member's `orcid` → cross-links them
year: 2025                               # Required — listing groups by year
doi: https://doi.org/10.1000/...         # Optional
venue: IEEE Transactions on Robotics     # Optional
keywords: [control systems, UAV]         # Optional
abstract_screenshot: doe2025.png         # Optional — abstract screenshot next to the .md
---
```

#### **Project**

```yaml
---
title: Autonomous Drone Swarm     # Required
description: One-line summary      # Optional
status: ongoing                   # Optional — open | ongoing | completed | maintained
year: 2025                        # Optional
image: assets/cover.webp          # Optional
funded: true                      # Optional — shows a "Funded" badge
---
```

#### **Position**

```yaml
---
title: PhD Positions in Robotics  # Required
description: Short summary         # Optional
type: Students                     # Optional — free-form audience label
year: 2025                         # Optional
requirements:                      # Optional — bullet list
  - Strong background in control theory
email: phd@your-lab.edu           # Optional — application contact
---
```

### Configurable navigation

The `navigation` array controls three things at once:

1. **Header links** — in the order you list them.
2. **Footer quick links**.
3. **Route guard** — any section page (`/members`, `/publications`, `/projects`, `/positions`, `/news`) that is **not** listed returns 404. The home page (`/`) is always accessible.

So to hide a section entirely, simply omit it from `navigation`. Each item's `labelKey` is an i18n key resolved against `src/i18n/*.json`.

### Member categories

The groups on the Members page are **fully configurable** — there are no built-in defaults. Declare them in `nuxt.config.ts`; array order is the display, filter, and sort order:

```ts
members: {
  categories: [
    { key: 'staff', labelKey: 'members.staff' },
    { key: 'research-students', labelKey: 'members.researchStudents' },
    { key: 'alumni', labelKey: 'members.alumni' },
  ],
},
```

- `key` — the value you put in each member's `category:` frontmatter.
- `labelKey` — the i18n key translated into the filter button, group heading, and profile badge.

Add matching keys + translations to `src/i18n/en.json` and `src/i18n/zh-CN.json`. This template ships with four: `staff`, `research-students`, `research-assistants`, `alumni`. The Members page shows a filter bar when there are 2+ categories, plus an **All** option.

### Internationalization (i18n)

Built on `@nuxtjs/i18n` with English and Simplified Chinese included. The active locale is stored in an `i18n_locale` cookie and switchable via the header toggle.

- **UI strings** live in `src/i18n/en.json` and `src/i18n/zh-CN.json`. The keys (e.g. `nav.home`, `members.staff`, `footer.brand`) are the Markuxt contract — keep every key, change only the values.
- **Adding a locale:** add a new file (e.g. `ja.json`), register it in `nuxt.config.ts` under `i18n.locales`, and translate every key.
- **Referencing strings in config:** fields like `navigation[].labelKey` and `members.categories[].labelKey` point at these keys, so the same config works in every language.

### Co-located assets

Place images and videos **next to** the Markdown that uses them (e.g. `src/members/staff/jane.webp` next to `jane.md`). At build time Markuxt syncs every non-document file into `public/_markuxt/` and rewrites the relative paths so they resolve on static hosting. Reference them relatively in frontmatter (`image: assets/jane.webp`) or the body (`![alt](jane.webp)`).

Absolute `/images/...` paths (from `src/public/images/`) pass through unchanged.

### Rich Markdown: Mermaid & math

The content pipeline is pre-configured with:

- **Mermaid** diagrams — write a fenced ` ```mermaid ` block and it renders to a diagram. See `src/projects/demo-project.md`.
- **LaTeX math** via KaTeX — `$inline$` and `$$display$$`. See `src/publications/demo-publication.md`.

Both are wired through `remark-math` + `rehype-katex`; no extra setup needed.

### Theming & design tokens

The **Seaside** look (ocean blue / teal) is applied entirely through CSS custom properties — there is no build-time theme switch.

- **Fine-tune tokens** in `styles/_tokens.css` (`:root { --color-primary: ...; }`). Colors, fonts, spacing, radii, and shadows are all tokens.
- **Site-level overrides** in `styles/_theme.css`.

Markuxt ships three other palettes (Forest, Sunset, Slate) as separate template repositories — each is the same component system with different token values.

### Dark / light mode

A toggle in the header switches themes. The choice is persisted to `localStorage` (`markuxt-color-mode`); the default follows the OS preference. An inline head script sets the mode before first paint to avoid a flash.

---

## Deployment

The included GitHub Actions workflow (`.github/workflows/deploy.yml`) deploys to **GitHub Pages** on every push to `main`.

1. In your repo: **Settings → Pages → Build and deployment → Source: GitHub Actions**.
2. `@markuxt/markuxt` is a package on the GitHub npm registry — the workflow already passes `GITHUB_TOKEN` to `pnpm install`. If you change the registry or package visibility, adjust `registry-url` / auth accordingly.
3. For subdirectory (project-page) deployment, set `NUXT_PUBLIC_BASE_URL` in the workflow.

```bash
# build a static site locally
pnpm generate   # → .output/public/
```

## License

© Your Lab Name, Your University. All rights reserved.
