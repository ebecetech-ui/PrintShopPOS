# POS Percetakan - Point of Sale System for Printing Business

## Overview
A comprehensive POS (Point of Sale) application specifically designed for printing businesses (Percetakan) in Indonesia. The system features invoice generation, financial tracking (pembukuan), order management, customer database, and role-based access control.

## Tech Stack
- **Frontend**: React + TypeScript + Vite + TailwindCSS
- **Backend**: Express.js + TypeScript
- **Database**: PostgreSQL (Neon) with Drizzle ORM
- **Authentication**: Replit Auth with role-based access control
- **UI Components**: shadcn/ui with Material Design 3 approach

## User Roles
The system supports 5 distinct user roles with different access levels:
1. **Admin** - Full system access including user management and settings
2. **Owner** - Business owner access to all features except user management
3. **Produksi** - Production staff access to order and product data
4. **Keuangan** - Finance staff access to accounting and financial reports
5. **Kasir** - Cashier access to orders, payments, and customer data

## Database Schema
- **users** - User accounts with role-based access
- **productTypes** - Product type/category master data
- **materials** - Material master data for printing products
- **units** - Unit of measurement master data
- **products** - Product catalog with pricing
- **customers** - Customer database
- **orders** - Order transactions with status tracking
- **orderItems** - Line items for each order
- **payments** - Payment records supporting multiple payment methods
- **expenses** - Business expense tracking
- **appSettings** - Application configuration

## Features Implemented
✅ Authentication with Replit Auth
✅ Role-based access control and menu filtering
✅ Master Data Management (Products, Types, Materials, Units)
✅ Customer Management
✅ Order Management with automatic invoice generation
✅ Payment tracking with multiple payment methods (Cash, Transfer, E-wallet)
✅ Financial tracking (Receivables, Revenue, Expenses)
✅ Dashboard with revenue statistics and charts
✅ Complete CRUD API for all entities

## API Routes
All routes are protected with `isAuthenticated` middleware:

### Authentication
- GET `/api/auth/user` - Get current user profile
- GET `/api/login` - Initiate Replit Auth login
- GET `/api/callback` - Auth callback handler
- GET `/api/logout` - Logout and clear session

### Master Data
- **Product Types**: GET/POST `/api/product-types`, PATCH/DELETE `/api/product-types/:id`
- **Materials**: GET/POST `/api/materials`, PATCH/DELETE `/api/materials/:id`
- **Units**: GET/POST `/api/units`, PATCH/DELETE `/api/units/:id`
- **Products**: GET/POST `/api/products`, GET/PATCH/DELETE `/api/products/:id`

### Customers
- GET/POST `/api/customers`
- GET/PATCH/DELETE `/api/customers/:id`

### Orders
- GET/POST `/api/orders`
- GET `/api/orders/:id` - Get order with items
- PATCH `/api/orders/:id/status` - Update order status

### Payments
- GET `/api/orders/:orderId/payments`
- POST `/api/payments`

### Expenses
- GET/POST `/api/expenses`
- PATCH/DELETE `/api/expenses/:id`

### Statistics
- GET `/api/stats/revenue` - Revenue statistics with date filtering
- GET `/api/stats/products` - Product-wise revenue breakdown

### Settings
- GET/POST `/api/settings` - Application settings

## Frontend Pages
- **Landing Page** (`/`) - Public landing page for unauthenticated users
- **Dashboard** (`/`) - Main dashboard with revenue stats and charts (authenticated)
- **Orders** (`/orders`) - Order listing and management
- **New Order** (`/orders/new`) - Create new order with invoice
- **Customers** (`/customers`) - Customer management
- **Products** (`/master/products`) - Product catalog management

## Payment Methods Supported
- Cash (Tunai)
- Bank Transfer
- E-wallet

## Order Status Tracking
- **pending** - Order created, awaiting production
- **processing** - In production
- **completed** - Production completed
- **delivered** - Delivered to customer
- **cancelled** - Order cancelled

## Payment Status Tracking
- **unpaid** - No payment received
- **partial** - Partial payment received
- **paid** - Fully paid

## Development
- Database schema is managed with Drizzle ORM
- Use `npm run db:push` to sync schema changes
- Seed data available via `npx tsx server/seed.ts`
- Server runs on port 5000 with Vite dev server

## Recent Changes
- Completed full authentication implementation with Replit Auth
- Implemented all backend API routes with validation
- Connected frontend to real API endpoints
- Added role-based sidebar menu filtering
- Created seed data for testing

## Next Steps
- Test end-to-end functionality
- Add more pages for accounting features (Piutang, Omset, etc)
- Implement invoice PDF generation
- Add data export features
