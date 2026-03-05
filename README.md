# Clementine Store E-commerce

Production-focused full-stack e-commerce platform built with React and Node.js/Express.

Live website (frontend): https://clementine-store.vercel.app/

## Highlights

- End-to-end shopping flow: browse products, filter/search, cart, checkout, and orders.
- Secure authentication with JWT access/refresh flow.
- OTP-based signup verification and forgot-password recovery.
- Admin capabilities for product/category/inventory management.
- Responsive UI optimized for desktop, tablet, and mobile.

## Screenshots

Add your best 4-6 screenshots here.

Recommended set:
- Home page
- Shop/filters page
- Product detail page
- Cart + checkout page
- Account/orders page
- Admin dashboard page

Example markdown:

```md
![Home](./screenshots/home.png)
![Shop](./screenshots/shop.png)
![Product Details](./screenshots/product-details.png)
![Checkout](./screenshots/checkout.png)
![Admin Dashboard](./screenshots/admin-dashboard.png)
```

## Tech Decisions

- `React + Vite` for fast development cycle and lean production bundles.
- `Node.js + Express` for clear API layering and maintainable controller/route structure.
- `PostgreSQL` for relational data integrity across users, products, cart, orders, and payments.
- `JWT + httpOnly refresh cookie` to balance SPA UX with session security.
- `Swagger/OpenAPI` annotations in routes for API discoverability and team onboarding.
- `EmailJS` integration for OTP delivery in user verification flows.

## Tech Stack

### Frontend
- React + Vite
- React Router
- Context API (cart and session-aware UI updates)
- EmailJS (`@emailjs/browser`) for OTP delivery in auth flows
- Framer Motion, Lucide React, React Colorful, React Inner Image Zoom
- CSS-first responsive component styling

### Backend
- Node.js + Express (ES Modules)
- PostgreSQL (`pg` pool)
- JWT auth (access token + refresh token cookie)
- Swagger/OpenAPI (`swagger-jsdoc`, `swagger-ui-express`)
- Bcrypt (`bcryptjs`) for password hashing
- Stripe for payments
- Cloudinary + Multer for media upload handling

### Tooling
- Vite (frontend build/dev)
- Nodemon (backend dev)
- ESLint (frontend linting)

## Project Structure

```text
Clementine Store/
|-- ecommerce-frontend/
|   |-- public/
|   `-- src/
|       |-- components/
|       |-- hooks/
|       |-- pages/
|       `-- utils/
`-- ecommerce-backend/
    |-- config/
    |-- controllers/
    |-- middleware/
    |-- routes/
    |-- docs/
    `-- scripts/
```

## Frontend Structure (Detailed)

```text
ecommerce-frontend/
|-- .gitignore
|-- Edit.jsx
|-- eslint.config.js
|-- index.html
|-- package.json
|-- README.md
|-- vite.config.js
|-- public/
|   |-- icons/
|   |-- illustrations/
|   `-- images/
|       |-- about_us/
|       |-- home/
|       `-- sponsored/
`-- src/
    |-- App.css
    |-- App.jsx
    |-- index.css
    |-- main.jsx
    |-- assets/
    |-- components/
    |   |-- ScrollToTop.jsx
    |   |-- account_avatar/
    |   |-- admin_manage_products/
    |   |-- auth/
    |   |-- breadcrumbs/
    |   |-- cart/
    |   |-- filters/
    |   |-- footer/
    |   |-- image_zoom/
    |   |-- modals/
    |   |-- nabar/
    |   |-- pagination/
    |   `-- products_grid/
    |-- hooks/
    |   |-- useAccordionData.jsx
    |   |-- useFetchAutocomplete.js
    |   |-- useFetchBrowseProducts.js
    |   |-- useFetchCategoriesWithImages.js
    |   |-- useFetchCategoryNames.js
    |   |-- useFetchMe.js
    |   |-- useFetchMyOrders.js
    |   |-- useFetchMyShippingDetails.js
    |   |-- useFetchNewProducts.js
    |   |-- useFetchProductDetails.js
    |   |-- useFetchProductReviews.js
    |   |-- usePostProductReview.js
    |   |-- useUpdateOrderShipping.js
    |   |-- admin_dashboard/
    |   |-- for_cart/
    |   |-- home_features/
    |   |-- payment/
    |   |-- profile/
    |   |-- support/
    |   `-- use_auth/
    |-- pages/
    |   |-- about_us/
    |   |-- account/
    |   |-- account_dashboard/
    |   |-- admin/
    |   |-- auth/
    |   |-- cart/
    |   |-- checkout/
    |   |-- home/
    |   |-- product_page/
    |   |-- shopping/
    |   `-- support/
    `-- utils/
        |-- apiFetch.js
        |-- notes.txt
        `-- slugUtils.js
```

## Backend Structure (Detailed)

```text
ecommerce-backend/
|-- package.json
|-- README.md
|-- server.js
|-- todo.txt
|-- config/
|   |-- cloudinary.js
|   `-- db.js
|-- controllers/
|   |-- authController.js
|   |-- cartController.js
|   |-- categoryController.js
|   |-- inventoryController.js
|   |-- orderController.js
|   |-- paymentCardController.js
|   |-- paymentController.js
|   |-- productController.js
|   |-- reviewController.js
|   |-- shippingController.js
|   |-- userController.js
|   `-- home_features/
|       `-- homeFeaturesController.js
|-- docs/
|   |-- indexes.sql
|   `-- swagger.js
|-- middleware/
|   `-- auth.js
|-- models/
|   `-- userModel.js
|-- routes/
|   |-- authRoutes.js
|   |-- cardRoutes.js
|   |-- cartItemRoutes.js
|   |-- cartRoutes.js
|   |-- categoryRoutes.js
|   |-- homeFeaturesRoutes.js
|   |-- inventoryRoutes.js
|   |-- orderRoutes.js
|   |-- paymentRoutes.js
|   |-- productRoutes.js
|   |-- reviewRoutes.js
|   |-- shippingRoutes.js
|   `-- userRoutes.js
`-- scripts/
    `-- fullscript.sql
```

## Quick Local Run

```bash
# frontend
cd ecommerce-frontend
npm install
npm run dev

# backend
cd ../ecommerce-backend
npm install
npm run dev
```

Local URLs:
- Frontend: `http://localhost:5173`
- Backend API: `http://localhost:5000`
- Swagger docs: `http://localhost:5000/api/docs`

## Configuration

Use `.env.local` for frontend and `.env` for backend.
Keep secrets private and out of source control.

### Frontend environment (`ecommerce-frontend/.env.local`)

```dotenv
VITE_API_BASE_URL=http://localhost:5000
VITE_EMAILJS_PUBLIC_KEY=your_public_key
VITE_EMAILJS_SERVICE_ID=your_service_id
VITE_EMAILJSOTP_TEMPLATE_ID=your_template_id
```

Notes:
- All frontend env vars must start with `VITE_`.
- Do not commit private keys or production-only secrets.

### Backend environment (`ecommerce-backend/.env`)

```dotenv
PORT=5000
NODE_ENV=development
CORS_ORIGIN=http://localhost:5173

DATABASE_URL=postgres://<user>:<password>@<host>:<port>/<db>

JWT_SECRET=your_access_secret
JWT_ACCESS_EXPIRES_IN=30m
JWT_REFRESH_SECRET=your_refresh_secret
JWT_REFRESH_EXPIRES_IN=7d

ADMIN_EMAILS=admin@example.com
ADMIN_USER_IDS=1,2

CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret

IMAGE_COMPRESSION_QUALITY=60
```

Notes:
- Use distinct JWT secrets.
- Restrict admin env values to trusted accounts only.
- For production, run with HTTPS and secure cookie settings.

## Notes For Public Sharing

- This README is intentionally client/recruiter focused.
- Do not publish database credentials, JWT secrets, or third-party private keys.
