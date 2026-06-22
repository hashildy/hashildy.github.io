# hashildy.github.io

Personal site and blog of [@hashildy](https://github.com/hashildy), published with
GitHub Pages at **https://hashildy.github.io**.

> **LaurenXen** — "An IT blog about DevOps, automation, Windows, Linux, EUC, and
> everything in between."

The site is a [Jekyll](https://jekyllrb.com/) site built on the
[**Minimal Mistakes**](https://github.com/mmistakes/minimal-mistakes) theme. The
theme is pulled in as a remote theme (`remote_theme: "mmistakes/minimal-mistakes"`
in `_config.yml`), so the bulk of the layouts and styling live upstream rather than
in this repo.

## Running locally

This site uses the [`github-pages`](https://github.com/github/pages-gem) gem (see
`Gemfile`), which pins Jekyll and its plugins to the versions GitHub Pages runs.

```bash
bundle install
bundle exec jekyll serve
```

Then open http://localhost:4000. Jekyll rebuilds on change, but note that edits to
`_config.yml` require restarting the server.

Plugins enabled via the `Gemfile` include `jekyll-paginate`, `jekyll-sitemap`,
`jekyll-gist`, `jekyll-feed`, `jemoji`, `jekyll-include-cache`, and
`jekyll-algolia`.

## Building JS assets

The theme's JavaScript is concatenated and minified into `assets/js/main.min.js`
using the npm scripts in `package.json` (requires Node):

```bash
npm install        # installs uglify-js, npm-run-all, onchange
npm run build:js   # uglify + prepend the banner (banner.js)
npm run watch:js   # rebuild on changes to assets/js/**/*.js
```

`build:js` runs `uglify` (bundles the jQuery vendor file, the plugins under
`assets/js/plugins/`, and `assets/js/_main.js`) followed by `add-banner`
(`node banner.js`).

## Layout

- `_config.yml` — site title, description, theme, plugins, and pagination settings.
- `index.html` — site home page (uses the theme's `home` layout).
- `assets/` — `css/` (`main.scss`), `images/`, and `js/` (source, plugins, vendor,
  and the built `main.min.js`).
- `_data/`, `_includes/`, `_layouts/`, `_sass/` — local overrides layered on top of
  the remote Minimal Mistakes theme.
- Blog posts go in `_posts/` and standalone pages in `_pages/` (the latter is wired
  up via `include` in `_config.yml`), following Minimal Mistakes conventions.

## Credits & license

Built on the [Minimal Mistakes](https://github.com/mmistakes/minimal-mistakes)
Jekyll theme by [Michael Rose](https://github.com/mmistakes), distributed under the
[MIT License](LICENSE) (see `LICENSE` for the full text).
