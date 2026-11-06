# The Maven Handbook

Sources of [book.maveniverse.eu](https://book.maveniverse.eu): a community-written book for
[Apache Maven](https://maven.apache.org/) users, by [Maveniverse](https://maveniverse.eu).

The site is built with [Hugo](https://gohugo.io/) and the [Docsy](https://www.docsy.dev/) theme
(pulled in as a Hugo module). Content is plain Markdown.

## Layout

```
content/
  en/                 English (main language)
    _index.md         home page
    docs/             the book itself, one directory per chapter
      10_introducing_maven/
      20_common_concepts/
      ...
  da/, fr/            Danish and French translations (mirror the en/ structure)
assets/               logo and SCSS overrides (Maveniverse look, shared with maveniverse.eu)
layouts/              small Hugo/Docsy template overrides
static/               favicons and other files copied as-is
hugo.yaml             site configuration (languages, menus, links, theme module)
```

Each chapter is a directory with an `_index.md` (chapter intro, ordered by its `weight`)
and one Markdown file per page. Pages start with front matter, for example:

```markdown
---
title: Build Lifecycle
weight: 50
description: How Maven decides what to run, and in which order.
---
```

## Editing

**Small fixes:** click "Edit this page" on any page of the site, and GitHub opens the source file
for editing and a pull request.

**Larger changes:** fork the repository, edit the files under `content/`, preview locally (see
below) and open a pull request against `main`. Translations go to the same path under
`content/da/` or `content/fr/`.

Questions and ideas are welcome in [GitHub discussions](https://github.com/orgs/maveniverse/discussions).

## Local preview

Requirements: [Node.js](https://nodejs.org/) (see `.nvmrc`), [Go](https://go.dev/) (Hugo uses it
to fetch the Docsy module) and Git. Hugo extended itself comes from npm.

```bash
npm install
npm run serve
```

Then open <http://localhost:1313/>. The site reloads as you edit.

Other useful commands:

| Command               | What it does                                |
|-----------------------|---------------------------------------------|
| `npm run build`       | build the site into `public/`               |
| `npm run check:links` | build and check for broken links            |
| `npm run fix:format`  | format sources with Prettier                |
| `npm run update`      | update npm packages and the Docsy module    |

Alternatively, with Docker: `docker compose up --build` and open <http://localhost:1313/>.

If a build fails with `permission denied` inside `public/`, delete `public/` (it is build output)
and run again.

## Publishing

Every push to `main` builds the site and deploys it to GitHub Pages via
`.github/workflows/hugo.yml`. There is no manual release step.

## License

Book content is published under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/);
the site sources are under the Apache License 2.0, see `LICENSE`.
