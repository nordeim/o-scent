Implementation Plan: Project Architecture Document (PAD)
Pre-Execution Analysis
Objective
Create a comprehensive, single-source-of-truth Project Architecture Document that enables any developer or AI coding agent to independently develop the complete Atelier Arôme e-commerce platform without ambiguity or deviation.

Document Scope
The PAD must cover:

Project vision and business context
Technical architecture decisions with rationale
Complete database schema with ERD
Full API specification
Frontend component architecture
Design system tokens and patterns
File/folder structure
Development workflow and standards
Security and performance requirements
Deployment architecture
Implementation phases with dependencies
Validation Criteria
Before execution, the plan must satisfy:

 Complete enough for greenfield development
 No ambiguous terminology or undefined references
 All relationships and dependencies explicitly stated
 Database schema supports all described features
 API endpoints cover all user stories
 Component hierarchy matches page requirements
 Design tokens match existing CSS implementation
Implementation Plan for PAD
Phase 1: Vision & Context (Sections 1-2)
Project overview and business goals
Target audience definition
Success metrics
Constraints and assumptions
Phase 2: Technical Foundation (Sections 3-5)
Technology stack with justification
System architecture diagrams
Database schema with complete ERD
Prisma schema definition
Phase 3: API Layer (Section 6)
RESTful API specification
Authentication flows
Request/response schemas
Error handling patterns
Phase 4: Frontend Architecture (Sections 7-9)
Component hierarchy
State management patterns
Routing structure
Design system tokens
Phase 5: Infrastructure (Sections 10-12)
Development workflow
Deployment architecture
Security requirements
Performance budgets
Phase 6: Implementation Roadmap (Section 13)
Phased delivery plan
Dependencies and milestones
Testing strategy
Execution: Project Architecture Document
📜 ATELIER ARÔME
Project Architecture Document (PAD)
Version 1.0.0 | Single Source of Truth
Table of Contents
Project Overview
Business Context
Technology Stack
System Architecture
Database Design
API Specification
Frontend Architecture
Design System
Component Library
Development Standards
Security Architecture
Infrastructure & Deployment
Implementation Roadmap
1. Project Overview
1.1 Executive Summary
Atelier Arôme is a luxury e-commerce platform for artisanal aromatherapy products, designed as a digital illuminated manuscript experience. The platform combines Renaissance aesthetic principles with modern e-commerce functionality, positioning the brand as a premium purveyor of handcrafted botanical essences.

1.2 Project Vision
"To create a digital experience that honors the craft of artisanal perfumery—where every interaction feels as intentional as the 72-hour distillation process that creates our essences."

1.3 Core Objectives
Objective	Success Metric	Priority
Immersive Brand Experience	Time on site > 4 minutes	P0
E-commerce Conversion	Conversion rate > 2.5%	P0
Accessibility Compliance	WCAG 2.2 AA (AAA where feasible)	P0
Performance Excellence	Core Web Vitals all "Good"	P0
Mobile Experience	Mobile conversion parity ±10%	P1
SEO Visibility	Organic traffic +50% YoY	P1
1.4 Target Users
Primary Persona: "The Connoisseur"
Demographics: 35-55, HHI $100K+, urban/suburban
Psychographics: Values craftsmanship, authenticity, ritual
Behavior: Research-intensive, brand-loyal, willing to pay premium
Goals: Find unique, high-quality aromatherapy products
Frustrations: Generic products, mass-market experiences
Secondary Persona: "The Gift Giver"
Demographics: 28-45, HHI $75K+
Psychographics: Thoughtful, appreciates presentation
Behavior: Seasonal purchaser, discovery-driven
Goals: Find memorable, beautifully presented gifts
Frustrations: Impersonal gift options
Tertiary Persona: "The Wellness Seeker"
Demographics: 25-40, health-conscious
Psychographics: Holistic wellness focused
Behavior: Needs-based purchasing, ingredient-conscious
Goals: Find natural, effective aromatherapy solutions
Frustrations: Unclear ingredient sourcing, synthetic alternatives
1.5 Key Features
text

┌─────────────────────────────────────────────────────────────────┐
│                    ATELIER ARÔME FEATURES                       │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐ │
│  │   COMPENDIUM    │  │    ALCHEMY      │  │   MANUSCRIPT    │ │
│  │   (Catalog)     │  │   (Process)     │  │ (Testimonials)  │ │
│  │                 │  │                 │  │                 │ │
│  │ • Product Grid  │  │ • Process Story │  │ • Patron Reviews│ │
│  │ • Filtering     │  │ • 4-Stage Flow  │  │ • Illuminated   │ │
│  │ • Sorting       │  │ • Animation     │  │   Entries       │ │
│  │ • Quick Add     │  │                 │  │                 │ │
│  └─────────────────┘  └─────────────────┘  └─────────────────┘ │
│                                                                 │
│  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐ │
│  │  VIAL (Cart)    │  │   CHECKOUT      │  │   ACCOUNT       │ │
│  │                 │  │                 │  │                 │ │
│  │ • Drawer UI     │  │ • Guest/Auth    │  │ • Order History │ │
│  │ • Quantity      │  │ • Stripe        │  │ • Addresses     │ │
│  │ • Persistence   │  │ • Order Confirm │  │ • Wishlist      │ │
│  │ • Animations    │  │                 │  │ • Settings      │ │
│  └─────────────────┘  └─────────────────┘  └─────────────────┘ │
│                                                                 │
│  ┌─────────────────────────────────────────────────────────────┐│
│  │                      ADMIN ATELIER                          ││
│  │                                                             ││
│  │  Dashboard │ Products │ Orders │ Customers │ Analytics     ││
│  │  Inventory │ Testimonials │ Newsletter │ Settings          ││
│  └─────────────────────────────────────────────────────────────┘│
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
2. Business Context
2.1 Product Catalog Structure
Categories (Humours)
Humour	Symbol	Color	Description
Calming	☾	#B8A9C9	Essences for relaxation and sleep
Uplifting	☀	#F5D489	Essences for energy and mood
Grounding	♁	#7C6354	Essences for stability and focus
Clarifying	☁	#7CB9A0	Essences for mental clarity
Product Attributes
Attribute	Type	Example Values
Rarity	Enum	Common, Rare, Limited
Season	Enum	Spring, Summer, Autumn, Winter
Extraction	String	Steam Distillation, Cold Press, Enfleurage
Origin	String	Provence, France
Scent Notes	Array	['Floral', 'Herbaceous', 'Sweet']
Product Variants (Phial Sizes)
Size	Price Range	Weight
5ml Phial	$36-48	25g
15ml Phial	$78-98	45g
30ml Vessel	$145-180	85g
2.2 Order Workflow
text

┌──────────┐    ┌──────────┐    ┌──────────┐    ┌──────────┐    ┌──────────┐
│ PENDING  │───▶│CONFIRMED │───▶│PROCESSING│───▶│ SHIPPED  │───▶│DELIVERED │
└──────────┘    └──────────┘    └──────────┘    └──────────┘    └──────────┘
     │                                               │
     │                                               ▼
     │                                         ┌──────────┐
     └────────────────────────────────────────▶│CANCELLED │
                                               └──────────┘

States:
- PENDING: Order created, awaiting payment confirmation
- CONFIRMED: Payment received, order accepted
- PROCESSING: Being prepared in the atelier
- SHIPPED: Dispatched with tracking number
- DELIVERED: Confirmed delivery
- CANCELLED: Order cancelled (before shipping only)
2.3 Business Rules
Pricing Rules
All prices in USD, tax-exclusive
Tax calculated at checkout based on shipping address
Free shipping on orders > $150
Inventory Rules
Low stock threshold: 10 units
Out of stock: Hide variant, show "Notify Me"
Limited edition: Max 100 units ever produced
Order Rules
Minimum order: 1 item
Maximum cart items: 12 unique variants
Guest checkout allowed
Order modifications: Only before "Processing" status
3. Technology Stack
3.1 Stack Overview
text

┌─────────────────────────────────────────────────────────────────┐
│                        CLIENT LAYER                             │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │                    Next.js 14+                           │   │
│  │                    (App Router)                          │   │
│  │  ┌─────────────┐  ┌─────────────┐  ┌─────────────────┐  │   │
│  │  │   React 18  │  │ TypeScript  │  │ Tailwind CSS 4  │  │   │
│  │  │    (RSC)    │  │    5.3+     │  │   + Shadcn-UI   │  │   │
│  │  └─────────────┘  └─────────────┘  └─────────────────┘  │   │
│  └─────────────────────────────────────────────────────────┘   │
├─────────────────────────────────────────────────────────────────┤
│                        STATE LAYER                              │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────────────────┐ │
│  │   Zustand   │  │ React Query │  │    React Hook Form      │ │
│  │(Client State)│  │(Server State)│ │    + Zod Validation     │ │
│  └─────────────┘  └─────────────┘  └─────────────────────────┘ │
├─────────────────────────────────────────────────────────────────┤
│                         API LAYER                               │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │               Next.js API Routes (Route Handlers)        │   │
│  │  ┌─────────────┐  ┌─────────────┐  ┌─────────────────┐  │   │
│  │  │ NextAuth.js │  │   tRPC      │  │  Stripe SDK     │  │   │
│  │  │    v5       │  │  (Optional) │  │                 │  │   │
│  │  └─────────────┘  └─────────────┘  └─────────────────┘  │   │
│  └─────────────────────────────────────────────────────────┘   │
├─────────────────────────────────────────────────────────────────┤
│                        DATA LAYER                               │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │                      Prisma ORM                          │   │
│  │  ┌─────────────────────────────────────────────────┐    │   │
│  │  │              PostgreSQL 15+                      │    │   │
│  │  │         (Neon / Supabase / Railway)              │    │   │
│  │  └─────────────────────────────────────────────────┘    │   │
│  └─────────────────────────────────────────────────────────┘   │
├─────────────────────────────────────────────────────────────────┤
│                     INFRASTRUCTURE                              │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────────────────┐ │
│  │   Vercel    │  │  Resend     │  │   Uploadthing / S3      │ │
│  │  (Hosting)  │  │  (Email)    │  │   (File Storage)        │ │
│  └─────────────┘  └─────────────┘  └─────────────────────────┘ │
└─────────────────────────────────────────────────────────────────┘
3.2 Technology Decisions & Rationale
Frontend Framework: Next.js 14+ (App Router)
Criteria	Decision Rationale
SSR/SSG	Product pages need SEO; App Router provides hybrid rendering
Performance	React Server Components reduce client bundle
DX	File-based routing, built-in API routes
Ecosystem	First-class Vercel deployment, excellent TypeScript support
Shadcn-UI	Built specifically for Next.js + Tailwind
Database: PostgreSQL + Prisma
Criteria	Decision Rationale
Relational	Complex product/order/user relationships
JSON Support	Flexible product attributes, cart data
Prisma	Type-safe queries, migrations, excellent DX
Hosting	Neon (serverless) or Supabase (managed)
State Management: Zustand + React Query
Concern	Solution	Rationale
Client State	Zustand	Lightweight, no boilerplate, TypeScript-first
Server State	React Query	Caching, refetching, mutations, optimistic updates
Forms	React Hook Form	Performance, validation, accessibility
Authentication: NextAuth.js v5
Feature	Implementation
Providers	Email/Password, Google, Apple
Session	JWT (for serverless) or Database
RBAC	Custom middleware for admin routes
Payments: Stripe
Feature	Implementation
Checkout	Stripe Checkout (hosted)
Webhooks	Order fulfillment on payment success
Subscriptions	Future: Quarterly essence subscription
3.3 Package Dependencies
JSON

{
  "dependencies": {
    "next": "^14.2.0",
    "react": "^18.3.0",
    "react-dom": "^18.3.0",
    "typescript": "^5.4.0",
    
    "tailwindcss": "^4.0.0",
    "@radix-ui/react-*": "latest",
    "class-variance-authority": "^0.7.0",
    "clsx": "^2.1.0",
    "tailwind-merge": "^2.3.0",
    "lucide-react": "^0.378.0",
    
    "@prisma/client": "^5.14.0",
    "next-auth": "^5.0.0-beta.18",
    "@tanstack/react-query": "^5.37.0",
    "zustand": "^4.5.0",
    "react-hook-form": "^7.51.0",
    "@hookform/resolvers": "^3.4.0",
    "zod": "^3.23.0",
    
    "stripe": "^15.5.0",
    "@stripe/stripe-js": "^3.4.0",
    "resend": "^3.2.0",
    
    "framer-motion": "^11.2.0",
    "embla-carousel-react": "^8.1.0",
    "sonner": "^1.4.0"
  },
  "devDependencies": {
    "prisma": "^5.14.0",
    "@types/node": "^20.12.0",
    "@types/react": "^18.3.0",
    "eslint": "^8.57.0",
    "eslint-config-next": "^14.2.0",
    "prettier": "^3.2.0",
    "prettier-plugin-tailwindcss": "^0.5.0"
  }
}
4. System Architecture
4.1 High-Level Architecture
text

                                    ┌─────────────────┐
                                    │    CDN Edge     │
                                    │    (Vercel)     │
                                    └────────┬────────┘
                                             │
                    ┌────────────────────────┼────────────────────────┐
                    │                        │                        │
                    ▼                        ▼                        ▼
           ┌───────────────┐        ┌───────────────┐        ┌───────────────┐
           │  Static Pages │        │   SSR Pages   │        │   API Routes  │
           │    (ISR)      │        │   (Dynamic)   │        │  (Serverless) │
           │               │        │               │        │               │
           │ • Homepage    │        │ • Cart        │        │ • /api/cart   │
           │ • Products    │        │ • Checkout    │        │ • /api/orders │
           │ • About       │        │ • Account     │        │ • /api/auth   │
           └───────────────┘        └───────────────┘        └───────┬───────┘
                                                                     │
                    ┌────────────────────────────────────────────────┘
                    │
                    ▼
           ┌───────────────────────────────────────────────────────────────┐
           │                         DATA LAYER                            │
           │  ┌─────────────┐  ┌─────────────┐  ┌─────────────────────┐   │
           │  │   Prisma    │  │   Redis     │  │   File Storage      │   │
           │  │   (ORM)     │  │  (Sessions) │  │   (Uploadthing)     │   │
           │  └──────┬──────┘  └──────┬──────┘  └─────────────────────┘   │
           │         │                │                                    │
           │         ▼                ▼                                    │
           │  ┌─────────────────────────────┐                             │
           │  │       PostgreSQL 15          │                             │
           │  │         (Neon)               │                             │
           │  └─────────────────────────────┘                             │
           └───────────────────────────────────────────────────────────────┘
                                             │
                    ┌────────────────────────┼────────────────────────┐
                    │                        │                        │
                    ▼                        ▼                        ▼
           ┌───────────────┐        ┌───────────────┐        ┌───────────────┐
           │    Stripe     │        │    Resend     │        │   Analytics   │
           │  (Payments)   │        │   (Email)     │        │  (Posthog)    │
           └───────────────┘        └───────────────┘        └───────────────┘
4.2 Request Flow Diagrams
Product Page Load (ISR)
text

┌──────────┐     ┌──────────┐     ┌──────────┐     ┌──────────┐
│  Browser │────▶│   Edge   │────▶│  Origin  │────▶│ Database │
└──────────┘     └──────────┘     └──────────┘     └──────────┘
     │                │                │                │
     │   Request      │                │                │
     │───────────────▶│                │                │
     │                │  Cache HIT?    │                │
     │                │────────────────│                │
     │                │      YES       │                │
     │◀───────────────│                │                │
     │   Cached HTML  │                │                │
     │                │                │                │
     │                │      NO        │                │
     │                │───────────────▶│                │
     │                │                │  Fetch Data   │
     │                │                │───────────────▶│
     │                │                │◀───────────────│
     │                │                │  Render SSR   │
     │                │◀───────────────│                │
     │◀───────────────│  Cache + Serve │                │
     │   Fresh HTML   │                │                │
Add to Cart Flow
text

┌──────────┐     ┌──────────┐     ┌──────────┐     ┌──────────┐
│  Client  │     │  Zustand │     │   API    │     │ Database │
└──────────┘     └──────────┘     └──────────┘     └──────────┘
     │                │                │                │
     │ Click "Add"    │                │                │
     │───────────────▶│                │                │
     │                │ Optimistic     │                │
     │                │ Update UI      │                │
     │◀───────────────│                │                │
     │ Show Toast     │                │                │
     │                │                │                │
     │                │ POST /api/cart │                │
     │                │───────────────▶│                │
     │                │                │  Upsert Cart  │
     │                │                │───────────────▶│
     │                │                │◀───────────────│
     │                │◀───────────────│  Cart Updated │
     │                │ Sync State     │                │
     │◀───────────────│                │                │
     │ Update Badge   │                │                │
Checkout Flow
text

┌──────────┐     ┌──────────┐     ┌──────────┐     ┌──────────┐
│  Client  │     │   API    │     │  Stripe  │     │ Database │
└──────────┘     └──────────┘     └──────────┘     └──────────┘
     │                │                │                │
     │ Click Checkout │                │                │
     │───────────────▶│                │                │
     │                │ Create Session │                │
     │                │───────────────▶│                │
     │                │◀───────────────│                │
     │◀───────────────│ Session URL    │                │
     │                │                │                │
     │ Redirect ─────────────────────▶ │                │
     │               Stripe Checkout   │                │
     │                                 │                │
     │ ◀───────────── Payment Complete │                │
     │                                 │                │
     │                │◀─── Webhook ───│                │
     │                │                │                │
     │                │  Create Order  │                │
     │                │───────────────────────────────▶ │
     │                │◀───────────────────────────────│
     │                │  Send Email    │                │
     │◀───────────────│                │                │
     │ Success Page   │                │                │
4.3 Caching Strategy
Resource	Cache Strategy	TTL	Invalidation
Product List	ISR	60s	On-demand revalidation
Product Detail	ISR	60s	On product update
Categories	Static	Build	Rebuild on change
Cart	No cache	-	Real-time
User Data	No cache	-	Session-based
Static Assets	Immutable	1 year	Content hash
5. Database Design
5.1 Entity Relationship Diagram
text

┌─────────────────────────────────────────────────────────────────────────────┐
│                           ENTITY RELATIONSHIP DIAGRAM                        │
└─────────────────────────────────────────────────────────────────────────────┘

                                    ┌──────────────┐
                                    │    User      │
                                    ├──────────────┤
                           ┌────────│ id           │────────┐
                           │        │ email        │        │
                           │        │ passwordHash │        │
                           │        │ firstName    │        │
                           │        │ lastName     │        │
                           │        │ ...          │        │
                           │        └──────────────┘        │
                           │               │                │
                           │               │ 1:N            │
                           │               ▼                │
          ┌────────────────┴───┐    ┌──────────────┐   ┌───┴────────────────┐
          │      Address       │    │    Order     │   │     Wishlist       │
          ├────────────────────┤    ├──────────────┤   ├────────────────────┤
          │ id                 │    │ id           │   │ id                 │
          │ userId        FK───┼────│ userId    FK─┼───│ userId        FK───┤
          │ type (ship/bill)   │    │ orderNumber  │   │ productId     FK───┼───┐
          │ addressLine1       │    │ status       │   │ createdAt          │   │
          │ city               │    │ total        │   └────────────────────┘   │
          │ ...                │    │ ...          │                            │
          └────────────────────┘    └──────┬───────┘                            │
                                           │                                     │
                                           │ 1:N                                 │
                                           ▼                                     │
                                    ┌──────────────┐                            │
                                    │  OrderItem   │                            │
                                    ├──────────────┤                            │
                                    │ id           │                            │
                                    │ orderId   FK─┼─┐                          │
                                    │ variantId FK─┼─┼──────────┐               │
                                    │ quantity     │ │          │               │
                                    │ unitPrice    │ │          │               │
                                    └──────────────┘ │          │               │
                                                     │          │               │
┌──────────────┐                                     │          │               │
│   Category   │                                     │          ▼               │
├──────────────┤                                     │  ┌──────────────────┐    │
│ id           │                                     │  │ ProductVariant   │    │
│ name         │                                     │  ├──────────────────┤    │
│ slug         │───┐                                 │  │ id               │    │
│ symbol       │   │                                 │  │ productId   FK───┼────┼───┐
│ color        │   │                                 │  │ name             │    │   │
└──────────────┘   │ 1:N                             │  │ sizeMl           │    │   │
                   │                                 │  │ price            │    │   │
                   │     ┌──────────────┐            │  │ sku              │    │   │
                   │     │   Product    │            │  └────────┬─────────┘    │   │
                   │     ├──────────────┤            │           │              │   │
                   └────▶│ id           │◀───────────┼───────────┼──────────────┘   │
                         │ categoryId FK│            │           │ 1:1              │
                         │ latinName    │◀───────────┼───────────┼──────────────────┘
                         │ commonName   │            │           ▼
                         │ slug         │            │   ┌──────────────┐
                         │ rarity       │            │   │  Inventory   │
                         │ season       │            │   ├──────────────┤
                         │ ...          │            │   │ id           │
                         └──────┬───────┘            │   │ variantId FK─┤
                                │                    │   │ quantity     │
                                │ 1:N                │   │ lowThreshold │
                                ▼                    │   └──────────────┘
                         ┌──────────────┐            │
                         │ ProductImage │            │
                         ├──────────────┤            │
                         │ id           │            │
                         │ productId FK─┤            │
                         │ url          │            │
                         │ altText      │            │
                         │ isPrimary    │            │
                         └──────────────┘            │
                                                     │
┌──────────────┐    ┌──────────────┐                │
│    Cart      │    │  CartItem    │                │
├──────────────┤    ├──────────────┤                │
│ id           │───▶│ id           │                │
│ userId    FK │    │ cartId    FK─┤                │
│ sessionId    │    │ variantId FK─┼────────────────┘
│ expiresAt    │    │ quantity     │
└──────────────┘    └──────────────┘


┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│ Testimonial  │    │  Newsletter  │    │  AdminUser   │
├──────────────┤    ├──────────────┤    ├──────────────┤
│ id           │    │ id           │    │ id           │
│ authorName   │    │ email        │    │ email        │
│ quote        │    │ firstName    │    │ role         │
│ isIlluminated│    │ subscribedAt │    │ lastLoginAt  │
│ productId FK │    │ confirmedAt  │    │ ...          │
│ ...          │    │ ...          │    └──────────────┘
└──────────────┘    └──────────────┘
5.2 Complete Prisma Schema
prisma

// prisma/schema.prisma

generator client {
  provider = "prisma-client-js"
}

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

// ============================================
// ENUMS
// ============================================

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

enum OrderStatus {
  PENDING
  CONFIRMED
  PROCESSING
  SHIPPED
  DELIVERED
  CANCELLED
}

enum AddressType {
  SHIPPING
  BILLING
}

enum AdminRole {
  SUPER_ADMIN
  ADMIN
  EDITOR
}

// ============================================
// USER & AUTH
// ============================================

model User {
  id              String    @id @default(cuid())
  email           String    @unique
  emailVerifiedAt DateTime? @map("email_verified_at")
  passwordHash    String?   @map("password_hash")
  firstName       String?   @map("first_name")
  lastName        String?   @map("last_name")
  phone           String?
  avatarUrl       String?   @map("avatar_url")
  
  // Relations
  addresses       Address[]
  orders          Order[]
  wishlists       Wishlist[]
  carts           Cart[]
  accounts        Account[]
  sessions        Session[]
  
  createdAt       DateTime  @default(now()) @map("created_at")
  updatedAt       DateTime  @updatedAt @map("updated_at")
  
  @@map("users")
}

model Account {
  id                String  @id @default(cuid())
  userId            String  @map("user_id")
  type              String
  provider          String
  providerAccountId String  @map("provider_account_id")
  refresh_token     String? @db.Text
  access_token      String? @db.Text
  expires_at        Int?
  token_type        String?
  scope             String?
  id_token          String? @db.Text
  session_state     String?
  
  user User @relation(fields: [userId], references: [id], onDelete: Cascade)
  
  @@unique([provider, providerAccountId])
  @@map("accounts")
}

model Session {
  id           String   @id @default(cuid())
  sessionToken String   @unique @map("session_token")
  userId       String   @map("user_id")
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
  id           String      @id @default(cuid())
  userId       String      @map("user_id")
  type         AddressType
  isDefault    Boolean     @default(false) @map("is_default")
  firstName    String      @map("first_name")
  lastName     String      @map("last_name")
  company      String?
  addressLine1 String      @map("address_line_1")
  addressLine2 String?     @map("address_line_2")
  city         String
  state        String?
  postalCode   String      @map("postal_code")
  country      String      @default("US")
  phone        String?
  
  user              User    @relation(fields: [userId], references: [id], onDelete: Cascade)
  shippingOrders    Order[] @relation("ShippingAddress")
  billingOrders     Order[] @relation("BillingAddress")
  
  createdAt    DateTime @default(now()) @map("created_at")
  updatedAt    DateTime @updatedAt @map("updated_at")
  
  @@map("addresses")
}

// ============================================
// PRODUCT CATALOG
// ============================================

model Category {
  id          String    @id @default(cuid())
  name        String    @unique
  slug        String    @unique
  symbol      String    // ☾, ☀, ♁, ☁
  description String?   @db.Text
  color       String    // Hex color
  sortOrder   Int       @default(0) @map("sort_order")
  isActive    Boolean   @default(true) @map("is_active")
  
  products    Product[]
  
  createdAt   DateTime  @default(now()) @map("created_at")
  updatedAt   DateTime  @updatedAt @map("updated_at")
  
  @@map("categories")
}

model Product {
  id               String   @id @default(cuid())
  sku              String   @unique
  folioNumber      String   @map("folio_number") // I, II, III, IV...
  latinName        String   @map("latin_name")
  commonName       String   @map("common_name")
  slug             String   @unique
  description      String   @db.Text
  shortDescription String?  @map("short_description")
  categoryId       String   @map("category_id")
  rarity           Rarity   @default(COMMON)
  season           Season
  extractionMethod String   @map("extraction_method")
  originLocation   String   @map("origin_location")
  originCountry    String   @map("origin_country")
  scentNotes       String[] @map("scent_notes") // Array of strings
  featured         Boolean  @default(false)
  isActive         Boolean  @default(true) @map("is_active")
  metaTitle        String?  @map("meta_title")
  metaDescription  String?  @map("meta_description")
  
  category         Category          @relation(fields: [categoryId], references: [id])
  variants         ProductVariant[]
  images           ProductImage[]
  testimonials     Testimonial[]
  wishlists        Wishlist[]
  
  createdAt        DateTime @default(now()) @map("created_at")
  updatedAt        DateTime @updatedAt @map("updated_at")
  
  @@index([categoryId])
  @@index([slug])
  @@index([isActive, featured])
  @@map("products")
}

model ProductVariant {
  id             String   @id @default(cuid())
  productId      String   @map("product_id")
  name           String   // "5ml Phial", "15ml Phial", "30ml Vessel"
  sizeMl         Int      @map("size_ml")
  price          Decimal  @db.Decimal(10, 2)
  compareAtPrice Decimal? @map("compare_at_price") @db.Decimal(10, 2)
  sku            String   @unique
  weightGrams    Int      @map("weight_grams")
  isActive       Boolean  @default(true) @map("is_active")
  
  product        Product     @relation(fields: [productId], references: [id], onDelete: Cascade)
  inventory      Inventory?
  cartItems      CartItem[]
  orderItems     OrderItem[]
  
  createdAt      DateTime @default(now()) @map("created_at")
  updatedAt      DateTime @updatedAt @map("updated_at")
  
  @@index([productId])
  @@map("product_variants")
}

model Inventory {
  id                String   @id @default(cuid())
  variantId         String   @unique @map("variant_id")
  quantity          Int      @default(0)
  lowStockThreshold Int      @default(10) @map("low_stock_threshold")
  
  variant           ProductVariant @relation(fields: [variantId], references: [id], onDelete: Cascade)
  
  updatedAt         DateTime @updatedAt @map("updated_at")
  
  @@map("inventory")
}

model ProductImage {
  id        String   @id @default(cuid())
  productId String   @map("product_id")
  url       String
  altText   String?  @map("alt_text")
  sortOrder Int      @default(0) @map("sort_order")
  isPrimary Boolean  @default(false) @map("is_primary")
  
  product   Product  @relation(fields: [productId], references: [id], onDelete: Cascade)
  
  createdAt DateTime @default(now()) @map("created_at")
  
  @@index([productId])
  @@map("product_images")
}

// ============================================
// CART
// ============================================

model Cart {
  id        String    @id @default(cuid())
  userId    String?   @map("user_id")
  sessionId String?   @map("session_id")
  expiresAt DateTime  @map("expires_at")
  
  user      User?     @relation(fields: [userId], references: [id], onDelete: Cascade)
  items     CartItem[]
  
  createdAt DateTime  @default(now()) @map("created_at")
  updatedAt DateTime  @updatedAt @map("updated_at")
  
  @@index([userId])
  @@index([sessionId])
  @@index([expiresAt])
  @@map("carts")
}

model CartItem {
  id        String   @id @default(cuid())
  cartId    String   @map("cart_id")
  variantId String   @map("variant_id")
  quantity  Int      @default(1)
  
  cart      Cart           @relation(fields: [cartId], references: [id], onDelete: Cascade)
  variant   ProductVariant @relation(fields: [variantId], references: [id])
  
  createdAt DateTime @default(now()) @map("created_at")
  updatedAt DateTime @updatedAt @map("updated_at")
  
  @@unique([cartId, variantId])
  @@map("cart_items")
}

// ============================================
// ORDERS
// ============================================

model Order {
  id                    String      @id @default(cuid())
  orderNumber           String      @unique @map("order_number")
  userId                String?     @map("user_id")
  email                 String
  status                OrderStatus @default(PENDING)
  subtotal              Decimal     @db.Decimal(10, 2)
  shippingCost          Decimal     @map("shipping_cost") @db.Decimal(10, 2)
  tax                   Decimal     @db.Decimal(10, 2)
  total                 Decimal     @db.Decimal(10, 2)
  currency              String      @default("USD")
  shippingAddressId     String?     @map("shipping_address_id")
  billingAddressId      String?     @map("billing_address_id")
  shippingMethod        String?     @map("shipping_method")
  trackingNumber        String?     @map("tracking_number")
  notes                 String?     @db.Text
  stripePaymentIntentId String?     @map("stripe_payment_intent_id")
  
  user                  User?       @relation(fields: [userId], references: [id])
  shippingAddress       Address?    @relation("ShippingAddress", fields: [shippingAddressId], references: [id])
  billingAddress        Address?    @relation("BillingAddress", fields: [billingAddressId], references: [id])
  items                 OrderItem[]
  
  paidAt                DateTime?   @map("paid_at")
  shippedAt             DateTime?   @map("shipped_at")
  deliveredAt           DateTime?   @map("delivered_at")
  cancelledAt           DateTime?   @map("cancelled_at")
  createdAt             DateTime    @default(now()) @map("created_at")
  updatedAt             DateTime    @updatedAt @map("updated_at")
  
  @@index([userId])
  @@index([status])
  @@index([orderNumber])
  @@map("orders")
}

model OrderItem {
  id          String   @id @default(cuid())
  orderId     String   @map("order_id")
  variantId   String   @map("variant_id")
  productName String   @map("product_name") // Denormalized
  variantName String   @map("variant_name") // Denormalized
  sku         String                        // Denormalized
  quantity    Int
  unitPrice   Decimal  @map("unit_price") @db.Decimal(10, 2)
  totalPrice  Decimal  @map("total_price") @db.Decimal(10, 2)
  
  order       Order          @relation(fields: [orderId], references: [id], onDelete: Cascade)
  variant     ProductVariant @relation(fields: [variantId], references: [id])
  
  createdAt   DateTime @default(now()) @map("created_at")
  
  @@index([orderId])
  @@map("order_items")
}

// ============================================
// WISHLIST
// ============================================

model Wishlist {
  id        String   @id @default(cuid())
  userId    String   @map("user_id")
  productId String   @map("product_id")
  
  user      User     @relation(fields: [userId], references: [id], onDelete: Cascade)
  product   Product  @relation(fields: [productId], references: [id], onDelete: Cascade)
  
  createdAt DateTime @default(now()) @map("created_at")
  
  @@unique([userId, productId])
  @@map("wishlists")
}

// ============================================
// TESTIMONIALS
// ============================================

model Testimonial {
  id             String   @id @default(cuid())
  authorName     String   @map("author_name")
  authorTitle    String?  @map("author_title")
  authorLocation String?  @map("author_location")
  quote          String   @db.Text
  rating         Int?     @default(5)
  isIlluminated  Boolean  @default(false) @map("is_illuminated")
  isVerified     Boolean  @default(false) @map("is_verified")
  folioReference String?  @map("folio_reference") // "Folio VII, Entry 12"
  productId      String?  @map("product_id")
  isActive       Boolean  @default(true) @map("is_active")
  sortOrder      Int      @default(0) @map("sort_order")
  
  product        Product? @relation(fields: [productId], references: [id])
  
  createdAt      DateTime @default(now()) @map("created_at")
  updatedAt      DateTime @updatedAt @map("updated_at")
  
  @@index([isActive, sortOrder])
  @@map("testimonials")
}

// ============================================
// NEWSLETTER
// ============================================

model NewsletterSubscriber {
  id             String    @id @default(cuid())
  email          String    @unique
  firstName      String?   @map("first_name")
  source         String?   // "footer", "correspondence_section"
  
  subscribedAt   DateTime  @default(now()) @map("subscribed_at")
  confirmedAt    DateTime? @map("confirmed_at")
  unsubscribedAt DateTime? @map("unsubscribed_at")
  
  @@map("newsletter_subscribers")
}

// ============================================
// ADMIN
// ============================================

model AdminUser {
  id           String    @id @default(cuid())
  email        String    @unique
  passwordHash String    @map("password_hash")
  firstName    String    @map("first_name")
  lastName     String    @map("last_name")
  role         AdminRole @default(ADMIN)
  isActive     Boolean   @default(true) @map("is_active")
  
  auditLogs    AuditLog[]
  
  lastLoginAt  DateTime? @map("last_login_at")
  createdAt    DateTime  @default(now()) @map("created_at")
  updatedAt    DateTime  @updatedAt @map("updated_at")
  
  @@map("admin_users")
}

model AuditLog {
  id          String   @id @default(cuid())
  adminUserId String   @map("admin_user_id")
  action      String   // "CREATE", "UPDATE", "DELETE"
  entityType  String   @map("entity_type") // "Product", "Order", etc.
  entityId    String   @map("entity_id")
  oldValues   Json?    @map("old_values")
  newValues   Json?    @map("new_values")
  ipAddress   String?  @map("ip_address")
  userAgent   String?  @map("user_agent")
  
  adminUser   AdminUser @relation(fields: [adminUserId], references: [id])
  
  createdAt   DateTime  @default(now()) @map("created_at")
  
  @@index([entityType, entityId])
  @@index([adminUserId])
  @@index([createdAt])
  @@map("audit_logs")
}

// ============================================
// CMS / SETTINGS
// ============================================

model Page {
  id              String    @id @default(cuid())
  title           String
  slug            String    @unique
  content         Json      // Rich text content
  metaTitle       String?   @map("meta_title")
  metaDescription String?   @map("meta_description")
  isPublished     Boolean   @default(false) @map("is_published")
  
  publishedAt     DateTime? @map("published_at")
  createdAt       DateTime  @default(now()) @map("created_at")
  updatedAt       DateTime  @updatedAt @map("updated_at")
  
  @@map("pages")
}

model Setting {
  id        String   @id @default(cuid())
  key       String   @unique
  value     Json
  group     String   // "general", "shipping", "email", etc.
  
  createdAt DateTime @default(now()) @map("created_at")
  updatedAt DateTime @updatedAt @map("updated_at")
  
  @@index([group])
  @@map("settings")
}
5.3 Database Indexes & Performance
SQL

-- Additional indexes for performance optimization

-- Product search
CREATE INDEX idx_products_search ON products 
USING GIN (to_tsvector('english', common_name || ' ' || latin_name || ' ' || description));

-- Order analytics
CREATE INDEX idx_orders_analytics ON orders (status, created_at) 
WHERE status != 'CANCELLED';

-- Inventory alerts
CREATE INDEX idx_inventory_low_stock ON inventory (quantity) 
WHERE quantity <= low_stock_threshold;

-- Cart cleanup
CREATE INDEX idx_carts_expired ON carts (expires_at) 
WHERE expires_at < NOW();
5.4 Seed Data Structure
TypeScript

// prisma/seed.ts - Seed data structure

const categories = [
  {
    name: 'Calming',
    slug: 'calming',
    symbol: '☾',
    color: '#B8A9C9',
    description: 'Essences for relaxation, sleep, and tranquility'
  },
  {
    name: 'Uplifting',
    slug: 'uplifting',
    symbol: '☀',
    color: '#F5D489',
    description: 'Essences for energy, mood, and vitality'
  },
  {
    name: 'Grounding',
    slug: 'grounding',
    symbol: '♁',
    color: '#7C6354',
    description: 'Essences for stability, focus, and centeredness'
  },
  {
    name: 'Clarifying',
    slug: 'clarifying',
    symbol: '☁',
    color: '#7CB9A0',
    description: 'Essences for mental clarity and respiratory wellness'
  }
];

const products = [
  {
    sku: 'LAV-724',
    folioNumber: 'I',
    latinName: 'Lavandula × intermedia',
    commonName: 'Provence Lavender',
    slug: 'provence-lavender',
    category: 'calming',
    rarity: 'RARE',
    season: 'SUMMER',
    extractionMethod: 'Steam Distillation',
    originLocation: 'Provence',
    originCountry: 'France',
    scentNotes: ['Floral', 'Herbaceous', 'Sweet'],
    featured: true,
    description: 'Harvested at dawn in the Provençal hills...',
    variants: [
      { name: '5ml Phial', sizeMl: 5, price: 42, sku: 'LAV-724-5ML', weightGrams: 25 },
      { name: '15ml Phial', sizeMl: 15, price: 98, sku: 'LAV-724-15ML', weightGrams: 45 },
      { name: '30ml Vessel', sizeMl: 30, price: 175, sku: 'LAV-724-30ML', weightGrams: 85 }
    ]
  },
  // ... additional products
];
6. API Specification
6.1 API Overview
text

Base URL: https://api.atelierarome.com/v1
          or /api (for Next.js API routes)

Authentication: Bearer token (JWT) or Cookie session
Content-Type: application/json
6.2 Public Endpoints
Products
YAML

GET /api/products:
  description: List products with filtering and pagination
  parameters:
    - name: category
      in: query
      type: string
      description: Filter by category slug
    - name: rarity
      in: query
      type: string
      enum: [common, rare, limited]
    - name: season
      in: query
      type: string
      enum: [spring, summer, autumn, winter]
    - name: featured
      in: query
      type: boolean
    - name: search
      in: query
      type: string
      description: Full-text search
    - name: sort
      in: query
      type: string
      enum: [folio, name, price-asc, price-desc, newest]
      default: folio
    - name: page
      in: query
      type: integer
      default: 1
    - name: limit
      in: query
      type: integer
      default: 12
      maximum: 50
  response:
    200:
      body:
        data:
          - id: string
            sku: string
            folioNumber: string
            latinName: string
            commonName: string
            slug: string
            shortDescription: string
            category:
              id: string
              name: string
              slug: string
              symbol: string
              color: string
            rarity: string
            season: string
            scentNotes: string[]
            featured: boolean
            primaryImage:
              url: string
              altText: string
            startingPrice: number
            variants:
              - id: string
                name: string
                sizeMl: number
                price: number
                inStock: boolean
        meta:
          page: integer
          limit: integer
          total: integer
          totalPages: integer

GET /api/products/{slug}:
  description: Get single product by slug
  parameters:
    - name: slug
      in: path
      type: string
      required: true
  response:
    200:
      body:
        id: string
        sku: string
        folioNumber: string
        latinName: string
        commonName: string
        slug: string
        description: string
        shortDescription: string
        category:
          id: string
          name: string
          slug: string
          symbol: string
          color: string
        rarity: string
        season: string
        extractionMethod: string
        originLocation: string
        originCountry: string
        scentNotes: string[]
        featured: boolean
        images:
          - id: string
            url: string
            altText: string
            isPrimary: boolean
        variants:
          - id: string
            name: string
            sizeMl: number
            price: number
            compareAtPrice: number | null
            sku: string
            inStock: boolean
            quantity: number
        relatedProducts:
          - id: string
            commonName: string
            slug: string
            primaryImage: string
            startingPrice: number
    404:
      body:
        error: "Product not found"
Categories
YAML

GET /api/categories:
  description: List all categories
  response:
    200:
      body:
        - id: string
          name: string
          slug: string
          symbol: string
          color: string
          description: string
          productCount: integer
Cart
YAML

POST /api/cart:
  description: Create a new cart (for guest users)
  response:
    201:
      body:
        id: string
        items: []
        subtotal: 0
        expiresAt: string (ISO date)

GET /api/cart/{id}:
  description: Get cart by ID
  parameters:
    - name: id
      in: path
      type: string
      required: true
  response:
    200:
      body:
        id: string
        items:
          - id: string
            variantId: string
            quantity: integer
            variant:
              id: string
              name: string
              sizeMl: number
              price: number
              sku: string
              product:
                commonName: string
                latinName: string
                slug: string
                primaryImage: string
        subtotal: number
        itemCount: integer

POST /api/cart/{id}/items:
  description: Add item to cart
  parameters:
    - name: id
      in: path
      type: string
      required: true
  body:
    variantId: string (required)
    quantity: integer (default: 1)
  response:
    200:
      body:
        # Updated cart object

PATCH /api/cart/{id}/items/{itemId}:
  description: Update cart item quantity
  parameters:
    - name: id
      in: path
      type: string
      required: true
    - name: itemId
      in: path
      type: string
      required: true
  body:
    quantity: integer (required, min: 1)
  response:
    200:
      body:
        # Updated cart object

DELETE /api/cart/{id}/items/{itemId}:
  description: Remove item from cart
  parameters:
    - name: id
      in: path
      type: string
      required: true
    - name: itemId
      in: path
      type: string
      required: true
  response:
    200:
      body:
        # Updated cart object
Checkout
YAML

POST /api/checkout:
  description: Create Stripe checkout session
  body:
    cartId: string (required)
    email: string (required for guest)
    shippingAddress:
      firstName: string
      lastName: string
      addressLine1: string
      addressLine2: string
      city: string
      state: string
      postalCode: string
      country: string
      phone: string
    billingAddress: object (optional, same as shipping if omitted)
  response:
    200:
      body:
        sessionId: string
        url: string (Stripe checkout URL)
    400:
      body:
        error: string
        details: object

POST /api/webhooks/stripe:
  description: Handle Stripe webhook events
  headers:
    stripe-signature: string
  events:
    - checkout.session.completed
    - payment_intent.succeeded
    - payment_intent.payment_failed
Newsletter
YAML

POST /api/newsletter/subscribe:
  description: Subscribe to newsletter
  body:
    email: string (required)
    firstName: string (optional)
    source: string (optional, e.g., "footer", "correspondence")
  response:
    201:
      body:
        message: "Successfully subscribed"
        email: string
    400:
      body:
        error: "Invalid email address"
    409:
      body:
        error: "Email already subscribed"
Testimonials
YAML

GET /api/testimonials:
  description: List active testimonials
  parameters:
    - name: limit
      in: query
      type: integer
      default: 6
    - name: illuminated
      in: query
      type: boolean
      description: Filter for illuminated entries only
  response:
    200:
      body:
        - id: string
          authorName: string
          authorTitle: string
          authorLocation: string
          quote: string
          rating: integer
          isIlluminated: boolean
          isVerified: boolean
          folioReference: string
          product:
            commonName: string
            slug: string
6.3 Authenticated Endpoints
Authentication
YAML

POST /api/auth/register:
  body:
    email: string (required)
    password: string (required, min 8 chars)
    firstName: string (required)
    lastName: string (required)
  response:
    201:
      body:
        user:
          id: string
          email: string
          firstName: string
          lastName: string
        message: "Verification email sent"
    400:
      body:
        error: "Validation error"
        details: object
    409:
      body:
        error: "Email already registered"

POST /api/auth/login:
  body:
    email: string (required)
    password: string (required)
  response:
    200:
      body:
        user:
          id: string
          email: string
          firstName: string
          lastName: string
        # Session cookie set
    401:
      body:
        error: "Invalid credentials"

POST /api/auth/logout:
  response:
    200:
      body:
        message: "Logged out successfully"

POST /api/auth/forgot-password:
  body:
    email: string (required)
  response:
    200:
      body:
        message: "Password reset email sent"

POST /api/auth/reset-password:
  body:
    token: string (required)
    password: string (required)
  response:
    200:
      body:
        message: "Password reset successful"
    400:
      body:
        error: "Invalid or expired token"
User Account
YAML

GET /api/me:
  description: Get current user profile
  authentication: required
  response:
    200:
      body:
        id: string
        email: string
        firstName: string
        lastName: string
        phone: string
        avatarUrl: string
        emailVerifiedAt: string
        createdAt: string

PATCH /api/me:
  description: Update user profile
  authentication: required
  body:
    firstName: string
    lastName: string
    phone: string
  response:
    200:
      body:
        # Updated user object

GET /api/me/orders:
  description: List user's orders
  authentication: required
  parameters:
    - name: status
      in: query
      type: string
    - name: page
      in: query
      type: integer
  response:
    200:
      body:
        data:
          - id: string
            orderNumber: string
            status: string
            total: number
            itemCount: integer
            createdAt: string
        meta:
          page: integer
          total: integer

GET /api/me/orders/{id}:
  description: Get order details
  authentication: required
  response:
    200:
      body:
        id: string
        orderNumber: string
        status: string
        subtotal: number
        shippingCost: number
        tax: number
        total: number
        shippingAddress: object
        billingAddress: object
        trackingNumber: string
        items:
          - productName: string
            variantName: string
            quantity: integer
            unitPrice: number
            totalPrice: number
        timeline:
          - status: string
            timestamp: string
        createdAt: string

GET /api/me/addresses:
  authentication: required
  response:
    200:
      body:
        - id: string
          type: string
          isDefault: boolean
          firstName: string
          lastName: string
          addressLine1: string
          addressLine2: string
          city: string
          state: string
          postalCode: string
          country: string
          phone: string

POST /api/me/addresses:
  authentication: required
  body:
    type: string (shipping | billing)
    isDefault: boolean
    firstName: string
    lastName: string
    addressLine1: string
    addressLine2: string
    city: string
    state: string
    postalCode: string
    country: string
    phone: string
  response:
    201:
      body:
        # Created address object

PATCH /api/me/addresses/{id}:
  authentication: required
  # Same body as POST
  response:
    200:
      body:
        # Updated address object

DELETE /api/me/addresses/{id}:
  authentication: required
  response:
    200:
      body:
        message: "Address deleted"

GET /api/me/wishlist:
  authentication: required
  response:
    200:
      body:
        - id: string
          product:
            id: string
            commonName: string
            slug: string
            primaryImage: string
            startingPrice: number
            inStock: boolean
          addedAt: string

POST /api/me/wishlist:
  authentication: required
  body:
    productId: string
  response:
    201:
      body:
        message: "Added to wishlist"

DELETE /api/me/wishlist/{productId}:
  authentication: required
  response:
    200:
      body:
        message: "Removed from wishlist"
6.4 Admin Endpoints
YAML

# All admin endpoints require authentication + admin role

GET /api/admin/dashboard:
  description: Dashboard statistics
  response:
    200:
      body:
        revenue:
          today: number
          thisWeek: number
          thisMonth: number
          percentChange: number
        orders:
          pending: integer
          processing: integer
          shipped: integer
        inventory:
          lowStock: integer
          outOfStock: integer
        customers:
          total: integer
          newThisMonth: integer
        topProducts:
          - productName: string
            sold: integer
            revenue: number

GET /api/admin/products:
  parameters:
    - name: search
    - name: category
    - name: status
    - name: page
    - name: limit
  response:
    200:
      body:
        data: Product[]
        meta: Pagination

POST /api/admin/products:
  body:
    # Full product object
  response:
    201:
      body:
        # Created product

PATCH /api/admin/products/{id}:
  body:
    # Partial product object
  response:
    200:
      body:
        # Updated product

DELETE /api/admin/products/{id}:
  response:
    200:
      body:
        message: "Product deleted"

GET /api/admin/orders:
  parameters:
    - name: status
    - name: dateFrom
    - name: dateTo
    - name: search
    - name: page
  response:
    200:
      body:
        data: Order[]
        meta: Pagination

PATCH /api/admin/orders/{id}:
  body:
    status: string
    trackingNumber: string
    notes: string
  response:
    200:
      body:
        # Updated order

GET /api/admin/inventory:
  parameters:
    - name: lowStock (boolean)
    - name: outOfStock (boolean)
  response:
    200:
      body:
        - variantId: string
          sku: string
          productName: string
          variantName: string
          quantity: integer
          lowStockThreshold: integer
          status: string

PATCH /api/admin/inventory/{variantId}:
  body:
    quantity: integer
    lowStockThreshold: integer
  response:
    200:
      body:
        # Updated inventory

# Similar patterns for:
# - /api/admin/customers
# - /api/admin/testimonials
# - /api/admin/newsletter
# - /api/admin/settings
6.5 Error Response Format
TypeScript

interface ErrorResponse {
  error: string;           // Human-readable error message
  code: string;            // Machine-readable error code
  details?: Record<string, string[]>; // Field-level validation errors
  requestId?: string;      // For debugging/support
}

// Error codes
const ERROR_CODES = {
  VALIDATION_ERROR: 'VALIDATION_ERROR',
  NOT_FOUND: 'NOT_FOUND',
  UNAUTHORIZED: 'UNAUTHORIZED',
  FORBIDDEN: 'FORBIDDEN',
  CONFLICT: 'CONFLICT',
  RATE_LIMITED: 'RATE_LIMITED',
  INTERNAL_ERROR: 'INTERNAL_ERROR',
  STRIPE_ERROR: 'STRIPE_ERROR',
  OUT_OF_STOCK: 'OUT_OF_STOCK',
  CART_EXPIRED: 'CART_EXPIRED',
};
7. Frontend Architecture
7.1 Directory Structure
text

atelier-arome/
├── app/                              # Next.js App Router
│   ├── (marketing)/                  # Marketing layout group
│   │   ├── layout.tsx
│   │   ├── page.tsx                  # Homepage
│   │   ├── about/
│   │   │   └── page.tsx              # About/Atelier story
│   │   ├── alchemy/
│   │   │   └── page.tsx              # Process page
│   │   └── contact/
│   │       └── page.tsx
│   │
│   ├── (shop)/                       # Shop layout group
│   │   ├── layout.tsx
│   │   ├── compendium/
│   │   │   ├── page.tsx              # Product listing
│   │   │   └── [slug]/
│   │   │       └── page.tsx          # Product detail
│   │   ├── cart/
│   │   │   └── page.tsx              # Cart page (full view)
│   │   └── checkout/
│   │       ├── page.tsx              # Checkout
│   │       └── success/
│   │           └── page.tsx          # Order confirmation
│   │
│   ├── (auth)/                       # Auth layout group
│   │   ├── layout.tsx
│   │   ├── login/
│   │   │   └── page.tsx
│   │   ├── register/
│   │   │   └── page.tsx
│   │   ├── forgot-password/
│   │   │   └── page.tsx
│   │   └── reset-password/
│   │       └── page.tsx
│   │
│   ├── (account)/                    # Account layout group
│   │   ├── layout.tsx                # With account sidebar
│   │   ├── account/
│   │   │   ├── page.tsx              # Dashboard
│   │   │   ├── orders/
│   │   │   │   ├── page.tsx          # Order history
│   │   │   │   └── [id]/
│   │   │   │       └── page.tsx      # Order detail
│   │   │   ├── addresses/
│   │   │   │   └── page.tsx
│   │   │   ├── wishlist/
│   │   │   │   └── page.tsx
│   │   │   └── settings/
│   │   │       └── page.tsx
│   │
│   ├── admin/                        # Admin section
│   │   ├── layout.tsx                # Admin layout with sidebar
│   │   ├── page.tsx                  # Dashboard
│   │   ├── products/
│   │   │   ├── page.tsx
│   │   │   ├── new/
│   │   │   │   └── page.tsx
│   │   │   └── [id]/
│   │   │       └── page.tsx
│   │   ├── orders/
│   │   │   ├── page.tsx
│   │   │   └── [id]/
│   │   │       └── page.tsx
│   │   ├── customers/
│   │   │   └── page.tsx
│   │   ├── inventory/
│   │   │   └── page.tsx
│   │   ├── testimonials/
│   │   │   └── page.tsx
│   │   ├── analytics/
│   │   │   └── page.tsx
│   │   └── settings/
│   │       └── page.tsx
│   │
│   ├── api/                          # API Routes
│   │   ├── auth/
│   │   │   └── [...nextauth]/
│   │   │       └── route.ts
│   │   ├── products/
│   │   │   ├── route.ts
│   │   │   └── [slug]/
│   │   │       └── route.ts
│   │   ├── categories/
│   │   │   └── route.ts
│   │   ├── cart/
│   │   │   ├── route.ts
│   │   │   └── [id]/
│   │   │       ├── route.ts
│   │   │       └── items/
│   │   │           ├── route.ts
│   │   │           └── [itemId]/
│   │   │               └── route.ts
│   │   ├── checkout/
│   │   │   └── route.ts
│   │   ├── newsletter/
│   │   │   └── route.ts
│   │   ├── testimonials/
│   │   │   └── route.ts
│   │   ├── me/
│   │   │   ├── route.ts
│   │   │   ├── orders/
│   │   │   │   └── route.ts
│   │   │   ├── addresses/
│   │   │   │   └── route.ts
│   │   │   └── wishlist/
│   │   │       └── route.ts
│   │   ├── admin/
│   │   │   └── ...
│   │   └── webhooks/
│   │       └── stripe/
│   │           └── route.ts
│   │
│   ├── 
