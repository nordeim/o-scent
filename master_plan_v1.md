MASTER_EXECUTION_PLAN.md
Atelier Arôme — E-Commerce Platform
text

╔══════════════════════════════════════════════════════════════════════════════╗
║                                                                              ║
║   █████╗ ████████╗███████╗██╗     ██╗███████╗██████╗                        ║
║  ██╔══██╗╚══██╔══╝██╔════╝██║     ██║██╔════╝██╔══██╗                       ║
║  ███████║   ██║   █████╗  ██║     ██║█████╗  ██████╔╝                       ║
║  ██╔══██║   ██║   ██╔══╝  ██║     ██║██╔══╝  ██╔══██╗                       ║
║  ██║  ██║   ██║   ███████╗███████╗██║███████╗██║  ██║                       ║
║  ╚═╝  ╚═╝   ╚═╝   ╚══════╝╚══════╝╚═╝╚══════╝╚═╝  ╚═╝                       ║
║                                                                              ║
║   █████╗ ██████╗  ██████╗ ███╗   ███╗███████╗                               ║
║  ██╔══██╗██╔══██╗██╔═══██╗████╗ ████║██╔════╝                               ║
║  ███████║██████╔╝██║   ██║██╔████╔██║█████╗                                 ║
║  ██╔══██║██╔══██╗██║   ██║██║╚██╔╝██║██╔══╝                                 ║
║  ██║  ██║██║  ██║╚██████╔╝██║ ╚═╝ ██║███████╗                               ║
║  ╚═╝  ╚═╝╚═╝  ╚═╝ ╚═════╝ ╚═╝     ╚═╝╚══════╝                               ║
║                                                                              ║
║                    MASTER EXECUTION PLAN                                     ║
║                    Version 1.0.0                                             ║
║                    Last Updated: 2024                                        ║
║                                                                              ║
╚══════════════════════════════════════════════════════════════════════════════╝
Table of Contents
Executive Overview
Phase Dependencies Map
Phase 1: Backend Foundation
Phase 2: Frontend Foundation
Phase 3: Authentication System
Phase 4: Product Catalog
Phase 5: Shopping Cart
Phase 6: Checkout & Payments
Phase 7: Order Management
Phase 8: User Account
Phase 9: Admin Panel
Phase 10: Search & Discovery
Phase 11: Reviews & Social Proof
Phase 12: Performance & Optimization
Phase 13: Testing Suite
Phase 14: Deployment & Launch
Post-Launch Roadmap
1. Executive Overview
Project Scope
Metric	Value
Total Phases	14
Backend Files	~85 files
Frontend Files	~120 files
Database Tables	22 tables
API Endpoints	~65 endpoints
Estimated Duration	15-18 weeks
Technology Stack Summary
text

┌─────────────────────────────────────────────────────────────────────────────┐
│  BACKEND (Laravel 12)              │  FRONTEND (Next.js 15)                │
├─────────────────────────────────────────────────────────────────────────────┤
│  • PHP 8.3+                        │  • React 19                           │
│  • Laravel Sanctum (Auth)          │  • TypeScript 5.x                     │
│  • Eloquent ORM                    │  • Tailwind CSS 4.0                   │
│  • PostgreSQL 16                   │  • Shadcn-UI + Radix                  │
│  • Redis 7.x                       │  • Framer Motion                      │
│  • Meilisearch                     │  • Zustand + TanStack Query           │
│  • Filament 3.x (Admin)            │  • React Hook Form + Zod              │
│  • Stripe SDK                      │  • NextAuth.js v5                     │
│  • Resend (Email)                  │  • Vercel Deployment                  │
└─────────────────────────────────────────────────────────────────────────────┘
Execution Principles
Vertical Slicing: Each phase delivers end-to-end functionality
API-First: Backend endpoints completed before frontend consumption
Test-Driven: Critical paths have tests before features ship
Incremental Deployment: Each phase is deployable to staging
Documentation-Inline: Code documentation written alongside implementation
2. Phase Dependencies Map
mermaid

flowchart TB
    subgraph Foundation["Foundation Layer"]
        P1[Phase 1: Backend Foundation]
        P2[Phase 2: Frontend Foundation]
    end
    
    subgraph Core["Core Commerce"]
        P3[Phase 3: Authentication]
        P4[Phase 4: Product Catalog]
        P5[Phase 5: Shopping Cart]
        P6[Phase 6: Checkout & Payments]
        P7[Phase 7: Order Management]
    end
    
    subgraph Extended["Extended Features"]
        P8[Phase 8: User Account]
        P9[Phase 9: Admin Panel]
        P10[Phase 10: Search]
        P11[Phase 11: Reviews]
    end
    
    subgraph Launch["Launch Preparation"]
        P12[Phase 12: Performance]
        P13[Phase 13: Testing]
        P14[Phase 14: Deployment]
    end
    
    P1 --> P2
    P1 --> P3
    P2 --> P3
    P3 --> P4
    P4 --> P5
    P5 --> P6
    P6 --> P7
    P3 --> P8
    P7 --> P8
    P1 --> P9
    P4 --> P9
    P7 --> P9
    P4 --> P10
    P7 --> P11
    P8 --> P11
    
    P9 --> P12
    P10 --> P12
    P11 --> P12
    P12 --> P13
    P13 --> P14

    style P1 fill:#1e3a5f
    style P2 fill:#1e3a5f
    style P3 fill:#2d4a3e
    style P4 fill:#2d4a3e
    style P5 fill:#2d4a3e
    style P6 fill:#2d4a3e
    style P7 fill:#2d4a3e
    style P8 fill:#4a3f35
    style P9 fill:#4a3f35
    style P10 fill:#4a3f35
    style P11 fill:#4a3f35
    style P12 fill:#3d2c4a
    style P13 fill:#3d2c4a
    style P14 fill:#3d2c4a
Critical Path
text

P1 → P3 → P4 → P5 → P6 → P7 → P14
Minimum Viable Product (MVP) requires Phases 1-7 + 14.

Phase 1: Backend Foundation
Overview
Attribute	Value
Duration	5-7 days
Priority	Critical
Dependencies	None
Deliverables	Laravel project, database schema, core models
Files to Create
1.1 Project Configuration Files
File: composer.json
Attribute	Details
Path	atelier-arome-api/composer.json
Purpose	PHP dependency management and autoloading configuration
Priority	Critical
Features:

Laravel 12.x framework requirement
Sanctum for API authentication
Horizon for queue management
Stripe SDK for payments
Filament admin panel packages
Meilisearch Scout driver
Interfaces:

JSON

{
  "require": {
    "php": "^8.3",
    "laravel/framework": "^12.0",
    "laravel/sanctum": "^4.0",
    "laravel/horizon": "^5.0",
    "stripe/stripe-php": "^13.0",
    "filament/filament": "^3.0",
    "meilisearch/meilisearch-php": "^1.0",
    "laravel/scout": "^10.0",
    "cloudinary-labs/cloudinary-laravel": "^2.0",
    "resend/resend-php": "^0.10"
  }
}
Checklist:

 Define PHP version requirement (8.3+)
 Add Laravel 12 framework dependency
 Add authentication packages (Sanctum)
 Add queue management (Horizon)
 Add payment processing (Stripe)
 Add admin panel (Filament)
 Add search engine (Meilisearch/Scout)
 Add media management (Cloudinary)
 Add email service (Resend)
 Configure PSR-4 autoloading
 Add development dependencies (PHPUnit, Pint, PHPStan)
 Run composer install and verify
File: .env.example
Attribute	Details
Path	atelier-arome-api/.env.example
Purpose	Environment variable template for all deployments
Priority	Critical
Features:

Database configuration (PostgreSQL)
Redis connection settings
Stripe API keys
Cloudinary credentials
Resend API key
Meilisearch configuration
Singapore-specific settings (GST, currency)
Interfaces:

env

# Application
APP_NAME="Atelier Arôme API"
APP_ENV=local
APP_KEY=
APP_DEBUG=true
APP_URL=http://localhost:8000
FRONTEND_URL=http://localhost:3000

# Database
DB_CONNECTION=pgsql
DB_HOST=127.0.0.1
DB_PORT=5432
DB_DATABASE=atelier_arome
DB_USERNAME=postgres
DB_PASSWORD=

# Redis
REDIS_HOST=127.0.0.1
REDIS_PASSWORD=null
REDIS_PORT=6379

# Stripe
STRIPE_KEY=pk_test_...
STRIPE_SECRET=sk_test_...
STRIPE_WEBHOOK_SECRET=whsec_...

# Cloudinary
CLOUDINARY_URL=cloudinary://...

# Resend
RESEND_API_KEY=re_...
MAIL_FROM_ADDRESS=correspondence@atelierarome.com
MAIL_FROM_NAME="Atelier Arôme"

# Meilisearch
MEILISEARCH_HOST=http://127.0.0.1:7700
MEILISEARCH_KEY=

# Singapore Settings
SHOP_CURRENCY=SGD
SHOP_GST_RATE=0.09
SHOP_COUNTRY=SG
Checklist:

 Define all application settings
 Configure database connection variables
 Add Redis configuration
 Add Stripe keys placeholder
 Add Cloudinary URL placeholder
 Add Resend API key placeholder
 Add Meilisearch configuration
 Define Singapore-specific shop settings
 Add CORS frontend URL
 Document each variable with comments
File: config/shop.php
Attribute	Details
Path	atelier-arome-api/config/shop.php
Purpose	E-commerce specific configuration
Priority	High
Features:

Currency settings (SGD)
GST rate configuration (9%)
Cart limits and expiry
Order number format
Shipping defaults
Payment methods configuration
Interfaces:

PHP

<?php

return [
    'currency' => env('SHOP_CURRENCY', 'SGD'),
    'currency_symbol' => 'S$',
    'country' => env('SHOP_COUNTRY', 'SG'),
    
    'tax' => [
        'gst_rate' => (float) env('SHOP_GST_RATE', 0.09),
        'gst_name' => 'GST',
        'inclusive' => false,
    ],
    
    'cart' => [
        'max_items' => 12,
        'session_lifetime_hours' => 72,
        'abandoned_threshold_hours' => 24,
    ],
    
    'order' => [
        'number_prefix' => 'AA',
        'number_format' => '{prefix}-{date}-{sequence}',
    ],
    
    'shipping' => [
        'default_country' => 'SG',
        'free_shipping_threshold' => 150.00,
    ],
    
    'payment' => [
        'methods' => ['card', 'paynow', 'grabpay'],
        'default_method' => 'card',
    ],
    
    'inventory' => [
        'low_stock_threshold' => 5,
        'allow_backorder' => false,
    ],
];
Checklist:

 Define currency configuration (SGD)
 Set GST rate (9%)
 Configure cart limitations
 Define order number format
 Set shipping defaults
 Configure payment methods
 Set inventory thresholds
 Add environment variable fallbacks
 Document configuration options
File: config/cors.php
Attribute	Details
Path	atelier-arome-api/config/cors.php
Purpose	Cross-Origin Resource Sharing configuration for Next.js frontend
Priority	Critical
Features:

Allow Next.js frontend origin
Configure allowed headers for API requests
Enable credentials for cookie-based auth
Set appropriate cache times
Interfaces:

PHP

<?php

return [
    'paths' => ['api/*', 'sanctum/csrf-cookie'],
    
    'allowed_methods' => ['*'],
    
    'allowed_origins' => [
        env('FRONTEND_URL', 'http://localhost:3000'),
    ],
    
    'allowed_origins_patterns' => [],
    
    'allowed_headers' => ['*'],
    
    'exposed_headers' => [],
    
    'max_age' => 0,
    
    'supports_credentials' => true,
];
Checklist:

 Configure allowed origins for frontend
 Enable credentials support
 Set allowed methods
 Configure API and Sanctum paths
 Test CORS with frontend requests
1.2 Database Migrations
File: 2024_01_01_000001_create_users_table.php
Attribute	Details
Path	database/migrations/2024_01_01_000001_create_users_table.php
Purpose	User accounts for customers and administrators
Priority	Critical
Features:

UUID primary keys for security
Role-based access (customer, admin, superadmin)
Email verification support
Soft deletes for data retention
Optimized indexes
Schema:

PHP

Schema::create('users', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->string('name');
    $table->string('email')->unique();
    $table->timestamp('email_verified_at')->nullable();
    $table->string('password');
    $table->string('phone', 20)->nullable();
    $table->enum('role', ['customer', 'admin', 'superadmin'])->default('customer');
    $table->rememberToken();
    $table->timestamps();
    $table->softDeletes();
    
    $table->index(['email', 'role']);
    $table->index('created_at');
});
Checklist:

 Use UUID for primary key
 Add all required columns
 Implement role enum
 Add soft deletes
 Create performance indexes
 Add email uniqueness constraint
 Test migration up/down
File: 2024_01_01_000002_create_categories_table.php
Attribute	Details
Path	database/migrations/2024_01_01_000002_create_categories_table.php
Purpose	Product categories (Singles, Blends, Sets, Gift)
Priority	High
Schema:

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
    
    $table->index(['is_active', 'sort_order']);
});
Checklist:

 Create UUID primary key
 Add slug with unique constraint
 Include sort_order for ordering
 Add is_active flag
 Create composite index
 Test migration
File: 2024_01_01_000003_create_products_table.php
Attribute	Details
Path	database/migrations/2024_01_01_000003_create_products_table.php
Purpose	Essence products with alchemical attributes
Priority	Critical
Schema:

PHP

Schema::create('products', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('category_id')->constrained()->onDelete('cascade');
    $table->string('name');
    $table->string('slug')->unique();
    $table->string('latin_name')->nullable();
    $table->text('description');
    $table->text('long_description')->nullable();
    $table->enum('humour', ['calming', 'uplifting', 'grounding', 'clarifying']);
    $table->enum('rarity', ['common', 'rare', 'limited'])->default('common');
    $table->enum('season', ['spring', 'summer', 'autumn', 'winter']);
    $table->string('extraction_method')->nullable();
    $table->string('folio_number', 10)->nullable();
    $table->boolean('is_featured')->default(false);
    $table->boolean('is_active')->default(true);
    $table->integer('sort_order')->default(0);
    $table->jsonb('meta_data')->nullable();
    $table->timestamps();
    $table->softDeletes();
    
    $table->index(['is_active', 'is_featured']);
    $table->index(['humour', 'is_active']);
    $table->index(['rarity', 'is_active']);
    $table->index(['season', 'is_active']);
    $table->index('category_id');
});
Checklist:

 Create UUID primary key
 Add foreign key to categories
 Implement humour/rarity/season enums
 Add featured and active flags
 Include JSONB for flexible metadata
 Add soft deletes
 Create filter-optimized indexes
 Test cascade delete behavior
File: 2024_01_01_000004_create_product_variants_table.php
Attribute	Details
Path	database/migrations/2024_01_01_000004_create_product_variants_table.php
Purpose	Size variants (5ml, 15ml, 30ml phials)
Priority	Critical
Schema:

PHP

Schema::create('product_variants', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('product_id')->constrained()->onDelete('cascade');
    $table->string('name'); // "5ml Phial", "15ml Phial", "30ml Phial"
    $table->string('sku')->unique();
    $table->decimal('price', 10, 2);
    $table->decimal('compare_at_price', 10, 2)->nullable();
    $table->integer('weight_grams')->default(50);
    $table->boolean('is_default')->default(false);
    $table->boolean('is_active')->default(true);
    $table->timestamps();
    
    $table->index(['product_id', 'is_active']);
    $table->index('sku');
});
Checklist:

 Create UUID primary key
 Add foreign key to products
 Include SKU with uniqueness
 Add price and compare_at_price
 Include weight for shipping
 Add is_default flag
 Create product lookup index
 Test cascade behavior
File: 2024_01_01_000005_create_product_images_table.php
Attribute	Details
Path	database/migrations/2024_01_01_000005_create_product_images_table.php
Purpose	Multiple product images with ordering
Priority	High
Schema:

PHP

Schema::create('product_images', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('product_id')->constrained()->onDelete('cascade');
    $table->string('url');
    $table->string('alt_text')->nullable();
    $table->integer('sort_order')->default(0);
    $table->boolean('is_primary')->default(false);
    $table->timestamps();
    
    $table->index(['product_id', 'sort_order']);
});
Checklist:

 Create UUID primary key
 Add foreign key to products
 Include URL and alt text
 Add sort_order for gallery ordering
 Add is_primary flag
 Create composite index
 Test cascade behavior
File: 2024_01_01_000006_create_tags_table.php
Attribute	Details
Path	database/migrations/2024_01_01_000006_create_tags_table.php
Purpose	Scent notes tagging (Floral, Herbaceous, Citrus, etc.)
Priority	Medium
Schema:

PHP

Schema::create('tags', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->string('name')->unique();
    $table->string('slug')->unique();
    $table->timestamps();
});

Schema::create('product_tag', function (Blueprint $table) {
    $table->foreignUuid('product_id')->constrained()->onDelete('cascade');
    $table->foreignUuid('tag_id')->constrained()->onDelete('cascade');
    $table->primary(['product_id', 'tag_id']);
});
Checklist:

 Create tags table with UUID
 Add name and slug uniqueness
 Create pivot table for product_tag
 Add composite primary key
 Test many-to-many relationship
File: 2024_01_01_000007_create_addresses_table.php
Attribute	Details
Path	database/migrations/2024_01_01_000007_create_addresses_table.php
Purpose	Saved shipping and billing addresses
Priority	High
Schema:

PHP

Schema::create('addresses', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('user_id')->constrained()->onDelete('cascade');
    $table->string('label')->default('Home');
    $table->string('recipient_name');
    $table->string('phone', 20);
    $table->string('line_1');
    $table->string('line_2')->nullable();
    $table->string('postal_code', 10);
    $table->string('city')->default('Singapore');
    $table->string('country', 2)->default('SG');
    $table->boolean('is_default_shipping')->default(false);
    $table->boolean('is_default_billing')->default(false);
    $table->timestamps();
    
    $table->index(['user_id', 'is_default_shipping']);
});
Checklist:

 Create UUID primary key
 Add foreign key to users
 Include all address fields
 Add default shipping/billing flags
 Set Singapore defaults
 Create user lookup index
File: 2024_01_01_000008_create_carts_table.php
Attribute	Details
Path	database/migrations/2024_01_01_000008_create_carts_table.php
Purpose	Shopping carts (supports guest and authenticated)
Priority	Critical
Schema:

PHP

Schema::create('carts', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('user_id')->nullable()->constrained()->onDelete('cascade');
    $table->string('session_id')->nullable()->index();
    $table->foreignUuid('coupon_id')->nullable()->constrained()->nullOnDelete();
    $table->decimal('subtotal', 10, 2)->default(0);
    $table->decimal('discount_amount', 10, 2)->default(0);
    $table->decimal('gst_amount', 10, 2)->default(0);
    $table->decimal('total', 10, 2)->default(0);
    $table->timestamp('expires_at')->nullable();
    $table->timestamps();
    
    $table->index(['user_id']);
    $table->index(['session_id', 'expires_at']);
});
Checklist:

 Create UUID primary key
 Add nullable user_id for guests
 Add session_id for guest tracking
 Include pricing columns
 Add expires_at for cart cleanup
 Create user and session indexes
 Test guest cart functionality
File: 2024_01_01_000009_create_cart_items_table.php
Attribute	Details
Path	database/migrations/2024_01_01_000009_create_cart_items_table.php
Purpose	Cart line items with quantity and pricing
Priority	Critical
Schema:

PHP

Schema::create('cart_items', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('cart_id')->constrained()->onDelete('cascade');
    $table->foreignUuid('variant_id')->constrained('product_variants')->onDelete('cascade');
    $table->integer('quantity')->default(1);
    $table->decimal('unit_price', 10, 2);
    $table->decimal('total_price', 10, 2);
    $table->timestamps();
    
    $table->unique(['cart_id', 'variant_id']);
    $table->index('cart_id');
});
Checklist:

 Create UUID primary key
 Add foreign keys to cart and variant
 Include quantity and pricing
 Add unique constraint for cart+variant
 Create cart lookup index
 Test cascade behavior
File: 2024_01_01_000010_create_orders_table.php
Attribute	Details
Path	database/migrations/2024_01_01_000010_create_orders_table.php
Purpose	Completed customer orders
Priority	Critical
Schema:

PHP

Schema::create('orders', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('user_id')->constrained()->onDelete('restrict');
    $table->string('order_number', 20)->unique();
    $table->enum('status', ['pending', 'processing', 'shipped', 'delivered', 'cancelled'])
          ->default('pending');
    $table->enum('payment_status', ['pending', 'paid', 'failed', 'refunded'])
          ->default('pending');
    $table->foreignUuid('shipping_address_id')->constrained('addresses')->onDelete('restrict');
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
    
    $table->index(['user_id', 'status']);
    $table->index(['status', 'created_at']);
    $table->index('order_number');
    $table->index('payment_status');
});
Checklist:

 Create UUID primary key
 Add foreign key to users
 Generate unique order numbers
 Implement status enums
 Add address references
 Include all pricing columns
 Add tracking information
 Create status/date indexes
 Test order number generation
File: 2024_01_01_000011_create_order_items_table.php
Attribute	Details
Path	database/migrations/2024_01_01_000011_create_order_items_table.php
Purpose	Order line items with snapshotted product data
Priority	Critical
Schema:

PHP

Schema::create('order_items', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('order_id')->constrained()->onDelete('cascade');
    $table->foreignUuid('variant_id')->constrained('product_variants')->onDelete('restrict');
    $table->string('product_name'); // Snapshot
    $table->string('variant_name'); // Snapshot
    $table->string('sku'); // Snapshot
    $table->integer('quantity');
    $table->decimal('unit_price', 10, 2);
    $table->decimal('total_price', 10, 2);
    $table->timestamps();
    
    $table->index('order_id');
});
Checklist:

 Create UUID primary key
 Add foreign keys
 Include product snapshots
 Add pricing columns
 Create order lookup index
 Test snapshot preservation
File: 2024_01_01_000012_create_payments_table.php
Attribute	Details
Path	database/migrations/2024_01_01_000012_create_payments_table.php
Purpose	Payment records and Stripe integration tracking
Priority	Critical
Schema:

PHP

Schema::create('payments', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('order_id')->constrained()->onDelete('cascade');
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
    
    $table->index('order_id');
    $table->index('stripe_payment_intent_id');
    $table->index(['status', 'created_at']);
});
Checklist:

 Create UUID primary key
 Add Stripe identifiers
 Implement payment method enum
 Add status tracking
 Include metadata JSONB
 Create necessary indexes
 Test payment recording
File: 2024_01_01_000013_create_coupons_table.php
Attribute	Details
Path	database/migrations/2024_01_01_000013_create_coupons_table.php
Purpose	Discount codes and promotions
Priority	Medium
Schema:

PHP

Schema::create('coupons', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->string('code', 32)->unique();
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
    
    $table->index(['code', 'is_active']);
    $table->index(['is_active', 'starts_at', 'expires_at']);
});
Checklist:

 Create UUID primary key
 Add unique code constraint
 Implement discount type enum
 Add usage tracking
 Include date restrictions
 Create validity indexes
 Test coupon validation
File: 2024_01_01_000014_create_coupon_usages_table.php
Attribute	Details
Path	database/migrations/2024_01_01_000014_create_coupon_usages_table.php
Purpose	Track coupon redemptions
Priority	Medium
Schema:

PHP

Schema::create('coupon_usages', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('coupon_id')->constrained()->onDelete('cascade');
    $table->foreignUuid('user_id')->constrained()->onDelete('cascade');
    $table->foreignUuid('order_id')->constrained()->onDelete('cascade');
    $table->timestamp('used_at');
    
    $table->unique(['coupon_id', 'user_id', 'order_id']);
    $table->index('coupon_id');
});
Checklist:

 Create UUID primary key
 Add all foreign keys
 Add unique constraint
 Create lookup indexes
File: 2024_01_01_000015_create_inventories_table.php
Attribute	Details
Path	database/migrations/2024_01_01_000015_create_inventories_table.php
Purpose	Stock level tracking per variant
Priority	High
Schema:

PHP

Schema::create('inventories', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('variant_id')->unique()->constrained('product_variants')->onDelete('cascade');
    $table->integer('quantity')->default(0);
    $table->integer('reserved_quantity')->default(0);
    $table->integer('low_stock_threshold')->default(5);
    $table->timestamp('last_restocked_at')->nullable();
    $table->timestamps();
    
    $table->index(['quantity', 'low_stock_threshold']);
});
Checklist:

 Create UUID primary key
 Add one-to-one with variants
 Include reserved quantity
 Add low stock threshold
 Create stock level index
File: 2024_01_01_000016_create_inventory_movements_table.php
Attribute	Details
Path	database/migrations/2024_01_01_000016_create_inventory_movements_table.php
Purpose	Audit log for inventory changes
Priority	Medium
Schema:

PHP

Schema::create('inventory_movements', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('inventory_id')->constrained()->onDelete('cascade');
    $table->foreignUuid('order_id')->nullable()->constrained()->nullOnDelete();
    $table->enum('type', ['addition', 'subtraction', 'reservation', 'release']);
    $table->integer('quantity');
    $table->string('reason')->nullable();
    $table->timestamps();
    
    $table->index(['inventory_id', 'created_at']);
});
Checklist:

 Create UUID primary key
 Add foreign keys
 Implement movement type enum
 Create audit index
File: 2024_01_01_000017_create_reviews_table.php
Attribute	Details
Path	database/migrations/2024_01_01_000017_create_reviews_table.php
Purpose	Product reviews from verified purchasers
Priority	Medium
Schema:

PHP

Schema::create('reviews', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('product_id')->constrained()->onDelete('cascade');
    $table->foreignUuid('user_id')->constrained()->onDelete('cascade');
    $table->foreignUuid('order_id')->nullable()->constrained()->nullOnDelete();
    $table->tinyInteger('rating'); // 1-5
    $table->string('title')->nullable();
    $table->text('body');
    $table->boolean('is_verified_purchase')->default(false);
    $table->boolean('is_approved')->default(false);
    $table->timestamps();
    
    $table->unique(['product_id', 'user_id']);
    $table->index(['product_id', 'is_approved']);
    $table->index(['is_approved', 'created_at']);
});
Checklist:

 Create UUID primary key
 Add foreign keys
 Enforce one review per product per user
 Add moderation flag
 Create approval indexes
File: 2024_01_01_000018_create_testimonials_table.php
Attribute	Details
Path	database/migrations/2024_01_01_000018_create_testimonials_table.php
Purpose	Curated patron testimonials (Manuscript section)
Priority	Medium
Schema:

PHP

Schema::create('testimonials', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->string('author_name');
    $table->string('author_title');
    $table->text('quote');
    $table->boolean('is_verified')->default(false);
    $table->boolean('is_illuminated')->default(false); // Featured styling
    $table->string('folio_reference')->nullable();
    $table->integer('sort_order')->default(0);
    $table->boolean('is_active')->default(true);
    $table->timestamps();
    
    $table->index(['is_active', 'sort_order']);
});
Checklist:

 Create UUID primary key
 Add author information
 Include illuminated flag
 Add sort ordering
 Create active/sort index
File: 2024_01_01_000019_create_wishlists_table.php
Attribute	Details
Path	database/migrations/2024_01_01_000019_create_wishlists_table.php
Purpose	User wishlists ("Bookmarked Essences")
Priority	Medium
Schema:

PHP

Schema::create('wishlists', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('user_id')->constrained()->onDelete('cascade');
    $table->string('name')->default('Bookmarked Essences');
    $table->timestamps();
    
    $table->index('user_id');
});

Schema::create('wishlist_items', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('wishlist_id')->constrained()->onDelete('cascade');
    $table->foreignUuid('product_id')->constrained()->onDelete('cascade');
    $table->timestamp('added_at');
    
    $table->unique(['wishlist_id', 'product_id']);
});
Checklist:

 Create wishlists table
 Create wishlist_items pivot
 Add unique constraint
 Create user lookup index
File: 2024_01_01_000020_create_newsletter_subscribers_table.php
Attribute	Details
Path	database/migrations/2024_01_01_000020_create_newsletter_subscribers_table.php
Purpose	Email newsletter subscriptions (Quarterly Folio)
Priority	Medium
Schema:

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
    
    $table->index(['is_confirmed', 'unsubscribed_at']);
});
Checklist:

 Create UUID primary key
 Add email uniqueness
 Include confirmation flow
 Add unsubscribe tracking
 Create subscription status index
File: 2024_01_01_000021_create_settings_table.php
Attribute	Details
Path	database/migrations/2024_01_01_000021_create_settings_table.php
Purpose	Site configuration and settings
Priority	Low
Schema:

PHP

Schema::create('settings', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->string('key')->unique();
    $table->text('value');
    $table->string('type')->default('string'); // string, integer, boolean, json
    $table->timestamps();
});
Checklist:

 Create UUID primary key
 Add unique key constraint
 Include type casting
 Add timestamps
1.3 Eloquent Models
File: app/Models/User.php
Attribute	Details
Path	atelier-arome-api/app/Models/User.php
Purpose	User model with authentication and relationships
Priority	Critical
Features:

UUID trait
Sanctum HasApiTokens
Role-based methods
Relationships to orders, addresses, cart, wishlist, reviews
Interfaces:

PHP

class User extends Authenticatable
{
    use HasApiTokens, HasFactory, Notifiable, HasUuids, SoftDeletes;
    
    // Relationships
    public function addresses(): HasMany;
    public function orders(): HasMany;
    public function cart(): HasOne;
    public function wishlist(): HasOne;
    public function reviews(): HasMany;
    
    // Role methods
    public function isAdmin(): bool;
    public function isSuperAdmin(): bool;
    public function isCustomer(): bool;
    
    // Scopes
    public function scopeCustomers(Builder $query): Builder;
    public function scopeAdmins(Builder $query): Builder;
}
Checklist:

 Extend Authenticatable
 Use HasApiTokens trait
 Use HasUuids trait
 Implement SoftDeletes
 Define all relationships
 Add role checking methods
 Create query scopes
 Define hidden/casts arrays
 Add password hashing mutator
 Write model tests
File: app/Models/Product.php
Attribute	Details
Path	atelier-arome-api/app/Models/Product.php
Purpose	Essence product model with alchemical attributes
Priority	Critical
Features:

UUID and SoftDeletes
Category, variants, images relationships
Humour/rarity/season enum casting
Scout searchable integration
Price accessor (from default variant)
Interfaces:

PHP

class Product extends Model
{
    use HasFactory, HasUuids, SoftDeletes, Searchable;
    
    // Relationships
    public function category(): BelongsTo;
    public function variants(): HasMany;
    public function defaultVariant(): HasOne;
    public function images(): HasMany;
    public function primaryImage(): HasOne;
    public function tags(): BelongsToMany;
    public function reviews(): HasMany;
    public function wishlistItems(): HasMany;
    
    // Accessors
    public function getPriceAttribute(): float;
    public function getFormattedPriceAttribute(): string;
    public function getAverageRatingAttribute(): ?float;
    public function getHumourDataAttribute(): array;
    
    // Scopes
    public function scopeActive(Builder $query): Builder;
    public function scopeFeatured(Builder $query): Builder;
    public function scopeByHumour(Builder $query, string $humour): Builder;
    public function scopeByRarity(Builder $query, string $rarity): Builder;
    public function scopeBySeason(Builder $query, string $season): Builder;
    
    // Scout
    public function toSearchableArray(): array;
}
Checklist:

 Use HasUuids and SoftDeletes
 Define all relationships
 Cast enums properly
 Implement price accessor
 Add rating accessor
 Create filter scopes
 Implement Searchable
 Define fillable/casts
 Write model tests
File: app/Models/ProductVariant.php
Attribute	Details
Path	atelier-arome-api/app/Models/ProductVariant.php
Purpose	Size variants with pricing and inventory
Priority	Critical
Interfaces:

PHP

class ProductVariant extends Model
{
    use HasFactory, HasUuids;
    
    // Relationships
    public function product(): BelongsTo;
    public function inventory(): HasOne;
    public function cartItems(): HasMany;
    public function orderItems(): HasMany;
    
    // Accessors
    public function getFormattedPriceAttribute(): string;
    public function getIsOnSaleAttribute(): bool;
    public function getSavingsAttribute(): ?float;
    public function getStockQuantityAttribute(): int;
    public function getIsInStockAttribute(): bool;
    
    // Methods
    public function hasStock(int $quantity = 1): bool;
    public function reserveStock(int $quantity): bool;
    public function releaseStock(int $quantity): bool;
}
Checklist:

 Use HasUuids trait
 Define relationships
 Add price formatting
 Implement stock helpers
 Create sale detection
 Write model tests
File: app/Models/Category.php
Attribute	Details
Path	atelier-arome-api/app/Models/Category.php
Purpose	Product categories
Priority	High
Interfaces:

PHP

class Category extends Model
{
    use HasFactory, HasUuids;
    
    public function products(): HasMany;
    public function activeProducts(): HasMany;
    
    public function scopeActive(Builder $query): Builder;
    public function scopeOrdered(Builder $query): Builder;
    
    public function getProductCountAttribute(): int;
}
Checklist:

 Define product relationship
 Add active scope
 Add ordered scope
 Create product count accessor
 Generate slug on save
File: app/Models/Cart.php
Attribute	Details
Path	atelier-arome-api/app/Models/Cart.php
Purpose	Shopping cart with totals calculation
Priority	Critical
Interfaces:

PHP

class Cart extends Model
{
    use HasFactory, HasUuids;
    
    // Relationships
    public function user(): BelongsTo;
    public function items(): HasMany;
    public function coupon(): BelongsTo;
    
    // Methods
    public function addItem(ProductVariant $variant, int $quantity = 1): CartItem;
    public function updateItem(CartItem $item, int $quantity): CartItem;
    public function removeItem(CartItem $item): void;
    public function clear(): void;
    public function applyCoupon(Coupon $coupon): void;
    public function removeCoupon(): void;
    public function recalculateTotals(): void;
    
    // Accessors
    public function getItemCountAttribute(): int;
    public function getIsEmptyAttribute(): bool;
    public function getFormattedTotalAttribute(): string;
    
    // Scopes
    public function scopeForUser(Builder $query, User $user): Builder;
    public function scopeForSession(Builder $query, string $sessionId): Builder;
    public function scopeNotExpired(Builder $query): Builder;
}
Checklist:

 Define all relationships
 Implement add/update/remove methods
 Add coupon handling
 Create total calculation
 Add GST calculation
 Create session/user scopes
 Implement expiry check
 Write model tests
File: app/Models/CartItem.php
Attribute	Details
Path	atelier-arome-api/app/Models/CartItem.php
Purpose	Cart line items
Priority	Critical
Interfaces:

PHP

class CartItem extends Model
{
    use HasFactory, HasUuids;
    
    public function cart(): BelongsTo;
    public function variant(): BelongsTo;
    
    public function updateQuantity(int $quantity): void;
    public function getProductAttribute(): Product;
    public function getFormattedTotalAttribute(): string;
}
Checklist:

 Define relationships
 Add product accessor
 Implement quantity update
 Calculate total on change
File: app/Models/Order.php
Attribute	Details
Path	atelier-arome-api/app/Models/Order.php
Purpose	Completed orders with status tracking
Priority	Critical
Interfaces:

PHP

class Order extends Model
{
    use HasFactory, HasUuids;
    
    // Relationships
    public function user(): BelongsTo;
    public function items(): HasMany;
    public function payments(): HasMany;
    public function shippingAddress(): BelongsTo;
    public function billingAddress(): BelongsTo;
    public function coupon(): BelongsTo;
    
    // Status methods
    public function isPending(): bool;
    public function isProcessing(): bool;
    public function isShipped(): bool;
    public function isDelivered(): bool;
    public function isCancelled(): bool;
    public function isPaid(): bool;
    public function canBeCancelled(): bool;
    
    // Actions
    public function markAsProcessing(): void;
    public function markAsShipped(string $trackingNumber, ?string $trackingUrl): void;
    public function markAsDelivered(): void;
    public function cancel(): void;
    
    // Accessors
    public function getFormattedTotalAttribute(): string;
    public function getStatusLabelAttribute(): string;
    
    // Scopes
    public function scopeByStatus(Builder $query, string $status): Builder;
    public function scopeRecent(Builder $query): Builder;
    
    // Boot
    protected static function boot(): void; // Generate order number
}
Checklist:

 Define all relationships
 Implement status enum casting
 Add status helper methods
 Create status transition methods
 Generate order numbers
 Add scopes for filtering
 Write model tests
File: app/Models/OrderItem.php
Attribute	Details
Path	atelier-arome-api/app/Models/OrderItem.php
Purpose	Order line items with product snapshots
Priority	Critical
Interfaces:

PHP

class OrderItem extends Model
{
    use HasFactory, HasUuids;
    
    public function order(): BelongsTo;
    public function variant(): BelongsTo;
    
    public function getFormattedTotalAttribute(): string;
    
    public static function fromCartItem(CartItem $cartItem): self;
}
Checklist:

 Define relationships
 Snapshot product data
 Factory method from cart item
File: app/Models/Payment.php
Attribute	Details
Path	atelier-arome-api/app/Models/Payment.php
Purpose	Payment records with Stripe integration
Priority	Critical
Interfaces:

PHP

class Payment extends Model
{
    use HasFactory, HasUuids;
    
    public function order(): BelongsTo;
    
    public function isSuccessful(): bool;
    public function isFailed(): bool;
    public function isRefunded(): bool;
    
    public function markAsSucceeded(): void;
    public function markAsFailed(string $reason): void;
    public function markAsRefunded(): void;
}
Checklist:

 Define order relationship
 Add Stripe ID tracking
 Implement status methods
 Add status transitions
File: app/Models/Inventory.php
Attribute	Details
Path	atelier-arome-api/app/Models/Inventory.php
Purpose	Stock level management
Priority	High
Interfaces:

PHP

class Inventory extends Model
{
    use HasFactory, HasUuids;
    
    public function variant(): BelongsTo;
    public function movements(): HasMany;
    
    public function getAvailableQuantityAttribute(): int;
    public function isLowStock(): bool;
    public function isOutOfStock(): bool;
    
    public function reserve(int $quantity, ?Order $order = null): bool;
    public function release(int $quantity, ?Order $order = null): bool;
    public function deduct(int $quantity, Order $order): bool;
    public function add(int $quantity, string $reason = 'Restock'): bool;
}
Checklist:

 Define relationships
 Calculate available quantity
 Implement stock operations
 Log all movements
 Add low stock detection
File: app/Models/Coupon.php
Attribute	Details
Path	atelier-arome-api/app/Models/Coupon.php
Purpose	Discount codes with validation
Priority	Medium
Interfaces:

PHP

class Coupon extends Model
{
    use HasFactory, HasUuids;
    
    public function usages(): HasMany;
    
    public function isValid(): bool;
    public function isExpired(): bool;
    public function hasReachedLimit(): bool;
    public function meetsMinimumOrder(float $subtotal): bool;
    public function canBeUsedBy(User $user): bool;
    
    public function calculateDiscount(float $subtotal): float;
    public function incrementUsage(): void;
    
    public function scopeActive(Builder $query): Builder;
    public function scopeValid(Builder $query): Builder;
}
Checklist:

 Define relationships
 Implement validation logic
 Add discount calculation
 Create validity scopes
File: app/Models/Address.php
Attribute	Details
Path	atelier-arome-api/app/Models/Address.php
Purpose	User saved addresses
Priority	High
Interfaces:

PHP

class Address extends Model
{
    use HasFactory, HasUuids;
    
    public function user(): BelongsTo;
    
    public function getFullAddressAttribute(): string;
    public function setAsDefaultShipping(): void;
    public function setAsDefaultBilling(): void;
}
Checklist:

 Define user relationship
 Add full address accessor
 Implement default setters
File: app/Models/Review.php
Attribute	Details
Path	atelier-arome-api/app/Models/Review.php
Purpose	Product reviews with moderation
Priority	Medium
Interfaces:

PHP

class Review extends Model
{
    use HasFactory, HasUuids;
    
    public function product(): BelongsTo;
    public function user(): BelongsTo;
    public function order(): BelongsTo;
    
    public function approve(): void;
    public function reject(): void;
    
    public function scopeApproved(Builder $query): Builder;
    public function scopePending(Builder $query): Builder;
}
Checklist:

 Define relationships
 Add moderation methods
 Create approval scopes
File: app/Models/Testimonial.php
Attribute	Details
Path	atelier-arome-api/app/Models/Testimonial.php
Purpose	Curated patron testimonials
Priority	Medium
Interfaces:

PHP

class Testimonial extends Model
{
    use HasFactory, HasUuids;
    
    public function scopeActive(Builder $query): Builder;
    public function scopeIlluminated(Builder $query): Builder;
    public function scopeOrdered(Builder $query): Builder;
}
Checklist:

 Define scopes
 Add ordering logic
File: app/Models/Wishlist.php
Attribute	Details
Path	atelier-arome-api/app/Models/Wishlist.php
Purpose	User wishlist
Priority	Medium
Interfaces:

PHP

class Wishlist extends Model
{
    use HasFactory, HasUuids;
    
    public function user(): BelongsTo;
    public function items(): HasMany;
    public function products(): BelongsToMany;
    
    public function addProduct(Product $product): WishlistItem;
    public function removeProduct(Product $product): void;
    public function hasProduct(Product $product): bool;
}
Checklist:

 Define relationships
 Implement add/remove/check methods
File: app/Models/NewsletterSubscriber.php
Attribute	Details
Path	atelier-arome-api/app/Models/NewsletterSubscriber.php
Purpose	Email subscribers
Priority	Medium
Interfaces:

PHP

class NewsletterSubscriber extends Model
{
    use HasFactory, HasUuids;
    
    public function confirm(): void;
    public function unsubscribe(): void;
    public function isActive(): bool;
    
    public function scopeActive(Builder $query): Builder;
    public function scopeConfirmed(Builder $query): Builder;
}
Checklist:

 Implement confirmation flow
 Add unsubscribe method
 Create active scope
1.4 Enums
File: app/Enums/OrderStatus.php
Attribute	Details
Path	atelier-arome-api/app/Enums/OrderStatus.php
Purpose	Order status enum with labels
Priority	High
Interfaces:

PHP

enum OrderStatus: string
{
    case PENDING = 'pending';
    case PROCESSING = 'processing';
    case SHIPPED = 'shipped';
    case DELIVERED = 'delivered';
    case CANCELLED = 'cancelled';
    
    public function label(): string;
    public function color(): string;
    public function canTransitionTo(self $status): bool;
}
Checklist:

 Define all status cases
 Add label method
 Add color for UI
 Implement transition validation
File: app/Enums/PaymentStatus.php
Attribute	Details
Path	atelier-arome-api/app/Enums/PaymentStatus.php
Purpose	Payment status enum
Priority	High
Interfaces:

PHP

enum PaymentStatus: string
{
    case PENDING = 'pending';
    case PAID = 'paid';
    case FAILED = 'failed';
    case REFUNDED = 'refunded';
    
    public function label(): string;
    public function color(): string;
}
Checklist:

 Define all status cases
 Add helper methods
File: app/Enums/PaymentMethod.php
Attribute	Details
Path	atelier-arome-api/app/Enums/PaymentMethod.php
Purpose	Supported payment methods
Priority	High
Interfaces:

PHP

enum PaymentMethod: string
{
    case CARD = 'card';
    case PAYNOW = 'paynow';
    case GRABPAY = 'grabpay';
    
    public function label(): string;
    public function icon(): string;
}
Checklist:

 Define all methods
 Add display labels
File: app/Enums/ProductHumour.php
Attribute	Details
Path	atelier-arome-api/app/Enums/ProductHumour.php
Purpose	Alchemical humour types
Priority	High
Interfaces:

PHP

enum ProductHumour: string
{
    case CALMING = 'calming';
    case UPLIFTING = 'uplifting';
    case GROUNDING = 'grounding';
    case CLARIFYING = 'clarifying';
    
    public function label(): string;
    public function symbol(): string;
    public function color(): string;
}
Checklist:

 Define all humours
 Add symbol mapping
 Add color mapping
File: app/Enums/ProductRarity.php
Attribute	Details
Path	atelier-arome-api/app/Enums/ProductRarity.php
Purpose	Product rarity levels
Priority	High
Interfaces:

PHP

enum ProductRarity: string
{
    case COMMON = 'common';
    case RARE = 'rare';
    case LIMITED = 'limited';
    
    public function label(): string;
    public function color(): string;
}
Checklist:

 Define all rarities
 Add display helpers
File: app/Enums/ProductSeason.php
Attribute	Details
Path	atelier-arome-api/app/Enums/ProductSeason.php
Purpose	Seasonal product classifications
Priority	High
Interfaces:

PHP

enum ProductSeason: string
{
    case SPRING = 'spring';
    case SUMMER = 'summer';
    case AUTUMN = 'autumn';
    case WINTER = 'winter';
    
    public function label(): string;
    public function months(): array;
}
Checklist:

 Define all seasons
 Add label mapping
File: app/Enums/UserRole.php
Attribute	Details
Path	atelier-arome-api/app/Enums/UserRole.php
Purpose	User role definitions
Priority	High
Interfaces:

PHP

enum UserRole: string
{
    case CUSTOMER = 'customer';
    case ADMIN = 'admin';
    case SUPERADMIN = 'superadmin';
    
    public function label(): string;
    public function permissions(): array;
}
Checklist:

 Define all roles
 Add permission mapping
1.5 Database Seeders
File: database/seeders/DatabaseSeeder.php
Attribute	Details
Path	atelier-arome-api/database/seeders/DatabaseSeeder.php
Purpose	Master seeder orchestration
Priority	High
Interfaces:

PHP

class DatabaseSeeder extends Seeder
{
    public function run(): void
    {
        $this->call([
            SettingsSeeder::class,
            CategorySeeder::class,
            ProductSeeder::class,
            UserSeeder::class,
            TestimonialSeeder::class,
        ]);
    }
}
Checklist:

 Order seeders by dependency
 Add conditional for production
File: database/seeders/CategorySeeder.php
Attribute	Details
Path	atelier-arome-api/database/seeders/CategorySeeder.php
Purpose	Seed product categories
Priority	High
Features:

Singles (Individual essences)
Blends (Curated combinations)
Sets (Gift collections)
Gift (Gift-ready packaging)
Checklist:

 Create all four categories
 Add descriptions
 Set sort order
 Mark as active
File: database/seeders/ProductSeeder.php
Attribute	Details
Path	atelier-arome-api/database/seeders/ProductSeeder.php
Purpose	Seed sample essence products
Priority	High
Features:

12 sample essences from mockup
All humour types represented
Multiple rarity levels
All seasons covered
Three variants per product (5ml, 15ml, 30ml)
Inventory initialization
Checklist:

 Create 12 products
 Add variants for each
 Initialize inventory
 Add product images
 Create tags
 Attach tags to products
File: database/seeders/UserSeeder.php
Attribute	Details
Path	atelier-arome-api/database/seeders/UserSeeder.php
Purpose	Seed admin and test users
Priority	High
Checklist:

 Create superadmin user
 Create admin user
 Create test customer
 Set known passwords for dev
File: database/seeders/TestimonialSeeder.php
Attribute	Details
Path	atelier-arome-api/database/seeders/TestimonialSeeder.php
Purpose	Seed testimonials from mockup
Priority	Medium
Checklist:

 Create 7 testimonials
 Mark featured ones as illuminated
 Set sort order
 Add folio references
Phase 1 Summary Checklist
text

Phase 1: Backend Foundation
├── Project Configuration
│   ├── [ ] composer.json configured
│   ├── [ ] .env.example complete
│   ├── [ ] config/shop.php created
│   ├── [ ] config/cors.php configured
│   └── [ ] All configs verified
│
├── Database Migrations (21 migrations)
│   ├── [ ] Users table
│   ├── [ ] Categories table
│   ├── [ ] Products table
│   ├── [ ] Product variants table
│   ├── [ ] Product images table
│   ├── [ ] Tags + pivot table
│   ├── [ ] Addresses table
│   ├── [ ] Carts table
│   ├── [ ] Cart items table
│   ├── [ ] Orders table
│   ├── [ ] Order items table
│   ├── [ ] Payments table
│   ├── [ ] Coupons table
│   ├── [ ] Coupon usages table
│   ├── [ ] Inventories table
│   ├── [ ] Inventory movements table
│   ├── [ ] Reviews table
│   ├── [ ] Testimonials table
│   ├── [ ] Wishlists + items table
│   ├── [ ] Newsletter subscribers table
│   ├── [ ] Settings table
│   └── [ ] All migrations run successfully
│
├── Eloquent Models (18 models)
│   ├── [ ] User model complete
│   ├── [ ] Product model complete
│   ├── [ ] ProductVariant model complete
│   ├── [ ] Category model complete
│   ├── [ ] Cart model complete
│   ├── [ ] CartItem model complete
│   ├── [ ] Order model complete
│   ├── [ ] OrderItem model complete
│   ├── [ ] Payment model complete
│   ├── [ ] Inventory model complete
│   ├── [ ] Coupon model complete
│   ├── [ ] Address model complete
│   ├── [ ] Review model complete
│   ├── [ ] Testimonial model complete
│   ├── [ ] Wishlist model complete
│   ├── [ ] NewsletterSubscriber model complete
│   ├── [ ] All relationships tested
│   └── [ ] All models have factories
│
├── Enums (7 enums)
│   ├── [ ] OrderStatus enum
│   ├── [ ] PaymentStatus enum
│   ├── [ ] PaymentMethod enum
│   ├── [ ] ProductHumour enum
│   ├── [ ] ProductRarity enum
│   ├── [ ] ProductSeason enum
│   └── [ ] UserRole enum
│
├── Database Seeders
│   ├── [ ] DatabaseSeeder orchestrated
│   ├── [ ] CategorySeeder complete
│   ├── [ ] ProductSeeder complete
│   ├── [ ] UserSeeder complete
│   ├── [ ] TestimonialSeeder complete
│   └── [ ] All seeders run successfully
│
└── Verification
    ├── [ ] php artisan migrate runs
    ├── [ ] php artisan db:seed runs
    ├── [ ] All relationships work
    └── [ ] PHPStan passes
Phase 2: Frontend Foundation
Overview
Attribute	Value
Duration	5-7 days
Priority	Critical
Dependencies	Phase 1 (partial)
Deliverables	Next.js project, design system, layout components
Files to Create
2.1 Project Configuration
File: package.json
Attribute	Details
Path	atelier-arome-web/package.json
Purpose	Node.js dependencies and scripts
Priority	Critical
Features:

Next.js 15 with React 19
TypeScript configuration
Tailwind CSS 4.0
All UI dependencies
Key Dependencies:

JSON

{
  "dependencies": {
    "next": "^15.0.0",
    "react": "^19.0.0",
    "react-dom": "^19.0.0",
    "@radix-ui/react-dialog": "^1.0.0",
    "@radix-ui/react-dropdown-menu": "^2.0.0",
    "@radix-ui/react-select": "^2.0.0",
    "@radix-ui/react-toast": "^1.0.0",
    "@tanstack/react-query": "^5.0.0",
    "zustand": "^5.0.0",
    "framer-motion": "^11.0.0",
    "react-hook-form": "^7.0.0",
    "@hookform/resolvers": "^3.0.0",
    "zod": "^3.0.0",
    "lucide-react": "^0.300.0",
    "class-variance-authority": "^0.7.0",
    "clsx": "^2.0.0",
    "tailwind-merge": "^2.0.0",
    "next-auth": "^5.0.0-beta"
  }
}
Checklist:

 Define all dependencies
 Add dev dependencies
 Configure scripts
 Run npm install
 Verify all packages work
File: tailwind.config.ts
Attribute	Details
Path	atelier-arome-web/tailwind.config.ts
Purpose	Extended Tailwind theme for Atelier design system
Priority	Critical
Features:

Full color system from CSS mockup
Typography scale with fluid sizing
Custom spacing (golden ratio)
Custom animations
Component-specific variants
Checklist:

 Define ink color scale
 Define gold color scale
 Define parchment colors
 Add botanical accent colors
 Configure font families
 Add fluid typography scale
 Define custom spacing
 Add border radius tokens
 Configure box shadows
 Define z-index scale
 Add keyframe animations
 Configure animation utilities
 Add plugins (animate, typography)
 Verify all classes work
File: src/app/globals.css
Attribute	Details
Path	atelier-arome-web/src/app/globals.css
Purpose	Global styles, CSS variables, base styles
Priority	Critical
Features:

Tailwind directives
CSS custom properties for theming
Base element styles
Focus styles
Selection styles
Print styles
Checklist:

 Add Tailwind directives
 Define CSS variables
 Style base elements
 Add focus-visible styles
 Configure selection colors
 Add reduced motion support
 Include print styles
File: src/styles/fonts.ts
Attribute	Details
Path	atelier-arome-web/src/styles/fonts.ts
Purpose	Font declarations with next/font
Priority	High
Features:

Cormorant Garamond (display)
Crimson Pro (body)
Great Vibes (accent)
Optimized loading
Interfaces:

TypeScript

import { Cormorant_Garamond, Crimson_Pro } from 'next/font/google';
import localFont from 'next/font/local';

export const displayFont: NextFont;
export const bodyFont: NextFont;
export const accentFont: NextFont;

export const fontVariables: string;
Checklist:

 Configure Cormorant Garamond
 Configure Crimson Pro
 Configure Great Vibes
 Export CSS variables
 Test font loading
File: src/styles/animations.ts
Attribute	Details
Path	atelier-arome-web/src/styles/animations.ts
Purpose	Framer Motion animation variants
Priority	High
Features:

Page transitions
Element reveals
Stagger children
Scroll-triggered animations
Reduced motion alternatives
Interfaces:

TypeScript

export const fadeIn: Variants;
export const fadeInUp: Variants;
export const fadeInDown: Variants;
export const scaleIn: Variants;
export const slideInLeft: Variants;
export const slideInRight: Variants;
export const staggerContainer: Variants;
export const staggerItem: Variants;

export const springTransition: Transition;
export const smoothTransition: Transition;

export const useReducedMotion: () => boolean;
export const getAnimationProps: (variants: Variants) => AnimationProps;
Checklist:

 Define fade variants
 Define slide variants
 Define scale variants
 Create stagger variants
 Add spring transitions
 Implement reduced motion hook
 Create animation helper
2.2 Layout Components
File: src/app/layout.tsx
Attribute	Details
Path	atelier-arome-web/src/app/layout.tsx
Purpose	Root layout with providers and global structure
Priority	Critical
Features:

HTML/body configuration
Font application
All providers wrapped
Metadata configuration
Analytics integration
Interfaces:

TypeScript

interface RootLayoutProps {
  children: React.ReactNode;
}

export const metadata: Metadata;
export default function RootLayout({ children }: RootLayoutProps): JSX.Element;
Checklist:

 Configure HTML lang
 Apply font variables
 Wrap with providers
 Add skip link
 Configure metadata
 Add viewport settings
 Include favicon
File: src/providers/index.tsx
Attribute	Details
Path	atelier-arome-web/src/providers/index.tsx
Purpose	Compose all application providers
Priority	High
Features:

TanStack Query provider
Auth provider
Cart provider
Toast provider
Theme provider
Interfaces:

TypeScript

interface ProvidersProps {
  children: React.ReactNode;
}

export function Providers({ children }: ProvidersProps): JSX.Element;
Checklist:

 Create query client
 Wrap with QueryClientProvider
 Add SessionProvider
 Add CartProvider
 Add ToastProvider
 Test provider hierarchy
File: src/components/layout/header/header.tsx
Attribute	Details
Path	atelier-arome-web/src/components/layout/header/header.tsx
Purpose	Main site header with navigation
Priority	Critical
Features:

Atelier seal logo
Desktop navigation
Mobile menu toggle
Search button
Cart button with count
Scroll-based styling
Sticky positioning
Interfaces:

TypeScript

export interface HeaderProps {
  className?: string;
}

export function Header({ className }: HeaderProps): JSX.Element;
Checklist:

 Implement atelier seal
 Add navigation links
 Create cart button with count
 Add search trigger
 Implement mobile toggle
 Add scroll shadow effect
 Test sticky behavior
 Ensure accessibility
File: src/components/layout/header/atelier-seal.tsx
Attribute	Details
Path	atelier-arome-web/src/components/layout/header/atelier-seal.tsx
Purpose	Animated logo component
Priority	High
Features:

SVG seal with rotation animation
Text overlay
Responsive sizing
Link to home
Interfaces:

TypeScript

export interface AtelierSealProps {
  size?: 'sm' | 'md' | 'lg';
  animate?: boolean;
  className?: string;
}

export function AtelierSeal(props: AtelierSealProps): JSX.Element;
Checklist:

 Create SVG seal
 Add rotation animation
 Make responsive
 Add reduced motion support
File: src/components/layout/header/nav-link.tsx
Attribute	Details
Path	atelier-arome-web/src/components/layout/header/nav-link.tsx
Purpose	Navigation link with Roman numeral
Priority	High
Features:

Roman numeral label
Active state detection
Hover underline animation
Accessible
Interfaces:

TypeScript

export interface NavLinkProps {
  href: string;
  number: string;
  label: string;
  className?: string;
}

export function NavLink(props: NavLinkProps): JSX.Element;
Checklist:

 Display Roman numeral
 Detect active route
 Add hover animation
 Ensure accessibility
File: src/components/layout/header/mobile-nav.tsx
Attribute	Details
Path	atelier-arome-web/src/components/layout/header/mobile-nav.tsx
Purpose	Mobile navigation drawer
Priority	High
Features:

Full-screen overlay
Slide-in animation
Navigation links
Close on route change
Focus trap
Body scroll lock
Interfaces:

TypeScript

export interface MobileNavProps {
  isOpen: boolean;
  onClose: () => void;
}

export function MobileNav(props: MobileNavProps): JSX.Element;
Checklist:

 Implement slide animation
 Add all nav links
 Create close button
 Implement focus trap
 Lock body scroll
 Close on navigation
 Add escape key handler
File: src/components/layout/header/search-dialog.tsx
Attribute	Details
Path	atelier-arome-web/src/components/layout/header/search-dialog.tsx
Purpose	Search modal with autocomplete
Priority	Medium
Features:

Modal overlay
Search input
Recent searches
Search suggestions
Keyboard navigation
Interfaces:

TypeScript

export interface SearchDialogProps {
  isOpen: boolean;
  onClose: () => void;
}

export function SearchDialog(props: SearchDialogProps): JSX.Element;
Checklist:

 Create modal structure
 Add search input
 Implement suggestions
 Add keyboard nav
 Handle search submit
File: src/components/layout/footer/colophon.tsx
Attribute	Details
Path	atelier-arome-web/src/components/layout/footer/colophon.tsx
Purpose	Site footer with full navigation and information
Priority	High
Features:

Atelier information
Navigation columns
Contact information
Social links
Newsletter signup
Copyright and legal
Interfaces:

TypeScript

export function Colophon(): JSX.Element;
Checklist:

 Create grid layout
 Add atelier info
 Include navigation
 Add contact details
 Create social links
 Add copyright
 Include legal links
File: src/components/layout/atelier-banner.tsx
Attribute	Details
Path	atelier-arome-web/src/components/layout/atelier-banner.tsx
Purpose	Top announcement banner
Priority	Medium
Features:

Configurable message
Current batch info
Dismissible option
Persistent close state
Interfaces:

TypeScript

export interface AtelierBannerProps {
  message?: string;
  subMessage?: string;
  dismissible?: boolean;
}

export function AtelierBanner(props: AtelierBannerProps): JSX.Element;
Checklist:

 Create banner structure
 Add ornament icons
 Implement dismiss
 Persist dismiss state
File: src/components/layout/texture-overlay.tsx
Attribute	Details
Path	atelier-arome-web/src/components/layout/texture-overlay.tsx
Purpose	Parchment texture effect
Priority	Low
Features:

Fixed positioning
SVG noise pattern
Pointer-events disabled
Performance optimized
Checklist:

 Create texture pattern
 Position fixed
 Disable interactions
 Optimize rendering
File: src/components/layout/gold-leaf-accents.tsx
Attribute	Details
Path	atelier-arome-web/src/components/layout/gold-leaf-accents.tsx
Purpose	Floating gold leaf decorations
Priority	Low
Features:

Multiple positioned elements
Parallax scroll effect
Reduced motion support
Checklist:

 Create gold gradients
 Add parallax scroll
 Support reduced motion
File: src/components/layout/skip-link.tsx
Attribute	Details
Path	atelier-arome-web/src/components/layout/skip-link.tsx
Purpose	Accessibility skip navigation
Priority	High
Features:

Visually hidden until focused
Links to main content
Keyboard accessible
Checklist:

 Hidden by default
 Visible on focus
 Link to #main-content
2.3 Shadcn UI Components
File: src/components/ui/button.tsx
Attribute	Details
Path	atelier-arome-web/src/components/ui/button.tsx
Purpose	Base button with Atelier variants
Priority	Critical
Features:

Shadcn base with CVA
Atelier variants (primary, secondary, outline, ghost)
Size variants
Loading state
Icon support
Ornament support
Interfaces:

TypeScript

export interface ButtonProps extends React.ButtonHTMLAttributes<HTMLButtonElement> {
  variant?: 'primary' | 'secondary' | 'outline' | 'ghost' | 'link';
  size?: 'sm' | 'md' | 'lg';
  isLoading?: boolean;
  leftIcon?: React.ReactNode;
  rightIcon?: React.ReactNode;
  ornament?: string;
  asChild?: boolean;
}

export const Button: React.ForwardRefExoticComponent<ButtonProps>;
Checklist:

 Base from Shadcn
 Add Atelier variants
 Style with Tailwind
 Add loading state
 Support icons
 Add ornament option
 Test all variants
File: src/components/ui/card.tsx
Attribute	Details
Path	atelier-arome-web/src/components/ui/card.tsx
Purpose	Base card component
Priority	High
Features:

Card, CardHeader, CardContent, CardFooter
Hover effects
Border styling
Checklist:

 Create compound component
 Add Atelier styling
 Include hover effects
File: src/components/ui/input.tsx
Attribute	Details
Path	atelier-arome-web/src/components/ui/input.tsx
Purpose	Form input with ornament
Priority	High
Features:

Styled input
Focus ornament dot
Error state
Label integration
Checklist:

 Style input field
 Add focus ornament
 Include error styling
 Support labels
File: src/components/ui/select.tsx
Attribute	Details
Path	atelier-arome-web/src/components/ui/select.tsx
Purpose	Dropdown select using Radix
Priority	High
Features:

Radix Select primitive
Custom trigger styling
Atelier option styling
Checklist:

 Use Radix Select
 Style trigger
 Style options
 Add ornaments
File: src/components/ui/dialog.tsx
Attribute	Details
Path	atelier-arome-web/src/components/ui/dialog.tsx
Purpose	Modal dialog using Radix
Priority	High
Features:

Radix Dialog primitive
Overlay with backdrop
Close button
Animation
Checklist:

 Use Radix Dialog
 Style overlay
 Add animations
 Include close button
File: src/components/ui/sheet.tsx
Attribute	Details
Path	atelier-arome-web/src/components/ui/sheet.tsx
Purpose	Slide-out drawer (for Vial/Cart)
Priority	Critical
Features:

Radix Dialog as base
Slide from right
Header/content/footer structure
Close button
Checklist:

 Use Radix Dialog
 Add slide animation
 Structure components
 Style for cart use
File: src/components/ui/toast.tsx
Attribute	Details
Path	atelier-arome-web/src/components/ui/toast.tsx
Purpose	Toast notifications
Priority	High
Features:

Radix Toast primitive
Multiple variants (success, error, warning, info)
Wax seal icon
Auto-dismiss
Checklist:

 Use Radix Toast
 Add variants
 Style with seal
 Configure timing
File: src/components/ui/skeleton.tsx
Attribute	Details
Path	atelier-arome-web/src/components/ui/skeleton.tsx
Purpose	Loading skeleton
Priority	Medium
Features:

Parchment-colored skeleton
Pulse animation
Various shapes
Checklist:

 Create base skeleton
 Add pulse animation
 Style with theme colors
File: src/components/ui/separator.tsx
Attribute	Details
Path	
