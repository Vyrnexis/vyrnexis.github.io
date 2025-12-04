# Vyrnexis — Dark Tech Blog (Jekyll Version)

This repo is a Jekyll-powered version of the **Vyrnexis** dark tech blog.

- Uses a custom layout in `_layouts/default.html`
- Home page (`index.html`) lists posts automatically
- Posts live in `_posts/` as Markdown files
- Logos and avatar live in `assets/`

## Structure

```text
vyrnexis-jekyll-full/
├── index.html
├── _config.yml
├── _layouts/
│   └── default.html
├── _posts/
│   └── 2025-12-04-welcome-to-vyrnexis.md
└── assets/
    ├── logo-vyrnexis.svg
    ├── logo-original-vyrnexis.svg
    └── avatar-vyrnexis-400.svg
```

## Deploy to GitHub Pages

1. Create a repository named:

   ```text
   vyrnexis.github.io
   ```

2. Copy all files from this folder into the repository root.

3. From a terminal:

   ```bash
   git init
   git add .
   git commit -m "Initial Vyrnexis Jekyll site"
   git branch -M main
   git remote add origin https://github.com/<your-username>/vyrnexis.github.io.git
   git push -u origin main
   ```

4. Open:

   ```text
   https://<your-username>.github.io/
   ```

## Adding New Posts

1. Create a new file in `_posts/` with this naming pattern:

   ```text
   YYYY-MM-DD-your-title-here.md
   ```

2. Start it with front matter, for example:

   ```yaml
   ---
   layout: default
   title: "My Second Post"
   date: 2025-12-10
   author: "Vyrnexis"
   ---
   ```

3. Write the rest in **Markdown**. Example:

   ```markdown
   This is another post on the Vyrnexis blog.

   - bullet 1
   - bullet 2
   ```

4. Commit and push:

   ```bash
   git add _posts/2025-12-10-my-second-post.md
   git commit -m "Add new post"
   git push
   ```

The home page will automatically show the new post.

## Logos & Avatar

- `assets/logo-vyrnexis.svg` — minimal square logo for the site header.
- `assets/logo-original-vyrnexis.svg` — alternate logo with the wordmark “VYRNEXIS”.
- `assets/avatar-vyrnexis-400.svg` — square avatar suitable for exporting to PNG (e.g. 400×400) for social profiles.

You can open these SVGs in a vector editor (Inkscape, Figma, etc.) to tweak colours or export PNGs.
