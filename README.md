# An opinionated starting point for web projects

- [**Brunch**](https://brunch.io/docs/config) for static site generation.
- [**Pug**](https://pugjs.org/) (and [companion plugin](https://github.com/bmatcuk/pug-brunch-static)) for flexible static markup.
- [**Stylus**](http://stylus-lang.com/) for flexible styling.
- [**Mithril**](https://mithril.js.org/api.html) for SPAs and JS utilities.
- [**Netlify**](https://www.netlify.com/docs/netlify-toml-reference/) for static hosting, auth, and serverless functions.

## Hints

### General

- ESLint pre-commit hook automatically attempts to fix JS errors and styles.
- Prefer root (non-relative) imports:
  - Pug: `extends /_shared/layout` (root)
  - JS: `import '_shared/util';`
  - Stylus: `@import _shared/config`
- Secrets should be stored in `.env`.
  - Make a copy from `.env.example`. Do not check this file in.
  - Import or require `dotenv/config` at the beginning of any script to
    populate `process.env.*`.
  - Existing ENV variables will never be overwritten.

### /source/**.pug

- Each `/source/**.pug` is compiled to `/public/**.html`.
- Layouts accept YAML and JSON frontmatter.
- Create a 404.pug and Netlify will automatically use it.
- Prefer `<script defer ...>` in the `<head>`.

### /source/*/*.js

- Each `/source/*/index{,~*}.js` is compiled to `/public/assets/*.js`.
- To bundle npm modules, name the file `index~module1~module2~etc.js`.
- To bundle `_shared` JS modules, name the file `index~_shared~module1~etc.js`.
- `/source/global/*.js` must be loaded on every page.
- Only modules actually `import`ed will be included.

### /source/*/*.styl

- Each `/source/*/index.styl` is compiled to `/public/assets/*.css`.

## To Do

- Document Netlify functions
- CSS framework / conventions
- Purify CSS to reduce output
- Pug conventions for loading assets
