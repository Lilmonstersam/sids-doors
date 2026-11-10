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

33 routes and 53 product pages, covering the five approved navigation families plus
brand, industry and service-area pages.

The November 2026 update applies the client's change list
(`docs/Sids Doors - New site changes (Nov 2026).docx`): new home page copy and enquiry
form, 4-step process, full service-area list, Sectional door openers renamed to Overhead
door openers, discontinued Merlin, Centsys, Centurion, Rotech and Gate Drive Systems
products removed, the new Merlin and Grifco opener, gate and accessory ranges added,
B&D / Steel-Line / Gliderol brochure slots on the door pages, tilt doors on application
only, and new Servicing and repairs copy with a booking form.

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

Anything still waiting on Sid's Doors is flagged in the mockup itself: a dashed yellow
"TBC" / "To be supplied" marker, a grey "Product image pending" placeholder, or a
"Details TBA" tag on product cards. Outstanding as of November 2026:

- QBCC licence number
- New home page photos, and a new photo for the myQ Gateway Bundle M828AU774
- Photos, descriptions and specs for every new product
- B&D, Steel-Line and Gliderol brochure PDFs, plus framing documents
- Confirmation on whether Merlin Silent Drive Pro MR855EVO and Quiet Drive Pro MR655EVO
  stay (not mentioned in the change list, so still shown)

Two of the three homepage testimonials are still invented placeholder copy that must not
be published. See also `docs/Sids Doors Mockup - Reviewer Notes.docx` (September review).

---

Prepared by [Digilari](https://www.digilari.com.au/).
