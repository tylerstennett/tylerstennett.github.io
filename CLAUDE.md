# CLAUDE.md

Personal academic website for Tyler Stennett, served at https://tylerstennett.github.io. A hand-built Jekyll site (no theme gem) deployed natively by GitHub Pages.

## Repository conventions

### Commits

Use Conventional Commits: `<type>: <subject>` with an imperative, lowercase subject and no trailing period.

- Types: `feat`, `fix`, `docs`, `style`, `refactor`, `chore`
- Examples: `feat: add publications page`, `fix: correct active nav state on blog posts`, `chore: update cv pdf`

### Branches

- Name branches `<type>/<kebab-case-name>` using the same types as commits.
- Examples: `feat/site-scaffold`, `fix/nav-mobile`, `docs/update-readme`
- Merge into `main`; `main` is what GitHub Pages deploys.

## Project structure

- `_config.yml` — site metadata, plugins, permalink style, front-matter defaults
- `_layouts/` — `default` (skeleton), `home` (hero + news + selected pubs), `page`, `post`, `research-note`
- `_includes/` — `head`, `nav`, `footer`, `publication` (renders one publication entry)
- `_sass/` — theme partials: `_variables` (design tokens), `_base` (typography), `_layout` (header/container/footer), `_components` (hero, pubs, pills, lists)
- `_data/` — `publications.yml`, `talks.yml`, `teaching.yml` drive the corresponding pages
- `_posts/` — short news items listed in the News section at `/posts/`
- `_research/` — longer, accessible paper overviews listed as Research Notes at `/posts/`
- Section pages at the repo root: `index.md`, `publications.md`, `cv.md`, `teaching.md`, `talks.md`, `posts.md`
- `assets/` — `css/main.scss` (Sass entry point), `img/` (profile photo), `files/` (CV PDF)

## Editing content

- Publications, talks, and teaching entries live in `_data/*.yml` — edit the YAML, not the pages.
- News items are files in `_posts/` named `YYYY-MM-DD-slug.md`; the four most recent appear on the homepage.
- Research notes are files in `_research/`. Include `title`, `takeaway`, `description`, `date`, `venue`, and the associated paper metadata in front matter; reading time is calculated automatically.
- Publications with `selected: true` appear in the homepage "Selected Publications" section (first three).
- The homepage serves `assets/img/headshot.jpg`, a web-optimized (640px JPEG) version of the full-res source `assets/img/headshot_square.png` (which is excluded from the built site). To update the photo, replace the source and regenerate: `sips -Z 640 -s format jpeg -s formatOptions 85 assets/img/headshot_square.png --out assets/img/headshot.jpg`.
- The CV page (`cv.md`) embeds `assets/files/Tyler_Stennett_CV.pdf` in an inline viewer with download and open-in-new-tab buttons (touch devices get only the buttons). To update the CV, replace the PDF in place, keeping the filename, and bump `updated` in the front matter of `cv.md`.
- Never edit `_site/` — it is generated output and gitignored.

## Local development

Requires Ruby 3.3 specifically — macOS system Ruby (2.6) is too old, and newer Rubies (4.x) make bundler resolve an outdated `github-pages` gem. Ruby 3.3 matches what GitHub's Pages builder runs. One-time setup:

```sh
brew install ruby@3.3
echo 'export PATH="/opt/homebrew/opt/ruby@3.3/bin:$PATH"' >> ~/.zshrc && exec zsh
bundle config set --local path vendor/bundle
bundle install
```

Then to serve locally:

```sh
bundle exec jekyll serve --livereload
# → http://localhost:4000
```

## Deployment

Push to `main`; GitHub Pages builds the site natively with the `github-pages` gem. Do not add a GitHub Actions workflow, and only use plugins on the github-pages whitelist (currently jekyll-seo-tag, jekyll-feed, jekyll-sitemap).

Because the github-pages gem pins Jekyll 3.x with an old Sass converter, `_sass/` must use `@import` — not the modern `@use`/`@forward` module system.

## Design notes

- All colors are CSS custom properties in `_sass/_variables.scss`. Dark mode is intentionally not implemented; add it later with a `@media (prefers-color-scheme: dark)` block overriding those properties.
- Fonts are system stacks (serif display, sans body) — zero external requests. If a custom face is ever wanted, self-host woff2 files in `assets/fonts/`; do not link external font CDNs.
