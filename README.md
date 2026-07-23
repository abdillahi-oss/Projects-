# Eclipse — Premium Smart LED Lighting Storefront

E-commerce storefront for Eclipse, a smart LED lighting brand. Dark, premium aesthetic with electric-blue and warm-gold accents. Single-page frontend with product detail views, a slide-out cart, and a full checkout flow backed by a small order API.

**Built by Abdillahi** — design direction, product line, brand, and photography. Developed with AI-assisted tooling (Claude).

## Features

- Animated brand loading screen
- Product catalog: Eclipse Zenith (COB strip, 3 color temps, 5m/10m), Lumière (RGBWW smart strip), Nova (smart controller), Extender, Pendants, Garden Lights (coming soon)
- Variant selection (color temperature, length) tracked per cart line
- Slide-out cart drawer with quantity controls and live subtotal
- Checkout with Ontario HST (13%), order reference generation, and success screen
- Real installation photo gallery with lightbox
- Order API that re-prices carts server-side (client prices are never trusted) and persists orders
- Mailto fallback so orders still work with no backend running

## Structure

```
frontend/
  index.html        — single-page storefront (views toggled by JS)
  css/styles.css    — all styling
  js/app.js         — views, cart state, checkout, API calls
  assets/           — logo + real installation photos
backend/
  server.js         — Express order API, also serves the frontend
  package.json
```

## Run locally

```bash
cd backend
npm install
npm start
# open http://localhost:3001
```

Frontend-only (no backend): just open `frontend/index.html` in a browser. Checkout falls back to the email-order flow.

## API

| Method | Route         | Description                              |
|--------|---------------|------------------------------------------|
| GET    | /api/health   | Health check                             |
| POST   | /api/orders   | Submit an order (validated + re-priced)  |
| GET    | /api/orders   | List orders (requires `x-admin-token`)   |

## Roadmap

- Stripe payment integration
- Pendants product details + garden lights launch
- Order status emails
