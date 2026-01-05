MASTER_EXECUTION_PLAN.md
Atelier Arôme — Complete Development Blueprint
📋 Executive Overview
Project Identity
Attribute	Value
Project Name	Atelier Arôme E-Commerce Platform
Version	1.0.0
Architecture	Headless Commerce (Laravel API + Next.js Frontend)
Target Market	Singapore SME — Artisanal Aromatherapy
Aesthetic	Illuminated Manuscript / Refined Luxury
Technology Stack Summary
text

┌─────────────────────────────────────────────────────────────────────────────┐
│                           TECHNOLOGY STACK                                  │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  BACKEND (Laravel 12)                 FRONTEND (Next.js 15)                │
│  ─────────────────────                ──────────────────────               │
│  • PHP 8.3+                           • React 19                           │
│  • Laravel 12.x                       • TypeScript 5.x                     │
│  • PostgreSQL 16+                     • Tailwind CSS 4.0                   │
│  • Redis 7.x                          • Shadcn-UI + Radix                  │
│  • Laravel Sanctum                    • Framer Motion                      │
│  • Filament 3.x (Admin)               • Zustand + TanStack Query           │
│  • Meilisearch                        • React Hook Form + Zod              │
│                                                                             │
│  INTEGRATIONS                         INFRASTRUCTURE                        │
│  ────────────                         ──────────────                        │
│  • Stripe (Payments)                  • Vercel (Frontend)                  │
│  • PayNow via Stripe                  • Laravel Forge (Backend)            │
│  • Resend (Email)                     • Neon/Supabase (Database)           │
│  • Cloudinary (Media)                 • Cloudflare (CDN/DNS)               │
│  • SingPost (Shipping)                • Sentry (Monitoring)                │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
Phase Overview Map
mermaid

flowchart TB
    subgraph Foundation["🏗️ FOUNDATION (Weeks 1-2)"]
        P1[Phase 1: Backend Foundation]
        P2[Phase 2: Frontend Foundation]
        P3[Phase 3: Design System]
    end

    subgraph Core["⚙️ CORE FEATURES (Weeks 3-6)"]
        P4[Phase 4: Authentication]
        P5[Phase 5: Product Catalog Backend]
        P6[Phase 6: Product Catalog Frontend]
        P7[Phase 7: Cart System]
    end

    subgraph Commerce["🛒 COMMERCE (Weeks 7-10)"]
        P8[Phase 8: User Accounts]
        P9[Phase 9: Checkout Flow]
        P10[Phase 10: Payment Integration]
        P11[Phase 11: Order Management]
    end

    subgraph Admin["🔧 ADMINISTRATION (Weeks 11-12)"]
        P12[Phase 12: Admin Panel]
        P13[Phase 13: Inventory & Analytics]
    end

    subgraph Launch["🚀 LAUNCH (Weeks 13-15)"]
        P14[Phase 14: Content & Marketing]
        P15[Phase 15: Testing & QA]
        P16[Phase 16: Deployment]
    end

    P1 --> P2
    P2 --> P3
    P3 --> P4
    P4 --> P5
    P5 --> P6
    P6 --> P7
    P7 --> P8
    P7 --> P9
    P8 --> P9
    P9 --> P10
    P10 --> P11
    P11 --> P12
    P12 --> P13
    P13 --> P14
    P14 --> P15
    P15 --> P16

    style Foundation fill:#e0f2fe
    style Core fill:#fef3c7
    style Commerce fill:#d1fae5
    style Admin fill:#fce7f3
    style Launch fill:#f3e8ff
🏗️ PHASE 1: Backend Foundation
Phase Objective
Establish the Laravel 12 API project with complete database schema, core configurations, and foundational services.

Prerequisites
PHP 8.3+ installed
Composer 2.x installed
PostgreSQL 16+ running
Redis 7.x running
Estimated Duration: 5 days
File Manifest
1.1 Project Configuration Files
composer.json
Purpose: Define PHP dependencies and project metadata.

Features:

Laravel 12 framework
Sanctum for API authentication
Filament for admin panel
Stripe SDK for payments
Meilisearch client for search
Laravel Horizon for queues
Spatie packages (permissions, media, sluggable)
Interfaces:

N/A (configuration file)
Dependencies:

None
Checklist:

 Define project name and description
 Add Laravel 12 framework dependency
 Add laravel/sanctum for API auth
 Add filament/filament for admin
 Add stripe/stripe-php for payments
 Add meilisearch/meilisearch-php for search
 Add laravel/horizon for queue dashboard
 Add spatie/laravel-permission for roles
 Add spatie/laravel-medialibrary for media
 Add spatie/laravel-sluggable for slugs
 Add resend/resend-php for email
 Add barryvdh/laravel-dompdf for invoices
 Add development dependencies (PHPUnit, Faker, IDE helpers)
 Configure autoload namespaces
 Define scripts for common tasks
.env.example
Purpose: Template for environment configuration.

Features:

Application settings
Database connection
Redis configuration
Mail configuration
Stripe API keys
Cloudinary credentials
Frontend URL for CORS
Interfaces:

N/A (configuration template)
Dependencies:

None
Checklist:

 APP_NAME, APP_ENV, APP_KEY, APP_DEBUG, APP_URL
 DB_CONNECTION=pgsql with host, port, database, username, password
 REDIS_HOST, REDIS_PASSWORD, REDIS_PORT
 MAIL_MAILER=resend with RESEND_API_KEY
 STRIPE_KEY, STRIPE_SECRET, STRIPE_WEBHOOK_SECRET
 CLOUDINARY_URL or individual credentials
 MEILISEARCH_HOST, MEILISEARCH_KEY
 FRONTEND_URL for CORS
 SANCTUM_STATEFUL_DOMAINS
 GST_RATE=0.09
 DEFAULT_CURRENCY=SGD
 SINGPOST_API_KEY, SINGPOST_API_SECRET
config/shop.php
Purpose: Custom e-commerce configuration values.

Features:

GST rate configuration
Currency settings
Cart limits
Abandoned cart timing
Inventory thresholds
Order number format
Interfaces:

PHP

return [
    'gst_rate' => env('GST_RATE', 0.09),
    'currency' => env('DEFAULT_CURRENCY', 'SGD'),
    'max_cart_items' => 12,
    'abandoned_cart_hours' => 24,
    'low_stock_threshold' => 10,
    'order_number_prefix' => 'AA',
    // ...
];
Dependencies:

None
Checklist:

 Define GST rate (9% for Singapore)
 Set default currency to SGD
 Configure max cart items (12)
 Set abandoned cart expiry (24 hours)
 Define low stock threshold
 Configure order number format
 Set default shipping rates
 Define product variant sizes
config/cors.php
Purpose: Configure Cross-Origin Resource Sharing for Next.js frontend.

Features:

Allowed origins (frontend URL)
Allowed methods
Allowed headers
Credentials support
Exposed headers
Interfaces:

PHP

return [
    'paths' => ['api/*', 'sanctum/csrf-cookie'],
    'allowed_origins' => [env('FRONTEND_URL', 'http://localhost:3000')],
    'allowed_methods' => ['*'],
    'allowed_headers' => ['*'],
    'supports_credentials' => true,
];
Dependencies:

fruitcake/laravel-cors (built into Laravel 12)
Checklist:

 Configure paths for API and Sanctum
 Set allowed origins from environment
 Allow all methods for REST API
 Enable credentials for Sanctum cookies
 Expose necessary headers
 Set max age for preflight caching
config/sanctum.php
Purpose: Configure Laravel Sanctum for SPA authentication.

Features:

Stateful domains for cookie auth
Token expiration
Guard configuration
Middleware customization
Interfaces:

PHP

return [
    'stateful' => explode(',', env('SANCTUM_STATEFUL_DOMAINS', 'localhost:3000')),
    'expiration' => null, // Tokens don't expire
    'guard' => ['web'],
    // ...
];
Dependencies:

laravel/sanctum
Checklist:

 Configure stateful domains for frontend
 Set token expiration policy
 Define authentication guard
 Configure middleware stack
1.2 Database Migrations
database/migrations/2024_01_01_000001_create_users_table.php
Purpose: Create users table with customer and admin roles.

Features:

UUID primary key
Name, email, password fields
Phone number for Singapore
Role enum (customer, admin, superadmin)
Email verification
Soft deletes
Interfaces:

PHP

Schema::create('users', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->string('name');
    $table->string('email')->unique();
    $table->string('password');
    $table->string('phone')->nullable();
    $table->enum('role', ['customer', 'admin', 'superadmin'])->default('customer');
    $table->timestamp('email_verified_at')->nullable();
    $table->rememberToken();
    $table->timestamps();
    $table->softDeletes();
});
Dependencies:

None
Checklist:

 UUID primary key for security
 Name field (required)
 Email field with unique constraint
 Hashed password field
 Phone field for Singapore numbers
 Role enum with default 'customer'
 Email verification timestamp
 Remember token for sessions
 Timestamps (created_at, updated_at)
 Soft deletes for data retention
 Index on email and role
database/migrations/2024_01_01_000002_create_categories_table.php
Purpose: Product categories (Singles, Blends, Sets, Gift).

Features:

UUID primary key
Name and slug (unique)
Description
Image URL
Sort order
Active status
Interfaces:

PHP

Schema::create('categories', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->string('name');
    $table->string('slug')->unique();
    $table->text('description')->nullable();
    $table->string('image_url')->nullable();
    $table->integer('sort_order')->default(0);
    $table->boolean('is_active')->default(true);
    $table->timestamps();
});
Dependencies:

None
Checklist:

 UUID primary key
 Category name
 URL-friendly slug (unique)
 Description text
 Image URL for category display
 Sort order for manual ordering
 Active toggle
 Timestamps
 Index on slug and is_active
database/migrations/2024_01_01_000003_create_products_table.php
Purpose: Main product (essence) records.

Features:

UUID primary key
Category relationship
Name, slug, Latin name
Short and long descriptions
Humour, rarity, season enums
Extraction method
Folio number
Featured and active flags
JSON metadata
Interfaces:

PHP

Schema::create('products', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('category_id')->constrained()->cascadeOnDelete();
    $table->string('name');
    $table->string('slug')->unique();
    $table->string('latin_name')->nullable();
    $table->text('description');
    $table->text('long_description')->nullable();
    $table->enum('humour', ['calming', 'uplifting', 'grounding', 'clarifying']);
    $table->enum('rarity', ['common', 'rare', 'limited'])->default('common');
    $table->enum('season', ['spring', 'summer', 'autumn', 'winter'])->nullable();
    $table->string('extraction_method')->nullable();
    $table->string('folio_number')->nullable();
    $table->boolean('is_featured')->default(false);
    $table->boolean('is_active')->default(true);
    $table->integer('sort_order')->default(0);
    $table->jsonb('meta_data')->nullable();
    $table->timestamps();
    $table->softDeletes();
});
Dependencies:

categories table
Checklist:

 UUID primary key
 Foreign key to categories
 Product name
 URL-friendly slug (unique)
 Latin botanical name
 Short description
 Long description for detail page
 Humour enum (calming, uplifting, grounding, clarifying)
 Rarity enum (common, rare, limited)
 Season enum (spring, summer, autumn, winter)
 Extraction method text
 Folio number for manuscript theme
 Featured flag
 Active flag
 Sort order
 JSONB metadata for flexibility
 Timestamps and soft deletes
 Indexes on slug, humour, rarity, is_active, is_featured
database/migrations/2024_01_01_000004_create_product_variants_table.php
Purpose: Product size variants (5ml, 15ml, 30ml phials).

Features:

UUID primary key
Product relationship
Variant name/size
SKU (unique)
Price in SGD
Compare-at price for sales
Weight for shipping
Default variant flag
Active status
Interfaces:

PHP

Schema::create('product_variants', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('product_id')->constrained()->cascadeOnDelete();
    $table->string('name'); // "5ml Phial", "15ml Phial", "30ml Phial"
    $table->string('sku')->unique();
    $table->decimal('price_sgd', 10, 2);
    $table->decimal('compare_at_price', 10, 2)->nullable();
    $table->integer('weight_grams')->default(0);
    $table->boolean('is_default')->default(false);
    $table->boolean('is_active')->default(true);
    $table->timestamps();
});
Dependencies:

products table
Checklist:

 UUID primary key
 Foreign key to products
 Variant name (5ml, 15ml, 30ml)
 Unique SKU
 Price in SGD (decimal 10,2)
 Compare-at price for strikethrough
 Weight in grams for shipping
 Default variant flag
 Active flag
 Timestamps
 Indexes on sku, product_id, is_active
database/migrations/2024_01_01_000005_create_product_images_table.php
Purpose: Multiple images per product.

Features:

UUID primary key
Product relationship
Image URL
Alt text for accessibility
Sort order
Primary image flag
Interfaces:

PHP

Schema::create('product_images', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('product_id')->constrained()->cascadeOnDelete();
    $table->string('url');
    $table->string('alt_text')->nullable();
    $table->integer('sort_order')->default(0);
    $table->boolean('is_primary')->default(false);
    $table->timestamps();
});
Dependencies:

products table
Checklist:

 UUID primary key
 Foreign key to products
 Image URL (Cloudinary)
 Alt text for accessibility
 Sort order for gallery
 Primary image flag
 Timestamps
 Index on product_id
database/migrations/2024_01_01_000006_create_tags_table.php
Purpose: Scent note tags for products.

Features:

UUID primary key
Tag name
URL-friendly slug
Interfaces:

PHP

Schema::create('tags', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->string('name')->unique();
    $table->string('slug')->unique();
    $table->timestamps();
});
Dependencies:

None
Checklist:

 UUID primary key
 Tag name (unique)
 Slug (unique)
 Timestamps
 Indexes on name and slug
database/migrations/2024_01_01_000007_create_product_tag_table.php
Purpose: Many-to-many pivot for products and tags.

Features:

Composite primary key
Foreign keys to products and tags
Interfaces:

PHP

Schema::create('product_tag', function (Blueprint $table) {
    $table->foreignUuid('product_id')->constrained()->cascadeOnDelete();
    $table->foreignUuid('tag_id')->constrained()->cascadeOnDelete();
    $table->primary(['product_id', 'tag_id']);
});
Dependencies:

products table
tags table
Checklist:

 Foreign key to products
 Foreign key to tags
 Composite primary key
 Cascade deletes
database/migrations/2024_01_01_000008_create_addresses_table.php
Purpose: Customer shipping and billing addresses.

Features:

UUID primary key
User relationship
Address label
Recipient details
Singapore address format
Default flags
Interfaces:

PHP

Schema::create('addresses', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('user_id')->constrained()->cascadeOnDelete();
    $table->string('label')->nullable(); // "Home", "Office"
    $table->string('recipient_name');
    $table->string('phone');
    $table->string('line_1');
    $table->string('line_2')->nullable();
    $table->string('postal_code', 10);
    $table->string('city')->default('Singapore');
    $table->string('country', 2)->default('SG');
    $table->boolean('is_default_shipping')->default(false);
    $table->boolean('is_default_billing')->default(false);
    $table->timestamps();
});
Dependencies:

users table
Checklist:

 UUID primary key
 Foreign key to users
 Address label
 Recipient name
 Phone number
 Address line 1 (required)
 Address line 2 (optional)
 Postal code (6 digits for SG)
 City (default Singapore)
 Country code (default SG)
 Default shipping flag
 Default billing flag
 Timestamps
 Index on user_id
database/migrations/2024_01_01_000009_create_carts_table.php
Purpose: Shopping cart for guests and authenticated users.

Features:

UUID primary key
Optional user relationship
Session ID for guests
Coupon relationship
Calculated totals
Expiration timestamp
Interfaces:

PHP

Schema::create('carts', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('user_id')->nullable()->constrained()->cascadeOnDelete();
    $table->string('session_id')->nullable()->index();
    $table->foreignUuid('coupon_id')->nullable()->constrained()->nullOnDelete();
    $table->decimal('subtotal', 10, 2)->default(0);
    $table->decimal('discount_amount', 10, 2)->default(0);
    $table->decimal('gst_amount', 10, 2)->default(0);
    $table->decimal('total', 10, 2)->default(0);
    $table->timestamp('expires_at')->nullable();
    $table->timestamps();
});
Dependencies:

users table
coupons table
Checklist:

 UUID primary key
 Nullable foreign key to users
 Session ID for guest carts
 Nullable foreign key to coupons
 Subtotal (before discounts)
 Discount amount
 GST amount (9%)
 Total (final amount)
 Expiration timestamp
 Timestamps
 Indexes on user_id, session_id, expires_at
database/migrations/2024_01_01_000010_create_cart_items_table.php
Purpose: Individual items in shopping cart.

Features:

UUID primary key
Cart relationship
Variant relationship
Quantity
Unit and total prices
Interfaces:

PHP

Schema::create('cart_items', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('cart_id')->constrained()->cascadeOnDelete();
    $table->foreignUuid('variant_id')->constrained('product_variants')->cascadeOnDelete();
    $table->integer('quantity')->default(1);
    $table->decimal('unit_price', 10, 2);
    $table->decimal('total_price', 10, 2);
    $table->timestamps();
});
Dependencies:

carts table
product_variants table
Checklist:

 UUID primary key
 Foreign key to carts
 Foreign key to product_variants
 Quantity (integer, minimum 1)
 Unit price at time of addition
 Total price (unit × quantity)
 Timestamps
 Unique constraint on cart_id + variant_id
 Index on cart_id
database/migrations/2024_01_01_000011_create_coupons_table.php
Purpose: Discount codes and promotions.

Features:

UUID primary key
Unique coupon code
Description
Type (percentage, fixed, free shipping)
Value
Minimum order amount
Usage limits
Date validity
Interfaces:

PHP

Schema::create('coupons', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->string('code')->unique();
    $table->text('description')->nullable();
    $table->enum('type', ['percentage', 'fixed_amount', 'free_shipping']);
    $table->decimal('value', 10, 2);
    $table->decimal('minimum_order_amount', 10, 2)->nullable();
    $table->integer('usage_limit')->nullable();
    $table->integer('usage_count')->default(0);
    $table->boolean('is_active')->default(true);
    $table->timestamp('starts_at')->nullable();
    $table->timestamp('expires_at')->nullable();
    $table->timestamps();
});
Dependencies:

None
Checklist:

 UUID primary key
 Unique coupon code (uppercase)
 Description text
 Type enum
 Value (percentage or fixed amount)
 Minimum order threshold
 Usage limit (per coupon)
 Usage count tracking
 Active flag
 Start date
 Expiry date
 Timestamps
 Index on code, is_active
database/migrations/2024_01_01_000012_create_coupon_usages_table.php
Purpose: Track coupon redemptions per user.

Features:

UUID primary key
Coupon, user, order relationships
Usage timestamp
Interfaces:

PHP

Schema::create('coupon_usages', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('coupon_id')->constrained()->cascadeOnDelete();
    $table->foreignUuid('user_id')->constrained()->cascadeOnDelete();
    $table->foreignUuid('order_id')->constrained()->cascadeOnDelete();
    $table->timestamp('used_at');
});
Dependencies:

coupons table
users table
orders table
Checklist:

 UUID primary key
 Foreign key to coupons
 Foreign key to users
 Foreign key to orders
 Usage timestamp
 Unique constraint on coupon_id + user_id (if single use per user)
database/migrations/2024_01_01_000013_create_orders_table.php
Purpose: Completed customer orders.

Features:

UUID primary key
User relationship
Unique order number
Status and payment status enums
Address snapshots
Pricing breakdown
Notes and tracking
Interfaces:

PHP

Schema::create('orders', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('user_id')->constrained()->cascadeOnDelete();
    $table->string('order_number')->unique();
    $table->enum('status', ['pending', 'processing', 'shipped', 'delivered', 'cancelled'])->default('pending');
    $table->enum('payment_status', ['pending', 'paid', 'failed', 'refunded'])->default('pending');
    $table->foreignUuid('shipping_address_id')->constrained('addresses')->restrictOnDelete();
    $table->foreignUuid('billing_address_id')->nullable()->constrained('addresses')->nullOnDelete();
    $table->foreignUuid('coupon_id')->nullable()->constrained()->nullOnDelete();
    $table->decimal('subtotal', 10, 2);
    $table->decimal('discount_amount', 10, 2)->default(0);
    $table->decimal('shipping_amount', 10, 2)->default(0);
    $table->decimal('gst_amount', 10, 2);
    $table->decimal('total', 10, 2);
    $table->text('notes')->nullable();
    $table->text('admin_notes')->nullable();
    $table->string('tracking_number')->nullable();
    $table->string('tracking_url')->nullable();
    $table->timestamp('shipped_at')->nullable();
    $table->timestamp('delivered_at')->nullable();
    $table->timestamps();
});
Dependencies:

users table
addresses table
coupons table
Checklist:

 UUID primary key
 Foreign key to users
 Unique order number (AA-YYYYMMDD-XXXX)
 Order status enum
 Payment status enum
 Foreign key to shipping address
 Nullable foreign key to billing address
 Nullable foreign key to coupon
 Subtotal
 Discount amount
 Shipping amount
 GST amount
 Total
 Customer notes
 Admin notes
 Tracking number
 Tracking URL
 Shipped timestamp
 Delivered timestamp
 Timestamps
 Indexes on order_number, user_id, status, payment_status
database/migrations/2024_01_01_000014_create_order_items_table.php
Purpose: Line items within an order.

Features:

UUID primary key
Order relationship
Variant relationship
Product snapshot data
Quantity and pricing
Interfaces:

PHP

Schema::create('order_items', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('order_id')->constrained()->cascadeOnDelete();
    $table->foreignUuid('variant_id')->constrained('product_variants')->restrictOnDelete();
    $table->string('product_name'); // Snapshot
    $table->string('variant_name'); // Snapshot
    $table->string('sku'); // Snapshot
    $table->integer('quantity');
    $table->decimal('unit_price', 10, 2);
    $table->decimal('total_price', 10, 2);
    $table->timestamps();
});
Dependencies:

orders table
product_variants table
Checklist:

 UUID primary key
 Foreign key to orders
 Foreign key to product_variants
 Product name snapshot
 Variant name snapshot
 SKU snapshot
 Quantity
 Unit price at purchase
 Total price
 Timestamps
 Index on order_id
database/migrations/2024_01_01_000015_create_payments_table.php
Purpose: Payment transaction records.

Features:

UUID primary key
Order relationship
Stripe identifiers
Payment method enum
Payment status enum
Amount and currency
Metadata and failure info
Interfaces:

PHP

Schema::create('payments', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('order_id')->constrained()->cascadeOnDelete();
    $table->string('stripe_payment_intent_id')->unique()->nullable();
    $table->string('stripe_charge_id')->nullable();
    $table->enum('method', ['card', 'paynow', 'grabpay'])->default('card');
    $table->enum('status', ['pending', 'succeeded', 'failed', 'refunded'])->default('pending');
    $table->decimal('amount', 10, 2);
    $table->string('currency', 3)->default('SGD');
    $table->jsonb('metadata')->nullable();
    $table->text('failure_reason')->nullable();
    $table->timestamp('paid_at')->nullable();
    $table->timestamp('refunded_at')->nullable();
    $table->timestamps();
});
Dependencies:

orders table
Checklist:

 UUID primary key
 Foreign key to orders
 Stripe PaymentIntent ID
 Stripe Charge ID
 Payment method enum
 Payment status enum
 Amount
 Currency (SGD)
 JSONB metadata
 Failure reason text
 Paid timestamp
 Refunded timestamp
 Timestamps
 Indexes on stripe_payment_intent_id, order_id, status
database/migrations/2024_01_01_000016_create_inventories_table.php
Purpose: Stock level tracking per variant.

Features:

UUID primary key
One-to-one variant relationship
Quantity on hand
Reserved quantity
Low stock threshold
Restock timestamp
Interfaces:

PHP

Schema::create('inventories', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('variant_id')->unique()->constrained('product_variants')->cascadeOnDelete();
    $table->integer('quantity')->default(0);
    $table->integer('reserved_quantity')->default(0);
    $table->integer('low_stock_threshold')->default(10);
    $table->timestamp('last_restocked_at')->nullable();
    $table->timestamps();
});
Dependencies:

product_variants table
Checklist:

 UUID primary key
 One-to-one with product_variants
 Quantity on hand
 Reserved quantity (pending orders)
 Low stock threshold
 Last restock timestamp
 Timestamps
 Index on quantity
database/migrations/2024_01_01_000017_create_inventory_movements_table.php
Purpose: Audit log for stock changes.

Features:

UUID primary key
Inventory relationship
Optional order relationship
Movement type enum
Quantity changed
Reason description
Interfaces:

PHP

Schema::create('inventory_movements', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('inventory_id')->constrained()->cascadeOnDelete();
    $table->foreignUuid('order_id')->nullable()->constrained()->nullOnDelete();
    $table->enum('type', ['addition', 'subtraction', 'reservation', 'release']);
    $table->integer('quantity');
    $table->string('reason')->nullable();
    $table->timestamp('created_at');
});
Dependencies:

inventories table
orders table
Checklist:

 UUID primary key
 Foreign key to inventories
 Nullable foreign key to orders
 Movement type enum
 Quantity (positive integer)
 Reason description
 Created timestamp
 Index on inventory_id, type
database/migrations/2024_01_01_000018_create_reviews_table.php
Purpose: Customer product reviews.

Features:

UUID primary key
Product, user, order relationships
Rating (1-5)
Title and body
Verified purchase flag
Approval status
Interfaces:

PHP

Schema::create('reviews', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('product_id')->constrained()->cascadeOnDelete();
    $table->foreignUuid('user_id')->constrained()->cascadeOnDelete();
    $table->foreignUuid('order_id')->nullable()->constrained()->nullOnDelete();
    $table->tinyInteger('rating')->unsigned();
    $table->string('title')->nullable();
    $table->text('body');
    $table->boolean('is_verified_purchase')->default(false);
    $table->boolean('is_approved')->default(false);
    $table->timestamps();
});
Dependencies:

products table
users table
orders table
Checklist:

 UUID primary key
 Foreign key to products
 Foreign key to users
 Nullable foreign key to orders
 Rating 1-5 (tinyInteger)
 Review title
 Review body
 Verified purchase flag
 Approval status
 Timestamps
 Unique constraint on product_id + user_id
 Index on product_id, is_approved
database/migrations/2024_01_01_000019_create_testimonials_table.php
Purpose: Featured patron testimonials (non-product specific).

Features:

UUID primary key
Author information
Quote text
Display options
Sort order
Interfaces:

PHP

Schema::create('testimonials', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->string('author_name');
    $table->string('author_title')->nullable();
    $table->text('quote');
    $table->boolean('is_verified')->default(false);
    $table->boolean('is_illuminated')->default(false);
    $table->string('folio_reference')->nullable();
    $table->integer('sort_order')->default(0);
    $table->boolean('is_active')->default(true);
    $table->timestamps();
});
Dependencies:

None
Checklist:

 UUID primary key
 Author name
 Author title/occupation
 Quote text
 Verified flag
 Illuminated flag (featured style)
 Folio reference number
 Sort order
 Active flag
 Timestamps
 Index on is_active
database/migrations/2024_01_01_000020_create_wishlists_table.php
Purpose: User wishlist containers.

Features:

UUID primary key
User relationship
Wishlist name
Interfaces:

PHP

Schema::create('wishlists', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('user_id')->constrained()->cascadeOnDelete();
    $table->string('name')->default('Bookmarked Essences');
    $table->timestamps();
});
Dependencies:

users table
Checklist:

 UUID primary key
 Foreign key to users
 Wishlist name with default
 Timestamps
 Index on user_id
database/migrations/2024_01_01_000021_create_wishlist_items_table.php
Purpose: Products in wishlists.

Features:

UUID primary key
Wishlist relationship
Product relationship
Added timestamp
Interfaces:

PHP

Schema::create('wishlist_items', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('wishlist_id')->constrained()->cascadeOnDelete();
    $table->foreignUuid('product_id')->constrained()->cascadeOnDelete();
    $table->timestamp('added_at');
    
    $table->unique(['wishlist_id', 'product_id']);
});
Dependencies:

wishlists table
products table
Checklist:

 UUID primary key
 Foreign key to wishlists
 Foreign key to products
 Added timestamp
 Unique constraint on wishlist_id + product_id
database/migrations/2024_01_01_000022_create_newsletter_subscribers_table.php
Purpose: Email newsletter subscriptions.

Features:

UUID primary key
Email and name
Confirmation status
Subscription lifecycle
Interfaces:

PHP

Schema::create('newsletter_subscribers', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->string('email')->unique();
    $table->string('name')->nullable();
    $table->boolean('is_confirmed')->default(false);
    $table->string('confirmation_token')->nullable();
    $table->timestamp('confirmed_at')->nullable();
    $table->timestamp('unsubscribed_at')->nullable();
    $table->timestamps();
});
Dependencies:

None
Checklist:

 UUID primary key
 Unique email
 Optional name
 Confirmation flag
 Confirmation token
 Confirmed timestamp
 Unsubscribed timestamp
 Timestamps
 Index on email, is_confirmed
database/migrations/2024_01_01_000023_create_settings_table.php
Purpose: Key-value store for site configuration.

Features:

UUID primary key
Key and value
Value type hint
Interfaces:

PHP

Schema::create('settings', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->string('key')->unique();
    $table->text('value')->nullable();
    $table->string('type')->default('string'); // string, integer, boolean, json
    $table->timestamps();
});
Dependencies:

None
Checklist:

 UUID primary key
 Unique key
 Value text
 Type hint
 Timestamps
 Index on key
1.3 Eloquent Models
app/Models/User.php
Purpose: Customer and admin user model.

Features:

UUID trait
Authenticatable
Has API tokens (Sanctum)
Has many addresses, orders, reviews, wishlists
Role-based helpers
Interfaces:

PHP

class User extends Authenticatable
{
    use HasFactory, HasApiTokens, Notifiable, SoftDeletes;
    use HasUuids;

    protected $fillable = ['name', 'email', 'password', 'phone', 'role'];
    protected $hidden = ['password', 'remember_token'];
    protected $casts = [
        'email_verified_at' => 'datetime',
        'password' => 'hashed',
        'role' => UserRole::class,
    ];

    // Relationships
    public function addresses(): HasMany;
    public function orders(): HasMany;
    public function reviews(): HasMany;
    public function wishlist(): HasOne;
    public function cart(): HasOne;

    // Helpers
    public function isAdmin(): bool;
    public function isSuperAdmin(): bool;
    public function defaultShippingAddress(): ?Address;
}
Dependencies:

Address, Order, Review, Wishlist, Cart models
UserRole enum
Checklist:

 Use HasUuids trait
 Use HasApiTokens (Sanctum)
 Use SoftDeletes
 Define fillable fields
 Hide password and token
 Cast role to enum
 addresses() hasMany relationship
 orders() hasMany relationship
 reviews() hasMany relationship
 wishlist() hasOne relationship
 cart() hasOne relationship
 isAdmin() helper method
 isSuperAdmin() helper method
 defaultShippingAddress() helper
 defaultBillingAddress() helper
app/Models/Product.php
Purpose: Essence product model.

Features:

UUID trait
Sluggable behavior
Searchable (Scout)
Category, variants, images, tags relationships
Scopes for filtering
Interfaces:

PHP

class Product extends Model
{
    use HasFactory, HasUuids, Sluggable, Searchable, SoftDeletes;

    protected $fillable = [
        'category_id', 'name', 'slug', 'latin_name', 'description',
        'long_description', 'humour', 'rarity', 'season',
        'extraction_method', 'folio_number', 'is_featured', 'is_active',
        'sort_order', 'meta_data',
    ];

    protected $casts = [
        'humour' => ProductHumour::class,
        'rarity' => ProductRarity::class,
        'season' => ProductSeason::class,
        'is_featured' => 'boolean',
        'is_active' => 'boolean',
        'meta_data' => 'array',
    ];

    // Relationships
    public function category(): BelongsTo;
    public function variants(): HasMany;
    public function images(): HasMany;
    public function tags(): BelongsToMany;
    public function reviews(): HasMany;

    // Accessors
    public function getPrimaryImageAttribute(): ?ProductImage;
    public function getDefaultVariantAttribute(): ?ProductVariant;
    public function getPriceRangeAttribute(): array;
    public function getAverageRatingAttribute(): float;

    // Scopes
    public function scopeActive(Builder $query): Builder;
    public function scopeFeatured(Builder $query): Builder;
    public function scopeByHumour(Builder $query, string $humour): Builder;
    public function scopeByRarity(Builder $query, string $rarity): Builder;
    public function scopeBySeason(Builder $query, string $season): Builder;
}
Dependencies:

Category, ProductVariant, ProductImage, Tag, Review models
ProductHumour, ProductRarity, ProductSeason enums
Sluggable, Searchable traits
Checklist:

 Use HasUuids trait
 Use Sluggable trait (Spatie)
 Use Searchable trait (Scout)
 Use SoftDeletes
 Define fillable fields
 Cast enums (humour, rarity, season)
 Cast booleans and JSON
 category() belongsTo relationship
 variants() hasMany relationship
 images() hasMany relationship
 tags() belongsToMany relationship
 reviews() hasMany relationship
 getPrimaryImageAttribute accessor
 getDefaultVariantAttribute accessor
 getPriceRangeAttribute accessor
 getAverageRatingAttribute accessor
 scopeActive query scope
 scopeFeatured query scope
 scopeByHumour query scope
 scopeByRarity query scope
 scopeBySeason query scope
 toSearchableArray() for Meilisearch
app/Models/ProductVariant.php
Purpose: Product size variant (5ml, 15ml, 30ml).

Features:

UUID trait
Product relationship
Inventory relationship
Price formatting
Interfaces:

PHP

class ProductVariant extends Model
{
    use HasFactory, HasUuids;

    protected $fillable = [
        'product_id', 'name', 'sku', 'price_sgd',
        'compare_at_price', 'weight_grams', 'is_default', 'is_active',
    ];

    protected $casts = [
        'price_sgd' => 'decimal:2',
        'compare_at_price' => 'decimal:2',
        'is_default' => 'boolean',
        'is_active' => 'boolean',
    ];

    // Relationships
    public function product(): BelongsTo;
    public function inventory(): HasOne;
    public function cartItems(): HasMany;
    public function orderItems(): HasMany;

    // Accessors
    public function getFormattedPriceAttribute(): string;
    public function getIsOnSaleAttribute(): bool;
    public function getAvailableQuantityAttribute(): int;

    // Methods
    public function isInStock(): bool;
    public function reserveStock(int $quantity): bool;
    public function releaseStock(int $quantity): bool;
}
Dependencies:

Product, Inventory, CartItem, OrderItem models
Checklist:

 Use HasUuids trait
 Define fillable fields
 Cast decimals and booleans
 product() belongsTo relationship
 inventory() hasOne relationship
 cartItems() hasMany relationship
 orderItems() hasMany relationship
 getFormattedPriceAttribute accessor
 getIsOnSaleAttribute accessor
 getAvailableQuantityAttribute accessor
 isInStock() method
 reserveStock() method
 releaseStock() method
[Continue with remaining models following same pattern: Category, Cart, CartItem, Order, OrderItem, Payment, Inventory, Address, Review, Testimonial, Wishlist, WishlistItem, Coupon, CouponUsage, NewsletterSubscriber, Setting, Tag, ProductImage]

1.4 Enums
app/Enums/UserRole.php
Purpose: User role enumeration.

Features:

Customer, Admin, SuperAdmin values
Label method for display
Color method for UI
Interfaces:

PHP

enum UserRole: string
{
    case Customer = 'customer';
    case Admin = 'admin';
    case SuperAdmin = 'superadmin';

    public function label(): string
    {
        return match($this) {
            self::Customer => 'Customer',
            self::Admin => 'Administrator',
            self::SuperAdmin => 'Super Administrator',
        };
    }
}
Dependencies:

None
Checklist:

 Define Customer case
 Define Admin case
 Define SuperAdmin case
 label() method for display
 isAtLeast() helper for permission checks
app/Enums/OrderStatus.php
Purpose: Order lifecycle status.

Interfaces:

PHP

enum OrderStatus: string
{
    case Pending = 'pending';
    case Processing = 'processing';
    case Shipped = 'shipped';
    case Delivered = 'delivered';
    case Cancelled = 'cancelled';

    public function label(): string;
    public function color(): string;
    public function icon(): string;
    public function canTransitionTo(OrderStatus $status): bool;
}
Checklist:

 Define all status cases
 label() for display names
 color() for UI badges
 icon() for status icons
 canTransitionTo() for valid transitions
app/Enums/PaymentStatus.php
Purpose: Payment transaction status.

Interfaces:

PHP

enum PaymentStatus: string
{
    case Pending = 'pending';
    case Succeeded = 'succeeded';
    case Failed = 'failed';
    case Refunded = 'refunded';
}
Checklist:

 Define all status cases
 label() method
 color() method
app/Enums/PaymentMethod.php
Purpose: Available payment methods.

Interfaces:

PHP

enum PaymentMethod: string
{
    case Card = 'card';
    case PayNow = 'paynow';
    case GrabPay = 'grabpay';
}
Checklist:

 Define all payment method cases
 label() method
 icon() method
app/Enums/ProductHumour.php
Purpose: Product humour classification.

Interfaces:

PHP

enum ProductHumour: string
{
    case Calming = 'calming';
    case Uplifting = 'uplifting';
    case Grounding = 'grounding';
    case Clarifying = 'clarifying';

    public function label(): string;
    public function symbol(): string;
    public function color(): string;
}
Checklist:

 Define all humour cases
 label() for display names
 symbol() for alchemical symbols (☾ ☀ ♁ ☁)
 color() for theme colors
app/Enums/ProductRarity.php
Purpose: Product rarity classification.

Interfaces:

PHP

enum ProductRarity: string
{
    case Common = 'common';
    case Rare = 'rare';
    case Limited = 'limited';
}
Checklist:

 Define all rarity cases
 label() method
 color() method
app/Enums/ProductSeason.php
Purpose: Product seasonal classification.

Interfaces:

PHP

enum ProductSeason: string
{
    case Spring = 'spring';
    case Summer = 'summer';
    case Autumn = 'autumn';
    case Winter = 'winter';
}
Checklist:

 Define all season cases
 label() method (e.g., "Early Spring")
1.5 Core Services
app/Services/GSTService.php
Purpose: Singapore GST calculation service.

Features:

Calculate GST from subtotal
Calculate inclusive/exclusive GST
Format for display
Configurable rate
Interfaces:

PHP

class GSTService
{
    public function __construct(
        private float $rate = 0.09
    ) {}

    public function calculateGST(float $subtotal): float;
    public function calculateGSTInclusive(float $total): float;
    public function formatGST(float $amount): string;
    public function getRate(): float;
}
Dependencies:

config/shop.php
Checklist:

 Constructor with configurable rate
 calculateGST() from subtotal
 calculateGSTInclusive() from total
 formatGST() with currency
 getRate() accessor
 Unit tests for calculations
app/Services/CartService.php
Purpose: Shopping cart business logic.

Features:

Get or create cart
Add, update, remove items
Calculate totals with GST
Apply/remove coupons
Merge guest cart on login
Cart expiration
Interfaces:

PHP

class CartService
{
    public function getCart(?User $user, ?string $sessionId): Cart;
    public function createCart(?User $user, ?string $sessionId): Cart;
    public function addItem(Cart $cart, ProductVariant $variant, int $quantity = 1): CartItem;
    public function updateItemQuantity(CartItem $item, int $quantity): CartItem;
    public function removeItem(CartItem $item): void;
    public function clearCart(Cart $cart): void;
    public function applyCoupon(Cart $cart, string $code): Cart;
    public function removeCoupon(Cart $cart): Cart;
    public function calculateTotals(Cart $cart): Cart;
    public function mergeGuestCart(Cart $guestCart, User $user): Cart;
    public function cleanExpiredCarts(): int;
}
Dependencies:

Cart, CartItem, ProductVariant, User, Coupon models
GSTService
CouponService
Checklist:

 getCart() find by user or session
 createCart() with expiration
 addItem() with stock validation
 updateItemQuantity() with limits
 removeItem() with recalculation
 clearCart() remove all items
 applyCoupon() with validation
 removeCoupon()
 calculateTotals() with GST
 mergeGuestCart() on login
 cleanExpiredCarts() scheduled task
 Events for cart changes
 Unit tests
app/Services/InventoryService.php
Purpose: Stock management and tracking.

Features:

Check availability
Reserve stock for checkout
Release reserved stock
Deduct stock on order
Restock products
Low stock alerts
Interfaces:

PHP

class InventoryService
{
    public function isAvailable(ProductVariant $variant, int $quantity = 1): bool;
    public function getAvailableQuantity(ProductVariant $variant): int;
    public function reserve(ProductVariant $variant, int $quantity, ?Order $order = null): bool;
    public function release(ProductVariant $variant, int $quantity, ?Order $order = null): bool;
    public function deduct(ProductVariant $variant, int $quantity, Order $order): bool;
    public function restock(ProductVariant $variant, int $quantity, string $reason = 'Manual restock'): bool;
    public function checkLowStock(ProductVariant $variant): bool;
    public function getLowStockVariants(): Collection;
}
Dependencies:

Inventory, InventoryMovement, ProductVariant, Order models
InventoryLow event
Checklist:

 isAvailable() check quantity
 getAvailableQuantity() (quantity - reserved)
 reserve() for checkout
 release() on cart/order cancel
 deduct() on order completion
 restock() with movement log
 checkLowStock() against threshold
 getLowStockVariants() for alerts
 Log all movements
 Dispatch LowStock event
 Unit tests
app/Services/CouponService.php
Purpose: Discount code validation and application.

Features:

Validate coupon code
Check eligibility
Calculate discount
Track usage
Interfaces:

PHP

class CouponService
{
    public function findByCode(string $code): ?Coupon;
    public function validate(Coupon $coupon, Cart $cart, ?User $user = null): ValidationResult;
    public function calculateDiscount(Coupon $coupon, float $subtotal): float;
    public function recordUsage(Coupon $coupon, User $user, Order $order): CouponUsage;
    public function isExpired(Coupon $coupon): bool;
    public function hasReachedLimit(Coupon $coupon): bool;
    public function hasUserUsed(Coupon $coupon, User $user): bool;
}
Dependencies:

Coupon, CouponUsage, Cart, User, Order models
InvalidCouponException
Checklist:

 findByCode() case-insensitive
 validate() comprehensive checks
 calculateDiscount() by type
 recordUsage() after order
 isExpired() check dates
 hasReachedLimit() check count
 hasUserUsed() per-user limit
 Throw InvalidCouponException
 Return ValidationResult object
 Unit tests
1.6 Database Seeders
database/seeders/DatabaseSeeder.php
Purpose: Main seeder orchestrator.

Interfaces:

PHP

class DatabaseSeeder extends Seeder
{
    public function run(): void
    {
        $this->call([
            UserSeeder::class,
            CategorySeeder::class,
            TagSeeder::class,
            ProductSeeder::class,
            TestimonialSeeder::class,
            SettingsSeeder::class,
        ]);
    }
}
Checklist:

 Call seeders in correct order
 Handle production vs development
database/seeders/UserSeeder.php
Purpose: Create admin and test users.

Checklist:

 Create superadmin user
 Create admin user
 Create test customer (dev only)
 Hash passwords properly
database/seeders/CategorySeeder.php
Purpose: Create product categories.

Checklist:

 Create "Single Essences" category
 Create "Blended Essences" category
 Create "Gift Sets" category
 Create "Accessories" category
 Set sort orders
 Add descriptions
database/seeders/ProductSeeder.php
Purpose: Create sample essence products.

Checklist:

 Create 12 essence products
 Create 3 variants per product (5ml, 15ml, 30ml)
 Assign categories
 Create inventory records
 Add product images
 Add scent note tags
 Set featured products
 Vary humours, rarities, seasons
database/seeders/TestimonialSeeder.php
Purpose: Create patron testimonials.

Checklist:

 Create 7+ testimonials
 Set one as illuminated (featured)
 Add verified flag to some
 Set folio references
 Order by sort_order
database/seeders/SettingsSeeder.php
Purpose: Initialize site settings.

Checklist:

 Set shop name
 Set contact email
 Set GST rate
 Set default currency
 Set social media URLs
Phase 1 Completion Checklist
text

┌─────────────────────────────────────────────────────────────────────────────┐
│ PHASE 1: BACKEND FOUNDATION — COMPLETION CHECKLIST                         │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│ Configuration                                                               │
│ ─────────────                                                               │
│ [ ] composer.json with all dependencies                                     │
│ [ ] .env.example with all variables                                         │
│ [ ] config/shop.php custom config                                           │
│ [ ] config/cors.php for Next.js                                             │
│ [ ] config/sanctum.php for SPA auth                                         │
│                                                                             │
│ Database                                                                    │
│ ────────                                                                    │
│ [ ] All 23 migrations created                                               │
│ [ ] Migrations run successfully                                             │
│ [ ] Indexes created for performance                                         │
│ [ ] Foreign keys with proper cascades                                       │
│                                                                             │
│ Models                                                                      │
│ ──────                                                                      │
│ [ ] All 18 Eloquent models created                                          │
│ [ ] Relationships defined correctly                                         │
│ [ ] Accessors and scopes implemented                                        │
│ [ ] Casts configured for enums/JSON                                         │
│                                                                             │
│ Enums                                                                       │
│ ─────                                                                       │
│ [ ] All 7 enums created                                                     │
│ [ ] Helper methods implemented                                              │
│                                                                             │
│ Services                                                                    │
│ ────────                                                                    │
│ [ ] GSTService implemented                                                  │
│ [ ] CartService implemented                                                 │
│ [ ] InventoryService implemented                                            │
│ [ ] CouponService implemented                                               │
│                                                                             │
│ Seeders                                                                     │
│ ───────                                                                     │
│ [ ] All seeders created                                                     │
│ [ ] Sample data seeded successfully                                         │
│                                                                             │
│ Testing                                                                     │
│ ───────                                                                     │
│ [ ] Database migrations tested                                              │
│ [ ] Models relationships tested                                             │
│ [ ] Service unit tests passing                                              │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
🎨 PHASE 2: Frontend Foundation
Phase Objective
Establish the Next.js 15 project with TypeScript, configure the design system with Tailwind CSS 4.0, and set up Shadcn-UI components.

Prerequisites
Node.js 20+ installed
pnpm or npm installed
Phase 1 completed
Estimated Duration: 4 days
File Manifest
2.1 Project Configuration Files
package.json
Purpose: Node.js dependencies and scripts.

Features:

Next.js 15 framework
React 19
TypeScript 5.x
Tailwind CSS 4.0
Shadcn-UI dependencies
Framer Motion
State management (Zustand, TanStack Query)
Form handling (React Hook Form, Zod)
Interfaces:

JSON

{
  "name": "atelier-arome-web",
  "version": "1.0.0",
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "next lint",
    "type-check": "tsc --noEmit"
  },
  "dependencies": {
    "next": "^15.0.0",
    "react": "^19.0.0",
    "react-dom": "^19.0.0",
    // ... all dependencies
  }
}
Checklist:

 Next.js 15 and React 19
 TypeScript 5.x
 Tailwind CSS 4.0
 @radix-ui/* components
 class-variance-authority
 clsx and tailwind-merge
 framer-motion
 zustand
 @tanstack/react-query
 react-hook-form
 @hookform/resolvers
 zod
 lucide-react
 next-auth (if using)
 axios or native fetch
 date-fns
 Development dependencies (ESLint, Prettier, TypeScript)
 Scripts for dev, build, lint, type-check
tsconfig.json
Purpose: TypeScript compiler configuration.

Features:

Strict mode enabled
Path aliases
Next.js plugin
Module resolution
Interfaces:

JSON

{
  "compilerOptions": {
    "target": "ES2022",
    "lib": ["dom", "dom.iterable", "esnext"],
    "allowJs": true,
    "skipLibCheck": true,
    "strict": true,
    "noEmit": true,
    "esModuleInterop": true,
    "module": "esnext",
    "moduleResolution": "bundler",
    "resolveJsonModule": true,
    "isolatedModules": true,
    "jsx": "preserve",
    "incremental": true,
    "plugins": [{ "name": "next" }],
    "paths": {
      "@/*": ["./src/*"]
    }
  },
  "include": ["next-env.d.ts", "**/*.ts", "**/*.tsx", ".next/types/**/*.ts"],
  "exclude": ["node_modules"]
}
Checklist:

 Target ES2022
 Strict mode enabled
 Next.js plugin configured
 Path alias @/* → ./src/*
 Include all TypeScript files
 Exclude node_modules
tailwind.config.ts
Purpose: Tailwind CSS configuration with Atelier Arôme design tokens.

Features:

Extended color palette (ink, gold, parchment, botanicals)
Custom typography scale (fluid)
Font families (Cormorant Garamond, Crimson Pro, Great Vibes)
Spacing scale (golden ratio)
Custom shadows
Animation keyframes
Shadcn-UI integration
Interfaces:

TypeScript

import type { Config } from 'tailwindcss'

const config: Config = {
  darkMode: ['class'],
  content: ['./src/**/*.{ts,tsx}'],
  theme: {
    extend: {
      colors: {
        ink: { DEFAULT: '#2A2D26', light: '#4A4D46', muted: '#545752' },
        gold: { DEFAULT: '#C9A769', light: '#E8D8B6', dark: '#A98750', muted: 'rgba(201, 167, 105, 0.3)', text: '#8B7355' },
        parchment: { DEFAULT: '#FAF8F5', dark: '#F5F1EB', darker: '#E8E4D9' },
        // ... botanical colors
      },
      fontFamily: {
        display: ['var(--font-cormorant)', 'Georgia', 'serif'],
        body: ['var(--font-crimson)', 'Georgia', 'serif'],
        accent: ['var(--font-great-vibes)', 'cursive'],
      },
      // ... rest of config
    }
  },
  plugins: [
    require('tailwindcss-animate'),
    require('@tailwindcss/typography'),
  ],
}

export default config
Checklist:

 Configure darkMode with class strategy
 Set content paths for src directory
 Define ink color scale
 Define gold color scale
 Define parchment color scale
 Define botanical accent colors (lavender, eucalyptus, bergamot, rosehip)
 Configure font families with CSS variables
 Define fluid typography scale
 Define spacing scale
 Define border-radius scale
 Define box-shadow scale
 Define z-index scale
 Define keyframe animations
 Define animation utilities
 Add tailwindcss-animate plugin
 Add @tailwindcss/typography plugin
next.config.ts
Purpose: Next.js configuration.

Features:

Image optimization domains
Environment variables
Redirect/rewrite rules
Security headers
Interfaces:

TypeScript

import type { NextConfig } from 'next'

const nextConfig: NextConfig = {
  images: {
    remotePatterns: [
      { protocol: 'https', hostname: 'res.cloudinary.com' },
      { protocol: 'https', hostname: 'images.unsplash.com' },
    ],
  },
  env: {
    NEXT_PUBLIC_API_URL: process.env.NEXT_PUBLIC_API_URL,
  },
  async headers() {
    return [
      {
        source: '/:path*',
        headers: [
          { key: 'X-Frame-Options', value: 'DENY' },
          { key: 'X-Content-Type-Options', value: 'nosniff' },
          { key: 'Referrer-Policy', value: 'strict-origin-when-cross-origin' },
        ],
      },
    ]
  },
}

export default nextConfig
Checklist:

 Configure image domains (Cloudinary)
 Expose public environment variables
 Add security headers
 Configure redirects if needed
 Enable experimental features if needed
components.json
Purpose: Shadcn-UI configuration.

Interfaces:

JSON

{
  "$schema": "https://ui.shadcn.com/schema.json",
  "style": "default",
  "rsc": true,
  "tsx": true,
  "tailwind": {
    "config": "tailwind.config.ts",
    "css": "src/app/globals.css",
    "baseColor": "neutral",
    "cssVariables": true,
    "prefix": ""
  },
  "aliases": {
    "components": "@/components",
    "utils": "@/lib/utils",
    "ui": "@/components/ui",
    "lib": "@/lib",
    "hooks": "@/hooks"
  }
}
Checklist:

 Set style to default
 Enable RSC (React Server Components)
 Enable TSX
 Configure Tailwind paths
 Set baseColor to neutral
 Enable CSS variables
 Configure path aliases
.env.local.example
Purpose: Frontend environment template.

Checklist:

 NEXT_PUBLIC_API_URL
 NEXT_PUBLIC_SITE_URL
 NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY
 NEXTAUTH_SECRET
 NEXTAUTH_URL
2.2 Global Styles and Fonts
src/app/globals.css
Purpose: Global styles, Tailwind directives, and CSS custom properties.

Features:

Tailwind base, components, utilities
CSS custom properties for colors
Font-face declarations
Global element styles
Shadcn-UI component styles
Interfaces:

CSS

@tailwind base;
@tailwind components;
@tailwind utilities;

@layer base {
  :root {
    /* Colors */
    --color-ink: 42 45 38;
    --color-gold: 201 167 105;
    --color-parchment: 250 248 245;
    /* ... more variables */
    
    /* Radii */
    --radius: 0.5rem;
    
    /* Shadcn variables */
    --background: 0 0% 100%;
    --foreground: 42 8% 14%;
    /* ... */
  }
}

@layer base {
  * {
    @apply border-border;
  }
  body {
    @apply bg-parchment text-ink font-body;
  }
}

/* Custom component styles */
@layer components {
  .section-label { /* ... */ }
  .section-title { /* ... */ }
  /* ... */
}
Checklist:

 Tailwind directives
 CSS custom properties for all colors
 Typography variables
 Spacing variables
 Shadcn-UI required variables
 Body default styles
 Focus visible styles
 Selection styles
 Custom component classes
 Animation utilities
 Reduced motion media query
src/styles/fonts.ts
Purpose: Font configuration using next/font.

Features:

Cormorant Garamond (display)
Crimson Pro (body)
Great Vibes (accent)
CSS variables for each font
Interfaces:

TypeScript

import { Cormorant_Garamond, Crimson_Pro, Great_Vibes } from 'next/font/google'

export const cormorantGaramond = Cormorant_Garamond({
  subsets: ['latin'],
  weight: ['300', '400', '500', '600', '700'],
  style: ['normal', 'italic'],
  variable: '--font-cormorant',
  display: 'swap',
})

export const crimsonPro = Crimson_Pro({
  subsets: ['latin'],
  weight: ['300', '400', '500', '600', '700'],
  style: ['normal', 'italic'],
  variable: '--font-crimson',
  display: 'swap',
})

export const greatVibes = Great_Vibes({
  subsets: ['latin'],
  weight: ['400'],
  variable: '--font-great-vibes',
  display: 'swap',
})

export const fontVariables = `${cormorantGaramond.variable} ${crimsonPro.variable} ${greatVibes.variable}`
Checklist:

 Import Cormorant Garamond with weights
 Import Crimson Pro with weights
 Import Great Vibes
 Configure CSS variables
 Set display: swap for performance
 Export combined variables string
src/styles/animations.ts
Purpose: Framer Motion animation variants.

Features:

Page transition variants
Stagger children variants
Fade in/out variants
Slide variants
Scale variants
Reduced motion considerations
Interfaces:

TypeScript

import { Variants } from 'framer-motion'

export const fadeIn: Variants = {
  hidden: { opacity: 0 },
  visible: { opacity: 1, transition: { duration: 0.5 } },
}

export const slideUp: Variants = {
  hidden: { opacity: 0, y: 20 },
  visible: { opacity: 1, y: 0, transition: { duration: 0.5 } },
}

export const staggerContainer: Variants = {
  hidden: { opacity: 0 },
  visible: {
    opacity: 1,
    transition: { staggerChildren: 0.1 },
  },
}

export const scaleIn: Variants = {
  hidden: { opacity: 0, scale: 0.95 },
  visible: { opacity: 1, scale: 1, transition: { duration: 0.3 } },
}

// More variants...
Checklist:

 fadeIn variant
 fadeOut variant
 slideUp variant
 slideDown variant
 slideLeft variant
 slideRight variant
 scaleIn variant
 staggerContainer variant
 staggerItem variant
 Page transition variants
 Drawer/modal variants
 Toast variants
 Reduced motion fallbacks
2.3 Core Utilities
src/lib/utils/cn.ts
Purpose: Utility for merging Tailwind classes.

Features:

Merge class names
Handle conditional classes
Resolve Tailwind conflicts
Interfaces:

TypeScript

import { type ClassValue, clsx } from 'clsx'
import { twMerge } from 'tailwind-merge'

export function cn(...inputs: ClassValue[]): string {
  return twMerge(clsx(inputs))
}
Checklist:

 Import clsx
 Import twMerge
 Export cn function
 Type properly with ClassValue
src/lib/utils/format-currency.ts
Purpose: Currency formatting for SGD.

Interfaces:

TypeScript

export function formatCurrency(
  amount: number,
  currency: string = 'SGD',
  locale: string = 'en-SG'
): string {
  return new Intl.NumberFormat(locale, {
    style: 'currency',
    currency,
    minimumFractionDigits: 2,
    maximumFractionDigits: 2,
  }).format(amount)
}

export function formatCurrencyCompact(amount: number): string {
  return `$${amount.toFixed(0)}`
}
Checklist:

 formatCurrency with full formatting
 formatCurrencyCompact for prices
 Handle zero and negative values
 Default to SGD and en-SG locale
src/lib/utils/format-date.ts
Purpose: Date formatting utilities.

Interfaces:

TypeScript

import { format, formatDistanceToNow, parseISO } from 'date-fns'

export function formatDate(date: string | Date, pattern: string = 'MMM d, yyyy'): string;
export function formatDateTime(date: string | Date): string;
export function formatRelative(date: string | Date): string;
export function formatOrderDate(date: string | Date): string;
Checklist:

 formatDate with customizable pattern
 formatDateTime for full timestamp
 formatRelative for "2 hours ago"
 formatOrderDate for order display
 Handle string and Date inputs
src/lib/utils/calculate-gst.ts
Purpose: Client-side GST calculation (matching backend).

Interfaces:

TypeScript

const GST_RATE = 0.09

export function calculateGST(subtotal: number): number {
  return subtotal * GST_RATE
}

export function calculateTotalWithGST(subtotal: number): number {
  return subtotal * (1 + GST_RATE)
}

export function calculateGSTFromTotal(total: number): number {
  return total - (total / (1 + GST_RATE))
}
Checklist:

 Define GST_RATE constant
 calculateGST from subtotal
 calculateTotalWithGST
 calculateGSTFromTotal (reverse)
 Round to 2 decimal places
src/lib/constants/alchemical-data.ts
Purpose: Static data for humours, seasons, rarities.

Interfaces:

TypeScript

export const HUMOURS = {
  calming: { symbol: '☾', label: 'Calming', color: 'lavender' },
  uplifting: { symbol: '☀', label: 'Uplifting', color: 'bergamot' },
  grounding: { symbol: '♁', label: 'Grounding', color: 'sage' },
  clarifying: { symbol: '☁', label: 'Clarifying', color: 'eucalyptus' },
} as const

export const RARITIES = {
  common: { label: 'Common', color: 'ink-muted' },
  rare: { label: 'Rare', color: 'gold' },
  limited: { label: 'Limited', color: 'rose' },
} as const

export const SEASONS = {
  spring: { label: 'Early Spring' },
  summer: { label: 'High Summer' },
  autumn: { label: 'Autumn' },
  winter: { label: 'Winter' },
} as const
Checklist:

 HUMOURS object with symbols and colors
 RARITIES object with labels and colors
 SEASONS object with labels
 Type exports for TypeScript
src/lib/constants/site-config.ts
Purpose: Site-wide configuration constants.

Interfaces:

TypeScript

export const SITE_CONFIG = {
  name: 'Atelier Arôme',
  tagline: 'Artisanal Alchemy for the Senses',
  description: 'Aromatherapy elevated to artisanal alchemy...',
  url: process.env.NEXT_PUBLIC_SITE_URL || 'https://atelierarome.sg',
  ogImage: '/images/og-image.jpg',
  locale: 'en-SG',
  currency: 'SGD',
  gstRate: 0.09,
  maxCartItems: 12,
  socialLinks: {
    instagram: 'https://instagram.com/atelierarome',
    pinterest: 'https://pinterest.com/atelierarome',
  },
  contact: {
    email: 'correspondence@atelierarome.sg',
    address: '...',
  },
}
Checklist:

 Site name and tagline
 Meta description
 Site URL from env
 OG image path
 Locale and currency
 GST rate
 Cart limits
 Social links
 Contact information
src/lib/constants/navigation.ts
Purpose: Navigation structure.

Interfaces:

TypeScript

export const MAIN_NAV = [
  { number: 'I', label: 'Compendium', href: '/compendium' },
  { number: 'II', label: 'Alchemy', href: '/alchemy' },
  { number: 'III', label: 'The Atelier', href: '/about' },
  { number: 'IV', label: 'Manuscript', href: '/testimonials' },
]

export const FOOTER_NAV = {
  folios: [...],
  correspondence: [...],
  legal: [...],
}

export const ACCOUNT_NAV = [...]
Checklist:

 Main navigation items
 Footer navigation sections
 Account navigation items
 Mobile navigation items
 Type exports
2.4 Type Definitions
src/types/product.ts
Purpose: Product-related TypeScript types.

Interfaces:

TypeScript

export type ProductHumour = 'calming' | 'uplifting' | 'grounding' | 'clarifying'
export type ProductRarity = 'common' | 'rare' | 'limited'
export type ProductSeason = 'spring' | 'summer' | 'autumn' | 'winter'

export interface Product {
  id: string
  categoryId: string
  name: string
  slug: string
  latinName: string | null
  description: string
  longDescription: string | null
  humour: ProductHumour
  rarity: ProductRarity
  season: ProductSeason | null
  extractionMethod: string | null
  folioNumber: string | null
  isFeatured: boolean
  isActive: boolean
  
