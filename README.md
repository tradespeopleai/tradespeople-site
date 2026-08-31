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
| `privacy.html` | Privacy policy (EU + UK GDPR) |
| `terms.html` | Terms of service (governed by England & Wales law) |
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

## Operating entity

The site is published by **Unit 37 OÜ**, an Estonian private limited company,
registry code 16961687, Tornimäe tn 5, Kesklinna linnaosa, Tallinn, 10145.

Because the controller sits in Estonia while the service targets UK
tradespeople, the privacy policy cites both the EU and UK GDPR, and names both
the ICO and the Estonian Data Protection Inspectorate as complaint routes. The
terms still choose England & Wales law, which the parties are free to do in a
B2B contract.

## Before going live

- Not VAT-registered as of August 2026. The terms say so explicitly; revisit
  that clause and add the `EE`-prefixed number if registration happens.
- Consider a role mailbox (e.g. `hello@`) in place of the personal address.
- Consider whether a UK Article 27 representative is required.

## Deploy

Pushing to `main` publishes to GitHub Pages via `.github/workflows/deploy.yml`.
