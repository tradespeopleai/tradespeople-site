# Tradespeople — marketing site

Static one-pager plus UK privacy policy and terms of service for
[Tradespeople](../prototype), the AI back office for UK sole-trader tradespeople.

No build step. Plain HTML + one stylesheet.

## Local preview

```bash
python3 -m http.server 8899
# → http://localhost:8899
```

## Files

| File | Purpose |
|---|---|
| `index.html` | One-page site |
| `privacy.html` | Privacy policy (UK GDPR) |
| `terms.html` | Terms of service (England & Wales) |
| `styles.css` | Shared stylesheet, palette matched to the Pro app |
| `logo.png` | Round logo, 500×500 |
| `logo-120.png` | Round logo, 120×120 |
| `logo-source.jpeg` | Original square logo |
| `favicon.ico`, `favicon-32.png`, `apple-touch-icon.png` | Icons, generated from the logo |

Regenerate the round logo and icons from a new square source:

```bash
magick -size 500x500 xc:'#1a1a1a' \
  \( logo-source.jpeg -resize 380x380 \) -gravity center -composite \
  \( -size 500x500 xc:none -fill white -draw 'circle 250,250 250,3' -alpha copy \) \
  -compose CopyOpacity -composite PNG32:logo.png
```

## Before going live

Replace the placeholders in `privacy.html` and `terms.html`:
`[Company Name] Ltd`, `[00000000]`, `[Registered Address]`, and confirm
`hello@tradespeople.co.uk` is a mailbox that exists.

## Deploy

Pushing to `main` publishes to GitHub Pages via `.github/workflows/deploy.yml`.
