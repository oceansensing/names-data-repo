# Decisions

Dated, irreversible-leaning decisions, one entry each, newest last. The
reasoning lives in `PLAN.md`.

**What counts as one-way in a data repository**: a decision that puts bytes in
readers' hands under a shape they will code against; a decision about which
repository owns a product, since moving one costs a migration in two places;
and a decision that forecloses an upstream.

## D1 — 2026-11-11 — Its own repository, R2 alone, once a month

The names of land and water get a repository of their own (2026-11-11) and **publish to Cloudflare R2 alone**, as every new product since the site pipeline's D13: the website's map draws none of it, and it carries a contract of its own. Once a month, from its sources' own files.

## D2 — 2026-11-12 — The borders: a second product, its tree carried by the workflow's cache

The districts' and counties' borders join as a product of their own (`borders`), made from the same selection as the names: a small root on the `published` branch naming a version of a tree of line tiles, `land/district-borders/`, which the branch never holds — the workflow's cache carries it between runs, under the version the root names, as the sibling origins' land trees are carried. Its step runs every run and its fetcher makes the tree again only when due (once a month), when the stage lacks the version the root names, or when a dispatch names it: a cache that misses costs one build (about 300 MB fetched), never a run that cannot publish. The tiles' shape — `{"lines": …}` keyed `<south>_<west>`, two tiers — is the shape readers code against.
