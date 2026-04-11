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

## Deep linking (App Links / Universal Links)

This repo hosts the verification files for shared game URLs (`/game/*`) used by the Flutter app.

| File | Purpose |
|------|---------|
| `.well-known/apple-app-site-association` | iOS Universal Links — uses Team ID `54M5J42GVY` with dev and prod bundle IDs. |
| `.well-known/assetlinks.json` | Android App Links — **edit** each `REPLACE_WITH_*` with real SHA-256 fingerprints from Play Console / your keystore (see below). |
| `.nojekyll` | Tells GitHub Pages **not** to run Jekyll so `.well-known` is published as static files. |

After pushing, verify (replace host if you use `www` only):

```bash
curl -sS "https://court-connect-hub.com/.well-known/apple-app-site-association" | head
curl -sS "https://court-connect-hub.com/.well-known/assetlinks.json" | head
```

**Android SHA-256**

- **Prod** (`com.courtconnect.court_connect`): Google Play Console → **Release** → **App integrity** → **App signing** → **App signing key certificate** → SHA-256.
- **Dev** (`…court_connect.dev`): debug keystore (`keytool -list -v -keystore ~/.android/debug.keystore …`) and/or the signing key used for that flavor.

**iOS / apex vs `www`**

- Repo `CNAME` is **`www.court-connect-hub.com`**. The Flutter app uses share links on **`court-connect-hub.com`** (apex).
- For Universal Links to verify, the **same host** that appears in links must serve the AASA file. Either:
  - Configure **both** apex and `www` for this GitHub Pages site in **Settings → Pages → Custom domain** and DNS (see [GitHub docs](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/about-custom-domains-and-github-pages)), **or**
  - Change the app’s `kGameShareDeepLinkHost` to `www.court-connect-hub.com` so it matches where Pages is primary.

## Notes

- Assets use **relative** paths (`css/styles.css`) so they work for project sites under a subpath.
- No build step — plain HTML/CSS only.
