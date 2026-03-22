# CourtConnect — GitHub Pages site

Static landing page for **CourtConnect**: the Flutter app, Spring Boot backend, and project links.

## What’s here

| File | Purpose |
|------|---------|
| `index.html` | Home page (hero, features, contact email) |
| `privacy.html` | Privacy Notice (Shuttle Swap Labs / CourtConnect) |
| `terms.html` | Terms of Use |
| `css/styles.css` | Base styling |
| `css/legal.css` | Typography & layout for legal pages |
| `assets/app-icon-512.png` | App icon (same as Flutter / IconKitchen `web/icon-512.png`) |
| `favicon.ico`, `apple-touch-icon.png` | Favicons from IconKitchen `web/` output |

## Enable GitHub Pages

1. Push this repository to GitHub.
2. On the repo: **Settings → Pages**.
3. **Source:** Deploy from a branch.
4. **Branch:** `main` (or `master`) and folder **`/ (root)`**.
5. Save. After a minute, the site is available at:

   `https://<username>.github.io/<repository>/`

   Example: `https://yourname.github.io/courtconnect-site/`

## Customize before sharing

Edit **`index.html`**:

- **Play Store:** uncomment the script at the bottom and set the real Play Store URL, or change the **Get the app** button `href`.
- **Contact:** support email is set in the mailto link (update if it changes).

## Local preview

Open `index.html` in a browser, or from this directory:

```bash
python3 -m http.server 8080
```

Then visit `http://127.0.0.1:8080`.

## Notes

- Assets use **relative** paths (`css/styles.css`) so they work for project sites under a subpath.
- No build step — plain HTML/CSS only.
