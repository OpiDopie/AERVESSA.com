# AERVESSA Website

A simple, static website for AERVESSA (commercial scenting & managed
diffusion). Built with plain HTML, CSS, and JavaScript — no build tools,
frameworks, or installs required — so it's easy to edit and ready to host
for free on GitHub Pages.

## File structure

```
aervessa/
├── index.html        ← the one-page site (About, Pricing, Areas, Reviews, Contact)
├── css/
│   └── styles.css     ← all styling, colors, fonts, and animations
├── js/
│   └── main.js         ← mobile menu, scroll animations, footer year
└── README.md
```

Everything is in three files on purpose. When you're ready to add more
pages, copy `index.html` to a new file (e.g. `services.html`), keep the
same `<head>` and the `css/js` links, and just change the `<body>` content.
Add a link to it in the `<nav class="main-nav">` block in every page.

## How to host it on GitHub Pages (free)

1. **Create a GitHub account** if you don't have one, at github.com.
2. **Create a new repository** — for example, name it `aervessa-website`.
   Keep it Public (GitHub Pages requires a public repo on free accounts).
3. **Upload the files.** On the repo page, click "Add file" → "Upload
   files," then drag in everything from this `aervessa` folder
   (`index.html`, the `css` folder, the `js` folder, this `README.md`).
   Make sure the folder structure stays intact — `styles.css` should end
   up at `css/styles.css` in the repo, not loose at the root.
4. **Turn on GitHub Pages.** Go to the repo's **Settings** tab → **Pages**
   (left sidebar). Under "Build and deployment," set **Source** to
   "Deploy from a branch," pick the `main` branch and the `/ (root)`
   folder, then click **Save**.
5. **Wait about a minute**, then refresh that Pages settings screen. GitHub
   will show your live URL, something like:
   `https://your-username.github.io/aervessa-website/`
6. Whenever you edit a file and upload the new version (or `git push` if
   you're using Git locally), the live site updates automatically within a
   minute or two.

### Using a custom domain (optional, later)
If you buy a domain (e.g. `aervessa.com`), you can point it at this site
from the same Settings → Pages screen using the "Custom domain" field —
GitHub has a guide linked right there when you get to that step.

## Editing the content

You don't need to know code to update most of the site — everything is
plain text inside `index.html`. Open the file in any text editor (or edit
directly on GitHub by clicking the pencil icon on the file page) and look
for these sections, marked with comments like `<!-- ================= ABOUT ================= -->`:

- **About Us** — `id="about"`
- **Pricing** — `id="pricing"` — each plan is one `<div class="price-card">` block. Duplicate a block to add a plan, delete one to remove it.
- **Areas Served** — `id="areas"` — add or remove `<li>City Name</li>` items in the `area-list`.
- **Reviews** — `id="reviews"` — each testimonial is one `<blockquote class="review-card">` block. Copy/paste the block to add another.
- **Contact** — `id="contact"` — update the email, phone number, and the form.

## Setting up the contact form

The contact form currently points to a placeholder:
`action="https://formspree.io/f/your-form-id"`. GitHub Pages can't run
server code, so the form needs a free third-party form handler:

1. Go to [formspree.io](https://formspree.io) and create a free account.
2. Create a new form and copy the endpoint URL it gives you
   (looks like `https://formspree.io/f/abcdwxyz`).
3. In `index.html`, find `<form class="contact-form" ... action="...">`
   and replace the placeholder URL with your real one.
4. Formspree will email you every submission. (Netlify Forms is a good
   alternative if you ever move hosting off GitHub Pages.)

## Colors & fonts (the design system)

All colors and fonts are defined once at the top of `css/styles.css`
under `:root { ... }`. Change a value there and it updates everywhere on
the site automatically — for example, `--brass-500` is the gold accent
color used on buttons and highlights, and `--plum-950` / `--plum-800` are
the deep purple tones used in the header, hero, and pricing section.

## Animations

Sections gently fade and rise into view as you scroll (the `.reveal`
class in `styles.css` + the IntersectionObserver code in `main.js`). The
hero also has a looping "diffusion rings" animation as a nod to what the
business does. All animation respects visitors' OS-level "reduce motion"
accessibility setting automatically.

## Planning future pages

Because the whole site is static HTML/CSS/JS, adding pages later (a full
Services page, a Booking page, a Blog, etc.) just means:

1. Duplicate `index.html` → rename it (e.g. `services.html`).
2. Replace the `<body>` content with the new page's content, keeping the
   header/nav and footer structure.
3. Add a link to it from the main nav in **every** HTML file so it's
   reachable site-wide.
4. Upload it to the same GitHub repo — no extra setup needed.
