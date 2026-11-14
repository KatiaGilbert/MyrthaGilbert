# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this site is

Personal website for Myrtha Gilbert, Haitian historian and author. The site is in French (some articles in Haitian Creole or Spanish). It is a fully static site — no build system, no framework, no package manager.

## To view the site

Open any `.html` file directly in a browser (double-click or drag into browser). No server needed.

## File structure

- `index.html` — home page (hero, books grid, biography, article previews, contact form)
- `publications.html` — full article/publication index with filter buttons
- `article-*.html` — individual article pages (one file per article)
- `*.avif` / `*.jpg` — images (books covers, portraits). `.avif` is primary; `.jpg` fallback via `onerror`

## Architecture: CSS is duplicated in every file

There is no shared stylesheet. Each page has its own `<style>` block with the full CSS. The color palette (CSS variables) and nav/footer markup must be kept consistent across all files manually.

**Color palette (copy these exactly into every new page):**
```css
--blue:#3A6B9A; --blue2:#4A80B5;
--blue-light:#EAF4FB; --blue-mid:#7AAEC8;
--nav-bg:#2A4A60; --footer-bg:#152A3A;
--text:#1A2A35; --text2:#3A5060; --text3:#7A9BAA;
--bg:#F4F9FC; --white:#FFF; --border:#C8DFE8;
```

## Adding a new article

1. Copy an existing `article-*.html` file as a starting point.
2. Update the `<title>`, the breadcrumb text, `<h1>`, `.article-meta` date, and the article body.
3. Add a `<div class="pub-card" data-type="article">` entry at the top of the correct year section in `publications.html`.
4. Add a preview card in the `#articles` section of `index.html` if it should appear on the home page.

## Contact form

The contact form in `index.html` posts to Formspree: `https://formspree.io/f/xeenaeko`.

## Nav links

- On `index.html`: nav links use anchor hashes (`#livres`, `#biographie`, etc.)
- On all other pages: nav links point back to `index.html#livres`, `index.html#biographie`, etc.
