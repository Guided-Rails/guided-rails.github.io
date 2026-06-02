# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Jekyll-based blog at `guidedrails.com` where Abdullah Hashim writes about accessibility and testing in Rails. Hosted on GitHub Pages, styled with Tailwind via CDN. The bar for this site is "as simple as possible" — resist adding scaffolding, components, or build steps.

## Development Commands

```bash
bin/dev                     # preferred: bundle install if needed, then serve with livereload
bundle install              # install gem dependencies
bundle exec jekyll serve    # serve at http://localhost:4000 with auto-regen
bundle exec jekyll build    # build to _site/ (git-ignored)
```

## Architecture

- `_config.yml` — site metadata; sets `permalink: /:title/`, a default `layout: post` for everything in `_posts/`, and loads the `jekyll-feed` plugin (RSS at `/feed.xml`).
- `_layouts/default.html` — HTML shell. Loads Tailwind via CDN with the typography plugin (`?plugins=typography`), then the two stylesheets, emits `{% feed_meta %}`, and renders the header link home plus the footer.
- `_layouts/home.html` — homepage: site title, tagline, list of posts. Used by `index.markdown`.
- `_layouts/post.html` — single post view: title, date, and content wrapped in a `.prose` container (Tailwind typography).
- `_posts/` — blog posts, named `YYYY-MM-DD-title.markdown`. Front matter is just `title` + `date`; the default `layout: post` applies.
- `assets/css/main.css` — styles inline code and code blocks within `.prose`.
- `assets/css/syntax.css` — Rouge syntax-highlighting theme (GitHub light) for fenced code.
- `assets/audio/` — `.m4a` clips for accessibility demos (e.g. VoiceOver announcements), embedded with `<audio>` in posts.
- `index.markdown` — front matter only; delegates to `home.html`.
- `404.html` — minimal not-found page.
- `CNAME` — points to `guidedrails.com`.

## Notes

- GitHub Pages auto-deploys on push to `main`.
- `Gemfile.lock` is git-ignored.
- Ruby 3.4.2, Jekyll 3.10 via the `github-pages` gem.
- Styling is Tailwind utilities + the typography plugin, plus the two stylesheets above. Reach for a Tailwind utility class in markup first; only edit `main.css`/`syntax.css` for things utilities can't reach (Rouge token colors, `.prose` code styling).
- Posts following an accessibility-demo pattern interleave the bad/good code (fenced ```erb), a live interactive `<figure>`, and an `<audio>` clip with a transcript — see the icon-button post for the established shape.
