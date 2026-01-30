# CLAUDE.md

This file provides guidance to Claude Code when working with code in this repository.

## Project Overview

Static website for the New College Poker Society (NCPS) at the University of Oxford. Serves as the society's public-facing site and sponsorship deck.

**Live site:** https://aaronrose227.github.io/NCPS/

## Technology

- Pure HTML and CSS — no frameworks, no JavaScript, no build step
- Hosted on GitHub Pages (deploys from `main` branch)
- Styled with a shared `style.css` across all pages

## Design

- Minimal, inspired by https://devanshpanda.com/
- Charcoal background (`#2b2b2b`), white text (`#fff`), serif font
- Homepage is centered vertically and horizontally with the logo inline beside the title
- Subpages use a left-aligned 600px max-width column with the NCPS logo fixed in the top right
- Fully responsive — uses percentages, `vw` units, and media queries for mobile

## File Structure

```
index.html          # Homepage — centered title, nav, Instagram link
about.html          # About the society
sponsor.html        # Sponsorship info with CSS poker table graphic
committee.html      # Committee members and roles
gallery.html        # Photos from sessions
contact.html        # Contact email
style.css           # Shared stylesheet for all pages
logo.png            # NCPS logo (transparent background, white)
sig-logo.png        # Susquehanna SIG sponsor logo (white version)
og-image.jpg        # Open Graph preview image (logo on charcoal)
gallery/            # Photo assets
  session1.jpg      # Cash game session photo
README.md           # Repo README
```

## Key Details

- **Sponsor page poker table**: CSS-drawn oval table with seats positioned using percentages for responsiveness. Sponsors get their logo at a seat with chips; empty seats show "open seat" in grey italic.
- **Open Graph tags**: Every page has OG meta tags for link previews. The image is `og-image.jpg` (logo on charcoal background, 1200x630).
- **Images**: Photos should be converted from HEIC to JPEG and compressed before adding. Use `sips` for conversion and resizing.
- **Instagram**: Linked on homepage with an inline SVG icon.

## Deployment

Changes pushed to `main` branch auto-deploy to GitHub Pages. After pushing, the live site updates within a couple of minutes.

```bash
git add .
git commit -m "Description of change"
git push origin main
```

## Adding Content

### New gallery photo
1. Convert to JPEG: `sips -s format jpeg photo.HEIC --out gallery/name.jpg`
2. Compress: `sips --resampleWidth 1200 -s formatOptions 70 gallery/name.jpg`
3. Add a new `<div>` block in `gallery.html` with the image and caption

### New sponsor
In `sponsor.html`, replace an "open seat" div with:
```html
<div class="seat seat-N">
  <img class="seat-logo" src="sponsor-logo.png" alt="Sponsor Name">
</div>
```
Add chips on the table for that seat:
```html
<div class="table-chips table-chips-N">
  <span class="chip chip-red"></span>
  <span class="chip chip-blue"></span>
  <span class="chip chip-black"></span>
</div>
```

## Contact

Society email: aaronij54@gmail.com
Instagram: @newcollegepokersoc
