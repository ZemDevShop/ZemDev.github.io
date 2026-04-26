# ZemDev — FiveM Resources Marketplace

## Original Problem Statement
> "Creame una pagina web — quiero una pagina para vender productos de fivem scripts bases etc con el nombre en grande ZemDev"

User choices captured:
- Brand: **ZemDev** displayed massive in hero
- Products: FiveM scripts, bases, MLOs, vehicles
- Payment: **BBVA bank transfer** (display only) + Discord confirmation
- Admin panel for products
- Aesthetic: dark cyberpunk gaming, neon green/purple, dev-style typography
- Language: Spanish

## Architecture
- **Backend**: FastAPI + Motor (MongoDB) + JWT (PyJWT) + bcrypt
- **Frontend**: React 19 + React Router 7 + Tailwind + custom CSS + lucide-react
- **Auth**: httpOnly cookie + Bearer token fallback (cross-domain safe)
- **DB**: `zemdev_database` — collections: `users`, `products`

## Personas
- **Visitor / Customer** — browses catalog, filters by category, opens purchase modal to see BBVA info, contacts via Discord to confirm.
- **Admin (single seeded user)** — logs in at `/admin/login`, manages products from `/admin` dashboard (create / edit / delete).

## What's been implemented (2026-01)
- Hero with massive `ZemDev` text + cyberpunk grid background and animated scan line
- Public product catalog with filter pills (All / Scripts / Bases / MLOs / Vehículos)
- 6 seeded products with images, prices in MXN, badges
- Purchase modal: BBVA bank details (banco, titular, CLABE, cuenta, referencia, monto) with copy-to-clipboard + Discord CTA
- Admin login (JWT, cookie + Bearer fallback)
- Admin dashboard: products table with create / edit / delete via modal form
- Footer + contact section + "Why ZemDev" section
- Spanish UI throughout

## Endpoints
- `GET /api/products` (public) — list products, optional `?category=`
- `GET /api/products/{id}` (public)
- `POST /api/products` (admin)
- `PUT /api/products/{id}` (admin)
- `DELETE /api/products/{id}` (admin)
- `POST /api/auth/login`
- `POST /api/auth/logout`
- `GET /api/auth/me`

## Testing
- Backend pytest: 10/10 ✅ (`/app/backend/tests/test_zemdev_api.py`)
- Frontend Playwright smoke: ✅ — hero, filters, purchase modal, admin login, dashboard

## Backlog / Future
- **P1**: Search bar in catalog, individual product detail page (deep links)
- **P1**: Image upload for admin (currently URL only)
- **P2**: Brute-force lockout on `/api/auth/login` (5 attempts → 15 min)
- **P2**: Order tracking — generate purchase order with reference number, customer enters it on Discord ticket
- **P2**: Migrate to FastAPI lifespan context manager (deprecated startup events)
- **P2**: Stripe integration as payment alternative (kept BBVA as primary per user)
- **P3**: Multi-admin roles, customer reviews, demo videos per product

## Credentials
See `/app/memory/test_credentials.md`.
