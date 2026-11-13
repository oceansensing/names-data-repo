# names-data-repo

The **names** of land and water, and their administrative context: a data repository of the oceansensing ocean map system, with its own
schedule and its own place on Cloudflare R2, and no code of its own.

**Publishing since 2026-11-11**, once a month. `PLAN.md` is the founding plan; `CLAUDE.md` carries what must not be
got wrong and the shared doc doctrine.

## What it publishes

The names of land and water as label points, once a month, in one file, `names.json`: each name with its kind (ocean, sea, strait, country, capital, city, state or province, county, district, land region, peak, lake, river, undersea feature), a detail (a state's type, a district's term in its country, an undersea feature's kind), the point it is written at, **the zoom it is named from** (and to, where its source says), a peak's height, its country, and **its parent** — the state or province and the country it is in. Rows in the order a map places them: by kind's rank, then by zoom, the larger or better known first. The header credits every source and each district country's license, source and term. R2's alone.

**And the districts' and counties' borders** (since 2026-11-12, the product `borders`): the edges two of the areas the names name share — the Census's counties and the districts of each country kept — never a coast or a country's outer edge. A root, `district-borders.json`, names a version of the tree `land/district-borders/`, whose `index.json` names its tiers and their tiles: **states**, the states' lines alone simplified to 0.02° in 30° tiles, drawn from zoom 4 to 6 (since 2026-11-13); **coarse**, simplified to 0.002° in 20° tiles, drawn to zoom 9; **fine**, the sources' own detail in 5° tiles, from zoom 9. Each tile is `{"lines": [[[lon, lat], …], …], "states": […]}`, named `<south>_<west>`: `lines` the edges between two areas of one state, `states` those between two states (since 2026-11-12) — and, for the countries no district set covers, Natural Earth's own state lines (1:50m) — either left out where a tile has none. The root credits the same sources as `names.json`. R2's alone; the tree carried between runs by the workflow's cache, made again once a month or when a run's stage lacks it.

**And the named areas' outlines** (since 2026-11-12, the product `areas`): each area the names name — the Census's counties and the districts of each country kept — its outline simplified to 0.002° (about 220 m), with its name, its country's term for it and its state or province, so a reader can say which district or county a point is in. A root, `district-areas.json`, names a version of the tree `land/district-areas/`, whose `index.json` names its 5° tiles; each tile is `{"areas": [{"name", "term", "parent", "country", "polygons"}, …]}`, named `<south>_<west>`, an area across a tile's edge cut there and in each tile it meets, each polygon a list of closed rings of `[lon, lat]`, its outer ring first. **One area once**: an area two files both hold (Puerto Rico's municipios, the Census's and geoBoundaries') is kept once, the Census's, and one another file divides finer (Guam) gives way to the finer; where two countries' files otherwise overlap — a disputed place, or a file drawn past its border — both are kept. Made by the borders' step from the same download; R2's alone, the tree carried by the workflow's cache as the borders' is. **The names rows come from the same areas** since: a district named as its state is kept when it is under half its state (São Paulo's city, Kabul's district).

**And the EEZ boundaries** (since 2026-11-13, the product `eez`): every line of Marine Regions' Maritime Boundaries Geodatabase (`eez_boundaries`, version 12 at the first build: 2,349 lines), the baselines the zones are measured from included, each classed by its `line_type` into one of six kinds — `limit` (200 NM, 12 NM, an undisputed unilateral claim), `boundary` (a treaty, a median line, a court ruling), `joint` (a joint regime), `unsettled` (a line in dispute, at sea or over land), `baseline` (straight, archipelagic, normal) and `connection` (a connection line); a type not classed refuses the build. A root, `eez-boundaries.json`, names a version of the tree `land/eez-boundaries/`, whose `index.json` names its tiers and their tiles: **world**, simplified to 0.05° in 90° tiles, drawn to zoom 4; **coarse**, simplified to 0.005° in 30° tiles, from zoom 4 to 8; **fine**, the source's own detail to 0.0001° in 10° tiles, from zoom 8. Each tile is `{"<kind>": [[[lon, lat], …], …], …}`, named `<south>_<west>`, holding the kinds it has. Made by a step of its own once a month, from one request to Marine Regions' WFS; R2's alone, the tree carried by the workflow's cache as the borders' is. **Not for legal, economic or navigational use** (Marine Regions' terms).

These products are published to **Cloudflare R2 alone**, for a downstream reader: no Pages site,
and the website neither draws nor lists them (the site pipeline's D13).

## Where the data comes from

**Natural Earth** 10m (public domain; its own label points and ranks), **GeoNames**' undersea features (CC BY 4.0; `allCountries.zip` and `featureCodes_en.txt`), the **U.S. Census Bureau**'s 2024 cartographic boundaries of the counties (public domain) and **geoBoundaries** gbOpen ADM2 (CC BY 4.0, each country under its own license; Runfola et al. 2020, PLoS ONE 15(4): e0231866). **Their terms were read before a line was written** (2026-11-11), each country's geoBoundaries license among them: a country is kept only where its license allows commercial use with credit (an allowlist in the fetcher); share-alike licenses and permissions given to geoBoundaries alone leave its districts out. **And Marine Regions'** Maritime Boundaries Geodatabase (Flanders Marine Institute; CC BY 4.0 since its version 11, 2019; cited as *Flanders Marine Institute (2026): MarineRegions.org*), read 2026-11-13: its products are not made available for download here, only the lines drawn from them, on R2 behind a reader's host.

## How it runs

The orchestrator (the site's private `pipeline/`), the fetchers and the
published-file contract all come from `oceansensing.github.io`, checked out at
run time. This repository carries `pipeline/products.toml` and its publish
workflow, and nothing else executable. Each run publishes to Cloudflare R2 alone
(the site pipeline's D13). Related repositories: none it depends on.

**Which document gets what, and what "update docs" means across all
thirty-six repositories, is the doctrine block at the top of `CLAUDE.md`**: the
same text in all thirty-six, held equal by the site's `check:docs`.

## Structure

```
README.md       what this is
CLAUDE.md       what must not be got wrong, and the shared doc doctrine
PLAN.md         the founding plan and running record
DECISIONS.md    dated one-way decisions, D1 onward
pipeline/       products.toml, the declaration the orchestrator reads
.github/        the publish workflow
```
