Project Architecture Document (PAD)
Atelier Arôme — Artisanal Aromatherapy E-Commerce Platform
Document Control
Attribute	Value
Document Version	1.0.0
Status	Final Draft
Classification	Technical Specification
Target Audience	Developers, AI Coding Agents, Technical Architects
Last Updated	2024
Table of Contents
Executive Summary
Project Vision & Objectives
Technical Architecture Overview
Technology Stack Specification
Database Architecture
API Architecture
Frontend Architecture
Design System Specification
Authentication & Authorization
E-Commerce Domain Logic
Content Management System
Email & Notification System
Performance Strategy
Security Architecture
Accessibility Specification
Testing Strategy
Deployment & Infrastructure
Monitoring & Observability
Development Guidelines
Appendices
1. Executive Summary
1.1 Project Definition
Atelier Arôme is a luxury artisanal aromatherapy e-commerce platform that transforms the digital shopping experience into an illuminated manuscript journey. The platform sells handcrafted botanical essences through a Renaissance-inspired interface that honors ancient alchemical traditions while delivering modern e-commerce functionality.

1.2 Core Value Proposition
text

┌─────────────────────────────────────────────────────────────────────────┐
│                         VALUE PROPOSITION                                │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  "Where botanical science becomes sensory poetry"                        │
│                                                                          │
│  • Premium artisanal essences ($36-$68 per 5ml phial)                   │
│  • Renaissance manuscript aesthetic as brand differentiator              │
│  • Storytelling-first commerce (narrative over transaction)              │
│  • Target demographic: Affluent wellness enthusiasts, 28-55              │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
1.3 Document Purpose
This PAD serves as the single source of truth for implementing the complete Atelier Arôme platform. Any developer or AI coding agent should be able to:

Implement the full codebase without ambiguity
Make architectural decisions consistent with this specification
Maintain the aesthetic and technical vision throughout development
Extend the platform following established patterns
1.4 Success Criteria
Metric	Target
Lighthouse Performance	≥ 90
Lighthouse Accessibility	≥ 98
Core Web Vitals (LCP)	< 2.0s
Core Web Vitals (FID)	< 100ms
Core Web Vitals (CLS)	< 0.05
WCAG Compliance	AAA
Uptime SLA	99.9%
Cart Abandonment Rate	< 60%
2. Project Vision & Objectives
2.1 Vision Statement
Transform the transactional e-commerce experience into a contemplative journey through an illuminated manuscript, where each product is a verse in nature's poetry and the purchase process becomes a ritual of discovery.

2.2 Strategic Objectives
text

┌─────────────────────────────────────────────────────────────────────────┐
│                        STRATEGIC OBJECTIVES                              │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  O1: BRAND DIFFERENTIATION                                               │
│      Create an unforgettable digital experience that competitors         │
│      cannot replicate through template solutions                         │
│                                                                          │
│  O2: CONVERSION OPTIMIZATION                                             │
│      Balance aesthetic richness with frictionless purchasing             │
│      while maintaining premium positioning                               │
│                                                                          │
│  O3: CUSTOMER RETENTION                                                  │
│      Build patron relationships through storytelling,                    │
│      correspondence (newsletter), and exclusive access                   │
│                                                                          │
│  O4: OPERATIONAL EXCELLENCE                                              │
│      Implement robust inventory, order, and fulfillment                  │
│      management for artisanal production scale                          │
│                                                                          │
│  O5: SCALABLE ARCHITECTURE                                               │
│      Build foundation for international expansion,                       │
│      localization, and product line extensions                          │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
2.3 User Personas
2.3.1 Primary Persona: The Conscious Connoisseur
YAML

Name: Isabelle
Age: 38
Occupation: Writer/Creative Professional
Income: $120,000+
Location: Urban, cosmopolitan

Characteristics:
  - Values craftsmanship and authenticity
  - Willing to pay premium for quality
  - Researches products thoroughly before purchase
  - Appreciates narrative and storytelling
  - Active on Instagram, Pinterest

Goals:
  - Find unique, artisanal products
  - Understand provenance and process
  - Curate a personal aromatic collection
  - Share discoveries with like-minded community

Pain Points:
  - Overwhelmed by generic wellness products
  - Skeptical of marketing claims
  - Limited time for extensive browsing
2.3.2 Secondary Persona: The Thoughtful Gifter
YAML

Name: Marcus
Age: 45
Occupation: Executive/Professional
Income: $180,000+
Location: Suburban

Characteristics:
  - Purchases for partners, clients, colleagues
  - Values presentation and unboxing experience
  - Makes purchasing decisions quickly once committed
  - Prefers curated recommendations

Goals:
  - Find memorable, distinctive gifts
  - Easy gifting options (gift wrap, messages)
  - Reliable delivery for occasions

Pain Points:
  - Decision fatigue when choosing products
  - Concerns about recipient preferences
  - Time constraints for shopping
2.4 Feature Priority Matrix
text

┌────────────────────────────────────────────────────────────────────────┐
│                    FEATURE PRIORITY MATRIX                              │
├────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  HIGH IMPACT                                                            │
│      │                                                                  │
│      │  ┌─────────────────┐      ┌─────────────────┐                   │
│      │  │ Product Catalog │      │ Checkout Flow   │                   │
│      │  │ & Filtering     │      │ & Payments      │                   │
│      │  └─────────────────┘      └─────────────────┘                   │
│      │                                                                  │
│      │  ┌─────────────────┐      ┌─────────────────┐                   │
│      │  │ User Accounts   │      │ Order Management│                   │
│      │  │ & Auth          │      │                 │                   │
│      │  └─────────────────┘      └─────────────────┘                   │
│      │                                                                  │
│  MEDIUM│  ┌─────────────────┐      ┌─────────────────┐                 │
│  IMPACT│  │ Newsletter/     │      │ Testimonials/   │                 │
│      │  │ Correspondence  │      │ Reviews         │                   │
│      │  └─────────────────┘      └─────────────────┘                   │
│      │                                                                  │
│      │  ┌─────────────────┐      ┌─────────────────┐                   │
│      │  │ Wishlist/       │      │ Gift Options    │                   │
│      │  │ Favorites       │      │                 │                   │
│      │  └─────────────────┘      └─────────────────┘                   │
│      │                                                                  │
│  LOW │  ┌─────────────────┐      ┌─────────────────┐                   │
│  IMPACT│  │ Loyalty Program │      │ Subscription    │                 │
│      │  │                 │      │ Service         │                   │
│      │  └─────────────────┘      └─────────────────┘                   │
│      │                                                                  │
│      └──────────────────────────────────────────────────►              │
│           LOW EFFORT              HIGH EFFORT                           │
│                                                                         │
└────────────────────────────────────────────────────────────────────────┘
3. Technical Architecture Overview
3.1 High-Level Architecture Diagram
text

┌─────────────────────────────────────────────────────────────────────────────────────┐
│                              ATELIER ARÔME ARCHITECTURE                              │
└─────────────────────────────────────────────────────────────────────────────────────┘

                                    ┌─────────────────┐
                                    │   CDN (Vercel)  │
                                    │   Edge Network  │
                                    └────────┬────────┘
                                             │
                                             ▼
┌─────────────────────────────────────────────────────────────────────────────────────┐
│                                  CLIENT LAYER                                        │
├─────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                      │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐                 │
│  │   Desktop   │  │   Mobile    │  │   Tablet    │  │    PWA      │                 │
│  │   Browser   │  │   Browser   │  │   Browser   │  │  (Future)   │                 │
│  └──────┬──────┘  └──────┬──────┘  └──────┬──────┘  └──────┬──────┘                 │
│         │                │                │                │                         │
│         └────────────────┴────────────────┴────────────────┘                         │
│                                    │                                                 │
│                          ┌─────────▼─────────┐                                       │
│                          │    Next.js 14+    │                                       │
│                          │   React 18+ RSC   │                                       │
│                          │  Tailwind + Shadcn│                                       │
│                          └─────────┬─────────┘                                       │
│                                    │                                                 │
└────────────────────────────────────┼────────────────────────────────────────────────┘
                                     │
                                     ▼
┌─────────────────────────────────────────────────────────────────────────────────────┐
│                               APPLICATION LAYER                                      │
├─────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                      │
│  ┌─────────────────────────────────────────────────────────────────────────────┐    │
│  │                         Next.js App Router                                   │    │
│  ├─────────────────────────────────────────────────────────────────────────────┤    │
│  │                                                                              │    │
│  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐     │    │
│  │  │    Pages     │  │   Layouts    │  │  Components  │  │   Hooks      │     │    │
│  │  │  (RSC/RCC)   │  │   (RSC)      │  │  (RSC/RCC)   │  │              │     │    │
│  │  └──────────────┘  └──────────────┘  └──────────────┘  └──────────────┘     │    │
│  │                                                                              │    │
│  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐     │    │
│  │  │   Server     │  │     API      │  │  Middleware  │  │   Actions    │     │    │
│  │  │   Actions    │  │   Routes     │  │              │  │   (Mutations)│     │    │
│  │  └──────────────┘  └──────────────┘  └──────────────┘  └──────────────┘     │    │
│  │                                                                              │    │
│  └─────────────────────────────────────────────────────────────────────────────┘    │
│                                                                                      │
│  ┌─────────────────────────────────────────────────────────────────────────────┐    │
│  │                           SERVICE LAYER                                      │    │
│  ├─────────────────────────────────────────────────────────────────────────────┤    │
│  │                                                                              │    │
│  │  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐            │    │
│  │  │   Product   │ │    Cart     │ │    Order    │ │    User     │            │    │
│  │  │   Service   │ │   Service   │ │   Service   │ │   Service   │            │    │
│  │  └─────────────┘ └─────────────┘ └─────────────┘ └─────────────┘            │    │
│  │                                                                              │    │
│  │  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐            │    │
│  │  │   Payment   │ │    Email    │ │   Content   │ │  Analytics  │            │    │
│  │  │   Service   │ │   Service   │ │   Service   │ │   Service   │            │    │
│  │  └─────────────┘ └─────────────┘ └─────────────┘ └─────────────┘            │    │
│  │                                                                              │    │
│  └─────────────────────────────────────────────────────────────────────────────┘    │
│                                                                                      │
└─────────────────────────────────────────────────────────────────────────────────────┘
                                     │
                                     ▼
┌─────────────────────────────────────────────────────────────────────────────────────┐
│                                 DATA LAYER                                           │
├─────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                      │
│  ┌─────────────────────────────────────────────────────────────────────────────┐    │
│  │                              Prisma ORM                                      │    │
│  └─────────────────────────────────────────────────────────────────────────────┘    │
│                                     │                                                │
│         ┌───────────────────────────┼───────────────────────────┐                   │
│         │                           │                           │                   │
│         ▼                           ▼                           ▼                   │
│  ┌─────────────────┐      ┌─────────────────┐      ┌─────────────────┐             │
│  │   PostgreSQL    │      │      Redis      │      │   Blob Storage  │             │
│  │   (Neon/Supabase)│      │   (Upstash)    │      │  (Cloudinary)   │             │
│  │                  │      │                 │      │                  │             │
│  │  • Users         │      │  • Sessions     │      │  • Product Images│             │
│  │  • Products      │      │  • Cart Cache   │      │  • Botanical Art │             │
│  │  • Orders        │      │  • Rate Limits  │      │  • User Uploads  │             │
│  │  • Testimonials  │      │                 │      │                  │             │
│  └─────────────────┘      └─────────────────┘      └─────────────────┘             │
│                                                                                      │
└─────────────────────────────────────────────────────────────────────────────────────┘
                                     │
                                     ▼
┌─────────────────────────────────────────────────────────────────────────────────────┐
│                            EXTERNAL SERVICES                                         │
├─────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                      │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐             │
│  │    Stripe    │  │    Resend    │  │   Clerk/     │  │   Sentry     │             │
│  │   Payments   │  │    Email     │  │   NextAuth   │  │  Monitoring  │             │
│  └──────────────┘  └──────────────┘  └──────────────┘  └──────────────┘             │
│                                                                                      │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐             │
│  │   Vercel     │  │   PostHog    │  │   Shippo     │  │   Algolia    │             │
│  │   Analytics  │  │   Analytics  │  │   Shipping   │  │   Search     │             │
│  └──────────────┘  └──────────────┘  └──────────────┘  └──────────────┘             │
│                                                                                      │
└─────────────────────────────────────────────────────────────────────────────────────┘
3.2 Request Flow Diagram
text

┌─────────────────────────────────────────────────────────────────────────────────────┐
│                           REQUEST FLOW: ADD TO CART                                  │
└─────────────────────────────────────────────────────────────────────────────────────┘

┌──────────┐     ┌──────────┐     ┌──────────┐     ┌──────────┐     ┌──────────┐
│  Client  │     │   Edge   │     │  Next.js │     │  Prisma  │     │ Postgres │
│  (React) │     │ Middleware│     │  Server  │     │   ORM    │     │    DB    │
└────┬─────┘     └────┬─────┘     └────┬─────┘     └────┬─────┘     └────┬─────┘
     │                │                │                │                │
     │  1. Click      │                │                │                │
     │  "Add to Vial" │                │                │                │
     │────────────────►                │                │                │
     │                │                │                │                │
     │                │  2. Auth       │                │                │
     │                │  Validation    │                │                │
     │                │───────────────►│                │                │
     │                │                │                │                │
     │                │                │  3. Server     │                │
     │                │                │  Action        │                │
     │                │                │  (addToCart)   │                │
     │                │                │────────────────►                │
     │                │                │                │                │
     │                │                │                │  4. Query      │
     │                │                │                │  Product       │
     │                │                │                │────────────────►
     │                │                │                │                │
     │                │                │                │  5. Product    │
     │                │                │                │◄────────────────
     │                │                │                │                │
     │                │                │                │  6. Upsert     │
     │                │                │                │  Cart Item     │
     │                │                │                │────────────────►
     │                │                │                │                │
     │                │                │                │  7. Updated    │
     │                │                │                │  Cart          │
     │                │                │                │◄────────────────
     │                │                │                │                │
     │                │                │  8. Cart       │                │
     │                │                │  State         │                │
     │                │                │◄────────────────                │
     │                │                │                │                │
     │  9. Revalidate │                │                │                │
     │  + Toast       │                │                │                │
     │◄────────────────────────────────│                │                │
     │                │                │                │                │
     │  10. A11y      │                │                │                │
     │  Announcement  │                │                │                │
     │  (Live Region) │                │                │                │
     │                │                │                │                │
     ▼                ▼                ▼                ▼                ▼
3.3 Component Architecture Overview
text

┌─────────────────────────────────────────────────────────────────────────────────────┐
│                          COMPONENT ARCHITECTURE                                      │
└─────────────────────────────────────────────────────────────────────────────────────┘

                              ┌─────────────────────┐
                              │    RootLayout       │
                              │    (Server)         │
                              │                     │
                              │  • Fonts            │
                              │  • Metadata         │
                              │  • Theme Provider   │
                              │  • Session Provider │
                              └──────────┬──────────┘
                                         │
              ┌──────────────────────────┼──────────────────────────┐
              │                          │                          │
              ▼                          ▼                          ▼
    ┌─────────────────┐      ┌─────────────────────┐      ┌─────────────────┐
    │  MarketingLayout│      │    ShopLayout       │      │   AdminLayout   │
    │     (Server)    │      │     (Server)        │      │    (Server)     │
    │                 │      │                     │      │                 │
    │  • Hero Header  │      │  • Shop Header      │      │  • Admin Nav    │
    │  • Full Footer  │      │  • Mini Footer      │      │  • Sidebar      │
    └────────┬────────┘      └──────────┬──────────┘      └────────┬────────┘
             │                          │                          │
    ┌────────┴────────┐      ┌──────────┴──────────┐      ┌────────┴────────┐
    │                 │      │                     │      │                 │
    ▼                 ▼      ▼                     ▼      ▼                 ▼
┌───────┐  ┌───────┐  ┌───────────┐  ┌───────────┐  ┌───────────┐  ┌───────────┐
│ Home  │  │ About │  │Compendium │  │  Product  │  │ Dashboard │  │  Orders   │
│ Page  │  │ Page  │  │  (Shop)   │  │  Detail   │  │   Page    │  │   Page    │
└───────┘  └───────┘  └───────────┘  └───────────┘  └───────────┘  └───────────┘
4. Technology Stack Specification
4.1 Complete Stack Definition
YAML

# ═══════════════════════════════════════════════════════════════════════════════
# TECHNOLOGY STACK SPECIFICATION
# ═══════════════════════════════════════════════════════════════════════════════

frontend:
  framework: "Next.js 14.2+"
  runtime: "React 18.3+"
  rendering:
    - "React Server Components (RSC) - Default"
    - "Client Components - Interactive elements only"
  styling:
    primary: "Tailwind CSS 4.0"
    components: "Shadcn/UI (Radix primitives)"
    methodology: "Utility-first with component abstraction"
  state_management:
    server: "React Server Components (fetch + cache)"
    client: "Zustand (minimal client state)"
    forms: "React Hook Form + Zod"
  animations:
    library: "Framer Motion 11+"
    css: "Tailwind transitions + @keyframes"

backend:
  framework: "Next.js App Router (API Routes + Server Actions)"
  language: "TypeScript 5.4+"
  orm: "Prisma 5.10+"
  validation: "Zod 3.22+"
  
database:
  primary: "PostgreSQL 15+"
  provider: "Neon (serverless) OR Supabase"
  caching: "Upstash Redis"
  
authentication:
  provider: "Clerk OR NextAuth.js v5"
  strategies:
    - "Email/Password"
    - "Magic Link"
    - "OAuth (Google, Apple)"
  session: "JWT (stateless) OR Database sessions"

payments:
  provider: "Stripe"
  features:
    - "Stripe Checkout"
    - "Stripe Elements (embedded)"
    - "Stripe Webhooks"
    - "Stripe Tax (optional)"

email:
  provider: "Resend"
  templates: "React Email"
  
file_storage:
  provider: "Cloudinary OR Uploadthing"
  cdn: "Vercel Edge Network"

search:
  provider: "Algolia OR Meilisearch (self-hosted)"
  fallback: "PostgreSQL full-text search"

analytics:
  primary: "PostHog"
  secondary: "Vercel Analytics"
  
monitoring:
  errors: "Sentry"
  logs: "Axiom OR Vercel Logs"
  uptime: "Vercel / Better Uptime"

deployment:
  platform: "Vercel"
  regions: "iad1 (primary), sfo1 (secondary)"
  edge: "Vercel Edge Middleware"

development:
  package_manager: "pnpm 8+"
  linting: "ESLint + Prettier"
  type_checking: "TypeScript strict mode"
  git_hooks: "Husky + lint-staged"
  testing:
    unit: "Vitest"
    integration: "Playwright"
    e2e: "Playwright"
4.2 Version Pinning
JSON

{
  "engines": {
    "node": ">=20.0.0",
    "pnpm": ">=8.0.0"
  },
  "dependencies": {
    "next": "^14.2.0",
    "react": "^18.3.0",
    "react-dom": "^18.3.0",
    "@prisma/client": "^5.10.0",
    "zod": "^3.22.0",
    "zustand": "^4.5.0",
    "framer-motion": "^11.0.0",
    "@clerk/nextjs": "^4.29.0",
    "stripe": "^14.0.0",
    "@stripe/stripe-js": "^3.0.0",
    "resend": "^3.0.0",
    "@tanstack/react-query": "^5.0.0",
    "react-hook-form": "^7.50.0",
    "@hookform/resolvers": "^3.3.0"
  },
  "devDependencies": {
    "typescript": "^5.4.0",
    "prisma": "^5.10.0",
    "tailwindcss": "^4.0.0",
    "eslint": "^8.57.0",
    "prettier": "^3.2.0",
    "vitest": "^1.3.0",
    "@playwright/test": "^1.42.0"
  }
}
5. Database Architecture
5.1 Entity Relationship Diagram
text

┌─────────────────────────────────────────────────────────────────────────────────────┐
│                          ENTITY RELATIONSHIP DIAGRAM                                 │
└─────────────────────────────────────────────────────────────────────────────────────┘

                                    ┌─────────────────┐
                                    │      User       │
                                    ├─────────────────┤
                                    │ PK id           │
                                    │    clerkId      │
                                    │    email        │
                                    │    name         │
                                    │    role         │
                                    │    createdAt    │
                                    │    updatedAt    │
                                    └────────┬────────┘
                                             │
              ┌──────────────────────────────┼──────────────────────────────┐
              │                              │                              │
              │ 1:N                          │ 1:N                          │ 1:N
              ▼                              ▼                              ▼
    ┌─────────────────┐            ┌─────────────────┐            ┌─────────────────┐
    │     Address     │            │      Order      │            │   Testimonial   │
    ├─────────────────┤            ├─────────────────┤            ├─────────────────┤
    │ PK id           │            │ PK id           │            │ PK id           │
    │ FK userId       │            │ FK userId       │            │ FK userId       │
    │    type         │            │    orderNumber  │            │ FK essenceId    │
    │    firstName    │            │    status       │            │    content      │
    │    lastName     │            │    subtotal     │            │    rating       │
    │    line1        │            │    tax          │            │    status       │
    │    line2        │            │    shipping     │            │    featured     │
    │    city         │            │    total        │            │    folio        │
    │    state        │            │    currency     │            │    createdAt    │
    │    postalCode   │            │ FK addressId    │            └─────────────────┘
    │    country      │            │    stripeId     │
    │    isDefault    │            │    createdAt    │
    └─────────────────┘            │    updatedAt    │
                                   └────────┬────────┘
                                            │
                                            │ 1:N
                                            ▼
                                   ┌─────────────────┐
                                   │    OrderItem    │
                                   ├─────────────────┤
                                   │ PK id           │
                                   │ FK orderId      │
                                   │ FK essenceId    │
                                   │ FK variantId    │
                                   │    quantity     │
                                   │    unitPrice    │
                                   │    totalPrice   │
                                   └─────────────────┘
                                            ▲
                                            │ N:1
    ┌─────────────────┐            ┌────────┴────────┐            ┌─────────────────┐
    │    Category     │◄───────────│     Essence     │───────────►│    Botanical    │
    ├─────────────────┤     N:1    ├─────────────────┤     N:1    ├─────────────────┤
    │ PK id           │            │ PK id           │            │ PK id           │
    │    name         │            │    slug         │            │    latinName    │
    │    slug         │            │    name         │            │    commonName   │
    │    description  │            │    description  │            │    family       │
    │    sortOrder    │            │ FK categoryId   │            │    origin       │
    └─────────────────┘            │ FK botanicalId  │            │    description  │
                                   │    humour       │            │    properties   │
                                   │    rarity       │            │    imageUrl     │
                                   │    season       │            └─────────────────┘
                                   │    extraction   │
                                   │    notes        │
                                   │    featured     │
                                   │    published    │
                                   │    createdAt    │
                                   │    updatedAt    │
                                   └────────┬────────┘
                                            │
                                            │ 1:N
                                            ▼
                                   ┌─────────────────┐
                                   │  EssenceVariant │
                                   ├─────────────────┤
                                   │ PK id           │
                                   │ FK essenceId    │
                                   │    sku          │
                                   │    name         │
                                   │    size         │
                                   │    unit         │
                                   │    price        │
                                   │    comparePrice │
                                   │    costPrice    │
                                   │    stock        │
                                   │    lowStockAt   │
                                   │    isDefault    │
                                   └─────────────────┘


                                   ┌─────────────────┐
                                   │      Cart       │
                                   ├─────────────────┤
                                   │ PK id           │
                                   │ FK userId (opt) │
                                   │    sessionId    │
                                   │    expiresAt    │
                                   │    createdAt    │
                                   │    updatedAt    │
                                   └────────┬────────┘
                                            │
                                            │ 1:N
                                            ▼
                                   ┌─────────────────┐
                                   │    CartItem     │
                                   ├─────────────────┤
                                   │ PK id           │
                                   │ FK cartId       │
                                   │ FK variantId    │
                                   │    quantity     │
                                   │    addedAt      │
                                   └─────────────────┘


    ┌─────────────────┐            ┌─────────────────┐            ┌─────────────────┐
    │   Subscriber    │            │    Campaign     │            │   PageContent   │
    ├─────────────────┤            ├─────────────────┤            ├─────────────────┤
    │ PK id           │            │ PK id           │            │ PK id           │
    │    email        │            │    name         │            │    slug         │
    │    name         │            │    subject      │            │    title        │
    │    status       │            │    content      │            │    content      │
    │    source       │            │    status       │            │    seoTitle     │
    │    subscribedAt │            │    sentAt       │            │    seoDesc      │
    │    unsubscribedAt│           │    openRate     │            │    published    │
    │    preferences  │            │    clickRate    │            │    createdAt    │
    └─────────────────┘            └─────────────────┘            │    updatedAt    │
                                                                  └─────────────────┘
5.2 Complete Prisma Schema
prisma

// ═══════════════════════════════════════════════════════════════════════════════
// PRISMA SCHEMA - ATELIER ARÔME
// ═══════════════════════════════════════════════════════════════════════════════

generator client {
  provider        = "prisma-client-js"
  previewFeatures = ["fullTextSearch", "driverAdapters"]
}

datasource db {
  provider  = "postgresql"
  url       = env("DATABASE_URL")
  directUrl = env("DATABASE_URL_UNPOOLED")
}

// ═══════════════════════════════════════════════════════════════════════════════
// ENUMS
// ═══════════════════════════════════════════════════════════════════════════════

enum UserRole {
  PATRON       // Regular customer
  ARTISAN      // Staff member
  ALCHEMIST    // Admin/Super admin
}

enum Humour {
  CALMING      // ☾ Moon - relaxation, sleep
  UPLIFTING    // ☀ Sun - energy, joy
  GROUNDING    // ♁ Earth - stability, focus
  CLARIFYING   // ☁ Air - clarity, mental
}

enum Rarity {
  COMMON       // Standard availability
  RARE         // Limited batches
  LIMITED      // Seasonal/special edition
  EXCLUSIVE    // One-time production
}

enum Season {
  SPRING
  SUMMER
  AUTUMN
  WINTER
  ALL_SEASONS
}

enum ExtractionMethod {
  STEAM_DISTILLATION
  COLD_PRESS
  SOLVENT_EXTRACTION
  CO2_EXTRACTION
  ENFLEURAGE
  MACERATION
}

enum OrderStatus {
  PENDING          // Awaiting payment
  CONFIRMED        // Payment received
  PROCESSING       // Being prepared
  DISPATCHED       // Shipped
  DELIVERED        // Received by patron
  CANCELLED        // Cancelled
  REFUNDED         // Refunded
}

enum PaymentStatus {
  PENDING
  PROCESSING
  SUCCEEDED
  FAILED
  REFUNDED
  PARTIALLY_REFUNDED
}

enum AddressType {
  SHIPPING
  BILLING
  BOTH
}

enum TestimonialStatus {
  PENDING      // Awaiting review
  APPROVED     // Published
  REJECTED     // Not published
  FEATURED     // Highlighted on homepage
}

enum SubscriberStatus {
  ACTIVE
  UNSUBSCRIBED
  BOUNCED
  COMPLAINED
}

enum CampaignStatus {
  DRAFT
  SCHEDULED
  SENDING
  SENT
  FAILED
}

// ═══════════════════════════════════════════════════════════════════════════════
// USER & AUTHENTICATION
// ═══════════════════════════════════════════════════════════════════════════════

model User {
  id            String    @id @default(cuid())
  clerkId       String    @unique  // External auth provider ID
  email         String    @unique
  emailVerified DateTime?
  
  // Profile
  firstName     String?
  lastName      String?
  displayName   String?
  avatarUrl     String?
  phone         String?
  
  // Role & Status
  role          UserRole  @default(PATRON)
  isActive      Boolean   @default(true)
  
  // Preferences
  preferences   Json?     // { newsletter: true, notifications: {...} }
  
  // Timestamps
  createdAt     DateTime  @default(now())
  updatedAt     DateTime  @updatedAt
  lastLoginAt   DateTime?
  
  // Relations
  addresses     Address[]
  orders        Order[]
  testimonials  Testimonial[]
  cart          Cart?
  wishlist      Wishlist?
  
  @@index([email])
  @@index([clerkId])
  @@map("users")
}

model Address {
  id          String      @id @default(cuid())
  userId      String
  user        User        @relation(fields: [userId], references: [id], onDelete: Cascade)
  
  type        AddressType @default(BOTH)
  isDefault   Boolean     @default(false)
  
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
  
  // Validation
  validated   Boolean     @default(false)
  validatedAt DateTime?
  
  createdAt   DateTime    @default(now())
  updatedAt   DateTime    @updatedAt
  
  // Relations
  orders      Order[]
  
  @@index([userId])
  @@map("addresses")
}

// ═══════════════════════════════════════════════════════════════════════════════
// PRODUCT CATALOG
// ═══════════════════════════════════════════════════════════════════════════════

model Category {
  id          String    @id @default(cuid())
  slug        String    @unique
  name        String
  description String?
  
  // Display
  imageUrl    String?
  iconSymbol  String?   // Alchemical symbol
  sortOrder   Int       @default(0)
  
  // Visibility
  published   Boolean   @default(true)
  
  createdAt   DateTime  @default(now())
  updatedAt   DateTime  @updatedAt
  
  // Relations
  essences    Essence[]
  
  @@map("categories")
}

model Botanical {
  id            String    @id @default(cuid())
  slug          String    @unique
  
  // Nomenclature
  latinName     String    // e.g., "Lavandula × intermedia"
  commonName    String    // e.g., "Provence Lavender"
  family        String?   // e.g., "Lamiaceae"
  
  // Origin
  origin        String?   // e.g., "Provence, France"
  regions       String[]  // Multiple growing regions
  
  // Properties
  description   String    @db.Text
  properties    Json?     // { therapeutic: [...], aromatic: [...] }
  
  // Visuals
  imageUrl      String?
  illustrationSvg String?  @db.Text  // SVG illustration code
  
  createdAt     DateTime  @default(now())
  updatedAt     DateTime  @updatedAt
  
  // Relations
  essences      Essence[]
  
  @@map("botanicals")
}

model Essence {
  id            String    @id @default(cuid())
  slug          String    @unique
  
  // Basic Info
  name          String
  tagline       String?   // Short marketing phrase
  description   String    @db.Text
  
  // Classification
  categoryId    String
  category      Category  @relation(fields: [categoryId], references: [id])
  botanicalId   String
  botanical     Botanical @relation(fields: [botanicalId], references: [id])
  
  // Aromatic Profile
  humour        Humour
  rarity        Rarity    @default(COMMON)
  season        Season    @default(ALL_SEASONS)
  extraction    ExtractionMethod
  
  // Aromatic Notes
  topNotes      String[]
  heartNotes    String[]
  baseNotes     String[]
  
  // Production
  batchNumber   String?   // e.g., "N° 724"
  harvestDate   DateTime?
  distillDate   DateTime?
  
  // Display
  folio         String?   // Roman numeral for display (I, II, III...)
  featured      Boolean   @default(false)
  featuredOrder Int?
  
  // SEO
  seoTitle      String?
  seoDescription String?
  
  // Visibility
  published     Boolean   @default(false)
  publishedAt   DateTime?
  
  createdAt     DateTime  @default(now())
  updatedAt     DateTime  @updatedAt
  
  // Relations
  variants      EssenceVariant[]
  images        EssenceImage[]
  testimonials  Testimonial[]
  
  @@index([slug])
  @@index([categoryId])
  @@index([humour])
  @@index([rarity])
  @@index([published])
  @@map("essences")
}

model EssenceVariant {
  id            String    @id @default(cuid())
  essenceId     String
  essence       Essence   @relation(fields: [essenceId], references: [id], onDelete: Cascade)
  
  // Identification
  sku           String    @unique
  name          String    // e.g., "5ml Phial", "15ml Decanter"
  
  // Size
  size          Decimal   @db.Decimal(10, 2)  // e.g., 5.00
  unit          String    @default("ml")       // ml, oz
  
  // Pricing (in cents to avoid floating point issues)
  price         Int       // Current price in cents
  comparePrice  Int?      // Original/compare at price
  costPrice     Int?      // Cost for profit calculation
  
  // Inventory
  stock         Int       @default(0)
  lowStockAt    Int       @default(5)
  trackInventory Boolean  @default(true)
  allowBackorder Boolean  @default(false)
  
  // Display
  isDefault     Boolean   @default(false)
  sortOrder     Int       @default(0)
  
  // Status
  available     Boolean   @default(true)
  
  createdAt     DateTime  @default(now())
  updatedAt     DateTime  @updatedAt
  
  // Relations
  cartItems     CartItem[]
  orderItems    OrderItem[]
  
  @@index([essenceId])
  @@index([sku])
  @@map("essence_variants")
}

model EssenceImage {
  id          String    @id @default(cuid())
  essenceId   String
  essence     Essence   @relation(fields: [essenceId], references: [id], onDelete: Cascade)
  
  url         String
  altText     String?
  width       Int?
  height      Int?
  
  type        String    @default("product") // product, botanical, detail
  isPrimary   Boolean   @default(false)
  sortOrder   Int       @default(0)
  
  createdAt   DateTime  @default(now())
  
  @@index([essenceId])
  @@map("essence_images")
}

// ═══════════════════════════════════════════════════════════════════════════════
// CART & WISHLIST
// ═══════════════════════════════════════════════════════════════════════════════

model Cart {
  id          String    @id @default(cuid())
  
  // Owner (one of these should be set)
  userId      String?   @unique
  user        User?     @relation(fields: [userId], references: [id], onDelete: Cascade)
  sessionId   String?   @unique  // For anonymous carts
  
  // Expiration for anonymous carts
  expiresAt   DateTime?
  
  // Metadata
  currency    String    @default("USD")
  note        String?   // Gift message or special instructions
  
  createdAt   DateTime  @default(now())
  updatedAt   DateTime  @updatedAt
  
  // Relations
  items       CartItem[]
  
  @@index([sessionId])
  @@map("carts")
}

model CartItem {
  id          String    @id @default(cuid())
  cartId      String
  cart        Cart      @relation(fields: [cartId], references: [id], onDelete: Cascade)
  
  variantId   String
  variant     EssenceVariant @relation(fields: [variantId], references: [id])
  
  quantity    Int       @default(1)
  
  // Snapshot of price at time of adding
  unitPrice   Int       // Price in cents at time of adding
  
  addedAt     DateTime  @default(now())
  updatedAt   DateTime  @updatedAt
  
  @@unique([cartId, variantId])
  @@index([cartId])
  @@map("cart_items")
}

model Wishlist {
  id          String    @id @default(cuid())
  userId      String    @unique
  user        User      @relation(fields: [userId], references: [id], onDelete: Cascade)
  
  createdAt   DateTime  @default(now())
  updatedAt   DateTime  @updatedAt
  
  // Relations
  items       WishlistItem[]
  
  @@map("wishlists")
}

model WishlistItem {
  id          String    @id @default(cuid())
  wishlistId  String
  wishlist    Wishlist  @relation(fields: [wishlistId], references: [id], onDelete: Cascade)
  
  variantId   String
  
  addedAt     DateTime  @default(now())
  
  @@unique([wishlistId, variantId])
  @@index([wishlistId])
  @@map("wishlist_items")
}

// ═══════════════════════════════════════════════════════════════════════════════
// ORDERS
// ═══════════════════════════════════════════════════════════════════════════════

model Order {
  id            String        @id @default(cuid())
  orderNumber   String        @unique  // Human-readable: "AA-2024-001234"
  
  // Customer
  userId        String
  user          User          @relation(fields: [userId], references: [id])
  email         String        // Snapshot for order notifications
  
  // Status
  status        OrderStatus   @default(PENDING)
  paymentStatus PaymentStatus @default(PENDING)
  
  // Shipping Address (snapshot)
  shippingAddressId String?
  shippingAddress   Address?  @relation(fields: [shippingAddressId], references: [id])
  shippingSnapshot  Json?     // Full address snapshot at time of order
  
  // Totals (in cents)
  subtotal      Int           // Sum of line items
  discountTotal Int           @default(0)
  shippingTotal Int           @default(0)
  taxTotal      Int           @default(0)
  grandTotal    Int           // Final total
  
  currency      String        @default("USD")
  
  // Discount
  discountCode  String?
  discountType  String?       // percentage, fixed
  discountValue Int?
  
  // Payment
  stripePaymentIntentId String?
  stripeChargeId        String?
  
  // Shipping
  shippingMethod  String?
  shippingCarrier String?
  trackingNumber  String?
  trackingUrl     String?
  
  // Gift
  isGift        Boolean       @default(false)
  giftMessage   String?
  giftWrap      Boolean       @default(false)
  
  // Notes
  customerNote  String?
  internalNote  String?       // Staff notes
  
  // Timestamps
  createdAt     DateTime      @default(now())
  updatedAt     DateTime      @updatedAt
  confirmedAt   DateTime?
  dispatchedAt  DateTime?
  deliveredAt   DateTime?
  cancelledAt   DateTime?
  
  // Relations
  items         OrderItem[]
  events        OrderEvent[]
  
  @@index([userId])
  @@index([orderNumber])
  @@index([status])
  @@index([createdAt])
  @@map("orders")
}

model OrderItem {
  id            String    @id @default(cuid())
  orderId       String
  order         Order     @relation(fields: [orderId], references: [id], onDelete: Cascade)
  
  // Product snapshot (in case product is deleted later)
  variantId     String
  variant       EssenceVariant @relation(fields: [variantId], references: [id])
  essenceId     String
  
  // Snapshot of product details
  essenceName   String
  variantName   String
  sku           String
  
  // Quantity & Pricing
  quantity      Int
  unitPrice     Int       // Price per unit in cents
  totalPrice    Int       // quantity * unitPrice
  
  createdAt     DateTime  @default(now())
  
  @@index([orderId])
  @@map("order_items")
}

model OrderEvent {
  id          String    @id @default(cuid())
  orderId     String
  order       Order     @relation(fields: [orderId], references: [id], onDelete: Cascade)
  
  type        String    // status_change, note_added, email_sent, etc.
  description String
  metadata    Json?
  
  createdBy   String?   // User ID or "system"
  createdAt   DateTime  @default(now())
  
  @@index([orderId])
  @@map("order_events")
}

// ═══════════════════════════════════════════════════════════════════════════════
// TESTIMONIALS (PATRON'S MANUSCRIPT)
// ═══════════════════════════════════════════════════════════════════════════════

model Testimonial {
  id          String            @id @default(cuid())
  
  // Author
  userId      String?
  user        User?             @relation(fields: [userId], references: [id], onDelete: SetNull)
  authorName  String            // Display name (may differ from user name)
  authorTitle String?           // e.g., "Writer & Historian, Paris"
  authorLocation String?
  
  // Product (optional - can be general)
  essenceId   String?
  essence     Essence?          @relation(fields: [essenceId], references: [id], onDelete: SetNull)
  
  // Content
  content     String            @db.Text
  rating      Int?              @default(5)  // 1-5 stars (optional)
  
  // Display
  status      TestimonialStatus @default(PENDING)
  featured    Boolean           @default(false)
  folio       String?           // e.g., "Folio VII, Entry 12"
  illuminated Boolean           @default(false)  // Special display treatment
  
  // Verification
  verified    Boolean           @default(false)  // Verified purchase
  orderId     String?           // Link to order for verification
  
  createdAt   DateTime          @default(now())
  updatedAt   DateTime          @updatedAt
  publishedAt DateTime?
  
  @@index([status])
  @@index([featured])
  @@index([essenceId])
  @@map("testimonials")
}

// ═══════════════════════════════════════════════════════════════════════════════
// NEWSLETTER / CORRESPONDENCE
// ═══════════════════════════════════════════════════════════════════════════════

model Subscriber {
  id              String            @id @default(cuid())
  email           String            @unique
  
  // Profile
  firstName       String?
  lastName        String?
  
  // Status
  status          SubscriberStatus  @default(ACTIVE)
  
  // Source
  source          String?           // homepage, checkout, popup, etc.
  
  // Preferences
  preferences     Json?             // { quarterly_folio: true, new_essences: true }
  
  // Tracking
  subscribedAt    DateTime          @default(now())
  confirmedAt     DateTime?         // Double opt-in confirmation
  unsubscribedAt  DateTime?
  
  // Engagement
  lastEmailAt     DateTime?
  lastOpenAt      DateTime?
  lastClickAt     DateTime?
  emailCount      Int               @default(0)
  openCount       Int               @default(0)
  clickCount      Int               @default(0)
  
  @@index([email])
  @@index([status])
  @@map("subscribers")
}

model Campaign {
  id            String          @id @default(cuid())
  
  name          String
  subject       String
  preheader     String?
  
  // Content
  contentHtml   String          @db.Text
  contentText   String?         @db.Text
  
  // Targeting
  segment       Json?           // Filter criteria for subscribers
  
  // Status
  status        CampaignStatus  @default(DRAFT)
  
  // Scheduling
  scheduledFor  DateTime?
  
  // Sending
  sentAt        DateTime?
  sentCount     Int             @default(0)
  
  // Analytics
  openCount     Int             @default(0)
  clickCount    Int             @default(0)
  bounceCount   Int             @default(0)
  unsubCount    Int             @default(0)
  
  createdAt     DateTime        @default(now())
  updatedAt     DateTime        @updatedAt
  
  @@map("campaigns")
}

// ═══════════════════════════════════════════════════════════════════════════════
// CONTENT MANAGEMENT
// ═══════════════════════════════════════════════════════════════════════════════

model PageContent {
  id            String    @id @default(cuid())
  slug          String    @unique
  
  // Content
  title         String
  content       Json      // Rich text content structure
  
  // SEO
  seoTitle      String?
  seoDescription String?
  ogImage       String?
  
  // Status
  published     Boolean   @default(false)
  
  createdAt     DateTime  @default(now())
  updatedAt     DateTime  @updatedAt
  publishedAt   DateTime?
  
  @@map("page_contents")
}

model AlchemyStep {
  id            String    @id @default(cuid())
  
  // Display
  stepNumber    Int       // 1, 2, 3, 4
  romanNumeral  String    // I, II, III, IV
  
  // Content
  latinName     String    // Nigredo, Albedo, Citrinitas, Rubedo
  englishName   String    // The Blackening, The Whitening, etc.
  description   String    @db.Text
  
  // Details
  duration      String?   // "7-14 Days"
  temperature   String?   // "40°C ±0.1"
  vessel        String?   // "Hand-blown Glass"
  
  // Display
  symbol        String?   // Alchemical symbol
  sortOrder     Int       @default(0)
  
  createdAt     DateTime  @default(now())
  updatedAt     DateTime  @updatedAt
  
  @@map("alchemy_steps")
}

// ═══════════════════════════════════════════════════════════════════════════════
// DISCOUNT CODES
// ═══════════════════════════════════════════════════════════════════════════════

model DiscountCode {
  id              String    @id @default(cuid())
  
  code            String    @unique
  description     String?
  
  // Type
  type            String    // percentage, fixed_amount, free_shipping
  value           Int       // Percentage (10 = 10%) or cents (1000 = $10)
  
  // Constraints
  minimumAmount   Int?      // Minimum order amount in cents
  maximumUses     Int?      // Total uses allowed
  usesPerCustomer Int?      @default(1)
  
  // Validity
  startsAt        DateTime  @default(now())
  expiresAt       DateTime?
  
  // Tracking
  usedCount       Int       @default(0)
  
  // Status
  active          Boolean   @default(true)
  
  createdAt       DateTime  @default(now())
  updatedAt       DateTime  @updatedAt
  
  @@index([code])
  @@map("discount_codes")
}

// ═══════════════════════════════════════════════════════════════════════════════
// AUDIT & ANALYTICS
// ═══════════════════════════════════════════════════════════════════════════════

model AuditLog {
  id          String    @id @default(cuid())
  
  // Actor
  userId      String?
  sessionId   String?
  ipAddress   String?
  userAgent   String?
  
  // Action
  action      String    // create, update, delete, login, etc.
  resource    String    // user, order, essence, etc.
  resourceId  String?
  
  // Details
  details     Json?     // Additional context
  
  createdAt   DateTime  @default(now())
  
  @@index([userId])
  @@index([action])
  @@index([resource])
  @@index([createdAt])
  @@map("audit_logs")
}
5.3 Database Indexes and Performance
SQL

-- ═══════════════════════════════════════════════════════════════════════════════
-- ADDITIONAL INDEXES FOR PERFORMANCE
-- ═══════════════════════════════════════════════════════════════════════════════

-- Full-text search on essences
CREATE INDEX idx_essences_search ON essences 
USING GIN (to_tsvector('english', name || ' ' || description));

-- Composite indexes for common queries
CREATE INDEX idx_essences_catalog ON essences (published, humour, rarity) 
WHERE published = true;

CREATE INDEX idx_orders_user_status ON orders (user_id, status, created_at DESC);

CREATE INDEX idx_cart_items_cart ON cart_items (cart_id, added_at DESC);

-- Partial index for active carts only
CREATE INDEX idx_carts_active ON carts (session_id) 
WHERE expires_at > NOW() OR user_id IS NOT NULL;

-- Index for inventory management
CREATE INDEX idx_variants_low_stock ON essence_variants (stock) 
WHERE stock < low_stock_at AND track_inventory = true;
6. API Architecture
6.1 API Design Principles
YAML

principles:
  style: "REST-inspired with Server Actions"
  versioning: "URL path (/api/v1/...) for external APIs"
  authentication: "Bearer token (Clerk) + Session cookies"
  rate_limiting: "Upstash Redis rate limiter"
  error_handling: "Consistent error response format"
  
response_format:
  success:
    data: "Requested resource(s)"
    meta: "Pagination, counts, etc."
  error:
    error:
      code: "MACHINE_READABLE_CODE"
      message: "Human readable message"
      details: "Additional error context (optional)"
6.2 API Route Structure
text

┌─────────────────────────────────────────────────────────────────────────────────────┐
│                              API ROUTE STRUCTURE                                     │
└─────────────────────────────────────────────────────────────────────────────────────┘

app/
├── api/
│   ├── v1/
│   │   ├── essences/
│   │   │   ├── route.ts              GET: List essences
│   │   │   └── [slug]/
│   │   │       └── route.ts          GET: Single essence
│   │   │
│   │   ├── cart/
│   │   │   ├── route.ts              GET: Get cart, POST: Add item
│   │   │   └── [itemId]/
│   │   │       └── route.ts          PATCH: Update qty, DELETE: Remove
│   │   │
│   │   ├── orders/
│   │   │   ├── route.ts              GET: List orders, POST: Create
│   │   │   └── [orderId]/
│   │   │       └── route.ts          GET: Single order
│   │   │
│   │   ├── checkout/
│   │   │   ├── route.ts              POST: Create checkout session
│   │   │   └── complete/
│   │   │       └── route.ts          POST: Complete order
│   │   │
│   │   ├── testimonials/
│   │   │   ├── route.ts              GET: List, POST: Create
│   │   │   └── [id]/
│   │   │       └── route.ts          GET: Single
│   │   │
│   │   └── subscribers/
│   │       └── route.ts              POST: Subscribe
│   │
│   ├── webhooks/
│   │   ├── stripe/
│   │   │   └── route.ts              Stripe webhook handler
│   │   └── clerk/
│   │       └── route.ts              Clerk webhook handler
│   │
│   └── admin/
│       └── v1/
│           ├── essences/             CRUD for admin
│           ├── orders/               Order management
│           ├── customers/            Customer management
│           └── analytics/            Dashboard data
6.3 API Endpoint Specifications
6.3.1 Essences API
TypeScript

// ═══════════════════════════════════════════════════════════════════════════════
// GET /api/v1/essences
// List essences with filtering and pagination
// ═══════════════════════════════════════════════════════════════════════════════

// Request
interface ListEssencesRequest {
  // Filtering
  humour?: Humour | Humour[];
  rarity?: Rarity | Rarity[];
  season?: Season;
  categorySlug?: string;
  featured?: boolean;
  
  // Search
  search?: string;
  
  // Sorting
  sortBy?: 'name' | 'price' | 'createdAt' | 'featured';
  sortOrder?: 'asc' | 'desc';
  
  // Pagination
  page?: number;      // Default: 1
  limit?: number;     // Default: 12, Max: 48
}

// Response
interface ListEssencesResponse {
  data: EssenceListItem[];
  meta: {
    total: number;
    page: number;
    limit: number;
    totalPages: number;
    hasMore: boolean;
  };
  filters: {
    humours: { value: Humour; count: number }[];
    rarities: { value: Rarity; count: number }[];
    priceRange: { min: number; max: number };
  };
}

interface EssenceListItem {
  id: string;
  slug: string;
  name: string;
  tagline: string;
  humour: Humour;
  rarity: Rarity;
  season: Season;
  folio: string;
  featured: boolean;
  botanical: {
    latinName: string;
    commonName: string;
  };
  defaultVariant: {
    id: string;
    price: number;
    comparePrice: number | null;
    inStock: boolean;
  };
  primaryImage: {
    url: string;
    altText: string;
  };
}

// ═══════════════════════════════════════════════════════════════════════════════
// GET /api/v1/essences/[slug]
// Get single essence with full details
// ═══════════════════════════════════════════════════════════════════════════════

interface GetEssenceResponse {
  data: EssenceDetail;
}

interface EssenceDetail extends EssenceListItem {
  description: string;
  extraction: ExtractionMethod;
  topNotes: string[];
  heartNotes: string[];
  baseNotes: string[];
  batchNumber: string | null;
  
  botanical: {
    id: string;
    latinName: string;
    commonName: string;
    family: string;
    origin: string;
    description: string;
    properties: Record<string, string[]>;
  };
  
  category: {
    id: string;
    slug: string;
    name: string;
  };
  
  variants: {
    id: string;
    sku: string;
    name: string;
    size: number;
    unit: string;
    price: number;
    comparePrice: number | null;
    inStock: boolean;
    stock: number;
    isDefault: boolean;
  }[];
  
  images: {
    id: string;
    url: string;
    altText: string;
    type: string;
    isPrimary: boolean;
  }[];
  
  testimonials: {
    id: string;
    authorName: string;
    content: string;
    rating: number;
    createdAt: string;
  }[];
  
  relatedEssences: EssenceListItem[];
}
6.3.2 Cart API
TypeScript

// ═══════════════════════════════════════════════════════════════════════════════
// GET /api/v1/cart
// Get current cart
// ═══════════════════════════════════════════════════════════════════════════════

interface GetCartResponse {
  data: Cart;
}

interface Cart {
  id: string;
  items: CartItem[];
  itemCount: number;
  subtotal: number;      // In cents
  currency: string;
  note: string | null;
  createdAt: string;
  updatedAt: string;
}

interface CartItem {
  id: string;
  quantity: number;
  unitPrice: number;
  totalPrice: number;
  addedAt: string;
  variant: {
    id: string;
    sku: string;
    name: string;
    size: number;
    unit: string;
    price: number;
    inStock: boolean;
    stock: number;
  };
  essence: {
    id: string;
    slug: string;
    name: string;
    humour: Humour;
    primaryImage: {
      url: string;
      altText: string;
    };
  };
}

// ═══════════════════════════════════════════════════════════════════════════════
// POST /api/v1/cart
// Add item to cart
// ═══════════════════════════════════════════════════════════════════════════════

interface AddToCartRequest {
  variantId: string;
  quantity: number;     // Default: 1
}

interface AddToCartResponse {
  data: Cart;
  added: CartItem;      // The item that was added
}

// ═══════════════════════════════════════════════════════════════════════════════
// PATCH /api/v1/cart/[itemId]
// Update cart item quantity
// ═══════════════════════════════════════════════════════════════════════════════

interface UpdateCartItemRequest {
  quantity: number;
}

interface UpdateCartItemResponse {
  data: Cart;
  updated: CartItem;
}

// ═══════════════════════════════════════════════════════════════════════════════
// DELETE /api/v1/cart/[itemId]
// Remove item from cart
// ═══════════════════════════════════════════════════════════════════════════════

interface RemoveCartItemResponse {
  data: Cart;
  removed: { id: string };
}
6.3.3 Checkout & Orders API
TypeScript

// ═══════════════════════════════════════════════════════════════════════════════
// POST /api/v1/checkout
// Create Stripe checkout session
// ═══════════════════════════════════════════════════════════════════════════════

interface CreateCheckoutRequest {
  shippingAddressId?: string;
  shippingMethod: string;
  discountCode?: string;
  isGift?: boolean;
  giftMessage?: string;
  giftWrap?: boolean;
  customerNote?: string;
}

interface CreateCheckoutResponse {
  data: {
    checkoutUrl: string;      // Stripe Checkout URL
    sessionId: string;        // Stripe session ID
    orderId: string;          // Pre-created order ID
  };
}

// ═══════════════════════════════════════════════════════════════════════════════
// GET /api/v1/orders
// List user's orders
// ═══════════════════════════════════════════════════════════════════════════════

interface ListOrdersRequest {
  status?: OrderStatus;
  page?: number;
  limit?: number;
}

interface ListOrdersResponse {
  data: OrderListItem[];
  meta: {
    total: number;
    page: number;
    limit: number;
    totalPages: number;
  };
}

interface OrderListItem {
  id: string;
  orderNumber: string;
  status: OrderStatus;
  paymentStatus: PaymentStatus;
  grandTotal: number;
  currency: string;
  itemCount: number;
  createdAt: string;
  dispatchedAt: string | null;
  deliveredAt: string | null;
}

// ═══════════════════════════════════════════════════════════════════════════════
// GET /api/v1/orders/[orderId]
// Get order details
// ═══════════════════════════════════════════════════════════════════════════════

interface GetOrderResponse {
  data: OrderDetail;
}

interface OrderDetail extends OrderListItem {
  email: string;
  
  shippingAddress: {
    firstName: string;
    lastName: string;
    line1: string;
    line2: string | null;
    city: string;
    state: string;
    postalCode: string;
    country: string;
  };
  
  items: {
    id: string;
    essenceName: string;
    variantName: string;
    sku: string;
    quantity: number;
    unitPrice: number;
    totalPrice: number;
    essence: {
      slug: string;
      primaryImage: { url: string };
    };
  }[];
  
  subtotal: number;
  discountTotal: number;
  shippingTotal: number;
  taxTotal: number;
  
  discountCode: string | null;
  
  shippingMethod: string;
  shippingCarrier: string | null;
  trackingNumber: string | null;
  trackingUrl: string | null;
  
  isGift: boolean;
  giftMessage: string | null;
  
  events: {
    type: string;
    description: string;
    createdAt: string;
  }[];
}
6.4 Server Actions
TypeScript

// ═══════════════════════════════════════════════════════════════════════════════
// SERVER ACTIONS - Primary mutation interface
// Located in: app/actions/
// ═══════════════════════════════════════════════════════════════════════════════

// app/actions/cart.ts
'use server';

import { revalidatePath } from 'next/cache';
import { z } from 'zod';

const AddToCartSchema = z.object({
  variantId: z.string().cuid(),
  quantity: z.number().int().min(1).max(10).default(1),
});

export async function addToCart(formData: FormData) {
  const validatedFields = AddToCartSchema.safeParse({
    variantId: formData.get('variantId'),
    quantity: Number(formData.get('quantity')) || 1,
  });

  if (!validatedFields.success) {
    return {
      success: false,
      error: {
        code: 'VALIDATION_ERROR',
        message: 'Invalid input',
        details: validatedFields.error.flatten(),
      },
    };
  }

  try {
    // Get or create cart
    const cart = await getOrCreateCart();
    
    // Validate variant exists and has stock
    const variant = await prisma.essenceVariant.findUnique({
      where: { id: validatedFields.data.variantId },
      include: { essence: true },
    });

    if (!variant || !variant.available) {
      return {
        success: false,
        error: {
          code: 'VARIANT_NOT_FOUND',
          message: 'This essence variant is not available',
        },
      };
    }

    if (variant.trackInventory && variant.stock < validatedFields.data.quantity) {
      return {
        success: false,
        error: {
          code: 'INSUFFICIENT_STOCK',
          message: `Only ${variant.stock} available`,
        },
      };
    }

    // Upsert cart item
    const cartItem = await prisma.cartItem.upsert({
      where: {
        cartId_variantId: {
          cartId: cart.id,
          variantId: variant.id,
        },
      },
      update: {
        quantity: { increment: validatedFields.data.quantity },
        unitPrice: variant.price,
      },
      create: {
        cartId: cart.id,
        variantId: variant.id,
        quantity: validatedFields.data.quantity,
        unitPrice: variant.price,
      },
    });

    revalidatePath('/cart');
    revalidatePath('/compendium');

    return {
      success: true,
      data: {
        itemId: cartItem.id,
        essenceName: variant.essence.name,
        quantity: validatedFields.data.quantity,
      },
    };
  } catch (error) {
    console.error('addToCart error:', error);
    return {
      success: false,
      error: {
        code: 'INTERNAL_ERROR',
        message: 'Failed to add item to cart',
      },
    };
  }
}

export async function updateCartItemQuantity(itemId: string, quantity: number) {
  // Implementation
}

export async function removeFromCart(itemId: string) {
  // Implementation
}

export async function clearCart() {
  // Implementation
}

// app/actions/checkout.ts
export async function createCheckoutSession(formData: FormData) {
  // Implementation with Stripe
}

// app/actions/newsletter.ts
export async function subscribeToNewsletter(formData: FormData) {
  // Implementation
}

// app/actions/testimonial.ts
export async function submitTestimonial(formData: FormData) {
  // Implementation
}
7. Frontend Architecture
7.1 Directory Structure
text

┌─────────────────────────────────────────────────────────────────────────────────────┐
│                           PROJECT DIRECTORY STRUCTURE                                │
└─────────────────────────────────────────────────────────────────────────────────────┘

atelier-arome/
├── .github/
│   └── workflows/
│       ├── ci.yml                    # Continuous integration
│       ├── deploy-preview.yml        # Preview deployments
│       └── deploy-production.yml     # Production deployment
│
├── .husky/
│   ├── pre-commit                    # Lint-staged
│   └── commit-msg                    # Commitlint
│
├── prisma/
│   ├── schema.prisma                 # Database schema
│   ├── migrations/                   # Migration files
│   └── seed.ts                       # Database seeding
│
├── public/
│   ├── fonts/                        # Self-hosted fonts (if needed)
│   ├── images/
│   │   ├── botanicals/               # Botanical illustrations
│   │   ├── products/                 # Product photography
│   │   └── patterns/                 # Decorative patterns
│   ├── icons/
│   │   └── alchemical/               # Custom SVG symbols
│   ├── favicon.ico
│   ├── apple-touch-icon.png
│   └── manifest.json
│
├── src/
│   ├── app/                          # Next.js App Router
│   │   ├── (marketing)/              # Marketing pages group
│   │   │   ├── layout.tsx            # Full header/footer layout
│   │   │   ├── page.tsx              # Homepage
│   │   │   ├── about/
│   │   │   │   └── page.tsx          # About/Atelier page
│   │   │   ├── alchemy/
│   │   │   │   └── page.tsx          # Process page
│   │   │   └── correspondence/
│   │   │       └── page.tsx          # Newsletter page
│   │   │
│   │   ├── (shop)/                   # Shop pages group
│   │   │   ├── layout.tsx            # Shop-specific layout
│   │   │   ├── compendium/           # Product catalog
│   │   │   │   ├── page.tsx          # Catalog page
│   │   │   │   └── [slug]/
│   │   │   │       └── page.tsx      # Product detail
│   │   │   ├── cart/
│   │   │   │   └── page.tsx          # Cart page
│   │   │   └── checkout/
│   │   │       ├── page.tsx          # Checkout page
│   │   │       └── success/
│   │   │           └── page.tsx      # Order confirmation
│   │   │
│   │   ├── (account)/                # Authenticated pages
│   │   │   ├── layout.tsx            # Account layout
│   │   │   ├── account/
│   │   │   │   └── page.tsx          # Account overview
│   │   │   ├── orders/
│   │   │   │   ├── page.tsx          # Order history
│   │   │   │   └── [orderId]/
│   │   │   │       └── page.tsx      # Order detail
│   │   │   ├── addresses/
│   │   │   │   └── page.tsx          # Address book
│   │   │   └── wishlist/
│   │   │       └── page.tsx          # Wishlist
│   │   │
│   │   ├── (admin)/                  # Admin dashboard
│   │   │   ├── layout.tsx            # Admin layout
│   │   │   ├── admin/
│   │   │   │   ├── page.tsx          # Dashboard
│   │   │   │   ├── essences/
│   │   │   │   ├── orders/
│   │   │   │   ├── customers/
│   │   │   │   └── settings/
│   │   │
│   │   ├── api/                      # API routes
│   │   │   ├── v1/                   # Versioned API
│   │   │   └── webhooks/             # Webhook handlers
│   │   │
│   │   ├── layout.tsx                # Root layout
│   │   ├── loading.tsx               # Global loading
│   │   ├── error.tsx                 # Global error
│   │   ├── not-found.tsx             # 404 page
│   │   └── globals.css               # Global styles
│   │
│   ├── components/                   # React components
│   │   ├── ui/                       # Shadcn/UI base components
│   │   │   ├── button.tsx
│   │   │   ├── dialog.tsx
│   │   │   ├── dropdown-menu.tsx
│   │   │   ├── form.tsx
│   │   │   ├── input.tsx
│   │   │   ├── select.tsx
│   │   │   ├── toast.tsx
│   │   │   └── ... (40+ components)
│   │   │
│   │   ├── manuscript/               # Manuscript-themed wrappers
│   │   │   ├── manuscript-button.tsx
│   │   │   ├── manuscript-card.tsx
│   │   │   ├── manuscript-dialog.tsx
│   │   │   ├── illuminated-initial.tsx
│   │   │   ├── gold-border.tsx
│   │   │   ├── parchment-texture.tsx
│   │   │   └── wax-seal.tsx
│   │   │
│   │   ├── layout/                   # Layout components
│   │   │   ├── header/
│   │   │   │   ├── header.tsx
│   │   │   │   ├── atelier-seal.tsx
│   │   │   │   ├── nav-link.tsx
│   │   │   │   ├── mobile-nav.tsx
│   │   │   │   └── cart-button.tsx
│   │   │   ├── footer/
│   │   │   │   ├── colophon.tsx
│   │   │   │   └── footer-nav.tsx
│   │   │   └── sidebar/
│   │   │       └── admin-sidebar.tsx
│   │   │
│   │   ├── sections/                 # Page sections
│   │   │   ├── hero/
│   │   │   │   ├── hero.tsx
│   │   │   │   ├── hero-vessel.tsx
│   │   │   │   └── hero-botanicals.tsx
│   │   │   ├── compendium/
│   │   │   │   ├── compendium-grid.tsx
│   │   │   │   ├── essence-card.tsx
│   │   │   │   ├── essence-filters.tsx
│   │   │   │   └── essence-sort.tsx
│   │   │   ├── alchemy/
│   │   │   │   ├── alchemy-process.tsx
│   │   │   │   └── alchemy-step.tsx
│   │   │   ├── manuscript/
│   │   │   │   ├── testimonial-grid.tsx
│   │   │   │   └── testimonial-entry.tsx
│   │   │   └── correspondence/
│   │   │       └── newsletter-form.tsx
│   │   │
│   │   ├── cart/                     # Cart components
│   │   │   ├── cart-drawer.tsx
│   │   │   ├── cart-item.tsx
│   │   │   ├── cart-summary.tsx
│   │   │   └── add-to-cart-button.tsx
│   │   │
│   │   ├── checkout/                 # Checkout components
│   │   │   ├── checkout-form.tsx
│   │   │   ├── shipping-form.tsx
│   │   │   ├── order-summary.tsx
│   │   │   └── payment-form.tsx
│   │   │
│   │   ├── product/                  # Product components
│   │   │   ├── product-gallery.tsx
│   │   │   ├── product-info.tsx
│   │   │   ├── variant-selector.tsx
│   │   │   └── related-products.tsx
│   │   │
│   │   ├── account/                  # Account components
│   │   │   ├── order-list.tsx
│   │   │   ├── order-detail.tsx
│   │   │   └── address-form.tsx
│   │   │
│   │   ├── admin/                    # Admin components
│   │   │   ├── dashboard/
│   │   │   ├── essence-editor/
│   │   │   └── order-manager/
│   │   │
│   │   └── shared/                   # Shared components
│   │       ├── loading-spinner.tsx
│   │       ├── error-boundary.tsx
│   │       ├── seo.tsx
│   │       ├── price.tsx
│   │       └── image.tsx
│   │
│   ├── hooks/                        # Custom hooks
│   │   ├── use-cart.ts
│   │   ├── use-wishlist.ts
│   │   ├── use-media-query.ts
│   │   ├── use-scroll.ts
│   │   ├── use-reduced-motion.ts
│   │   └── use-toast.ts
│   │
│   ├── lib/                          # Utility libraries
│   │   ├── prisma.ts                 # Prisma client
│   │   ├── stripe.ts                 # Stripe config
│   │   ├── resend.ts                 # Email client
│   │   ├── redis.ts                  # Redis client
│   │   ├── auth.ts                   # Auth utilities
│   │   ├── utils.ts                  # General utilities
│   │   └── constants.ts              # App constants
│   │
│   ├── services/                     # Business logic services
│   │   ├── cart.service.ts
│   │   ├── order.service.ts
│   │   ├── product.service.ts
│   │   ├── payment.service.ts
│   │   ├── email.service.ts
│   │   └── analytics.service.ts
│   │
│   ├── actions/                      # Server actions
│   │   ├── 
