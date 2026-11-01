# MECDITRINA website

Website of MECDITRINA (MEChanobiology Devices and Innovative Tools for Research IN cAncer), built on the
[al-folio](https://github.com/alshedivat/al-folio) v1 Jekyll starter and published with GitHub Pages. The site is
bilingual: English at `/`, French at `/fr/`.

## Publish it

1. In the GitHub organization, create an empty public repository named `<org>.github.io`.
2. Push this folder to its `main` branch.
3. **Settings → Actions → General → Workflow permissions**: select _Read and write permissions_.
4. Wait for the **Deploy site** action to finish (Actions tab), then go to **Settings → Pages**, set _Source_ to
   _Deploy from a branch_, branch `gh-pages`, folder `/ (root)`.
5. In `_config.yml`, set `url:` to `https://<org>.github.io` (or to your custom domain).

Every push to `main` rebuilds and republishes the site in a few minutes.

## Edit the content

| What                             | Where (English / French)                                                                            |
| -------------------------------- | --------------------------------------------------------------------------------------------------- |
| Instruments and techniques       | `_data/instruments.yml` (`field` / `field_fr`)                                                      |
| People, institutes, references   | `_data/people.yml` (`field` / `field_fr`)                                                           |
| News                             | one file per item in `_news/` (`content` / `content_fr`); items dated in the future wait            |
| Page text                        | `_pages/*.md` / `_pages/fr/*.md` (same file names)                                                  |
| Interface strings (buttons, nav) | `_data/i18n.yml` (`en:` / `fr:`)                                                                    |
| Request form and contact address | front matter of `_pages/contact.md` (`tally_form_id`, `contact_email`; the French page reuses them) |
| Legal notice / GDPR text         | `_pages/legal.md` / `_pages/fr/legal.md`                                                            |

Every content change goes in both languages. Files can be edited directly on github.com (pencil icon); the site
rebuilds on commit.

## Privacy

The pages make no requests to third parties: fonts are self-hosted in `assets/fonts/`, and the two JavaScript/CSS
libraries (Font Awesome, back-to-top button) are committed in `assets/vendor/`, so builds need no network access. The Tally
request form is click-to-load: nothing is requested from Tally until the visitor clicks "Show the request form".
Keep it that way for any future embed, and keep both legal notices in line.

## Updating the vendored libraries

Font Awesome and vanilla-back-to-top are not downloaded at build time. To update one, replace its files in
`assets/vendor/` with those of the new npm release, then update `version` and the SRI `integrity` hash in
`third_party_libraries` (`_config.yml`). Step-by-step commands are in `CLAUDE.md` ("Vendored libraries").

## Preview mode

`preview: true` in `_config.yml` makes `robots.txt` ask all crawlers to stay away (no sitemap advertised). **Set
`preview: false` at launch.**

## Visual identity

From the MECDITRINA presentation (October 2026):

- **Wordmark**: "MEC" in deep teal `#015977`, "DITRINA" in a mauve → pink → peach gradient
  (`#9F639B` → `#D1638B` → `#E18B6A` → `#F99E72`). Vector files: `assets/img/mecditrina-wordmark.svg`
  (light backgrounds) and `mecditrina-wordmark-dark.svg` (dark backgrounds).
- **Header band**: aqua → lavender → pink → peach (`#6FC8D2` → `#C9AED5` → `#E8B7C3` → `#FCB88F`).
- **Text**: navy `#183A4A` / `#23394B`, secondary `#4F616F`, accent teal `#119BA5`.
- **Fonts**: Montserrat (wordmark, headings) and Inter (body text), self-hosted (SIL Open Font License).

All of it lives in `_sass/_mecditrina.scss`.

## Files that override the al-folio theme

Two theme files are overridden locally:

- `assets/css/main.scss`: identical to the theme's, plus one line loading `_sass/_mecditrina.scss`.
- `_includes/header.liquid`: the theme's version, except that the navbar shows the coloured wordmark
  (`_includes/wordmark.liquid`, whose text is set by `wordmark:` in `_config.yml`), lists only the pages of the
  current language, has an EN/FR switch and a skip-to-content link, and takes its interface strings from
  `_data/i18n.yml`.

When updating the al-folio gems, run `bundle exec al-folio upgrade overrides audit` and check whether these two files
changed upstream.

## Launch checklist

- [ ] Set `preview: false` in `_config.yml`.
- [ ] Settings → Pages: deploy from branch `gh-pages`, `/ (root)`.
- [ ] Internal open items (people, content checks) are tracked outside the repository (`NOTES.local.md`, not committed).
