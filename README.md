# Vyrnexis Blog (GitHub Pages)

Custom-coded blog built for GitHub Pages. It is Jekyll-compatible and uses GitHub's built-in Jekyll pipeline to render Markdown posts and layouts.

## Project Layout

```text
vyrnexis.github.io/
├── _config.yml
├── _data/
│   └── links.yml
├── _layouts/
│   └── default.html
├── _posts/
│   ├── 2025-12-04-welcome-to-vyrnexis.md
│   └── 2025-12-04-rc4-nim.md
├── assets/
│   ├── avatar-vyrnexis-400.svg
│   ├── icon-discord.svg
│   ├── icon-github.svg
│   ├── icon-mail.svg
│   ├── icon-portfolio.svg
│   ├── icon-youtube.svg
│   ├── logo-vyrnexis.svg
│   ├── vyrnexis.png
│   └── vyrnexis_600px.png
├── about.md
├── favicon.ico
├── index.html
└── CNAME
```

## Customize The Site

- Edit `_config.yml` for site-level copy and metadata.
- Edit `_data/links.yml` for sidebar links and icon files.
- Edit `_layouts/default.html` for layout, styling, and client-side behavior.
- Replace icons or logos in `assets/` as needed.

## Add A Post

1. Create a file in `_posts/` named `YYYY-MM-DD-your-title.md`.
2. Add front matter:

```yaml
---
layout: default
title: "My Post Title"
date: 2025-12-10 14:00:00 +0800
author: "Your Name"
---
```

3. Write Markdown content. Example with an image and Nim code:

````markdown
![Screenshot]({{ '/assets/example.png' | relative_url }})

```nim
echo "Hello from Nim"
```
````

4. Commit and push. GitHub Pages rebuilds automatically.

## Local Preview (Optional)

If Jekyll is installed locally:

```bash
jekyll serve
```

Then open `http://localhost:4000`.

## Deploy On GitHub Pages

1. Push this repo to GitHub.
2. In repo settings, enable GitHub Pages from the main branch.
3. If using a custom domain, set DNS and add/update `CNAME`.
4. Wait for Pages build and certificate issuance, then enable HTTPS.

## Implementation Notes

- Accent toggle persists in `localStorage`.
- Scroll restoration is handled to avoid jumpy navigation.
- Rouge syntax highlighting is styled in `default.html`.
