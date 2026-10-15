# MYChen's Blog

Personal tech blog at **https://ustc-cmy.github.io** — notes on machine learning,
neural networks, and coding in Python, plus a few life posts.

Built with [Jekyll](https://jekyllrb.com/) on the
[MVM (Minimum Viable Model)](https://github.com/AmazingDD/MVM) theme,
deployed automatically to GitHub Pages via GitHub Actions.

## Stack

| Piece | Choice |
|---|---|
| Static site generator | Jekyll 4 (Ruby) |
| Theme | MVM — card-based, responsive, dark-mode aware |
| Hosting | GitHub Pages (`main` branch → Actions → Pages) |
| Search | Simple Jekyll Search (client-side, reads `search.json`) |
| Comments | Optional, via utterances |
| Analytics | Google Analytics (GA4) |

## Local development

Requires Ruby 3.x and Bundler.

```bash
bundle install
bundle exec jekyll serve --livereload
```

Then open <http://127.0.0.1:4000>.

If the local port 4000 is taken, pass another one:

```bash
bundle exec jekyll serve --livereload --port 4001
```

## Writing a post

Add a Markdown file to `_posts/` named `YYYY-MM-DD-slug.md`. The front matter
drives the card image, tags, reading time, and SEO metadata:

```yaml
---
layout: post
title: "Your title here"
date: 2024-01-01 12:00:00 +0800
description: One or two sentences — used for SEO and social previews.
img: posts/20240101/cover.jpg      # relative to assets/img/
tags: [python, machine learning]
read_time: true
show_date: true
toc: true                          # optional: right-hand table of contents
mermaid: true                      # optional: enable Mermaid diagrams
mathjax: true                      # optional: enable $...$ math rendering
---
```

If `description` is omitted, the first paragraph of the post is used instead.
If `img` is omitted, `default_image` from `_config.yml` is used.

**Image paths must be absolute from the site root** — write
`/assets/img/posts/...`, not `../assets/img/posts/...`. The theme builds
`../` prefixes itself, so relative paths break under pagination and IPFS.

## Deployment

Every push to `main` triggers `.github/workflows/pages.yml`, which builds the
site and publishes it to GitHub Pages. The live URL appears at the bottom of
the **Actions** tab after each run.

## Repo layout

```
_config.yml            Site settings, author info, plugins
_layouts/              default, home-page, post, menu-page
_includes/             Header, footer, SEO, scripts, share widgets
_pages/                About, archive, tags, tag pages
_posts/                Blog posts
assets/
  css/                 Compiled styles (main.css) + highlight themes
  img/                 Branding, post covers, favicons
  js/                  Search, theme toggle, Mermaid
index.html             Homepage — renders the paginated post card grid
sitemap.xml            Hand-written sitemap (jekyll-sitemap also enabled)
search.json            Client-side search index, generated at build
```

## Credits

Theme: [MVM](https://github.com/AmazingDD/MVM), licensed under GPL-3.0.
Icons: Font Awesome. Fonts: Lora and Source Sans Pro (SIL Open Font License).

## License

Site content and theme modifications follow the repository `LICENSE` file.