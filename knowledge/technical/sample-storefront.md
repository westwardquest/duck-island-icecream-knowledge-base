# Sample storefront (`sample-storefront/`)

## Purpose

A minimal **Next.js** (App Router) app that stands in for the real Duck Island site while people file tickets against this workspace. It is **static**: no Supabase, no WarpDesk HTTP calls from the browser.

## Run and build

```bash
cd sample-storefront
npm install
npm run dev
```

Open the URL Next prints (usually `http://localhost:3000`). Production build: `npm run build` then `npm start`.

## Structure

| Area | Notes |
| ---- | ----- |
| **`app/page.tsx`** | Home page: hero, flavour section (tabs), visit section, footer |
| **`app/page.module.css`** | Page layout, cards, tab strip |
| **`components/DuckIslandLogo.tsx`** | Official wordmark (see `components/` + markup helper) |
| **`components/FlavourListTabs.tsx`** | Client component: **Regular** vs **Special** tabs; reuses card grid styles |
| **`data/officialFlavours.ts`** | Names, blurbs, dietary tags — snapshot from **duckislandicecream.co.nz/flavours** |
| **`data/specialFlavours.ts`** | Scoop-store specials — snapshot from **…/scoop-store-special-flavours** |

Copy is **manually maintained** to match the live site; nothing is scraped at runtime.

## Flavour tabs

- **Regular flavours** — Full public range from `officialFlavours`.
- **Special flavours** — Curated scoop-shop list from `specialFlavours`.

Intro copy under the tabs links to the same public URLs used for the snapshots so reviewers can compare.

## Styling and fonts

Global tokens live in **`app/globals.css`**. **`layout.tsx`** loads **DM Sans** and **Fraunces** via `next/font`. Keep new UI consistent with existing spacing, borders, and accent colours.

## Testing changes

After UI or data edits, run **`npm run build`** in **`sample-storefront/`** to catch TypeScript and Next errors before opening a PR or handing off for QA.
