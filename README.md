# Sid's Doors - website structure mockup

An interactive, single-file mockup of the proposed Sid's Doors site structure, built to
accompany the SEO site structure recommendation. It is a clickable prototype, not the
production build: no back end, no forms that submit, no CMS.

**Live:** https://lilmonstersam.github.io/sids-doors/

## What's in here

| Path | What it is |
|---|---|
| `index.html` | The whole mockup: markup, styles and a hash router in one file |
| `images/` | Product, project and logo assets, referenced as `images/...` |
| `docs/` | Reviewer notes: outstanding items and what Sid's Doors still needs to supply |
| `.github/workflows/deploy.yml` | Builds and publishes to GitHub Pages on push to `main` |

## Scope

38 routes and 51 product pages, covering the five approved navigation families plus
brand, industry and service-area pages. All 50 indexable `/product/` URLs on the current
live site are represented.

Navigation is hash-based (`#/garage-door-openers/roller-door-openers/`), so the whole
prototype is one HTML file and any URL can be shared or bookmarked. Nothing needs a
build step or a server: opening `index.html` locally works exactly like the deployed
version.

## Running it locally

Open `index.html` in a browser. That's it.

If you would rather serve it over HTTP:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deployment

Pushing to `main` triggers `.github/workflows/deploy.yml`, which stages `index.html`,
`.nojekyll` and `images/` into `_site`, checks every referenced asset resolves, and
publishes to GitHub Pages. `docs/` is deliberately excluded; the reviewer notes are
internal.

**One-time setup:** in the repository, go to *Settings -> Pages* and set **Source** to
**GitHub Actions**. Without that the workflow will fail at the deploy step.

### First push

```bash
cd "Sid's Doors/seo/mockups/sids-doors"
git init -b main
git add .
git commit -m "Add Sid's Doors structure mockup"
git remote add origin https://github.com/Lilmonstersam/sids-doors.git
git push -u origin main
```

## Editing

Everything lives in `index.html`. The parts you are most likely to touch:

- `products`: the product catalogue (title, brand, copy, features, specs, brochure URL)
- `routes`: every page, its hero copy, and which products or child pages it lists
- `nav` / `familyLinks`: primary navigation and the dropdown contents
- `manuals`: the searchable document library
- `industries` / `productIndustries`: industry tagging, which is a cross-cutting filter
  and does not affect a product's canonical category or breadcrumb

Brochure links point at PDFs on `sidsdoors.com.au`; they are not mirrored here.

## Known gaps

See `docs/Sids Doors Mockup - Reviewer Notes.docx`. The short version: the four smart
connectivity kit subcategories have no products yet, nine products have no image, and
two of the three homepage testimonials are invented placeholder copy that must not be
published.

---

Prepared by [Digilari](https://www.digilari.com.au/).
