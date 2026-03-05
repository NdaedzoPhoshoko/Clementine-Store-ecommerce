# Clementine Store E-commerce

Production-focused full-stack e-commerce platform built with React and Node.js/Express.

Live website (frontend): https://clementine-store.vercel.app/
Backend is integrated and hosted on Render.

## Highlights

- End-to-end shopping flow: browse products, filter/search, cart, checkout, and orders.
- Secure authentication with JWT access/refresh flow.
- OTP-based signup verification and forgot-password recovery.
- Admin capabilities for product/category/inventory management.
- Responsive UI optimized for desktop, tablet, and mobile.

## Screenshots
- Home page
  <img width="1298" height="535" alt="image" src="https://github.com/user-attachments/assets/89628691-9237-4b89-974a-06e109ee18a2" />

- Shop/filters page
  <img width="1297" height="613" alt="image" src="https://github.com/user-attachments/assets/75028f55-f1c8-495a-b588-01c2d2b63869" />

- Product detail page
  <img width="1298" height="615" alt="image" src="https://github.com/user-attachments/assets/b7ff8348-6b87-4ab7-be0f-9c631eeb30b0" />

- Cart page
  <img width="1299" height="614" alt="image" src="https://github.com/user-attachments/assets/385b4102-2ef2-44a6-811b-622da6ffdb70" />

- Payment Page
  <img width="1295" height="614" alt="image" src="https://github.com/user-attachments/assets/36f8a396-f9d1-4faa-b3b5-f71df51efdd4" />

- User Account
  <img width="1291" height="611" alt="image" src="https://github.com/user-attachments/assets/e3038d90-7f2c-4bcc-8391-6eced2b52f7a" />

- Admin Dashboard + Add New Order
  <img width="1294" height="614" alt="image" src="https://github.com/user-attachments/assets/7367b322-0b34-425b-84a7-2a41eb537033" />

- NavBar + Product Ads
  <img width="1291" height="588" alt="image" src="https://github.com/user-attachments/assets/c4580b8b-21ba-4e64-8f87-885fda97e266" />

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
