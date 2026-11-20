# Delta Kebab optional customer accounts — STAGING

Added a small navbar profile icon, Login/Register, My Orders and My Rewards pages. Guest checkout and existing browser-local order tracking are retained. Logged-in checkout sends the customer bearer token to the backend; order history is fetched on demand with a limit of 20. Account session token uses sessionStorage (cleared when browser session ends). Passwords are not persisted.

Backend requirement: the *staging* backend from DeltaKebab_Admin_Delete_Print_STAGING.zip with /api/v1/customer endpoints. Do not deploy the customer website independently against a production backend that lacks those endpoints.

Known limitations: loyalty reward redemption at checkout is NOT implemented in the backend. Rewards page is read-only and explicitly says redemption is coming soon. Old guest orders are not automatically linked to a newly registered account. Reorder button is not implemented. Customer account creation needs MongoDB V2 and the customer index initialization. Full integration tests were not run; do not deploy to production without testing registration, login, logout, guest order, authenticated order, order history, mobile navigation, and existing cart flow.

Install and test in staging: npm ci && npm run build. Configure VITE_API_URL for your staging backend. No server files are modified by this customer-only ZIP.
