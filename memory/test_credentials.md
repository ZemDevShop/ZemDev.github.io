# ZemDev Test Credentials

## Admin
- Email: `admin@zemdev.com`
- Password: `ZemDev2026!`
- Role: admin
- Login URL: `/admin/login`
- Dashboard URL: `/admin`

## Auth Endpoints
- POST `/api/auth/login` - body: `{"email":"...","password":"..."}`
- POST `/api/auth/logout`
- GET `/api/auth/me` (requires cookie or `Authorization: Bearer <token>`)

## Product Endpoints
- GET `/api/products` (public)
- GET `/api/products/{id}` (public)
- POST `/api/products` (admin)
- PUT `/api/products/{id}` (admin)
- DELETE `/api/products/{id}` (admin)
