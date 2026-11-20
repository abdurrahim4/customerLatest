# Delta Kebab Customer Website — Categories & VAT Integration

Based on the previous Connected V5 customer website, adapted for the `DeltaKebab_Categories_VAT_Admin_Server` backend.

## Run
1. Start your **existing working Categories & VAT server** from its `server` directory: `npm run dev` (default port 5000).
2. In `deltakebab-customer`, run `npm install`, then `npm run dev`.
3. Open the URL shown by Vite (typically http://localhost:5173).
4. If your backend is not on port 5000, copy `.env.example` to `.env` and set `VITE_API_URL` to the backend origin, e.g. `https://serverappdemo.onrender.com`.

## Data compatibility
- Branches: `GET /api/v1/restaurants` — only selected branch's menu is shown.
- Products: `GET /api/v1/restaurants/:id/products` — branch-specific product records.
- Categories and VAT: `GET /api/v1/restaurants/:id/categories` — category `vatRate`.
- Product sizes: existing branch-specific `Size` customization group (one selection), not a new catalog.
- Global Meat/Sauce/Extras: `GET /api/v1/restaurants/:id/customizations`; only groups referenced by the product are shown.
- Checkout: `POST /api/v1/orders` sends product IDs, quantities, group option IDs and payment method; **the server** recalculates subtotal, VAT and total and snapshots the order.
- Payment: cash on delivery or card on delivery. Customer login optional/not required.

## Important
Prices in this implementation are assumed to be **before VAT**, matching the supplied server. The displayed VAT is an estimate from the latest fetched category/group rates. The server-calculated order total is authoritative. Do not use live until local end-to-end testing of checkout, tax, sizes, and product availability is complete. Confirm legal Polish VAT and tax-inclusive vs tax-exclusive pricing with an accountant.

No changes to your working backend, database, Admin Panel or `.env` are needed for this frontend update. Do not run `npm run seed` or migration.

The previous V5 site uses React/Vite. This package preserves that stack and layout.
