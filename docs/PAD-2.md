Project Architecture Document
Atelier Arôme — Artisanal Aromatherapy E-Commerce Platform
Document Control
Attribute	Value
Version	2.0.0
Status	Final
Classification	Technical Reference
Last Updated	2024
Author	Senior Solutions Architect
Table of Contents
Executive Summary
Vision & Design Philosophy
System Architecture
Technology Stack
Project Structure
Database Architecture
API Specification
Frontend Architecture
Backend Architecture
Authentication & Authorization
State Management
Component Library
Styling Architecture
Accessibility Specification
Performance Requirements
Security Specification
Testing Strategy
Third-Party Integrations
Deployment Architecture
Development Standards
Error Handling & Logging
Appendices
1. Executive Summary
1.1 Project Overview
Atelier Arôme is a luxury artisanal aromatherapy e-commerce platform that transforms the digital shopping experience into an illuminated manuscript journey. The platform combines Renaissance-inspired aesthetics with modern e-commerce functionality to serve discerning customers seeking handcrafted botanical essences.

1.2 Business Objectives
Objective	Success Metric
Premium Brand Experience	NPS > 70, Avg. session duration > 4 min
E-commerce Conversion	Conversion rate > 3.5%
Customer Retention	Repeat purchase rate > 40%
Accessibility Compliance	WCAG 2.1 AAA certification
Performance Excellence	Lighthouse score > 95 all categories
1.3 Scope
In Scope
Full e-commerce functionality (browse, cart, checkout, orders)
User authentication and account management
Product catalog with filtering and search
Subscription/newsletter system
Admin dashboard for content and order management
Multi-language support (English, French)
Payment processing (Stripe)
Email notifications
Testimonial/review system
Out of Scope (Future Phases)
Mobile native applications
Loyalty/rewards program
Wholesale B2B portal
Physical store integration
Subscription box service
1.4 Key Architectural Decisions
Decision	Rationale
Next.js 14 (App Router)	SSR for SEO, RSC for performance, excellent DX
PostgreSQL	Relational integrity for e-commerce, JSON support for flexibility
Prisma ORM	Type-safe database access, excellent migrations
Tailwind CSS 4.0	Utility-first, design system consistency
shadcn/ui	Accessible primitives, full customization control
Stripe	Industry-standard payments, excellent documentation
Resend	Modern email infrastructure, React email support
2. Vision & Design Philosophy
2.1 Aesthetic Direction
text

┌─────────────────────────────────────────────────────────────────┐
│                    DESIGN PHILOSOPHY                            │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   ╔═══════════════════════════════════════════════════════╗    │
│   ║           ILLUMINATED MANUSCRIPT METAPHOR              ║    │
│   ╠═══════════════════════════════════════════════════════╣    │
│   ║                                                        ║    │
│   ║  • Parchment textures and warm tones                  ║    │
│   ║  • Gold leaf accents and metallic highlights          ║    │
│   ║  • Calligraphic typography hierarchy                  ║    │
│   ║  • Hand-drawn botanical illustrations                 ║    │
│   ║  • Wax seal motifs and decorative borders            ║    │
│   ║  • Folio-style navigation and pagination             ║    │
│   ║                                                        ║    │
│   ╚═══════════════════════════════════════════════════════╝    │
│                                                                 │
│   Tone: Luxurious, Artisanal, Historical, Sensory, Poetic      │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
2.2 Design Tokens
Color Palette
text

PRIMARY PALETTE
┌────────────────────────────────────────────────────────────────┐
│                                                                │
│  INK FAMILY                    GOLD FAMILY                     │
│  ┌─────────┐                   ┌─────────┐                     │
│  │ #2A2D26 │ ink               │ #C9A769 │ gold                │
│  │ #4A4D46 │ ink-light         │ #E8D8B6 │ gold-light          │
│  │ #545752 │ ink-muted         │ #A98750 │ gold-dark           │
│  └─────────┘                   │ #8B7355 │ gold-text (a11y)    │
│                                └─────────┘                     │
│                                                                │
│  PARCHMENT FAMILY              ACCENT FAMILY                   │
│  ┌─────────┐                   ┌─────────┐                     │
│  │ #FAF8F5 │ parchment         │ #B8A9C9 │ lavender            │
│  │ #F5F1EB │ parchment-dark    │ #7CB9A0 │ eucalyptus          │
│  │ #E8E4D9 │ parchment-darker  │ #F5D489 │ bergamot            │
│  └─────────┘                   │ #E8B4B8 │ rosehip             │
│                                │ #B87D7D │ rose                 │
│                                │ #9A8C6D │ bronze               │
│                                │ #7C6354 │ sage                 │
│                                └─────────┘                     │
│                                                                │
└────────────────────────────────────────────────────────────────┘
Typography Scale
text

FONT FAMILIES
┌────────────────────────────────────────────────────────────────┐
│                                                                │
│  Display:  Cormorant Garamond (400, 500, 600, 700)            │
│  Body:     Crimson Pro (400, 500, 600 + italics)              │
│  Accent:   Great Vibes (400) — illuminated initials only      │
│  Ornament: Playfair Display (400, 600) — special headings     │
│                                                                │
└────────────────────────────────────────────────────────────────┘

FLUID TYPE SCALE (clamp-based)
┌──────────┬─────────────────────────────────────────┬───────────┐
│ Token    │ Formula                                 │ Use Case  │
├──────────┼─────────────────────────────────────────┼───────────┤
│ text-xs  │ clamp(0.75rem, 0.7rem + 0.25vw, 0.875rem)  │ Captions  │
│ text-sm  │ clamp(0.875rem, 0.8rem + 0.35vw, 1rem)     │ Labels    │
│ text-base│ clamp(1rem, 0.95rem + 0.25vw, 1.125rem)    │ Body      │
│ text-lg  │ clamp(1.125rem, 1rem + 0.5vw, 1.25rem)     │ Lead      │
│ text-xl  │ clamp(1.25rem, 1.1rem + 0.75vw, 1.5rem)    │ H4        │
│ text-2xl │ clamp(1.5rem, 1.25rem + 1.25vw, 2rem)      │ H3        │
│ text-3xl │ clamp(2rem, 1.5rem + 2.5vw, 3rem)          │ H2        │
│ text-4xl │ clamp(2.5rem, 2rem + 2.5vw, 4rem)          │ H1        │
│ text-5xl │ clamp(3rem, 2.5rem + 2.5vw, 5rem)          │ Display   │
└──────────┴─────────────────────────────────────────┴───────────┘
Spacing Scale (Golden Ratio Inspired)
text

┌──────────┬────────────┬─────────────────────────────────────────┐
│ Token    │ Value      │ Use Case                                │
├──────────┼────────────┼─────────────────────────────────────────┤
│ space-3xs│ 0.125rem   │ Hairline gaps                           │
│ space-2xs│ 0.25rem    │ Icon gaps                               │
│ space-xs │ 0.5rem     │ Tight grouping                          │
│ space-sm │ 0.75rem    │ Related elements                        │
│ space-md │ 1rem       │ Base unit                               │
│ space-lg │ 1.5rem     │ Component padding                       │
│ space-xl │ 2rem       │ Section gaps                            │
│ space-2xl│ 3rem       │ Major sections                          │
│ space-3xl│ 4rem       │ Page sections                           │
│ space-4xl│ 6rem       │ Hero spacing                            │
│ space-5xl│ 8rem       │ Major landmarks                         │
│ space-6xl│ 12rem      │ Dramatic spacing                        │
└──────────┴────────────┴─────────────────────────────────────────┘
3. System Architecture
3.1 High-Level Architecture Diagram
text

┌─────────────────────────────────────────────────────────────────────────────┐
│                           ATELIER ARÔME SYSTEM ARCHITECTURE                 │
└─────────────────────────────────────────────────────────────────────────────┘

                                    ┌─────────────┐
                                    │   CLIENTS   │
                                    └──────┬──────┘
                                           │
                    ┌──────────────────────┼──────────────────────┐
                    │                      │                      │
              ┌─────▼─────┐         ┌──────▼──────┐        ┌──────▼──────┐
              │  Desktop  │         │   Mobile    │        │   Tablet    │
              │  Browser  │         │   Browser   │        │   Browser   │
              └─────┬─────┘         └──────┬──────┘        └──────┬──────┘
                    │                      │                      │
                    └──────────────────────┼──────────────────────┘
                                           │
                                           ▼
                    ┌─────────────────────────────────────────────┐
                    │                 CDN (Vercel Edge)           │
                    │  ┌─────────────────────────────────────┐   │
                    │  │  Static Assets / Edge Caching       │   │
                    │  │  • Images (optimized)               │   │
                    │  │  • Fonts (subset, preloaded)        │   │
                    │  │  • CSS/JS bundles                   │   │
                    │  └─────────────────────────────────────┘   │
                    └────────────────────┬────────────────────────┘
                                         │
                                         ▼
┌────────────────────────────────────────────────────────────────────────────┐
│                            NEXT.JS APPLICATION                              │
│  ┌──────────────────────────────────────────────────────────────────────┐  │
│  │                         PRESENTATION LAYER                            │  │
│  │  ┌────────────────┐  ┌────────────────┐  ┌────────────────────────┐  │  │
│  │  │  Server        │  │  Client        │  │  Shared Components     │  │  │
│  │  │  Components    │  │  Components    │  │  (shadcn/ui wrapped)   │  │  │
│  │  │  (RSC)         │  │  (Interactive) │  │                        │  │  │
│  │  └────────────────┘  └────────────────┘  └────────────────────────┘  │  │
│  └──────────────────────────────────────────────────────────────────────┘  │
│  ┌──────────────────────────────────────────────────────────────────────┐  │
│  │                         APPLICATION LAYER                             │  │
│  │  ┌────────────────┐  ┌────────────────┐  ┌────────────────────────┐  │  │
│  │  │  Server        │  │  API Routes    │  │  Middleware            │  │  │
│  │  │  Actions       │  │  (/api/*)      │  │  (Auth, i18n, etc.)    │  │  │
│  │  └────────────────┘  └────────────────┘  └────────────────────────┘  │  │
│  └──────────────────────────────────────────────────────────────────────┘  │
│  ┌──────────────────────────────────────────────────────────────────────┐  │
│  │                          SERVICE LAYER                                │  │
│  │  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌────────────┐  │  │
│  │  │ Product  │ │  Order   │ │  User    │ │  Cart    │ │ Newsletter │  │  │
│  │  │ Service  │ │ Service  │ │ Service  │ │ Service  │ │  Service   │  │  │
│  │  └──────────┘ └──────────┘ └──────────┘ └──────────┘ └────────────┘  │  │
│  └──────────────────────────────────────────────────────────────────────┘  │
│  ┌──────────────────────────────────────────────────────────────────────┐  │
│  │                       DATA ACCESS LAYER                               │  │
│  │  ┌─────────────────────────────────────────────────────────────────┐ │  │
│  │  │                     PRISMA ORM                                   │ │  │
│  │  │  • Type-safe queries  • Migrations  • Connection pooling        │ │  │
│  │  └─────────────────────────────────────────────────────────────────┘ │  │
│  └──────────────────────────────────────────────────────────────────────┘  │
└────────────────────────────────────────────────────────────────────────────┘
                                         │
                    ┌────────────────────┼────────────────────┐
                    │                    │                    │
                    ▼                    ▼                    ▼
         ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐
         │   PostgreSQL    │  │      Redis      │  │   Cloudinary    │
         │   (Neon/Supabase)│  │   (Upstash)     │  │   (Images)      │
         │                 │  │                 │  │                 │
         │  • User data    │  │  • Sessions     │  │  • Product imgs │
         │  • Products     │  │  • Rate limit   │  │  • Thumbnails   │
         │  • Orders       │  │  • Cart cache   │  │  • Transforms   │
         │  • Reviews      │  │                 │  │                 │
         └─────────────────┘  └─────────────────┘  └─────────────────┘

                    ┌────────────────────┼────────────────────┐
                    │                    │                    │
                    ▼                    ▼                    ▼
         ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐
         │     Stripe      │  │     Resend      │  │    Sentry       │
         │   (Payments)    │  │    (Email)      │  │  (Monitoring)   │
         │                 │  │                 │  │                 │
         │  • Checkout     │  │  • Transactional│  │  • Errors       │
         │  • Webhooks     │  │  • Marketing    │  │  • Performance  │
         │  • Refunds      │  │  • Templates    │  │  • Tracing      │
         └─────────────────┘  └─────────────────┘  └─────────────────┘
3.2 Request Flow Diagram
text

┌─────────────────────────────────────────────────────────────────────────────┐
│                            REQUEST FLOW                                      │
└─────────────────────────────────────────────────────────────────────────────┘

    USER ACTION                    SYSTEM PROCESSING                    RESPONSE
    ───────────                    ─────────────────                    ────────

┌─────────────┐
│ User clicks │
│ "Add to     │
│  Vial"      │
└──────┬──────┘
       │
       ▼
┌──────────────┐     ┌─────────────────────────────────────────────────────┐
│ Client Event │────▶│ 1. Event Handler captures click                     │
│ (onClick)    │     │ 2. Extract product ID from data attribute           │
└──────────────┘     │ 3. Optimistic UI update (show added state)          │
                     └────────────────────┬────────────────────────────────┘
                                          │
                                          ▼
                     ┌─────────────────────────────────────────────────────┐
                     │ Server Action: addToCart(productId, quantity)       │
                     │ ┌─────────────────────────────────────────────────┐ │
                     │ │ • Validate session                              │ │
                     │ │ • Check product exists & in stock               │ │
                     │ │ • Get or create cart                            │ │
                     │ │ • Add/update cart item                          │ │
                     │ │ • Calculate totals                              │ │
                     │ │ • Return updated cart                           │ │
                     │ └─────────────────────────────────────────────────┘ │
                     └────────────────────┬────────────────────────────────┘
                                          │
       ┌──────────────────────────────────┼──────────────────────────────────┐
       │                                  │                                  │
       ▼                                  ▼                                  ▼
┌──────────────┐                 ┌──────────────┐                  ┌──────────────┐
│ Update Cart  │                 │ Show Toast   │                  │ Update Cart  │
│ Count Badge  │                 │ Notification │                  │ Drawer       │
│ (Header)     │                 │              │                  │              │
└──────────────┘                 └──────────────┘                  └──────────────┘
       │                                  │                                  │
       └──────────────────────────────────┼──────────────────────────────────┘
                                          │
                                          ▼
                     ┌─────────────────────────────────────────────────────┐
                     │ Screen Reader Announcement:                         │
                     │ "Provence Lavender added to collection. 3 items."   │
                     └─────────────────────────────────────────────────────┘
3.3 Data Flow Diagram
text

┌─────────────────────────────────────────────────────────────────────────────┐
│                            DATA FLOW DIAGRAM                                 │
└─────────────────────────────────────────────────────────────────────────────┘

                              ┌─────────────────┐
                              │    BROWSER      │
                              │  ┌───────────┐  │
                              │  │  Zustand  │  │
                              │  │  Store    │  │
                              │  └─────┬─────┘  │
                              └───────┼─────────┘
                                      │
                    ┌─────────────────┼─────────────────┐
                    │                 │                 │
              ┌─────▼─────┐     ┌─────▼─────┐    ┌──────▼──────┐
              │   Cart    │     │   Auth    │    │  Products   │
              │   State   │     │   State   │    │   Cache     │
              │           │     │           │    │   (SWR)     │
              └─────┬─────┘     └─────┬─────┘    └──────┬──────┘
                    │                 │                 │
                    └─────────────────┼─────────────────┘
                                      │
                                      ▼
                    ┌─────────────────────────────────────┐
                    │         SERVER ACTIONS              │
                    │                                     │
                    │  • addToCart()    • createOrder()  │
                    │  • updateCart()   • updateUser()   │
                    │  • removeItem()   • subscribe()    │
                    │                                     │
                    └─────────────────┬───────────────────┘
                                      │
                                      ▼
                    ┌─────────────────────────────────────┐
                    │         SERVICE LAYER               │
                    │                                     │
                    │  ┌─────────────────────────────┐   │
                    │  │    Business Logic            │   │
                    │  │    • Validation              │   │
                    │  │    • Calculations            │   │
                    │  │    • Transformations         │   │
                    │  └─────────────────────────────┘   │
                    │                                     │
                    └─────────────────┬───────────────────┘
                                      │
                                      ▼
                    ┌─────────────────────────────────────┐
                    │         PRISMA CLIENT               │
                    │                                     │
                    │  prisma.product.findMany()         │
                    │  prisma.cart.upsert()              │
                    │  prisma.order.create()             │
                    │                                     │
                    └─────────────────┬───────────────────┘
                                      │
                                      ▼
                    ┌─────────────────────────────────────┐
                    │         POSTGRESQL                  │
                    │         ┌───────────────────┐       │
                    │         │                   │       │
                    │         │   products        │       │
                    │         │   users           │       │
                    │         │   orders          │       │
                    │         │   cart_items      │       │
                    │         │   ...             │       │
                    │         │                   │       │
                    │         └───────────────────┘       │
                    └─────────────────────────────────────┘
4. Technology Stack
4.1 Stack Overview
text

┌─────────────────────────────────────────────────────────────────────────────┐
│                          TECHNOLOGY STACK                                    │
└─────────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────────┐
│ LAYER          │ TECHNOLOGY              │ VERSION   │ PURPOSE              │
├─────────────────────────────────────────────────────────────────────────────┤
│                │                         │           │                      │
│ FRONTEND       │ Next.js                 │ 14.x      │ React framework      │
│                │ React                   │ 18.x      │ UI library           │
│                │ TypeScript              │ 5.x       │ Type safety          │
│                │ Tailwind CSS            │ 4.0       │ Styling              │
│                │ shadcn/ui               │ latest    │ Component primitives │
│                │ Radix UI                │ latest    │ Accessible primitives│
│                │ Framer Motion           │ 11.x      │ Animations           │
│                │ Zustand                 │ 4.x       │ Client state         │
│                │ React Hook Form         │ 7.x       │ Form handling        │
│                │ Zod                     │ 3.x       │ Schema validation    │
│                │                         │           │                      │
├─────────────────────────────────────────────────────────────────────────────┤
│                │                         │           │                      │
│ BACKEND        │ Next.js API Routes      │ 14.x      │ API endpoints        │
│                │ Server Actions          │ 14.x      │ Server mutations     │
│                │ Prisma                  │ 5.x       │ ORM                  │
│                │ NextAuth.js             │ 5.x       │ Authentication       │
│                │                         │           │                      │
├─────────────────────────────────────────────────────────────────────────────┤
│                │                         │           │                      │
│ DATABASE       │ PostgreSQL              │ 15.x      │ Primary database     │
│                │ Redis (Upstash)         │ latest    │ Caching/sessions     │
│                │                         │           │                      │
├─────────────────────────────────────────────────────────────────────────────┤
│                │                         │           │                      │
│ SERVICES       │ Stripe                  │ latest    │ Payments             │
│                │ Resend                  │ latest    │ Transactional email  │
│                │ Cloudinary              │ latest    │ Image optimization   │
│                │ Sentry                  │ latest    │ Error monitoring     │
│                │ Vercel Analytics        │ latest    │ Web analytics        │
│                │                         │           │                      │
├─────────────────────────────────────────────────────────────────────────────┤
│                │                         │           │                      │
│ INFRASTRUCTURE │ Vercel                  │ -         │ Hosting/CDN          │
│                │ Neon / Supabase         │ -         │ Managed PostgreSQL   │
│                │ GitHub Actions          │ -         │ CI/CD                │
│                │                         │           │                      │
├─────────────────────────────────────────────────────────────────────────────┤
│                │                         │           │                      │
│ DEVELOPMENT    │ ESLint                  │ 8.x       │ Linting              │
│                │ Prettier                │ 3.x       │ Formatting           │
│                │ Husky                   │ 9.x       │ Git hooks            │
│                │ Vitest                  │ 1.x       │ Unit testing         │
│                │ Playwright              │ 1.x       │ E2E testing          │
│                │ Storybook               │ 8.x       │ Component docs       │
│                │                         │           │                      │
└─────────────────────────────────────────────────────────────────────────────┘
4.2 Dependency Manifest
JSON

{
  "name": "atelier-arome",
  "version": "2.0.0",
  "private": true,
  "scripts": {
    "dev": "next dev",
    "build": "prisma generate && next build",
    "start": "next start",
    "lint": "next lint",
    "lint:fix": "next lint --fix",
    "format": "prettier --write .",
    "format:check": "prettier --check .",
    "typecheck": "tsc --noEmit",
    "test": "vitest",
    "test:e2e": "playwright test",
    "test:coverage": "vitest --coverage",
    "db:generate": "prisma generate",
    "db:push": "prisma db push",
    "db:migrate": "prisma migrate dev",
    "db:migrate:prod": "prisma migrate deploy",
    "db:seed": "prisma db seed",
    "db:studio": "prisma studio",
    "storybook": "storybook dev -p 6006",
    "build-storybook": "storybook build",
    "prepare": "husky"
  },
  "dependencies": {
    "@hookform/resolvers": "^3.3.4",
    "@prisma/client": "^5.10.0",
    "@radix-ui/react-accordion": "^1.1.2",
    "@radix-ui/react-alert-dialog": "^1.0.5",
    "@radix-ui/react-aspect-ratio": "^1.0.3",
    "@radix-ui/react-avatar": "^1.0.4",
    "@radix-ui/react-checkbox": "^1.0.4",
    "@radix-ui/react-dialog": "^1.0.5",
    "@radix-ui/react-dropdown-menu": "^2.0.6",
    "@radix-ui/react-label": "^2.0.2",
    "@radix-ui/react-navigation-menu": "^1.1.4",
    "@radix-ui/react-popover": "^1.0.7",
    "@radix-ui/react-radio-group": "^1.1.3",
    "@radix-ui/react-scroll-area": "^1.0.5",
    "@radix-ui/react-select": "^2.0.0",
    "@radix-ui/react-separator": "^1.0.3",
    "@radix-ui/react-sheet": "^1.0.5",
    "@radix-ui/react-slot": "^1.0.2",
    "@radix-ui/react-tabs": "^1.0.4",
    "@radix-ui/react-toast": "^1.1.5",
    "@radix-ui/react-tooltip": "^1.0.7",
    "@radix-ui/react-visually-hidden": "^1.0.3",
    "@sentry/nextjs": "^7.100.0",
    "@stripe/stripe-js": "^3.0.0",
    "@upstash/ratelimit": "^1.0.0",
    "@upstash/redis": "^1.28.0",
    "@vercel/analytics": "^1.2.0",
    "@vercel/speed-insights": "^1.0.0",
    "class-variance-authority": "^0.7.0",
    "clsx": "^2.1.0",
    "cmdk": "^1.0.0",
    "date-fns": "^3.3.0",
    "framer-motion": "^11.0.0",
    "lucide-react": "^0.344.0",
    "next": "14.1.0",
    "next-auth": "^5.0.0-beta.15",
    "next-intl": "^3.9.0",
    "next-themes": "^0.2.1",
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "react-hook-form": "^7.50.0",
    "resend": "^3.2.0",
    "sonner": "^1.4.0",
    "stripe": "^14.18.0",
    "swr": "^2.2.0",
    "tailwind-merge": "^2.2.0",
    "tailwindcss-animate": "^1.0.7",
    "zod": "^3.22.0",
    "zustand": "^4.5.0"
  },
  "devDependencies": {
    "@playwright/test": "^1.42.0",
    "@storybook/addon-essentials": "^8.0.0",
    "@storybook/addon-interactions": "^8.0.0",
    "@storybook/addon-links": "^8.0.0",
    "@storybook/blocks": "^8.0.0",
    "@storybook/nextjs": "^8.0.0",
    "@storybook/react": "^8.0.0",
    "@storybook/test": "^8.0.0",
    "@testing-library/jest-dom": "^6.4.0",
    "@testing-library/react": "^14.2.0",
    "@types/node": "^20.11.0",
    "@types/react": "^18.2.0",
    "@types/react-dom": "^18.2.0",
    "@vitejs/plugin-react": "^4.2.0",
    "@vitest/coverage-v8": "^1.3.0",
    "autoprefixer": "^10.4.0",
    "eslint": "^8.56.0",
    "eslint-config-next": "14.1.0",
    "eslint-config-prettier": "^9.1.0",
    "eslint-plugin-storybook": "^0.8.0",
    "husky": "^9.0.0",
    "jsdom": "^24.0.0",
    "lint-staged": "^15.2.0",
    "postcss": "^8.4.0",
    "prettier": "^3.2.0",
    "prettier-plugin-tailwindcss": "^0.5.0",
    "prisma": "^5.10.0",
    "storybook": "^8.0.0",
    "tailwindcss": "^4.0.0",
    "typescript": "^5.3.0",
    "vitest": "^1.3.0"
  },
  "prisma": {
    "seed": "tsx prisma/seed.ts"
  },
  "lint-staged": {
    "*.{js,jsx,ts,tsx}": [
      "eslint --fix",
      "prettier --write"
    ],
    "*.{json,md,css}": [
      "prettier --write"
    ]
  }
}
5. Project Structure
5.1 Directory Tree
text

atelier-arome/
├── .github/
│   ├── workflows/
│   │   ├── ci.yml                    # Continuous Integration
│   │   ├── deploy-preview.yml        # Preview deployments
│   │   └── deploy-production.yml     # Production deployments
│   ├── ISSUE_TEMPLATE/
│   │   ├── bug_report.md
│   │   └── feature_request.md
│   └── PULL_REQUEST_TEMPLATE.md
│
├── .husky/
│   ├── pre-commit                    # Lint-staged
│   └── pre-push                      # Type check
│
├── .storybook/
│   ├── main.ts                       # Storybook config
│   ├── preview.ts                    # Global decorators
│   └── theme.ts                      # Custom theme
│
├── prisma/
│   ├── migrations/                   # Database migrations
│   │   └── 20240101000000_init/
│   ├── schema.prisma                 # Database schema
│   └── seed.ts                       # Seed data
│
├── public/
│   ├── fonts/                        # Self-hosted fonts
│   │   ├── cormorant-garamond-*.woff2
│   │   └── crimson-pro-*.woff2
│   ├── images/
│   │   ├── botanicals/               # Botanical illustrations
│   │   ├── products/                 # Product images
│   │   └── textures/                 # Background textures
│   ├── icons/
│   │   ├── favicon.svg
│   │   ├── apple-touch-icon.png
│   │   └── site.webmanifest
│   └── og-image.jpg                  # Social preview
│
├── src/
│   ├── app/                          # Next.js App Router
│   │   ├── (auth)/                   # Auth route group
│   │   │   ├── login/
│   │   │   │   └── page.tsx
│   │   │   ├── register/
│   │   │   │   └── page.tsx
│   │   │   ├── forgot-password/
│   │   │   │   └── page.tsx
│   │   │   └── layout.tsx
│   │   │
│   │   ├── (shop)/                   # Shop route group
│   │   │   ├── compendium/           # Products listing
│   │   │   │   ├── page.tsx
│   │   │   │   ├── loading.tsx
│   │   │   │   └── [slug]/
│   │   │   │       ├── page.tsx
│   │   │   │       └── loading.tsx
│   │   │   ├── alchemy/              # Process page
│   │   │   │   └── page.tsx
│   │   │   ├── atelier/              # About page
│   │   │   │   └── page.tsx
│   │   │   ├── manuscript/           # Testimonials
│   │   │   │   └── page.tsx
│   │   │   └── layout.tsx
│   │   │
│   │   ├── (checkout)/               # Checkout route group
│   │   │   ├── cart/
│   │   │   │   └── page.tsx
│   │   │   ├── checkout/
│   │   │   │   └── page.tsx
│   │   │   ├── confirmation/
│   │   │   │   └── [orderId]/
│   │   │   │       └── page.tsx
│   │   │   └── layout.tsx
│   │   │
│   │   ├── (account)/                # Account route group
│   │   │   ├── account/
│   │   │   │   ├── page.tsx          # Dashboard
│   │   │   │   ├── orders/
│   │   │   │   │   ├── page.tsx
│   │   │   │   │   └── [orderId]/
│   │   │   │   │       └── page.tsx
│   │   │   │   ├── settings/
│   │   │   │   │   └── page.tsx
│   │   │   │   └── addresses/
│   │   │   │       └── page.tsx
│   │   │   └── layout.tsx
│   │   │
│   │   ├── admin/                    # Admin dashboard
│   │   │   ├── page.tsx
│   │   │   ├── layout.tsx
│   │   │   ├── products/
│   │   │   │   ├── page.tsx
│   │   │   │   ├── new/
│   │   │   │   │   └── page.tsx
│   │   │   │   └── [id]/
│   │   │   │       └── page.tsx
│   │   │   ├── orders/
│   │   │   │   ├── page.tsx
│   │   │   │   └── [id]/
│   │   │   │       └── page.tsx
│   │   │   ├── customers/
│   │   │   │   └── page.tsx
│   │   │   └── settings/
│   │   │       └── page.tsx
│   │   │
│   │   ├── api/                      # API Routes
│   │   │   ├── auth/
│   │   │   │   └── [...nextauth]/
│   │   │   │       └── route.ts
│   │   │   ├── products/
│   │   │   │   ├── route.ts          # GET products
│   │   │   │   └── [id]/
│   │   │   │       └── route.ts
│   │   │   ├── cart/
│   │   │   │   └── route.ts
│   │   │   ├── orders/
│   │   │   │   └── route.ts
│   │   │   ├── newsletter/
│   │   │   │   └── route.ts
│   │   │   ├── webhooks/
│   │   │   │   └── stripe/
│   │   │   │       └── route.ts
│   │   │   └── health/
│   │   │       └── route.ts
│   │   │
│   │   ├── layout.tsx                # Root layout
│   │   ├── page.tsx                  # Home page
│   │   ├── loading.tsx               # Global loading
│   │   ├── error.tsx                 # Error boundary
│   │   ├── not-found.tsx             # 404 page
│   │   ├── global-error.tsx          # Global error
│   │   ├── sitemap.ts                # Dynamic sitemap
│   │   ├── robots.ts                 # Robots.txt
│   │   └── manifest.ts               # Web manifest
│   │
│   ├── components/                   # React Components
│   │   ├── ui/                       # shadcn/ui components
│   │   │   ├── button.tsx
│   │   │   ├── card.tsx
│   │   │   ├── dialog.tsx
│   │   │   ├── dropdown-menu.tsx
│   │   │   ├── form.tsx
│   │   │   ├── input.tsx
│   │   │   ├── label.tsx
│   │   │   ├── select.tsx
│   │   │   ├── sheet.tsx
│   │   │   ├── skeleton.tsx
│   │   │   ├── sonner.tsx
│   │   │   ├── tabs.tsx
│   │   │   ├── textarea.tsx
│   │   │   └── tooltip.tsx
│   │   │
│   │   ├── layout/                   # Layout components
│   │   │   ├── header/
│   │   │   │   ├── header.tsx
│   │   │   │   ├── header-nav.tsx
│   │   │   │   ├── header-seal.tsx
│   │   │   │   ├── header-tools.tsx
│   │   │   │   ├── mobile-nav.tsx
│   │   │   │   └── index.ts
│   │   │   ├── footer/
│   │   │   │   ├── footer.tsx
│   │   │   │   ├── footer-nav.tsx
│   │   │   │   ├── footer-social.tsx
│   │   │   │   └── index.ts
│   │   │   ├── cart-drawer/
│   │   │   │   ├── cart-drawer.tsx
│   │   │   │   ├── cart-item.tsx
│   │   │   │   ├── cart-summary.tsx
│   │   │   │   └── index.ts
│   │   │   └── providers/
│   │   │       ├── theme-provider.tsx
│   │   │       ├── cart-provider.tsx
│   │   │       ├── toast-provider.tsx
│   │   │       └── index.ts
│   │   │
│   │   ├── shared/                   # Shared components
│   │   │   ├── section-header.tsx
│   │   │   ├── section-border.tsx
│   │   │   ├── illuminated-initial.tsx
│   │   │   ├── gold-leaf-background.tsx
│   │   │   ├── parchment-texture.tsx
│   │   │   ├── wax-seal.tsx
│   │   │   ├── botanical-illustration.tsx
│   │   │   ├── decorative-rule.tsx
│   │   │   ├── page-wrapper.tsx
│   │   │   ├── skip-link.tsx
│   │   │   ├── back-to-top.tsx
│   │   │   └── index.ts
│   │   │
│   │   ├── products/                 # Product components
│   │   │   ├── essence-card.tsx
│   │   │   ├── essence-grid.tsx
│   │   │   ├── essence-filters.tsx
│   │   │   ├── essence-sort.tsx
│   │   │   ├── essence-detail.tsx
│   │   │   ├── humour-badge.tsx
│   │   │   ├── rarity-badge.tsx
│   │   │   └── index.ts
│   │   │
│   │   ├── home/                     # Home page components
│   │   │   ├── hero.tsx
│   │   │   ├── hero-vessel.tsx
│   │   │   ├── hero-botanicals.tsx
│   │   │   ├── featured-essences.tsx
│   │   │   ├── alchemy-preview.tsx
│   │   │   ├── testimonials-preview.tsx
│   │   │   ├── newsletter-signup.tsx
│   │   │   └── index.ts
│   │   │
│   │   ├── alchemy/                  # Alchemy page components
│   │   │   ├── alchemy-step.tsx
│   │   │   ├── alchemy-process.tsx
│   │   │   ├── apparatus-gallery.tsx
│   │   │   └── index.ts
│   │   │
│   │   ├── testimonials/             # Testimonial components
│   │   │   ├── manuscript-entry.tsx
│   │   │   ├── manuscript-grid.tsx
│   │   │   ├── manuscript-pagination.tsx
│   │   │   └── index.ts
│   │   │
│   │   ├── checkout/                 # Checkout components
│   │   │   ├── checkout-form.tsx
│   │   │   ├── order-summary.tsx
│   │   │   ├── shipping-form.tsx
│   │   │   ├── payment-form.tsx
│   │   │   └── index.ts
│   │   │
│   │   ├── account/                  # Account components
│   │   │   ├── order-history.tsx
│   │   │   ├── order-detail.tsx
│   │   │   ├── address-book.tsx
│   │   │   ├── profile-form.tsx
│   │   │   └── index.ts
│   │   │
│   │   ├── admin/                    # Admin components
│   │   │   ├── dashboard-stats.tsx
│   │   │   ├── product-form.tsx
│   │   │   ├── order-table.tsx
│   │   │   ├── customer-table.tsx
│   │   │   └── index.ts
│   │   │
│   │   └── forms/                    # Form components
│   │       ├── newsletter-form.tsx
│   │       ├── contact-form.tsx
│   │       ├── login-form.tsx
│   │       ├── register-form.tsx
│   │       └── index.ts
│   │
│   ├── lib/                          # Utilities & Config
│   │   ├── prisma.ts                 # Prisma client
│   │   ├── auth.ts                   # NextAuth config
│   │   ├── stripe.ts                 # Stripe config
│   │   ├── resend.ts                 # Email config
│   │   ├── redis.ts                  # Redis client
│   │   ├── cloudinary.ts             # Image config
│   │   ├── utils.ts                  # General utilities
│   │   ├── cn.ts                     # Class merging
│   │   ├── constants.ts              # App constants
│   │   ├── config.ts                 # Environment config
│   │   └── validations/              # Zod schemas
│   │       ├── auth.ts
│   │       ├── product.ts
│   │       ├── order.ts
│   │       ├── cart.ts
│   │       └── newsletter.ts
│   │
│   ├── services/                     # Business Logic
│   │   ├── product.service.ts
│   │   ├── cart.service.ts
│   │   ├── order.service.ts
│   │   ├── user.service.ts
│   │   ├── newsletter.service.ts
│   │   ├── payment.service.ts
│   │   └── email.service.ts
│   │
│   ├── actions/                      # Server Actions
│   │   ├── cart.actions.ts
│   │   ├── order.actions.ts
│   │   ├── user.actions.ts
│   │   ├── newsletter.actions.ts
│   │   └── admin.actions.ts
│   │
│   ├── hooks/                        # Custom Hooks
│   │   ├── use-cart.ts
│   │   ├── use-products.ts
│   │   ├── use-auth.ts
│   │   ├── use-media-query.ts
│   │   ├── use-reduced-motion.ts
│   │   ├── use-scroll-position.ts
│   │   ├── use-intersection.ts
│   │   ├── use-local-storage.ts
│   │   ├── use-debounce.ts
│   │   └── use-toast.ts
│   │
│   ├── stores/                       # Zustand Stores
│   │   ├── cart.store.ts
│   │   ├── ui.store.ts
│   │   └── filter.store.ts
│   │
│   ├── types/                        # TypeScript Types
│   │   ├── product.types.ts
│   │   ├── cart.types.ts
│   │   ├── order.types.ts
│   │   ├── user.types.ts
│   │   ├── api.types.ts
│   │   └── index.ts
│   │
│   ├── styles/                       # Global Styles
│   │   ├── globals.css               # Global CSS + Tailwind
│   │   ├── fonts.css                 # Font-face declarations
│   │   ├── animations.css            # Keyframe animations
│   │   └── print.css                 # Print styles
│   │
│   ├── emails/                       # React Email Templates
│   │   ├── order-confirmation.tsx
│   │   ├── shipping-notification.tsx
│   │   ├── welcome.tsx
│   │   ├── newsletter-welcome.tsx
│   │   ├── password-reset.tsx
│   │   └── components/
│   │       ├── email-layout.tsx
│   │       ├── email-header.tsx
│   │       └── email-footer.tsx
│   │
│   ├── i18n/                         # Internationalization
│   │   ├── config.ts
│   │   ├── request.ts
│   │   └── messages/
│   │       ├── en.json
│   │       └── fr.json
│   │
│   └── middleware.ts                 # Next.js middleware
│
├── tests/                            # Test Files
│   ├── unit/                         # Unit tests
│   │   ├── services/
│   │   ├── hooks/
│   │   └── utils/
│   ├── integration/                  # Integration tests
│   │   ├── api/
│   │   └── components/
│   └── e2e/                          # End-to-end tests
│       ├── checkout.spec.ts
│       ├── authentication.spec.ts
│       └── products.spec.ts
│
├── .env.example                      # Environment template
├── .env.local                        # Local environment (gitignored)
├── .eslintrc.json                    # ESLint config
├── .prettierrc                       # Prettier config
├── .gitignore
├── components.json                   # shadcn/ui config
├── next.config.js                    # Next.js config
├── tailwind.config.ts                # Tailwind config
├── tsconfig.json                     # TypeScript config
├── vitest.config.ts                  # Vitest config
├── playwright.config.ts              # Playwright config
└── README.md
5.2 Module Dependency Graph
text

┌─────────────────────────────────────────────────────────────────────────────┐
│                       MODULE DEPENDENCY GRAPH                                │
└─────────────────────────────────────────────────────────────────────────────┘

                              ┌─────────────────┐
                              │   app/page.tsx  │
                              │   (Entry Point) │
                              └────────┬────────┘
                                       │
                    ┌──────────────────┼──────────────────┐
                    │                  │                  │
                    ▼                  ▼                  ▼
           ┌───────────────┐  ┌───────────────┐  ┌───────────────┐
           │   app/       │  │  components/  │  │    lib/       │
           │   layout.tsx  │  │   layout/     │  │   config.ts   │
           └───────┬───────┘  └───────┬───────┘  └───────┬───────┘
                   │                  │                  │
                   ▼                  ▼                  ▼
           ┌───────────────────────────────────────────────────────┐
           │                     PROVIDERS                          │
           │  ┌─────────┐  ┌─────────┐  ┌─────────┐  ┌─────────┐  │
           │  │ Theme   │  │  Cart   │  │  Auth   │  │  Toast  │  │
           │  │Provider │  │Provider │  │Provider │  │Provider │  │
           │  └────┬────┘  └────┬────┘  └────┬────┘  └────┬────┘  │
           └───────┼────────────┼────────────┼────────────┼────────┘
                   │            │            │            │
                   ▼            ▼            ▼            ▼
           ┌───────────────────────────────────────────────────────┐
           │                     STORES                             │
           │  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐   │
           │  │ cart.store  │  │  ui.store   │  │filter.store │   │
           │  └──────┬──────┘  └──────┬──────┘  └──────┬──────┘   │
           └─────────┼────────────────┼────────────────┼───────────┘
                     │                │                │
                     └────────────────┼────────────────┘
                                      │
                                      ▼
           ┌───────────────────────────────────────────────────────┐
           │                     HOOKS                              │
           │  ┌──────────┐  ┌──────────┐  ┌──────────┐            │
           │  │ use-cart │  │ use-auth │  │use-toast │  ...       │
           │  └────┬─────┘  └────┬─────┘  └────┬─────┘            │
           └───────┼─────────────┼─────────────┼───────────────────┘
                   │             │             │
                   ▼             ▼             ▼
           ┌───────────────────────────────────────────────────────┐
           │                   COMPONENTS                           │
           │  ┌────────────────────────────────────────────────┐   │
           │  │                 PAGE COMPONENTS                 │   │
           │  │  ┌─────┐  ┌─────────┐  ┌─────────┐  ┌───────┐  │   │
           │  │  │Hero │  │Essence  │  │Checkout │  │Account│  │   │
           │  │  │     │  │Grid     │  │Form     │  │       │  │   │
           │  │  └──┬──┘  └────┬────┘  └────┬────┘  └───┬───┘  │   │
           │  └─────┼──────────┼────────────┼──────────┼────────┘   │
           │        │          │            │          │            │
           │        ▼          ▼            ▼          ▼            │
           │  ┌────────────────────────────────────────────────┐   │
           │  │              SHARED COMPONENTS                  │   │
           │  │  ┌───────┐  ┌───────┐  ┌───────┐  ┌───────┐   │   │
           │  │  │Section│  │Illumin│  │Wax    │  │Decorat│   │   │
           │  │  │Header │  │Initial│  │Seal   │  │iveRule│   │   │
           │  │  └───────┘  └───────┘  └───────┘  └───────┘   │   │
           │  └─────────────────────┬──────────────────────────┘   │
           └────────────────────────┼──────────────────────────────┘
                                    │
                                    ▼
           ┌───────────────────────────────────────────────────────┐
           │                   UI COMPONENTS                        │
           │  ┌────────────────────────────────────────────────┐   │
           │  │                  shadcn/ui                      │   │
           │  │  ┌──────┐ ┌──────┐ ┌──────┐ ┌──────┐ ┌──────┐ │   │
           │  │  │Button│ │Dialog│ │Form  │ │Sheet │ │Toast │ │   │
           │  │  └──────┘ └──────┘ └──────┘ └──────┘ └──────┘ │   │
           │  └────────────────────────────────────────────────┘   │
           └───────────────────────────────────────────────────────┘
                                    │
                                    ▼
           ┌───────────────────────────────────────────────────────┐
           │                 SERVER ACTIONS                         │
           │  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐   │
           │  │cart.actions │  │order.actions│  │user.actions │   │
           │  └──────┬──────┘  └──────┬──────┘  └──────┬──────┘   │
           └─────────┼────────────────┼────────────────┼───────────┘
                     │                │                │
                     └────────────────┼────────────────┘
                                      │
                                      ▼
           ┌───────────────────────────────────────────────────────┐
           │                    SERVICES                            │
           │  ┌──────────────┐  ┌──────────────┐  ┌────────────┐  │
           │  │cart.service  │  │order.service │  │payment.svc │  │
           │  └──────┬───────┘  └──────┬───────┘  └──────┬─────┘  │
           └─────────┼─────────────────┼─────────────────┼─────────┘
                     │                 │                 │
                     └─────────────────┼─────────────────┘
                                       │
                                       ▼
           ┌───────────────────────────────────────────────────────┐
           │                    PRISMA ORM                          │
           │            ┌───────────────────────────┐              │
           │            │    prisma.ts (client)     │              │
           │            └─────────────┬─────────────┘              │
           └──────────────────────────┼────────────────────────────┘
                                      │
                                      ▼
           ┌───────────────────────────────────────────────────────┐
           │                   POSTGRESQL                           │
           └───────────────────────────────────────────────────────┘
6. Database Architecture
6.1 Entity Relationship Diagram
text

┌─────────────────────────────────────────────────────────────────────────────┐
│                     ENTITY RELATIONSHIP DIAGRAM                              │
└─────────────────────────────────────────────────────────────────────────────┘

┌───────────────────────┐       ┌───────────────────────┐
│        USER           │       │       ACCOUNT         │
├───────────────────────┤       ├───────────────────────┤
│ id          UUID  PK  │──┐    │ id           UUID PK  │
│ email       VARCHAR   │  │    │ userId       UUID FK  │──┐
│ emailVerified DATETIME│  │    │ type         VARCHAR  │  │
│ name        VARCHAR   │  │    │ provider     VARCHAR  │  │
│ password    VARCHAR?  │  │    │ providerAcctId VARCHAR│  │
│ image       VARCHAR?  │  │    │ refresh_token TEXT?   │  │
│ role        ENUM      │  │    │ access_token  TEXT?   │  │
│ createdAt   DATETIME  │  │    │ expires_at   INT?     │  │
│ updatedAt   DATETIME  │  │    │ token_type   VARCHAR? │  │
└───────────────────────┘  │    └───────────────────────┘  │
         │                 │                               │
         │ 1              │                               │
         │                 └───────────────────────────────┘
         │                              ∞
         │
         │ 1                    ┌───────────────────────┐
         │                      │       SESSION         │
         │                      ├───────────────────────┤
         ├──────────────────────│ id           UUID PK  │
         │                      │ userId       UUID FK  │
         │                      │ sessionToken VARCHAR  │
         │                      │ expires      DATETIME │
         │                      └───────────────────────┘
         │
         │ 1
         ├──────────────────────────────────────────────────────────┐
         │                                                          │
         ▼ ∞                                                        ▼ ∞
┌───────────────────────┐                              ┌───────────────────────┐
│       ADDRESS         │                              │        ORDER          │
├───────────────────────┤                              ├───────────────────────┤
│ id          UUID  PK  │                              │ id           UUID PK  │
│ userId      UUID  FK  │                              │ userId       UUID FK  │
│ type        ENUM      │                              │ orderNumber  VARCHAR  │
│ firstName   VARCHAR   │                              │ status       ENUM     │
│ lastName    VARCHAR   │                              │ subtotal     DECIMAL  │
│ street      VARCHAR   │                              │ tax          DECIMAL  │
│ city        VARCHAR   │                              │ shipping     DECIMAL  │
│ state       VARCHAR   │                              │ total        DECIMAL  │
│ postalCode  VARCHAR   │                              │ currency     VARCHAR  │
│ country     VARCHAR   │                              │ shippingAddressId UUID│
│ phone       VARCHAR?  │                              │ billingAddressId  UUID│
│ isDefault   BOOLEAN   │                              │ stripePaymentId VARCHAR│
│ createdAt   DATETIME  │                              │ notes        TEXT?    │
│ updatedAt   DATETIME  │                              │ createdAt    DATETIME │
└───────────────────────┘                              │ updatedAt    DATETIME │
                                                       └───────────────────────┘
                                                                │
                                                                │ 1
                                                                │
                                                                ▼ ∞
                                                       ┌───────────────────────┐
                                                       │      ORDER_ITEM       │
                                                       ├───────────────────────┤
                                                       │ id           UUID PK  │
         ┌─────────────────────────────────────────────│ orderId      UUID FK  │
         │                                             │ productId    UUID FK  │
         │                                             │ quantity     INT      │
         │                                             │ unitPrice    DECIMAL  │
         │                                             │ totalPrice   DECIMAL  │
         │                                             │ createdAt    DATETIME │
         │                                             └───────────────────────┘
         │                                                        ▲
         │                                                        │ ∞
         │                                                        │
         │ ∞                                                      │ 1
         ▼                                                        │
┌───────────────────────┐      ┌───────────────────────┐         │
│       PRODUCT         │      │     PRODUCT_IMAGE     │         │
├───────────────────────┤      ├───────────────────────┤         │
│ id          UUID  PK  │──────│ id           UUID PK  │         │
│ slug        VARCHAR   │  1  ∞│ productId    UUID FK  │         │
│ latinName   VARCHAR   │      │ url          VARCHAR  │         │
│ commonName  VARCHAR   │      │ alt          VARCHAR  │         │
│ description TEXT      │      │ position     INT      │         │
│ humour      ENUM      │      │ createdAt    DATETIME │         │
│ rarity      ENUM      │      └───────────────────────┘         │
│ season      ENUM      │                                        │
│ notes       JSON      │──────────────────────────────────────────
│ extraction  VARCHAR   │
│ origin      VARCHAR   │
│ price       DECIMAL   │      ┌───────────────────────┐
│ compareAtPrice DECIMAL│      │       CATEGORY        │
│ sku         VARCHAR   │      ├───────────────────────┤
│ inventory   INT       │      │ id           UUID PK  │
│ weight      DECIMAL?  │  ∞  1│ name         VARCHAR  │
│ categoryId  UUID  FK  │──────│ slug         VARCHAR  │
│ featured    BOOLEAN   │      │ description  TEXT?    │
│ status      ENUM      │      │ position     INT      │
│ createdAt   DATETIME  │      │ createdAt    DATETIME │
│ updatedAt   DATETIME  │      └───────────────────────┘
└───────────────────────┘
         │
         │ 1
         │
         ▼ ∞
┌───────────────────────┐
│       CART_ITEM       │
├───────────────────────┤
│ id          UUID  PK  │
│ cartId      UUID  FK  │──┐
│ productId   UUID  FK  │  │
│ quantity    INT       │  │
│ createdAt   DATETIME  │  │
│ updatedAt   DATETIME  │  │
└───────────────────────┘  │
                           │ ∞
                           │
                           │ 1
                           ▼
                  ┌───────────────────────┐
                  │         CART          │
                  ├───────────────────────┤
                  │ id           UUID PK  │
                  │ userId       UUID FK? │ (nullable for guest)
                  │ sessionId    VARCHAR? │ (for guest carts)
                  │ expiresAt    DATETIME?│
                  │ createdAt    DATETIME │
                  │ updatedAt    DATETIME │
                  └───────────────────────┘

┌───────────────────────┐       ┌───────────────────────┐
│       REVIEW          │       │     NEWSLETTER        │
├───────────────────────┤       ├───────────────────────┤
│ id          UUID  PK  │       │ id           UUID PK  │
│ productId   UUID  FK  │       │ email        VARCHAR  │
│ userId      UUID  FK  │       │ name         VARCHAR? │
│ rating      INT       │       │ status       ENUM     │
│ title       VARCHAR?  │       │ source       VARCHAR  │
│ content     TEXT      │       │ subscribedAt DATETIME │
│ verified    BOOLEAN   │       │ unsubscribedAt DATETIME?│
│ featured    BOOLEAN   │       │ createdAt    DATETIME │
│ status      ENUM      │       └───────────────────────┘
│ createdAt   DATETIME  │
│ updatedAt   DATETIME  │
└───────────────────────┘
6.2 Prisma Schema
prisma

// prisma/schema.prisma

generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider  = "postgresql"
  url       = env("DATABASE_URL")
  directUrl = env("DIRECT_URL")
}

// ============================================
// ENUMS
// ============================================

enum UserRole {
  CUSTOMER
  ADMIN
  SUPER_ADMIN
}

enum AddressType {
  SHIPPING
  BILLING
}

enum OrderStatus {
  PENDING
  CONFIRMED
  PROCESSING
  SHIPPED
  DELIVERED
  CANCELLED
  REFUNDED
}

enum ProductStatus {
  DRAFT
  ACTIVE
  ARCHIVED
}

enum Humour {
  CALMING
  UPLIFTING
  GROUNDING
  CLARIFYING
}

enum Rarity {
  COMMON
  RARE
  LIMITED
}

enum Season {
  SPRING
  SUMMER
  AUTUMN
  WINTER
}

enum ReviewStatus {
  PENDING
  APPROVED
  REJECTED
}

enum NewsletterStatus {
  ACTIVE
  UNSUBSCRIBED
  BOUNCED
}

// ============================================
// AUTHENTICATION MODELS (NextAuth.js)
// ============================================

model User {
  id            String    @id @default(cuid())
  email         String    @unique
  emailVerified DateTime?
  name          String?
  password      String?   // Hashed, nullable for OAuth users
  image         String?
  role          UserRole  @default(CUSTOMER)
  
  // Relations
  accounts      Account[]
  sessions      Session[]
  addresses     Address[]
  orders        Order[]
  reviews       Review[]
  cart          Cart?
  
  createdAt     DateTime  @default(now())
  updatedAt     DateTime  @updatedAt
  
  @@index([email])
  @@map("users")
}

model Account {
  id                String  @id @default(cuid())
  userId            String
  type              String
  provider          String
  providerAccountId String
  refresh_token     String? @db.Text
  access_token      String? @db.Text
  expires_at        Int?
  token_type        String?
  scope             String?
  id_token          String? @db.Text
  session_state     String?
  
  user User @relation(fields: [userId], references: [id], onDelete: Cascade)
  
  @@unique([provider, providerAccountId])
  @@index([userId])
  @@map("accounts")
}

model Session {
  id           String   @id @default(cuid())
  sessionToken String   @unique
  userId       String
  expires      DateTime
  
  user User @relation(fields: [userId], references: [id], onDelete: Cascade)
  
  @@index([userId])
  @@map("sessions")
}

model VerificationToken {
  identifier String
  token      String   @unique
  expires    DateTime
  
  @@unique([identifier, token])
  @@map("verification_tokens")
}

// ============================================
// USER RELATED MODELS
// ============================================

model Address {
  id         String      @id @default(cuid())
  userId     String
  type       AddressType
  firstName  String
  lastName   String
  company    String?
  street     String
  apartment  String?
  city       String
  state      String
  postalCode String
  country    String      @default("US")
  phone      String?
  isDefault  Boolean     @default(false)
  
  user User @relation(fields: [userId], references: [id], onDelete: Cascade)
  
  // Orders using this address
  shippingOrders Order[] @relation("ShippingAddress")
  billingOrders  Order[] @relation("BillingAddress")
  
  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt
  
  @@index([userId])
  @@index([userId, type])
  @@map("addresses")
}

// ============================================
// PRODUCT MODELS
// ============================================

model Category {
  id          String    @id @default(cuid())
  name        String
  slug        String    @unique
  description String?   @db.Text
  image       String?
  position    Int       @default(0)
  
  products Product[]
  
  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt
  
  @@map("categories")
}

model Product {
  id             String        @id @default(cuid())
  slug           String        @unique
  sku            String        @unique
  latinName      String
  commonName     String
  description    String        @db.Text
  shortDescription String?     @db.Text
  
  // Atelier-specific attributes
  humour         Humour
  rarity         Rarity        @default(COMMON)
  season         Season
  notes          Json          // Array of scent notes
  extraction     String        // e.g., "Steam Distillation"
  origin         String        // e.g., "Provence, France"
  
  // Pricing
  price          Decimal       @db.Decimal(10, 2)
  compareAtPrice Decimal?      @db.Decimal(10, 2)
  costPrice      Decimal?      @db.Decimal(10, 2)
  
  // Inventory
  inventory      Int           @default(0)
  lowStockThreshold Int        @default(5)
  trackInventory Boolean       @default(true)
  
  // Physical attributes
  weight         Decimal?      @db.Decimal(6, 2) // in grams
  volume         Decimal?      @db.Decimal(6, 2) // in ml
  
  // Organization
  categoryId     String?
  category       Category?     @relation(fields: [categoryId], references: [id])
  
  // Visibility
  featured       Boolean       @default(false)
  status         ProductStatus @default(DRAFT)
  
  // SEO
  metaTitle      String?
  metaDescription String?      @db.Text
  
  // Relations
  images         ProductImage[]
  cartItems      CartItem[]
  orderItems     OrderItem[]
  reviews        Review[]
  
  createdAt      DateTime      @default(now())
  updatedAt      DateTime      @updatedAt
  
  @@index([slug])
  @@index([sku])
  @@index([status])
  @@index([categoryId])
  @@index([humour])
  @@index([featured, status])
  @@map("products")
}

model ProductImage {
  id        String  @id @default(cuid())
  productId String
  url       String
  alt       String
  position  Int     @default(0)
  
  product Product @relation(fields: [productId], references: [id], onDelete: Cascade)
  
  createdAt DateTime @default(now())
  
  @@index([productId])
  @@map("product_images")
}

// ============================================
// CART MODELS
// ============================================

model Cart {
  id        String     @id @default(cuid())
  userId    String?    @unique
  sessionId String?    @unique // For guest carts
  expiresAt DateTime?  // Guest carts expire
  
  user  User?      @relation(fields: [userId], references: [id], onDelete: Cascade)
  items CartItem[]
  
  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt
  
  @@index([sessionId])
  @@index([expiresAt])
  @@map("carts")
}

model CartItem {
  id        String @id @default(cuid())
  cartId    String
  productId String
  quantity  Int    @default(1)
  
  cart    Cart    @relation(fields: [cartId], references: [id], onDelete: Cascade)
  product Product @relation(fields: [productId], references: [id], onDelete: Cascade)
  
  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt
  
  @@unique([cartId, productId])
  @@index([cartId])
  @@index([productId])
  @@map("cart_items")
}

// ============================================
// ORDER MODELS
// ============================================

model Order {
  id                String      @id @default(cuid())
  orderNumber       String      @unique
  userId            String
  
  // Status
  status            OrderStatus @default(PENDING)
  
  // Pricing
  subtotal          Decimal     @db.Decimal(10, 2)
  tax               Decimal     @db.Decimal(10, 2) @default(0)
  shippingCost      Decimal     @db.Decimal(10, 2) @default(0)
  discount          Decimal     @db.Decimal(10, 2) @default(0)
  total             Decimal     @db.Decimal(10, 2)
  currency          String      @default("USD")
  
  // Addresses (snapshot at time of order)
  shippingAddressId String?
  billingAddressId  String?
  shippingAddress   Address?    @relation("ShippingAddress", fields: [shippingAddressId], references: [id])
  billingAddress    Address?    @relation("BillingAddress", fields: [billingAddressId], references: [id])
  
  // Address snapshots (in case original is deleted)
  shippingSnapshot  Json?
  billingSnapshot   Json?
  
  // Payment
  stripePaymentIntentId String? @unique
  paymentStatus     String?
  paidAt            DateTime?
  
  // Shipping
  shippingMethod    String?
  trackingNumber    String?
  shippedAt         DateTime?
  deliveredAt       DateTime?
  
  // Notes
  customerNotes     String?     @db.Text
  internalNotes     String?     @db.Text
  
  // Relations
  user              User        @relation(fields: [userId], references: [id])
  items             OrderItem[]
  
  createdAt         DateTime    @default(now())
  updatedAt         DateTime    @updatedAt
  
  @@index([userId])
  @@index([orderNumber])
  @@index([status])
  @@index([createdAt])
  @@map("orders")
}

model OrderItem {
  id         String  @id @default(cuid())
  orderId    String
  productId  String
  
  // Snapshot of product at time of order
  productSnapshot Json
  
  quantity   Int
  unitPrice  Decimal @db.Decimal(10, 2)
  totalPrice Decimal @db.Decimal(10, 2)
  
  order   Order   @relation(fields: [orderId], references: [id], onDelete: Cascade)
  product Product @relation(fields: [productId], references: [id])
  
  createdAt DateTime @default(now())
  
  @@index([orderId])
  @@index([productId])
  @@map("order_items")
}

// ============================================
// REVIEW MODELS
// ============================================

model Review {
  id        String       @id @default(cuid())
  productId String
  userId    String
  
  rating    Int          // 1-5
  title     String?
  content   String       @db.Text
  
  verified  Boolean      @default(false) // Verified purchase
  featured  Boolean      @default(false)
  status    ReviewStatus @default(PENDING)
  
  // Admin response
  response  String?      @db.Text
  respondedAt DateTime?
  
  product Product @relation(fields: [productId], references: [id], onDelete: Cascade)
  user    User    @relation(fields: [userId], references: [id], onDelete: Cascade)
  
  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt
  
  @@unique([productId, userId])
  @@index([productId])
  @@index([userId])
  @@index([status])
  @@map("reviews")
}

// ============================================
// NEWSLETTER MODEL
// ============================================

model Newsletter {
  id             String           @id @default(cuid())
  email          String           @unique
  name           String?
  status         NewsletterStatus @default(ACTIVE)
  source         String           @default("website") // website, checkout, popup
  
  subscribedAt   DateTime         @default(now())
  unsubscribedAt DateTime?
  
  createdAt      DateTime         @default(now())
  updatedAt      DateTime         @updatedAt
  
  @@index([email])
  @@index([status])
  @@map("newsletter_subscribers")
}

// ============================================
// SETTINGS & CONFIGURATION
// ============================================

model Setting {
  id    String @id @default(cuid())
  key   String @unique
  value Json
  
  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt
  
  @@map("settings")
}
6.3 Database Indexes Strategy
text

┌─────────────────────────────────────────────────────────────────────────────┐
│                         INDEX STRATEGY                                       │
└─────────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────────┐
│ TABLE          │ INDEX NAME                    │ COLUMNS                    │
├─────────────────────────────────────────────────────────────────────────────┤
│ users          │ users_email_idx               │ email                      │
├─────────────────────────────────────────────────────────────────────────────┤
│ products       │ products_slug_idx             │ slug                       │
│                │ products_sku_idx              │ sku                        │
│                │ products_status_idx           │ status                     │
│                │ products_category_idx         │ categoryId                 │
│                │ products_humour_idx           │ humour                     │
│                │ products_featured_status_idx  │ featured, status           │
├─────────────────────────────────────────────────────────────────────────────┤
│ orders         │ orders_user_idx               │ userId                     │
│                │ orders_number_idx             │ orderNumber                │
│                │ orders_status_idx             │ status                     │
│                │ orders_created_idx            │ createdAt                  │
├─────────────────────────────────────────────────────────────────────────────┤
│ cart_items     │ cart_items_cart_idx           │ cartId                     │
│                │ cart_items_product_idx        │ productId                  │
├─────────────────────────────────────────────────────────────────────────────┤
│ reviews        │ reviews_product_idx           │ productId                  │
│                │ reviews_user_idx              │ userId                     │
│                │ reviews_status_idx            │ status                     │
├─────────────────────────────────────────────────────────────────────────────┤
│ newsletter     │ newsletter_email_idx          │ email                      │
│                │ newsletter_status_idx         │ status                     │
└─────────────────────────────────────────────────────────────────────────────┘
6.4 Seed Data
TypeScript

// prisma/seed.ts

import { PrismaClient, Humour, Rarity, Season, ProductStatus } from '@prisma/client';
import { hash } from 'bcryptjs';

const prisma = new PrismaClient();

async function main() {
  console.log('🌱 Seeding database...');

  // Create admin user
  const adminPassword = await hash('admin123', 12);
  const admin = await prisma.user.upsert({
    where: { email: 'admin@atelierarome.com' },
    update: {},
    create: {
      email: 'admin@atelierarome.com',
      name: 'Master Perfumer',
      password: adminPassword,
      role: 'ADMIN',
      emailVerified: new Date(),
    },
  });
  console.log('✓ Admin user created');

  // Create categories
  const categories = await Promise.all([
    prisma.category.upsert({
      where: { slug: 'floral' },
      update: {},
      create: {
        name: 'Floral Essences',
        slug: 'floral',
        description: 'Delicate botanical extracts from nature\'s most fragrant blooms.',
        position: 1,
      },
    }),
    prisma.category.upsert({
      where: { slug: 'herbal' },
      update: {},
      create: {
        name: 'Herbal Compounds',
        slug: 'herbal',
        description: 'Aromatic herbs distilled to capture their therapeutic essence.',
        position: 2,
      },
    }),
    prisma.category.upsert({
      where: { slug: 'citrus' },
      update: {},
      create: {
        name: 'Citrus Extracts',
        slug: 'citrus',
        description: 'Bright and uplifting essences from sun-ripened fruits.',
        position: 3,
      },
    }),
    prisma.category.upsert({
      where: { slug: 'woody' },
      update: {},
      create: {
        name: 'Woody Notes',
        slug: 'woody',
        description: 'Deep, grounding aromas from ancient forests.',
        position: 4,
      },
    }),
  ]);
  console.log('✓ Categories created');

  // Create products
  const products = [
    {
      slug: 'provence-lavender',
      sku: 'LAV-001',
      latinName: 'Lavandula × intermedia',
      commonName: 'Provence Lavender',
      description: 'Harvested at dawn in the Provençal hills, this lavender possesses a sweetness found only in blossoms kissed by the morning\'s first light. Its effect is one of profound calm, like the silence between breaths.',
      shortDescription: 'The quintessential calming essence from the lavender fields of Provence.',
      humour: Humour.CALMING,
      rarity: Rarity.RARE,
      season: Season.SUMMER,
      notes: ['Floral', 'Herbaceous', 'Sweet', 'Slightly Camphoraceous'],
      extraction: 'Steam Distillation',
      origin: 'Provence, France',
      price: 42.00,
      compareAtPrice: null,
      inventory: 50,
      volume: 5.0,
      weight: 15.0,
      categoryId: categories[0].id,
      featured: true,
      status: ProductStatus.ACTIVE,
    },
    {
      slug: 'tasmanian-eucalyptus',
      sku: 'EUC-001',
      latinName: 'Eucalyptus globulus',
      commonName: 'Tasmanian Eucalyptus',
      description: 'The crisp, clean scent of Tasmania\'s ancient forests. This essence clears the mind as morning mist clears from mountain valleys, leaving only clarity and renewed focus.',
      shortDescription: 'A clarifying essence that opens the airways and refreshes the spirit.',
      humour: Humour.CLARIFYING,
      rarity: Rarity.COMMON,
      season: Season.AUTUMN,
      notes: ['Camphorous', 'Fresh', 'Clean', 'Slightly Medicinal'],
      extraction: 'Steam Distillation',
      origin: 'Tasmania, Australia',
      price: 36.00,
      compareAtPrice: null,
      inventory: 100,
      volume: 5.0,
      weight: 15.0,
      categoryId: categories[1].id,
      featured: false,
      status: 
