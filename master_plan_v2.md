Atelier Arôme — Complete E-Commerce Platform Build
📋 Document Control
Property	Value
Version	1.0.0
Created	2024
Status	Approved for Execution
Architecture	Laravel 12 API + Next.js 15 Frontend
Total Phases	8
Estimated Duration	15 weeks
🎯 Executive Summary
This Master Execution Plan provides a complete, phase-by-phase blueprint for building the Atelier Arôme e-commerce platform. Each phase is designed to be:

Independent: Can be developed and tested in isolation
Incremental: Builds upon previous phases
Deployable: Produces working, testable functionality
Documented: Every file has clear specifications
The plan covers 200+ files across backend (Laravel) and frontend (Next.js), with detailed checklists ensuring nothing is missed.

🏛️ Architecture Recap
text

┌─────────────────────────────────────────────────────────────────────────────┐
│                           PRODUCTION ARCHITECTURE                            │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   ┌─────────────────┐         ┌─────────────────┐         ┌─────────────┐   │
│   │   Next.js 15    │  HTTPS  │   Laravel 12    │         │ PostgreSQL  │   │
│   │   (Vercel)      │◄───────►│   (Forge)       │◄───────►│   (Neon)    │   │
│   │                 │   API   │                 │         │             │   │
│   │  - React 19     │         │  - Sanctum Auth │         │  - Primary  │   │
│   │  - Tailwind 4   │         │  - Eloquent ORM │         │  - Replica  │   │
│   │  - Shadcn-UI    │         │  - Horizon Jobs │         │             │   │
│   │  - Zustand      │         │  - Filament     │         └─────────────┘   │
│   │  - TanStack Q   │         │                 │                           │
│   └─────────────────┘         └────────┬────────┘                           │
│                                        │                                    │
│                               ┌────────┴────────┐                           │
│                               │                 │                           │
│                       ┌───────▼──────┐  ┌───────▼──────┐                    │
│                       │    Redis     │  │  Meilisearch │                    │
│                       │   (Cache)    │  │   (Search)   │                    │
│                       └──────────────┘  └──────────────┘                    │
│                                                                             │
│   External Services:                                                        │
│   ├── Stripe (Payments)                                                     │
│   ├── Cloudinary (Media)                                                    │
│   ├── Resend (Email)                                                        │
│   └── SingPost API (Shipping)                                               │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
📐 Development Standards
Code Quality Standards
YAML

Backend (Laravel):
  PHP Version: 8.3+
  Style Guide: PSR-12
  Static Analysis: PHPStan Level 8
  Testing: PHPUnit + Pest
  Code Coverage: Minimum 80%

Frontend (Next.js):
  TypeScript: Strict mode enabled
  Linting: ESLint + Prettier
  Testing: Vitest + Testing Library
  Accessibility: WCAG 2.1 AA minimum
  Performance: Core Web Vitals pass
Git Workflow
text

main (production)
  └── develop (integration)
       ├── feature/phase-1-foundation
       ├── feature/phase-2-products
       ├── feature/phase-3-cart
       └── ...
Commit Convention
text

type(scope): description

Types: feat, fix, docs, style, refactor, test, chore
Scope: api, web, db, auth, cart, checkout, admin
🗺️ Phase Dependency Graph
mermaid

flowchart TD
    P1[Phase 1: Foundation] --> P2[Phase 2: Products]
    P1 --> P3[Phase 3: Cart & Auth]
    P2 --> P3
    P3 --> P4[Phase 4: Checkout]
    P4 --> P5[Phase 5: Orders]
    P3 --> P6[Phase 6: Account]
    P5 --> P6
    P6 --> P7[Phase 7: Admin]
    P5 --> P7
    P7 --> P8[Phase 8: Enhancement]
    P8 --> P9[Phase 9: Launch]
    
    style P1 fill:#e0f2fe
    style P2 fill:#dbeafe
    style P3 fill:#c7d2fe
    style P4 fill:#fef3c7
    style P5 fill:#fde68a
    style P6 fill:#d1fae5
    style P7 fill:#a7f3d0
    style P8 fill:#fce7f3
    style P9 fill:#f0abfc
📦 PHASE 1: Foundation & Infrastructure
Phase Overview
Property	Value
Duration	2 weeks
Priority	Critical Path
Dependencies	None
Deliverables	Project scaffolding, database schema, design system
Prerequisites
 Development environment configured (PHP 8.3, Node 20, PostgreSQL 16)
 Git repositories created (atelier-arome-api, atelier-arome-web)
 External service accounts created (Stripe, Cloudinary, Resend)
 Domain and DNS configured
1.1 Backend Foundation Files
1.1.1 Project Configuration Files
File: composer.json
text

Path: atelier-arome-api/composer.json
Type: Configuration
Description: Composer package manifest defining all PHP dependencies for the Laravel API.

Features:

Laravel 12 framework
Sanctum for API authentication
Stripe SDK for payments
Horizon for queue management
Filament for admin panel
Interfaces: N/A (Configuration file)

Checklist:

 Laravel 12.x requirement specified
 PHP 8.3 minimum version set
 All required packages listed with version constraints
 PSR-4 autoloading configured for App namespace
 Scripts defined (post-autoload-dump, post-install-cmd)
 Dev dependencies separated (phpunit, phpstan, pint)
File: .env.example
text

Path: atelier-arome-api/.env.example
Type: Configuration Template
Description: Environment variable template for local development and deployment reference.

Features:

Database connection settings
Redis configuration
Mail settings (Resend)
Stripe API keys
Cloudinary credentials
Application secrets
Interfaces: N/A (Template file)

Checklist:

 APP_NAME, APP_ENV, APP_KEY, APP_DEBUG, APP_URL defined
 DB_CONNECTION, DB_HOST, DB_PORT, DB_DATABASE, DB_USERNAME, DB_PASSWORD
 REDIS_HOST, REDIS_PASSWORD, REDIS_PORT
 MAIL_MAILER, MAIL_HOST, MAIL_PORT, MAIL_USERNAME, MAIL_PASSWORD
 STRIPE_KEY, STRIPE_SECRET, STRIPE_WEBHOOK_SECRET
 CLOUDINARY_URL, CLOUDINARY_CLOUD_NAME, CLOUDINARY_API_KEY, CLOUDINARY_API_SECRET
 MEILISEARCH_HOST, MEILISEARCH_KEY
 FRONTEND_URL for CORS
 GST_RATE=0.09 (Singapore specific)
 DEFAULT_CURRENCY=SGD
File: config/shop.php
text

Path: atelier-arome-api/config/shop.php
Type: Configuration
Description: Custom e-commerce configuration values specific to Atelier Arôme.

Features:

GST rate configuration
Currency settings
Cart limits
Order number format
Shipping defaults
Interfaces:

PHP

return [
    'gst_rate' => env('GST_RATE', 0.09),
    'currency' => env('DEFAULT_CURRENCY', 'SGD'),
    'max_cart_items' => 12,
    'abandoned_cart_hours' => 24,
    'order_number_prefix' => 'AA',
    'phial_sizes' => ['5ml', '15ml', '30ml'],
    'humours' => ['calming', 'uplifting', 'grounding', 'clarifying'],
    'rarities' => ['common', 'rare', 'limited'],
    'seasons' => ['spring', 'summer', 'autumn', 'winter'],
];
Checklist:

 GST rate configurable via environment
 Currency code (SGD) set
 Max cart items limit (12) defined
 Abandoned cart timeout configured
 Order number prefix set
 All enum values defined as arrays
 Default shipping zones configured
File: config/cors.php
text

Path: atelier-arome-api/config/cors.php
Type: Configuration
Description: Cross-Origin Resource Sharing configuration for Next.js frontend communication.

Features:

Allowed origins (frontend URL)
Allowed methods
Credential support for cookies
Header configuration
Interfaces:

PHP

return [
    'paths' => ['api/*', 'sanctum/csrf-cookie'],
    'allowed_methods' => ['*'],
    'allowed_origins' => [env('FRONTEND_URL', 'http://localhost:3000')],
    'allowed_origins_patterns' => [],
    'allowed_headers' => ['*'],
    'exposed_headers' => [],
    'max_age' => 0,
    'supports_credentials' => true,
];
Checklist:

 API paths included
 Sanctum CSRF cookie path included
 Frontend URL configurable via environment
 Credentials support enabled
 All HTTP methods allowed
 Proper headers exposed
File: config/sanctum.php
text

Path: atelier-arome-api/config/sanctum.php
Type: Configuration
Description: Laravel Sanctum configuration for SPA authentication.

Features:

Stateful domains configuration
Token expiration settings
Cookie configuration
Interfaces:

PHP

return [
    'stateful' => explode(',', env('SANCTUM_STATEFUL_DOMAINS', 
        'localhost,localhost:3000,127.0.0.1,127.0.0.1:8000')),
    'expiration' => null,
    'token_prefix' => env('SANCTUM_TOKEN_PREFIX', ''),
    'middleware' => [
        'authenticate_session' => Laravel\Sanctum\Http\Middleware\AuthenticateSession::class,
        'encrypt_cookies' => Illuminate\Cookie\Middleware\EncryptCookies::class,
        'validate_csrf_token' => Illuminate\Foundation\Http\Middleware\ValidateCsrfToken::class,
    ],
];
Checklist:

 Stateful domains include localhost and production frontend
 Token expiration set appropriately (null for session-based)
 Middleware stack configured correctly
 Guard set to 'sanctum'
1.1.2 Database Migrations
File: database/migrations/2024_01_01_000001_create_categories_table.php
text

Path: atelier-arome-api/database/migrations/2024_01_01_000001_create_categories_table.php
Type: Migration
Description: Creates the categories table for product organization.

Features:

UUID primary key
Name and slug (unique)
Description text
Image URL
Sort order
Active status
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
});
Checklist:

 UUID primary key used
 Slug column has unique index
 Description is nullable text
 Sort order has default value
 is_active boolean with default true
 Timestamps included
 Down method drops table
File: database/migrations/2024_01_01_000002_create_products_table.php
text

Path: atelier-arome-api/database/migrations/2024_01_01_000002_create_products_table.php
Type: Migration
Description: Creates the products table for essence/product storage.

Features:

UUID primary key
Foreign key to categories
Product metadata (name, slug, latin_name, description)
Enum fields (humour, rarity, season)
Featured and active flags
Soft deletes
Schema:

PHP

Schema::create('products', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('category_id')->nullable()->constrained()->nullOnDelete();
    $table->string('name');
    $table->string('slug')->unique();
    $table->string('latin_name')->nullable();
    $table->text('description');
    $table->text('long_description')->nullable();
    $table->enum('humour', ['calming', 'uplifting', 'grounding', 'clarifying']);
    $table->enum('rarity', ['common', 'rare', 'limited'])->default('common');
    $table->enum('season', ['spring', 'summer', 'autumn', 'winter']);
    $table->string('extraction_method')->nullable();
    $table->string('folio_number')->nullable();
    $table->boolean('is_featured')->default(false);
    $table->boolean('is_active')->default(true);
    $table->integer('sort_order')->default(0);
    $table->json('meta_data')->nullable();
    $table->timestamps();
    $table->softDeletes();
    
    $table->index(['humour', 'is_active']);
    $table->index(['rarity', 'is_active']);
    $table->index(['season', 'is_active']);
    $table->index(['is_featured', 'is_active']);
});
Checklist:

 UUID primary key used
 Category foreign key with null on delete
 Slug has unique index
 All enum fields have valid values
 Default values set for rarity, is_featured, is_active, sort_order
 Soft deletes enabled
 Composite indexes for common queries
 Meta data JSON column for extensibility
 Down method drops table
File: database/migrations/2024_01_01_000003_create_product_variants_table.php
text

Path: atelier-arome-api/database/migrations/2024_01_01_000003_create_product_variants_table.php
Type: Migration
Description: Creates product variants table for different phial sizes.

Features:

UUID primary key
Foreign key to products
Size name (5ml, 15ml, 30ml)
SKU (unique)
Pricing (price, compare_at_price)
Weight for shipping
Default and active flags
Schema:

PHP

Schema::create('product_variants', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('product_id')->constrained()->cascadeOnDelete();
    $table->string('name'); // "5ml", "15ml", "30ml"
    $table->string('sku')->unique();
    $table->decimal('price_sgd', 10, 2);
    $table->decimal('compare_at_price', 10, 2)->nullable();
    $table->integer('weight_grams')->default(50);
    $table->boolean('is_default')->default(false);
    $table->boolean('is_active')->default(true);
    $table->timestamps();
    
    $table->index(['product_id', 'is_active']);
});
Checklist:

 UUID primary key used
 Product foreign key with cascade delete
 SKU has unique index
 Price uses decimal(10,2) for accuracy
 Compare at price nullable for sale indication
 Weight in grams for shipping calculation
 is_default flag for default selection
 Composite index on product_id + is_active
 Down method drops table
File: database/migrations/2024_01_01_000004_create_product_images_table.php
text

Path: atelier-arome-api/database/migrations/2024_01_01_000004_create_product_images_table.php
Type: Migration
Description: Creates product images table for multiple product images.

Schema:

PHP

Schema::create('product_images', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('product_id')->constrained()->cascadeOnDelete();
    $table->string('url');
    $table->string('alt_text')->nullable();
    $table->integer('sort_order')->default(0);
    $table->boolean('is_primary')->default(false);
    $table->timestamps();
    
    $table->index(['product_id', 'is_primary']);
});
Checklist:

 UUID primary key
 Product foreign key with cascade delete
 URL column for Cloudinary URL
 Alt text for accessibility
 Sort order for gallery ordering
 is_primary flag for main image
 Index on product_id + is_primary
File: database/migrations/2024_01_01_000005_create_tags_table.php
text

Path: atelier-arome-api/database/migrations/2024_01_01_000005_create_tags_table.php
Type: Migration
Description: Creates tags table for scent notes tagging.

Schema:

PHP

Schema::create('tags', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->string('name')->unique();
    $table->string('slug')->unique();
    $table->timestamps();
});
Checklist:

 UUID primary key
 Name unique index
 Slug unique index
 Timestamps included
File: database/migrations/2024_01_01_000006_create_product_tag_table.php
text

Path: atelier-arome-api/database/migrations/2024_01_01_000006_create_product_tag_table.php
Type: Migration
Description: Creates pivot table for product-tag many-to-many relationship.

Schema:

PHP

Schema::create('product_tag', function (Blueprint $table) {
    $table->foreignUuid('product_id')->constrained()->cascadeOnDelete();
    $table->foreignUuid('tag_id')->constrained()->cascadeOnDelete();
    $table->primary(['product_id', 'tag_id']);
});
Checklist:

 Composite primary key
 Both foreign keys with cascade delete
 No timestamps (pivot table)
File: database/migrations/2024_01_01_000007_create_addresses_table.php
text

Path: atelier-arome-api/database/migrations/2024_01_01_000007_create_addresses_table.php
Type: Migration
Description: Creates addresses table for user shipping/billing addresses.

Schema:

PHP

Schema::create('addresses', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('user_id')->constrained()->cascadeOnDelete();
    $table->string('label')->default('Home'); // Home, Office, etc.
    $table->string('recipient_name');
    $table->string('phone');
    $table->string('line_1');
    $table->string('line_2')->nullable();
    $table->string('postal_code');
    $table->string('city')->default('Singapore');
    $table->string('country')->default('SG');
    $table->boolean('is_default_shipping')->default(false);
    $table->boolean('is_default_billing')->default(false);
    $table->timestamps();
    
    $table->index(['user_id', 'is_default_shipping']);
    $table->index(['user_id', 'is_default_billing']);
});
Checklist:

 UUID primary key
 User foreign key with cascade delete
 Label for address naming
 All Singapore address fields present
 Country defaults to SG
 City defaults to Singapore
 Default shipping/billing flags
 Indexes for default address lookups
File: database/migrations/2024_01_01_000008_create_carts_table.php
text

Path: atelier-arome-api/database/migrations/2024_01_01_000008_create_carts_table.php
Type: Migration
Description: Creates carts table for shopping cart persistence.

Schema:

PHP

Schema::create('carts', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('user_id')->nullable()->constrained()->cascadeOnDelete();
    $table->string('session_id')->nullable()->index(); // For guest carts
    $table->foreignUuid('coupon_id')->nullable()->constrained()->nullOnDelete();
    $table->decimal('subtotal', 10, 2)->default(0);
    $table->decimal('discount_amount', 10, 2)->default(0);
    $table->decimal('gst_amount', 10, 2)->default(0);
    $table->decimal('total', 10, 2)->default(0);
    $table->timestamp('expires_at')->nullable();
    $table->timestamps();
    
    $table->index(['session_id', 'expires_at']);
});
Checklist:

 UUID primary key
 User foreign key nullable (guest carts)
 Session ID for guest cart tracking
 Coupon foreign key nullable
 All monetary values as decimal(10,2)
 Expires at for cart cleanup
 Index for session ID + expiry
File: database/migrations/2024_01_01_000009_create_cart_items_table.php
text

Path: atelier-arome-api/database/migrations/2024_01_01_000009_create_cart_items_table.php
Type: Migration
Description: Creates cart items table for cart line items.

Schema:

PHP

Schema::create('cart_items', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('cart_id')->constrained()->cascadeOnDelete();
    $table->foreignUuid('variant_id')->constrained('product_variants')->cascadeOnDelete();
    $table->integer('quantity')->default(1);
    $table->decimal('unit_price', 10, 2);
    $table->decimal('total_price', 10, 2);
    $table->timestamps();
    
    $table->unique(['cart_id', 'variant_id']);
});
Checklist:

 UUID primary key
 Cart foreign key with cascade delete
 Variant foreign key with cascade delete
 Quantity with default 1
 Unit and total price as decimal
 Unique constraint on cart + variant
File: database/migrations/2024_01_01_000010_create_orders_table.php
text

Path: atelier-arome-api/database/migrations/2024_01_01_000010_create_orders_table.php
Type: Migration
Description: Creates orders table for completed orders.

Schema:

PHP

Schema::create('orders', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('user_id')->constrained()->cascadeOnDelete();
    $table->string('order_number')->unique(); // AA-YYYYMMDD-XXXX
    $table->enum('status', ['pending', 'processing', 'shipped', 'delivered', 'cancelled'])
          ->default('pending');
    $table->enum('payment_status', ['pending', 'paid', 'failed', 'refunded'])
          ->default('pending');
    $table->foreignUuid('shipping_address_id')->constrained('addresses');
    $table->foreignUuid('billing_address_id')->nullable()->constrained('addresses');
    $table->foreignUuid('coupon_id')->nullable()->constrained()->nullOnDelete();
    $table->decimal('subtotal', 10, 2);
    $table->decimal('discount_amount', 10, 2)->default(0);
    $table->decimal('shipping_amount', 10, 2)->default(0);
    $table->decimal('gst_amount', 10, 2);
    $table->decimal('total', 10, 2);
    $table->text('notes')->nullable(); // Customer notes
    $table->text('admin_notes')->nullable(); // Internal notes
    $table->string('tracking_number')->nullable();
    $table->string('tracking_url')->nullable();
    $table->timestamp('shipped_at')->nullable();
    $table->timestamp('delivered_at')->nullable();
    $table->timestamps();
    
    $table->index(['user_id', 'status']);
    $table->index(['status', 'created_at']);
    $table->index('order_number');
});
Checklist:

 UUID primary key
 User foreign key required
 Order number unique with index
 Status enum with valid states
 Payment status enum with valid states
 Shipping address required
 Billing address optional
 All monetary values as decimal
 Tracking fields nullable
 Timestamp fields for shipped/delivered
 Indexes for common queries
File: database/migrations/2024_01_01_000011_create_order_items_table.php
text

Path: atelier-arome-api/database/migrations/2024_01_01_000011_create_order_items_table.php
Type: Migration
Description: Creates order items table with snapshot data for order line items.

Schema:

PHP

Schema::create('order_items', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('order_id')->constrained()->cascadeOnDelete();
    $table->foreignUuid('variant_id')->constrained('product_variants')->nullOnDelete();
    $table->string('product_name'); // Snapshot
    $table->string('variant_name'); // Snapshot
    $table->string('sku'); // Snapshot
    $table->integer('quantity');
    $table->decimal('unit_price', 10, 2);
    $table->decimal('total_price', 10, 2);
    $table->timestamps();
});
Checklist:

 UUID primary key
 Order foreign key with cascade delete
 Variant foreign key with null on delete (preserve order if product deleted)
 Snapshot fields for product/variant name/SKU
 Quantity and prices stored
 Timestamps included
File: database/migrations/2024_01_01_000012_create_payments_table.php
text

Path: atelier-arome-api/database/migrations/2024_01_01_000012_create_payments_table.php
Type: Migration
Description: Creates payments table for payment records and Stripe integration.

Schema:

PHP

Schema::create('payments', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('order_id')->constrained()->cascadeOnDelete();
    $table->string('stripe_payment_intent_id')->unique()->nullable();
    $table->string('stripe_charge_id')->nullable();
    $table->enum('method', ['card', 'paynow', 'grabpay'])->default('card');
    $table->enum('status', ['pending', 'succeeded', 'failed', 'refunded'])
          ->default('pending');
    $table->decimal('amount', 10, 2);
    $table->string('currency', 3)->default('SGD');
    $table->json('metadata')->nullable();
    $table->string('failure_reason')->nullable();
    $table->timestamp('paid_at')->nullable();
    $table->timestamp('refunded_at')->nullable();
    $table->timestamps();
    
    $table->index(['order_id', 'status']);
    $table->index('stripe_payment_intent_id');
});
Checklist:

 UUID primary key
 Order foreign key with cascade delete
 Stripe IDs with unique constraint
 Payment method enum
 Status enum
 Amount as decimal
 Currency code field
 Metadata JSON for Stripe response
 Failure reason for debugging
 Payment and refund timestamps
File: database/migrations/2024_01_01_000013_create_coupons_table.php
text

Path: atelier-arome-api/database/migrations/2024_01_01_000013_create_coupons_table.php
Type: Migration
Description: Creates coupons table for discount codes.

Schema:

PHP

Schema::create('coupons', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->string('code')->unique();
    $table->text('description')->nullable();
    $table->enum('type', ['percentage', 'fixed_amount', 'free_shipping']);
    $table->decimal('value', 10, 2); // Percentage or fixed amount
    $table->decimal('minimum_order_amount', 10, 2)->default(0);
    $table->integer('usage_limit')->nullable(); // Null = unlimited
    $table->integer('usage_count')->default(0);
    $table->boolean('is_active')->default(true);
    $table->timestamp('starts_at')->nullable();
    $table->timestamp('expires_at')->nullable();
    $table->timestamps();
    
    $table->index(['code', 'is_active']);
    $table->index(['expires_at', 'is_active']);
});
Checklist:

 UUID primary key
 Code unique and indexed
 Type enum for discount type
 Value for percentage or amount
 Minimum order amount
 Usage limit and count tracking
 Active flag
 Date range for validity
 Indexes for validation queries
File: database/migrations/2024_01_01_000014_create_coupon_usages_table.php
text

Path: atelier-arome-api/database/migrations/2024_01_01_000014_create_coupon_usages_table.php
Type: Migration
Description: Creates coupon usages table for tracking redemptions.

Schema:

PHP

Schema::create('coupon_usages', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('coupon_id')->constrained()->cascadeOnDelete();
    $table->foreignUuid('user_id')->constrained()->cascadeOnDelete();
    $table->foreignUuid('order_id')->constrained()->cascadeOnDelete();
    $table->timestamp('used_at');
    
    $table->unique(['coupon_id', 'user_id', 'order_id']);
});
Checklist:

 UUID primary key
 All foreign keys with cascade delete
 Unique constraint to prevent duplicates
 Timestamp for usage tracking
File: database/migrations/2024_01_01_000015_create_reviews_table.php
text

Path: atelier-arome-api/database/migrations/2024_01_01_000015_create_reviews_table.php
Type: Migration
Description: Creates reviews table for product reviews.

Schema:

PHP

Schema::create('reviews', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('product_id')->constrained()->cascadeOnDelete();
    $table->foreignUuid('user_id')->constrained()->cascadeOnDelete();
    $table->foreignUuid('order_id')->nullable()->constrained()->nullOnDelete();
    $table->tinyInteger('rating')->unsigned(); // 1-5
    $table->string('title')->nullable();
    $table->text('body');
    $table->boolean('is_verified_purchase')->default(false);
    $table->boolean('is_approved')->default(false);
    $table->timestamps();
    
    $table->unique(['product_id', 'user_id']);
    $table->index(['product_id', 'is_approved']);
});
Checklist:

 UUID primary key
 Product and user foreign keys
 Optional order link for verified purchases
 Rating 1-5 as tinyInteger
 Title optional, body required
 Verified purchase flag
 Approval flag for moderation
 One review per user per product
File: database/migrations/2024_01_01_000016_create_testimonials_table.php
text

Path: atelier-arome-api/database/migrations/2024_01_01_000016_create_testimonials_table.php
Type: Migration
Description: Creates testimonials table for patron testimonials (curated).

Schema:

PHP

Schema::create('testimonials', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->string('author_name');
    $table->string('author_title');
    $table->text('quote');
    $table->boolean('is_verified')->default(false);
    $table->boolean('is_illuminated')->default(false); // Featured style
    $table->string('folio_reference')->nullable(); // "Folio VII, Entry 12"
    $table->integer('sort_order')->default(0);
    $table->boolean('is_active')->default(true);
    $table->timestamps();
    
    $table->index(['is_active', 'sort_order']);
});
Checklist:

 UUID primary key
 Author information fields
 Quote text
 Verified and illuminated flags
 Folio reference for manuscript styling
 Sort order and active flag
 Index for active testimonials query
File: database/migrations/2024_01_01_000017_create_wishlists_table.php
text

Path: atelier-arome-api/database/migrations/2024_01_01_000017_create_wishlists_table.php
Type: Migration
Description: Creates wishlists table for user wishlists.

Schema:

PHP

Schema::create('wishlists', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('user_id')->constrained()->cascadeOnDelete();
    $table->string('name')->default('Bookmarked Essences');
    $table->timestamps();
    
    $table->index('user_id');
});
Checklist:

 UUID primary key
 User foreign key with cascade delete
 Name with default value
 Timestamps included
File: database/migrations/2024_01_01_000018_create_wishlist_items_table.php
text

Path: atelier-arome-api/database/migrations/2024_01_01_000018_create_wishlist_items_table.php
Type: Migration
Description: Creates wishlist items table for wishlist products.

Schema:

PHP

Schema::create('wishlist_items', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('wishlist_id')->constrained()->cascadeOnDelete();
    $table->foreignUuid('product_id')->constrained()->cascadeOnDelete();
    $table->timestamp('added_at');
    
    $table->unique(['wishlist_id', 'product_id']);
});
Checklist:

 UUID primary key
 Both foreign keys with cascade delete
 Timestamp for when added
 Unique constraint on wishlist + product
File: database/migrations/2024_01_01_000019_create_newsletter_subscribers_table.php
text

Path: atelier-arome-api/database/migrations/2024_01_01_000019_create_newsletter_subscribers_table.php
Type: Migration
Description: Creates newsletter subscribers table.

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
    
    $table->index(['email', 'is_confirmed']);
});
Checklist:

 UUID primary key
 Email unique
 Name optional
 Confirmation flow fields
 Unsubscribe tracking
 Index for confirmation queries
File: database/migrations/2024_01_01_000020_create_inventories_table.php
text

Path: atelier-arome-api/database/migrations/2024_01_01_000020_create_inventories_table.php
Type: Migration
Description: Creates inventories table for stock tracking per variant.

Schema:

PHP

Schema::create('inventories', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('variant_id')->unique()->constrained('product_variants')->cascadeOnDelete();
    $table->integer('quantity')->default(0);
    $table->integer('reserved_quantity')->default(0); // During checkout
    $table->integer('low_stock_threshold')->default(10);
    $table->timestamp('last_restocked_at')->nullable();
    $table->timestamps();
});
Checklist:

 UUID primary key
 Variant foreign key unique (one inventory per variant)
 Quantity and reserved quantity
 Low stock threshold configurable
 Last restocked timestamp
File: database/migrations/2024_01_01_000021_create_inventory_movements_table.php
text

Path: atelier-arome-api/database/migrations/2024_01_01_000021_create_inventory_movements_table.php
Type: Migration
Description: Creates inventory movements table for audit trail.

Schema:

PHP

Schema::create('inventory_movements', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->foreignUuid('inventory_id')->constrained()->cascadeOnDelete();
    $table->foreignUuid('order_id')->nullable()->constrained()->nullOnDelete();
    $table->enum('type', ['addition', 'subtraction', 'reservation', 'release']);
    $table->integer('quantity');
    $table->string('reason')->nullable();
    $table->timestamps();
    
    $table->index(['inventory_id', 'created_at']);
});
Checklist:

 UUID primary key
 Inventory foreign key with cascade delete
 Optional order reference
 Movement type enum
 Quantity (positive value, type determines direction)
 Reason for audit
 Index for movement history queries
File: database/migrations/2024_01_01_000022_create_settings_table.php
text

Path: atelier-arome-api/database/migrations/2024_01_01_000022_create_settings_table.php
Type: Migration
Description: Creates settings table for site configuration.

Schema:

PHP

Schema::create('settings', function (Blueprint $table) {
    $table->uuid('id')->primary();
    $table->string('key')->unique();
    $table->text('value')->nullable();
    $table->string('type')->default('string'); // string, integer, boolean, json
    $table->timestamps();
});
Checklist:

 UUID primary key
 Key unique
 Value as text for flexibility
 Type for casting
 Timestamps included
1.1.3 Enum Classes
File: app/Enums/OrderStatus.php
text

Path: atelier-arome-api/app/Enums/OrderStatus.php
Type: Enum
Description: Order status enumeration with labels and colors.

Interface:

PHP

<?php

namespace App\Enums;

enum OrderStatus: string
{
    case Pending = 'pending';
    case Processing = 'processing';
    case Shipped = 'shipped';
    case Delivered = 'delivered';
    case Cancelled = 'cancelled';
    
    public function label(): string
    {
        return match($this) {
            self::Pending => 'Pending',
            self::Processing => 'Processing',
            self::Shipped => 'Shipped',
            self::Delivered => 'Delivered',
            self::Cancelled => 'Cancelled',
        };
    }
    
    public function color(): string
    {
        return match($this) {
            self::Pending => 'warning',
            self::Processing => 'info',
            self::Shipped => 'primary',
            self::Delivered => 'success',
            self::Cancelled => 'danger',
        };
    }
    
    public static function values(): array
    {
        return array_column(self::cases(), 'value');
    }
}
Checklist:

 String-backed enum
 All status values defined
 Label method for display
 Color method for UI
 Values static method for validation
File: app/Enums/PaymentStatus.php
text

Path: atelier-arome-api/app/Enums/PaymentStatus.php
Type: Enum
Description: Payment status enumeration.

Interface:

PHP

<?php

namespace App\Enums;

enum PaymentStatus: string
{
    case Pending = 'pending';
    case Paid = 'paid';
    case Failed = 'failed';
    case Refunded = 'refunded';
    
    public function label(): string;
    public function color(): string;
    public static function values(): array;
}
Checklist:

 String-backed enum
 All payment states defined
 Label and color methods
 Values static method
File: app/Enums/PaymentMethod.php
text

Path: atelier-arome-api/app/Enums/PaymentMethod.php
Type: Enum
Description: Payment method enumeration for Singapore payment options.

Interface:

PHP

<?php

namespace App\Enums;

enum PaymentMethod: string
{
    case Card = 'card';
    case PayNow = 'paynow';
    case GrabPay = 'grabpay';
    
    public function label(): string;
    public function icon(): string; // For frontend display
    public static function values(): array;
}
Checklist:

 String-backed enum
 All Singapore payment methods
 Label and icon methods
 Values static method
File: app/Enums/ProductHumour.php
text

Path: atelier-arome-api/app/Enums/ProductHumour.php
Type: Enum
Description: Product humour enumeration with symbols.

Interface:

PHP

<?php

namespace App\Enums;

enum ProductHumour: string
{
    case Calming = 'calming';
    case Uplifting = 'uplifting';
    case Grounding = 'grounding';
    case Clarifying = 'clarifying';
    
    public function label(): string;
    public function symbol(): string
    {
        return match($this) {
            self::Calming => '☾',
            self::Uplifting => '☀',
            self::Grounding => '♁',
            self::Clarifying => '☁',
        };
    }
    public function color(): string;
    public static function values(): array;
}
Checklist:

 String-backed enum
 All humours defined
 Symbol method matching mockup
 Label and color methods
 Values static method
File: app/Enums/ProductRarity.php
text

Path: atelier-arome-api/app/Enums/ProductRarity.php
Type: Enum
Description: Product rarity enumeration.

Interface:

PHP

<?php

namespace App\Enums;

enum ProductRarity: string
{
    case Common = 'common';
    case Rare = 'rare';
    case Limited = 'limited';
    
    public function label(): string;
    public function color(): string;
    public static function values(): array;
}
Checklist:

 String-backed enum
 All rarities defined
 Label and color methods
File: app/Enums/ProductSeason.php
text

Path: atelier-arome-api/app/Enums/ProductSeason.php
Type: Enum
Description: Product season enumeration.

Interface:

PHP

<?php

namespace App\Enums;

enum ProductSeason: string
{
    case Spring = 'spring';
    case Summer = 'summer';
    case Autumn = 'autumn';
    case Winter = 'winter';
    
    public function label(): string
    {
        return match($this) {
            self::Spring => 'Early Spring',
            self::Summer => 'High Summer',
            self::Autumn => 'Autumn',
            self::Winter => 'Winter',
        };
    }
    public static function values(): array;
}
Checklist:

 String-backed enum
 All seasons defined
 Label method with display names
File: app/Enums/UserRole.php
text

Path: atelier-arome-api/app/Enums/UserRole.php
Type: Enum
Description: User role enumeration.

Interface:

PHP

<?php

namespace App\Enums;

enum UserRole: string
{
    case Customer = 'customer';
    case Admin = 'admin';
    case SuperAdmin = 'superadmin';
    
    public function label(): string;
    public function permissions(): array;
    public static function values(): array;
}
Checklist:

 String-backed enum
 All roles defined
 Permissions method for authorization
 Label and values methods
1.1.4 Base Model Configuration
File: app/Models/Concerns/HasUuid.php
text

Path: atelier-arome-api/app/Models/Concerns/HasUuid.php
Type: Trait
Description: Trait for UUID primary key handling.

Interface:

PHP

<?php

namespace App\Models\Concerns;

use Illuminate\Support\Str;

trait HasUuid
{
    public static function bootHasUuid(): void
    {
        static::creating(function ($model) {
            if (empty($model->{$model->getKeyName()})) {
                $model->{$model->getKeyName()} = (string) Str::uuid();
            }
        });
    }
    
    public function getIncrementing(): bool
    {
        return false;
    }
    
    public function getKeyType(): string
    {
        return 'string';
    }
}
Checklist:

 Boot method generates UUID on creating
 Incrementing disabled
 Key type set to string
 Works with existing UUID values
1.1.5 Seeders
File: database/seeders/CategorySeeder.php
text

Path: atelier-arome-api/database/seeders/CategorySeeder.php
Type: Seeder
Description: Seeds initial product categories.

Data:

PHP

$categories = [
    ['name' => 'Single Essences', 'slug' => 'singles', 'description' => 'Pure, undiluted botanical essences'],
    ['name' => 'Blended Essences', 'slug' => 'blends', 'description' => 'Artfully combined aromatic compositions'],
    ['name' => 'Gift Sets', 'slug' => 'sets', 'description' => 'Curated collections for gifting'],
    ['name' => 'Diffuser Collections', 'slug' => 'diffusers', 'description' => 'Aromatic diffuser blends'],
];
Checklist:

 All categories defined
 Slugs are URL-safe
 Descriptions provided
 Active by default
 Uses factory or direct insert
File: database/seeders/ProductSeeder.php
text

Path: atelier-arome-api/database/seeders/ProductSeeder.php
Type: Seeder
Description: Seeds sample products matching the mockup.

Data:

PHP

$products = [
    [
        'name' => 'Provence Lavender',
        'latin_name' => 'Lavandula × intermedia',
        'slug' => 'provence-lavender',
        'humour' => 'calming',
        'rarity' => 'rare',
        'season' => 'summer',
        'folio_number' => 'I',
        'is_featured' => true,
        'description' => 'Harvested at dawn in the Provençal hills...',
        'extraction_method' => 'Steam Distillation',
        'variants' => [
            ['name' => '5ml', 'sku' => 'LAV-724-5ML', 'price_sgd' => 42.00, 'is_default' => true],
            ['name' => '15ml', 'sku' => 'LAV-724-15ML', 'price_sgd' => 98.00],
            ['name' => '30ml', 'sku' => 'LAV-724-30ML', 'price_sgd' => 178.00],
        ],
        'tags' => ['Floral', 'Herbaceous', 'Sweet'],
    ],
    // ... more products
];
Checklist:

 At least 6 sample products
 All humours represented
 All rarities represented
 Variants created for each
 Tags associated
 Inventory initialized
File: database/seeders/TestimonialSeeder.php
text

Path: atelier-arome-api/database/seeders/TestimonialSeeder.php
Type: Seeder
Description: Seeds testimonials matching the mockup.

Checklist:

 3+ testimonials from mockup
 One marked as illuminated
 Verified flags set
 Folio references included
1.2 Frontend Foundation Files
1.2.1 Project Configuration
File: package.json
text

Path: atelier-arome-web/package.json
Type: Configuration
Description: NPM package manifest for Next.js frontend.

Dependencies:

JSON

{
  "dependencies": {
    "next": "^15.0.0",
    "react": "^19.0.0",
    "react-dom": "^19.0.0",
    "@tanstack/react-query": "^5.0.0",
    "zustand": "^5.0.0",
    "react-hook-form": "^7.0.0",
    "@hookform/resolvers": "^3.0.0",
    "zod": "^3.0.0",
    "framer-motion": "^11.0.0",
    "lucide-react": "^0.400.0",
    "clsx": "^2.0.0",
    "tailwind-merge": "^2.0.0",
    "class-variance-authority": "^0.7.0",
    "@radix-ui/react-dialog": "^1.0.0",
    "@radix-ui/react-dropdown-menu": "^2.0.0",
    "@radix-ui/react-select": "^2.0.0",
    "@radix-ui/react-toast": "^1.0.0",
    "@radix-ui/react-tooltip": "^1.0.0",
    "@radix-ui/react-slot": "^1.0.0"
  },
  "devDependencies": {
    "typescript": "^5.0.0",
    "@types/react": "^18.0.0",
    "@types/node": "^20.0.0",
    "tailwindcss": "^4.0.0",
    "postcss": "^8.0.0",
    "autoprefixer": "^10.0.0",
    "eslint": "^8.0.0",
    "eslint-config-next": "^15.0.0",
    "prettier": "^3.0.0",
    "@tailwindcss/typography": "^0.5.0",
    "tailwindcss-animate": "^1.0.0"
  }
}
Checklist:

 Next.js 15 specified
 React 19 specified
 All Shadcn dependencies included
 Tailwind 4.0 specified
 TypeScript configuration
 ESLint and Prettier
 Scripts defined (dev, build, start, lint)
File: tailwind.config.ts
text

Path: atelier-arome-web/tailwind.config.ts
Type: Configuration
Description: Tailwind CSS configuration with Atelier Arôme design system.

Features:

Custom color palette (ink, gold, parchment, botanicals)
Typography scale (fluid sizing)
Font families (Cormorant, Crimson, Great Vibes)
Spacing scale (golden ratio inspired)
Custom animations
Shadcn-UI integration
Checklist:

 All colors from CSS extracted
 All font families defined
 Fluid typography scale implemented
 Custom spacing values
 Animations keyframes defined
 Dark mode disabled (light theme only)
 Tailwindcss-animate plugin
 Typography plugin
 Content paths configured
File: tsconfig.json
text

Path: atelier-arome-web/tsconfig.json
Type: Configuration
Description: TypeScript compiler configuration.

Checklist:

 Strict mode enabled
 Path aliases configured (@/)
 Module resolution set to bundler
 JSX setting for React
 Incremental compilation enabled
File: next.config.ts
text

Path: atelier-arome-web/next.config.ts
Type: Configuration
Description: Next.js framework configuration.

Interface:

TypeScript

import type { NextConfig } from 'next'

const nextConfig: NextConfig = {
  experimental: {
    typedRoutes: true,
  },
  images: {
    remotePatterns: [
      {
        protocol: 'https',
        hostname: 'res.cloudinary.com',
      },
    ],
  },
  async rewrites() {
    return [
      {
        source: '/api/v1/:path*',
        destination: `${process.env.API_URL}/api/v1/:path*`,
      },
    ]
  },
}

export default nextConfig
Checklist:

 Typed routes enabled
 Cloudinary image domain configured
 API proxy rewrites configured
 Environment variables referenced
File: components.json
text

Path: atelier-arome-web/components.json
Type: Configuration
Description: Shadcn-UI configuration file.

Checklist:

 Style set to "default"
 RSC enabled
 TSX enabled
 Tailwind config path correct
 Aliases configured
1.2.2 Core Application Files
File: src/app/layout.tsx
text

Path: atelier-arome-web/src/app/layout.tsx
Type: Layout Component
Description: Root layout component wrapping all pages.

Features:

HTML document structure
Font loading (Cormorant, Crimson, Great Vibes)
Global providers (Query, Auth, Toast)
Metadata configuration
Analytics script
Interface:

TypeScript

export default function RootLayout({
  children,
}: {
  children: React.ReactNode
}): React.JSX.Element
Checklist:

 HTML lang="en" set
 Font preloading configured
 All providers wrapped
 Metadata exported
 Skip link included
 A11y announcer region included
 Body class configured
File: src/app/globals.css
text

Path: atelier-arome-web/src/app/globals.css
Type: Stylesheet
Description: Global CSS including Tailwind directives and base styles.

Features:

Tailwind base, components, utilities
CSS custom properties (from mockup)
Base element styles
Accessibility utilities
Print styles
Checklist:

 @tailwind directives included
 CSS variables layer defined
 Base styles layer defined
 Components layer for custom classes
 Utilities layer for overrides
 Focus styles defined
 Selection styles defined
 Reduced motion query respected
 Print styles included
File: src/styles/fonts.ts
text

Path: atelier-arome-web/src/styles/fonts.ts
Type: Module
Description: Font configuration using next/font/local.

Interface:

TypeScript

import localFont from 'next/font/local'

export const cormorantGaramond = localFont({
  src: [
    { path: '../../public/fonts/cormorant-garamond/CormorantGaramond-Light.woff2', weight: '300' },
    { path: '../../public/fonts/cormorant-garamond/CormorantGaramond-Regular.woff2', weight: '400' },
    { path: '../../public/fonts/cormorant-garamond/CormorantGaramond-Medium.woff2', weight: '500' },
    { path: '../../public/fonts/cormorant-garamond/CormorantGaramond-SemiBold.woff2', weight: '600' },
    { path: '../../public/fonts/cormorant-garamond/CormorantGaramond-Bold.woff2', weight: '700' },
  ],
  variable: '--font-display',
  display: 'swap',
})

export const crimsonPro = localFont({ /* ... */ })
export const greatVibes = localFont({ /* ... */ })
Checklist:

 All font weights loaded
 CSS variables assigned
 Display swap for performance
 Local font files referenced
 Fallback fonts configured
File: src/styles/animations.ts
text

Path: atelier-arome-web/src/styles/animations.ts
Type: Module
Description: Framer Motion animation variants.

Interface:

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

export const liquidWave: Variants = { /* vessel animation */ }
export const floatBotanical: Variants = { /* botanical animation */ }
export const rotateSeal: Variants = { /* seal animation */ }
Checklist:

 All animation variants from CSS converted
 Reduced motion variants included
 Stagger variants for lists
 Entry animations defined
 Exit animations defined
 Hover variants defined
1.2.3 Utility Files
File: src/lib/utils/cn.ts
text

Path: atelier-arome-web/src/lib/utils/cn.ts
Type: Utility
Description: Class name merging utility (clsx + tailwind-merge).

Interface:

TypeScript

import { clsx, type ClassValue } from 'clsx'
import { twMerge } from 'tailwind-merge'

export function cn(...inputs: ClassValue[]): string {
  return twMerge(clsx(inputs))
}
Checklist:

 Combines clsx and tailwind-merge
 Proper TypeScript types
 Default export or named export
File: src/lib/utils/format-currency.ts
text

Path: atelier-arome-web/src/lib/utils/format-currency.ts
Type: Utility
Description: Currency formatting utility for SGD.

Interface:

TypeScript

export function formatCurrency(
  amount: number,
  currency: string = 'SGD',
  locale: string = 'en-SG'
): string {
  return new Intl.NumberFormat(locale, {
    style: 'currency',
    currency,
    minimumFractionDigits: 0,
    maximumFractionDigits: 2,
  }).format(amount)
}
Checklist:

 SGD as default currency
 Singapore locale
 Proper decimal handling
 Zero decimals for whole numbers
File: src/lib/utils/calculate-gst.ts
text

Path: atelier-arome-web/src/lib/utils/calculate-gst.ts
Type: Utility
Description: GST calculation utility for Singapore 9% tax.

Interface:

TypeScript

const GST_RATE = 0.09

export function calculateGST(subtotal: number): number {
  return Math.round(subtotal * GST_RATE * 100) / 100
}

export function calculateTotalWithGST(subtotal: number): number {
  return subtotal + calculateGST(subtotal)
}

export function extractGSTFromTotal(total: number): {
  subtotal: number
  gst: number
} {
  const subtotal = total / (1 + GST_RATE)
  const gst = total - subtotal
  return {
    subtotal: Math.round(subtotal * 100) / 100,
    gst: Math.round(gst * 100) / 100,
  }
}
Checklist:

 9% GST rate correct
 Rounding to 2 decimal places
 Forward calculation (add GST)
 Reverse calculation (extract GST)
 Export all functions
File: src/lib/constants/alchemical-data.ts
text

Path: atelier-arome-web/src/lib/constants/alchemical-data.ts
Type: Constants
Description: Constant data for humours, seasons, rarities matching mockup.

Interface:

TypeScript

export const HUMOURS = {
  calming: { symbol: '☾', label: 'Calming', color: 'var(--color-lavender)' },
  uplifting: { symbol: '☀', label: 'Uplifting', color: 'var(--color-bergamot)' },
  grounding: { symbol: '♁', label: 'Grounding', color: 'var(--color-sage)' },
  clarifying: { symbol: '☁', label: 'Clarifying', color: 'var(--color-eucalyptus)' },
} as const

export const SEASONS = {
  spring: 'Early Spring',
  summer: 'High Summer',
  autumn: 'Autumn',
  winter: 'Winter',
} as const

export const RARITIES = {
  common: { label: 'Common', color: 'var(--color-ink-muted)' },
  rare: { label: 'Rare', color: 'var(--color-gold)' },
  limited: { label: 'Limited', color: 'var(--color-rose)' },
} as const

export type Humour = keyof typeof HUMOURS
export type Season = keyof typeof SEASONS
export type Rarity = keyof typeof RARITIES
Checklist:

 All humours with symbols
 All seasons with labels
 All rarities with colors
 TypeScript types exported
 Matches mockup exactly
File: src/lib/constants/site-config.ts
text

Path: atelier-arome-web/src/lib/constants/site-config.ts
Type: Constants
Description: Site-wide configuration constants.

Interface:

TypeScript

export const siteConfig = {
  name: 'Atelier Arôme',
  tagline: 'Artisanal Alchemy for the Senses',
  description: 'Aromatherapy elevated to artisanal alchemy. Handcrafted botanical essences from our atelier.',
  url: process.env.NEXT_PUBLIC_SITE_URL || 'https://atelierarome.sg',
  ogImage: '/images/og-image.jpg',
  links: {
    instagram: 'https://instagram.com/atelierarome',
    pinterest: 'https://pinterest.com/atelierarome',
  },
  contact: {
    email: 'correspondence@atelierarome.com',
    address: {
      line1: 'Rue des Alchimistes, 7',
      line2: 'Provence-Alpes-Côte d\'Azur',
      country: 'France',
    },
  },
  currency: 'SGD',
  gstRate: 0.09,
  maxCartItems: 12,
} as const
Checklist:

 Site name and tagline
 Meta description
 URL configuration
 Social links
 Contact information
 E-commerce settings
1.2.4 Provider Components
File: src/providers/query-provider.tsx
text

Path: atelier-arome-web/src/providers/query-provider.tsx
Type: Provider Component
Description: TanStack Query provider with default configuration.

Interface:

TypeScript

'use client'

import { QueryClient, QueryClientProvider } from '@tanstack/react-query'
import { ReactQueryDevtools } from '@tanstack/react-query-devtools'
import { useState } from 'react'

export function QueryProvider({ children }: { children: React.ReactNode }) {
  const [queryClient] = useState(
    () =>
      new QueryClient({
        defaultOptions: {
          queries: {
            staleTime: 60 * 1000, // 1 minute
            refetchOnWindowFocus: false,
          },
        },
      })
  )

  return (
    <QueryClientProvider client={queryClient}>
      {children}
      <ReactQueryDevtools initialIsOpen={false} />
    </QueryClientProvider>
  )
}
Checklist:

 'use client' directive
 QueryClient created in useState
 Default stale time configured
 DevTools included (dev only)
 Children properly rendered
File: src/providers/toast-provider.tsx
text

Path: atelier-arome-web/src/providers/toast-provider.tsx
Type: Provider Component
Description: Toast notification provider using Shadcn Toast.

Checklist:

 'use client' directive
 Toaster component rendered
 Toast viewport positioned
 Custom styling applied
1.2.5 Type Definitions
File: src/types/product.ts
text

Path: atelier-arome-web/src/types/product.ts
Type: TypeScript Types
Description: Product-related TypeScript interfaces.

Interface:

TypeScript

import { Humour, Season, Rarity } from '@/lib/constants/alchemical-data'

export interface ProductVariant {
  id: string
  name: string // "5ml", "15ml", "30ml"
  sku: string
  priceSgd: number
  compareAtPrice: number | null
  weightGrams: number
  isDefault: boolean
  isActive: boolean
}

export interface ProductImage {
  id: string
  url: string
  altText: string | null
  sortOrder: number
  isPrimary: boolean
}

export interface Product {
  id: string
  categoryId: string | null
  name: string
  slug: string
  latinName: string | null
  description: string
  longDescription: string | null
  humour: Humour
  rarity: Rarity
  season: Season
  extractionMethod: string | null
  folioNumber: string | null
  isFeatured: boolean
  isActive: boolean
  sortOrder: number
  variants: ProductVariant[]
  images: ProductImage[]
  tags: string[]
  category?: Category
  createdAt: string
  updatedAt: string
}

export interface ProductListItem extends Omit<Product, 'longDescription' | 'variants'> {
  defaultVariant: ProductVariant
  minPrice: number
  maxPrice: number
}

export interface Category {
  id: string
  name: string
  slug: string
  description: string | null
  imageUrl: string | null
  sortOrder: number
  isActive: boolean
}

export interface ProductFilters {
  humour?: Humour | 'all'
  rarity?: Rarity | 'all'
  season?: Season | 'all'
  category?: string
  search?: string
  sort?: 'folio' | 'humour' | 'rarity' | 'season' | 'price-asc' | 'price-desc'
}
Checklist:

 Product interface complete
 ProductVariant interface
 ProductImage interface
 Category interface
 ProductListItem for listings (optimized)
 ProductFilters for filtering
 All fields match API response
 Proper TypeScript types (no any)
File: src/types/cart.ts
text

Path: atelier-arome-web/src/types/cart.ts
Type: TypeScript Types
Description: Cart-related TypeScript interfaces.

Interface:

TypeScript

export interface CartItem {
  id: string
  variantId: string
  quantity: number
  unitPrice: number
  totalPrice: number
  product: {
    id: string
    name: string
    slug: string
    latinName: string | null
    humour: Humour
    image: string | null
  }
  variant: {
    id: string
    name: string
    sku: string
  }
}

export interface Cart {
  id: string
  userId: string | null
  sessionId: string | null
  couponId: string | null
  coupon: Coupon | null
  items: CartItem[]
  subtotal: number
  discountAmount: number
  gstAmount: number
  total: number
  itemCount: number
  expiresAt: string | null
}

export interface Coupon {
  id: string
  code: string
  type: 'percentage' | 'fixed_amount' | 'free_shipping'
  value: number
  minimumOrderAmount: number
}

export interface AddToCartPayload {
  variantId: string
  quantity: number
}

export interface UpdateCartItemPayload {
  quantity: number
}
Checklist:

 CartItem with nested product/variant info
 Cart with all totals
 Coupon interface
 Request payload types
 Item count computed
File: src/types/order.ts
text

Path: atelier-arome-web/src/types/order.ts
Type: TypeScript Types
Description: Order-related TypeScript interfaces.

Interface:

TypeScript

export type OrderStatus = 'pending' | 'processing' | 'shipped' | 'delivered' | 'cancelled'
export type PaymentStatus = 'pending' | 'paid' | 'failed' | 'refunded'

export interface OrderItem {
  id: string
  productName: string
  variantName: string
  sku: string
  quantity: number
  unitPrice: number
  totalPrice: number
}

export interface Order {
  id: string
  orderNumber: string
  status: OrderStatus
  paymentStatus: PaymentStatus
  shippingAddress: Address
  billingAddress: Address | null
  items: OrderItem[]
  subtotal: number
  discountAmount: number
  shippingAmount: number
  gstAmount: number
  total: number
  notes: string | null
  trackingNumber: string | null
  trackingUrl: string | null
  shippedAt: string | null
  deliveredAt: string | null
  createdAt: string
  updatedAt: string
}

export interface OrderListItem {
  id: string
  orderNumber: string
  status: OrderStatus
  paymentStatus: PaymentStatus
  total: number
  itemCount: number
  createdAt: string
}
Checklist:

 OrderStatus type
 PaymentStatus type
 Order interface complete
 OrderItem interface
 OrderListItem for history (optimized)
 Address reference
File: src/types/user.ts
text

Path: atelier-arome-web/src/types/user.ts
Type: TypeScript Types
Description: User-related TypeScript interfaces.

Interface:

TypeScript

export type UserRole = 'customer' | 'admin' | 'superadmin'

export interface User {
  id: string
  name: string
  email: string
  phone: string | null
  role: UserRole
  emailVerifiedAt: string | null
  createdAt: string
  updatedAt: string
}

export interface Address {
  id: string
  userId: string
  label: string
  recipientName: string
  phone: string
  line1: string
  line2: string | null
  postalCode: string
  city: string
  country: string
  isDefaultShipping: boolean
  isDefaultBilling: boolean
}

export interface AuthResponse {
  user: User
  token: string
}

export interface LoginPayload {
  email: string
  password: string
}

export interface RegisterPayload {
  name: string
  email: string
  password: string
  passwordConfirmation: string
}
Checklist:

 User interface
 UserRole type
 Address interface
 Auth response type
 Login/Register payloads
File: src/types/api.ts
text

Path: atelier-arome-web/src/types/api.ts
Type: TypeScript Types
Description: API response wrapper types.

Interface:

TypeScript

export interface ApiResponse<T> {
  data: T
  message?: string
}

export interface PaginatedResponse<T> {
  data: T[]
  meta: {
    currentPage: number
    lastPage: number
    perPage: number
    total: number
  }
  links: {
    first: string
    last: string
    prev: string | null
    next: string | null
  }
}

export interface ApiError {
  message: string
  errors?: Record<string, string[]>
  statusCode: number
}

export interface ValidationError {
  message: string
  errors: Record<string, string[]>
}
Checklist:

 Generic API response wrapper
 Paginated response type
 Error types defined
 Validation error format matches Laravel
Phase 1 Completion Criteria
Backend Checklist
 All migrations created and tested
 All enums defined with methods
 Seeders populate test data
 Configuration files complete
 Database schema matches ERD
 php artisan migrate:fresh --seed works
Frontend Checklist
 Next.js project scaffolded
 Tailwind configured with design system
 All utility functions created
 Type definitions complete
 Providers configured
 npm run dev works
 npm run build succeeds
Integration Checklist
 CORS configured correctly
 API proxy rewrites work
 Environment variables documented
 Git repositories initialized
 README files created
📦 PHASE 2: Core Product System
Phase Overview
Property	Value
Duration	2 weeks
Priority	Critical Path
Dependencies	Phase 1 complete
Deliverables	Product API, product catalog, product detail pages
2.1 Backend — Models
File: app/Models/Category.php
text

Path: atelier-arome-api/app/Models/Category.php
Type: Eloquent Model
Description: Category model for product organization.

Features:

UUID primary key
Slug generation
Product relationship
Active scope
Ordered scope
Interface:

PHP

<?php

namespace App\Models;

use App\Models\Concerns\HasUuid;
use Illuminate\Database\Eloquent\Model;
use Illuminate\Database\Eloquent\Relations\HasMany;
use Illuminate\Database\Eloquent\Builder;

class Category extends Model
{
    use HasUuid;
    
    protected $fillable = [
        'name',
        'slug',
        'description',
        'image_url',
        'sort_order',
        'is_active',
    ];
    
    protected $casts = [
        'is_active' => 'boolean',
        'sort_order' => 'integer',
    ];
    
    // Relationships
    public function products(): HasMany;
    
    // Scopes
    public function scopeActive(Builder $query): Builder;
    public function scopeOrdered(Builder $query): Builder;
    
    // Accessors
    public function getProductCountAttribute(): int;
    
    // Route model binding
    public function getRouteKeyName(): string
    {
        return 'slug';
    }
}
Checklist:

 HasUuid trait used
 All fillable fields defined
 Proper casts configured
 Products relationship defined
 Active scope filters is_active = true
 Ordered scope sorts by sort_order
 Route key name set to slug
 Product count accessor
File: app/Models/Product.php
text

Path: atelier-arome-api/app/Models/Product.php
Type: Eloquent Model
Description: Core product model for essences.

Features:

UUID primary key
Slug generation
Soft deletes
Multiple relationships
Enum casting
Search indexing
Complex scopes
Interface:

PHP

<?php

namespace App\Models;

use App\Enums\ProductHumour;
use App\Enums\ProductRarity;
use App\Enums\ProductSeason;
use App\Models\Concerns\HasUuid;
use Illuminate\Database\Eloquent\Model;
use Illuminate\Database\Eloquent\SoftDeletes;
use Illuminate\Database\Eloquent\Relations\BelongsTo;
use Illuminate\Database\Eloquent\Relations\HasMany;
use Illuminate\Database\Eloquent\Relations\BelongsToMany;
use Illuminate\Database\Eloquent\Builder;
use Laravel\Scout\Searchable;

class Product extends Model
{
    use HasUuid, SoftDeletes, Searchable;
    
    protected $fillable = [
        'category_id',
        'name',
        'slug',
        'latin_name',
        'description',
        'long_description',
        'humour',
        'rarity',
        'season',
        'extraction_method',
        'folio_number',
        'is_featured',
        'is_active',
        'sort_order',
        'meta_data',
    ];
    
    protected $casts = [
        'humour' => ProductHumour::class,
        'rarity' => ProductRarity::class,
        'season' => ProductSeason::class,
        'is_featured' => 'boolean',
        'is_active' => 'boolean',
        'sort_order' => 'integer',
        'meta_data' => 'array',
    ];
    
    // Relationships
    public function category(): BelongsTo;
    public function variants(): HasMany;
    public function images(): HasMany;
    public function tags(): BelongsToMany;
    public function reviews(): HasMany;
    public function wishlistItems(): HasMany;
    
    // Scopes
    public function scopeActive(Builder $query): Builder;
    public function scopeFeatured(Builder $query): Builder;
    public function scopeByHumour(Builder $query, ProductHumour $humour): Builder;
    public function scopeByRarity(Builder $query, ProductRarity $rarity): Builder;
    public function scopeBySeason(Builder $query, ProductSeason $season): Builder;
    public function scopeOrdered(Builder $query): Builder;
    
    // Accessors
    public function getDefaultVariantAttribute(): ?ProductVariant;
    public function getPrimaryImageAttribute(): ?ProductImage;
    public function getMinPriceAttribute(): float;
    public function getMaxPriceAttribute(): float;
    public function getAverageRatingAttribute(): float;
    public function getReviewCountAttribute(): int;
    public function getInStockAttribute(): bool;
    
    // Route model binding
    public function getRouteKeyName(): string
    {
        return 'slug';
    }
    
    // Search
    public function toSearchableArray(): array;
}
Checklist:

 HasUuid trait
 SoftDeletes trait
 Searchable trait (Scout)
 All fillable fields
 Enum casts for humour/rarity/season
 Boolean casts
 JSON cast for meta_data
 Category relationship (BelongsTo)
 Variants relationship (HasMany)
 Images relationship (HasMany)
 Tags relationship (BelongsToMany)
 Reviews relationship (HasMany)
 Active scope
 Featured scope
 Filter scopes (humour, rarity, season)
 Ordered scope
 Default variant accessor
 Primary image accessor
 Min/max price accessors
 Average rating accessor
 Review count accessor
 In stock accessor
 Route key name (slug)
 Searchable array for Meilisearch
File: app/Models/ProductVariant.php
text

Path: atelier-arome-api/app/Models/ProductVariant.php
Type: Eloquent Model
Description: Product variant model for different phial sizes.

Interface:

PHP

<?php

namespace App\Models;

class ProductVariant extends Model
{
    use HasUuid;
    
    protected $fillable = [
        'product_id',
        'name',
        'sku',
        'price_sgd',
        'compare_at_price',
        'weight_grams',
        'is_default',
        'is_active',
    ];
    
    protected $casts = [
        'price_sgd' => 'decimal:2',
        'compare_at_price' => 'decimal:2',
        'weight_grams' => 'integer',
        'is_default' => 'boolean',
        'is_active' => 'boolean',
    ];
    
    // Relationships
    public function product(): BelongsTo;
    public function inventory(): HasOne;
    public function cartItems(): HasMany;
    public function orderItems(): HasMany;
    
    // Scopes
    public function scopeActive(Builder $query): Builder;
    public function scopeDefault(Builder $query): Builder;
    
    // Accessors
    public function getOnSaleAttribute(): bool;
    public function getDiscountPercentageAttribute(): ?int;
    public function getStockQuantityAttribute(): int;
    public function getInStockAttribute(): bool;
}
Checklist:

 HasUuid trait
 All fillable fields
 Decimal casts for prices
 Product relationship
 Inventory relationship
 Cart/order items relationships
 Active scope
 Default scope
 On sale accessor
 Discount percentage accessor
 Stock quantity accessor
 In stock accessor
File: app/Models/ProductImage.php
text

Path: atelier-arome-api/app/Models/ProductImage.php
Type: Eloquent Model
Description: Product image model.

Interface:

PHP

<?php

namespace App\Models;

class ProductImage extends Model
{
    use HasUuid;
    
    protected $fillable = [
        'product_id',
        'url',
        'alt_text',
        'sort_order',
        'is_primary',
    ];
    
    protected $casts = [
        'sort_order' => 'integer',
        'is_primary' => 'boolean',
    ];
    
    // Relationships
    public function product(): BelongsTo;
    
    // Scopes
    public function scopePrimary(Builder $query): Builder;
    public function scopeOrdered(Builder $query): Builder;
}
Checklist:

 HasUuid trait
 All fillable fields
 Product relationship
 Primary scope
 Ordered scope
File: app/Models/Tag.php
text

Path: atelier-arome-api/app/Models/Tag.php
Type: Eloquent Model
Description: Tag model for scent notes.

Checklist:

 HasUuid trait
 Name and slug fields
 Products relationship (BelongsToMany)
 Route key name (slug)
File: app/Models/Inventory.php
text

Path: atelier-arome-api/app/Models/Inventory.php
Type: Eloquent Model
Description: Inventory tracking model.

Interface:

PHP

<?php

namespace App\Models;

class Inventory extends Model
{
    use HasUuid;
    
    protected $fillable = [
        'variant_id',
        'quantity',
        'reserved_quantity',
        'low_stock_threshold',
        'last_restocked_at',
    ];
    
    protected $casts = [
        'quantity' => 'integer',
        'reserved_quantity' => 'integer',
        'low_stock_threshold' => 'integer',
        'last_restocked_at' => 'datetime',
    ];
    
    // Relationships
    public function variant(): BelongsTo;
    public function movements(): HasMany;
    
    // Accessors
    public function getAvailableQuantityAttribute(): int
    {
        return max(0, $this->quantity - $this->reserved_quantity);
    }
    
    public function getIsLowStockAttribute(): bool
    {
        return $this->available_quantity <= $this->low_stock_threshold;
    }
    
    public function getInStockAttribute(): bool
    {
        return $this->available_quantity > 0;
    }
    
    // Methods
    public function reserve(int $quantity): bool;
    public function release(int $quantity): bool;
    public function deduct(int $quantity): bool;
    public function add(int $quantity, ?string $reason = null): bool;
}
Checklist:

 HasUuid trait
 Variant relationship (unique)
 Movements relationship
 Available quantity accessor
 Is low stock accessor
 In stock accessor
 Reserve method
 Release method
 Deduct method
 Add method
2.2 Backend — API Resources
File: app/Http/Resources/ProductResource.php
text

Path: atelier-arome-api/app/Http/Resources/ProductResource.php
Type: API Resource
Description: JSON:API resource for product serialization.

Interface:

PHP

<?php

namespace App\Http\Resources;

use Illuminate\Http\Request;
use Illuminate\Http\Resources\Json\JsonResource;

class ProductResource extends JsonResource
{
    public function toArray(Request $request): array
    {
        return [
            'id' => $this->id,
            'categoryId' => $this->category_id,
            'name' => $this->name,
            'slug' => $this->slug,
            'latinName' => $this->latin_name,
            'description' => $this->description,
            'longDescription' => $this->when(
                $request->routeIs('products.show'),
                $this->long_description
            ),
            'humour' => $this->humour->value,
            'humourLabel' => $this->humour->label(),
            'humourSymbol' => $this->humour->symbol(),
            'rarity' => $this->rarity->value,
            'rarityLabel' => $this->rarity->label(),
            'season' => $this->season->value,
            'seasonLabel' => $this->season->label(),
            'extractionMethod' => $this->extraction_method,
            'folioNumber' => $this->folio_number,
            'isFeatured' => $this->is_featured,
            'isActive' => $this->is_active,
            
            // Computed attributes
            'minPrice' => $this->min_price,
            'maxPrice' => $this->max_price,
            'averageRating' => $this->average_rating,
            'reviewCount' => $this->review_count,
            'inStock' => $this->in_stock,
            
            // Relationships
            'defaultVariant' => new ProductVariantResource($this->defaultVariant),
            'variants' => ProductVariantResource::collection(
                $this->whenLoaded('variants')
            ),
            'images' => ProductImageResource::collection(
                $this->whenLoaded('images')
            ),
            'tags' => $this->whenLoaded('tags', fn() => 
                $this->tags->pluck('name')
            ),
            'category' => new CategoryResource(
                $this->whenLoaded('category')
            ),
            
            // Timestamps
            'createdAt' => $this->created_at->toISOString(),
            'updatedAt' => $this->updated_at->toISOString(),
        ];
    }
}
Checklist:

 All product fields included
 Enum values with labels and symbols
 Computed attributes included
 Conditional relationship loading
 Long description conditional (detail only)
 Camel case key transformation
 ISO date formatting
 Default variant always included
 Variants/images when loaded
File: app/Http/Resources/ProductCollection.php
text

Path: atelier-arome-api/app/Http/Resources/ProductCollection.php
Type: API Resource Collection
Description: Resource collection for paginated product listings.

Checklist:

 Extends ResourceCollection
 Pagination meta included
 Links included
 Collection wrapper
File: app/Http/Resources/ProductVariantResource.php
text

Path: atelier-arome-api/app/Http/Resources/ProductVariantResource.php
Type: API Resource
Description: JSON:API resource for variant serialization.

Interface:

PHP

<?php

namespace App\Http\Resources;

class ProductVariantResource extends JsonResource
{
    public function toArray(Request $request): array
    {
        return [
            'id' => $this->id,
            'name' => $this->name,
            'sku' => $this->sku,
            'priceSgd' => (float) $this->price_sgd,
            'compareAtPrice' => $this->compare_at_price 
                ? (float) $this->compare_at_price 
                : null,
            'weightGrams' => $this->weight_grams,
            'isDefault' => $this->is_default,
            'isActive' => $this->is_active,
            'onSale' => $this->on_sale,
            'discountPercentage' => $this->discount_percentage,
            'stockQuantity' => $this->stock_quantity,
            'inStock' => $this->in_stock,
        ];
    }
}
Checklist:

 All variant fields
 Price as float
 On sale computed
 Discount percentage computed
 Stock quantity from inventory
 In stock boolean
File: app/Http/Resources/CategoryResource.php
text

Path: atelier-arome-api/app/Http/Resources/CategoryResource.php
Type: API Resource
Checklist:

 All category fields
 Product count when needed
 Camel case keys
2.3 Backend — Controllers
File:
