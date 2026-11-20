# Delta Kebab Customer — Checkout and Delivery Update

This customer app is based on the existing Geoapify-enabled Delta Kebab React customer site.

## Features
- Cart displays items, size/meat/sauce/extras, subtotal, VAT and total before delivery.
- Address form collects street, house number, postal code, city, apartment and floor.
- POST `/api/v1/delivery/quote` uses the selected branch and customer address. The **backend** handles Geoapify geocoding and road distance, 15 km limit, Admin Panel delivery fee bands, promotions and alternate-branch recommendation.
- If the quote is eligible **and includes a signed quoteToken**, the site automatically navigates to checkout.
- Changing the address, cart quantities, options or branch invalidates the quote; a pending quote cannot override newer changes.
- Checkout shows delivery fee, VAT and total, customer details, and Cash/Card on Delivery.
- Orders page, Why Us and Contact remain available; status polling occurs every 15 seconds while visible.
- Product images are lazy loaded.

## Install
1. Keep your current **optimized Geoapify backend** and Admin Panel. No DB migration or seed is needed.
2. In `customer/`, run `npm install`, then `npm run dev`.
3. Set `VITE_API_URL=https://serverappdemo.onrender.com` in `customer/.env` if needed (do not put API secrets here).
4. The backend must have `GEOAPIFY_API_KEY`, `DELIVERY_QUOTE_SECRET`, and the admin delivery bands configured.
5. Verify a real address within 15 km and one beyond 15 km; test promotion, VAT and order submission.

## Notes
- No API secrets are bundled.
- VAT display is an estimate based on product category and option rates. **Server order totals are authoritative.**
- The customer site does not itself measure road distance; it requests a server-signed quote.
- This release does not modify your backend or MongoDB records.
