# whatcani.build

Static web site for **whatcani.build** — the trading name of Bakos & Evans Pty Ltd
(ABN 25 622 644 464), an urban-planning consultancy in Sydney, NSW.

Eight hand-written HTML pages. No CMS, no build step, no generator.

---

## Deployment

Hosted on Vercel, auto-deploying from the `main` branch of this repository.

**The repository root is the web root.** A file committed as `index.html` is served
at `https://whatcani.build/index.html`; a file committed as `images/floor-plan.jpg`
is served at `https://whatcani.build/images/floor-plan.jpg`.

There is no `site/` folder in this repository. When uploading from the local working
copy, drag the *contents* of the local `site/` folder to the repository root — never
the folder itself, or the files land one level too deep and every path 404s.

## Source of truth

The live site is the single source of truth. Each page's HTML in this repository is
the only copy of its content.

Before editing, pull the current live pages down into the local working copy
(`sync-from-live.command`). Editing a stale local copy and pushing it is what causes
the site to revert to older versions.

Do not add a page generator or template script to this repository, and do not keep a
second copy of the page wording in a separate Markdown file. Both have caused reverts
before.

## Layout

| Path | Contents |
|---|---|
| `index.html` | Home |
| `about.html` | The practice and its principals |
| `services.html` | Service tiers |
| `pricing.html` | Fixed fees, GST inclusive |
| `blog.html` | Articles, published as in-page overlays |
| `testimonials.html` | Client outcomes and project snapshots |
| `contact.html` | Enquiry form (Formspree) |
| `legals.html` | Legal notices — do not edit without instruction |
| `images/` | Site photography, plus an image map in `images/README.md` |
| `logo-*.svg`, `dwelling-type-*.svg` | Brand and illustration assets |

Each page carries its own complete copy of the CSS. Any style fix or new component
must be applied identically to all eight files.

## Progressive Web App

The site is installable via Chrome's "Install page as app" and iOS Safari's
"Add to Home Screen".

| File | Purpose |
|---|---|
| `manifest.json` | Web app manifest — name, colours, icon set |
| `icon-192.png`, `icon-512.png`, `icon-1024.png` | Standard icons, artwork at 66% of the canvas |
| `icon-192-maskable.png`, `icon-512-maskable.png` | Maskable icons, artwork at 58% so nothing clips under a circular crop |
| `apple-touch-icon.png` | 180x180, used by iOS |
| `favicon.svg`, `favicon-32.png`, `favicon-16.png`, `favicon.ico` | Browser tab icons |

All icons are the house-and-question-mark mark in white and orange on black.

Two constraints worth remembering. Every icon path must resolve from the web root —
if an icon 404s, Chrome and Safari silently fall back to a generic letter tile. And
the manifest's icon list must not lead with an SVG entry, because iOS cannot render
one as a Home Screen icon and will fall back to that same letter tile.

## Stack

Vercel (hosting) · Formspree (forms) · Titan via Crazy Domains (email).

**The DNS MX records must never be touched.**
