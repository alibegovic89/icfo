# Deploy iCFO to icfolimited.com (GitHub Pages)

## Why a public repo?

GitHub Pages serves a website **from a repository**, and it can only serve from
a **public** repo (on the free plan). It cannot serve from this private repo.
So we keep the split you already use for robertpersonalfinance:

- **This private repo** (`claude-code-v1`) = source of truth. Strategy docs,
  pricing, client data, secrets — all stay here, private.
- **A new public repo** = just the published website files. Everything in it is
  already visible to any site visitor, so nothing sensitive is exposed.

The files to publish live in this folder (`ventures/icfo/site/`).

## Files to upload (this folder)

- `index.html` — the landing page
- `impressum.html` — legal notice (required in Germany)
- `datenschutz.html` — privacy policy (required in Germany)
- `CNAME` — contains `icfolimited.com` (tells GitHub Pages your custom domain)
- `.nojekyll` — serves the files as-is

## Steps

1. **Create the repo.** On GitHub, new **public** repo under `alibegovic89`,
   e.g. `icfolimited`.
2. **Upload the 5 files** into the repo root (GitHub's "Add file → Upload files"
   works from iPad Safari). Keep the filenames exactly as above.
3. **Turn on Pages.** Repo **Settings → Pages → Build and deployment →
   Source: Deploy from a branch → `main` / `/ (root)` → Save.**
4. **Custom domain.** In the same Pages screen, set **Custom domain** to
   `icfolimited.com` and Save. (The `CNAME` file already sets this too.)
5. **DNS at GoDaddy.** In the icfolimited.com DNS settings:
   - Add four **A** records for the apex (`@`) pointing to GitHub Pages:
     - `185.199.108.153`
     - `185.199.109.153`
     - `185.199.110.153`
     - `185.199.111.153`
   - Add a **CNAME** record: `www` → `alibegovic89.github.io`
   - Remove any GoDaddy "parking" A/CNAME records that conflict.
6. **HTTPS.** Back in Settings → Pages, wait until the domain check passes, then
   tick **Enforce HTTPS**. DNS can take from minutes up to ~24h.

## After it's live — quick checks

- `https://icfolimited.com` loads with a padlock (HTTPS).
- Footer **Imprint** / **Privacy** links open `impressum.html` / `datenschutz.html`.
- Submit the form once — the enquiry should arrive (Formspree emails it to you;
  confirm the address on your Formspree form is `icfolimited@gmail.com`).
- Visits show up in your GoatCounter dashboard (`icfo.goatcounter.com`).

## Before going live — housekeeping

- **Formspree:** sign the DPA (Formspree dashboard) since it processes EU
  personal data; confirm notifications go to `icfolimited@gmail.com`.
- **GoatCounter:** keep the default privacy settings (no personal data).
- **Legal review:** have the Impressum/Datenschutz checked by a qualified
  adviser before scaled use — the pages are accurate to what we know but this
  is not legal advice.
