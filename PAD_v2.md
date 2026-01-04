Atelier Arôme — Project Architecture Document
Executive Summary
Project Vision
Transform a sophisticated artisanal aromatherapy brand into a full-featured e-commerce platform serving the Singapore market. The architecture prioritizes aesthetic preservation, scalability, and local market compliance while delivering an exceptional customer experience that mirrors the brand's "alchemical luxury" identity.

Architecture Philosophy
text

┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│   DECOUPLED MONOLITH — API-FIRST ARCHITECTURE                              │
│                                                                             │
│   ┌─────────────────────┐         ┌─────────────────────┐                  │
│   │                     │   API   │                     │                  │
│   │   NEXT.JS 15        │◄───────►│   LARAVEL 12        │                  │
│   │   Frontend          │  JSON   │   Backend           │                  │
│   │                     │         │                     │                  │
│   │   • SSR/ISR Pages   │         │   • RESTful API     │                  │
│   │   • React 19        │         │   • Sanctum Auth    │                  │
│   │   • Shadcn UI       │         │   • Eloquent ORM    │                  │
│   │   • Tailwind 4.0    │         │   • Queue Workers   │                  │
│   │                     │         │                     │                  │
│   └─────────┬───────────┘         └──────────┬──────────┘                  │
│             │                                │                              │
│             │         ┌──────────────────────┤                              │
│             │         │                      │                              │
│             ▼         ▼                      ▼                              │
│   ┌─────────────────────┐         ┌─────────────────────┐                  │
│   │   VERCEL            │         │   FORGE/VAPOR       │                  │
│   │   Edge Network      │         │   Laravel Hosting   │                  │
│   └─────────────────────┘         └─────────────────────┘                  │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
Singapore Market Considerations
Requirement	Implementation
GST 9%	Automatic tax calculation on all orders
SGD Currency	Default currency with formatting
PayNow	Integration via Stripe Singapore or HitPay
SingPost	Shipping rate API integration
PDPA Compliance	Data protection consent flows
Local Payments	GrabPay, PayNow, NETS optional
Technology Stack Specification
Backend (Laravel 12)
YAML

Core:
  PHP: "^8.3"
  Laravel: "^12.0"
  
Database & ORM:
  PostgreSQL: "^16.0"
  Eloquent ORM: "native"
  
Authentication:
  Laravel Sanctum: "^4.0"      # API token + SPA authentication
  
API:
  Laravel API Resources: "native"
  Spatie Query Builder: "^6.0"  # Advanced filtering/sorting
  
E-Commerce:
  Custom Models: "Bespoke"      # Products, Orders, Cart
  Stripe PHP SDK: "^15.0"       # Payment processing
  
Queue & Jobs:
  Laravel Horizon: "^5.0"       # Redis queue management
  Redis: "^7.0"
  
File Storage:
  Laravel Filesystem: "native"
  Cloudinary SDK: "^2.0"        # Image optimization CDN
  
Email:
  Resend PHP SDK: "^0.10"       # Transactional email
  Laravel Mail: "native"
  
Admin Panel:
  Filament: "^3.2"              # Admin dashboard
  
Testing:
  Pest PHP: "^3.0"
  Laravel Dusk: "^8.0"          # Browser testing
  
Dev Tools:
  Laravel Pint: "^1.0"          # Code styling
  Larastan: "^2.0"              # Static analysis
  Laravel IDE Helper: "^3.0"
Frontend (Next.js 15)
YAML

Core:
  Next.js: "^15.0"
  React: "^19.0"
  TypeScript: "^5.6"
  
Styling:
  Tailwind CSS: "^4.0"
  tailwindcss-animate: "^1.0"
  
UI Components:
  Shadcn UI: "latest"           # Radix primitives
  Radix UI: "^1.1"              # Accessible components
  Lucide React: "^0.400"        # Icons
  
Animations:
  Framer Motion: "^11.0"        # Complex animations
  
State Management:
  Zustand: "^5.0"               # Client state
  TanStack Query: "^5.0"        # Server state
  
Forms:
  React Hook Form: "^7.0"
  Zod: "^3.23"                  # Schema validation
  
HTTP:
  Ky: "^1.5"                    # Fetch wrapper
  
Utilities:
  date-fns: "^3.6"              # Date formatting
  clsx: "^2.1"                  # Class merging
  tailwind-merge: "^2.5"
  
Testing:
  Vitest: "^2.0"
  React Testing Library: "^16.0"
  Playwright: "^1.45"           # E2E testing
Infrastructure
YAML

Frontend Hosting:
  Provider: "Vercel"
  Features:
    - Edge Functions
    - ISR (Incremental Static Regeneration)
    - Image Optimization
    - Analytics
    
Backend Hosting:
  Provider: "Laravel Forge + DigitalOcean"
  Alternative: "Laravel Vapor (AWS Serverless)"
  
Database:
  Provider: "Supabase PostgreSQL"
  Alternative: "PlanetScale (MySQL)"
  
Cache:
  Provider: "Upstash Redis"
  
CDN:
  Provider: "Cloudinary"
  Use: "Product images, optimized delivery"
  
Email:
  Provider: "Resend"
  
Payments:
  Primary: "Stripe Singapore"
  Secondary: "HitPay (PayNow, GrabPay)"
  
Monitoring:
  Error Tracking: "Sentry"
  APM: "Laravel Telescope (dev), Datadog (prod)"
  Logs: "Papertrail or Logtail"
File Hierarchy Diagram
Laravel Backend Structure
text

atelier-arome-api/
├── app/
│   ├── Actions/                          # Single-purpose action classes
│   │   ├── Cart/
│   │   │   ├── AddItemToCart.php         # Add product to cart
│   │   │   ├── RemoveItemFromCart.php    # Remove product from cart
│   │   │   ├── UpdateCartItemQuantity.php
│   │   │   └── ClearCart.php
│   │   ├── Checkout/
│   │   │   ├── CreateOrder.php           # Convert cart to order
│   │   │   ├── ProcessPayment.php        # Stripe payment processing
│   │   │   ├── ApplyDiscount.php
│   │   │   └── CalculateShipping.php     # SingPost rate calculation
│   │   ├── Order/
│   │   │   ├── FulfillOrder.php          # Mark order as fulfilled
│   │   │   ├── RefundOrder.php
│   │   │   └── SendOrderConfirmation.php
│   │   └── Newsletter/
│   │       └── SubscribeToNewsletter.php # "Correspondence" signup
│   │
│   ├── Console/
│   │   └── Commands/
│   │       ├── SyncInventory.php         # Inventory sync job
│   │       ├── SendAbandonedCartEmails.php
│   │       └── GenerateSalesReport.php
│   │
│   ├── Enums/                            # PHP 8.1+ Enums
│   │   ├── OrderStatus.php               # pending, processing, shipped, delivered
│   │   ├── PaymentStatus.php             # pending, completed, failed, refunded
│   │   ├── ProductHumour.php             # calming, uplifting, grounding, clarifying
│   │   ├── ProductRarity.php             # common, rare, limited
│   │   └── Season.php                    # spring, summer, autumn, winter
│   │
│   ├── Events/
│   │   ├── OrderPlaced.php
│   │   ├── OrderShipped.php
│   │   ├── PaymentReceived.php
│   │   └── NewsletterSubscribed.php
│   │
│   ├── Exceptions/
│   │   ├── InsufficientStockException.php
│   │   ├── PaymentFailedException.php
│   │   └── InvalidDiscountCodeException.php
│   │
│   ├── Http/
│   │   ├── Controllers/
│   │   │   ├── Api/
│   │   │   │   └── V1/
│   │   │   │       ├── AuthController.php           # Login, register, logout
│   │   │   │       ├── ProductController.php        # CRUD + filtering
│   │   │   │       ├── CategoryController.php
│   │   │   │       ├── CartController.php           # Cart operations
│   │   │   │       ├── CheckoutController.php       # Checkout flow
│   │   │   │       ├── OrderController.php          # Order history
│   │   │   │       ├── AddressController.php        # Saved addresses
│   │   │   │       ├── WishlistController.php       # "Bookmarked Essences"
│   │   │   │       ├── NewsletterController.php     # "Correspondence"
│   │   │   │       ├── TestimonialController.php    # "Manuscript" entries
│   │   │   │       └── WebhookController.php        # Stripe webhooks
│   │   │   │
│   │   │   └── Webhook/
│   │   │       └── StripeWebhookController.php
│   │   │
│   │   ├── Middleware/
│   │   │   ├── EnsureCartExists.php
│   │   │   ├── VerifyStripeSignature.php
│   │   │   └── LocalizeSingapore.php     # SGD, timezone
│   │   │
│   │   ├── Requests/
│   │   │   ├── Auth/
│   │   │   │   ├── LoginRequest.php
│   │   │   │   └── RegisterRequest.php
│   │   │   ├── Cart/
│   │   │   │   ├── AddToCartRequest.php
│   │   │   │   └── UpdateCartItemRequest.php
│   │   │   ├── Checkout/
│   │   │   │   ├── CheckoutRequest.php
│   │   │   │   └── ApplyDiscountRequest.php
│   │   │   └── Product/
│   │   │       ├── StoreProductRequest.php
│   │   │       └── UpdateProductRequest.php
│   │   │
│   │   └── Resources/
│   │       ├── ProductResource.php           # "Essence" API response
│   │       ├── ProductCollection.php
│   │       ├── CartResource.php              # "Vial" cart response
│   │       ├── CartItemResource.php
│   │       ├── OrderResource.php
│   │       ├── OrderCollection.php
│   │       ├── CategoryResource.php
│   │       ├── TestimonialResource.php       # "Manuscript" entry
│   │       └── UserResource.php
│   │
│   ├── Jobs/
│   │   ├── ProcessStripePayment.php
│   │   ├── SendOrderConfirmationEmail.php
│   │   ├── SendShippingNotification.php
│   │   ├── SyncProductToAlgolia.php          # Search indexing
│   │   └── GenerateInvoicePdf.php
│   │
│   ├── Listeners/
│   │   ├── SendOrderConfirmation.php
│   │   ├── UpdateInventoryOnOrder.php
│   │   ├── NotifyAdminOfNewOrder.php
│   │   └── AddSubscriberToMailingList.php
│   │
│   ├── Mail/
│   │   ├── OrderConfirmation.php             # "Atelier Dispatch" email
│   │   ├── OrderShipped.php
│   │   ├── WelcomeNewsletter.php             # "Quarterly Folio" welcome
│   │   ├── AbandonedCart.php
│   │   └── PasswordReset.php
│   │
│   ├── Models/
│   │   ├── User.php                          # Customer/Admin
│   │   ├── Product.php                       # "Essence"
│   │   ├── ProductVariant.php                # 5ml, 15ml, 30ml phials
│   │   ├── Category.php                      # Singles, Blends, Sets
│   │   ├── Tag.php                           # Humour, Season
│   │   ├── Cart.php                          # "Collection Vial"
│   │   ├── CartItem.php
│   │   ├── Order.php
│   │   ├── OrderItem.php
│   │   ├── Address.php                       # Singapore addresses
│   │   ├── Discount.php                      # Promo codes
│   │   ├── Wishlist.php                      # "Bookmarked Essences"
│   │   ├── Testimonial.php                   # "Manuscript" entries
│   │   ├── NewsletterSubscriber.php          # "Correspondence"
│   │   ├── Inventory.php
│   │   └── ShippingRate.php                  # SingPost rates
│   │
│   ├── Notifications/
│   │   ├── OrderPlacedNotification.php
│   │   ├── OrderShippedNotification.php
│   │   └── LowStockNotification.php
│   │
│   ├── Observers/
│   │   ├── OrderObserver.php                 # Auto-generate order number
│   │   ├── ProductObserver.php               # Slug generation
│   │   └── CartObserver.php                  # Expiry handling
│   │
│   ├── Policies/
│   │   ├── OrderPolicy.php
│   │   ├── AddressPolicy.php
│   │   └── WishlistPolicy.php
│   │
│   ├── Providers/
│   │   ├── AppServiceProvider.php
│   │   ├── AuthServiceProvider.php
│   │   ├── EventServiceProvider.php
│   │   └── StripeServiceProvider.php
│   │
│   ├── Services/
│   │   ├── CartService.php                   # Cart business logic
│   │   ├── CheckoutService.php
│   │   ├── PaymentService.php                # Stripe abstraction
│   │   ├── ShippingService.php               # SingPost integration
│   │   ├── TaxService.php                    # GST calculation
│   │   ├── InventoryService.php
│   │   └── SearchService.php                 # Algolia/Meilisearch
│   │
│   └── Traits/
│       ├── HasUuid.php
│       ├── HasSlug.php
│       └── FormatsAsCurrency.php             # SGD formatting
│
├── bootstrap/
│   ├── app.php
│   └── providers.php
│
├── config/
│   ├── app.php
│   ├── auth.php
│   ├── cart.php                              # Cart settings (TTL, max items)
│   ├── checkout.php                          # GST rate, shipping zones
│   ├── database.php
│   ├── filament.php                          # Admin panel config
│   ├── horizon.php                           # Queue dashboard
│   ├── mail.php
│   ├── payments.php                          # Stripe keys, webhooks
│   ├── sanctum.php
│   └── services.php                          # Third-party API keys
│
├── database/
│   ├── factories/
│   │   ├── UserFactory.php
│   │   ├── ProductFactory.php
│   │   ├── OrderFactory.php
│   │   └── TestimonialFactory.php
│   │
│   ├── migrations/
│   │   ├── 0001_01_01_000000_create_users_table.php
│   │   ├── 0001_01_01_000001_create_cache_table.php
│   │   ├── 0001_01_01_000002_create_jobs_table.php
│   │   ├── 2024_01_01_000001_create_categories_table.php
│   │   ├── 2024_01_01_000002_create_products_table.php
│   │   ├── 2024_01_01_000003_create_product_variants_table.php
│   │   ├── 2024_01_01_000004_create_tags_table.php
│   │   ├── 2024_01_01_000005_create_product_tag_table.php
│   │   ├── 2024_01_01_000006_create_carts_table.php
│   │   ├── 2024_01_01_000007_create_cart_items_table.php
│   │   ├── 2024_01_01_000008_create_addresses_table.php
│   │   ├── 2024_01_01_000009_create_orders_table.php
│   │   ├── 2024_01_01_000010_create_order_items_table.php
│   │   ├── 2024_01_01_000011_create_discounts_table.php
│   │   ├── 2024_01_01_000012_create_wishlists_table.php
│   │   ├── 2024_01_01_000013_create_testimonials_table.php
│   │   ├── 2024_01_01_000014_create_newsletter_subscribers_table.php
│   │   ├── 2024_01_01_000015_create_inventories_table.php
│   │   └── 2024_01_01_000016_create_shipping_rates_table.php
│   │
│   └── seeders/
│       ├── DatabaseSeeder.php
│       ├── CategorySeeder.php
│       ├── ProductSeeder.php                 # Initial "Essences"
│       ├── TagSeeder.php                     # Humours, Seasons
│       ├── TestimonialSeeder.php             # "Manuscript" entries
│       ├── ShippingRateSeeder.php            # SG shipping zones
│       └── AdminUserSeeder.php
│
├── routes/
│   ├── api.php                               # API v1 routes
│   ├── channels.php                          # Broadcasting
│   ├── console.php                           # Artisan commands
│   └── web.php                               # Filament admin
│
├── storage/
│   ├── app/
│   │   ├── invoices/                         # Generated PDFs
│   │   └── exports/                          # CSV exports
│   ├── framework/
│   └── logs/
│
├── tests/
│   ├── Feature/
│   │   ├── Api/
│   │   │   ├── AuthTest.php
│   │   │   ├── ProductTest.php
│   │   │   ├── CartTest.php
│   │   │   ├── CheckoutTest.php
│   │   │   └── OrderTest.php
│   │   └── Webhook/
│   │       └── StripeWebhookTest.php
│   │
│   ├── Unit/
│   │   ├── Services/
│   │   │   ├── TaxServiceTest.php
│   │   │   └── CartServiceTest.php
│   │   └── Models/
│   │       └── ProductTest.php
│   │
│   └── Pest.php
│
├── .env.example
├── artisan
├── composer.json
├── phpstan.neon
├── phpunit.xml
└── README.md
Next.js Frontend Structure
text

atelier-arome-web/
├── public/
│   ├── fonts/
│   │   ├── CormorantGaramond-Light.woff2
│   │   ├── CormorantGaramond-Regular.woff2
│   │   ├── CormorantGaramond-Medium.woff2
│   │   ├── CormorantGaramond-SemiBold.woff2
│   │   ├── CormorantGaramond-Bold.woff2
│   │   ├── CormorantGaramond-LightItalic.woff2
│   │   ├── CormorantGaramond-Italic.woff2
│   │   ├── CrimsonPro-Light.woff2
│   │   ├── CrimsonPro-Regular.woff2
│   │   ├── CrimsonPro-Medium.woff2
│   │   ├── CrimsonPro-SemiBold.woff2
│   │   ├── CrimsonPro-LightItalic.woff2
│   │   ├── CrimsonPro-Italic.woff2
│   │   ├── GreatVibes-Regular.woff2
│   │   ├── PlayfairDisplay-Regular.woff2
│   │   └── PlayfairDisplay-Medium.woff2
│   │
│   ├── images/
│   │   ├── og-image.jpg                      # Social preview
│   │   ├── favicon.svg
│   │   └── botanicals/                       # Botanical illustrations
│   │       ├── lavender.svg
│   │       ├── eucalyptus.svg
│   │       ├── bergamot.svg
│   │       └── rose.svg
│   │
│   ├── manifest.json
│   └── robots.txt
│
├── src/
│   ├── app/                                  # Next.js App Router
│   │   ├── (storefront)/                     # Public pages group
│   │   │   ├── layout.tsx                    # Storefront layout with header/footer
│   │   │   ├── page.tsx                      # Homepage
│   │   │   ├── loading.tsx                   # Loading UI
│   │   │   ├── error.tsx                     # Error boundary
│   │   │   │
│   │   │   ├── compendium/                   # Product catalog
│   │   │   │   ├── page.tsx                  # All products (filterable)
│   │   │   │   ├── loading.tsx
│   │   │   │   └── [slug]/
│   │   │   │       ├── page.tsx              # Product detail page
│   │   │   │       ├── loading.tsx
│   │   │   │       └── opengraph-image.tsx   # Dynamic OG image
│   │   │   │
│   │   │   ├── alchemy/                      # About/Process page
│   │   │   │   └── page.tsx
│   │   │   │
│   │   │   ├── atelier/                      # About the studio
│   │   │   │   └── page.tsx
│   │   │   │
│   │   │   ├── manuscript/                   # Testimonials
│   │   │   │   └── page.tsx
│   │   │   │
│   │   │   ├── correspondence/               # Newsletter
│   │   │   │   └── page.tsx
│   │   │   │
│   │   │   └── search/                       # Search results
│   │   │       └── page.tsx
│   │   │
│   │   ├── (checkout)/                       # Checkout flow group
│   │   │   ├── layout.tsx                    # Minimal checkout layout
│   │   │   ├── vial/                         # Cart page
│   │   │   │   └── page.tsx
│   │   │   ├── checkout/
│   │   │   │   ├── page.tsx                  # Checkout form
│   │   │   │   ├── shipping/
│   │   │   │   │   └── page.tsx
│   │   │   │   └── payment/
│   │   │   │       └── page.tsx
│   │   │   └── confirmation/
│   │   │       └── [orderId]/
│   │   │           └── page.tsx              # Order confirmation
│   │   │
│   │   ├── (account)/                        # Account pages group
│   │   │   ├── layout.tsx                    # Account sidebar layout
│   │   │   ├── account/
│   │   │   │   ├── page.tsx                  # Account overview
│   │   │   │   ├── orders/
│   │   │   │   │   ├── page.tsx              # Order history
│   │   │   │   │   └── [orderId]/
│   │   │   │   │       └── page.tsx          # Order detail
│   │   │   │   ├── addresses/
│   │   │   │   │   └── page.tsx
│   │   │   │   ├── bookmarks/                # Wishlist
│   │   │   │   │   └── page.tsx
│   │   │   │   └── settings/
│   │   │   │       └── page.tsx
│   │   │   └── auth/
│   │   │       ├── login/
│   │   │       │   └── page.tsx
│   │   │       ├── register/
│   │   │       │   └── page.tsx
│   │   │       └── forgot-password/
│   │   │           └── page.tsx
│   │   │
│   │   ├── (legal)/                          # Legal pages
│   │   │   ├── privacy/
│   │   │   │   └── page.tsx
│   │   │   ├── terms/
│   │   │   │   └── page.tsx
│   │   │   └── shipping-policy/
│   │   │       └── page.tsx
│   │   │
│   │   ├── api/                              # Next.js API routes (BFF)
│   │   │   ├── auth/
│   │   │   │   └── [...nextauth]/
│   │   │   │       └── route.ts              # NextAuth handlers
│   │   │   ├── revalidate/
│   │   │   │   └── route.ts                  # ISR revalidation webhook
│   │   │   └── checkout/
│   │   │       └── create-session/
│   │   │           └── route.ts              # Stripe session creation
│   │   │
│   │   ├── globals.css                       # Global styles + Tailwind
│   │   ├── layout.tsx                        # Root layout
│   │   ├── not-found.tsx                     # 404 page
│   │   └── sitemap.ts                        # Dynamic sitemap
│   │
│   ├── components/
│   │   ├── ui/                               # Shadcn UI components
│   │   │   ├── button.tsx
│   │   │   ├── input.tsx
│   │   │   ├── label.tsx
│   │   │   ├── select.tsx
│   │   │   ├── checkbox.tsx
│   │   │   ├── radio-group.tsx
│   │   │   ├── dialog.tsx                    # Modal base
│   │   │   ├── sheet.tsx                     # Drawer base (Vial drawer)
│   │   │   ├── toast.tsx
│   │   │   ├── toaster.tsx
│   │   │   ├── skeleton.tsx
│   │   │   ├── separator.tsx
│   │   │   ├── badge.tsx
│   │   │   ├── card.tsx
│   │   │   ├── accordion.tsx
│   │   │   ├── tabs.tsx
│   │   │   ├── dropdown-menu.tsx
│   │   │   ├── navigation-menu.tsx
│   │   │   ├── pagination.tsx
│   │   │   ├── form.tsx                      # React Hook Form wrapper
│   │   │   └── scroll-area.tsx
│   │   │
│   │   ├── layout/                           # Layout components
│   │   │   ├── header/
│   │   │   │   ├── header.tsx                # Main header
│   │   │   │   ├── header-seal.tsx           # Atelier logo/seal
│   │   │   │   ├── header-nav.tsx            # Desktop navigation
│   │   │   │   ├── header-tools.tsx          # Search, cart, menu
│   │   │   │   ├── mobile-nav.tsx            # Mobile navigation drawer
│   │   │   │   └── atelier-banner.tsx        # Top announcement bar
│   │   │   │
│   │   │   ├── footer/
│   │   │   │   ├── colophon.tsx              # Full footer
│   │   │   │   └── colophon-newsletter.tsx   # Footer newsletter signup
│   │   │   │
│   │   │   ├── vial-drawer.tsx               # Cart drawer (Sheet)
│   │   │   └── back-to-top.tsx
│   │   │
│   │   ├── home/                             # Homepage sections
│   │   │   ├── hero-section.tsx              # Illuminated manuscript hero
│   │   │   ├── hero-vessel.tsx               # Animated vessel illustration
│   │   │   ├── hero-botanicals.tsx           # Floating botanical elements
│   │   │   ├── featured-essences.tsx         # Featured products grid
│   │   │   └── correspondence-section.tsx   # Newsletter CTA
│   │   │
│   │   ├── products/                         # Product components
│   │   │   ├── essence-card.tsx              # Product card
│   │   │   ├── essence-grid.tsx              # Product grid layout
│   │   │   ├── essence-filters.tsx           # Humour/Season filters
│   │   │   ├── essence-sort.tsx              # Sort dropdown
│   │   │   ├── essence-detail.tsx            # PDP main content
│   │   │   ├── essence-gallery.tsx           # Image gallery
│   │   │   ├── variant-selector.tsx          # Size/variant picker
│   │   │   ├── add-to-vial-button.tsx        # Add to cart button
│   │   │   └── related-essences.tsx          # Related products
│   │   │
│   │   ├── cart/                             # Cart components
│   │   │   ├── cart-item.tsx                 # Single cart item
│   │   │   ├── cart-summary.tsx              # Subtotal, taxes, total
│   │   │   ├── quantity-selector.tsx
│   │   │   └── empty-cart.tsx
│   │   │
│   │   ├── checkout/                         # Checkout components
│   │   │   ├── checkout-form.tsx             # Main checkout form
│   │   │   ├── shipping-form.tsx             # Address form
│   │   │   ├── payment-form.tsx              # Stripe Elements
│   │   │   ├── order-summary.tsx
│   │   │   ├── discount-input.tsx
│   │   │   └── shipping-options.tsx          # SingPost options
│   │   │
│   │   ├── account/                          # Account components
│   │   │   ├── order-card.tsx
│   │   │   ├── order-status-badge.tsx
│   │   │   ├── address-card.tsx
│   │   │   ├── address-form.tsx
│   │   │   └── bookmark-card.tsx             # Wishlist item
│   │   │
│   │   ├── content/                          # Content components
│   │   │   ├── alchemy-step.tsx              # Process step
│   │   │   ├── manuscript-entry.tsx          # Testimonial card
│   │   │   ├── manuscript-carousel.tsx       # Testimonial carousel
│   │   │   └── apparatus-item.tsx            # Equipment illustration
│   │   │
│   │   ├── decorative/                       # Visual/decorative elements
│   │   │   ├── gold-leaf.tsx                 # Floating gold accents
│   │   │   ├── texture-overlay.tsx           # Parchment texture
│   │   │   ├── section-border.tsx            # Ornamental dividers
│   │   │   ├── illuminated-initial.tsx       # Drop cap
│   │   │   ├── wax-seal.tsx                  # Decorative seal
│   │   │   ├── quill-icon.tsx                # Animated quill
│   │   │   └── alchemical-symbol.tsx         # Rotating symbol
│   │   │
│   │   ├── forms/                            # Form components
│   │   │   ├── correspondence-form.tsx       # Newsletter signup
│   │   │   ├── contact-form.tsx
│   │   │   ├── login-form.tsx
│   │   │   ├── register-form.tsx
│   │   │   └── search-form.tsx
│   │   │
│   │   └── shared/                           # Shared utilities
│   │       ├── section-header.tsx            # Consistent section headers
│   │       ├── section-label.tsx             # "First Folio" labels
│   │       ├── price-display.tsx             # Currency formatting
│   │       ├── humour-badge.tsx              # ☾ Calming, ☀ Uplifting
│   │       ├── rarity-badge.tsx              # Rare, Limited badges
│   │       ├── loading-skeleton.tsx          # Skeleton variants
│   │       └── error-boundary.tsx
│   │
│   ├── hooks/                                # Custom React hooks
│   │   ├── use-cart.ts                       # Cart state + actions
│   │   ├── use-checkout.ts                   # Checkout flow state
│   │   ├── use-products.ts                   # Product fetching
│   │   ├── use-auth.ts                       # Authentication state
│   │   ├── use-wishlist.ts                   # Bookmark management
│   │   ├── use-local-storage.ts
│   │   ├── use-debounce.ts
│   │   ├── use-intersection-observer.ts
│   │   ├── use-media-query.ts
│   │   ├── use-reduced-motion.ts
│   │   └── use-scroll-position.ts
│   │
│   ├── lib/                                  # Utilities and configs
│   │   ├── api/
│   │   │   ├── client.ts                     # API client (ky wrapper)
│   │   │   ├── endpoints.ts                  # API endpoint constants
│   │   │   ├── products.ts                   # Product API functions
│   │   │   ├── cart.ts                       # Cart API functions
│   │   │   ├── checkout.ts                   # Checkout API functions
│   │   │   ├── orders.ts                     # Order API functions
│   │   │   ├── auth.ts                       # Auth API functions
│   │   │   └── newsletter.ts
│   │   │
│   │   ├── utils/
│   │   │   ├── cn.ts                         # clsx + tailwind-merge
│   │   │   ├── format-currency.ts            # SGD formatting
│   │   │   ├── format-date.ts
│   │   │   ├── slugify.ts
│   │   │   └── validators.ts                 # Zod schemas
│   │   │
│   │   ├── constants/
│   │   │   ├── navigation.ts                 # Nav items
│   │   │   ├── humours.ts                    # Humour data (symbols, colors)
│   │   │   ├── seasons.ts
│   │   │   └── site.ts                       # Site metadata
│   │   │
│   │   ├── fonts.ts                          # Font configuration
│   │   └── stripe.ts                         # Stripe client setup
│   │
│   ├── stores/                               # Zustand stores
│   │   ├── cart-store.ts                     # Cart state
│   │   ├── ui-store.ts                       # UI state (drawers, modals)
│   │   └── filter-store.ts                   # Product filter state
│   │
│   ├── types/                                # TypeScript types
│   │   ├── product.ts
│   │   ├── cart.ts
│   │   ├── order.ts
│   │   ├── user.ts
│   │   ├── api.ts                            # API response types
│   │   └── index.ts
│   │
│   └── styles/                               # Additional styles
│       ├── typography.css                    # Font face declarations
│       └── animations.css                    # Framer Motion presets
│
├── .env.example
├── .env.local
├── components.json                           # Shadcn UI config
├── next.config.ts
├── package.json
├── postcss.config.js
├── tailwind.config.ts                        # Extended theme
├── tsconfig.json
└── README.md
Database Schema
Entity Relationship Diagram
mermaid

erDiagram
    USERS ||--o{ ORDERS : places
    USERS ||--o{ ADDRESSES : has
    USERS ||--o{ WISHLISTS : maintains
    USERS ||--o{ CARTS : has
    
    CATEGORIES ||--o{ PRODUCTS : contains
    PRODUCTS ||--o{ PRODUCT_VARIANTS : has
    PRODUCTS ||--o{ PRODUCT_TAG : tagged_with
    TAGS ||--o{ PRODUCT_TAG : tags
    
    CARTS ||--o{ CART_ITEMS : contains
    CART_ITEMS }o--|| PRODUCT_VARIANTS : references
    
    ORDERS ||--o{ ORDER_ITEMS : contains
    ORDERS }o--|| ADDRESSES : ships_to
    ORDERS }o--o| DISCOUNTS : applies
    ORDER_ITEMS }o--|| PRODUCT_VARIANTS : references
    
    WISHLISTS }o--|| PRODUCTS : bookmarks

    USERS {
        uuid id PK
        string name
        string email UK
        string password
        string phone
        boolean is_admin
        timestamp email_verified_at
        timestamp created_at
        timestamp updated_at
    }
    
    CATEGORIES {
        uuid id PK
        string name
        string slug UK
        text description
        string image_url
        integer sort_order
        boolean is_active
        timestamp created_at
        timestamp updated_at
    }
    
    PRODUCTS {
        uuid id PK
        uuid category_id FK
        string folio_number
        string latin_name
        string common_name
        string slug UK
        text short_description
        text long_description
        enum humour "calming|uplifting|grounding|clarifying"
        enum rarity "common|rare|limited"
        enum season "spring|summer|autumn|winter"
        string extraction_method
        json scent_notes "array of strings"
        string origin_region
        boolean is_featured
        boolean is_active
        integer sort_order
        timestamp created_at
        timestamp updated_at
    }
    
    PRODUCT_VARIANTS {
        uuid id PK
        uuid product_id FK
        string sku UK
        string size_label "5ml|15ml|30ml"
        integer size_ml
        decimal price_sgd "precision 10,2"
        decimal compare_at_price_sgd
        integer stock_quantity
        integer low_stock_threshold
        boolean track_inventory
        boolean is_active
        timestamp created_at
        timestamp updated_at
    }
    
    TAGS {
        uuid id PK
        string name
        string slug UK
        string type "humour|season|collection"
        string icon
        string color
        timestamp created_at
        timestamp updated_at
    }
    
    PRODUCT_TAG {
        uuid product_id FK
        uuid tag_id FK
    }
    
    CARTS {
        uuid id PK
        uuid user_id FK "nullable for guest"
        string session_id "for guest carts"
        string currency "default SGD"
        timestamp expires_at
        timestamp created_at
        timestamp updated_at
    }
    
    CART_ITEMS {
        uuid id PK
        uuid cart_id FK
        uuid product_variant_id FK
        integer quantity
        decimal unit_price_sgd
        timestamp created_at
        timestamp updated_at
    }
    
    ADDRESSES {
        uuid id PK
        uuid user_id FK
        string label "Home|Office|etc"
        string recipient_name
        string phone
        string address_line_1
        string address_line_2
        string postal_code
        string city "default Singapore"
        string country_code "default SG"
        boolean is_default
        timestamp created_at
        timestamp updated_at
    }
    
    ORDERS {
        uuid id PK
        uuid user_id FK "nullable for guest"
        string order_number UK
        uuid shipping_address_id FK
        uuid billing_address_id FK
        string guest_email "for guest checkout"
        decimal subtotal_sgd
        decimal discount_amount_sgd
        decimal shipping_amount_sgd
        decimal tax_amount_sgd "GST 9%"
        decimal total_sgd
        string currency "default SGD"
        enum status "pending|confirmed|processing|shipped|delivered|cancelled"
        enum payment_status "pending|paid|failed|refunded|partially_refunded"
        string payment_intent_id "Stripe"
        string payment_method
        uuid discount_id FK "nullable"
        string shipping_method
        string tracking_number
        string tracking_url
        text notes
        json metadata
        timestamp paid_at
        timestamp shipped_at
        timestamp delivered_at
        timestamp cancelled_at
        timestamp created_at
        timestamp updated_at
    }
    
    ORDER_ITEMS {
        uuid id PK
        uuid order_id FK
        uuid product_variant_id FK
        string product_name "snapshot"
        string variant_name "snapshot"
        string sku "snapshot"
        integer quantity
        decimal unit_price_sgd
        decimal total_price_sgd
        timestamp created_at
        timestamp updated_at
    }
    
    DISCOUNTS {
        uuid id PK
        string code UK
        string description
        enum type "percentage|fixed_amount|free_shipping"
        decimal value
        decimal minimum_order_amount
        integer usage_limit
        integer usage_count
        boolean is_active
        timestamp starts_at
        timestamp expires_at
        timestamp created_at
        timestamp updated_at
    }
    
    WISHLISTS {
        uuid id PK
        uuid user_id FK
        uuid product_id FK
        timestamp created_at
    }
    
    TESTIMONIALS {
        uuid id PK
        string author_name
        string author_title
        string author_location
        text quote
        string folio_reference
        boolean is_verified
        boolean is_illuminated "featured styling"
        boolean is_active
        integer sort_order
        timestamp created_at
        timestamp updated_at
    }
    
    NEWSLETTER_SUBSCRIBERS {
        uuid id PK
        string email UK
        string name
        boolean is_active
        string source "website|checkout|popup"
        timestamp subscribed_at
        timestamp unsubscribed_at
        timestamp created_at
        timestamp updated_at
    }
    
    SHIPPING_RATES {
        uuid id PK
        string name
        string carrier "SingPost|etc"
        string method_code
        text description
        decimal min_order_amount
        decimal max_order_amount
        decimal rate_sgd
        integer estimated_days_min
        integer estimated_days_max
        boolean is_active
        integer sort_order
        timestamp created_at
        timestamp updated_at
    }
Key Design Decisions
Decision	Rationale
UUIDs as Primary Keys	Security (non-guessable), distributed systems ready
Snapshot in Order Items	Preserve historical data even if products change
Guest Cart via Session ID	Enable cart persistence without forced registration
GST as Separate Column	Clear audit trail for Singapore tax compliance
Soft Currency Storage	Always store as SGD, convert at display if needed
JSON for Scent Notes	Flexible array storage without junction table
Application Flow Diagrams
User Authentication Flow
mermaid

sequenceDiagram
    autonumber
    participant U as User (Browser)
    participant N as Next.js Frontend
    participant L as Laravel API
    participant DB as PostgreSQL
    participant R as Redis (Sessions)

    Note over U,R: Registration Flow
    U->>N: Fill registration form
    N->>N: Validate with Zod
    N->>L: POST /api/v1/auth/register
    L->>L: Validate request
    L->>DB: Create user record
    L->>L: Generate Sanctum token
    L->>R: Store session
    L-->>N: 201 { user, token }
    N->>N: Store token in httpOnly cookie
    N-->>U: Redirect to account

    Note over U,R: Login Flow
    U->>N: Submit credentials
    N->>L: POST /api/v1/auth/login
    L->>DB: Verify credentials
    alt Credentials Valid
        L->>L: Generate Sanctum token
        L->>R: Store session
        L-->>N: 200 { user, token }
        N->>N: Set auth cookie
        N-->>U: Redirect to intended page
    else Credentials Invalid
        L-->>N: 401 { error: "Invalid credentials" }
        N-->>U: Show error message
    end

    Note over U,R: Authenticated Request
    U->>N: Access protected page
    N->>N: Read token from cookie
    N->>L: GET /api/v1/user (Bearer token)
    L->>L: Validate Sanctum token
    L->>DB: Fetch user data
    L-->>N: 200 { user }
    N-->>U: Render protected content

    Note over U,R: Logout Flow
    U->>N: Click logout
    N->>L: POST /api/v1/auth/logout
    L->>R: Invalidate session
    L->>DB: Delete token
    L-->>N: 200 { message: "Logged out" }
    N->>N: Clear auth cookie
    N-->>U: Redirect to home
Product Browsing to Cart Flow
mermaid

sequenceDiagram
    autonumber
    participant U as User
    participant N as Next.js
    participant Z as Zustand Store
    participant L as Laravel API
    participant DB as PostgreSQL

    Note over U,DB: Browse Compendium (Products)
    U->>N: Visit /compendium
    N->>L: GET /api/v1/products?humour=calming
    L->>DB: Query products with filters
    DB-->>L: Product results
    L-->>N: 200 { data: [...], meta: {...} }
    N->>N: Render product grid (ISR cached)
    N-->>U: Display filtered products

    Note over U,DB: View Product Detail
    U->>N: Click on "Provence Lavender"
    N->>L: GET /api/v1/products/provence-lavender
    L->>DB: Fetch product + variants
    DB-->>L: Product with variants
    L-->>N: 200 { product, variants }
    N-->>U: Display PDP with variant selector

    Note over U,DB: Add to Vial (Cart)
    U->>N: Select 15ml, click "To Vial"
    N->>Z: addToCart(variantId, qty)
    Z->>Z: Optimistic update
    N->>L: POST /api/v1/cart/items
    L->>L: Get/create cart (session or user)
    L->>DB: Check variant stock
    alt Stock Available
        L->>DB: Insert cart_item
        DB-->>L: Cart item created
        L-->>N: 201 { cart }
        Z->>Z: Confirm update
        N-->>U: Show toast "Added to vial"
        N->>N: Update cart count in header
    else Out of Stock
        L-->>N: 422 { error: "Insufficient stock" }
        Z->>Z: Rollback optimistic update
        N-->>U: Show error "Out of stock"
    end

    Note over U,DB: View Cart Drawer
    U->>N: Click cart icon
    N->>Z: Read cart state
    N-->>U: Open vial drawer with items
Checkout Flow
mermaid

sequenceDiagram
    autonumber
    participant U as User
    participant N as Next.js
    participant L as Laravel API
    participant S as Stripe
    participant SP as SingPost API
    participant DB as PostgreSQL
    participant Q as Redis Queue

    Note over U,Q: Initiate Checkout
    U->>N: Click "Dispatch to Atelier"
    N->>L: GET /api/v1/cart
    L->>DB: Validate cart items still available
    L-->>N: 200 { cart, validation }
    N-->>U: Redirect to /checkout

    Note over U,Q: Shipping Address
    U->>N: Enter Singapore address
    N->>N: Validate postal code format
    N->>L: POST /api/v1/checkout/shipping-rates
    L->>SP: Calculate shipping for postal code
    SP-->>L: Shipping options
    L-->>N: 200 { shippingRates }
    N-->>U: Display shipping options
    U->>N: Select "Standard Delivery"

    Note over U,Q: Apply Discount (Optional)
    U->>N: Enter promo code "ATELIER10"
    N->>L: POST /api/v1/checkout/apply-discount
    L->>DB: Validate discount code
    alt Valid & Not Expired
        L->>L: Calculate discount
        L-->>N: 200 { discount, newTotal }
        N-->>U: Show updated totals
    else Invalid
        L-->>N: 422 { error: "Invalid code" }
        N-->>U: Show error
    end

    Note over U,Q: Payment
    U->>N: Enter card details
    N->>S: Create PaymentMethod
    S-->>N: PaymentMethod ID
    N->>L: POST /api/v1/checkout/complete
    L->>L: Calculate final totals (incl GST 9%)
    L->>S: Create PaymentIntent
    S-->>L: PaymentIntent (requires_confirmation)
    L->>S: Confirm PaymentIntent
    
    alt Payment Successful
        S-->>L: PaymentIntent succeeded
        L->>DB: Create Order record
        L->>DB: Create OrderItems
        L->>DB: Clear cart
        L->>DB: Decrement inventory
        L->>Q: Dispatch SendOrderConfirmation job
        L-->>N: 201 { order }
        N-->>U: Redirect to /confirmation/ORD-XXXX
    else Payment Failed
        S-->>L: PaymentIntent failed
        L-->>N: 422 { error: "Payment declined" }
        N-->>U: Show payment error
    end

    Note over U,Q: Post-Order (Async)
    Q->>L: Process SendOrderConfirmation
    L->>L: Generate order email
    L->>L: Send via Resend
Order Lifecycle Flow
mermaid

stateDiagram-v2
    [*] --> Pending: Order Created
    
    Pending --> Confirmed: Payment Verified
    Pending --> Cancelled: Payment Failed / Timeout
    
    Confirmed --> Processing: Admin Acknowledges
    Confirmed --> Cancelled: Customer Requests / Admin Cancels
    
    Processing --> Shipped: Tracking Added
    Processing --> Cancelled: Fulfillment Issue
    
    Shipped --> Delivered: Delivery Confirmed
    Shipped --> Shipped: In Transit
    
    Delivered --> [*]: Order Complete
    Cancelled --> [*]: Order Closed
    
    note right of Confirmed
        Email: Order Confirmation
        Inventory: Reserved
    end note
    
    note right of Shipped
        Email: Shipping Notification
        Tracking: SingPost/Courier
    end note
    
    note right of Delivered
        Email: Delivery Confirmation
        Review Request: 7 days later
    end note
    
    note right of Cancelled
        Refund: If paid
        Inventory: Released
    end note
Admin Order Management Flow
mermaid

flowchart TD
    subgraph Dashboard["Filament Admin Dashboard"]
        A[Orders List] --> B{Order Status}
        
        B -->|Pending| C[View Details]
        B -->|Confirmed| D[Process Order]
        B -->|Shipped| E[Track Delivery]
        
        C --> F{Payment OK?}
        F -->|Yes| G[Confirm Order]
        F -->|No| H[Cancel Order]
        
        D --> I[Pick & Pack]
        I --> J[Generate Label]
        J --> K[Enter Tracking]
        K --> L[Mark Shipped]
        L --> M[Auto-email Customer]
        
        E --> N{Delivered?}
        N -->|Yes| O[Mark Delivered]
        N -->|Issue| P[Investigate]
        P --> Q{Refund?}
        Q -->|Yes| R[Process Refund]
        Q -->|No| S[Resolve Issue]
    end
    
    subgraph Automation["Background Jobs"]
        T[Abandoned Cart] --> U[Send Reminder Email]
        V[Low Stock] --> W[Alert Admin]
        X[Daily] --> Y[Generate Reports]
    end
API Route Specification
Base Configuration
text

Base URL: https://api.atelierarome.sg/api/v1
Content-Type: application/json
Authentication: Bearer token (Laravel Sanctum)
Rate Limit: 60 requests/minute (guest), 120/minute (authenticated)
Endpoint Reference
Authentication
Method	Endpoint	Description	Auth
POST	/auth/register	Create new account	No
POST	/auth/login	Authenticate user	No
POST	/auth/logout	Invalidate session	Yes
POST	/auth/forgot-password	Request reset email	No
POST	/auth/reset-password	Reset with token	No
GET	/auth/user	Get current user	Yes
PUT	/auth/user	Update profile	Yes
PUT	/auth/password	Change password	Yes
Products (Essences)
Method	Endpoint	Description	Auth
GET	/products	List all products	No
GET	/products/{slug}	Get single product	No
GET	/products/featured	Featured products	No
GET	/categories	List categories	No
GET	/categories/{slug}/products	Products by category	No
Query Parameters for /products:

TypeScript

interface ProductQueryParams {
  // Filtering
  category?: string;           // Category slug
  humour?: 'calming' | 'uplifting' | 'grounding' | 'clarifying';
  rarity?: 'common' | 'rare' | 'limited';
  season?: 'spring' | 'summer' | 'autumn' | 'winter';
  min_price?: number;
  max_price?: number;
  in_stock?: boolean;
  
  // Sorting
  sort?: 'folio' | 'name' | 'price_asc' | 'price_desc' | 'newest';
  
  // Pagination
  page?: number;
  per_page?: number;           // Default: 12, Max: 50
  
  // Search
  search?: string;             // Full-text search
}
Response Example:

JSON

{
  "data": [
    {
      "id": "01HQ7GXABC123",
      "folio_number": "I",
      "latin_name": "Lavandula × intermedia",
      "common_name": "Provence Lavender",
      "slug": "provence-lavender",
      "short_description": "Harvested at dawn in the Provençal hills...",
      "humour": {
        "key": "calming",
        "label": "Calming",
        "symbol": "☾",
        "color": "#B8A9C9"
      },
      "rarity": {
        "key": "rare",
        "label": "Rare"
      },
      "season": {
        "key": "summer",
        "label": "Early Summer"
      },
      "scent_notes": ["Floral", "Herbaceous", "Sweet"],
      "extraction_method": "Steam Distillation",
      "origin_region": "Provence, France",
      "is_featured": true,
      "category": {
        "id": "01HQ7GXDEF456",
        "name": "Singles",
        "slug": "singles"
      },
      "variants": [
        {
          "id": "01HQ7GXGHI789",
          "sku": "LAV-724-5ML",
          "size_label": "5ml",
          "size_ml": 5,
          "price": {
            "amount": 4200,
            "formatted": "$42.00",
            "currency": "SGD"
          },
          "compare_at_price": null,
          "in_stock": true,
          "stock_quantity": 24
        },
        {
          "id": "01HQ7GXJKL012",
          "sku": "LAV-724-15ML",
          "size_label": "15ml",
          "size_ml": 15,
          "price": {
            "amount": 9800,
            "formatted": "$98.00",
            "currency": "SGD"
          },
          "compare_at_price": null,
          "in_stock": true,
          "stock_quantity": 12
        }
      ],
      "images": [
        {
          "id": "img_001",
          "url": "https://cdn.atelierarome.sg/products/lavender-main.jpg",
          "alt": "Provence Lavender essence phial",
          "is_primary": true
        }
      ],
      "created_at": "2024-01-15T10:30:00Z"
    }
  ],
  "meta": {
    "current_page": 1,
    "per_page": 12,
    "total": 24,
    "total_pages": 2,
    "has_more": true
  },
  "links": {
    "first": "/api/v1/products?page=1",
    "next": "/api/v1/products?page=2",
    "prev": null,
    "last": "/api/v1/products?page=2"
  }
}
Cart (Vial)
Method	Endpoint	Description	Auth
GET	/cart	Get current cart	No*
POST	/cart/items	Add item to cart	No*
PUT	/cart/items/{id}	Update item quantity	No*
DELETE	/cart/items/{id}	Remove item	No*
DELETE	/cart	Clear entire cart	No*
POST	/cart/merge	Merge guest cart to user	Yes
*Guest carts use session ID; authenticated carts use user ID.

Add to Cart Request:

JSON

{
  "variant_id": "01HQ7GXGHI789",
  "quantity": 1
}
Cart Response:

JSON

{
  "data": {
    "id": "cart_01HQ7GXMNO345",
    "items": [
      {
        "id": "ci_01HQ7GXPQR678",
        "variant": {
          "id": "01HQ7GXGHI789",
          "sku": "LAV-724-5ML",
          "size_label": "5ml",
          "product": {
            "common_name": "Provence Lavender",
            "latin_name": "Lavandula × intermedia",
            "slug": "provence-lavender",
            "humour": {
              "key": "calming",
              "symbol": "☾",
              "label": "Calming"
            },
            "image": {
              "url": "https://cdn.atelierarome.sg/products/lavender-thumb.jpg",
              "alt": "Provence Lavender"
            }
          }
        },
        "quantity": 2,
        "unit_price": {
          "amount": 4200,
          "formatted": "$42.00"
        },
        "line_total": {
          "amount": 8400,
          "formatted": "$84.00"
        }
      }
    ],
    "item_count": 2,
    "subtotal": {
      "amount": 8400,
      "formatted": "$84.00",
      "currency": "SGD"
    },
    "expires_at": "2024-02-01T10:30:00Z"
  }
}
Checkout
Method	Endpoint	Description	Auth
POST	/checkout/validate	Validate cart for checkout	No
POST	/checkout/shipping-rates	Get shipping options	No
POST	/checkout/apply-discount	Apply promo code	No
DELETE	/checkout/remove-discount	Remove promo code	No
POST	/checkout/complete	Complete order	No
Complete Checkout Request:

JSON

{
  "email": "customer@example.com",
  "shipping_address": {
    "recipient_name": "Jane Doe",
    "phone": "+6591234567",
    "address_line_1": "123 Orchard Road",
    "address_line_2": "#10-05 Luxury Towers",
    "postal_code": "238858",
    "city": "Singapore",
    "country_code": "SG"
  },
  "billing_same_as_shipping": true,
  "shipping_method": "singpost_standard",
  "payment_method_id": "pm_1234567890",
  "discount_code": "ATELIER10",
  "notes": "Please gift wrap",
  "newsletter_opt_in": true
}
Checkout Response:

JSON

{
  "data": {
    "order": {
      "id": "01HQ7GXSTU901",
      "order_number": "ORD-2024-00142",
      "status": "confirmed",
      "payment_status": "paid",
      "email": "customer@example.com",
      "shipping_address": {...},
      "items": [...],
      "subtotal": {"amount": 8400, "formatted": "$84.00"},
      "discount": {"code": "ATELIER10", "amount": 840, "formatted": "-$8.40"},
      "shipping": {"method": "Standard Delivery", "amount": 500, "formatted": "$5.00"},
      "tax": {"rate": 0.09, "label": "GST 9%", "amount": 685, "formatted": "$6.85"},
      "total": {"amount": 8345, "formatted": "$83.45", "currency": "SGD"},
      "created_at": "2024-01-20T14:30:00Z"
    },
    "confirmation_url": "/confirmation/ORD-2024-00142"
  }
}
Orders
Method	Endpoint	Description	Auth
GET	/orders	List user's orders	Yes
GET	/orders/{orderNumber}	Get order details	Yes
GET	/orders/{orderNumber}/invoice	Download invoice PDF	Yes
Addresses
Method	Endpoint	Description	Auth
GET	/addresses	List saved addresses	Yes
POST	/addresses	Create new address	Yes
PUT	/addresses/{id}	Update address	Yes
DELETE	/addresses/{id}	Delete address	Yes
POST	/addresses/{id}/default	Set as default	Yes
Wishlist (Bookmarks)
Method	Endpoint	Description	Auth
GET	/wishlist	Get bookmarked products	Yes
POST	/wishlist	Add product to wishlist	Yes
DELETE	/wishlist/{productId}	Remove from wishlist	Yes
Testimonials (Manuscript)
Method	Endpoint	Description	Auth
GET	/testimonials	List approved testimonials	No
Newsletter (Correspondence)
Method	Endpoint	Description	Auth
POST	/newsletter/subscribe	Subscribe to newsletter	No
POST	/newsletter/unsubscribe	Unsubscribe	No
Component Architecture
Design System Mapping
text

SHADCN PRIMITIVE          →    ATELIER COMPONENT         →    USAGE
─────────────────────          ──────────────────             ─────

Button                    →    btn--primary                   CTAs, actions
                               btn--secondary                 Secondary actions
                               btn--outline                   Tertiary actions
                               essence-card__action           Add to cart

Sheet                     →    VialDrawer                     Cart drawer

Dialog                    →    QuickViewModal                 Product quick view
                               ConfirmationDialog             Delete confirmations

Card                      →    EssenceCard                    Product cards
                               ManuscriptEntry                Testimonials
                               AlchemyStep                    Process steps

Select                    →    CompendiumSort                 Product sorting
                               VariantSelector                Size picker

RadioGroup                →    ShippingOptions                Shipping selection
                               PaymentMethods                 Payment type

Input + Label             →    CorrespondenceField            Styled form inputs

Checkbox                  →    ConsentCheckbox                Newsletter consent

Toast                     →    AtelierToast                   Wax-sealed notifications

Badge                     →    HumourBadge                    ☾ Calming badges
                               RarityBadge                    "Rare" / "Limited"

Skeleton                  →    EssenceCardSkeleton            Loading states
                               ManuscriptSkeleton

NavigationMenu            →    HeaderNav                      Desktop navigation

Accordion                 →    ProductFAQ                     FAQ on PDP
                               CheckoutSummary                Mobile order summary

Tabs                      →    AccountTabs                    Account navigation

Pagination                →    ManuscriptPagination           Testimonial pages
                               CompendiumPagination           Product pages

ScrollArea                →    VialDrawerContent              Cart scroll

Form                      →    All forms                      RHF integration
Component Hierarchy
text

App
├── RootLayout
│   ├── Providers (QueryClient, Auth, Theme)
│   ├── TextureOverlay
│   ├── GoldLeafAccents
│   └── Toaster
│
├── StorefrontLayout
│   ├── AtelierBanner
│   ├── Header
│   │   ├── HeaderSeal (Logo)
│   │   ├── HeaderNav
│   │   │   └── NavItem × 4
│   │   └── HeaderTools
│   │       ├── SearchButton
│   │       ├── CartButton (with count)
│   │       └── MobileMenuToggle
│   ├── MobileNav (Sheet)
│   ├── VialDrawer (Sheet)
│   │   ├── CartItem × n
│   │   │   ├── ProductInfo
│   │   │   ├── QuantitySelector
│   │   │   └── RemoveButton
│   │   ├── CartSummary
│   │   └── DispatchButton
│   ├── Main (children)
│   ├── BackToTop
│   └── Colophon (Footer)
│
├── HomePage
│   ├── HeroSection
│   │   ├── HeroBorder
│   │   ├── IlluminatedInitial
│   │   ├── HeroContent
│   │   │   ├── HeroTitle
│   │   │   ├── HeroSubtitle
│   │   │   ├── HeroExcerpt
│   │   │   ├── HeroActions
│   │   │   └── HeroCredentials
│   │   ├── HeroVisual
│   │   │   ├── VesselContainer
│   │   │   │   ├── Vessel (animated)
│   │   │   │   └── Botanicals (parallax)
│   │   │   └── AlchemicalSymbol
│   │   └── ScrollIndicator
│   │
│   ├── CompendiumSection (Featured)
│   │   ├── SectionHeader
│   │   └── EssenceGrid
│   │       └── EssenceCard × n
│   │
│   ├── AlchemySection
│   │   ├── SectionHeader
│   │   ├── AlchemyStep × 4
│   │   └── ApparatusGrid
│   │
│   ├── ManuscriptSection
│   │   ├── SectionHeader
│   │   ├── ManuscriptEntry × 3
│   │   └── ManuscriptPagination
│   │
│   └── CorrespondenceSection
│       ├── CorrespondenceContent
│       ├── CorrespondenceForm
│       └── CorrespondenceVisual
│
├── CompendiumPage
│   ├── SectionHeader
│   ├── FilterBar
│   │   ├── HumourFilters
│   │   └── SortSelect
│   ├── EssenceGrid
│   │   └── EssenceCard × n
│   ├── LoadMoreButton
│   └── CompendiumCounter
│
├── ProductDetailPage
│   ├── Breadcrumbs
│   ├── ProductGrid
│   │   ├── ProductGallery
│   │   │   ├── MainImage
│   │   │   └── Thumbnails
│   │   └── ProductInfo
│   │       ├── LatinName
│   │       ├── CommonName
│   │       ├── HumourBadge
│   │       ├── Description
│   │       ├── ScentNotes
│   │       ├── ExtractionDetails
│   │       ├── VariantSelector
│   │       ├── PriceDisplay
│   │       ├── AddToVialButton
│   │       └── WishlistButton
│   ├── ProductTabs
│   │   ├── DetailsTab
│   │   ├── IngredientsTab
│   │   └── UsageTab
│   └── RelatedProducts
│
├── CheckoutFlow
│   ├── CheckoutLayout (minimal header)
│   ├── VialPage
│   │   ├── CartItems
│   │   ├── DiscountInput
│   │   ├── CartSummary
│   │   └── ProceedButton
│   ├── ShippingPage
│   │   ├── AddressForm
│   │   └── ShippingOptions
│   ├── PaymentPage
│   │   ├── PaymentForm (Stripe Elements)
│   │   └── OrderSummary
│   └── ConfirmationPage
│       ├── OrderConfirmation
│       ├── OrderDetails
│       └── NextSteps
│
└── AccountPages
    ├── AccountLayout (sidebar)
    ├── OrdersPage
    │   └── OrderCard × n
    ├── OrderDetailPage
    │   ├── OrderStatus
    │   ├── OrderItems
    │   └── OrderActions
    ├── AddressesPage
    │   ├── AddressCard × n
    │   └── AddressForm (modal)
    ├── BookmarksPage
    │   └── BookmarkCard × n
    └── SettingsPage
        ├── ProfileForm
        └── PasswordForm
State Management Strategy
Overview
text

┌─────────────────────────────────────────────────────────────────────────────┐
│                          STATE MANAGEMENT LAYERS                            │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   SERVER STATE (TanStack Query)                                            │
│   ───────────────────────────────                                          │
│   • Products, categories, testimonials                                      │
│   • Orders, addresses, wishlist                                            │
│   • User profile data                                                       │
│   • Automatic caching, background refetch, stale-while-revalidate          │
│                                                                             │
│   CLIENT STATE (Zustand)                                                   │
│   ──────────────────────                                                   │
│   • Cart (with localStorage persistence)                                    │
│   • UI state (drawer open, mobile nav, filters)                            │
│   • Checkout form progress                                                  │
│                                                                             │
│   FORM STATE (React Hook Form + Zod)                                       │
│   ────────────────────────────────────                                     │
│   • All user input forms                                                    │
│   • Validation schemas                                                      │
│   • Error handling                                                          │
│                                                                             │
│   URL STATE (Next.js searchParams)                                         │
│   ────────────────────────────────                                         │
│   • Product filters (humour, rarity, season)                               │
│   • Sort order                                                              │
│   • Pagination                                                              │
│   • Search query                                                            │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
Zustand Store: Cart
TypeScript

// src/stores/cart-store.ts
import { create } from 'zustand';
import { persist, createJSONStorage } from 'zustand/middleware';
import type { CartItem, Cart } from '@/types';

interface CartState {
  // State
  items: CartItem[];
  isLoading: boolean;
  isHydrated: boolean;
  
  // Computed
  itemCount: number;
  subtotal: number;
  
  // Actions
  addItem: (variantId: string, quantity?: number) => Promise<void>;
  updateQuantity: (itemId: string, quantity: number) => Promise<void>;
  removeItem: (itemId: string) => Promise<void>;
  clearCart: () => Promise<void>;
  syncWithServer: () => Promise<void>;
  setHydrated: () => void;
}

export const useCartStore = create<CartState>()(
  persist(
    (set, get) => ({
      items: [],
      isLoading: false,
      isHydrated: false,
      
      get itemCount() {
        return get().items.reduce((sum, item) => sum + item.quantity, 0);
      },
      
      get subtotal() {
        return get().items.reduce(
          (sum, item) => sum + item.unitPrice * item.quantity,
          0
        );
      },
      
      addItem: async (variantId, quantity = 1) => {
        set({ isLoading: true });
        
        // Optimistic update
        const existingItem = get().items.find(
          item => item.variant.id === variantId
        );
        
        if (existingItem) {
          set(state => ({
            items: state.items.map(item =>
              item.variant.id === variantId
                ? { ...item, quantity: item.quantity + quantity }
                : item
            ),
          }));
        } else {
          // Fetch variant data and add
          // ... API call
        }
        
        try {
          // Sync with server
          await api.cart.addItem(variantId, quantity);
        } catch (error) {
          // Rollback on failure
          // ... restore previous state
        } finally {
          set({ isLoading: false });
        }
      },
      
      updateQuantity: async (itemId, quantity) => {
        // Similar optimistic pattern
      },
      
      removeItem: async (itemId) => {
        // Similar optimistic pattern
      },
      
      clearCart: async () => {
        set({ items: [], isLoading: false });
        await api.cart.clear();
      },
      
      syncWithServer: async () => {
        const serverCart = await api.cart.get();
        set({ items: serverCart.items });
      },
      
      setHydrated: () => set({ isHydrated: true }),
    }),
    {
      name: 'atelier-cart',
      storage: createJSONStorage(() => localStorage),
      onRehydrateStorage: () => (state) => {
        state?.setHydrated();
      },
    }
  )
);
TanStack Query: Products
TypeScript

// src/hooks/use-products.ts
import { useQuery, useInfiniteQuery } from '@tanstack/react-query';
import { api } from '@/lib/api/client';
import type { Product, ProductQueryParams } from '@/types';

export const productKeys = {
  all: ['products'] as const,
  lists: () => [...productKeys.all, 'list'] as const,
  list: (params: ProductQueryParams) =>
    [...productKeys.lists(), params] as const,
  details: () => [...productKeys.all, 'detail'] as const,
  detail: (slug: string) => [...productKeys.details(), slug] as const,
  featured: () => [...productKeys.all, 'featured'] as const,
};

export function useProducts(params: ProductQueryParams) {
  return useInfiniteQuery({
    queryKey: productKeys.list(params),
    queryFn: ({ pageParam = 1 }) =>
      api.products.list({ ...params, page: pageParam }),
    getNextPageParam: (lastPage) =>
      lastPage.meta.has_more ? lastPage.meta.current_page + 1 : undefined,
    staleTime: 5 * 60 * 1000, // 5 minutes
  });
}

export function useProduct(slug: string) {
  return useQuery({
    queryKey: productKeys.detail(slug),
    queryFn: () => api.products.get(slug),
    staleTime: 10 * 60 * 1000, // 10 minutes
  });
}

export function useFeaturedProducts() {
  return useQuery({
    queryKey: productKeys.featured(),
    queryFn: () => api.products.featured(),
    staleTime: 15 * 60 * 1000, // 15 minutes
  });
}
Authentication & Authorization
Laravel Sanctum Configuration
PHP

// config/sanctum.php
return [
    'stateful' => explode(',', env('SANCTUM_STATEFUL_DOMAINS', sprintf(
        '%s%s',
        'localhost,localhost:3000,127.0.0.1,127.0.0.1:8000,::1',
        env('APP_URL') ? ','.parse_url(env('APP_URL'), PHP_URL_HOST) : ''
    ))),
    
    'expiration' => 60 * 24 * 7, // 7 days
    
    'middleware' => [
        'verify_csrf_token' => \App\Http\Middleware\VerifyCsrfToken::class,
        'encrypt_cookies' => \App\Http\Middleware\EncryptCookies::class,
    ],
];
Role-Based Access
PHP

// app/Enums/UserRole.php
enum UserRole: string
{
    case Customer = 'customer';
    case Admin = 'admin';
}

// app/Models/User.php
class User extends Authenticatable
{
    public function isAdmin(): bool
    {
        return $this->role === UserRole::Admin;
    }
    
    public function isCustomer(): bool
    {
        return $this->role === UserRole::Customer;
    }
}

// Middleware for admin routes
class EnsureIsAdmin
{
    public function handle(Request $request, Closure $next)
    {
        if (!$request->user()?->isAdmin()) {
            abort(403, 'Unauthorized');
        }
        return $next($request);
    }
}
API Route Protection
PHP

// routes/api.php
Route::prefix('v1')->group(function () {
    // Public routes
    Route::get('/products', [ProductController::class, 'index']);
    Route::get('/products/{slug}', [ProductController::class, 'show']);
    Route::get('/categories', [CategoryController::class, 'index']);
    Route::get('/testimonials', [TestimonialController::class, 'index']);
    Route::post('/newsletter/subscribe', [NewsletterController::class, 'subscribe']);
    
    // Guest cart routes (session-based)
    Route::prefix('cart')->group(function () {
        Route::get('/', [CartController::class, 'show']);
        Route::post('/items', [CartController::class, 'addItem']);
        Route::put('/items/{id}', [CartController::class, 'updateItem']);
        Route::delete('/items/{id}', [CartController::class, 'removeItem']);
    });
    
    // Checkout (guest or authenticated)
    Route::prefix('checkout')->group(function () {
        Route::post('/validate', [CheckoutController::class, 'validate']);
        Route::post('/shipping-rates', [CheckoutController::class, 'shippingRates']);
        Route::post('/apply-discount', [CheckoutController::class, 'applyDiscount']);
        Route::post('/complete', [CheckoutController::class, 'complete']);
    });
    
    // Authentication
    Route::prefix('auth')->group(function () {
        Route::post('/register', [AuthController::class, 'register']);
        Route::post('/login', [AuthController::class, 'login']);
        Route::post('/forgot-password', [AuthController::class, 'forgotPassword']);
        Route::post('/reset-password', [AuthController::class, 'resetPassword']);
        
        Route::middleware('auth:sanctum')->group(function () {
            Route::get('/user', [AuthController::class, 'user']);
            Route::put('/user', [AuthController::class, 'updateProfile']);
            Route::put('/password', [AuthController::class, 'updatePassword']);
            Route::post('/logout', [AuthController::class, 'logout']);
        });
    });
    
    // Protected customer routes
    Route::middleware('auth:sanctum')->group(function () {
        Route::post('/cart/merge', [CartController::class, 'merge']);
        
        Route::apiResource('addresses', AddressController::class);
        Route::post('/addresses/{id}/default', [AddressController::class, 'setDefault']);
        
        Route::get('/orders', [OrderController::class, 'index']);
        Route::get('/orders/{orderNumber}', [OrderController::class, 'show']);
        Route::get('/orders/{orderNumber}/invoice', [OrderController::class, 'invoice']);
        
        Route::get('/wishlist', [WishlistController::class, 'index']);
        Route::post('/wishlist', [WishlistController::class, 'store']);
        Route::delete('/wishlist/{productId}', [WishlistController::class, 'destroy']);
    });
    
    // Webhook (no auth, signature verification)
    Route::post('/webhooks/stripe', [StripeWebhookController::class, 'handle'])
        ->middleware(VerifyStripeSignature::class);
});
Payment Integration Blueprint
Stripe Configuration
PHP

// config/payments.php
return [
    'stripe' => [
        'key' => env('STRIPE_KEY'),
        'secret' => env('STRIPE_SECRET'),
        'webhook_secret' => env('STRIPE_WEBHOOK_SECRET'),
        'currency' => 'sgd',
        'payment_methods' => [
            'card',
            'grabpay',    // GrabPay (Singapore)
            'paynow',     // PayNow (Singapore bank transfer)
        ],
    ],
    
    'tax' => [
        'gst_rate' => 0.09, // 9% GST for Singapore
        'gst_label' => 'GST',
    ],
];
Payment Service
PHP

// app/Services/PaymentService.php
class PaymentService
{
    public function __construct(
        private StripeClient $stripe
    ) {}
    
    public function createPaymentIntent(Order $order): PaymentIntent
    {
        return 
