---
name: Atelier Arôme Master Execution Plan
overview: ""
todos: []
---

# Master E

xecution Plan: Atelier Arôme E-Commerce Platform

## Executive Summary

This plan executes the PAD_v3 architecture for Atelier Arôme, a Singapore-based artisanal aromatherapy e-commerce platform. The project follows a decoupled headless architecture with Laravel 12 API backend and Next.js 15 frontend, preserving the distinctive "Illuminated Manuscript" aesthetic while delivering enterprise-grade commerce capabilities.

**Confirmed Decisions:**

- Product variants: Fixed sizes (5ml, 15ml, 30ml)

- Inventory: Single warehouse architecture

- Shipping: Flat-rate first, SingPost API in Phase 3

- Payments: Stripe MVP, PayNow deferred to Phase 3

**Timeline:** 15 weeks across 6 phases

**Architecture:** Laravel 12 API + Next.js 15 frontend + PostgreSQL + Redis + Meilisearch---

## Phase 1: Foundation & Infrastructure (Weeks 1-3)

### Objectives

- Set up development environments for both backend and frontend

- Create complete database schema with migrations

- Implement core authentication system

- Establish design system foundation

- Configure CI/CD and deployment pipelines

### Backend Files

#### 1.1 Project Setup Files

**File:** `atelier-arome-api/composer.json`

- **Purpose:** PHP dependency management

- **Features:**

- Laravel 12.x framework

- Sanctum 4.x for API authentication

- Filament 3.x for admin panel

- Stripe PHP SDK

- Meilisearch Scout driver

- Pest PHP for testing

- **Interfaces:** Standard Composer package definitions

- **Checklist:**

- [ ] Define Laravel 12.x requirement

- [ ] Add Sanctum, Filament, Stripe dependencies

- [ ] Configure autoload namespaces

- [ ] Set PHP 8.3+ requirement

- [ ] Add development dependencies (Pest, Pint, Larastan)

**File:** `atelier-arome-api/.env.example`

- **Purpose:** Environment configuration template

- **Features:**

- Database connection strings (PostgreSQL)

- Redis configuration

- Stripe API keys

- Meilisearch connection

- Cloudinary credentials

- Resend email API key

- Singapore-specific settings (GST rate, currency)

- **Interfaces:** Environment variable definitions

- **Checklist:**

- [ ] PostgreSQL connection string

- [ ] Redis host/port/password

- [ ] Stripe publishable/secret keys

- [ ] Meilisearch host/key

- [ ] Cloudinary cloud name/API key

- [ ] Resend API key

- [ ] APP_URL, SANCTUM_STATEFUL_DOMAINS

- [ ] SHOP_GST_RATE=0.09, SHOP_CURRENCY=SGD

**File:** `atelier-arome-api/config/shop.php`

- **Purpose:** E-commerce configuration

- **Features:**

- GST rate (9%)

- Currency (SGD)

- Max cart items (12)

- Abandoned cart timeout (24 hours)

- Order number format

- **Interfaces:** Config array with shop settings

- **Checklist:**

- [ ] Define GST rate constant

- [ ] Set currency to SGD

- [ ] Configure cart limits

- [ ] Set order number prefix (AA-)

- [ ] Define shipping zones

#### 1.2 Database Schema Files

**File:** `atelier-arome-api/database/migrations/2024_01_01_000001_create_users_table.php`

- **Purpose:** User authentication and profile storage

- **Features:**

- UUID primary key

- Email/password authentication

- Role enum (customer, admin, superadmin)

- Email verification tracking

- Soft deletes

- **Interfaces:** Laravel migration with up/down methods

- **Checklist:**

- [ ] UUID primary key

- [ ] Email unique constraint

- [ ] Password hash column

- [ ] Role enum column

- [ ] Email verification columns

- [ ] Timestamps and soft deletes

- [ ] Indexes on email, role

**File:** `atelier-arome-api/database/migrations/2024_01_01_000002_create_products_table.php`

- **Purpose:** Product (Essence) master data

- **Features:**

- UUID primary key

- Category relationship

- Slug for SEO-friendly URLs

- Latin name, description fields

- Humour, rarity, season enums

- Folio number for catalog organization

- Featured flag

- Soft deletes

- **Interfaces:** Migration with foreign key to categories

- **Checklist:**

- [ ] UUID primary key

- [ ] Category foreign key

- [ ] Slug unique constraint

- [ ] Enum columns (humour, rarity, season)

- [ ] Folio number string

- [ ] Featured boolean

- [ ] JSON metadata column

- [ ] Indexes on slug, category_id, is_featured

**File:** `atelier-arome-api/database/migrations/2024_01_01_000003_create_product_variants_table.php`

- **Purpose:** Product size variants (5ml, 15ml, 30ml)

- **Features:**

- UUID primary key

- Product relationship

- SKU unique constraint

- Fixed size names (5ml Phial, 15ml Bottle, 30ml Vessel)

- Price in SGD (decimal 10,2)

- Compare at price for sales
- Weight for shipping

- Default variant flag

- **Interfaces:** Migration with foreign key to products

- **Checklist:**

- [ ] UUID primary key

- [ ] Product foreign key

- [ ] SKU unique constraint

- [ ] Name column (fixed: 5ml|15ml|30ml)

- [ ] Price decimal(10,2)

- [ ] Compare at price nullable

- [ ] Weight in grams

- [ ] Default variant boolean

- [ ] Index on product_id, sku

**File:** `atelier-arome-api/database/migrations/2024_01_01_000020_create_inventories_table.php`

- **Purpose:** Current stock levels per variant

- **Features:**

- UUID primary key

- Variant relationship (one-to-one)

- Quantity available

- Reserved quantity (for pending orders)

- Low stock threshold

- Last restocked timestamp

- **Interfaces:** Migration with unique constraint on variant_id

- **Checklist:**

- [ ] UUID primary key

- [ ] Variant foreign key (unique)

- [ ] Quantity integer

- [ ] Reserved quantity integer

- [ ] Low stock threshold integer

- [ ] Last restocked timestamp

- [ ] Index on variant_id

**File:** `atelier-arome-api/database/migrations/2024_01_01_000021_create_inventory_movements_table.php`

- **Purpose:** Audit trail for all stock changes

- **Features:**

- UUID primary key

- Inventory relationship

- Order relationship (nullable)

- Type enum (addition, subtraction, reservation, release)

- Quantity change amount

- Reason text

- Performed by user (admin)

- **Interfaces:** Migration with foreign keys and enum

- **Checklist:**

- [ ] UUID primary key

- [ ] Inventory foreign key

- [ ] Order foreign key (nullable)

- [ ] Type enum

- [ ] Quantity integer

- [ ] Reason text

- [ ] Performed by user foreign key

- [ ] Indexes on inventory_id, order_id, created_at

**File:** `atelier-arome-api/database/migrations/2024_01_01_000008_create_carts_table.php`

- **Purpose:** Shopping cart storage

- **Features:**

- UUID primary key

- User relationship (nullable for guests)

- Session ID for guest carts

- Coupon relationship (nullable)

- Calculated totals (subtotal, discount, GST, total)

- Expiration timestamp

- **Interfaces:** Migration with nullable user_id

- **Checklist:**

- [ ] UUID primary key

- [ ] User foreign key (nullable)

- [ ] Session ID string (nullable)

- [ ] Coupon foreign key (nullable)

- [ ] Subtotal decimal

- [ ] Discount amount decimal

- [ ] GST amount decimal

- [ ] Total decimal

- [ ] Expires at timestamp

- [ ] Index on session_id, user_id

**File:** `atelier-arome-api/database/migrations/2024_01_01_000010_create_orders_table.php`

- **Purpose:** Completed order records

- **Features:**

- UUID primary key

- User relationship (nullable for guest orders)

- Order number (AA-YYYYMMDD-XXXX format)

- Status enum (pending, processing, shipped, delivered, cancelled)

- Payment status enum

- Address relationships (shipping, billing)

- Financial totals with GST breakdown

- Tracking information

- Timestamps for lifecycle events

- **Interfaces:** Migration with multiple foreign keys

- **Checklist:**

- [ ] UUID primary key

- [ ] User foreign key (nullable)

- [ ] Order number unique string

- [ ] Status enum

- [ ] Payment status enum

- [ ] Shipping/billing address foreign keys

- [ ] Subtotal, discount, shipping, GST, total decimals

- [ ] Tracking number/URL

- [ ] Shipped at, delivered at timestamps

- [ ] Indexes on order_number, user_id, status

#### 1.3 Core Model Files

**File:** `atelier-arome-api/app/Models/User.php`

- **Purpose:** User authentication and profile model

- **Features:**

- Sanctum HasApiTokens trait

- Role enum accessor

- Relationships: addresses, orders, cart, wishlist

- Helper methods: isAdmin(), isCustomer()

- **Interfaces:**

- `public function addresses(): HasMany`

- `public function orders(): HasMany`

- `public function cart(): HasOne`

- `public function isAdmin(): bool`

- **Checklist:**

- [ ] Extend Authenticatable

- [ ] Use HasApiTokens trait

- [ ] Define fillable fields

- [ ] Cast role to enum

- [ ] Define relationships

- [ ] Add role helper methods

- [ ] Implement soft deletes

**File:** `atelier-arome-api/app/Models/Product.php`

- **Purpose:** Product (Essence) model

- **Features:**

- Slug generation on creation

- Relationships: category, variants, images, reviews

- Enum casts for humour, rarity, season

- Scopes: featured(), active()

- Searchable with Meilisearch

- **Interfaces:**

- `public function variants(): HasMany`

- `public function images(): HasMany`

- `public function category(): BelongsTo`

- `public function scopeFeatured($query)`

- `public function scopeActive($query)`

- **Checklist:**

- [ ] Define fillable fields

- [ ] Cast enums

- [ ] Define relationships

- [ ] Implement slug generation (observer)

- [ ] Add Meilisearch searchable trait

- [ ] Define scopes

- [ ] Soft deletes

**File:** `atelier-arome-api/app/Models/ProductVariant.php`

- **Purpose:** Product size variant model

- **Features:**

- Product relationship

- Inventory relationship (one-to-one)

- Price formatting helpers

- Stock availability checks

- **Interfaces:**

- `public function product(): BelongsTo`

- `public function inventory(): HasOne`

- `public function isInStock(): bool`

- `public function formattedPrice(): string`

- **Checklist:**

- [ ] Define fillable fields

- [ ] Define relationships

- [ ] Add stock check methods

- [ ] Price formatting helpers

- [ ] SKU generation logic

**File:** `atelier-arome-api/app/Models/Inventory.php`

- **Purpose:** Stock level model

- **Features:**

- Variant relationship

- Available quantity calculation

- Low stock detection

- Movement history relationship

- **Interfaces:**

- `public function variant(): BelongsTo`

- `public function movements(): HasMany`

- `public function availableQuantity(): int`

- `public function isLowStock(): bool`

- **Checklist:**

- [ ] Define relationships

- [ ] Add quantity calculation methods

- [ ] Low stock detection

- [ ] Stock adjustment methods

**File:** `atelier-arome-api/app/Models/Cart.php`

- **Purpose:** Shopping cart model

- **Features:**

- User relationship (nullable)

- Session-based guest carts

- Items relationship

- Coupon relationship

- Total calculation methods

- Expiration handling

- **Interfaces:**

- `public function items(): HasMany`

- `public function user(): BelongsTo`

- `public function calculateTotals(): void`

- `public function isExpired(): bool`

- **Checklist:**

- [ ] Define relationships

- [ ] Add total calculation logic

- [ ] GST calculation integration

- [ ] Expiration check methods

- [ ] Guest cart identification

#### 1.4 Enum Files

**File:** `atelier-arome-api/app/Enums/ProductHumour.php`

- **Purpose:** Product humour classification enum

- **Features:**

- Calming, Uplifting, Grounding, Clarifying

- Symbol mapping (☾, ☀, ♁, ☁)

- Color mapping for UI

- **Interfaces:**

- `public function symbol(): string`

- `public function color(): string`

- `public function label(): string`

- **Checklist:**

- [ ] Define enum cases

- [ ] Add symbol method

- [ ] Add color method

- [ ] Add label method

**File:** `atelier-arome-api/app/Enums/OrderStatus.php`

- **Purpose:** Order lifecycle status enum

- **Features:**

- Pending, Processing, Shipped, Delivered, Cancelled

- Status transition validation

- Color mapping for admin UI

- **Interfaces:**

- `public function canTransitionTo(OrderStatus $status): bool`

- `public function color(): string`

- **Checklist:**

- [ ] Define enum cases

- [ ] Add transition validation

- [ ] Add color mapping

#### 1.5 Authentication Files

**File:** `atelier-arome-api/app/Http/Controllers/Api/V1/AuthController.php`

- **Purpose:** Authentication endpoints

- **Features:**

- Register new user

- Login with email/password

- Logout (revoke token)

- Get current user

- Password reset flow

- **Interfaces:**

- `public function register(RegisterRequest $request): JsonResponse`

- `public function login(LoginRequest $request): JsonResponse`

- `public function logout(Request $request): JsonResponse`

- `public function me(Request $request): JsonResponse`

- **Checklist:**

- [ ] Register endpoint with validation

- [ ] Login endpoint with Sanctum token generation

- [ ] Logout endpoint with token revocation

- [ ] Me endpoint for current user

- [ ] Password reset endpoints

- [ ] Email verification endpoints

- [ ] Error handling and responses

**File:** `atelier-arome-api/app/Http/Requests/Auth/RegisterRequest.php`

- **Purpose:** Registration validation
- **Features:**

- Email uniqueness validation

- Password strength requirements

- Name validation

- **Interfaces:** Laravel FormRequest with rules() method

- **Checklist:**

- [ ] Email required, email format, unique

- [ ] Password required, min 8 chars, confirmed

- [ ] Name required, string, max 255

- [ ] Phone optional, format validation

**File:** `atelier-arome-api/config/sanctum.php`

- **Purpose:** Sanctum API authentication configuration

- **Features:**

- Stateful domain configuration

- Token expiration settings

- Middleware configuration

- **Interfaces:** Config array

- **Checklist:**

- [ ] Configure stateful domains (localhost, production)

- [ ] Set token expiration (7 days)

- [ ] Configure middleware groups

### Frontend Files

#### 1.6 Next.js Project Setup

**File:** `atelier-arome-web/package.json`

- **Purpose:** Node.js dependencies and scripts

- **Features:**

- Next.js 15.x

- React 19.x

- TypeScript 5.x

- Tailwind CSS 4.0

- Shadcn-UI components

- TanStack Query, Zustand, React Hook Form

- Framer Motion

- **Interfaces:** Standard package.json with scripts

- **Checklist:**

- [ ] Next.js 15.x dependency

- [ ] React 19.x

- [ ] TypeScript 5.x

- [ ] Tailwind CSS 4.0

- [ ] Shadcn-UI dependencies

- [ ] State management libraries

- [ ] Form libraries

- [ ] Animation library

- [ ] Development dependencies (ESLint, Prettier)

**File:** `atelier-arome-web/tailwind.config.ts`

- **Purpose:** Tailwind theme configuration with Illuminated Manuscript design system

- **Features:**

- Custom color palette (ink, gold, parchment, botanical)

- Typography scale (Cormorant Garamond, Crimson Pro, Great Vibes)

- Custom animations (liquid-wave, float-botanical, rotate-seal)

- Spacing scale (golden ratio inspired)

- Box shadows with gold accents

- **Interfaces:** Tailwind Config type

- **Checklist:**

- [ ] Define ink color system

- [ ] Define gold color system

- [ ] Define parchment backgrounds

- [ ] Define botanical accent colors

- [ ] Configure font families

- [ ] Set up fluid typography scale

- [ ] Define custom animations

- [ ] Configure spacing scale

- [ ] Add gold shadow variants

**File:** `atelier-arome-web/components.json`

- **Purpose:** Shadcn-UI component configuration

- **Features:**

- Component aliases

- Style configuration

- RSC compatibility

- **Interfaces:** Shadcn config schema

- **Checklist:**

- [ ] Set style to "default"

- [ ] Enable RSC

- [ ] Configure aliases (@/components, @/lib)

- [ ] Set base color to neutral

- [ ] Enable CSS variables

**File:** `atelier-arome-web/src/app/globals.css`

- **Purpose:** Global styles and Tailwind directives

- **Features:**

- Tailwind base, components, utilities

- CSS custom properties for theming

- Font face declarations

- Reduced motion support

- **Interfaces:** CSS with Tailwind directives

- **Checklist:**

- [ ] Tailwind directives

- [ ] CSS custom properties for colors

- [ ] Font face declarations

- [ ] Reduced motion media query

- [ ] Base typography styles

#### 1.7 Design System Components

**File:** `atelier-arome-web/src/components/ui/button.tsx`

- **Purpose:** Base button component (Shadcn-UI)

- **Features:**

- Variants: primary, secondary, outline, ghost

- Sizes: sm, md, lg

- Manuscript-styled with gold accents

- Loading states

- **Interfaces:**

- `ButtonProps extends React.ButtonHTMLAttributes<HTMLButtonElement>`

- Variant and size props

- **Checklist:**

- [ ] Install Shadcn button component

- [ ] Customize with gold accent colors

- [ ] Add manuscript styling

- [ ] Implement loading state

- [ ] Add disabled states

**File:** `atelier-arome-web/src/components/ui/card.tsx`

- **Purpose:** Card component for product displays

- **Features:**

- Manuscript-styled borders

- Gold accent on hover

- Illuminated effect variant

- **Interfaces:** Shadcn Card component with custom variants

- **Checklist:**

- [ ] Install Shadcn card component

- [ ] Add manuscript border styling

- [ ] Implement hover effects

- [ ] Add illuminated variant

**File:** `atelier-arome-web/src/components/shared/section-header.tsx`

- **Purpose:** Consistent section headers with ornamental styling

- **Features:**

- Folio number display

- Ornamental rule divider

- Typography hierarchy

- **Interfaces:**

- `SectionHeaderProps { label: string; title: string; folio?: string }`

- **Checklist:**

- [ ] Folio number display

- [ ] Ornamental rule component

- [ ] Typography styling

- [ ] Responsive layout

**File:** `atelier-arome-web/src/lib/utils/cn.ts`

- **Purpose:** Class name merger utility

- **Features:**

- Combines clsx and tailwind-merge

- Handles conditional classes

- **Interfaces:** `cn(...inputs: ClassValue[]): string`

- **Checklist:**

- [ ] Import clsx and tailwind-merge

- [ ] Create cn function

- [ ] Export utility

#### 1.8 API Client Setup

**File:** `atelier-arome-web/src/lib/api/client.ts`

- **Purpose:** Axios/fetch wrapper for API calls

- **Features:**

- Base URL configuration

- Authentication token injection

- Request/response interceptors

- Error handling

- **Interfaces:**

- `apiClient.get<T>(url: string, config?: AxiosRequestConfig): Promise<T>`

- `apiClient.post<T>(url: string, data?: any, config?: AxiosRequestConfig): Promise<T>`

- **Checklist:**

- [ ] Configure base URL from env

- [ ] Add auth token interceptor

- [ ] Error handling interceptor

- [ ] TypeScript generics for responses

- [ ] Request timeout configuration

**File:** `atelier-arome-web/src/lib/api/endpoints.ts`

- **Purpose:** API endpoint constants

- **Features:**

- Centralized endpoint definitions

- Type-safe route building

- **Interfaces:** Exported constants for all API routes

- **Checklist:**

- [ ] Auth endpoints

- [ ] Product endpoints

- [ ] Cart endpoints

- [ ] Order endpoints

- [ ] User endpoints

---

## Phase 2: Core Commerce Features (Weeks 4-6)

### Objectives

- Implement product catalog with filtering

- Build cart system with guest persistence

- Create product detail pages

- Implement user authentication UI

- Set up basic admin interface

### Backend Files

#### 2.1 Product Management

**File:** `atelier-arome-api/app/Http/Controllers/Api/V1/ProductController.php`

- **Purpose:** Product listing and detail endpoints

- **Features:**

- Paginated product list

- Filtering by humour, rarity, season, category

- Sorting options

- Featured products endpoint

- Single product by slug

- **Interfaces:**

- `public function index(ProductFilterRequest $request): JsonResponse`

- `public function show(string $slug): JsonResponse`

- `public function featured(): JsonResponse`

- **Checklist:**