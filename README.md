# tylerstennett.github.io

Personal academic website of Tyler Stennett, PhD student in Computer Science at the Georgia Institute of Technology. Built with Jekyll (custom hand-written theme) and deployed via GitHub Pages at https://tylerstennett.com.

## Local development

```sh
bundle install
bundle exec jekyll serve --livereload
# → http://localhost:4000
```

Requires Ruby 3.3 — see [CLAUDE.md](CLAUDE.md) for one-time setup on macOS, project structure, and repository conventions (conventional commits, `feat/` branch naming).

## Web analytics

Cloudflare Web Analytics is configured for `tylerstennett.com` through a shared Jekyll include. The beacon is only emitted in production builds, so local development is not tracked. Analytics appear under **Analytics & Logs → Web Analytics** in the Cloudflare dashboard.

The configured site token in [`_config.yml`](_config.yml) is browser-visible and is not a secret. If the Cloudflare analytics property is recreated, replace that token with the value from its generated JavaScript snippet. Never add Cloudflare API tokens or account keys to this repository.
