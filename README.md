# Vyrnexis — Dark Tech Blog (Jekyll)

Minimal dark-themed Jekyll blog with accent toggle, responsive layout, and easy customization via `_config.yml` and `_data/links.yml`.

## Structure

```text
vyrnexis.github.io/
├── index.html               # Home lists posts
├── about.md                 # About page content
├── _config.yml              # Site settings, brand text, sidebar text
├── _data/
│   └── links.yml            # Sidebar links + icons
├── _layouts/
│   └── default.html         # Main layout, CSS, JS
├── _posts/                  # Blog posts (Markdown)
│   └── 2025-12-04-welcome-to-vyrnexis.md
└── assets/                  # Logos, avatar, icons
    ├── logo-vyrnexis.svg
    ├── avatar-vyrnexis-400.svg
    ├── icon-github.svg
    ├── icon-youtube.svg
    ├── icon-discord.svg
    ├── icon-portfolio.svg
    └── icon-mail.svg
├── favicon.ico              # Generated from assets/vyrnexis.png
```

## Customization

- Brand/subtitle/sidebar text: edit `_config.yml` (`brand_name`, `brand_subtitle`, `sidebar_handle`, `sidebar_subtext`).
- Sidebar links/icons: edit `_data/links.yml` (label, url, icon path). Add more entries as needed.
- Accent toggle: persists via localStorage; palettes are in `_layouts/default.html`.
- Images in posts: use standard Markdown `![Alt]({{ '/assets/your-image.png' | relative_url }})` and they’ll auto-fit the column.

## Adding Posts

1. Create `_posts/YYYY-MM-DD-title.md`
2. Add front matter:
   ```yaml
   ---
   layout: default
   title: "My Post Title"
   date: 2025-12-10
   author: "Your Name"
   ---
   ```
3. Write in Markdown. Example:
   ```markdown
   This is a post.

   ![Alt text]({{ '/assets/example.png' | relative_url }})

   - bullet 1
   - bullet 2
   ```
4. Commit and push; the home page lists it automatically.

## Running Locally (optional)

You don’t need to install anything to deploy on GitHub Pages (it runs Jekyll for you). If you want to preview locally and have Jekyll installed:

```bash
jekyll serve
# open http://localhost:4000
```

## Deploy to GitHub Pages

1. Create a repo named `<username>.github.io`.
2. Push this project to `main`.
3. GitHub Pages will build automatically using its built-in Jekyll.
4. Visit `https://<username>.github.io/`.

## Notes

- Scroll behavior: custom JS smooth-scrolls anchors and avoids jumpy back navigation.
- Accent theme: toggles between teal/purple and remembers your choice.
- Assets: SVG icons live in `assets/`; replace with your own if desired.
