# skhan61.github.io

Sayem Khan's personal site: https://skhan61.github.io

- Theme: [Hydejack](https://hydejack.com/) 9.2.1 (free), loaded with `remote_theme`. Only its documented settings are changed; there is no custom CSS and no custom layout.
- Hosting: GitHub Pages, branch build from `main` at `/` (no deploy workflow). Every push to `main` goes live in a few minutes.
- Look: always dark (`hydejack.dark_mode.always`), dark teal sidebar with the Aparajita flower art, amber accent, Aparajita icons.

## Updating the site

| Part | Where | How |
|---|---|---|
| About (`/`) | `index.md` | Edit the Markdown. The front matter (`layout: about`, `title`) gives the big name heading. |
| CV (`/cv/`) | `cv.md` | Automatic: each release of [skhan61/career](https://github.com/skhan61/career) pushes `assets/cv/sayem_khan_cv.pdf` and `_includes/cv-body.html`. Never edit those two by hand. |
| Blog (`/blog/`) | `_posts/YYYY-MM-DD-slug.md` | Add a post and push. The list shows "No posts yet." while there are none. |
| Sidebar text, menu, social links | `_config.yml` (`title`, `tagline`, `menu`), `_data/authors.yml` | Edit and push. |
| Colors | `_config.yml`: `accent_image` (sidebar background and art), `accent_color` (links), `theme_color`, `background_color` | |
| Icons | `assets/icons/` (`icon.svg`, `favicon.ico`, `apple-touch-icon.png`, `icon-*.png`), `/favicon.ico`; `_config.yml` `favicon`, `apple_touch_icon`; the SVG icon is linked in `_includes/my-head.html` | |
| Profile picture | `assets/img/me.jpg` (also `logo` in `_config.yml`) | Replace the file. |

## Layout

```
_config.yml            site and Hydejack settings
_data/                 author, social links, strings
_includes/my-head.html extra <head> tags (SVG icon)
_includes/cv-body.html CV as HTML (written by skhan61/career)
index.md  cv.md  blog/ pages
assets/cv/             CV PDF (written by skhan61/career)
assets/img/            profile picture, sidebar art
assets/icons/          site icons
sw.min.js              removes the service worker of an earlier theme
LICENSE.md NOTICE.md licenses/  Hydejack license files (GPL-3.0), kept as shipped
Gemfile  .github/      CI only, not published
```

## CI

`.github/workflows/ci.yml` builds the site with the same `github-pages` gem version that Pages uses and runs `html-proofer` on the result (internal links, images, scripts). Dependabot checks the actions and gems weekly. Pages does not depend on CI; it builds `main` on its own.

## Access

Besides the owner, only one deploy key can write here: "sync from skhan61/career", used by the career release to push the CV files.
