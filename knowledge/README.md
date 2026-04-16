# Knowledge base

Markdown under **`knowledge/`** is indexed for workspace search when the indexer or GitHub `push` webhook runs. See the WarpDesk docs (`knowledge_repo_and_index.md` in the framework repo).

## Layout

- **`business/`** — Customer-facing articles (default visibility in the app).
  - [`business/company-bio.md`](business/company-bio.md) — Brand / positioning
  - [`business/company-website.md`](business/company-website.md) — Official site URLs and related links
  - [`business/product/`](business/product/) — Product-oriented docs (e.g. menu subsets aligned with the public site)
- **`technical/`** — Internal-only docs (default visibility rules apply in the app). Add files here when they should not be treated as customer-facing.
