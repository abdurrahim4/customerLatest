# Delta Kebab Customer Website V5 — Connected to JSON Backend

Frontend only. No backend or admin files included.

## Run

1. Start your existing fixed JSON backend on https://serverappdemo.onrender.com (`npm run dev`).
2. In this customer folder run `npm install` and `npm run dev`.
3. Open http://localhost:5173.
4. Optional: copy `.env.example` to `.env` to customize VITE_API_URL.

## Integration

- GET /api/v1/restaurants — branch list
- GET /api/v1/restaurants/:id/products — products and prices for selected branch
- GET /api/v1/restaurants/:id/categories — categories
- GET /api/v1/restaurants/:id/customizations — option groups
- POST /api/v1/orders — checkout; server recalculates prices and notifies management via Socket.IO

Customer ordering does not require login. Customer order history on this device is not live order tracking.

## Changes in V5

- Clear branch-specific cart data when a different restaurant is selected.
- Handle invalid saved branch IDs.
- Clear customization modal when changing restaurants.
- Better backend validation and connection error messages.

Note: This is the original React/Vite customer website, not a plain HTML conversion. Styling remains unchanged.
"# customerLatest" 
