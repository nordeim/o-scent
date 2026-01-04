# Analysis Complete — Awaiting CSS, Then Presenting Architecture

---

I've thoroughly analyzed `index.html` and `main.js`. Before you share `styles.css`, let me demonstrate my deep understanding of this project and surface critical architectural decisions that require your input.

---

## What I've Extracted from the Mockup

### Brand & Aesthetic DNA

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  ATELIER ARÔME — DESIGN SYSTEM ANALYSIS                                     │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  AESTHETIC DIRECTION                                                        │
│  ─────────────────────                                                      │
│  Primary:    Refined Luxury × Editorial Manuscript                          │
│  Secondary:  Renaissance Alchemical / Botanical Illustration                │
│  Tone:       Poetic, Artisanal, Unhurried, Ceremonial                       │
│                                                                             │
│  TYPOGRAPHY HIERARCHY                                                       │
│  ─────────────────────                                                      │
│  Display:    Cormorant Garamond (300-700, italic)                          │
│  Body:       Crimson Pro (300-700, italic)                                  │
│  Accent:     Great Vibes (script flourishes)                                │
│  Editorial:  Playfair Display (headings)                                    │
│                                                                             │
│  VISUAL MOTIFS                                                              │
│  ─────────────────────                                                      │
│  • Gold leaf accents (floating, parallax)                                   │
│  • Parchment/manuscript textures                                            │
│  • Hand-drawn botanical SVGs                                                │
│  • Wax seals (authentication, CTAs)                                         │
│  • Illuminated initials (drop caps)                                         │
│  • Alchemical symbols (☾ ☀ ♁ ☁)                                             │
│  • Roman numeral folio numbering                                            │
│                                                                             │
│  COLOR INFERENCE (from markup)                                              │
│  ─────────────────────                                                      │
│  Ink:        Deep olive/charcoal (#2A2D26 from favicon)                     │
│  Gold:       Muted antique gold (#C9A769 from favicon)                      │
│  Paper:      Warm parchment (likely cream/off-white)                        │
│  Accents:    Botanical-derived (lavender, bergamot, eucalyptus)             │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Current Feature Inventory

| Section | Semantic Name | E-Commerce Function | Complexity |
|---------|---------------|---------------------|------------|
| Hero | Illuminated Opening | Landing / Brand Story | Low |
| Compendium | Product Catalog | Filterable product grid | High |
| Alchemy | Process / About | Trust-building content | Low |
| Manuscript | Testimonials | Social proof (paginated) | Medium |
| Correspondence | Newsletter | Email capture | Medium |
| Vial Drawer | Shopping Cart | Slide-out cart | High |
| Colophon | Footer | Navigation + Contact | Low |

### JavaScript Architecture Analysis

Your `main.js` reveals a **well-structured vanilla JS** foundation:

```
STATE MANAGEMENT          CART SYSTEM              ACCESSIBILITY
─────────────────         ────────────             ─────────────
• Centralized State       • LocalStorage persist   • Focus trapping
• Event dispatching       • Quantity controls      • ARIA live regions
• URL state sync          • Add/remove/update      • Reduced motion
                          • MAX 12 items           • Screen reader announces
                          
FILTERING/SORTING         ANIMATIONS               UTILITIES
─────────────────         ──────────               ─────────
• Humour-based filter     • IntersectionObserver   • Debounce/throttle
• Multi-sort options      • Parallax effects       • Smooth scroll
• Lazy loading ("3 of 12")• CSS class helpers      • Currency formatting
```

---

## Architectural Decisions Requiring Your Input

Before I produce the comprehensive architecture document, I need to validate my assumptions:

### 1. Technology Stack Selection

Given your expertise, I'm proposing:

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  RECOMMENDED STACK: NEXT.JS 15 FULL-STACK                                   │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  FRONTEND                           BACKEND                                 │
│  ────────                           ───────                                 │
│  • Next.js 15 (App Router)          • Next.js API Routes                   │
│  • React 19                         • Prisma ORM                            │
│  • TypeScript 5.x                   • PostgreSQL (Supabase/Neon)           │
│  • Tailwind CSS 4.0                 • NextAuth.js v5                       │
│  • Shadcn-UI (Radix primitives)     • Stripe SDK                           │
│  • Framer Motion (animations)       • Resend (transactional email)         │
│                                     • Cloudinary (image CDN)               │
│                                                                             │
│  DEPLOYMENT                         SINGAPORE-SPECIFIC                      │
│  ──────────                         ─────────────────                       │
│  • Vercel (Edge Network)            • GST 9% calculation                   │
│  • Supabase (DB + Auth optional)    • PayNow / GrabPay integration         │
│  • Cloudflare (DNS + CDN backup)    • SingPost API                          │
│                                     • SGD currency                          │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

**Alternative Consideration**: If you prefer **Laravel 12** backend with Next.js frontend (headless), I can architect that instead. This provides:
- Laravel's mature e-commerce packages (Lunar, Vanilo)
- Robust admin panel (Filament)
- Queue system for order processing

**Question**: Do you want **monolithic Next.js** or **Laravel API + Next.js frontend**?

---

### 2. E-Commerce Scope Clarification

Based on the mockup, I'm expanding to full production e-commerce:

```
CURRENT MOCKUP                    →    PRODUCTION EXPANSION
──────────────                         ────────────────────

Static product cards              →    Dynamic product pages with variants
                                       (sizes: 5ml, 15ml, 30ml phials)
                                       
Humour filter only                →    Full taxonomy:
                                       • Categories (Singles, Blends, Sets)
                                       • Humours (calming, uplifting, etc.)
                                       • Seasons
                                       • Rarity
                                       
LocalStorage cart                 →    Server-side cart (persists across devices)
                                       Guest + authenticated checkout
                                       
No checkout                       →    Multi-step checkout:
                                       • Cart review
                                       • Shipping (SG addresses)
                                       • Payment (Stripe + PayNow)
                                       • Confirmation + order tracking
                                       
No user accounts                  →    Full auth:
                                       • Email/password
                                       • Social (Google)
                                       • Order history
                                       • Saved addresses
                                       • Wishlist ("Bookmarked Essences")
                                       
No admin                          →    Admin dashboard:
                                       • Product CRUD
                                       • Order management
                                       • Customer database
                                       • Inventory tracking
                                       • Analytics
```

**Question**: Confirm this scope expansion is correct?

---

### 3. Payment Gateway Priority

For Singapore SME:

| Gateway | Priority | Use Case |
|---------|----------|----------|
| **Stripe** | Primary | Credit cards, Apple Pay, Google Pay |
| **PayNow** | Secondary | Local bank transfers (via Stripe or HitPay) |
| **GrabPay** | Optional | Mobile wallet users |

**Question**: Stripe as primary, or do you have an existing payment provider?

---

### 4. Design System Preservation

Your mockup has **exceptionally distinctive aesthetics**. My architecture will preserve:

```
WHAT I WILL PRESERVE                  HOW I'LL IMPLEMENT
────────────────────                  ──────────────────

Manuscript typography                 Extended Tailwind theme with custom
                                      font utilities (@font-face optimized)
                                      
Gold leaf parallax effects            Framer Motion + CSS custom properties
                                      with reduced-motion respect
                                      
Illuminated card design               Shadcn Card primitive + custom variants
                                      (essence-card, manuscript-entry)
                                      
Wax seal motifs                       SVG components with animation states
                                      
Botanical illustrations               Inline SVGs with CSS-driven theming
                                      
Vial drawer (cart)                    Shadcn Sheet + custom styling
                                      (preserving current UX exactly)
```

---

## What I'm Preparing

Once you share `styles.css` and confirm the above decisions, I'll deliver:

### 📄 Comprehensive Project Architecture Document

```
DOCUMENT STRUCTURE
──────────────────

1. EXECUTIVE SUMMARY
   └── Project vision, stack rationale, Singapore market considerations

2. TECHNOLOGY STACK SPECIFICATION
   └── Versions, packages, compatibility matrix

3. FILE HIERARCHY DIAGRAM
   └── Complete src/ structure with 100+ files annotated
   └── Each file: purpose, key exports, dependencies

4. DATABASE SCHEMA (Mermaid ERD)
   └── Users, Products, Orders, Inventory, Addresses, etc.
   └── Singapore-specific: GST, PayNow references

5. APPLICATION FLOW DIAGRAMS (Mermaid)
   └── User authentication flow
   └── Product browsing → Cart → Checkout
   └── Order processing lifecycle
   └── Admin workflows

6. API ROUTE SPECIFICATION
   └── RESTful endpoints with request/response shapes
   └── Authentication middleware patterns

7. COMPONENT ARCHITECTURE
   └── Atomic design mapping to Shadcn primitives
   └── Custom component specifications (EssenceCard, VialDrawer, etc.)

8. STATE MANAGEMENT STRATEGY
   └── Server state (TanStack Query)
   └── Client state (Zustand)
   └── Form state (React Hook Form)

9. AUTHENTICATION & AUTHORIZATION
   └── NextAuth.js configuration
   └── Role-based access (Customer, Admin)

10. PAYMENT INTEGRATION BLUEPRINT
    └── Stripe implementation
    └── Webhook handling
    └── Singapore payment methods

11. DEPLOYMENT & DEVOPS
    └── Environment configuration
    └── CI/CD pipeline
    └── Monitoring & logging

12. DEVELOPMENT PHASES & TIMELINE
    └── Phase breakdown with deliverables
    └── Dependency graph
```

---

## Ready for CSS

Please share `styles.css`. Once received, I'll:

1. Extract the complete color system and design tokens
2. Map CSS custom properties to Tailwind theme extensions
3. Identify animation keyframes for Framer Motion conversion
4. Document the responsive breakpoint strategy
5. Produce the full architecture document

---

Project Architecture Document
Atelier Arôme — Singapore E-Commerce Platform
Executive Summary
This document specifies the complete technical architecture for Atelier Arôme, a production-grade e-commerce platform for a Singapore-based artisanal aromatherapy company. The system employs a decoupled architecture: Laravel 12 as a headless API backend with Next.js 15 as the frontend, preserving the distinctive Renaissance manuscript aesthetic while delivering enterprise-grade e-commerce capabilities.

Table of Contents
Technology Stack Specification
System Architecture Overview
File Hierarchy — Laravel Backend
File Hierarchy — Next.js Frontend
Database Schema
Application Flow Diagrams
API Specification
Component Architecture
State Management Strategy
Authentication & Authorization
Payment Integration
Deployment Architecture
Development Phases
1. Technology Stack Specification
1.1 Backend Stack (Laravel 12)
Layer	Technology	Version	Purpose
Runtime	PHP	8.3+	Language runtime
Framework	Laravel	12.x	API framework
Database	PostgreSQL	16.x	Primary datastore
Cache	Redis	7.x	Session, cache, queues
Search	Meilisearch	1.6+	Product search
Queue	Laravel Horizon	5.x	Queue management
Admin Panel	Filament	3.x	Admin interface
API Docs	Scramble	0.11+	OpenAPI generation
Media	Spatie Media Library	11.x	Image management
Auth	Laravel Sanctum	4.x	API authentication
Payments	Stripe PHP SDK	13.x	Payment processing
Email	Resend	0.10+	Transactional email
1.2 Frontend Stack (Next.js 15)
Layer	Technology	Version	Purpose
Framework	Next.js	15.x	React meta-framework
React	React	19.x	UI library
Language	TypeScript	5.x	Type safety
Styling	Tailwind CSS	4.0	Utility-first CSS
Components	Shadcn/UI	latest	Radix primitives
Animation	Framer Motion	11.x	Declarative animations
State	Zustand	5.x	Client state
Server State	TanStack Query	5.x	Data fetching
Forms	React Hook Form	7.x	Form management
Validation	Zod	3.x	Schema validation
Icons	Lucide React	latest	Icon system
1.3 Infrastructure
Component	Technology	Purpose
Frontend Hosting	Vercel	Edge deployment
Backend Hosting	Laravel Forge / Render	PHP hosting
Database	Supabase / Neon	Managed PostgreSQL
File Storage	Cloudflare R2	S3-compatible CDN
Email	Resend	Transactional email
Monitoring	Sentry	Error tracking
Analytics	Plausible	Privacy-focused analytics
1.4 Singapore-Specific Integrations
Integration	Purpose	Provider
GST Calculation	9% tax computation	Built-in
PayNow	Local bank transfers	Stripe / HitPay
GrabPay	Mobile wallet	Stripe
Shipping	Domestic delivery	EasyParcel API
Address	SG address validation	OneMap API
2. System Architecture Overview
text

┌─────────────────────────────────────────────────────────────────────────────┐
│                           ATELIER ARÔME ARCHITECTURE                        │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │                         FRONTEND (Next.js 15)                        │   │
│  │                         Vercel Edge Network                          │   │
│  ├─────────────────────────────────────────────────────────────────────┤   │
│  │                                                                       │   │
│  │   ┌───────────┐  ┌───────────┐  ┌───────────┐  ┌───────────┐        │   │
│  │   │  Storefront │  │  Product  │  │  Checkout │  │  Account  │        │   │
│  │   │   Pages    │  │   Pages   │  │   Flow    │  │   Area    │        │   │
│  │   └─────┬─────┘  └─────┬─────┘  └─────┬─────┘  └─────┬─────┘        │   │
│  │         │              │              │              │               │   │
│  │         └──────────────┴──────────────┴──────────────┘               │   │
│  │                              │                                        │   │
│  │                   ┌──────────┴──────────┐                            │   │
│  │                   │   TanStack Query    │                            │   │
│  │                   │   + Zustand Store   │                            │   │
│  │                   └──────────┬──────────┘                            │   │
│  │                              │                                        │   │
│  └──────────────────────────────┼────────────────────────────────────────┘   │
│                                 │ HTTPS/REST                                │
│  ┌──────────────────────────────┼────────────────────────────────────────┐   │
│  │                              ▼                                        │   │
│  │                    BACKEND (Laravel 12)                              │   │
│  │                    Laravel Forge / Render                            │   │
│  ├─────────────────────────────────────────────────────────────────────┤   │
│  │                                                                       │   │
│  │   ┌─────────────────────────────────────────────────────────────┐   │   │
│  │   │                    API Gateway (Sanctum)                     │   │   │
│  │   └─────────────────────────────────────────────────────────────┘   │   │
│  │                              │                                        │   │
│  │   ┌──────────┬───────────┬──┴──────────┬─────────────┬────────────┐ │   │
│  │   │          │           │             │             │            │ │   │
│  │   ▼          ▼           ▼             ▼             ▼            │ │   │
│  │ ┌────────┐ ┌────────┐ ┌────────┐ ┌──────────┐ ┌──────────┐       │ │   │
│  │ │Products│ │ Orders │ │  Auth  │ │ Payments │ │ Shipping │       │ │   │
│  │ │ Module │ │ Module │ │ Module │ │  Module  │ │  Module  │       │ │   │
│  │ └───┬────┘ └───┬────┘ └───┬────┘ └────┬─────┘ └────┬─────┘       │ │   │
│  │     │          │          │           │            │              │ │   │
│  │     └──────────┴──────────┴───────────┴────────────┘              │ │   │
│  │                              │                                     │ │   │
│  │   ┌──────────────────────────┴──────────────────────────┐         │ │   │
│  │   │              Eloquent ORM + Repository Layer         │         │ │   │
│  │   └──────────────────────────┬──────────────────────────┘         │ │   │
│  │                              │                                     │ │   │
│  └──────────────────────────────┼─────────────────────────────────────┘ │   │
│                                 │                                        │
│  ┌──────────────────────────────┼────────────────────────────────────────┐   │
│  │                              ▼                                        │   │
│  │   ┌────────────┐  ┌────────────┐  ┌────────────┐  ┌────────────┐    │   │
│  │   │ PostgreSQL │  │   Redis    │  │ Meilisearch│  │Cloudflare R2│    │   │
│  │   │  Database  │  │   Cache    │  │   Search   │  │   Storage  │    │   │
│  │   └────────────┘  └────────────┘  └────────────┘  └────────────┘    │   │
│  │                        DATA LAYER                                    │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │                      EXTERNAL SERVICES                               │   │
│  ├─────────────────────────────────────────────────────────────────────┤   │
│  │  ┌─────────┐  ┌─────────┐  ┌─────────┐  ┌─────────┐  ┌─────────┐  │   │
│  │  │ Stripe  │  │ Resend  │  │EasyParcel│  │ Sentry  │  │Plausible│  │   │
│  │  │Payments │  │  Email  │  │ Shipping │  │ Errors  │  │Analytics│  │   │
│  │  └─────────┘  └─────────┘  └─────────┘  └─────────┘  └─────────┘  │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │                      ADMIN PANEL (Filament 3)                        │   │
│  │                      Same Laravel Instance                           │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
3. File Hierarchy — Laravel Backend
text

atelier-arome-api/
├── .env.example                    # Environment template
├── .env.testing                    # Test environment
├── composer.json                   # PHP dependencies
├── phpunit.xml                     # Test configuration
├── docker-compose.yml              # Local development
├── Dockerfile                      # Production container
│
├── app/
│   ├── Console/
│   │   └── Commands/
│   │       ├── SyncSearchIndex.php         # Meilisearch sync
│   │       ├── ProcessAbandonedCarts.php   # Cart recovery emails
│   │       ├── GenerateSitemap.php         # SEO sitemap
│   │       └── CalculateInventoryAlerts.php # Stock alerts
│   │
│   ├── Enums/
│   │   ├── OrderStatus.php                 # pending, processing, shipped, delivered, cancelled
│   │   ├── PaymentStatus.php               # pending, paid, failed, refunded
│   │   ├── ProductHumour.php               # calming, uplifting, grounding, clarifying
│   │   ├── ProductRarity.php               # common, rare, limited
│   │   ├── ProductSeason.php               # spring, summer, autumn, winter
│   │   └── UserRole.php                    # customer, admin, super_admin
│   │
│   ├── Events/
│   │   ├── OrderPlaced.php                 # Triggers confirmation email
│   │   ├── OrderShipped.php                # Triggers shipping notification
│   │   ├── PaymentReceived.php             # Triggers receipt
│   │   ├── LowStockDetected.php            # Admin alert
│   │   └── NewsletterSubscribed.php        # Welcome email trigger
│   │
│   ├── Exceptions/
│   │   ├── Handler.php                     # Global exception handler
│   │   ├── InsufficientStockException.php  # Inventory validation
│   │   ├── PaymentFailedException.php      # Stripe error wrapper
│   │   └── InvalidCouponException.php      # Discount validation
│   │
│   ├── Http/
│   │   ├── Controllers/
│   │   │   ├── Api/
│   │   │   │   └── V1/
│   │   │   │       ├── AuthController.php          # Login, register, logout
│   │   │   │       ├── ProductController.php       # CRUD + filtering
│   │   │   │       ├── CategoryController.php      # Category listing
│   │   │   │       ├── CartController.php          # Cart operations
│   │   │   │       ├── CheckoutController.php      # Checkout flow
│   │   │   │       ├── OrderController.php         # Order management
│   │   │   │       ├── PaymentController.php       # Stripe integration
│   │   │   │       ├── WebhookController.php       # Stripe webhooks
│   │   │   │       ├── AddressController.php       # Address CRUD
│   │   │   │       ├── UserController.php          # Profile management
│   │   │   │       ├── WishlistController.php      # Wishlist operations
│   │   │   │       ├── ReviewController.php        # Product reviews
│   │   │   │       ├── NewsletterController.php    # Subscription
│   │   │   │       ├── SearchController.php        # Meilisearch proxy
│   │   │   │       ├── ShippingController.php      # Rate calculation
│   │   │   │       └── ContentController.php       # CMS pages
│   │   │   │
│   │   │   └── Webhook/
│   │   │       └── StripeWebhookController.php     # Payment webhooks
│   │   │
│   │   ├── Middleware/
│   │   │   ├── ForceJsonResponse.php       # API JSON enforcement
│   │   │   ├── SetLocale.php               # i18n support
│   │   │   ├── TrackCartSession.php        # Guest cart tracking
│   │   │   └── LogApiRequests.php          # Request logging
│   │   │
│   │   ├── Requests/
│   │   │   ├── Auth/
│   │   │   │   ├── LoginRequest.php
│   │   │   │   ├── RegisterRequest.php
│   │   │   │   └── ForgotPasswordRequest.php
│   │   │   ├── Cart/
│   │   │   │   ├── AddToCartRequest.php
│   │   │   │   └── UpdateCartRequest.php
│   │   │   ├── Checkout/
│   │   │   │   ├── InitiateCheckoutRequest.php
│   │   │   │   └── CompleteCheckoutRequest.php
│   │   │   ├── Order/
│   │   │   │   └── CreateOrderRequest.php
│   │   │   ├── Product/
│   │   │   │   ├── ProductFilterRequest.php
│   │   │   │   └── ProductSearchRequest.php
│   │   │   └── User/
│   │   │       ├── UpdateProfileRequest.php
│   │   │       └── CreateAddressRequest.php
│   │   │
│   │   └── Resources/
│   │       ├── ProductResource.php         # Product JSON structure
│   │       ├── ProductCollection.php       # Paginated products
│   │       ├── CategoryResource.php        # Category structure
│   │       ├── CartResource.php            # Cart with items
│   │       ├── CartItemResource.php        # Single cart item
│   │       ├── OrderResource.php           # Order details
│   │       ├── OrderItemResource.php       # Order line items
│   │       ├── UserResource.php            # User profile
│   │       ├── AddressResource.php         # Address structure
│   │       ├── ReviewResource.php          # Review with rating
│   │       └── ShippingRateResource.php    # Shipping options
│   │
│   ├── Jobs/
│   │   ├── ProcessOrderPayment.php         # Async payment processing
│   │   ├── SendOrderConfirmation.php       # Email dispatch
│   │   ├── SendShippingNotification.php    # Tracking email
│   │   ├── SyncProductToSearch.php         # Meilisearch indexing
│   │   ├── ProcessCartAbandonment.php      # Recovery campaign
│   │   ├── GenerateInvoicePdf.php          # Invoice generation
│   │   └── CalculateShippingRates.php      # Rate lookup
│   │
│   ├── Listeners/
│   │   ├── SendOrderConfirmationEmail.php
│   │   ├── SendShippingUpdateEmail.php
│   │   ├── NotifyAdminLowStock.php
│   │   ├── SendWelcomeEmail.php
│   │   └── UpdateInventoryOnOrder.php
│   │
│   ├── Mail/
│   │   ├── OrderConfirmation.php           # Order placed email
│   │   ├── OrderShipped.php                # Shipping notification
│   │   ├── CartAbandonment.php             # Recovery email
│   │   ├── NewsletterWelcome.php           # Subscription welcome
│   │   ├── PasswordReset.php               # Password reset
│   │   └── LowStockAlert.php               # Admin notification
│   │
│   ├── Models/
│   │   ├── User.php                        # Customer/Admin user
│   │   ├── Product.php                     # Essence product
│   │   ├── ProductVariant.php              # Size variants (5ml, 15ml, 30ml)
│   │   ├── Category.php                    # Product categories
│   │   ├── Tag.php                         # Product tags
│   │   ├── Cart.php                        # Shopping cart
│   │   ├── CartItem.php                    # Cart line items
│   │   ├── Order.php                       # Customer order
│   │   ├── OrderItem.php                   # Order line items
│   │   ├── Address.php                     # Customer addresses
│   │   ├── Payment.php                     # Payment records
│   │   ├── Coupon.php                      # Discount codes
│   │   ├── CouponUsage.php                 # Usage tracking
│   │   ├── Review.php                      # Product reviews
│   │   ├── Wishlist.php                    # Customer wishlist
│   │   ├── WishlistItem.php                # Wishlist items
│   │   ├── NewsletterSubscriber.php        # Email subscribers
│   │   ├── Inventory.php                   # Stock tracking
│   │   ├── InventoryMovement.php           # Stock history
│   │   ├── ShippingZone.php                # Shipping regions
│   │   ├── ShippingRate.php                # Zone-based rates
│   │   ├── Page.php                        # CMS pages
│   │   ├── Setting.php                     # Site settings
│   │   └── AuditLog.php                    # Admin activity log
│   │
│   ├── Observers/
│   │   ├── ProductObserver.php             # Search index sync
│   │   ├── OrderObserver.php               # Order events
│   │   ├── InventoryObserver.php           # Stock alerts
│   │   └── ReviewObserver.php              # Rating recalculation
│   │
│   ├── Policies/
│   │   ├── OrderPolicy.php                 # Order access control
│   │   ├── AddressPolicy.php               # Address ownership
│   │   ├── ReviewPolicy.php                # Review permissions
│   │   └── WishlistPolicy.php              # Wishlist access
│   │
│   ├── Providers/
│   │   ├── AppServiceProvider.php          # Application bindings
│   │   ├── AuthServiceProvider.php         # Auth policies
│   │   ├── EventServiceProvider.php        # Event listeners
│   │   ├── RouteServiceProvider.php        # Route configuration
│   │   └── RepositoryServiceProvider.php   # Repository bindings
│   │
│   ├── Repositories/
│   │   ├── Contracts/
│   │   │   ├── ProductRepositoryInterface.php
│   │   │   ├── OrderRepositoryInterface.php
│   │   │   ├── CartRepositoryInterface.php
│   │   │   └── UserRepositoryInterface.php
│   │   │
│   │   └── Eloquent/
│   │       ├── ProductRepository.php
│   │       ├── OrderRepository.php
│   │       ├── CartRepository.php
│   │       └── UserRepository.php
│   │
│   ├── Services/
│   │   ├── CartService.php                 # Cart business logic
│   │   ├── CheckoutService.php             # Checkout orchestration
│   │   ├── OrderService.php                # Order processing
│   │   ├── PaymentService.php              # Stripe integration
│   │   ├── ShippingService.php             # Rate calculation
│   │   ├── InventoryService.php            # Stock management
│   │   ├── TaxService.php                  # GST calculation
│   │   ├── CouponService.php               # Discount validation
│   │   ├── SearchService.php               # Meilisearch wrapper
│   │   ├── MediaService.php                # Image processing
│   │   └── NotificationService.php         # Multi-channel notifications
│   │
│   └── ValueObjects/
│       ├── Money.php                       # Currency handling
│       ├── Address.php                     # Address structure
│       └── CartTotal.php                   # Cart calculations
│
├── bootstrap/
│   ├── app.php                             # Application bootstrap
│   └── providers.php                       # Provider registration
│
├── config/
│   ├── app.php                             # Application config
│   ├── auth.php                            # Authentication
│   ├── cache.php                           # Cache configuration
│   ├── cors.php                            # CORS settings
│   ├── database.php                        # Database connections
│   ├── filesystems.php                     # Storage disks
│   ├── horizon.php                         # Queue dashboard
│   ├── logging.php                         # Log channels
│   ├── mail.php                            # Email configuration
│   ├── queue.php                           # Queue connections
│   ├── sanctum.php                         # API auth
│   ├── scout.php                           # Search configuration
│   ├── services.php                        # External services
│   ├── shop.php                            # E-commerce settings
│   │   # - GST rate (0.09)
│   │   # - Currency (SGD)
│   │   # - Max cart items
│   │   # - Abandoned cart timeout
│   └── stripe.php                          # Payment configuration
│
├── database/
│   ├── factories/
│   │   ├── UserFactory.php
│   │   ├── ProductFactory.php
│   │   ├── CategoryFactory.php
│   │   ├── OrderFactory.php
│   │   └── ReviewFactory.php
│   │
│   ├── migrations/
│   │   ├── 0001_01_01_000001_create_users_table.php
│   │   ├── 0001_01_01_000002_create_categories_table.php
│   │   ├── 0001_01_01_000003_create_products_table.php
│   │   ├── 0001_01_01_000004_create_product_variants_table.php
│   │   ├── 0001_01_01_000005_create_product_images_table.php
│   │   ├── 0001_01_01_000006_create_carts_table.php
│   │   ├── 0001_01_01_000007_create_cart_items_table.php
│   │   ├── 0001_01_01_000008_create_addresses_table.php
│   │   ├── 0001_01_01_000009_create_orders_table.php
│   │   ├── 0001_01_01_000010_create_order_items_table.php
│   │   ├── 0001_01_01_000011_create_payments_table.php
│   │   ├── 0001_01_01_000012_create_coupons_table.php
│   │   ├── 0001_01_01_000013_create_coupon_usages_table.php
│   │   ├── 0001_01_01_000014_create_reviews_table.php
│   │   ├── 0001_01_01_000015_create_wishlists_table.php
│   │   ├── 0001_01_01_000016_create_wishlist_items_table.php
│   │   ├── 0001_01_01_000017_create_inventory_table.php
│   │   ├── 0001_01_01_000018_create_inventory_movements_table.php
│   │   ├── 0001_01_01_000019_create_shipping_zones_table.php
│   │   ├── 0001_01_01_000020_create_shipping_rates_table.php
│   │   ├── 0001_01_01_000021_create_newsletter_subscribers_table.php
│   │   ├── 0001_01_01_000022_create_pages_table.php
│   │   ├── 0001_01_01_000023_create_settings_table.php
│   │   ├── 0001_01_01_000024_create_audit_logs_table.php
│   │   └── 0001_01_01_000025_create_tags_table.php
│   │
│   └── seeders/
│       ├── DatabaseSeeder.php              # Master seeder
│       ├── UserSeeder.php                  # Admin users
│       ├── CategorySeeder.php              # Product categories
│       ├── ProductSeeder.php               # Sample essences
│       ├── CouponSeeder.php                # Demo coupons
│       ├── ShippingSeeder.php              # SG shipping zones
│       └── SettingsSeeder.php              # Default settings
│
├── resources/
│   └── views/
│       ├── emails/
│       │   ├── orders/
│       │   │   ├── confirmation.blade.php
│       │   │   ├── shipped.blade.php
│       │   │   └── invoice.blade.php
│       │   ├── cart/
│       │   │   └── abandonment.blade.php
│       │   └── newsletter/
│       │       └── welcome.blade.php
│       └── pdf/
│           └── invoice.blade.php           # PDF invoice template
│
├── routes/
│   ├── api.php                             # Public API routes
│   ├── api_v1.php                          # Versioned API routes
│   ├── web.php                             # Webhook routes
│   └── channels.php                        # Broadcasting channels
│
├── storage/
│   ├── app/
│   │   ├── invoices/                       # Generated invoices
│   │   └── exports/                        # Data exports
│   └── logs/                               # Application logs
│
└── tests/
    ├── Feature/
    │   ├── Api/
    │   │   ├── AuthTest.php
    │   │   ├── ProductTest.php
    │   │   ├── CartTest.php
    │   │   ├── CheckoutTest.php
    │   │   ├── OrderTest.php
    │   │   └── PaymentWebhookTest.php
    │   └── Services/
    │       ├── CartServiceTest.php
    │       ├── CheckoutServiceTest.php
    │       ├── TaxServiceTest.php
    │       └── InventoryServiceTest.php
    │
    └── Unit/
        ├── Models/
        │   ├── ProductTest.php
        │   ├── OrderTest.php
        │   └── CartTest.php
        └── ValueObjects/
            └── MoneyTest.php
4. File Hierarchy — Next.js Frontend
text

atelier-arome-web/
├── .env.local                              # Local environment
├── .env.production                         # Production environment
├── next.config.ts                          # Next.js configuration
├── tailwind.config.ts                      # Tailwind 4.0 configuration
├── tsconfig.json                           # TypeScript configuration
├── package.json                            # Node dependencies
├── components.json                         # Shadcn/UI configuration
│
├── public/
│   ├── fonts/
│   │   ├── CormorantGaramond-Variable.woff2    # Display font
│   │   ├── CrimsonPro-Variable.woff2           # Body font
│   │   └── GreatVibes-Regular.woff2            # Accent font
│   │
│   ├── images/
│   │   ├── botanicals/                     # Botanical SVG illustrations
│   │   │   ├── lavender.svg
│   │   │   ├── eucalyptus.svg
│   │   │   ├── bergamot.svg
│   │   │   └── rose.svg
│   │   ├── og-image.jpg                    # Social sharing image
│   │   └── favicon.svg                     # Alchemical seal favicon
│   │
│   ├── robots.txt                          # SEO robots
│   └── sitemap.xml                         # Generated sitemap
│
├── src/
│   ├── app/
│   │   ├── (storefront)/                   # Public storefront layout group
│   │   │   ├── layout.tsx                  # Storefront shell (header, footer)
│   │   │   │
│   │   │   ├── page.tsx                    # Homepage (Hero, Featured, CTA)
│   │   │   │
│   │   │   ├── compendium/                 # Product catalog
│   │   │   │   ├── page.tsx                # Product listing with filters
│   │   │   │   ├── loading.tsx             # Skeleton loader
│   │   │   │   └── [slug]/
│   │   │   │       ├── page.tsx            # Product detail page
│   │   │   │       ├── loading.tsx         # Product skeleton
│   │   │   │       └── opengraph-image.tsx # Dynamic OG image
│   │   │   │
│   │   │   ├── alchemy/                    # About / Process page
│   │   │   │   └── page.tsx
│   │   │   │
│   │   │   ├── atelier/                    # About the atelier
│   │   │   │   └── page.tsx
│   │   │   │
│   │   │   ├── manuscript/                 # Blog / Stories
│   │   │   │   ├── page.tsx                # Blog listing
│   │   │   │   └── [slug]/
│   │   │   │       └── page.tsx            # Blog post
│   │   │   │
│   │   │   ├── search/                     # Search results
│   │   │   │   └── page.tsx
│   │   │   │
│   │   │   └── [slug]/                     # CMS pages (privacy, terms)
│   │   │       └── page.tsx
│   │   │
│   │   ├── (checkout)/                     # Checkout layout group
│   │   │   ├── layout.tsx                  # Minimal checkout shell
│   │   │   │
│   │   │   ├── cart/                       # Cart page
│   │   │   │   └── page.tsx
│   │   │   │
│   │   │   ├── checkout/
│   │   │   │   ├── page.tsx                # Multi-step checkout
│   │   │   │   ├── shipping/
│   │   │   │   │   └── page.tsx            # Shipping step
│   │   │   │   ├── payment/
│   │   │   │   │   └── page.tsx            # Payment step
│   │   │   │   └── confirmation/
│   │   │   │       └── page.tsx            # Order confirmation
│   │   │   │
│   │   │   └── order/
│   │   │       └── [id]/
│   │   │           └── page.tsx            # Order status page
│   │   │
│   │   ├── (account)/                      # Authenticated layout group
│   │   │   ├── layout.tsx                  # Account sidebar layout
│   │   │   │
│   │   │   ├── account/
│   │   │   │   ├── page.tsx                # Account dashboard
│   │   │   │   ├── orders/
│   │   │   │   │   ├── page.tsx            # Order history
│   │   │   │   │   └── [id]/
│   │   │   │   │       └── page.tsx        # Order detail
│   │   │   │   ├── addresses/
│   │   │   │   │   └── page.tsx            # Saved addresses
│   │   │   │   ├── wishlist/
│   │   │   │   │   └── page.tsx            # Wishlist
│   │   │   │   └── settings/
│   │   │   │       └── page.tsx            # Profile settings
│   │   │   │
│   │   │   └── auth/
│   │   │       ├── login/
│   │   │       │   └── page.tsx            # Login page
│   │   │       ├── register/
│   │   │       │   └── page.tsx            # Registration page
│   │   │       ├── forgot-password/
│   │   │       │   └── page.tsx            # Password reset request
│   │   │       └── reset-password/
│   │   │           └── page.tsx            # Password reset form
│   │   │
│   │   ├── api/                            # Next.js API routes
│   │   │   ├── revalidate/
│   │   │   │   └── route.ts                # On-demand revalidation
│   │   │   └── preview/
│   │   │       └── route.ts                # CMS preview mode
│   │   │
│   │   ├── layout.tsx                      # Root layout
│   │   ├── loading.tsx                     # Global loading state
│   │   ├── error.tsx                       # Error boundary
│   │   ├── not-found.tsx                   # 404 page
│   │   └── globals.css                     # Global styles + Tailwind
│   │
│   ├── components/
│   │   ├── ui/                             # Shadcn/UI primitives (styled)
│   │   │   ├── button.tsx                  # Custom button variants
│   │   │   ├── card.tsx                    # Manuscript-styled cards
│   │   │   ├── dialog.tsx                  # Modal wrapper
│   │   │   ├── sheet.tsx                   # Drawer (cart, mobile nav)
│   │   │   ├── input.tsx                   # Form inputs
│   │   │   ├── select.tsx                  # Select dropdowns
│   │   │   ├── checkbox.tsx                # Checkboxes
│   │   │   ├── radio-group.tsx             # Radio buttons
│   │   │   ├── label.tsx                   # Form labels
│   │   │   ├── badge.tsx                   # Rarity badges
│   │   │   ├── separator.tsx               # Dividers
│   │   │   ├── skeleton.tsx                # Loading skeletons
│   │   │   ├── toast.tsx                   # Toast notifications
│   │   │   ├── toaster.tsx                 # Toast provider
│   │   │   ├── tooltip.tsx                 # Tooltips
│   │   │   ├── accordion.tsx               # FAQ accordions
│   │   │   ├── tabs.tsx                    # Product tabs
│   │   │   ├── slider.tsx                  # Price range slider
│   │   │   ├── scroll-area.tsx             # Scrollable containers
│   │   │   └── aspect-ratio.tsx            # Image containers
│   │   │
│   │   ├── layout/
│   │   │   ├── header/
│   │   │   │   ├── header.tsx              # Main header component
│   │   │   │   ├── header-seal.tsx         # Animated logo seal
│   │   │   │   ├── header-nav.tsx          # Desktop navigation
│   │   │   │   ├── header-tools.tsx        # Search, cart, menu buttons
│   │   │   │   └── mobile-nav.tsx          # Mobile navigation drawer
│   │   │   │
│   │   │   ├── footer/
│   │   │   │   ├── footer.tsx              # Colophon footer
│   │   │   │   └── footer-newsletter.tsx   # Newsletter signup
│   │   │   │
│   │   │   ├── atelier-banner.tsx          # Top announcement banner
│   │   │   ├── texture-overlay.tsx         # Parchment texture
│   │   │   ├── gold-leaf-accents.tsx       # Parallax gold decorations
│   │   │   ├── skip-link.tsx               # Accessibility skip nav
│   │   │   └── back-to-top.tsx             # Scroll to top button
│   │   │
│   │   ├── home/
│   │   │   ├── hero-section.tsx            # Illuminated hero
│   │   │   ├── hero-vessel.tsx             # Animated vessel illustration
│   │   │   ├── hero-botanicals.tsx         # Floating botanical elements
│   │   │   ├── featured-essences.tsx       # Featured products grid
│   │   │   ├── alchemy-preview.tsx         # Process teaser
│   │   │   └── testimonial-preview.tsx     # Featured testimonial
│   │   │
│   │   ├── product/
│   │   │   ├── essence-card.tsx            # Product card component
│   │   │   ├── essence-grid.tsx            # Product grid layout
│   │   │   ├── product-filters.tsx         # Humour/rarity/season filters
│   │   │   ├── product-sort.tsx            # Sort dropdown
│   │   │   ├── product-gallery.tsx         # Image gallery
│   │   │   ├── product-info.tsx            # Product details panel
│   │   │   ├── product-variants.tsx        # Size selector
│   │   │   ├── product-quantity.tsx        # Quantity selector
│   │   │   ├── product-reviews.tsx         # Reviews section
│   │   │   ├── product-related.tsx         # Related products
│   │   │   ├── add-to-cart-button.tsx      # Add to cart with feedback
│   │   │   ├── wishlist-button.tsx         # Wishlist toggle
│   │   │   └── product-skeleton.tsx        # Loading skeleton
│   │   │
│   │   ├── cart/
│   │   │   ├── cart-drawer.tsx             # Slide-out cart (vial drawer)
│   │   │   ├── cart-item.tsx               # Cart line item
│   │   │   ├── cart-summary.tsx            # Subtotal, tax, total
│   │   │   ├── cart-empty.tsx              # Empty cart state
│   │   │   ├── quantity-controls.tsx       # +/- buttons
│   │   │   └── cart-coupon.tsx             # Coupon input
│   │   │
│   │   ├── checkout/
│   │   │   ├── checkout-steps.tsx          # Step indicator
│   │   │   ├── shipping-form.tsx           # Shipping address form
│   │   │   ├── shipping-options.tsx        # Shipping method selection
│   │   │   ├── payment-form.tsx            # Stripe Elements
│   │   │   ├── order-summary.tsx           # Checkout sidebar summary
│   │   │   ├── payment-methods.tsx         # Card, PayNow, GrabPay
│   │   │   └── order-confirmation.tsx      # Success message
│   │   │
│   │   ├── account/
│   │   │   ├── account-sidebar.tsx         # Account navigation
│   │   │   ├── order-card.tsx              # Order history item
│   │   │   ├── address-card.tsx            # Saved address card
│   │   │   ├── address-form.tsx            # Address CRUD form
│   │   │   └── profile-form.tsx            # Profile edit form
│   │   │
│   │   ├── auth/
│   │   │   ├── login-form.tsx              # Login form
│   │   │   ├── register-form.tsx           # Registration form
│   │   │   ├── forgot-password-form.tsx    # Reset request
│   │   │   └── reset-password-form.tsx     # Password reset
│   │   │
│   │   ├── manuscript/
│   │   │   ├── testimonial-carousel.tsx    # Testimonials slider
│   │   │   ├── testimonial-card.tsx        # Single testimonial
│   │   │   └── blog-card.tsx               # Blog post preview
│   │   │
│   │   ├── search/
│   │   │   ├── search-modal.tsx            # Command palette search
│   │   │   ├── search-results.tsx          # Search results grid
│   │   │   └── search-input.tsx            # Search input component
│   │   │
│   │   ├── forms/
│   │   │   ├── newsletter-form.tsx         # Email subscription
│   │   │   ├── contact-form.tsx            # Contact page form
│   │   │   └── review-form.tsx             # Product review form
│   │   │
│   │   └── shared/
│   │       ├── section-header.tsx          # Section label + title
│   │       ├── ornamental-rule.tsx         # Decorative divider
│   │       ├── illuminated-initial.tsx     # Drop cap letter
│   │       ├── alchemical-symbol.tsx       # Humour icons
│   │       ├── price-display.tsx           # Formatted price
│   │       ├── rating-stars.tsx            # Star rating display
│   │       ├── empty-state.tsx             # Generic empty state
│   │       ├── loading-spinner.tsx         # Loading indicator
│   │       └── seo-metadata.tsx            # Dynamic meta tags
│   │
│   ├── hooks/
│   │   ├── use-cart.ts                     # Cart operations hook
│   │   ├── use-wishlist.ts                 # Wishlist operations
│   │   ├── use-auth.ts                     # Authentication hook
│   │   ├── use-checkout.ts                 # Checkout state
│   │   ├── use-search.ts                   # Search hook
│   │   ├── use-filters.ts                  # Product filter state
│   │   ├── use-media-query.ts              # Responsive helpers
│   │   ├── use-scroll-position.ts          # Scroll tracking
│   │   ├── use-reduced-motion.ts           # Motion preference
│   │   ├── use-local-storage.ts            # Persistent storage
│   │   └── use-toast.ts                    # Toast notifications
│   │
│   ├── lib/
│   │   ├── api/
│   │   │   ├── client.ts                   # Axios/fetch wrapper
│   │   │   ├── endpoints.ts                # API endpoint constants
│   │   │   ├── products.ts                 # Product API calls
│   │   │   ├── cart.ts                     # Cart API calls
│   │   │   ├── checkout.ts                 # Checkout API calls
│   │   │   ├── orders.ts                   # Order API calls
│   │   │   ├── auth.ts                     # Auth API calls
│   │   │   ├── user.ts                     # User API calls
│   │   │   └── newsletter.ts               # Newsletter API calls
│   │   │
│   │   ├── stripe/
│   │   │   ├── stripe-provider.tsx         # Stripe Elements provider
│   │   │   └── stripe-utils.ts             # Stripe helpers
│   │   │
│   │   ├── utils/
│   │   │   ├── cn.ts                       # Class name merge
│   │   │   ├── format-currency.ts          # SGD formatting
│   │   │   ├── format-date.ts              # Date formatting
│   │   │   ├── slugify.ts                  # URL slug generation
│   │   │   └── validators.ts               # Zod schemas
│   │   │
│   │   ├── constants/
│   │   │   ├── humours.ts                  # Humour symbols/labels
│   │   │   ├── seasons.ts                  # Season mappings
│   │   │   ├── navigation.ts               # Nav link constants
│   │   │   └── site.ts                     # Site metadata
│   │   │
│   │   └── fonts.ts                        # Next.js font loader
│   │
│   ├── stores/
│   │   ├── cart-store.ts                   # Zustand cart state
│   │   ├── auth-store.ts                   # Zustand auth state
│   │   ├── ui-store.ts                     # UI state (modals, drawers)
│   │   └── checkout-store.ts               # Checkout flow state
│   │
│   ├── types/
│   │   ├── product.ts                      # Product types
│   │   ├── cart.ts                         # Cart types
│   │   ├── order.ts                        # Order types
│   │   ├── user.ts                         # User types
│   │   ├── address.ts                      # Address types
│   │   ├── payment.ts                      # Payment types
│   │   ├── shipping.ts                     # Shipping types
│   │   └── api.ts                          # API response types
│   │
│   └── styles/
│       ├── design-tokens.css               # CSS custom properties
│       ├── typography.css                  # Font face declarations
│       ├── animations.css                  # Keyframe animations
│       └── manuscript-theme.css            # Manuscript styling
│
├── tests/
│   ├── e2e/
│   │   ├── checkout.spec.ts                # Checkout flow test
│   │   ├── cart.spec.ts                    # Cart operations test
│   │   └── auth.spec.ts                    # Auth flow test
│   │
│   └── components/
│       ├── essence-card.test.tsx           # Component tests
│       └── cart-drawer.test.tsx
│
└── playwright.config.ts                    # E2E test configuration
5. Database Schema
5.1 Entity Relationship Diagram
mermaid

erDiagram
    USERS ||--o{ ADDRESSES : has
    USERS ||--o{ ORDERS : places
    USERS ||--o| CARTS : has
    USERS ||--o{ REVIEWS : writes
    USERS ||--o| WISHLISTS : has
    
    CATEGORIES ||--o{ PRODUCTS : contains
    PRODUCTS ||--o{ PRODUCT_VARIANTS : has
    PRODUCTS ||--o{ PRODUCT_IMAGES : has
    PRODUCTS }o--o{ TAGS : tagged_with
    PRODUCTS ||--o{ REVIEWS : receives
    PRODUCTS ||--o{ INVENTORY : tracks
    
    CARTS ||--o{ CART_ITEMS : contains
    CART_ITEMS }o--|| PRODUCT_VARIANTS : references
    
    ORDERS ||--o{ ORDER_ITEMS : contains
    ORDERS ||--o{ PAYMENTS : has
    ORDERS }o--|| ADDRESSES : ships_to
    ORDERS }o--o| COUPONS : uses
    
    ORDER_ITEMS }o--|| PRODUCT_VARIANTS : references
    
    WISHLISTS ||--o{ WISHLIST_ITEMS : contains
    WISHLIST_ITEMS }o--|| PRODUCTS : references
    
    COUPONS ||--o{ COUPON_USAGES : tracks
    COUPON_USAGES }o--|| USERS : used_by
    
    SHIPPING_ZONES ||--o{ SHIPPING_RATES : has
    
    INVENTORY ||--o{ INVENTORY_MOVEMENTS : logs

    USERS {
        uuid id PK
        string name
        string email UK
        string password
        enum role "customer|admin|super_admin"
        string phone
        boolean email_verified
        timestamp email_verified_at
        string remember_token
        timestamp created_at
        timestamp updated_at
        timestamp deleted_at
    }
    
    CATEGORIES {
        uuid id PK
        string name
        string slug UK
        text description
        string image_url
        uuid parent_id FK
        integer sort_order
        boolean is_active
        timestamp created_at
        timestamp updated_at
    }
    
    PRODUCTS {
        uuid id PK
        uuid category_id FK
        string name
        string slug UK
        string latin_name
        text description
        text story
        enum humour "calming|uplifting|grounding|clarifying"
        enum rarity "common|rare|limited"
        enum season "spring|summer|autumn|winter"
        string extraction_method
        json scent_notes "['Floral','Herbaceous']"
        integer folio_number
        boolean is_featured
        boolean is_active
        decimal average_rating
        integer review_count
        json seo_metadata
        timestamp created_at
        timestamp updated_at
        timestamp deleted_at
    }
    
    PRODUCT_VARIANTS {
        uuid id PK
        uuid product_id FK
        string sku UK
        string name "5ml Phial|15ml Bottle|30ml Vessel"
        integer size_ml
        decimal price
        decimal compare_at_price
        boolean is_active
        timestamp created_at
        timestamp updated_at
    }
    
    PRODUCT_IMAGES {
        uuid id PK
        uuid product_id FK
        string url
        string alt_text
        integer sort_order
        boolean is_primary
        timestamp created_at
    }
    
    TAGS {
        uuid id PK
        string name
        string slug UK
        timestamp created_at
    }
    
    PRODUCT_TAG {
        uuid product_id FK
        uuid tag_id FK
    }
    
    CARTS {
        uuid id PK
        uuid user_id FK "nullable for guests"
        string session_id "guest identifier"
        decimal subtotal
        decimal tax_amount
        decimal total
        string currency "SGD"
        timestamp expires_at
        timestamp created_at
        timestamp updated_at
    }
    
    CART_ITEMS {
        uuid id PK
        uuid cart_id FK
        uuid product_variant_id FK
        integer quantity
        decimal unit_price
        decimal subtotal
        timestamp created_at
        timestamp updated_at
    }
    
    ADDRESSES {
        uuid id PK
        uuid user_id FK
        string label "Home|Office|Other"
        string recipient_name
        string phone
        string address_line_1
        string address_line_2
        string postal_code
        string city "Singapore"
        string country "SG"
        boolean is_default
        timestamp created_at
        timestamp updated_at
    }
    
    ORDERS {
        uuid id PK
        uuid user_id FK "nullable for guest orders"
        string order_number UK "AA-2024-000001"
        uuid shipping_address_id FK
        uuid billing_address_id FK
        uuid coupon_id FK
        enum status "pending|processing|shipped|delivered|cancelled"
        decimal subtotal
        decimal discount_amount
        decimal shipping_amount
        decimal tax_amount
        decimal total
        string currency "SGD"
        text notes
        string tracking_number
        string tracking_url
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
        decimal unit_price
        decimal subtotal
        timestamp created_at
    }
    
    PAYMENTS {
        uuid id PK
        uuid order_id FK
        string stripe_payment_intent_id UK
        string stripe_charge_id
        enum status "pending|succeeded|failed|refunded"
        enum method "card|paynow|grabpay"
        decimal amount
        string currency "SGD"
        json metadata
        string failure_reason
        timestamp paid_at
        timestamp refunded_at
        timestamp created_at
        timestamp updated_at
    }
    
    COUPONS {
        uuid id PK
        string code UK
        string description
        enum type "percentage|fixed_amount|free_shipping"
        decimal value
        decimal minimum_order_amount
        decimal maximum_discount_amount
        integer usage_limit
        integer usage_count
        boolean is_active
        timestamp starts_at
        timestamp expires_at
        timestamp created_at
        timestamp updated_at
    }
    
    COUPON_USAGES {
        uuid id PK
        uuid coupon_id FK
        uuid user_id FK
        uuid order_id FK
        timestamp used_at
    }
    
    REVIEWS {
        uuid id PK
        uuid product_id FK
        uuid user_id FK
        uuid order_id FK
        integer rating "1-5"
        string title
        text content
        boolean is_verified_purchase
        boolean is_approved
        timestamp approved_at
        timestamp created_at
        timestamp updated_at
    }
    
    WISHLISTS {
        uuid id PK
        uuid user_id FK UK
        timestamp created_at
        timestamp updated_at
    }
    
    WISHLIST_ITEMS {
        uuid id PK
        uuid wishlist_id FK
        uuid product_id FK
        timestamp created_at
    }
    
    INVENTORY {
        uuid id PK
        uuid product_variant_id FK UK
        integer quantity
        integer reserved_quantity
        integer low_stock_threshold
        boolean track_inventory
        timestamp created_at
        timestamp updated_at
    }
    
    INVENTORY_MOVEMENTS {
        uuid id PK
        uuid inventory_id FK
        uuid order_id FK "nullable"
        enum type "receipt|sale|adjustment|reservation|release"
        integer quantity_change
        integer quantity_after
        string reason
        uuid performed_by FK "admin user"
        timestamp created_at
    }
    
    SHIPPING_ZONES {
        uuid id PK
        string name "Singapore Standard|Singapore Express"
        string description
        boolean is_active
        timestamp created_at
        timestamp updated_at
    }
    
    SHIPPING_RATES {
        uuid id PK
        uuid shipping_zone_id FK
        string name "Standard Delivery|Express Delivery"
        decimal min_order_amount
        decimal max_order_amount
        decimal rate
        integer min_delivery_days
        integer max_delivery_days
        boolean is_active
        timestamp created_at
        timestamp updated_at
    }
    
    NEWSLETTER_SUBSCRIBERS {
        uuid id PK
        string email UK
        string name
        enum status "subscribed|unsubscribed"
        string source "footer|popup|checkout"
        timestamp subscribed_at
        timestamp unsubscribed_at
        timestamp created_at
        timestamp updated_at
    }
    
    PAGES {
        uuid id PK
        string title
        string slug UK
        text content
        json seo_metadata
        boolean is_published
        timestamp published_at
        timestamp created_at
        timestamp updated_at
    }
    
    SETTINGS {
        uuid id PK
        string key UK
        json value
        string group "general|shipping|tax|email"
        timestamp created_at
        timestamp updated_at
    }
    
    AUDIT_LOGS {
        uuid id PK
        uuid user_id FK
        string action "created|updated|deleted"
        string model_type
        uuid model_id
        json old_values
        json new_values
        string ip_address
        string user_agent
        timestamp created_at
    }
5.2 Key Database Indexes
SQL

-- Performance-critical indexes
CREATE INDEX idx_products_humour ON products(humour) WHERE is_active = true;
CREATE INDEX idx_products_category ON products(category_id) WHERE is_active = true;
CREATE INDEX idx_products_featured ON products(is_featured) WHERE is_active = true;
CREATE INDEX idx_products_search ON products USING gin(to_tsvector('english', name || ' ' || latin_name || ' ' || description));

CREATE INDEX idx_orders_user ON orders(user_id);
CREATE INDEX idx_orders_status ON orders(status);
CREATE INDEX idx_orders_created ON orders(created_at DESC);

CREATE INDEX idx_cart_items_cart ON cart_items(cart_id);
CREATE INDEX idx_cart_session ON carts(session_id) WHERE user_id IS NULL;

CREATE INDEX idx_inventory_variant ON inventory(product_variant_id);
CREATE INDEX idx_inventory_low_stock ON inventory(quantity) WHERE quantity <= low_stock_threshold;
6. Application Flow Diagrams
6.1 User Authentication Flow
mermaid

sequenceDiagram
    participant U as User
    participant FE as Next.js Frontend
    participant API as Laravel API
    participant DB as PostgreSQL
    participant Email as Resend

    rect rgb(240, 248, 255)
        Note over U,Email: Registration Flow
        U->>FE: Fill registration form
        FE->>FE: Validate with Zod
        FE->>API: POST /api/v1/auth/register
        API->>API: Validate request
        API->>DB: Check email uniqueness
        DB-->>API: Email available
        API->>DB: Create user
        DB-->>API: User created
        API->>Email: Queue verification email
        API-->>FE: 201 Created + token
        FE->>FE: Store token in httpOnly cookie
        FE-->>U: Redirect to verification notice
    end

    rect rgb(255, 248, 240)
        Note over U,Email: Login Flow
        U->>FE: Enter credentials
        FE->>API: POST /api/v1/auth/login
        API->>DB: Verify credentials
        DB-->>API: User found
        API->>API: Generate Sanctum token
        API-->>FE: 200 OK + token + user
        FE->>FE: Store token, update auth store
        FE-->>U: Redirect to dashboard/cart
    end

    rect rgb(248, 255, 240)
        Note over U,Email: Password Reset Flow
        U->>FE: Request password reset
        FE->>API: POST /api/v1/auth/forgot-password
        API->>DB: Find user by email
        API->>DB: Create password reset token
        API->>Email: Send reset email
        API-->>FE: 200 OK (always, for security)
        U->>FE: Click email link
        FE->>API: POST /api/v1/auth/reset-password
        API->>DB: Verify token, update password
        API-->>FE: 200 OK
        FE-->>U: Redirect to login
    end
6.2 Product Browsing Flow
mermaid

sequenceDiagram
    participant U as User
    participant FE as Next.js Frontend
    participant Cache as TanStack Query
    participant API as Laravel API
    participant Search as Meilisearch
    participant DB as PostgreSQL

    rect rgb(240, 248, 255)
        Note over U,DB: Initial Page Load (SSR)
        U->>FE: Navigate to /compendium
        FE->>API: GET /api/v1/products?featured=true&limit=12
        API->>DB: Query products with filters
        DB-->>API: Product list
        API-->>FE: JSON response
        FE->>FE: Render page (SSR)
        FE-->>U: Display product grid
    end

    rect rgb(255, 248, 240)
        Note over U,DB: Filter Application (CSR)
        U->>FE: Click "Calming" filter
        FE->>FE: Update URL params
        FE->>Cache: Check cache for query
        Cache-->>FE: Cache miss
        FE->>API: GET /api/v1/products?humour=calming
        API->>DB: Filtered query
        DB-->>API: Filtered products
        API-->>FE: JSON response
        FE->>Cache: Store in cache
        FE->>FE: Animate grid transition
        FE-->>U: Display filtered products
    end

    rect rgb(248, 255, 240)
        Note over U,DB: Search Flow
        U->>FE: Type "lavender" in search
        FE->>FE: Debounce input (300ms)
        FE->>API: GET /api/v1/search?q=lavender
        API->>Search: Query Meilisearch
        Search-->>API: Ranked results
        API-->>FE: Search results
        FE-->>U: Display instant results
    end

    rect rgb(255, 240, 248)
        Note over U,DB: Product Detail View
        U->>FE: Click on product card
        FE->>Cache: Check cache for product
        Cache-->>FE: Cache hit (from list)
        FE->>FE: Optimistic navigation
        FE->>API: GET /api/v1/products/{slug}
        API->>DB: Get product with variants, reviews
        DB-->>API: Full product data
        API-->>FE: Complete product JSON
        FE->>Cache: Update cache
        FE-->>U: Display product page
    end
6.3 Cart & Checkout Flow
mermaid

sequenceDiagram
    participant U as User
    participant FE as Next.js Frontend
    participant Store as Zustand Store
    participant API as Laravel API
    participant DB as PostgreSQL
    participant Stripe as Stripe API
    participant Email as Resend

    rect rgb(240, 248, 255)
        Note over U,DB: Add to Cart
        U->>FE: Click "Add to Vial"
        FE->>Store: Optimistic update
        Store-->>FE: Update cart UI
        FE->>API: POST /api/v1/cart/items
        API->>DB: Check inventory
        DB-->>API: Stock available
        API->>DB: Create/update cart item
        DB-->>API: Cart updated
        API-->>FE: Updated cart total
        FE->>Store: Sync with server state
        FE-->>U: Show toast notification
    end

    rect rgb(255, 248, 240)
        Note over U,Stripe: Checkout Process
        U->>FE: Click "Proceed to Checkout"
        FE->>API: POST /api/v1/checkout/init
        API->>DB: Validate cart, reserve inventory
        API->>Stripe: Create PaymentIntent
        Stripe-->>API: client_secret
        API-->>FE: Checkout session data
        FE-->>U: Show shipping form
        
        U->>FE: Enter shipping address
        FE->>API: POST /api/v1/checkout/shipping
        API->>DB: Calculate shipping rates
        API-->>FE: Shipping options
        FE-->>U: Show payment form
        
        U->>FE: Enter payment details
        FE->>Stripe: Confirm payment
        Stripe-->>FE: Payment succeeded
        FE->>API: POST /api/v1/checkout/complete
        API->>DB: Create order, deduct inventory
        API->>Email: Queue order confirmation
        API-->>FE: Order confirmation
        FE-->>U: Show confirmation page
    end

    rect rgb(248, 255, 240)
        Note over API,Email: Webhook Processing
        Stripe->>API: POST /webhooks/stripe
        API->>API: Verify signature
        API->>DB: Update payment status
        API->>DB: Update order status
        API->>Email: Send receipt
        API-->>Stripe: 200 OK
    end
6.4 Order Lifecycle Flow
mermaid

stateDiagram-v2
    [*] --> Pending: Order Created
    
    Pending --> Processing: Payment Confirmed
    Pending --> Cancelled: Payment Failed / Timeout
    
    Processing --> Shipped: Tracking Added
    Processing --> Cancelled: Admin Cancellation
    
    Shipped --> Delivered: Delivery Confirmed
    Shipped --> Returned: Return Requested
    
    Delivered --> [*]
    Cancelled --> [*]
    Returned --> Refunded: Refund Processed
    Refunded --> [*]
    
    note right of Pending
        - Inventory reserved
        - Payment pending
        - 30 min timeout
    end note
    
    note right of Processing
        - Payment confirmed
        - Preparing shipment
        - Admin dashboard action
    end note
    
    note right of Shipped
        - Tracking email sent
        - EasyParcel integration
        - Status updates
    end note
6.5 Admin Workflow Flow
mermaid

flowchart TB
    subgraph Admin["Admin Panel (Filament)"]
        Dashboard[Dashboard]
        Products[Product Management]
        Orders[Order Management]
        Customers[Customer Management]
        Inventory[Inventory]
        Coupons[Promotions]
        Content[CMS]
        Settings[Settings]
    end
    
    subgraph ProductFlow["Product Workflow"]
        CreateProduct[Create Product]
        AddVariants[Add Variants]
        UploadImages[Upload Images]
        SetInventory[Set Initial Stock]
        Publish[Publish to Store]
    end
    
    subgraph OrderFlow["Order Workflow"]
        ViewOrder[View Order]
        UpdateStatus[Update Status]
        AddTracking[Add Tracking]
        ProcessRefund[Process Refund]
        SendNotification[Send Update Email]
    end
    
    Dashboard --> Products
    Dashboard --> Orders
    Dashboard --> Inventory
    
    Products --> CreateProduct
    CreateProduct --> AddVariants
    AddVariants --> UploadImages
    UploadImages --> SetInventory
    SetInventory --> Publish
    
    Orders --> ViewOrder
    ViewOrder --> UpdateStatus
    UpdateStatus --> AddTracking
    AddTracking --> SendNotification
    ViewOrder --> ProcessRefund
7. API Specification
7.1 API Endpoints Overview
Authentication
Method	Endpoint	Description	Auth
POST	/api/v1/auth/register	Create new account	No
POST	/api/v1/auth/login	Authenticate user	No
POST	/api/v1/auth/logout	Invalidate token	Yes
POST	/api/v1/auth/forgot-password	Request reset	No
POST	/api/v1/auth/reset-password	Reset password	No
GET	/api/v1/auth/user	Get current user	Yes
Products
Method	Endpoint	Description	Auth
GET	/api/v1/products	List products (paginated, filterable)	No
GET	/api/v1/products/{slug}	Get product detail	No
GET	/api/v1/products/{slug}/reviews	Get product reviews	No
POST	/api/v1/products/{slug}/reviews	Create review	Yes
GET	/api/v1/categories	List categories	No
GET	/api/v1/search	Search products	No
Cart
Method	Endpoint	Description	Auth
GET	/api/v1/cart	Get current cart	Optional
POST	/api/v1/cart/items	Add item to cart	Optional
PUT	/api/v1/cart/items/{id}	Update cart item	Optional
DELETE	/api/v1/cart/items/{id}	Remove cart item	Optional
POST	/api/v1/cart/coupon	Apply coupon	Optional
DELETE	/api/v1/cart/coupon	Remove coupon	Optional
POST	/api/v1/cart/merge	Merge guest cart on login	Yes
Checkout
Method	Endpoint	Description	Auth
POST	/api/v1/checkout/init	Initialize checkout	Optional
POST	/api/v1/checkout/shipping	Set shipping address	Optional
GET	/api/v1/checkout/shipping-rates	Get shipping options	Optional
POST	/api/v1/checkout/complete	Complete order	Optional
Orders
Method	Endpoint	Description	Auth
GET	/api/v1/orders	List user's orders	Yes
GET	/api/v1/orders/{number}	Get order detail	Yes
GET	/api/v1/orders/{number}/track	Get tracking info	No
User Account
Method	Endpoint	Description	Auth
GET	/api/v1/user/profile	Get profile	Yes
PUT	/api/v1/user/profile	Update profile	Yes
GET	/api/v1/user/addresses	List addresses	Yes
POST	/api/v1/user/addresses	Create address	Yes
PUT	/api/v1/user/addresses/{id}	Update address	Yes
DELETE	/api/v1/user/addresses/{id}	Delete address	Yes
GET	/api/v1/user/wishlist	Get wishlist	Yes
POST	/api/v1/user/wishlist	Add to wishlist	Yes
DELETE	/api/v1/user/wishlist/{productId}	Remove from wishlist	Yes
Newsletter
Method	Endpoint	Description	Auth
POST	/api/v1/newsletter/subscribe	Subscribe	No
POST	/api/v1/newsletter/unsubscribe	Unsubscribe	No
7.2 Example Request/Response Structures
Product List Response
TypeScript

// GET /api/v1/products?humour=calming&sort=price_asc&page=1
{
  "data": [
    {
      "id": "550e8400-e29b-41d4-a716-446655440000",
      "name": "Provence Lavender",
      "slug": "provence-lavender",
      "latinName": "Lavandula × intermedia",
      "description": "Harvested at dawn in the Provençal hills...",
      "humour": "calming",
      "humourSymbol": "☾",
      "rarity": "rare",
      "season": "summer",
      "extraction": "Steam Distillation",
      "scentNotes": ["Floral", "Herbaceous", "Sweet"],
      "folioNumber": 1,
      "isFeatured": true,
      "averageRating": 4.8,
      "reviewCount": 24,
      "primaryImage": {
        "url": "https://cdn.atelierarome.com/products/lavender-01.jpg",
        "alt": "Provence Lavender essence in glass phial"
      },
      "variants": [
        {
          "id": "variant-001",
          "name": "5ml Phial",
          "sizeMl": 5,
          "price": 42.00,
          "compareAtPrice": null,
          "sku": "LAV-5ML-001",
          "inStock": true
        },
        {
          "id": "variant-002",
          "name": "15ml Bottle",
          "sizeMl": 15,
          "price": 98.00,
          "compareAtPrice": 115.00,
          "sku": "LAV-15ML-001",
          "inStock": true
        }
      ],
      "lowestPrice": 42.00,
      "createdAt": "2024-01-15T08:30:00Z"
    }
  ],
  "meta": {
    "currentPage": 1,
    "perPage": 12,
    "total": 47,
    "lastPage": 4
  },
  "links": {
    "first": "/api/v1/products?page=1",
    "last": "/api/v1/products?page=4",
    "next": "/api/v1/products?page=2",
    "prev": null
  }
}
Cart Response
TypeScript

// GET /api/v1/cart
{
  "data": {
    "id": "cart-550e8400",
    "items": [
      {
        "id": "item-001",
        "product": {
          "id": "prod-001",
          "name": "Provence Lavender",
          "slug": "provence-lavender",
          "latinName": "Lavandula × intermedia",
          "humour": "calming",
          "image": "https://cdn.atelierarome.com/products/lavender-01.jpg"
        },
        "variant": {
          "id": "variant-001",
          "name": "5ml Phial",
          "sku": "LAV-5ML-001"
        },
        "quantity": 2,
        "unitPrice": 42.00,
        "subtotal": 84.00
      }
    ],
    "itemCount": 2,
    "subtotal": 84.00,
    "discount": {
      "code": "WELCOME10",
      "type": "percentage",
      "value": 10,
      "amount": 8.40
    },
    "shipping": null,
    "tax": {
      "rate": 0.09,
      "amount": 6.80
    },
    "total": 82.40,
    "currency": "SGD"
  }
}
Checkout Complete Request
TypeScript

// POST /api/v1/checkout/complete
{
  "paymentIntentId": "pi_3N5xxxxxx",
  "shippingAddressId": "addr-001",
  "billingAddressId": "addr-001",
  "shippingRateId": "rate-standard",
  "email": "customer@example.com",
  "notes": "Please leave at door",
  "createAccount": false
}
Order Response
TypeScript

// GET /api/v1/orders/AA-2024-000123
{
  "data": {
    "id": "order-550e8400",
    "orderNumber": "AA-2024-000123",
    "status": "shipped",
    "items": [
      {
        "productName": "Provence Lavender",
        "variantName": "5ml Phial",
        "sku": "LAV-5ML-001",
        "quantity": 2,
        "unitPrice": 42.00,
        "subtotal": 84.00
      }
    ],
    "subtotal": 84.00,
    "discountAmount": 8.40,
    "shippingAmount": 5.00,
    "taxAmount": 7.25,
    "total": 87.85,
    "currency": "SGD",
    "shippingAddress": {
      "recipientName": "Jane Doe",
      "phone": "+65 9123 4567",
      "addressLine1": "123 Orchard Road",
      "addressLine2": "#05-01",
      "postalCode": "238858",
      "city": "Singapore",
      "country": "SG"
    },
    "tracking": {
      "carrier": "SingPost",
      "number": "RR123456789SG",
      "url": "https://www.singpost.com/track-items?id=RR123456789SG"
    },
    "createdAt": "2024-03-15T10:30:00Z",
    "shippedAt": "2024-03-16T14:00:00Z"
  }
}
8. Component Architecture
8.1 Component Hierarchy
text

┌─────────────────────────────────────────────────────────────────────────────┐
│                           COMPONENT ARCHITECTURE                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │                    LAYOUT COMPONENTS (Server)                        │   │
│  │  ┌──────────────────────────────────────────────────────────────┐   │   │
│  │  │ RootLayout                                                    │   │   │
│  │  │  ├── TextureOverlay (decorative)                              │   │   │
│  │  │  ├── GoldLeafAccents (decorative, parallax)                  │   │   │
│  │  │  └── Providers (QueryClient, Zustand, Stripe)                │   │   │
│  │  └──────────────────────────────────────────────────────────────┘   │   │
│  │                                                                      │   │
│  │  ┌──────────────────────────────────────────────────────────────┐   │   │
│  │  │ StorefrontLayout                                              │   │   │
│  │  │  ├── SkipLink                                                 │   │   │
│  │  │  ├── AtelierBanner                                           │   │   │
│  │  │  ├── Header                                                   │   │   │
│  │  │  │    ├── HeaderSeal (logo, animated)                        │   │   │
│  │  │  │    ├── HeaderNav (desktop nav)                            │   │   │
│  │  │  │    └── HeaderTools (search, cart, menu)                   │   │   │
│  │  │  ├── MobileNav (drawer)                                      │   │   │
│  │  │  ├── CartDrawer (sheet)                                      │   │   │
│  │  │  ├── {children}                                              │   │   │
│  │  │  ├── Footer                                                   │   │   │
│  │  │  ├── BackToTop                                               │   │   │
│  │  │  └── Toaster                                                 │   │   │
│  │  └──────────────────────────────────────────────────────────────┘   │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │                    PAGE COMPONENTS (Mixed)                           │   │
│  │                                                                      │   │
│  │  HomePage (Server)                                                   │   │
│  │  ├── HeroSection                                                     │   │
│  │  │    ├── IlluminatedInitial                                        │   │
│  │  │    ├── HeroTitle                                                 │   │
│  │  │    ├── HeroExcerpt                                               │   │
│  │  │    ├── HeroActions                                               │   │
│  │  │    ├── HeroVessel (animated, Client)                             │   │
│  │  │    └── ScrollIndicator                                           │   │
│  │  ├── FeaturedEssences (Server + Client hydration)                   │   │
│  │  │    └── EssenceGrid → EssenceCard[]                               │   │
│  │  ├── AlchemyPreview (Server)                                        │   │
│  │  └── TestimonialPreview (Server)                                    │   │
│  │                                                                      │   │
│  │  CompendiumPage (Server)                                            │   │
│  │  ├── SectionHeader                                                  │   │
│  │  ├── ProductFilters (Client - interactive)                         │   │
│  │  ├── ProductSort (Client)                                           │   │
│  │  ├── EssenceGrid (Server, streamed)                                 │   │
│  │  │    └── EssenceCard[] (Client for interactions)                   │   │
│  │  └── LoadMoreButton (Client)                                        │   │
│  │                                                                      │   │
│  │  ProductPage (Server)                                               │   │
│  │  ├── ProductGallery (Client - carousel)                             │   │
│  │  ├── ProductInfo                                                    │   │
│  │  │    ├── LatinName                                                 │   │
│  │  │    ├── ProductTitle                                              │   │
│  │  │    ├── HumourBadge                                               │   │
│  │  │    ├── ProductDescription                                       │   │
│  │  │    └── ProductNotes                                              │   │
│  │  ├── ProductVariants (Client)                                       │   │
│  │  ├── QuantitySelector (Client)                                      │   │
│  │  ├── AddToCartButton (Client)                                       │   │
│  │  ├── WishlistButton (Client)                                        │   │
│  │  ├── ProductReviews (Server + Client pagination)                    │   │
│  │  └── RelatedProducts (Server)                                       │   │
│  │                                                                      │   │
│  │  CheckoutPage (Client)                                              │   │
│  │  ├── CheckoutSteps                                                  │   │
│  │  ├── ShippingForm                                                   │   │
│  │  ├── ShippingOptions                                                │   │
│  │  ├── PaymentForm (Stripe Elements)                                  │   │
│  │  └── OrderSummary                                                   │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │                    SHARED COMPONENTS                                 │   │
│  │                                                                      │   │
│  │  UI Primitives (Shadcn)         Manuscript Components               │   │
│  │  ├── Button                     ├── SectionHeader                   │   │
│  │  ├── Card                       ├── OrnamentalRule                  │   │
│  │  ├── Dialog                     ├── IlluminatedInitial              │   │
│  │  ├── Sheet                      ├── AlchemicalSymbol                │   │
│  │  ├── Input                      ├── RarityBadge                     │   │
│  │  ├── Select                     ├── HumourIcon                      │   │
│  │  ├── Checkbox                   └── WaxSeal                         │   │
│  │  ├── Badge                                                          │   │
│  │  ├── Toast                      Product Components                  │   │
│  │  ├── Skeleton                   ├── EssenceCard                     │   │
│  │  └── Accordion                  ├── PriceDisplay                    │   │
│  │                                 ├── RatingStars                     │   │
│  │  Form Components               └── StockIndicator                   │   │
│  │  ├── NewsletterForm                                                 │   │
│  │  ├── ContactForm                Cart Components                     │   │
│  │  ├── ReviewForm                 ├── CartDrawer                      │   │
│  │  ├── AddressForm                ├── CartItem                        │   │
│  │  └── ProfileForm                ├── CartSummary                     │   │
│  │                                 └── QuantityControls                │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
8.2 Key Component Specifications
EssenceCard Component
TypeScript

// src/components/product/essence-card.tsx

interface EssenceCardProps {
  product: Product;
  variant?: 'default' | 'featured' | 'compact';
  showAddToCart?: boolean;
  showWishlist?: boolean;
  priority?: boolean; // Image priority loading
}

// Features:
// - Manuscript-styled card with illumination effect
// - Folio number badge (gold circle, roman numeral)
// - Rarity badge (if rare/limited)
// - Latin name with decorative rule
// - Humour icon with symbol (☾ ☀ ♁ ☁)
// - Hover animation: translateY(-8px) + shadow expansion
// - Add to Cart action with optimistic update
// - Wishlist heart toggle
// - Price display with variant range
// - Reduced motion support
CartDrawer Component
TypeScript

// src/components/cart/cart-drawer.tsx

interface CartDrawerProps {
  // Uses Shadcn Sheet primitive
}

// Features:
// - Slide-out from right (Sheet)
// - "Collection Vial" header
// - Empty state with vial illustration
// - Cart items with quantity controls
// - Humour badges per item
// - Subtotal, tax (GST 9%), total
// - Coupon input
// - "Dispatch to 
