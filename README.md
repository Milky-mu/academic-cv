# Academic Website

![Layout preview](.github/preview.webp)

A personal academic website built with [Hugo Blox](https://hugoblox.com/) and
deployed to GitHub Pages. Everything is plain text — Markdown and YAML — so you
edit it in any editor and publish by pushing to `main`.

---

## Start here: five files

Do these in order and the site is yours.

| # | File | What to change |
|---|------|----------------|
| 1 | `data/authors/me.yaml` | **The big one.** Your name, role, bio, links, interests, education, experience, skills, awards. Most of the homepage comes from here. |
| 2 | `assets/media/authors/me.png` | Replace with your own photo. Square, at least 640×640. Keep the filename. |
| 3 | `config/_default/params.yaml` | `identity.name`, `tagline`, `description` near the top. |
| 4 | `config/_default/hugo.yaml` | `baseURL` — must match where the site is served (see below). |
| 5 | `static/uploads/resume.pdf` | Replace with your actual CV. Keep the filename, or update the button in `content/_index.md`. |
| 6 | `content/_index.md` | The `contact-info` block at the bottom — department address, office hours, and the job-market call-out. |
| 7 | `assets/media/icons/custom/` | *Optional.* University logo SVGs for LinkedIn-style education emblems — see the README in that folder. |

> **Placeholders still in the repo:** the photo and `resume.pdf` are the
> template's demo files, not yours. Replace both before you share the link.

---

## Adding content

Every section works the same way: **one folder per item** inside `content/`.
Copy the `example-*` folder, rename it (the folder name becomes the URL), edit
the fields at the top, then delete the example.

| Section | Where | Shows up on |
|---------|-------|-------------|
| **Publications** | `content/publications/` | Homepage `#papers` + `#publications` |
| **Talks** | `content/events/` | Homepage `#talks` |
| **News** | `content/news/` | Homepage `#news` |
| **Projects** | `content/projects/` | `/projects/` |
| **Teaching** | `content/teaching/` | `/teaching/` |
| **Education & Experience** | `data/authors/me.yaml` | Homepage + `/experience/` |
| **Contact** | `content/_index.md` (last block) | Homepage `#contact` |

A few things worth knowing:

- **Featured publications.** Set `featured: true` on a paper and it appears in
  the "Selected Publications" grid at the top. Everything appears in the full
  citation list regardless.
- **Thumbnails.** Drop a `featured.jpg` or `featured.png` into an item's folder
  and it becomes the card image. No file, no image — that's fine.
- **Upcoming vs. past talks** are decided by the `event_start` date.

### Importing publications from BibTeX

Instead of writing each paper by hand: export a `.bib` file from Google Scholar
or Zotero, save it as **`publications.bib` in the repo root**, and push. The
`Import Publications From Bibtex` GitHub Action turns every entry into a
publication page and opens a pull request with the result.

---

## Editing the page layout

`content/_index.md` is the homepage. Its `sections:` list is rendered top to
bottom — reorder the blocks to reorder the page, delete one to remove it.

Two things must stay in sync: a block's `id:` and the matching `/#id` link in
`config/_default/menus.yaml`. Change one, change the other.

---

## Publishing

Pushing to `main` triggers `.github/workflows/deploy.yml`, which builds the site
and deploys it to GitHub Pages.

**One-time setup:** on GitHub, go to *Settings → Pages* and set **Source** to
**GitHub Actions**.

This site is served from the custom domain **muziouyang.com**, set under
*Settings → Pages → Custom domain*. Because the deploy goes through GitHub
Actions rather than a branch, no `static/CNAME` file is needed — GitHub ignores
one if present. The domain lives only in the repo settings.

**The deploy ignores `baseURL` in `config/_default/hugo.yaml`.**
`.github/workflows/build.yml` builds with
`--baseURL "${{ steps.pages.outputs.base_url }}/"`, and that value comes from
`actions/configure-pages`, which reads the domain out of *Settings → Pages*.
So the repo setting wins, and editing the config file will not change the
deployed site. Keep the config value correct anyway — `hugo server` uses it
locally, and it would apply again if the deploy ever moved off Actions.

One consequence: `configure-pages` reports the site as `http://` until
**Enforce HTTPS** is enabled in *Settings → Pages*. Turn that on, then rerun the
deploy, or absolute URLs in the page metadata (`og:url`, canonical) keep the
`http://` scheme even though visitors are redirected to HTTPS.

### DNS records

At the registrar, for the apex domain:

| Type | Name | Value |
| --- | --- | --- |
| A | `@` | `185.199.108.153` |
| A | `@` | `185.199.109.153` |
| A | `@` | `185.199.110.153` |
| A | `@` | `185.199.111.153` |
| AAAA | `@` | `2606:50c0:8000::153` |
| AAAA | `@` | `2606:50c0:8001::153` |
| AAAA | `@` | `2606:50c0:8002::153` |
| AAAA | `@` | `2606:50c0:8003::153` |
| CNAME | `www` | `milky-mu.github.io.` |

The `www` CNAME lets GitHub redirect `www.muziouyang.com` to the apex. Once DNS
resolves, tick **Enforce HTTPS** in *Settings → Pages*.

---

## Previewing locally (optional)

Not required — you can edit and push blind, and the Action will tell you if
something breaks. But a local preview is much faster to work with.

You need [Hugo Extended](https://gohugo.io/installation/) (see
`hugoblox.yaml` for the version this site is built with), [Go](https://go.dev/dl/),
and [Node.js](https://nodejs.org/):

```bash
npm install -g pnpm
pnpm install
pnpm dev
```

Then open <http://localhost:1313/>. The page reloads as you save.

---

## Configuration reference

| File | Controls |
|------|----------|
| `config/_default/params.yaml` | Identity, colors, fonts, header/footer, analytics, comments, SEO |
| `config/_default/hugo.yaml` | `baseURL`, language, page options |
| `config/_default/menus.yaml` | Navigation bar |
| `config/_default/languages.yaml` | Multilingual setup (commented out by default) |
| `hugoblox.yaml` | Hugo version and deploy target |

Useful knobs in `params.yaml`:

- `theme.colors.primary` — accent color, a Tailwind name (`indigo`) or hex
- `theme.mode` — `light`, `dark`, or `system`
- `content.math.enable` — set `true` for LaTeX in your pages
- `content.citations.style` — `apa`, `mla`, `chicago`, or `ieee`
- `analytics.*` — Google Analytics, Plausible, and others

Full documentation: <https://docs.hugoblox.com/>

---

Built on the [Hugo Blox](https://github.com/HugoBlox/hugo-blox-builder)
Academic CV template. Licensed under MIT — see `LICENSE.md`.
