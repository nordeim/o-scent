Project Architecture Document
Atelier Arôme — Artisanal Aromatherapy E-Commerce Platform
Document Control
Property	Value
Document Version	2.0.0
Status	Approved for Implementation
Classification	Internal — Development Team
Last Updated	2024
Author	Technical Architecture Team
Review Cycle	Quarterly
Table of Contents
Executive Summary
Project Vision & Objectives
Technology Stack
System Architecture
Database Schema
API Specification
Frontend Architecture
Design System
Authentication & Authorization
Third-Party Integrations
Performance Strategy
Security Framework
Testing Strategy
Deployment & Infrastructure
Development Guidelines
Appendices
1. Executive Summary
1.1 Purpose
This Project Architecture Document (PAD) serves as the single source of truth for the Atelier Arôme digital platform. It provides comprehensive specifications enabling any developer or AI coding agent to independently implement the complete system without ambiguity.

1.2 Scope
The platform is a luxury artisanal aromatherapy e-commerce experience that transforms the current static prototype into a fully functional production system with:

E-commerce capabilities — Full shopping cart, checkout, payment processing
Content management — Dynamic product catalog, testimonials, editorial content
User management — Customer accounts, order history, wishlists
Administrative interface — Product management, order fulfillment, analytics
Marketing automation — Newsletter subscriptions, promotional campaigns
1.3 Design Philosophy
The platform embodies the Renaissance manuscript aesthetic established in the prototype:

"This is not merely a website—it is a digital artifact that represents the pinnacle of thematic web design."

Every technical decision must honor:

Artisanal craftsmanship — No generic UI patterns
Deliberate friction — Luxury experience over speed optimization
Sensory translation — Digital representation of physical aromatherapy
Manuscript authenticity — Historical accuracy in visual language
1.4 Success Criteria
Metric	Target	Measurement
Lighthouse Performance	≥ 90	Monthly audit
Lighthouse Accessibility	≥ 95	Monthly audit
WCAG Compliance	AA (AAA preferred)	Automated + manual testing
First Contentful Paint	< 1.5s	Core Web Vitals
Largest Contentful Paint	< 2.5s	Core Web Vitals
Cumulative Layout Shift	< 0.1	Core Web Vitals
Time to Interactive	< 3.5s	Core Web Vitals
Uptime SLA	99.9%	Infrastructure monitoring
Cart Abandonment Rate	< 65%	Analytics
Conversion Rate	> 3%	Analytics
2. Project Vision & Objectives
2.1 Business Context
Atelier Arôme is a luxury artisanal aromatherapy brand positioned at the premium end of the market. The digital platform must:

Communicate craftsmanship — Every interaction reinforces the artisanal narrative
Justify premium pricing — $42-48 per 5ml phial requires perceived value
Build collector culture — Encourage repeat purchases and collection building
Enable global reach — International shipping and multi-currency support
Preserve exclusivity — Limited editions, waiting lists, member-only releases
2.2 Target User Personas
Primary Persona: The Connoisseur
YAML

Name: "Isabelle"
Age: 35-55
Income: $150k+
Characteristics:
  - Values authenticity over convenience
  - Researches extensively before purchasing
  - Appreciates craft and provenance stories
  - Willing to wait for quality
  - Desktop-primary (large screen appreciation)
Needs:
  - Rich product information
  - Provenance and process transparency
  - Elegant, unhurried experience
  - Personal recommendations
Secondary Persona: The Gift Giver
YAML

Name: "Marcus"
Age: 30-50
Income: $100k+
Characteristics:
  - Seeks memorable, unique gifts
  - Values presentation and packaging
  - Time-constrained
  - Mobile-first for discovery, desktop for purchase
Needs:
  - Gift recommendations
  - Beautiful packaging options
  - Gift messaging
  - Scheduled delivery
Tertiary Persona: The Wellness Enthusiast
YAML

Name: "Elena"
Age: 25-40
Income: $75k+
Characteristics:
  - Active wellness routine
  - Follows aromatherapy trends
  - Social media influenced
  - Mobile-primary
Needs:
  - Educational content
  - Usage guidance
  - Sample sets
  - Community connection
2.3 Feature Prioritization Matrix
text

┌─────────────────────────────────────────────────────────────────┐
│                         PRIORITY MATRIX                          │
├─────────────────────────────────────────────────────────────────┤
│                                                                  │
│  HIGH VALUE                                                      │
│  ▲                                                               │
│  │  ┌─────────────────┐    ┌─────────────────┐                  │
│  │  │ Product Catalog │    │  Shopping Cart  │   QUICK WINS     │
│  │  │    & Detail     │    │   & Checkout    │   (Do First)     │
│  │  └─────────────────┘    └─────────────────┘                  │
│  │                                                               │
│  │  ┌─────────────────┐    ┌─────────────────┐                  │
│  │  │  User Accounts  │    │    Newsletter   │                  │
│  │  │  & Order Hist.  │    │  Subscription   │                  │
│  │  └─────────────────┘    └─────────────────┘                  │
│  │                                                               │
│  │  ┌─────────────────┐    ┌─────────────────┐   STRATEGIC      │
│  │  │ Admin Dashboard │    │   Wishlist &    │   (Plan Well)    │
│  │  │ & Inventory     │    │   Collections   │                  │
│  │  └─────────────────┘    └─────────────────┘                  │
│  │                                                               │
│  │  ┌─────────────────┐    ┌─────────────────┐                  │
│  │  │   Gift Cards    │    │   Loyalty       │   FUTURE         │
│  │  │   & Vouchers    │    │   Program       │   (Backlog)      │
│  │  └─────────────────┘    └─────────────────┘                  │
│  │                                                               │
│  └──────────────────────────────────────────────────────────►   │
│                                                    HIGH EFFORT   │
│  LOW VALUE                                                       │
└─────────────────────────────────────────────────────────────────┘
2.4 Development Phases
Phase 1: Foundation (Weeks 1-4)
Project scaffolding and infrastructure
Database schema implementation
Authentication system
Core UI component library
Design system implementation
Phase 2: Commerce Core (Weeks 5-8)
Product catalog with filtering
Product detail pages
Shopping cart functionality
Checkout flow
Payment integration (Stripe)
Phase 3: User Experience (Weeks 9-12)
User registration and authentication
Account management
Order history
Wishlist functionality
Newsletter subscription
Phase 4: Administration (Weeks 13-16)
Admin dashboard
Product management
Order management
Inventory tracking
Analytics integration
Phase 5: Enhancement (Weeks 17-20)
Search optimization
Performance tuning
Accessibility audit and fixes
SEO optimization
Launch preparation
3. Technology Stack
3.1 Stack Overview
text

┌─────────────────────────────────────────────────────────────────────────┐
│                           TECHNOLOGY STACK                               │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │                         PRESENTATION LAYER                       │    │
│  │  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐             │    │
│  │  │  Next.js    │  │  Tailwind   │  │  Shadcn/UI  │             │    │
│  │  │    15       │  │  CSS 4.0    │  │ (Radix UI)  │             │    │
│  │  └─────────────┘  └─────────────┘  └─────────────┘             │    │
│  │  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐             │    │
│  │  │   React 19  │  │  Framer     │  │   Zustand   │             │    │
│  │  │             │  │   Motion    │  │   (State)   │             │    │
│  │  └─────────────┘  └─────────────┘  └─────────────┘             │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                                   │                                      │
│                                   ▼                                      │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │                         APPLICATION LAYER                        │    │
│  │  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐             │    │
│  │  │   Next.js   │  │    tRPC     │  │   NextAuth  │             │    │
│  │  │ API Routes  │  │   (v11+)    │  │    (v5)     │             │    │
│  │  └─────────────┘  └─────────────┘  └─────────────┘             │    │
│  │  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐             │    │
│  │  │    Zod      │  │   React     │  │  Uploadthing│             │    │
│  │  │ Validation  │  │   Query     │  │   (Files)   │             │    │
│  │  └─────────────┘  └─────────────┘  └─────────────┘             │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                                   │                                      │
│                                   ▼                                      │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │                           DATA LAYER                             │    │
│  │  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐             │    │
│  │  │   Prisma    │  │ PostgreSQL  │  │    Redis    │             │    │
│  │  │    ORM      │  │   (Neon)    │  │   (Upstash) │             │    │
│  │  └─────────────┘  └─────────────┘  └─────────────┘             │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                                   │                                      │
│                                   ▼                                      │
│  ┌─────────────────────────────────────────────────────────────────┐    │
│  │                      INFRASTRUCTURE LAYER                        │    │
│  │  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐             │    │
│  │  │   Vercel    │  │  Cloudflare │  │    Stripe   │             │    │
│  │  │  (Hosting)  │  │    (CDN)    │  │  (Payments) │             │    │
│  │  └─────────────┘  └─────────────┘  └─────────────┘             │    │
│  │  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐             │    │
│  │  │   Resend    │  │   Sentry    │  │  PostHog    │             │    │
│  │  │   (Email)   │  │  (Errors)   │  │ (Analytics) │             │    │
│  │  └─────────────┘  └─────────────┘  └─────────────┘             │    │
│  └─────────────────────────────────────────────────────────────────┘    │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
3.2 Technology Decisions & Rationale
Frontend Framework: Next.js 15 (App Router)
YAML

Decision: Next.js 15 with App Router
Rationale:
  - Server Components reduce client-side JavaScript
  - Built-in image optimization critical for visual-heavy site
  - SEO-friendly with static and dynamic rendering options
  - React Server Actions simplify mutations
  - Edge runtime for global performance
  - Streaming for perceived performance
  
Alternatives Considered:
  - Remix: Strong option but smaller ecosystem
  - Astro: Excellent for content but weaker for interactivity
  - SvelteKit: Performance benefits but React ecosystem preferred
  
Trade-offs:
  - Vendor coupling to Vercel ecosystem
  - Learning curve for App Router patterns
  - Bundle size management requires attention
Styling: Tailwind CSS 4.0 + Shadcn/UI
YAML

Decision: Tailwind CSS 4.0 with Shadcn/UI primitives
Rationale:
  - Tailwind 4.0 CSS-first configuration
  - Design token system via CSS variables
  - Shadcn/UI provides accessible primitives
  - Full control over component styling (not locked into library aesthetic)
  - Smaller bundle than component libraries (no unused styles)
  
Configuration:
  - Custom design tokens matching manuscript aesthetic
  - Extended color palette for botanical themes
  - Custom typography scale for Renaissance feel
  - Animation utilities for micro-interactions
  
Shadcn/UI Components to Use:
  - Dialog (cart drawer, modals)
  - Dropdown Menu (filters, sorts)
  - Toast (notifications)
  - Form primitives (inputs, checkboxes)
  - Accordion (FAQ, product details)
  - Tabs (product information)
  - Sheet (mobile navigation)
  - Skeleton (loading states)
Database: PostgreSQL (Neon)
YAML

Decision: PostgreSQL via Neon serverless
Rationale:
  - ACID compliance for financial transactions
  - JSON/JSONB for flexible product metadata
  - Full-text search for product discovery
  - Proven scalability
  - Neon provides serverless with branching for development
  
Schema Highlights:
  - Soft deletes for data retention
  - Audit logging for compliance
  - Optimistic locking for inventory
  - Indexed for common query patterns
  
Alternatives Considered:
  - PlanetScale (MySQL): Good but PostgreSQL features preferred
  - Supabase: Good but want more control over auth
  - CockroachDB: Overkill for current scale
ORM: Prisma
YAML

Decision: Prisma ORM
Rationale:
  - Type-safe database access
  - Excellent migration system
  - Prisma Studio for data exploration
  - Wide Next.js adoption
  - Good performance with query optimization
  
Configuration:
  - Prisma Accelerate for connection pooling
  - Prisma Pulse for real-time features (future)
  
Patterns:
  - Repository pattern for data access
  - Soft delete middleware
  - Audit logging middleware
State Management: Zustand + React Query
YAML

Decision: Zustand for client state, React Query for server state
Rationale:
  - Zustand: Minimal boilerplate, excellent TypeScript support
  - React Query: Caching, revalidation, optimistic updates
  - Clear separation of concerns
  
State Categories:
  - UI State (Zustand): Cart drawer open, mobile nav, filters
  - Server State (React Query): Products, orders, user data
  - Form State (React Hook Form): Checkout, registration
  
Persistence:
  - Cart persisted to localStorage
  - User preferences persisted to localStorage
  - Session data managed by NextAuth
Authentication: NextAuth.js v5
YAML

Decision: NextAuth.js v5 (Auth.js)
Rationale:
  - Native Next.js integration
  - Multiple provider support
  - Session management
  - CSRF protection built-in
  
Providers:
  - Email/Password (credentials)
  - Google OAuth
  - Apple Sign In (future)
  
Session Strategy:
  - JWT for stateless verification
  - Database sessions for admin users
  
Security:
  - httpOnly cookies
  - Secure flag in production
  - SameSite strict
Payments: Stripe
YAML

Decision: Stripe for payment processing
Rationale:
  - Industry standard
  - Global payment method support
  - Strong fraud protection
  - Excellent documentation
  - PCI compliance handled
  
Features to Implement:
  - Stripe Checkout (hosted)
  - Stripe Elements (embedded) - future
  - Webhooks for order fulfillment
  - Stripe Tax for automatic tax calculation
  - Stripe Shipping for rate calculation
  
Currencies:
  - Primary: USD
  - Secondary: EUR, GBP
  - Future: CAD, AUD, JPY
3.3 Development Dependencies
JSON

{
  "dependencies": {
    "next": "^15.0.0",
    "react": "^19.0.0",
    "react-dom": "^19.0.0",
    "@prisma/client": "^5.0.0",
    "@tanstack/react-query": "^5.0.0",
    "@trpc/client": "^11.0.0",
    "@trpc/server": "^11.0.0",
    "@trpc/react-query": "^11.0.0",
    "next-auth": "^5.0.0",
    "zod": "^3.23.0",
    "zustand": "^4.5.0",
    "tailwindcss": "^4.0.0",
    "framer-motion": "^11.0.0",
    "stripe": "^14.0.0",
    "@stripe/stripe-js": "^3.0.0",
    "resend": "^3.0.0",
    "@upstash/redis": "^1.28.0",
    "@upstash/ratelimit": "^1.0.0",
    "lucide-react": "^0.300.0",
    "class-variance-authority": "^0.7.0",
    "clsx": "^2.1.0",
    "tailwind-merge": "^2.2.0",
    "date-fns": "^3.0.0",
    "slugify": "^1.6.0"
  },
  "devDependencies": {
    "typescript": "^5.4.0",
    "@types/node": "^20.0.0",
    "@types/react": "^18.0.0",
    "prisma": "^5.0.0",
    "eslint": "^8.0.0",
    "eslint-config-next": "^15.0.0",
    "@typescript-eslint/eslint-plugin": "^7.0.0",
    "prettier": "^3.0.0",
    "prettier-plugin-tailwindcss": "^0.5.0",
    "vitest": "^1.0.0",
    "@testing-library/react": "^14.0.0",
    "playwright": "^1.40.0",
    "husky": "^9.0.0",
    "lint-staged": "^15.0.0"
  }
}
3.4 Environment Configuration
Bash

# .env.example

# ============================================
# APPLICATION
# ============================================
NODE_ENV=development
NEXT_PUBLIC_APP_URL=http://localhost:3000
NEXT_PUBLIC_APP_NAME="Atelier Arôme"

# ============================================
# DATABASE
# ============================================
DATABASE_URL="postgresql://user:password@host:5432/atelier_arome?schema=public"
DIRECT_URL="postgresql://user:password@host:5432/atelier_arome?schema=public"

# ============================================
# AUTHENTICATION
# ============================================
NEXTAUTH_URL=http://localhost:3000
NEXTAUTH_SECRET=your-secret-key-min-32-chars

# OAuth Providers
GOOGLE_CLIENT_ID=
GOOGLE_CLIENT_SECRET=

# ============================================
# PAYMENTS (STRIPE)
# ============================================
STRIPE_SECRET_KEY=sk_test_...
STRIPE_PUBLISHABLE_KEY=pk_test_...
STRIPE_WEBHOOK_SECRET=whsec_...

# ============================================
# EMAIL (RESEND)
# ============================================
RESEND_API_KEY=re_...
EMAIL_FROM="Atelier Arôme <correspondence@atelierarome.com>"

# ============================================
# CACHING (UPSTASH REDIS)
# ============================================
UPSTASH_REDIS_REST_URL=https://...
UPSTASH_REDIS_REST_TOKEN=...

# ============================================
# FILE UPLOADS (UPLOADTHING)
# ============================================
UPLOADTHING_SECRET=sk_live_...
UPLOADTHING_APP_ID=...

# ============================================
# MONITORING
# ============================================
SENTRY_DSN=https://...
NEXT_PUBLIC_POSTHOG_KEY=phc_...
NEXT_PUBLIC_POSTHOG_HOST=https://app.posthog.com

# ============================================
# FEATURE FLAGS
# ============================================
NEXT_PUBLIC_ENABLE_ANALYTICS=true
NEXT_PUBLIC_ENABLE_WISHLIST=true
NEXT_PUBLIC_ENABLE_REVIEWS=false
4. System Architecture
4.1 High-Level Architecture Diagram
text

┌─────────────────────────────────────────────────────────────────────────────────┐
│                              CLIENT LAYER                                        │
│  ┌─────────────────────────────────────────────────────────────────────────┐    │
│  │                            Web Browsers                                  │    │
│  │   Desktop (Chrome, Safari, Firefox)  │  Mobile (Safari, Chrome)         │    │
│  └─────────────────────────────────────────────────────────────────────────┘    │
└─────────────────────────────────────────────────────────────────────────────────┘
                                        │
                                        ▼
┌─────────────────────────────────────────────────────────────────────────────────┐
│                              CDN / EDGE LAYER                                    │
│  ┌─────────────────────────────────────────────────────────────────────────┐    │
│  │                         Vercel Edge Network                              │    │
│  │   ┌──────────────┐  ┌──────────────┐  ┌──────────────┐                  │    │
│  │   │ Static Asset │  │    Edge      │  │   DDoS       │                  │    │
│  │   │   Caching    │  │   Functions  │  │  Protection  │                  │    │
│  │   └──────────────┘  └──────────────┘  └──────────────┘                  │    │
│  └─────────────────────────────────────────────────────────────────────────┘    │
└─────────────────────────────────────────────────────────────────────────────────┘
                                        │
                                        ▼
┌─────────────────────────────────────────────────────────────────────────────────┐
│                            APPLICATION LAYER                                     │
│  ┌─────────────────────────────────────────────────────────────────────────┐    │
│  │                          Next.js Application                             │    │
│  │                                                                          │    │
│  │   ┌──────────────────────────────────────────────────────────────────┐  │    │
│  │   │                    PRESENTATION TIER                              │  │    │
│  │   │  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌────────────┐  │  │    │
│  │   │  │   React     │ │   Server    │ │   Client    │ │  Streaming │  │  │    │
│  │   │  │ Components  │ │ Components  │ │ Components  │ │    SSR     │  │  │    │
│  │   │  └─────────────┘ └─────────────┘ └─────────────┘ └────────────┘  │  │    │
│  │   └──────────────────────────────────────────────────────────────────┘  │    │
│  │                                  │                                       │    │
│  │   ┌──────────────────────────────────────────────────────────────────┐  │    │
│  │   │                     BUSINESS LOGIC TIER                           │  │    │
│  │   │  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌────────────┐  │  │    │
│  │   │  │    tRPC     │ │   Server    │ │  NextAuth   │ │   Stripe   │  │  │    │
│  │   │  │   Routers   │ │   Actions   │ │   Handlers  │ │  Webhooks  │  │  │    │
│  │   │  └─────────────┘ └─────────────┘ └─────────────┘ └────────────┘  │  │    │
│  │   └──────────────────────────────────────────────────────────────────┘  │    │
│  │                                  │                                       │    │
│  │   ┌──────────────────────────────────────────────────────────────────┐  │    │
│  │   │                      DATA ACCESS TIER                             │  │    │
│  │   │  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌────────────┐  │  │    │
│  │   │  │   Prisma    │ │    Redis    │ │   Service   │ │    Zod     │  │  │    │
│  │   │  │   Client    │ │   Client    │ │    Layer    │ │ Validation │  │  │    │
│  │   │  └─────────────┘ └─────────────┘ └─────────────┘ └────────────┘  │  │    │
│  │   └──────────────────────────────────────────────────────────────────┘  │    │
│  │                                                                          │    │
│  └─────────────────────────────────────────────────────────────────────────┘    │
└─────────────────────────────────────────────────────────────────────────────────┘
                    │                           │                    │
                    ▼                           ▼                    ▼
┌───────────────────────────┐ ┌───────────────────────────┐ ┌─────────────────────┐
│      DATA LAYER           │ │      CACHE LAYER          │ │   EXTERNAL SERVICES │
│  ┌─────────────────────┐  │ │  ┌─────────────────────┐  │ │ ┌─────────────────┐ │
│  │    PostgreSQL       │  │ │  │      Upstash        │  │ │ │     Stripe      │ │
│  │      (Neon)         │  │ │  │       Redis         │  │ │ │    Payments     │ │
│  │                     │  │ │  │                     │  │ │ └─────────────────┘ │
│  │  • Users            │  │ │  │  • Session Cache    │  │ │ ┌─────────────────┐ │
│  │  • Products         │  │ │  │  • Rate Limiting    │  │ │ │     Resend      │ │
│  │  • Orders           │  │ │  │  • Cart Cache       │  │ │ │     Email       │ │
│  │  • Inventory        │  │ │  │  • Product Cache    │  │ │ └─────────────────┘ │
│  │  • Testimonials     │  │ │  │                     │  │ │ ┌─────────────────┐ │
│  │  • Audit Logs       │  │ │  │                     │  │ │ │   Uploadthing   │ │
│  │                     │  │ │  │                     │  │ │ │    Storage      │ │
│  └─────────────────────┘  │ │  └─────────────────────┘  │ │ └─────────────────┘ │
└───────────────────────────┘ └───────────────────────────┘ └─────────────────────┘
4.2 Request Flow Diagram
text

┌─────────────────────────────────────────────────────────────────────────────────┐
│                           REQUEST FLOW: VIEW PRODUCT                             │
└─────────────────────────────────────────────────────────────────────────────────┘

  User                   Edge              Next.js             Prisma           DB
   │                      │                   │                  │              │
   │  GET /products/xyz   │                   │                  │              │
   │─────────────────────>│                   │                  │              │
   │                      │                   │                  │              │
   │                      │  Check cache      │                  │              │
   │                      │──────────────────>│                  │              │
   │                      │                   │                  │              │
   │                      │  Cache MISS       │                  │              │
   │                      │<──────────────────│                  │              │
   │                      │                   │                  │              │
   │                      │  Forward request  │                  │              │
   │                      │──────────────────>│                  │              │
   │                      │                   │                  │              │
   │                      │                   │  findUnique()    │              │
   │                      │                   │─────────────────>│              │
   │                      │                   │                  │              │
   │                      │                   │                  │  SELECT      │
   │                      │                   │                  │─────────────>│
   │                      │                   │                  │              │
   │                      │                   │                  │  Result      │
   │                      │                   │                  │<─────────────│
   │                      │                   │                  │              │
   │                      │                   │  Product data    │              │
   │                      │                   │<─────────────────│              │
   │                      │                   │                  │              │
   │                      │                   │  Render RSC      │              │
   │                      │                   │  ───────────     │              │
   │                      │                   │                  │              │
   │                      │  Streamed HTML    │                  │              │
   │                      │<──────────────────│                  │              │
   │                      │                   │                  │              │
   │                      │  Cache response   │                  │              │
   │                      │  ─────────────    │                  │              │
   │                      │                   │                  │              │
   │  Streamed HTML       │                   │                  │              │
   │<─────────────────────│                   │                  │              │
   │                      │                   │                  │              │
   │  Hydrate client      │                   │                  │              │
   │  ───────────────     │                   │                  │              │
   │                      │                   │                  │              │
4.3 Data Flow: Add to Cart
text

┌─────────────────────────────────────────────────────────────────────────────────┐
│                           DATA FLOW: ADD TO CART                                 │
└─────────────────────────────────────────────────────────────────────────────────┘

  Client                    tRPC               Service             Redis        DB
   │                         │                   │                   │          │
   │  cart.addItem()         │                   │                   │          │
   │────────────────────────>│                   │                   │          │
   │                         │                   │                   │          │
   │                         │  Validate input   │                   │          │
   │                         │  ──────────────   │                   │          │
   │                         │                   │                   │          │
   │                         │  Check auth       │                   │          │
   │                         │  ──────────────   │                   │          │
   │                         │                   │                   │          │
   │                         │  addToCart()      │                   │          │
   │                         │─────────────────> │                   │          │
   │                         │                   │                   │          │
   │                         │                   │  Check inventory  │          │
   │                         │                   │──────────────────>│          │
   │                         │                   │                   │          │
   │                         │                   │  Inventory OK     │          │
   │                         │                   │<──────────────────│          │
   │                         │                   │                   │          │
   │                         │                   │  Get/create cart  │          │
   │                         │                   │─────────────────────────────>│
   │                         │                   │                   │          │
   │                         │                   │  Cart data        │          │
   │                         │                   │<─────────────────────────────│
   │                         │                   │                   │          │
   │                         │                   │  Add item         │          │
   │                         │                   │─────────────────────────────>│
   │                         │                   │                   │          │
   │                         │                   │  Updated cart     │          │
   │                         │                   │<─────────────────────────────│
   │                         │                   │                   │          │
   │                         │                   │  Invalidate cache │          │
   │                         │                   │──────────────────>│          │
   │                         │                   │                   │          │
   │                         │  Cart response    │                   │          │
   │                         │<─────────────────│                   │          │
   │                         │                   │                   │          │
   │  Optimistic update      │                   │                   │          │
   │<────────────────────────│                   │                   │          │
   │                         │                   │                   │          │
   │  Toast notification     │                   │                   │          │
   │  ───────────────────    │                   │                   │          │
   │                         │                   │                   │          │
4.4 Checkout Flow
text

┌─────────────────────────────────────────────────────────────────────────────────┐
│                              CHECKOUT FLOW                                       │
└─────────────────────────────────────────────────────────────────────────────────┘

┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│    CART     │    │  SHIPPING   │    │   PAYMENT   │    │ CONFIRMATION│
│   REVIEW    │───>│  ADDRESS    │───>│   STRIPE    │───>│    PAGE     │
└─────────────┘    └─────────────┘    └─────────────┘    └─────────────┘
      │                  │                  │                  │
      ▼                  ▼                  ▼                  ▼
┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│  Validate   │    │  Calculate  │    │   Create    │    │   Create    │
│    cart     │    │   shipping  │    │   session   │    │    order    │
│   items     │    │   & tax     │    │             │    │             │
└─────────────┘    └─────────────┘    └─────────────┘    └─────────────┘
      │                  │                  │                  │
      ▼                  ▼                  ▼                  ▼
┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│   Check     │    │   Validate  │    │  Redirect   │    │   Update    │
│  inventory  │    │   address   │    │  to Stripe  │    │  inventory  │
└─────────────┘    └─────────────┘    └─────────────┘    └─────────────┘
                                           │                  │
                                           ▼                  ▼
                                     ┌─────────────┐    ┌─────────────┐
                                     │   Stripe    │    │    Send     │
                                     │   Hosted    │    │   emails    │
                                     │  Checkout   │    │             │
                                     └─────────────┘    └─────────────┘
                                           │
                                           ▼
                                     ┌─────────────┐
                                     │   Webhook   │
                                     │  Received   │
                                     └─────────────┘
5. Database Schema
5.1 Entity Relationship Diagram
text

┌─────────────────────────────────────────────────────────────────────────────────┐
│                        ENTITY RELATIONSHIP DIAGRAM                               │
└─────────────────────────────────────────────────────────────────────────────────┘

                              ┌──────────────────┐
                              │      USER        │
                              ├──────────────────┤
                              │ id               │
                              │ email            │
                              │ name             │
                              │ passwordHash     │
                              │ role             │
                              │ emailVerified    │
                              │ createdAt        │
                              │ updatedAt        │
                              └────────┬─────────┘
                                       │
           ┌───────────────────────────┼───────────────────────────┐
           │                           │                           │
           ▼                           ▼                           ▼
┌──────────────────┐       ┌──────────────────┐       ┌──────────────────┐
│     ADDRESS      │       │      ORDER       │       │     WISHLIST     │
├──────────────────┤       ├──────────────────┤       ├──────────────────┤
│ id               │       │ id               │       │ id               │
│ userId           │◄──────│ userId           │──────►│ userId           │
│ type             │       │ addressId        │       │ createdAt        │
│ firstName        │       │ status           │       └────────┬─────────┘
│ lastName         │       │ total            │                │
│ line1            │       │ subtotal         │                ▼
│ line2            │       │ shippingCost     │       ┌──────────────────┐
│ city             │       │ taxAmount        │       │  WISHLIST_ITEM   │
│ state            │       │ stripeSessionId  │       ├──────────────────┤
│ postalCode       │       │ stripePaymentId  │       │ id               │
│ country          │       │ createdAt        │       │ wishlistId       │
│ phone            │       │ updatedAt        │       │ productId        │──┐
│ isDefault        │       └────────┬─────────┘       │ addedAt          │  │
│ createdAt        │                │                 └──────────────────┘  │
└──────────────────┘                │                                       │
                                    ▼                                       │
                          ┌──────────────────┐                              │
                          │   ORDER_ITEM     │                              │
                          ├──────────────────┤                              │
                          │ id               │                              │
                          │ orderId          │                              │
                          │ productId        │──────────────────────────────┤
                          │ quantity         │                              │
                          │ unitPrice        │                              │
                          │ totalPrice       │                              │
                          └──────────────────┘                              │
                                                                            │
┌──────────────────────────────────────────────────────────────────────────────────┐
│                                                                                  │
│    ┌──────────────────┐       ┌──────────────────┐       ┌──────────────────┐   │
│    │     CATEGORY     │       │     PRODUCT      │       │   PRODUCT_IMAGE  │   │
│    ├──────────────────┤       ├──────────────────┤       ├──────────────────┤   │
│    │ id               │       │ id               │◄──────│ id               │   │
│    │ name             │◄──────│ categoryId       │       │ productId        │   │
│    │ slug             │       │ name             │       │ url              │   │
│    │ description      │       │ slug             │       │ alt              │   │
│    │ humourSymbol     │       │ latinName        │       │ position         │   │
│    │ color            │       │ description      │       │ isPrimary        │   │
│    │ createdAt        │       │ shortDescription │       │ createdAt        │   │
│    └──────────────────┘       │ price            │       └──────────────────┘   │
│                               │ compareAtPrice   │                              │
│    ┌──────────────────┐       │ sku              │◄──────────────────────────────┤
│    │   PRODUCT_TAG    │       │ rarity           │                              │
│    ├──────────────────┤       │ season           │       ┌──────────────────┐   │
│    │ id               │       │ extractionMethod │       │    INVENTORY     │   │
│    │ name             │◄──┐   │ scentNotes       │       ├──────────────────┤   │
│    │ slug             │   │   │ usageGuidance    │       │ id               │   │
│    └──────────────────┘   │   │ botanicalFamily  │       │ productId        │──►│
│                           │   │ origin           │       │ quantity         │   │
│    ┌──────────────────┐   │   │ harvestSeason    │       │ reserved         │   │
│    │ PRODUCT_TO_TAG   │   │   │ isActive         │       │ lowStockThreshold│   │
│    ├──────────────────┤   │   │ isFeatured       │       │ updatedAt        │   │
│    │ productId        │───┼───│ createdAt        │       └──────────────────┘   │
│    │ tagId            │───┘   │ updatedAt        │                              │
│    └──────────────────┘       │ deletedAt        │                              │
│                               └────────┬─────────┘                              │
│                                        │                                        │
└────────────────────────────────────────┼────────────────────────────────────────┘
                                         │
                   ┌─────────────────────┼─────────────────────┐
                   │                     │                     │
                   ▼                     ▼                     ▼
        ┌──────────────────┐  ┌──────────────────┐  ┌──────────────────┐
        │     CART         │  │     REVIEW       │  │   TESTIMONIAL    │
        ├──────────────────┤  ├──────────────────┤  ├──────────────────┤
        │ id               │  │ id               │  │ id               │
        │ userId           │  │ productId        │  │ productId        │
        │ sessionId        │  │ userId           │  │ authorName       │
        │ expiresAt        │  │ rating           │  │ authorTitle      │
        │ createdAt        │  │ title            │  │ quote            │
        │ updatedAt        │  │ body             │  │ isVerified       │
        └────────┬─────────┘  │ isVerified       │  │ isFeatured       │
                 │            │ createdAt        │  │ folioReference   │
                 ▼            └──────────────────┘  │ createdAt        │
        ┌──────────────────┐                        └──────────────────┘
        │   CART_ITEM      │
        ├──────────────────┤
        │ id               │
        │ cartId           │
        │ productId        │
        │ quantity         │
        │ addedAt          │
        └──────────────────┘


┌─────────────────────────────────────────────────────────────────────────────────┐
│                            SUPPORTING ENTITIES                                   │
└─────────────────────────────────────────────────────────────────────────────────┘

┌──────────────────┐       ┌──────────────────┐       ┌──────────────────┐
│   NEWSLETTER     │       │   AUDIT_LOG      │       │     SESSION      │
│   SUBSCRIBER     │       ├──────────────────┤       ├──────────────────┤
├──────────────────┤       │ id               │       │ id               │
│ id               │       │ userId           │       │ sessionToken     │
│ email            │       │ action           │       │ userId           │
│ name             │       │ entityType       │       │ expires          │
│ status           │       │ entityId         │       └──────────────────┘
│ source           │       │ oldValues        │
│ subscribedAt     │       │ newValues        │       ┌──────────────────┐
│ unsubscribedAt   │       │ ipAddress        │       │ VERIFICATION_    │
│ preferences      │       │ userAgent        │       │ TOKEN            │
└──────────────────┘       │ createdAt        │       ├──────────────────┤
                           └──────────────────┘       │ id               │
                                                      │ email            │
                                                      │ token            │
                                                      │ expires          │
                                                      └──────────────────┘
5.2 Prisma Schema
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

enum OrderStatus {
  PENDING
  CONFIRMED
  PROCESSING
  SHIPPED
  DELIVERED
  CANCELLED
  REFUNDED
}

enum AddressType {
  SHIPPING
  BILLING
}

enum ProductRarity {
  COMMON
  RARE
  LIMITED
  SEASONAL
}

enum ProductSeason {
  SPRING
  SUMMER
  AUTUMN
  WINTER
  ALL_YEAR
}

enum SubscriberStatus {
  ACTIVE
  UNSUBSCRIBED
  BOUNCED
}

// ============================================
// USER & AUTHENTICATION
// ============================================

model User {
  id             String    @id @default(cuid())
  email          String    @unique
  name           String?
  passwordHash   String?
  role           UserRole  @default(CUSTOMER)
  emailVerified  DateTime?
  image          String?
  
  // Preferences
  preferences    Json      @default("{}")
  
  // Timestamps
  createdAt      DateTime  @default(now())
  updatedAt      DateTime  @updatedAt
  deletedAt      DateTime?
  
  // Relations
  accounts       Account[]
  sessions       Session[]
  addresses      Address[]
  orders         Order[]
  reviews        Review[]
  wishlist       Wishlist?
  cart           Cart?
  auditLogs      AuditLog[]

  @@index([email])
  @@index([role])
  @@map("users")
}

model Account {
  id                 String  @id @default(cuid())
  userId             String
  type               String
  provider           String
  providerAccountId  String
  refresh_token      String? @db.Text
  access_token       String? @db.Text
  expires_at         Int?
  token_type         String?
  scope              String?
  id_token           String? @db.Text
  session_state      String?

  user User @relation(fields: [userId], references: [id], onDelete: Cascade)

  @@unique([provider, providerAccountId])
  @@map("accounts")
}

model Session {
  id           String   @id @default(cuid())
  sessionToken String   @unique
  userId       String
  expires      DateTime
  
  user User @relation(fields: [userId], references: [id], onDelete: Cascade)

  @@map("sessions")
}

model VerificationToken {
  identifier String
  token      String   @unique
  expires    DateTime

  @@unique([identifier, token])
  @@map("verification_tokens")
}

model Address {
  id          String      @id @default(cuid())
  userId      String
  type        AddressType @default(SHIPPING)
  
  firstName   String
  lastName    String
  company     String?
  line1       String
  line2       String?
  city        String
  state       String?
  postalCode  String
  country     String      @default("US")
  phone       String?
  
  isDefault   Boolean     @default(false)
  
  createdAt   DateTime    @default(now())
  updatedAt   DateTime    @updatedAt
  
  user        User        @relation(fields: [userId], references: [id], onDelete: Cascade)
  orders      Order[]

  @@index([userId])
  @@index([userId, isDefault])
  @@map("addresses")
}

// ============================================
// PRODUCT CATALOG
// ============================================

model Category {
  id            String    @id @default(cuid())
  name          String    @unique
  slug          String    @unique
  description   String?   @db.Text
  
  // Humour-specific styling
  humourSymbol  String?   // ☾, ☀, ♁, ☁
  color         String?   // Hex color for category
  
  // SEO
  metaTitle     String?
  metaDescription String? @db.Text
  
  createdAt     DateTime  @default(now())
  updatedAt     DateTime  @updatedAt
  
  products      Product[]

  @@index([slug])
  @@map("categories")
}

model ProductTag {
  id        String    @id @default(cuid())
  name      String    @unique
  slug      String    @unique
  
  products  ProductToTag[]

  @@map("product_tags")
}

model ProductToTag {
  productId String
  tagId     String
  
  product   Product    @relation(fields: [productId], references: [id], onDelete: Cascade)
  tag       ProductTag @relation(fields: [tagId], references: [id], onDelete: Cascade)

  @@id([productId, tagId])
  @@map("product_to_tags")
}

model Product {
  id                String         @id @default(cuid())
  
  // Basic Info
  name              String
  slug              String         @unique
  latinName         String?
  sku               String         @unique
  
  // Descriptions
  shortDescription  String?        @db.VarChar(255)
  description       String         @db.Text
  usageGuidance     String?        @db.Text
  
  // Pricing
  price             Decimal        @db.Decimal(10, 2)
  compareAtPrice    Decimal?       @db.Decimal(10, 2)
  costPrice         Decimal?       @db.Decimal(10, 2)
  
  // Classification
  categoryId        String
  rarity            ProductRarity  @default(COMMON)
  season            ProductSeason  @default(ALL_YEAR)
  
  // Botanical Details
  scentNotes        String[]       // Array of scent notes
  extractionMethod  String?
  botanicalFamily   String?
  origin            String?
  harvestSeason     String?
  
  // Volume
  volumeMl          Decimal        @default(5) @db.Decimal(5, 2)
  
  // Display
  folioNumber       String?        // Roman numeral for display
  
  // Status
  isActive          Boolean        @default(true)
  isFeatured        Boolean        @default(false)
  
  // SEO
  metaTitle         String?
  metaDescription   String?        @db.Text
  
  // Timestamps
  createdAt         DateTime       @default(now())
  updatedAt         DateTime       @updatedAt
  deletedAt         DateTime?
  
  // Relations
  category          Category       @relation(fields: [categoryId], references: [id])
  images            ProductImage[]
  tags              ProductToTag[]
  inventory         Inventory?
  cartItems         CartItem[]
  orderItems        OrderItem[]
  reviews           Review[]
  testimonials      Testimonial[]
  wishlistItems     WishlistItem[]

  @@index([slug])
  @@index([sku])
  @@index([categoryId])
  @@index([isActive, isFeatured])
  @@index([rarity])
  @@index([season])
  @@index([price])
  @@map("products")
}

model ProductImage {
  id         String   @id @default(cuid())
  productId  String
  
  url        String
  alt        String?
  width      Int?
  height     Int?
  
  position   Int      @default(0)
  isPrimary  Boolean  @default(false)
  
  createdAt  DateTime @default(now())
  
  product    Product  @relation(fields: [productId], references: [id], onDelete: Cascade)

  @@index([productId])
  @@index([productId, isPrimary])
  @@map("product_images")
}

model Inventory {
  id                 String   @id @default(cuid())
  productId          String   @unique
  
  quantity           Int      @default(0)
  reserved           Int      @default(0)
  lowStockThreshold  Int      @default(5)
  
  // Tracking
  lastRestocked      DateTime?
  
  updatedAt          DateTime @updatedAt
  
  product            Product  @relation(fields: [productId], references: [id], onDelete: Cascade)

  @@index([quantity])
  @@map("inventory")
}

// ============================================
// SHOPPING CART
// ============================================

model Cart {
  id         String     @id @default(cuid())
  userId     String?    @unique
  sessionId  String?    @unique
  
  expiresAt  DateTime?
  
  createdAt  DateTime   @default(now())
  updatedAt  DateTime   @updatedAt
  
  user       User?      @relation(fields: [userId], references: [id], onDelete: Cascade)
  items      CartItem[]

  @@index([sessionId])
  @@index([expiresAt])
  @@map("carts")
}

model CartItem {
  id         String   @id @default(cuid())
  cartId     String
  productId  String
  
  quantity   Int      @default(1)
  
  addedAt    DateTime @default(now())
  updatedAt  DateTime @updatedAt
  
  cart       Cart     @relation(fields: [cartId], references: [id], onDelete: Cascade)
  product    Product  @relation(fields: [productId], references: [id])

  @@unique([cartId, productId])
  @@index([cartId])
  @@map("cart_items")
}

// ============================================
// ORDERS
// ============================================

model Order {
  id                 String      @id @default(cuid())
  orderNumber        String      @unique
  userId             String?
  addressId          String?
  
  // Status
  status             OrderStatus @default(PENDING)
  
  // Amounts
  subtotal           Decimal     @db.Decimal(10, 2)
  shippingCost       Decimal     @default(0) @db.Decimal(10, 2)
  taxAmount          Decimal     @default(0) @db.Decimal(10, 2)
  discountAmount     Decimal     @default(0) @db.Decimal(10, 2)
  total              Decimal     @db.Decimal(10, 2)
  
  // Currency
  currency           String      @default("USD")
  
  // Stripe
  stripeSessionId    String?     @unique
  stripePaymentId    String?
  
  // Shipping
  shippingMethod     String?
  trackingNumber     String?
  trackingUrl        String?
  shippedAt          DateTime?
  deliveredAt        DateTime?
  
  // Guest checkout
  guestEmail         String?
  guestName          String?
  
  // Snapshot of shipping address (in case address is deleted)
  shippingAddress    Json?
  billingAddress     Json?
  
  // Notes
  customerNote       String?     @db.Text
  internalNote       String?     @db.Text
  
  // Timestamps
  createdAt          DateTime    @default(now())
  updatedAt          DateTime    @updatedAt
  cancelledAt        DateTime?
  refundedAt         DateTime?
  
  // Relations
  user               User?       @relation(fields: [userId], references: [id])
  address            Address?    @relation(fields: [addressId], references: [id])
  items              OrderItem[]

  @@index([userId])
  @@index([status])
  @@index([stripeSessionId])
  @@index([orderNumber])
  @@index([createdAt])
  @@map("orders")
}

model OrderItem {
  id          String   @id @default(cuid())
  orderId     String
  productId   String
  
  // Quantity
  quantity    Int
  
  // Pricing at time of order (snapshot)
  unitPrice   Decimal  @db.Decimal(10, 2)
  totalPrice  Decimal  @db.Decimal(10, 2)
  
  // Product snapshot (in case product is deleted/changed)
  productSnapshot Json?
  
  order       Order    @relation(fields: [orderId], references: [id], onDelete: Cascade)
  product     Product  @relation(fields: [productId], references: [id])

  @@index([orderId])
  @@map("order_items")
}

// ============================================
// WISHLIST
// ============================================

model Wishlist {
  id         String         @id @default(cuid())
  userId     String         @unique
  
  createdAt  DateTime       @default(now())
  updatedAt  DateTime       @updatedAt
  
  user       User           @relation(fields: [userId], references: [id], onDelete: Cascade)
  items      WishlistItem[]

  @@map("wishlists")
}

model WishlistItem {
  id          String   @id @default(cuid())
  wishlistId  String
  productId   String
  
  addedAt     DateTime @default(now())
  
  wishlist    Wishlist @relation(fields: [wishlistId], references: [id], onDelete: Cascade)
  product     Product  @relation(fields: [productId], references: [id])

  @@unique([wishlistId, productId])
  @@index([wishlistId])
  @@map("wishlist_items")
}

// ============================================
// REVIEWS & TESTIMONIALS
// ============================================

model Review {
  id           String   @id @default(cuid())
  productId    String
  userId       String
  
  rating       Int      // 1-5
  title        String?
  body         String   @db.Text
  
  isVerified   Boolean  @default(false) // Verified purchase
  isApproved   Boolean  @default(false) // Admin approval
  
  helpfulCount Int      @default(0)
  
  createdAt    DateTime @default(now())
  updatedAt    DateTime @updatedAt
  
  product      Product  @relation(fields: [productId], references: [id], onDelete: Cascade)
  user         User     @relation(fields: [userId], references: [id], onDelete: Cascade)

  @@unique([productId, userId])
  @@index([productId])
  @@index([isApproved])
  @@map("reviews")
}

model Testimonial {
  id              String   @id @default(cuid())
  productId       String?
  
  // Author (may not be a user)
  authorName      String
  authorTitle     String?
  authorLocation  String?
  authorImage     String?
  
  // Content
  quote           String   @db.Text
  
  // Display
  isVerified      Boolean  @default(false)
  isFeatured      Boolean  @default(false)
  isIlluminated   Boolean  @default(false) // Special styling
  
  folioReference  String?  // e.g., "Folio VII, Entry 12"
  
  // Admin
  isApproved      Boolean  @default(false)
  
  createdAt       DateTime @default(now())
  updatedAt       DateTime @updatedAt
  
  product         Product? @relation(fields: [productId], references: [id])

  @@index([isFeatured])
  @@index([isApproved])
  @@map("testimonials")
}

// ============================================
// NEWSLETTER
// ============================================

model NewsletterSubscriber {
  id              String           @id @default(cuid())
  email           String           @unique
  name            String?
  
  status          SubscriberStatus @default(ACTIVE)
  source          String?          // Where they subscribed from
  
  // Preferences
  preferences     Json             @default("{}")
  
  subscribedAt    DateTime         @default(now())
  unsubscribedAt  DateTime?
  
  // Verification
  verificationToken String?
  verifiedAt        DateTime?

  @@index([email])
  @@index([status])
  @@map("newsletter_subscribers")
}

// ============================================
// AUDIT & LOGGING
// ============================================

model AuditLog {
  id          String   @id @default(cuid())
  userId      String?
  
  action      String   // CREATE, UPDATE, DELETE, LOGIN, etc.
  entityType  String   // User, Product, Order, etc.
  entityId    String?
  
  oldValues   Json?
  newValues   Json?
  
  ipAddress   String?
  userAgent   String?
  
  createdAt   DateTime @default(now())
  
  user        User?    @relation(fields: [userId], references: [id])

  @@index([userId])
  @@index([entityType])
  @@index([action])
  @@index([createdAt])
  @@map("audit_logs")
}

// ============================================
// CONTENT MANAGEMENT
// ============================================

model Page {
  id            String   @id @default(cuid())
  title         String
  slug          String   @unique
  content       String   @db.Text
  
  // SEO
  metaTitle     String?
  metaDescription String? @db.Text
  
  isPublished   Boolean  @default(false)
  publishedAt   DateTime?
  
  createdAt     DateTime @default(now())
  updatedAt     DateTime @updatedAt

  @@index([slug])
  @@index([isPublished])
  @@map("pages")
}

model AlchemyStep {
  id          String   @id @default(cuid())
  
  position    Int
  romanNumeral String  // I, II, III, IV
  
  title       String   // e.g., "Nigredo • The Blackening"
  description String   @db.Text
  symbol      String?  // ♁, ☁, ☀, ❤
  
  // Duration & details
  duration    String?
  temperature String?
  vessel      String?
  process     String?
  
  createdAt   DateTime @default(now())
  updatedAt   DateTime @updatedAt

  @@unique([position])
  @@map("alchemy_steps")
}

// ============================================
// CONFIGURATION
// ============================================

model Setting {
  id        String   @id @default(cuid())
  key       String   @unique
  value     Json
  
  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt

  @@map("settings")
}
5.3 Database Indexes Strategy
SQL

-- Additional indexes for performance optimization
-- Run after Prisma migrations

-- Full-text search on products
CREATE INDEX IF NOT EXISTS idx_products_search 
ON products USING gin(to_tsvector('english', name || ' ' || COALESCE(description, '') || ' ' || COALESCE(latin_name, '')));

-- Composite index for product listing queries
CREATE INDEX IF NOT EXISTS idx_products_listing 
ON products (is_active, category_id, price) 
WHERE deleted_at IS NULL;

-- Composite index for order queries
CREATE INDEX IF NOT EXISTS idx_orders_user_status 
ON orders (user_id, status, created_at DESC);

-- Partial index for active carts
CREATE INDEX IF NOT EXISTS idx_carts_active 
ON carts (updated_at) 
WHERE expires_at IS NULL OR expires_at > NOW();

-- Index for inventory low stock alerts
CREATE INDEX IF NOT EXISTS idx_inventory_low_stock 
ON inventory (product_id) 
WHERE quantity <= low_stock_threshold;
5.4 Seed Data Structure
TypeScript

// prisma/seed.ts

import { PrismaClient, ProductRarity, ProductSeason, UserRole } from '@prisma/client';

const prisma = new PrismaClient();

async function main() {
  // ========================================
  // CATEGORIES (Humours)
  // ========================================
  const categories = await Promise.all([
    prisma.category.upsert({
      where: { slug: 'calming' },
      update: {},
      create: {
        name: 'Calming',
        slug: 'calming',
        description: 'Essences that promote tranquility, rest, and peaceful contemplation.',
        humourSymbol: '☾',
        color: '#B8A9C9',
        metaTitle: 'Calming Essences | Atelier Arôme',
        metaDescription: 'Discover our collection of calming botanical essences for tranquility and rest.',
      },
    }),
    prisma.category.upsert({
      where: { slug: 'uplifting' },
      update: {},
      create: {
        name: 'Uplifting',
        slug: 'uplifting',
        description: 'Essences that elevate mood, inspire joy, and brighten the spirit.',
        humourSymbol: '☀',
        color: '#F5D489',
        metaTitle: 'Uplifting Essences | Atelier Arôme',
        metaDescription: 'Experience our uplifting botanical essences that elevate mood and inspire joy.',
      },
    }),
    prisma.category.upsert({
      where: { slug: 'grounding' },
      update: {},
      create: {
        name: 'Grounding',
        slug: 'grounding',
        description: 'Essences that center the mind, connect to earth, and provide stability.',
        humourSymbol: '♁',
        color: '#7C6354',
        metaTitle: 'Grounding Essences | Atelier Arôme',
        metaDescription: 'Explore our grounding botanical essences for centering and stability.',
      },
    }),
    prisma.category.upsert({
      where: { slug: 'clarifying' },
      update: {},
      create: {
        name: 'Clarifying',
        slug: 'clarifying',
        description: 'Essences that clear the mind, refresh the senses, and promote mental clarity.',
        humourSymbol: '☁',
        color: '#7CB9A0',
        metaTitle: 'Clarifying Essences | Atelier Arôme',
        metaDescription: 'Discover our clarifying botanical essences for mental clarity and focus.',
      },
    }),
  ]);

  console.log('Created categories:', categories.map(c => c.name));

  // ========================================
  // PRODUCTS
  // ========================================
  const products = [
    {
      name: 'Provence Lavender',
      slug: 'provence-lavender',
      latinName: 'Lavandula × intermedia',
      sku: 'LAV-724',
      shortDescription: 'Harvested at dawn in the Provençal hills, possessing a sweetness found only in blossoms kissed by morning light.',
      description: `Harvested at dawn in the Provençal hills, this lavender possesses a sweetness found only in blossoms kissed by the morning's first light. Its effect is one of profound calm, like the silence between breaths.

Our Provence Lavender is sourced from a third-generation family farm in the Luberon valley, where traditional harvesting methods have been preserved for over a century. Each batch is hand-picked during the brief window of peak bloom, typically lasting only 10-14 days in early July.

The steam distillation process is conducted at precisely 40°C over 72 hours, preserving the most delicate aromatic compounds that would be destroyed by higher temperatures.`,
      usageGuidance: 'Add 3-5 drops to a diffuser for evening relaxation, or blend with a carrier oil for a calming massage. Perfect for pillow mists and bath rituals.',
      price: 42.00,
      compareAtPrice: null,
      categorySlug: 'calming',
      rarity: ProductRarity.RARE,
      season: ProductSeason.SUMMER,
      scentNotes: ['Floral', 'Herbaceous', 'Sweet'],
      extractionMethod: 'Steam Distillation',
      botanicalFamily: 'Lamiaceae',
      origin: 'Provence, France',
      harvestSeason: 'Early July',
      volumeMl: 5,
      folioNumber: 'I',
      isFeatured: true,
      stockQuantity: 24,
    },
    {
      name: 'Tasmanian Eucalyptus',
      slug: 'tasmanian-eucalyptus',
      latinName: 'Eucalyptus globulus',
      sku: 'EUC-511',
      shortDescription: 'The crisp, clean scent of Tasmania\'s ancient forests.',
      description: `The crisp, clean scent of Tasmania's ancient forests. This essence clears the mind as morning mist clears from mountain valleys.

Sourced from old-growth eucalyptus forests in Tasmania's central highlands, this essence captures the essence of pristine wilderness. The trees grow at elevations above 1,000 meters, where cold temperatures and clean air produce leaves of exceptional aromatic quality.`,
      usageGuidance: 'Ideal for steam inhalation during respiratory congestion, or add to a diffuser for a fresh, clean atmosphere. Excellent for morning clarity rituals.',
      price: 36.00,
      compareAtPrice: null,
      categorySlug: 'clarifying',
      rarity: ProductRarity.COMMON,
      season: ProductSeason.AUTUMN,
      scentNotes: ['Camphorous', 'Fresh', 'Clean'],
      extractionMethod: 'Steam Distillation',
      botanicalFamily: 'Myrtaceae',
      origin: 'Tasmania, Australia',
      harvestSeason: 'Late Autumn',
      volumeMl: 5,
      folioNumber: 'II',
      isFeatured: false,
      stockQuantity: 48,
    },
    {
      name: 'Calabrian Bergamot',
      slug: 'calabrian-bergamot',
      latinName: 'Citrus bergamia',
      sku: 'BER-328',
      shortDescription: 'From Italy\'s sun-drenched Calabrian coast, capturing the joyful brightness of citrus groves at harvest.',
      description: `From Italy's sun-drenched Calabrian coast, this essence captures the joyful brightness of citrus groves at harvest. A note of pure sunlight.

Bergamot thrives only in the specific microclimate of Calabria's Ionian coast, where the combination of mineral-rich soil, Mediterranean sun, and sea breezes creates conditions found nowhere else on Earth. Our bergamot is cold-pressed from the rinds of fruit harvested at peak ripeness in late winter.`,
      usageGuidance: 'Uplifting in any diffuser blend. Note: bergamot is photosensitive—avoid skin application before sun exposure. Perfect for afternoon energy renewal.',
      price: 48.00,
      compareAtPrice: 55.00,
      categorySlug: 'uplifting',
      rarity: ProductRarity.LIMITED,
      season: ProductSeason.WINTER,
      scentNotes: ['Citrus', 'Bright', 'Spicy'],
      extractionMethod: 'Cold Press',
      botanicalFamily: 'Rutaceae',
      origin: 'Calabria, Italy',
      harvestSeason: 'Late Winter',
      volumeMl: 5,
      folioNumber: 'III',
      isFeatured: true,
      stockQuantity: 12,
    },
    // Add more products...
  ];

  for (const productData of products) {
    const category = categories.find(c => c.slug === productData.categorySlug);
    if (!category) continue;

    const { categorySlug, stockQuantity, ...rest } = productData;

    const product = await prisma.product.upsert({
      where: { slug: productData.slug },
      update: {},
      create: {
        ...rest,
        categoryId: category.id,
        inventory: {
          create: {
            quantity: stockQuantity,
            lowStockThreshold: 5,
          },
        },
      },
    });

    console.log('Created product:', product.name);
  }

  // ========================================
  // TESTIMONIALS
  // ========================================
  const testimonials = [
    {
      authorName: 'Isabelle Moreau',
      authorTitle: 'Writer & Historian',
      authorLocation: 'Paris, France',
      quote: 'The Provence Lavender has transformed my evening ritual into a sacred practice. Its scent is not merely pleasant—it is profound, layered, and seems to hold within it the very quiet of the Provençal hills at dusk. This is not aromatherapy; it is time travel for the senses.',
      isVerified: true,
      isFeatured: true,
      isIlluminated: true,
      folioReference: 'Folio VII, Entry 12',
      isApproved: true,
    },
    {
      authorName: 'Marco Ferrara',
      authorTitle: 'Michelin-starred Chef',
      authorLocation: 'Florence, Italy',
      quote: 'As a chef, I understand transformation. What Atelier Arôme achieves with botanicals is culinary artistry for the soul. The Calabrian Bergamot is sunshine captured—it brightens not just a room, but one\'s very disposition.',
      isVerified: false,
      isFeatured: true,
      isIlluminated: false,
      isApproved: true,
    },
    {
      authorName: 'Dr. Evelyn Reed',
      authorTitle: 'Botanical Researcher',
      authorLocation: 'Oxford, UK',
      quote: 'The attention to detail is evident in every aspect. From the wax seal on the phial to the complexity of the scent itself—this is craftsmanship of the highest order. Each essence tells a story.',
      isVerified: false,
      isFeatured: true,
      isIlluminated: false,
      isApproved: true,
    },
  ];

  for (const testimonial of testimonials) {
    await prisma.testimonial.create({
      data: testimonial,
    });
  }

  console.log('Created testimonials');

  // ========================================
  // ALCHEMY STEPS
  // ========================================
  const alchemySteps = [
    {
      position: 1,
      romanNumeral: 'I',
      title: 'Nigredo • The Blackening',
      description: 'The raw botanical material undergoes its initial transformation through careful drying and preparation. This stage represents the dissolution of the material\'s original form, a necessary darkness before illumination.',
      symbol: '♁',
      duration: '7-14 Days',
      temperature: 'Ambient',
    },
    {
      position: 2,
      romanNumeral: 'II',
      title: 'Albedo • The Whitening',
      description: 'Through gentle steam distillation at precisely 40°C, the volatile aromatic compounds are released. This careful extraction preserves the most delicate notes that higher temperatures would destroy.',
      symbol: '☁',
      duration: '72 Hours',
      temperature: '40°C ±0.1',
    },
    {
      position: 3,
      romanNumeral: 'III',
      title: 'Citrinitas • The Yellowing',
      description: 'The separated essential oil undergoes a period of maturation in hand-blown glass vessels. During this stage, the aromatic profile deepens and complexifies, much like wine aging in oak barrels.',
      symbol: '☀',
      duration: '30-90 Days',
      vessel: 'Hand-blown Glass',
    },
    {
      position: 4,
      romanNumeral: 'IV',
      title: 'Rubedo • The Reddening',
      description: 'The final essence is evaluated, filtered, and bottled by hand. Each phial receives our wax seal, marking the completion of the transformation from raw botanical to perfected essence.',
      symbol: '❤',
      process: 'Hand-bottling',
    },
  ];

  for (const step of alchemySteps) {
    await prisma.alchemyStep.upsert({
      where: { position: step.position },
      update: step,
      create: step,
    });
  }

  console.log('Created alchemy steps');

  // ========================================
  // ADMIN USER
  // ========================================
  const adminUser = await prisma.user.upsert({
    where: { email: 'admin@atelierarome.com' },
    update: {},
    create: {
      email: 'admin@atelierarome.com',
      name: 'Atelier Administrator',
      role: UserRole.SUPER_ADMIN,
      emailVerified: new Date(),
    },
  });

  console.log('Created admin user:', adminUser.email);

  console.log('✅ Seed completed successfully');
}

main()
  .catch((e) => {
    console.error('❌ Seed failed:', e);
    process.exit(1);
  })
  .finally(async () => {
    await prisma.$disconnect();
  });
6. API Specification
6.1 API Architecture Overview
text

┌─────────────────────────────────────────────────────────────────────────────────┐
│                              API ARCHITECTURE                                    │
└─────────────────────────────────────────────────────────────────────────────────┘

                              ┌─────────────────────────────┐
                              │      CLIENT APPLICATION     │
                              │   (React Server Components  │
                              │    + Client Components)     │
                              └─────────────┬───────────────┘
                                            │
                    ┌───────────────────────┼───────────────────────┐
                    │                       │                       │
                    ▼                       ▼                       ▼
         ┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
         │  Server Actions │    │   tRPC Client   │    │   REST Calls    │
         │  (Mutations)    │    │   (Queries +    │    │   (Webhooks)    │
         │                 │    │    Mutations)   │    │                 │
         └────────┬────────┘    └────────┬────────┘    └────────┬────────┘
                  │                      │                      │
                  └──────────────────────┼──────────────────────┘
                                         │
                                         ▼
                              ┌─────────────────────────────┐
                              │        API LAYER            │
                              │  ┌─────────────────────┐   │
                              │  │   Authentication    │   │
                              │  │   Middleware        │   │
                              │  └─────────────────────┘   │
                              │  ┌─────────────────────┐   │
                              │  │   Rate Limiting     │   │
                              │  │   Middleware        │   │
                              │  └─────────────────────┘   │
                              │  ┌─────────────────────┐   │
                              │  │   Validation        │   │
                              │  │   (Zod)             │   │
                              │  └─────────────────────┘   │
                              └─────────────┬───────────────┘
                                            │
                                            ▼
                              ┌─────────────────────────────┐
                              │       SERVICE LAYER         │
                              │  ┌───────────────────────┐ │
                              │  │  ProductService       │ │
                              │  │  CartService          │ │
                              │  │  OrderService         │ │
                              │  │  UserService          │ │
                              │  │  PaymentService       │ │
                              │  └───────────────────────┘ │
                              └─────────────┬───────────────┘
                                            │
                                            ▼
                              ┌─────────────────────────────┐
                              │     DATA ACCESS LAYER       │
                              │         (Prisma)            │
                              
