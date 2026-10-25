# Phuket Holiday Planner V5 — release checklist

## Agreed outcome
Single mobile-first application with Today, Holiday, Explore and Diary; Plan A/Rainy Day per date; automatic V4 migration; activity completion, recurring food experiences, Try/Buy cards, flexible day scheduling and simple expense tracking.

## Implemented candidate
- Preserves V4 data, local browser key and a pre-migration snapshot; preserves day planning notes.
- Full-day template selection, one-tap activity adding, tentative times, locking, moving, arrow/drag reorder, past-day Yes/No/Later.
- 52 seeded activities plus 17 Try and 29 Buy items, with search, area filtering, favourites, repeated visits and shop-grouped wishlist stops.
- Day diary with optional notes and local compressed photos in IndexedDB; downloadable backup/restore including stored photos.
- Expenses, refunds received, editable categories, separate planned/actual figures and category allowances; no automatic refund on cancellation.
- Optional online weather hint and on-demand Wikimedia image lookup, with offline text fallback. Service worker caches the app shell.

## Independently executed test suites
Eight independent Node processes passed: migration, budget/refunds, expenses, scheduling, catalogue, repeat experiences, photo/diary storage contract and UI/offline source checks. Tests and results are packaged in the downloadable V5 candidate archive.

## Outstanding release gates — do not merge to live until checked
- **Real-browser E2E blocked**: test Chromium's administrator URL blocklist prevents navigation to local pages. Node mocked-DOM tests are not a substitute for phone Safari testing.
- **Exact catalogue reference photos incomplete**: the 98 entries have descriptions and image/lookup support but are not all prepopulated with licensed, verified photos.
- Real-device check of IndexedDB photo imports, photo-inclusive backups, touch drag/drop, offline cache, V4 migration against the actual phone's saved browser data, and external weather/image requests.
- Reconcile potential category allowance overlaps for restaurant activities before trusting all budget forecasts.

## Deployment
Direct live upgrade chosen, not a permanent parallel preview. This development branch is a staging mechanism only. Live main remains unchanged until tests and content are verified.