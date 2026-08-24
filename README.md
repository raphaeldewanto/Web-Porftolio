# Raphael Jonathan — Portfolio Website

A single-page portfolio site: black & white, sharp edges, serif type, built to showcase 10 WordPress projects with a hover-preview index list and full case-study popups.

## Files

```
index.html          → the entire site (structure, styles, and behavior in one file)
images/              → project screenshots, referenced by index.html
  allstar.webp
  hideaway.webp
  itb.webp
  kidssoho.webp
  kmf.webp
  malupilates.webp
  mantra.webp
  royalaventus.webp
  tijilibenoa.webp
  tijiliseminyak.webp
```

**Keep `index.html` and the `images` folder together, in the same directory, at all times.** The image paths inside the HTML are relative (e.g. `images/allstar.webp`), so if the two are separated, images won't load.

## How to view it

Just double-click `index.html` to open it in any browser. No build step, no server required — it's a self-contained static page.

## How to deploy it

Any static host works, since there's nothing to build. A few easy options:

- **Netlify / Vercel** — drag the whole folder (`index.html` + `images/`) into their web dashboard.
- **GitHub Pages** — push both into a repo, enable Pages on the `main` branch.
- **Your own hosting / cPanel** — upload both into `public_html` (or your web root) via FTP.

## How to add or update a project

Open `index.html` and search for `const projects = [` — this is the array that drives the whole "Selected Work" section. Each project is one object:

```js
{
  slug: "allstar",
  name: "All Star Legian",
  category: "Restaurant & Sports Bar",
  url: "https://allstarlegian.com/",
  brief: "...",
  challenge: "...",
  solution: "...",
  highlight: "..."
}
```

- **To add a new project:** copy an existing object, change every field, and give it a unique `slug`. It will automatically appear in the list, numbered correctly, with a working hover preview and modal — no other code changes needed.
- **To remove a project:** delete its whole `{ ... },` block from the array.
- **To reorder projects:** just move the objects up or down within the array — the row numbers (01, 02, 03…) are generated automatically from position, not hardcoded.

## How to swap in a new image

1. Drop the image file into `images/`, named to match the project's `slug` (e.g. `images/allstar.webp`).
2. In `index.html`, find the section commented `PROJECT THUMBNAILS — REAL IMAGES` near the top of the `<style>` block.
3. Add two lines for the new slug (copy an existing pair and change the slug + filename):

```css
.thumb[data-project="yourslug"] { background-size: cover; background-position: center; background-repeat: no-repeat; }
.thumb[data-project="yourslug"] { background-image: url('images/yourslug.webp'); }
```

That image will then automatically show in three places: the hover-preview (desktop), the inline thumbnail (mobile), and the case-study modal.

**Recommended image spec:** 1600×900px (or similar 16:9), exported as WebP or JPG, compressed to roughly 150–300KB each.

## Editing contact info

Search for `id="contact"` in `index.html` — the email, WhatsApp, and LinkedIn links are plain `<a href="...">` tags right below it. Edit the `href` and visible text directly.

## Notes

- No frameworks, no dependencies, no build tools — plain HTML, CSS, and vanilla JavaScript.
- Fonts fall back to Georgia/serif if "Anthropic Serif" isn't installed on the visitor's system.
- The cursor-follow image preview is desktop-only; mobile automatically shows an inline thumbnail instead.
- Respects `prefers-reduced-motion` for visitors who have that OS setting enabled.
