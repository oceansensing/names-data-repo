# names-data-repo: the founding plan and running record

The **names** of land and water, and their administrative context. Created on GitHub by the owner and given its documents by the site's
`pipeline/scaffold/new-origin.py`. **Publishing since 2026-11-11** (the first dispatched run, `43146399308`, 03:13 UTC
on the 12th: 64,580 names, 5.7 MB, `names` fresh, five files to R2), **its schedule daily** since, the build once a
month.

## What it is for

The names of land and water as label points, once a month, in one file, `names.json`: each name with its kind (ocean, sea, strait, country, capital, city, state or province, county, district, land region, peak, lake, river, undersea feature), a detail (a state's type, a district's term in its country, an undersea feature's kind), the point it is written at, **the zoom it is named from** (and to, where its source says), a peak's height, its country, and **its parent** — the state or province and the country it is in. Rows in the order a map places them: by kind's rank, then by zoom, the larger or better known first. The header credits every source and each district country's license, source and term. R2's alone.

## Where the data comes from

**Natural Earth** 10m (public domain; its own label points and ranks), **GeoNames**' undersea features (CC BY 4.0; `allCountries.zip` and `featureCodes_en.txt`), the **U.S. Census Bureau**'s 2024 cartographic boundaries of the counties (public domain) and **geoBoundaries** gbOpen ADM2 (CC BY 4.0, each country under its own license; Runfola et al. 2020, PLoS ONE 15(4): e0231866). **Their terms were read before a line was written** (2026-11-11), each country's geoBoundaries license among them: a country is kept only where its license allows commercial use with credit (an allowlist in the fetcher); share-alike licenses and permissions given to geoBoundaries alone leave its districts out.

## Open

1. ~~The first dispatched run, read~~ — 2026-11-11, run `43146399308`: 64,580 names (116 countries' districts, 46 left
   out by their licenses), 5,697,601 bytes, fresh, five files to R2.
2. The daily schedule, on since 2026-11-11, the month's build once in 720 hours: the next build read when it comes.
3. Countries whose districts their licenses leave out, each from a national source whose terms allow it, as they are read.
