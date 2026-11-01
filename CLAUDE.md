# MECDITRINA website — notes for Claude Code

Website of MECDITRINA (MEChanobiology Devices and Innovative Tools for Research IN cAncer), a Canceropôle PACA
"Actions Structurantes" project (Oct 2026 – Jun 2028) with two hubs: DyNaMo (Marseille, coordinator Michael Sebbagh)
and IRCAN (Nice, coordinator Etienne Boulter). The site is a showcase plus a single entry point ("guichet unique") for
access requests to mechanobiology instruments and expertise.

Repo: `Mecditrina/mecditrina.github.io` (public; preview mode until launch, see the preview flag). Etienne commits manually: **never commit or push**;
propose changes, then stop.

## Content rules

- Language: English for code, comments, commit messages and conversation. The site is bilingual (English and French).
- **Bilingual rule: every content change goes in both languages, in the same change.** English page `_pages/x.md` ↔
  French page `_pages/fr/x.md`; data fields `field` ↔ `field_fr`; interface strings in `_data/i18n.yml` (`en:` and
  `fr:` blocks, same keys); news items `content` ↔ `content_fr` (or `title` ↔ `title_fr`). If the French text is not
  ready, leave the English in place and add a `TODO(fr)` comment; never leave one language with different facts.
- French tone: neutral and factual, like the English. French text is drafted, then proofread by Etienne.
- French typography, in all French text (pages, `_fr` data fields, `i18n.yml` `fr:`, French footer span): U+00A0
  (no-break space) before `:` and inside `« »`; U+202F (narrow no-break space) before `;` `!` `?`. Write them as
  literal characters, not `&nbsp;`/`&#8239;`. Not inside URLs, front matter keys or Liquid tags.
- Tone: neutral and factual. No promotional or celebratory wording, no forward-looking claims.
- Text comes from the funded proposal and the 13 Oct 2026 meeting deck. Do not invent facts (instruments, sites,
  people, dates, commitments). If something is missing, leave a `TODO` comment and say so.
- **The git history becomes public with the site.** Never commit personal phone numbers, private emails, or names of
  people who have not agreed to be listed — not even temporarily.
- Request-form data stays in Tally (EU-hosted). No Google Sheets / Google Forms integration.
- No third-party requests from the pages (the legal notice relies on it). Fonts are self-hosted in `assets/fonts/`
  (`@font-face` in `_sass/_mecditrina.scss`); the two JavaScript/CSS libraries are vendored in `assets/vendor/` (see
  "Vendored libraries" below). Builds need no network access.
- **Click-to-load rule for any embed** (forms, videos, maps…): nothing may be requested from a third party until
  the visitor clicks. Show a button plus one line naming who the content comes from, insert the iframe from a small
  inline script on click, and keep a plain link that works without JavaScript. Model: `_includes/tally-embed.liquid`
  (Tally form on Contact). Both legal notices must describe what loads after the click and from whom.
- The project name may still change. Keep the name out of new code paths: the wordmark text lives only in
  `wordmark:` in `_config.yml`, rendered by `_includes/wordmark.liquid`.

## Architecture (al-folio v1)

- Thin starter: layouts, includes and Sass come from gems pinned in `Gemfile` (`al_folio_core` 1.0.15 etc.).
  `theme: al_folio_core` must stay in `_config.yml`.
- Gem files are customised by local overrides at the same path. Only two exist; keep it that way if possible:
  - `assets/css/main.scss` — the gem's version plus a final `@use "mecditrina";`
  - `_includes/header.liquid` — the gem's version, except: the navbar brand renders `wordmark.liquid` when
    `site.wordmark` is set; the nav lists only pages in the current language; "home"/brand go to that language's
    home page; an EN/FR switch links to the page with the same `ref:` in the other language; a skip-to-content
    link targets `#main-content` (an empty span after `</header>`, since the gem's main container has no id); all
    its interface strings (menu button, "(current)", theme toggle, switch labels) come from `_data/i18n.yml`.
  - After any gem update: `bundle exec al-folio upgrade overrides audit`.
- All identity styles: `_sass/_mecditrina.scss`. Components are prefixed `mx-` (`mx-hero`, `mx-section`, `mx-grid`,
  `mx-grid-2`, `mx-card`, `mx-icon` + tints `peach`/`lavender`/`mint`, `mx-chips`, `mx-steps`, `mx-badge`
  `marseille`/`nice`/`soon`, `mx-domain`, `mx-person`, `mx-avatar`, `mx-list-plain`, `mx-callout`,
  `mx-btn-primary`/`mx-btn-secondary`, `mx-form-frame`, `mx-note`). Reuse these before adding new ones; colours go
  through the `--global-*` variables so dark mode keeps working.
- Pages in `_pages/`: `about.md` (home, `permalink: /`), `instruments.md`, `expertise.md`, `news.md`, `people.md`,
  `contact.md` (nav_order 1–5), `legal.md` (not in nav, linked from `footer_text`), `404.md`.
- French pages in `_pages/fr/`, same file names, French permalinks: `/fr/`, `/fr/instruments/`, `/fr/expertise/`,
  `/fr/actualites/`, `/fr/equipe/`, `/fr/contact/`, `/fr/mentions-legales/`. `lang` comes from front-matter defaults in
  `_config.yml` (`en` everywhere, `fr` under `_pages/fr`); `<html lang>` follows it (via `al_rtl`). Each pair shares
  a `ref:` key (`home`, `instruments`, `expertise`, `news`, `people`, `contact`, `legal`). `og:locale` stays `en`
  (deliberately no `metadata.liquid` override). Internal links in French pages point to the French URLs.
- News lists use `_includes/news-list.liquid` (bilingual copy of the gem's `news.liquid`, French dates), not the
  gem include. Items dated after the build time are skipped until a later build. News items are inline only: the
  `news` collection has `output: false` (no page, no sitemap entry), so a non-inline item would link to nothing. `footer_text` holds both languages in `.mx-lang-en` / `.mx-lang-fr` spans; CSS shows the one matching
  `<html lang>`.
- French pages print data fields with `{% include tr.liquid obj=x key='field' %}` (`field_fr`, else English). English
  pages read the English fields directly. Interface strings used by both languages (e.g. instrument status labels)
  come from `_data/i18n.yml`. The 404 page is a single bilingual page with no automatic redirect.
- `sitemap.xml` (root) is a Liquid template that replaces jekyll-sitemap's output: it lists `site.html_pages` and
  published collection documents, with hreflang alternates for pages sharing a `ref:` (x-default = English). Never
  edit it to add pages; new pages and `ref:` pairs are picked up automatically.
- Data: `_data/instruments.yml` (domains → techniques with `sites`, `status: available|deploying|planned`, optional `equipment`),
  `_data/people.yml`. News: one file per item in `_news/`.
- Pages are HTML blocks inside Markdown files. Markdown inside an HTML block is not processed (kramdown
  `parse_block_html` is off), so write HTML (`<b>`, `<a href>`) there, not `**` or `[]()`.
- Internal links: use `{{ '/path/' | relative_url }}` in Liquid pages. Links in running text stay underlined (WCAG 1.4.1;
  rule "Links in running text" in `_sass/_mecditrina.scss`).

## Build, check, deploy

```bash
bundle install
bundle exec jekyll serve            # http://localhost:4000 (needs ImageMagick for jekyll-imagemagick)
npx prettier . --write              # CI fails on unformatted files (printWidth 150, liquid plugin)
```

- Docker alternative: `docker compose up` (serves on port 8080).
- `deploy.yml` builds with `JEKYLL_ENV=production`, then runs **PurgeCSS** on `_site`. Classes added only at runtime
  by JS must be safelisted in `purgecss.config.js`, otherwise they work locally and break in production.
- Workflows kept: `deploy`, `prettier`, `axe` (accessibility), `broken-links-site`.
- `preview:` in `_config.yml`: `true` before launch makes `robots.txt` disallow all crawlers (`Disallow: /`, no
  `Sitemap:` line); `false` serves the normal `robots.txt` with the sitemap. **Set `preview: false` at launch.**
- Publishing needs a public repo (GitHub Free): then Settings → Pages → Deploy from branch `gh-pages`, `/ (root)`.
  If the deploy fails with a 403, set workflow permissions to Read and write at org level.

## Vendored libraries

The pages load exactly two third-party libraries, committed in `assets/vendor/` (with their licence files) and
declared in `third_party_libraries` in `_config.yml` (`download: false`, local URLs, SRI `integrity` hashes):

- Font Awesome Free (`@fortawesome/fontawesome-free`): `assets/vendor/fontawesome/css/all.min.css` and
  `assets/vendor/fontawesome/webfonts/*.woff2` (the CSS loads `../webfonts/`).
- vanilla-back-to-top: `assets/vendor/vanilla-back-to-top/vanilla-back-to-top.min.js`.

There is no `jekyll-3rd-party-libraries` (it pinned `css_parser < 2.0`, see CVE-2026-53727) and no `al_img_tools`
(its only purpose here was that dependency; image zoom/lightbox are not used). Do not add them back.

To update a library (manually, e.g. when Dependabot or a release note calls for it):

1. In a scratch folder: `npm pack @fortawesome/fontawesome-free@X.Y.Z` (or `vanilla-back-to-top@X.Y.Z`), then
   `tar -xzf *.tgz`.
2. Copy the same files over the ones in `assets/vendor/` (`package/css/all.min.css`, `package/webfonts/*.woff2`,
   `package/LICENSE.txt`; or `package/dist/vanilla-back-to-top.min.js`, `package/LICENSE`).
3. Compute the new hash: `echo "sha256-$(openssl dgst -sha256 -binary FILE | openssl base64 -A)"`, and update
   `integrity` and `version` in `_config.yml`.
4. Production build + PurgeCSS; check that icons render, back-to-top works and the pages make no external requests.

## Visual identity (deck of 13 Oct 2026)

- Wordmark: "MEC" `#015977` (dark mode `#6FC8D2`); "DITRINA" gradient `#9F639B` → `#D1638B` 30% → `#E18B6A` 65% →
  `#F99E72`. Montserrat 700.
- Header band: `#6FC8D2` → `#A1B8DA` → `#C9AED5` → `#E8B7C3` → `#FCB88F`.
- Text: headings `#183A4A`, body `#23394B`, secondary `#4F616F`, accent `#119BA5`, hover `#A8476F`.
- Tints: `#E4F4F5`, `#FDF3EC`, `#F2EFF6`, `#E9F5F2`, `#EBF0F5`.
- Dark mode: background `#0E1F2B`, cards `#142A38`, text `#E2EBF0`.
- Fonts: Montserrat (wordmark, headings), Inter (body). Aptos (deck body font) is not licensed for the web.

## Open items

Read `NOTES.local.md` if present for open items that involve people or internal decisions. It is gitignored and
excluded from the build; never copy its content into a tracked file.

- At launch: set `preview: false` in `_config.yml`.
- Optional: partner/funder logo strip, custom domain.
