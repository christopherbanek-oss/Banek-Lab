# Banek Lab — Website (v2)

A dark, editorial scientific website for the Banek Laboratory. Three files,
no build step, fully responsive desktop and mobile.

## Files

- `index.html` — main landing page (hero, lab focus, gallery, research, team, contact)
- `publications.html` — auto-fetches Dr. Banek's publications live from PubMed
- `styles.css` — shared stylesheet

## Run it locally

Open `index.html` in any browser. The publications page makes a live API call
to PubMed, so for that page it's slightly more reliable to serve over HTTP:

```bash
cd banek-lab
python3 -m http.server 8000
# then visit http://localhost:8000
```

## What's in v2

- **Display type:** Instrument Serif — dramatic, high-contrast, characterful
- **Body type:** Inter Tight + JetBrains Mono for accents
- **Hero:** "The Banek Laboratory" set in massive serif with the second word
  in gold italic, plus a subtle EKG-style waveform decoration that ties to
  the lab's neural-recording work
- **Brand glyph:** A small SVG of a nerve waveform with a maroon nucleus —
  a starting point for an eventual lab logo
- **Drop cap** on the lab-focus paragraph (gold italic)
- **Numbered sections** with eyebrow labels (01 / 02 / 03 / 04 / 05) and
  italic accent words on each headline
- **Project list:** lowercase Roman numerals (i / ii / iii) in oversized
  gold italic, with hover state that pulls in a subtle maroon gradient and
  reveals a gold accent line at left
- **Gallery & team:** placeholder tiles styled with subtle gradients and
  corner numerals — when you add real photos, the placeholders disappear
- **Contact card:** maroon-to-gold accent line on the left, soft glow in the
  bottom-right corner
- **Publications:** grouped by year (sticky year headers in gold italic),
  with live filter, your name highlighted in maroon, and graceful fallback
  if PubMed is unreachable

## Adding your own content

### Team photos
In `index.html`, find the `member` blocks and uncomment / add an `<img>`
inside the `.photo` div. Drop your image into an `images/` folder next to
the HTML:
```html
<div class="photo">
  <span class="corner">/ 01</span>
  <img src="images/banek.jpg" alt="Christopher T. Banek, PhD" />
</div>
```
The "Photo to come" placeholder disappears automatically.

### Lab gallery photos
Same idea — find the `.gallery .tile` divs and add `<img>` tags inside.
Tiles come in `lg`, `md`, `sm`, and `tall` sizes.

### Adding more team members
Copy any `<article class="member">` block and edit the role, name, and bio.
The grid auto-flows.

### Tightening the PubMed query
If publications by other authors with the initials "Banek CT" start showing
up, edit the `PUBMED_QUERY` constant in `publications.html`:
```js
const PUBMED_QUERY = "Banek+CT[Author]";
// or: "Banek+CT[Author]+AND+Minnesota[Affiliation]"
// or: "Banek+Christopher+T[Author]"
```

## Hosting

Plain HTML/CSS/JS — works on any web host:
- UMN shared hosting (just SFTP the three files)
- GitHub Pages
- Netlify, Vercel, Cloudflare Pages (drag-and-drop the folder)
