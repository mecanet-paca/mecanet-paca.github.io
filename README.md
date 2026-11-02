# MECANET website

Website of MECANET (Mechanobiology Cancer Network), a structuring action of Canceropôle PACA, built on the
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

From the MECANET logo (Canceropôle PACA colours):

- **Logo**: temporary PNGs in `assets/img/`: `mecanet-wordmark.png` (navbar) and `mecanet-lockup.png` (home page), each with a `-dark` version
  for the dark theme.
- **Colours**: purple `#31217C`, teal `#00748C`, pink `#F14C80`, yellow `#FEB400`. Pink and yellow are for fills and
  decoration, never text on a light background.
- **Light theme**: purple headings and primary accents, teal links and secondary accents.
- **Dark theme**: yellow headings and primary accents, light teal links `#7FD3E3`.
- **Fonts**: Montserrat (headings) and Inter (body text), self-hosted (SIL Open Font License).

Colours and fonts live in `_sass/_mecanet.scss`.

## Files that override the al-folio theme

Two theme files are overridden locally:

- `assets/css/main.scss`: identical to the theme's, plus one line loading `_sass/_mecanet.scss`.
- `_includes/header.liquid`: the theme's version, except that the navbar shows the logo
  (`_includes/logo.liquid`), lists only the pages of the
  current language, has an EN/FR switch and a skip-to-content link, and takes its interface strings from
  `_data/i18n.yml`.

When updating the al-folio gems, run `bundle exec al-folio upgrade overrides audit` and check whether these two files
changed upstream.

## Launch checklist

- [ ] Set `preview: false` in `_config.yml`.
- [ ] Settings → Pages: deploy from branch `gh-pages`, `/ (root)`.
- [ ] Internal open items (people, content checks) are tracked outside the repository (`NOTES.local.md`, not committed).
