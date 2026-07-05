# Jyotisha — Vedic Astrology (PWA)

An astronomically computed Tamil/English Vedic horoscope app. Planetary positions are
computed with the Lahiri ayanamsa (via Don Cross's `astronomy-engine`); the app then
applies classical Jyotisha rules to produce a full jathagam — twelve houses, all sixteen
vargas, Navamsa/Dasamsa/Saptamsa cross-checks, Vimshottari + Jaimini Chara + Yogini dashas,
Ashtakavarga, Shadbala/Bhava-Bala, Gochara transits, and Varshaphal — entirely offline.

## What's in this folder
```
index.html                 the whole app (self-contained: engine + UI + readings)
manifest.webmanifest       PWA manifest (name, icons, colours)
sw.js                      service worker (offline caching)
vendor/jspdf.umd.min.js    PDF generation (MIT)
vendor/html2canvas.min.js  render-to-image for PDF (MIT)
icons/                     app icons (192/512 + maskable + apple-touch)
```

## Deploy free on GitHub Pages
1. Create a new GitHub repository, e.g. `jyotisha`.
2. Upload **all** the files in this folder, keeping the folder structure
   (`vendor/` and `icons/` must stay as sub-folders). On github.com you can drag the
   whole set into "Add file → Upload files".
3. In the repo, go to **Settings → Pages**.
4. Under "Build and deployment", set **Source = Deploy from a branch**, **Branch = main**,
   **Folder = / (root)**, then **Save**.
5. Wait ~1 minute. Your app is live at
   `https://<your-username>.github.io/<repo-name>/`

Because Pages serves over HTTPS, the service worker and "install app" both work.

## Install on your phone (as an app)
- **iPhone / iPad (Safari):** open the Pages URL → Share → **Add to Home Screen**.
- **Android (Chrome):** open the URL → menu → **Install app** / **Add to Home screen**.

After installing it launches full-screen, keeps working with no internet, and shows the
sun icon on your home screen.

## Saving a horoscope as PDF
1. Fill in the birth details and generate the chart.
2. Open the **AI Reading** tab and tap **★ Full life reading** for the complete report
   (or use any topic).
3. Tap **PDF / print** (the print button in the header) to open the report, then:
   - **Download PDF** — saves a real `.pdf` file (renders Tamil correctly), or
   - **Print** — uses your browser's *Save as PDF* / *Save to Files*.

## Notes
- **Everything works offline** — charts, all readings, dashas, transits, and PDF export.
- The optional **live-AI reading** calls Anthropic's API and only works inside the Claude
  app runtime; on your own hosted site it will simply fall back to the built-in
  **computed readings**, which are the full-featured, rule-based interpretations.
- To publish an update later, replace the files and bump the cache name in `sw.js`
  (`jyotisha-v1` → `jyotisha-v2`) so devices pick up the new version.

## Credits
- Astronomy: `astronomy-engine` by Don Cross (MIT)
- PDF: `jsPDF` and `html2canvas` (MIT)
- Fonts: Fraunces, Inter, Noto Sans Tamil (Google Fonts, OFL)

For guidance and reflection; not a substitute for professional advice.
