# Project Architecture Document: Atelier Arôme
## Digital Artisanal Aromatherapy Platform
**Document Version:** 3.0.0  
**Last Updated:** December 27, 2025  
**Classification:** Technical Specification  
**Status:** Authoritative  

---

## Table of Contents
1. [Executive Summary](#1-executive-summary)
2. [Business Requirements](#2-business-requirements)
3. [System Architecture](#3-system-architecture)
4. [Technology Stack](#4-technology-stack)
5. [Frontend Architecture](#5-frontend-architecture)
6. [Backend Architecture](#6-backend-architecture)
7. [Data Architecture](#7-data-architecture)
8. [API Specification](#8-api-specification)
9. [Security Architecture](#9-security-architecture)
10. [DevOps & Infrastructure](#10-devops--infrastructure)
11. [Development Guidelines](#11-development-guidelines)
12. [Implementation Roadmap](#12-implementation-roadmap)
13. [Appendices](#13-appendices)

---

## 1. Executive Summary

### 1.1 Project Vision
**Atelier Arôme** is not an e-commerce platform—it is a **digital alchemical manuscript** that transforms botanical commerce into an immersive experiential journey. The platform redefines luxury aromatherapy through Renaissance-inspired design, where every interaction feels like turning pages in an illuminated manuscript of botanical transformations.

### 1.2 Core Philosophy
- **Commerce as Ceremony**: Transaction as transformation, never transactional
- **Digital as Artifact**: Interface as illuminated manuscript, not UI template
- **Interaction as Ritual**: Scroll, click, and hover as alchemical gestures
- **Technology as Craft**: Code as quill, browser as parchment, commit as seal

### 1.3 Business Objectives
| Objective | Description | Success Metric |
|-----------|-------------|-----------------|
| Primary Revenue | Direct-to-consumer sales of botanical essences | €500K ARR Year 1 |
| Recurring Revenue | Quarterly Folio subscription service | 2,000 active subscribers Year 1 |
| Brand Authority | Establish as premier artisanal aromatherapy brand | 50K organic monthly visitors |
| Customer Retention | Build loyal customer base through exceptional experience | 40% repeat purchase rate |

### 1.4 Unique Value Proposition
**Aesthetic Differentiation**: Renaissance manuscript design language that is memorable and distinctive, avoiding all "AI slop" aesthetic pitfalls through:
- Distinctive typography (Cormorant Garamond, Crimson Pro) instead of generic system fonts
- Conceptual coherence where every element serves the alchemical narrative
- Purposeful asymmetry and organic composition over grid-based templates
- Meaningful micro-interactions that enhance storytelling rather than distract

**Educational Content**: Each product tells a story of botanical origin and alchemical transformation through:
- Manuscript-style product descriptions with historical context
- Botanical illustrations with scientific accuracy
- Alchemical process visualization showing extraction methods

**Artisanal Authenticity**: Small-batch production with full transparency of process:
- Batch numbers and harvest dates for traceability
- Distillation hours and extraction methods
- Artisan profiles and atelier stories

**Sensory Journey**: Digital experience designed to evoke olfactory imagination:
- Visual language that suggests scent profiles through color and form
- Micro-interactions that create tactile anticipation
- Audio-visual harmony that primes sensory memory

### 1.5 Target Audience
| Segment | Description | Characteristics | Digital Behavior |
|---------|-------------|-----------------|------------------|
| Primary | Conscious Luxury Consumers | Age 28-55, €80K+ income, values craftsmanship | Researches thoroughly, values storytelling, shares experiences |
| Secondary | Wellness Practitioners | Aromatherapists, spa owners, holistic practitioners | Technical knowledge seekers, bulk purchasers, professional network |
| Tertiary | Gift Purchasers | Premium gift seekers for special occasions | Occasional buyers, high value per transaction, emotional purchase drivers |

### 1.6 Document Scope
This PAD provides complete technical specifications for building the Atelier Arôme platform from scratch. It serves as the **single source of truth** for:
- System architecture and technology decisions
- Database schema and data relationships
- API contracts and integration points
- Security requirements and implementation
- Development standards and workflows
- Deployment and operational procedures
- Quality assurance protocols and success metrics

---

## 2. Business Requirements

### 2.1 Functional Requirements

#### 2.1.1 E-Commerce Core
| ID | Requirement | Priority | Description |
|----|-------------|----------|-------------|
| FR-001 | Product Catalog | P0 | Display essences with filtering by humour, season, rarity |
| FR-002 | Product Detail | P0 | Rich product pages with botanical information, notes, extraction method |
| FR-003 | Shopping Cart | P0 | Persistent cart with quantity management as alchemical vial |
| FR-004 | Checkout | P0 | Multi-step checkout with address, shipping, payment as ritual sequence |
| FR-005 | Payment Processing | P0 | Stripe integration for card payments with manuscript-style confirmation |
| FR-006 | Order Management | P0 | Order creation, confirmation, status tracking as alchemical dispatch |
| FR-007 | Inventory Management | P1 | Stock tracking with low-stock alerts tied to harvest cycles |
| FR-008 | Wishlist | P2 | Save products for later purchase as "specimen collection" |

#### 2.1.2 User Management
| ID | Requirement | Priority | Description |
|----|-------------|----------|-------------|
| FR-010 | Registration | P0 | Email/password registration with verification as "apprentice initiation" |
| FR-011 | Authentication | P0 | Secure login with session management as "atelier access" |
| FR-012 | Profile Management | P1 | Update personal information, preferences as "patron dossier" |
| FR-013 | Address Book | P1 | Multiple shipping/billing addresses as "correspondence locations" |
| FR-014 | Order History | P1 | View past orders with reorder capability as "manuscript archives" |
| FR-015 | Password Reset | P0 | Secure password recovery flow as "seal authentication" |
| FR-016 | Social Authentication | P2 | Google, Apple sign-in options as "guild credentials" |

#### 2.1.3 Subscription Service
| ID | Requirement | Priority | Description |
|----|-------------|----------|-------------|
| FR-020 | Folio Subscription | P1 | Quarterly subscription signup and management as "manuscript folios" |
| FR-021 | Subscription Billing | P1 | Recurring Stripe billing with seasonal pricing |
| FR-022 | Subscription Preferences | P1 | Pause, cancel, modify subscription as "alchemical schedule" |
| FR-023 | Digital Folio Delivery | P1 | Email delivery of quarterly manuscript content with illuminated attachments |

#### 2.1.4 Content Management
| ID | Requirement | Priority | Description |
|----|-------------|----------|-------------|
| FR-030 | Journal/Blog | P1 | Educational articles about botanicals and alchemy as "illuminated manuscripts" |
| FR-031 | Static Pages | P0 | About, Process, Contact, Legal pages as "atelier chronicles" |
| FR-032 | Testimonials | P1 | Customer testimonial display and management as "patron manuscripts" |
| FR-033 | Newsletter | P1 | Email capture and campaign integration as "correspondence folios" |

#### 2.1.5 Appointment Booking (Future Phase)
| ID | Requirement | Priority | Description |
|----|-------------|----------|-------------|
| FR-040 | Atelier Visits | P2 | Book appointments to visit the physical atelier |
| FR-041 | Calendar Integration | P2 | Availability management and booking confirmation |

### 2.2 Non-Functional Requirements

#### 2.2.1 Performance
| ID | Requirement | Target | Measurement |
|----|-------------|--------|-------------|
| NFR-001 | Page Load Time | < 2.5s | Largest Contentful Paint (LCP) |
| NFR-002 | Interactivity | < 100ms | First Input Delay (FID) |
| NFR-003 | Visual Stability | < 0.1 | Cumulative Layout Shift (CLS) |
| NFR-004 | API Response Time | < 200ms | 95th percentile |
| NFR-005 | Concurrent Users | 1,000 | Without performance degradation |
| NFR-006 | Animation Frame Rate | 60fps | During scroll interactions |

#### 2.2.2 Accessibility
| ID | Requirement | Target | Standard |
|----|-------------|--------|----------|
| NFR-010 | WCAG Compliance | Level AAA | WCAG 2.2 |
| NFR-011 | Keyboard Navigation | Full | All interactions keyboard-accessible |
| NFR-012 | Screen Reader Support | Full | Proper ARIA implementation with narrative descriptions |
| NFR-013 | Reduced Motion | Supported | prefers-reduced-motion honored with narrative alternatives |
| NFR-014 | Cognitive Load | Minimal | Progressive disclosure of information |

#### 2.2.3 Security
| ID | Requirement | Target | Standard |
|----|-------------|--------|----------|
| NFR-020 | Data Encryption | TLS 1.3 | In transit |
| NFR-021 | Data at Rest | AES-256 | PII encryption |
| NFR-022 | PCI Compliance | Level 1 | Via Stripe (no card data stored) |
| NFR-023 | Authentication | Secure | bcrypt, secure sessions, 2FA optional |
| NFR-024 | OWASP Top 10 | Protected | All vulnerabilities addressed |
| NFR-025 | GDPR Compliance | Full | Right to erasure, data portability |

#### 2.2.4 Availability
| ID | Requirement | Target | Notes |
|----|-------------|--------|-------|
| NFR-030 | Uptime | 99.95% | ~4.38 hours downtime/year |
| NFR-031 | Recovery Time | < 30 minutes | RTO for critical systems |
| NFR-032 | Data Loss | < 5 minutes | RPO for database |
| NFR-033 | Offline Capability | Read-only | Manuscript content available offline |

---

## 3. System Architecture

### 3.1 High-Level Architecture Diagram
```mermaid
graph TD
    subgraph Client["Client Layer"]
        direction TB
        Desktop[Desktop Browser]
        Mobile[Mobile Browser]
        Tablet[Tablet Browser]
        Kiosk[Kiosk (Atelier)]
    end

    subgraph Edge["CDN / Edge Layer"]
        Vercel[Vercel Edge Network]
        Vercel -->|Static Asset Caching| StaticAssets
        Vercel -->|Image Optimization| Images
        Vercel -->|Edge Functions| Functions
        Vercel -->|DDoS Protection| Security
    end

    subgraph Application["Application Layer"]
        NextJS[Next.js 14 Application]
        NextJS -->|React Server Components| RSC
        NextJS -->|API Routes| API
        NextJS -->|Server Actions| Actions
        NextJS -->|Middleware| Middleware
        NextJS -->|Authentication| Auth
    end

    subgraph Services["Service Layer"]
        ProductService[Product Service]
        OrderService[Order Service]
        UserService[User Service]
        SubscriptionService[Subscription Service]
        ServicesLayer[Prisma ORM]
    end

    subgraph Data["Data Layer"]
        PostgreSQL[PostgreSQL\n(Neon.tech)]
        Redis[Redis\n(Upstash)]
        Cloudinary[Cloudinary\n(Blob Storage)]
    end

    subgraph External["External Services"]
        Stripe[Stripe\n(Payments)]
        Resend[Resend\n(Email)]
        Sanity[Sanity\n(CMS)]
        Sentry[Sentry\n(Monitoring)]
        WebHaptics[Web Haptics\n(Feedback)]
        WebAudio[Web Audio\n(Ambience)]
    end

    Client --> Edge
    Edge --> Application
    Application --> Services
    Services --> Data
    Services --> External
    Data --> External
```

### 3.2 Architecture Principles
| Principle | Description | Implementation |
|-----------|-------------|----------------|
| **Manuscript-First** | Technical decisions serve the experiential narrative | Component architecture mirrors manuscript structure |
| **Type Safety** | End-to-end type safety from database to UI | TypeScript + Prisma + Zod with validation at every layer |
| **Progressive Enhancement** | Core functionality without JavaScript | Semantic HTML5 with CSS-only fallbacks for all interactions |
| **Sensory Performance** | Performance budgets for experiential integrity | Frame rate monitoring, asset prioritization, Web Worker offloading |
| **Fail Gracefully** | Resilient to external service failures | Circuit breakers, offline modes, fallback content |
| **Observable Craftsmanship** | Full visibility into system behavior | Structured logging with narrative context |

### 3.3 Data Flow Architecture
```mermaid
flowchart TB
    subgraph RequestFlow["Request Flow"]
        direction LR
        
        subgraph PageRequest["1. Page Request (SSR/SSG)"]
            Client1[Client Browser] --> EdgeCache[Edge Cache]
            EdgeCache --> NextJS1[Next.js RSC]
            NextJS1 --> Prisma1[Prisma ORM]
            Prisma1 --> NeonDB1[Neon DB]
        end
        
        subgraph APIRequest["2. API Request (Data Mutation)"]
            Client2[Client Action] --> APIRoute[API Route]
            APIRoute --> ServiceLayer[Service Layer]
            ServiceLayer --> Prisma2[Prisma ORM]
            Prisma2 --> NeonDB2[Neon DB]
            ServiceLayer --> Redis[Redis Cache]
        end
        
        subgraph RitualFlow["3. Ritual Flow (Multi-sensory)"]
            Client3[Scroll/Hover] --> RitualEngine[Ritual Engine]
            RitualEngine --> WebGL[WebGL Liquid]
            RitualEngine --> WebAudio[Audio Spatialization]
            RitualEngine --> WebHaptics[Haptic Feedback]
            RitualEngine --> Animation[CSS Animations]
        end
    end
```

### 3.4 Component Interaction Diagram
```mermaid
flowchart TB
    subgraph Client["Client Browser"]
        UI[React UI Components]
        State[Client State - Zustand]
        Forms[React Hook Form + Zod]
        Ritual[Scroll Ritual Engine]
    end
    
    subgraph Edge["Edge Layer"]
        Middleware[Next.js Middleware]
        Cache[Edge Cache]
    end

    subgraph Server["Application Server"]
        RSC[React Server Components]
        Actions[Server Actions]
        API[API Routes]
        Auth[NextAuth.js]
    end

    subgraph Services["Service Layer"]
        ProductSvc[Product Service]
        OrderSvc[Order Service]
        UserSvc[User Service]
        CartSvc[Cart Service - Vial]
        SubscriptionSvc[Subscription Service]
        RitualSvc[Ritual Service]
    end

    subgraph Data["Data Layer"]
        Prisma[Prisma Client]
        DB[(PostgreSQL)]
        Redis[(Redis Cache)]
    end

    subgraph External["External Services"]
        Stripe[Stripe API]
        Resend[Resend Email]
        Sanity[Sanity CMS]
        Cloudinary[Cloudinary CDN]
        WebHaptics[Haptics API]
        WebAudio[Web Audio API]
    end

    UI --> State
    UI --> Forms
    Forms --> Actions
    UI --> RSC
    UI --> Ritual

    RSC --> Middleware
    Actions --> Middleware
    Middleware --> Cache
    Middleware --> Auth
    Ritual --> Middleware

    RSC --> ProductSvc
    RSC --> UserSvc
    Actions --> OrderSvc
    Actions --> CartSvc
    API --> SubscriptionSvc
    Ritual --> RitualSvc

    ProductSvc --> Prisma
    OrderSvc --> Prisma
    UserSvc --> Prisma
    CartSvc --> Redis
    RitualSvc --> Redis
    SubscriptionSvc --> Prisma

    Prisma --> DB
    OrderSvc --> Stripe
    UserSvc --> Resend
    ProductSvc --> Sanity
    ProductSvc --> Cloudinary
    RitualSvc --> WebHaptics
    RitualSvc --> WebAudio
```

---

## 4. Technology Stack

### 4.1 Technology Decision Matrix

#### 4.1.1 Frontend Framework
| Option | Pros | Cons | Score |
|--------|------|------|-------|
| Next.js 14 | SSR/SSG, App Router, React ecosystem, Vercel integration | Learning curve for App Router | ⭐⭐⭐⭐⭐ |
| Remix | Full-stack, nested routes, progressive enhancement | Smaller ecosystem, less mature | ⭐⭐⭐⭐ |
| Astro | Excellent for content, island architecture | Less suited for dynamic e-commerce | ⭐⭐⭐ |
| SvelteKit | Fast, small bundle, simple syntax | Smaller ecosystem, fewer libraries | ⭐⭐⭐ |

**Decision**: Next.js 14 with App Router for its server-first architecture and edge optimization capabilities.

#### 4.1.2 Styling
| Option | Pros | Cons | Score |
|--------|------|------|-------|
| Tailwind CSS 4.0 | Utility-first, design system, small bundle | Verbose HTML | ⭐⭐⭐⭐⭐ |
| CSS Modules | Scoped, no runtime | Manual design tokens | ⭐⭐⭐⭐ |
| Vanilla Extract | Type-safe, zero-runtime | Learning curve | ⭐⭐⭐⭐ |
| Styled Components | Co-located, dynamic | Runtime cost | ⭐⭐⭐ |

**Decision**: Tailwind CSS 4.0 + Custom CSS Properties for design system consistency and performance.

#### 4.1.3 UI Components
| Option | Pros | Cons | Score |
|--------|------|------|-------|
| Shadcn/ui | Unstyled primitives, full control, accessible | Manual installation | ⭐⭐⭐⭐⭐ |
| Radix UI | Accessible primitives, unstyled | Styling overhead | ⭐⭐⭐⭐ |
| Headless UI | Tailwind integration, accessible | Limited components | ⭐⭐⭐⭐ |
| Chakra UI | Full design system, accessible | Opinionated styling | ⭐⭐⭐ |

**Decision**: Shadcn/ui (built on Radix primitives) for accessibility foundation with custom manuscript aesthetic.

#### 4.1.4 Database
| Option | Pros | Cons | Score |
|--------|------|------|-------|
| PostgreSQL (Neon) | Serverless, branching, scalable | Managed service cost | ⭐⭐⭐⭐⭐ |
| PlanetScale (MySQL) | Serverless, branching | MySQL limitations | ⭐⭐⭐⭐ |
| Supabase | PostgreSQL + extras | Less mature edge support | ⭐⭐⭐⭐ |
| MongoDB Atlas | Flexible schema | Not ideal for e-commerce | ⭐⭐⭐ |

**Decision**: PostgreSQL via Neon for ACID compliance and branching capabilities.

#### 4.1.5 ORM
| Option | Pros | Cons | Score |
|--------|------|------|-------|
| Prisma | Type-safe, great DX, migrations | Query overhead in some cases | ⭐⭐⭐⭐⭐ |
| Drizzle | Lightweight, SQL-like, fast | Newer, less ecosystem | ⭐⭐⭐⭐ |
| Kysely | Type-safe SQL builder | Manual migrations | ⭐⭐⭐ |
| Raw SQL | Full control | No type safety | ⭐⭐ |

**Decision**: Prisma ORM for type safety and developer experience.

#### 4.1.6 Animation & Sensory
| Option | Pros | Cons | Score |
|--------|------|------|-------|
| Framer Motion | React integration, complex animations | Bundle size | ⭐⭐⭐⭐⭐ |
| Three.js | 3D graphics, physics simulations | Learning curve | ⭐⭐⭐⭐ |
| GSAP | Professional animations, timeline control | Cost for commercial use | ⭐⭐⭐⭐ |
| CSS-only | Performance, no dependencies | Limited complexity | ⭐⭐⭐ |

**Decision**: Hybrid approach - Framer Motion for UI animations, Three.js for liquid simulations, CSS-only for performance-critical elements.

### 4.2 Complete Technology Stack
```yaml
ATELIER ARÔME TECHNOLOGY STACK
================================
frontend:
  framework: Next.js 14.2+
  language: TypeScript 5.4+
  runtime: React 18.3+
  styling:
    primary: Tailwind CSS 4.0
    components: Shadcn/ui (customized)
    animations: 
      - Framer Motion 11+ (UI)
      - Three.js 0.160+ (liquid simulations)
      - CSS Custom Properties (performance-critical)
  state_management:
    client: Zustand 4.5+ (ritual state)
    server: React Server Components + React Query 5.0
  forms: React Hook Form 7.51+ + Zod 3.23+
  sensory:
    haptics: Web Haptics API
    audio: Web Audio API
    spatial: Three.js Audio
  testing:
    unit: Vitest 1.5+
    component: React Testing Library 15+
    e2e: Playwright 1.43+
    visual: Chromatic
    accessibility: axe-core + Storybook

backend:
  runtime: Node.js 20 LTS
  framework: Next.js API Routes + Server Actions
  validation: Zod 3.23+
  authentication: NextAuth.js 5.0 (Auth.js)
  authorization: Custom RBAC middleware
  ritual_engine: Custom scroll ritual engine

database:
  primary: PostgreSQL 16 (Neon Serverless)
  orm: Prisma 5.14+
  cache: Redis (Upstash)
  search: PostgreSQL Full-Text Search + pgvector (future)

external_services:
  payments: Stripe (with Radar for fraud)
  email: Resend
  cms: Sanity v3 (with desk structure)
  media: Cloudinary (with AI optimization)
  analytics: Vercel Analytics + PostHog (privacy-focused)
  monitoring: Sentry + LogRocket
  seo: Next.js Sitemap + Structured Data

infrastructure:
  hosting: Vercel Pro
  cdn: Vercel Edge Network
  dns: Cloudflare (with DDoS protection)
  secrets: Vercel Environment Variables + Doppler
  preview: Vercel Preview Deployments

development:
  package_manager: pnpm 9+
  linting: ESLint 9 + Prettier 3
  git_hooks: Husky + lint-staged
  ci_cd: GitHub Actions
  documentation: Storybook 8+ + Typedoc
  design_tokens: Theo + Style Dictionary
```

### 4.3 Package Dependencies
```json
{
  "name": "atelier-arome",
  "version": "1.0.0",
  "private": true,
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "next lint",
    "test": "vitest",
    "test:e2e": "playwright test",
    "test:visual": "chromatic --project-token=$CHROMATIC_PROJECT_TOKEN",
    "db:push": "prisma db push",
    "db:migrate": "prisma migrate dev",
    "db:studio": "prisma studio",
    "db:seed": "tsx prisma/seed.ts",
    "storybook": "storybook dev -p 6006",
    "typecheck": "tsc --noEmit",
    "ritual:dev": "tsx lib/ritual-engine/dev.ts"
  },
  "dependencies": {
    "@auth/prisma-adapter": "^2.0.0",
    "@hookform/resolvers": "^3.3.4",
    "@prisma/client": "^5.14.0",
    "@radix-ui/react-accordion": "^1.1.2",
    "@radix-ui/react-alert-dialog": "^1.0.5",
    "@radix-ui/react-aspect-ratio": "^1.0.3",
    "@radix-ui/react-checkbox": "^1.0.4",
    "@radix-ui/react-dialog": "^1.0.5",
    "@radix-ui/react-dropdown-menu": "^2.0.6",
    "@radix-ui/react-label": "^2.0.2",
    "@radix-ui/react-popover": "^1.0.7",
    "@radix-ui/react-radio-group": "^1.1.3",
    "@radix-ui/react-select": "^2.0.0",
    "@radix-ui/react-separator": "^1.0.3",
    "@radix-ui/react-slot": "^1.0.2",
    "@radix-ui/react-tabs": "^1.0.4",
    "@radix-ui/react-toast": "^1.1.5",
    "@radix-ui/react-tooltip": "^1.0.7",
    "@sanity/client": "^6.15.7",
    "@sanity/image-url": "^1.0.2",
    "@sentry/nextjs": "^7.110.0",
    "@stripe/react-stripe-js": "^2.7.0",
    "@stripe/stripe-js": "^3.3.0",
    "@upstash/redis": "^1.30.0",
    "@vercel/analytics": "^1.2.2",
    "class-variance-authority": "^0.7.0",
    "clsx": "^2.1.0",
    "cmdk": "^1.0.0",
    "framer-motion": "^11.1.7",
    "lucide-react": "^0.372.0",
    "next": "14.2.3",
    "next-auth": "5.0.0-beta.18",
    "next-sanity": "^9.0.15",
    "react": "^18.3.1",
    "react-dom": "^18.3.1",
    "react-hook-form": "^7.51.3",
    "resend": "^3.2.0",
    "stripe": "^15.5.0",
    "tailwind-merge": "^2.3.0",
    "tailwindcss-animate": "^1.0.7",
    "three": "^0.160.0",
    "zod": "^3.23.4",
    "zustand": "^4.5.2"
  },
  "devDependencies": {
    "@chromatic-com/storybook": "^1.3.3",
    "@playwright/test": "^1.43.1",
    "@storybook/addon-essentials": "^8.0.9",
    "@storybook/addon-interactions": "^8.0.9",
    "@storybook/addon-links": "^8.0.9",
    "@storybook/blocks": "^8.0.9",
    "@storybook/nextjs": "^8.0.9",
    "@storybook/react": "^8.0.9",
    "@testing-library/jest-dom": "^6.4.2",
    "@testing-library/react": "^15.0.5",
    "@types/node": "^20.12.7",
    "@types/react": "^18.3.1",
    "@types/react-dom": "^18.3.0",
    "@typescript-eslint/eslint-plugin": "^7.7.1",
    "@typescript-eslint/parser": "^7.7.1",
    "autoprefixer": "^10.4.19",
    "eslint": "^9.1.1",
    "eslint-config-next": "14.2.3",
    "eslint-plugin-storybook": "^0.8.0",
    "husky": "^9.0.11",
    "lint-staged": "^15.2.2",
    "postcss": "^8.4.38",
    "prettier": "^3.2.5",
    "prettier-plugin-tailwindcss": "^0.5.14",
    "prisma": "^5.14.0",
    "storybook": "^8.0.9",
    "tailwindcss": "^4.0.0",
    "tsx": "^4.7.3",
    "typescript": "^5.4.5",
    "vitest": "^1.5.2"
  }
}
```

---

## 5. Frontend Architecture

### 5.1 Directory Structure
```
src/
├── app/                          # Next.js App Router
│   ├── (auth)/                   # Auth route group
│   │   ├── login/
│   │   │   └── page.tsx
│   │   ├── register/
│   │   │   └── page.tsx
│   │   ├── forgot-password/
│   │   │   └── page.tsx
│   │   ├── verify-email/
│   │   │   └── page.tsx
│   │   └── layout.tsx
│   ├── (shop)/                   # Shop route group
│   │   ├── page.tsx                # Homepage - Hero Folio
│   │   ├── compendium/           # Product catalog
│   │   │   ├── page.tsx            # Grid view with filters
│   │   │   ├── [slug]/             # Individual essence
│   │   │   │   └── page.tsx
│   │   │   └── layout.tsx          # Compendium layout
│   │   ├── alchemy/                # Process page
│   │   │   └── page.tsx
│   │   ├── atelier/              # About page
│   │   │   └── page.tsx
│   │   ├── manuscript/           # Blog/Journal
│   │   │   ├── page.tsx            # All manuscripts
│   │   │   ├── [slug]/             # Individual manuscript
│   │   │   │   └── page.tsx
│   │   │   └── layout.tsx
│   │   ├── vial/                  # Cart system
│   │   │   └── page.tsx
│   │   ├── dispatch/              # Checkout flow
│   │   │   ├── page.tsx            # Shipping & billing
│   │   │   ├── payment/
│   │   │   │   └── page.tsx        # Payment method
│   │   │   └── confirmation/       # Order confirmation
│   │   │       └── page.tsx
│   │   └── layout.tsx              # Shop layout
│   ├── (atelier)/                 # Admin/atelier management
│   │   ├── dashboard/
│   │   │   └── page.tsx
│   │   ├── essences/
│   │   │   ├── page.tsx
│   │   │   └── [id]/
│   │   │       └── page.tsx
│   │   ├── orders/
│   │   │   ├── page.tsx
│   │   │   └── [id]/
│   │   │       └── page.tsx
│   │   └── layout.tsx
│   ├── (account)/                 # Account route group
│   │   ├── patron/
│   │   │   ├── page.tsx            # Dashboard
│   │   │   ├── orders/
│   │   │   │   ├── page.tsx
│   │   │   │   └── [id]/
│   │   │   │       └── page.tsx
│   │   │   ├── addresses/
│   │   │   │   └── page.tsx
│   │   │   ├── folios/             # Subscriptions
│   │   │   │   └── page.tsx
│   │   │   └── settings/
│   │   │       └── page.tsx
│   │   └── layout.tsx
│   ├── api/                       # API Routes
│   │   ├── auth/
│   │   │   └── [...nextauth]/
│   │   │       └── route.ts
│   │   ├── webhooks/
│   │   │   ├── stripe/
│   │   │   │   └── route.ts
│   │   │   └── sanity/
│   │   │       └── route.ts
│   │   ├── vial/                   # Cart API
│   │   │   └── route.ts
│   │   ├── ritual/                 # Scroll ritual API
│   │   │   └── route.ts
│   │   └── folio/
│   │       └── route.ts
│   ├── ritual/                     # Ritual engine pages
│   │   ├── scroll-indicator/
│   │   │   └── page.tsx
│   │   └── haptic-feedback/
│   │       └── page.tsx
│   ├── error.tsx
│   ├── not-found.tsx
│   ├── loading.tsx
│   ├── layout.tsx                  # Root layout
│   └── globals.css
├── components/
│   ├── ui/                        # Shadcn UI components (customized)
│   │   ├── accordion.tsx
│   │   ├── alert-dialog.tsx
│   │   ├── button.tsx              # ManuscriptButton with ornament props
│   │   ├── card.tsx                # ManuscriptCard with border variants
│   │   ├── checkbox.tsx
│   │   ├── dialog.tsx
│   │   ├── dropdown-menu.tsx
│   │   ├── form.tsx
│   │   ├── input.tsx
│   │   ├── label.tsx
│   │   ├── popover.tsx
│   │   ├── radio-group.tsx
│   │   ├── select.tsx
│   │   ├── separator.tsx
│   │   ├── sheet.tsx               # VialDrawer component
│   │   ├── skeleton.tsx
│   │   ├── tabs.tsx
│   │   ├── toast.tsx
│   │   ├── toaster.tsx
│   │   └── tooltip.tsx
│   ├── layout/                    # Layout components
│   │   ├── header/
│   │   │   ├── header.tsx          # ManuscriptHeader with seal
│   │   │   ├── navigation.tsx      # ManuscriptNavigation with folio numbers
│   │   │   ├── mobile-nav.tsx
│   │   │   ├── vial-button.tsx     # VialCartButton with liquid animation
│   │   │   └── atelier-seal.tsx    # Animated gold seal
│   │   ├── footer/
│   │   │   ├── footer.tsx
│   │   │   └── colophon.tsx        # Historical colophon with printer marks
│   │   ├── parchment-overlay.tsx  # Noise texture overlay
│   │   ├── gold-leaf-accents.tsx   # Parallax gold leaf elements
│   │   ├── manuscript-border.tsx  # Hand-drawn border component
│   │   └── back-to-top.tsx         # Scroll to top with quill icon
│   ├── ritual/                    # Ritual components
│   │   ├── scroll-indicator.tsx    # Quill-pen scroll indicator
│   │   ├── haptic-feedback.tsx     # Haptic pulse controller
│   │   ├── audio-ambience.tsx      # Spatial audio controller
│   │   ├── liquid-simulation.tsx   # Three.js liquid wave simulation
│   │   └── section-transition.tsx  # Folio transition animations
│   ├── products/                  # Product components
│   │   ├── essence-card.tsx        # EssenceCard with humour badges
│   │   ├── essence-grid.tsx        # Asymmetric grid layout
│   │   ├── essence-filters.tsx     # HumourFilter with alchemical symbols
│   │   ├── essence-sort.tsx
│   │   ├── essence-detail.tsx      # Detailed product view
│   │   ├── botanical-illustration.tsx # Hand-drawn botanical SVGs
│   │   ├── humour-badge.tsx        # Humour type badges with symbols
│   │   └── rarity-tag.tsx          # Rarity indicators with illuminated borders
│   ├── cart/                      # Cart components (Vial system)
│   │   ├── vial-drawer.tsx         # Main vial drawer component
│   │   ├── vial-item.tsx           # Individual essence in vial
│   │   ├── vial-summary.tsx        # Subtotal and checkout
│   │   └── add-to-vial-button.tsx  # Add essence to vial with animation
│   ├── checkout/                  # Checkout components (Dispatch system)
│   │   ├── dispatch-form.tsx       # Multi-step dispatch form
│   │   ├── address-form.tsx        # Address form with manuscript styling
│   │   ├── shipping-options.tsx    # Shipping methods as courier options
│   │   ├── payment-form.tsx        # Payment form with illuminated fields
│   │   └── order-summary.tsx       # Order summary with alchemical pricing
│   ├── account/                   # Account components
│   │   ├── order-history.tsx       # Historical order list
│   │   ├── order-detail.tsx        # Detailed order view
│   │   ├── address-book.tsx        # Multiple addresses management
│   │   ├── subscription-card.tsx   # Folio subscription card
│   │   └── profile-form.tsx        # Patron profile form
│   ├── content/                   # Content components
│   │   ├── hero-section.tsx        # Hero folio with illuminated initial
│   │   ├── alchemy-process.tsx     # Four-step alchemical process
│   │   ├── testimonial-entry.tsx   # Patron testimonial with manuscript styling
│   │   ├── manuscript-card.tsx     # Journal entry card
│   │   ├── newsletter-form.tsx     # Correspondence subscription
│   │   ├── illuminated-initial.tsx # Decorative first letter
│   │   └── floating-botanicals.tsx # Floating plant specimens with physics
│   ├── decorative/               # Decorative elements
│   │   ├── gold-leaf.tsx           # Gold leaf accent with shimmer
│   │   ├── parchment-texture.tsx   # Parchment background texture
│   │   ├── manuscript-border.tsx   # Hand-drawn border with corner accents
│   │   ├── wax-seal.tsx            # Wax seal notification component
│   │   ├── quill-icon.tsx          # Animated quill icon
│   │   └── alchemical-symbol.tsx   # Alchemical symbols with rotation
│   └── shared/                    # Shared components
│       ├── section-header.tsx      # Section title with ornamentation
│       ├── loading-spinner.tsx     # Manuscript-style loading spinner
│       ├── error-boundary.tsx      # Error boundary with manuscript fallback
│       ├── seo.tsx                 # SEO metadata component
│       └── analytics.tsx           # Privacy-focused analytics
├── lib/                           # Utilities and configurations
│   ├── prisma.ts                  # Prisma client singleton
│   ├── auth.ts                    # NextAuth configuration
│   ├── stripe.ts                  # Stripe client
│   ├── sanity.ts                  # Sanity client
│   ├── redis.ts                   # Redis client
│   ├── resend.ts                  # Email client
│   ├── ritual-engine.ts           # Scroll ritual engine
│   ├── sensory-utils.ts           # Haptic, audio utility functions
│   ├── utils.ts                   # General utilities
│   └── constants.ts               # Application constants
├── services/                      # Business logic layer
│   ├── product.service.ts
│   ├── vial.service.ts            # Cart service renamed to Vial
│   ├── order.service.ts
│   ├── user.service.ts
│   ├── subscription.service.ts
│   ├── email.service.ts
│   ├── inventory.service.ts
│   └── ritual.service.ts          # Ritual service for scroll interactions
├── hooks/                         # Custom React hooks
│   ├── use-vial.ts                # Cart hook renamed to useVial
│   ├── use-user.ts
│   ├── use-products.ts
│   ├── use-scroll-ritual.ts       # Scroll ritual hook
│   ├── use-haptic-feedback.ts     # Haptic feedback hook
│   ├── use-audio-ambience.ts      # Spatial audio hook
│   ├── use-media-query.ts
│   ├── use-reduced-motion.ts
│   └── use-toast.ts               # Wax seal toast hook
├── stores/                        # Zustand stores
│   ├── vial.store.ts              # Cart store renamed to vial
│   ├── ui.store.ts                # UI state (drawers, modals)
│   ├── ritual.store.ts            # Ritual state (scroll position, haptics)
│   └── filter.store.ts            # Filter preferences
├── schemas/                       # Zod validation schemas
│   ├── product.schema.ts
│   ├── vial.schema.ts             # Cart schema renamed to vial
│   ├── order.schema.ts
│   ├── user.schema.ts
│   ├── address.schema.ts
│   └── subscription.schema.ts
├── types/                         # TypeScript types
│   ├── product.types.ts
│   ├── vial.types.ts              # Cart types renamed to vial
│   ├── order.types.ts
│   ├── user.types.ts
│   ├── ritual.types.ts            # Ritual engine types
│   └── api.types.ts
├── styles/                        # Global styles
│   ├── fonts.ts                   # Font configurations
│   ├── theme.ts                   # Design tokens
│   ├── animations.css             # Custom animations
│   └── ritual-animations.css      # Scroll-triggered animations
└── config/                        # Configuration files
    ├── site.ts                    # Site metadata
    ├── navigation.ts              # Navigation structure
    ├── seo.ts                     # SEO configuration
    └── ritual-config.ts           # Ritual engine configuration
```

### 5.2 Component Architecture

#### 5.2.1 Component Hierarchy Diagram
```mermaid
graph TB
subgraph RootLayout["Root Layout"]
ThemeProvider[Theme Provider]
AuthProvider[Auth Provider]
RitualProvider[Ritual Provider] --> SensoryEngine[Sensory Engine]
ToastProvider[Toast Provider - WaxSeal]

subgraph DecorativeLayer["Decorative Layer"]
ParchmentOverlay[Parchment Overlay]
GoldLeafAccents[Gold Leaf Accents]
ManuscriptBorder[Manuscript Border]
end

subgraph Header["Header - Atelier Banner"]
AtelierSeal[Atelier Seal - Gold embossed logo]
ManuscriptNavigation[Manuscript Navigation - Roman numerals]
VialButton[Vial Button - Liquid wave animation]
MobileNav[Mobile Nav - Hidden scroll menu]
end

subgraph Main["Main Content"]
PageContent[Page Content]
end

subgraph Footer["Footer - Colophon"]
AtelierInfo[Atelier Information]
ManuscriptNavigationCopy[Navigation Copy]
SocialCorrespondence[Social Links as Correspondence]
end

subgraph Drawers["Overlay Components"]
VialDrawer[Vial Drawer - Cart as collection vial]
WaxSealToast[Wax Seal Toast - Notifications]
QuillScrollIndicator[Quill Scroll Indicator]
end
end

ThemeProvider --> AuthProvider
AuthProvider --> RitualProvider
RitualProvider --> ToastProvider

ToastProvider --> DecorativeLayer
ToastProvider --> Header
ToastProvider --> Main
ToastProvider --> Footer
ToastProvider --> Drawers

DecorativeLayer --> Header
Header --> Main
Main --> Footer
```

#### 5.2.2 Component Specification Template
```typescript
/**
 * COMPONENT SPECIFICATION: EssenceCard
 * =====================================
 * 
 * Purpose: Display a single essence product in the compendium grid as an alchemical specimen
 * Narrative Role: Each card represents a botanical specimen in the atelier's collection
 * 
 * Props:
 * essence: Essence (required) - The essence data object with alchemical properties
 * variant: 'default' | 'featured' | 'compact' (optional, default: 'default')
 * onAddToVial: (essence: Essence) => void (optional) - Vial (cart) callback with ritual animation
 * showHumour: boolean (optional, default: true) - Show humour classification badge
 * showRarity: boolean (optional, default: true) - Show rarity indicator
 * isFloating: boolean (optional, default: false) - Enable floating animation for hero specimens
 * 
 * State:
 * isAdding: boolean - Loading state for add to vial with liquid animation
 * isHovered: boolean - Hover state for botanical specimen float animation
 * interactionCount: number - Track interactions for ritual progression
 * 
 * Accessibility:
 * article element with proper heading hierarchy (h3 for name, p for description)
 * Button with aria-label for screen readers: "Add {essence.name} to collection vial"
 * Reduced motion support: disable floating animation when prefers-reduced-motion
 * Focus management: keyboard navigable with visual focus ring
 * Semantic landmarks: section role="region" with aria-labelledby
 * 
 * Styling:
 * Uses Tailwind classes with custom theme tokens
 * Asymmetric layout with organic positioning
 * Botanical specimen illustration with floating animation
 * Humour badge positioned as alchemical classification
 * Gold leaf accents on hover for premium perception
 * Responsive: stacks on mobile, asymmetric grid on desktop
 * Print stylesheet: preserves manuscript aesthetic for physical printing
 * 
 * Performance:
 * Lazy-loaded botanical illustrations
 * CSS containment for layout isolation
 * Will-change optimization for floating animation
 * Intersection Observer for scroll-triggered animations
 * 
 * Ritual Integration:
 * Haptic feedback on add-to-vial interaction
 * Audio spatialization for liquid pouring sound
 * Scroll progress tracking for narrative sequencing
 */
interface EssenceCardProps {
  essence: Essence;
  variant?: 'default' | 'featured' | 'compact';
  onAddToVial?: (essence: Essence) => void;
  showHumour?: boolean;
  showRarity?: boolean;
  isFloating?: boolean;
  className?: string;
}
```

### 5.3 State Management Strategy

#### 5.3.1 State Distribution
```mermaid
flowchart TD
    subgraph StateManagement["State Management Strategy"]
        direction TB
        
        subgraph ServerState["SERVER STATE (React Query / RSC)"]
            ProductsCatalog[Products catalog]
            UserSession[User session]
            OrderHistory[Order history]
            CMSContent[CMS content]
            ServerStateStrategy[Strategy: React Server Components + Server Actions]
            ServerStateCache[Cache: Edge cache + Revalidation on mutation]
        end
        
        subgraph ClientState["CLIENT STATE (Zustand)"]
            Vial[Vial contents (synced to Redis)]
            UIState[UI state (mobile menu, drawers)]
            FilterPreferences[Filter preferences]
            FormState[Form state (temporary)]
            ClientStateStrategy[Strategy: Zustand stores with persistence]
            ClientStateSync[Sync: Optimistic updates + background sync]
        end
        
        subgraph RitualState["RITUAL STATE (Zustand + Web APIs)"]
            ScrollPosition[Scroll position and momentum]
            HapticFeedback[Haptic feedback state]
            AudioAmbience[Audio spatialization state]
            VisualRituals[Visual ritual animations]
            RitualStateStrategy[Strategy: Zustand + Web Haptics/Audio APIs]
            RitualStatePersistence[Persistence: session-based, not stored]
        end
        
        subgraph UrlState["URL STATE (nuqs)"]
            Filters[Filter selections]
            SortPreferences[Sort preferences]
            Pagination[Pagination]
            SearchQueries[Search queries]
            UrlStateStrategy[Strategy: Type-safe URL search params]
            UrlStateBenefits[Benefits: Shareable, bookmarkable, SSR-friendly]
        end
        
        subgraph FormState["FORM STATE (React Hook Form)"]
            CheckoutForms[Dispatch forms]
            ProfileForms[Patron forms]
            AddressForms[Correspondence location forms]
            NewsletterSignup[Correspondence signup]
            FormStateStrategy[Strategy: Uncontrolled forms with Zod validation]
            FormStateBenefits[Benefits: Performance, validation, type safety]
        end
    end
```

#### 5.3.2 Vial Store Implementation (Cart as Alchemical Collection Vial)
```typescript
// stores/vial.store.ts
import { create } from 'zustand';
import { persist, createJSONStorage } from 'zustand/middleware';
import { immer } from 'zustand/middleware/immer';
import type { VialItem, Essence } from '@/types';
import { triggerVialHaptic, triggerVialAudio } from '@/lib/sensory-utils';

interface VialState {
  items: VialItem[];
  isOpen: boolean;
  isLoading: boolean;
  lastSynced: Date | null;
  liquidLevel: number; // 0.0 to 1.0 representing fill level
  essenceColors: string[]; // For layered liquid effect
  
  // Actions
  addItem: (essence: Essence, quantity?: number) => void;
  removeItem: (essenceId: string) => void;
  updateQuantity: (essenceId: string, quantity: number) => void;
  clearVial: () => void;
  openVial: () => void;
  closeVial: () => void;
  toggleVial: () => void;
  syncWithServer: () => Promise<void>;
  
  // Computed (getters)
  getItemCount: () => number;
  getSubtotal: () => number;
  getLiquidLevel: () => number;
  getEssenceColors: () => string[];
  getItem: (essenceId: string) => VialItem | undefined;
}

export const useVialStore = create<VialState>()(
  persist(
    immer((set, get) => ({
      items: [],
      isOpen: false,
      isLoading: false,
      lastSynced: null,
      liquidLevel: 0,
      essenceColors: [],
      
      addItem: (essence, quantity = 1) => {
        set((state) => {
          const existingIndex = state.items.findIndex(
            (item) => item.essence.id === essence.id
          );
          
          if (existingIndex > -1) {
            state.items[existingIndex].quantity += quantity;
          } else {
            state.items.push({
              id: crypto.randomUUID(),
              essence,
              quantity,
              addedAt: new Date().toISOString(),
            });
          }
          
          // Update liquid level based on item count
          state.liquidLevel = Math.min(1, state.items.length / 12);
          
          // Update essence colors for layered liquid effect
          state.essenceColors = Array.from(
            new Set(state.items.map(item => item.essence.color))
          ).slice(0, 3); // Limit to 3 colors for performance
        });
        
        // Trigger sensory feedback
        triggerVialHaptic('add');
        triggerVialAudio('pour');
        
        // Trigger background sync
        get().syncWithServer();
      },
      
      removeItem: (essenceId) => {
        set((state) => {
          state.items = state.items.filter(
            (item) => item.essence.id !== essenceId
          );
          
          // Update liquid level
          state.liquidLevel = Math.min(1, state.items.length / 12);
          
          // Update essence colors
          state.essenceColors = Array.from(
            new Set(state.items.map(item => item.essence.color))
          ).slice(0, 3);
        });
        
        // Trigger sensory feedback
        triggerVialHaptic('remove');
        triggerVialAudio('swirl');
        
        get().syncWithServer();
      },
      
      updateQuantity: (essenceId, quantity) => {
        if (quantity < 1) {
          get().removeItem(essenceId);
          return;
        }
        
        set((state) => {
          const item = state.items.find(
            (item) => item.essence.id === essenceId
          );
          if (item) {
            const oldQuantity = item.quantity;
            item.quantity = quantity;
            
            // Adjust liquid level proportionally
            const quantityChange = quantity - oldQuantity;
            state.liquidLevel = Math.min(1, Math.max(0, 
              state.liquidLevel + (quantityChange / 12)
            ));
          }
        });
        
        // Trigger sensory feedback proportional to change
        const intensity = Math.abs(quantity - (get().getItem(essenceId)?.quantity || 1));
        triggerVialHaptic('update', intensity);
        triggerVialAudio('adjust');
        
        get().syncWithServer();
      },
      
      clearVial: () => {
        set({ items: [], liquidLevel: 0, essenceColors: [] });
        triggerVialHaptic('clear');
        triggerVialAudio('empty');
        get().syncWithServer();
      },
      
      openVial: () => {
        set({ isOpen: true });
        triggerVialHaptic('open');
      },
      
      closeVial: () => {
        set({ isOpen: false });
        triggerVialHaptic('close');
      },
      
      toggleVial: () => {
        const newState = !get().isOpen;
        set({ isOpen: newState });
        triggerVialHaptic(newState ? 'open' : 'close');
      },
      
      syncWithServer: async () => {
        set({ isLoading: true });
        try {
          await fetch('/api/vial', {
            method: 'POST',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify({ items: get().items }),
          });
          set({ lastSynced: new Date() });
        } catch (error) {
          console.error('Vial sync failed:', error);
          triggerVialHaptic('error');
        } finally {
          set({ isLoading: false });
        }
      },
      
      getItemCount: () => {
        return get().items.reduce((sum, item) => sum + item.quantity, 0);
      },
      
      getSubtotal: () => {
        return get().items.reduce(
          (sum, item) => sum + item.essence.price * item.quantity,
          0
        );
      },
      
      getLiquidLevel: () => {
        return get().liquidLevel;
      },
      
      getEssenceColors: () => {
        return get().essenceColors;
      },
      
      getItem: (essenceId) => {
        return get().items.find((item) => item.essence.id === essenceId);
      },
    })),
    {
      name: 'atelier-vial',
      storage: createJSONStorage(() => localStorage),
      partialize: (state) => ({
        items: state.items,
        lastSynced: state.lastSynced,
        liquidLevel: state.liquidLevel,
        essenceColors: state.essenceColors,
      }),
    }
  )
);
```

### 5.4 Design System Specification

#### 5.4.1 Design Tokens
```typescript
// styles/theme.ts
export const theme = {
  colors: {
    // Primary Palette - Illuminated Manuscript
    ink: {
      DEFAULT: '#2A2D26',           // Deep manuscript ink
      light: '#4A4D46',             // Lighter ink for secondary text
      muted: '#545752',             // Accessible version for contrast
      faded: '#6A6D66',             // Faded ink for subtle elements
    },
    gold: {
      DEFAULT: '#C9A769',           // Warm gold leaf
      light: '#E8D8B6',             // Light gold for highlights
      dark: '#A98750',              // Dark gold for shadows
      muted: 'rgba(201, 167, 105, 0.3)', // Muted gold for overlays
      text: '#8B7355',              // Accessible gold for text on light
    },
    parchment: {
      DEFAULT: '#FAF8F5',           // Warm parchment base
      dark: '#F5F1EB',              // Slightly darker parchment
      darker: '#E8E4D9',            // Darkest parchment for depth
    },
    
    // Accent Palette - Historical pigments
    bronze: '#9A8C6D',              // Bronze patina
    rose: '#B87D7D',                // Rose madder pigment
    sage: '#7C6354',                // Sage green
    slate: '#7A8C9D',               // Slate blue
    
    // Botanical Accents - Directly from distillation process
    lavender: {
      DEFAULT: '#B8A9C9',           // True lavender from Provence
      light: '#D6CCE0',
      dark: '#8A7DA4',
    },
    eucalyptus: {
      DEFAULT: '#7CB9A0',           // Tasmanian eucalyptus
      light: '#A8D6C0', 
      dark: '#5A8A78',
    },
    bergamot: {
      DEFAULT: '#F5D489',           // Calabrian bergamot
      light: '#F9E6B3',
      dark: '#C8A86C',
    },
    rosehip: {
      DEFAULT: '#E8B4B8',           // Wild rosehip
      light: '#F5D9DC',
      dark: '#B98488',
    },
    
    // Semantic Colors - For UI elements
    error: {
      DEFAULT: '#DC2626',           // Crimson error
      light: '#FECACA',
      dark: '#B91C1C',
    },
    success: {
      DEFAULT: '#16A34A',           // Deep green success
      light: '#BBF7D0',
      dark: '#15803D',
    },
    warning: {
      DEFAULT: '#CA8A04',           // Amber warning
      light: '#FEEB8B',
      dark: '#B45309',
    },
    info: {
      DEFAULT: '#2563EB',           // Deep blue info
      light: '#BFDBFE',
      dark: '#1E40AF',
    },
  },
  typography: {
    fonts: {
      // Renaissance manuscript text (15th century)
      manuscript: {
        display: ['Cormorant Garamond', 'Baskerville', 'serif'],
        body: ['Crimson Pro', 'Garamond Premier Pro', 'serif'],
        ornament: ['Playfair Display SC', 'Hoefler Text', 'serif'],
      },
      
      // Contemporary alchemical notation (21st century)
      alchemical: {
        symbols: ['Adobe Caslon Pro', 'serif'],
        measurements: ['IBM Plex Mono', 'monospace'],
        transitions: ['Great Vibes', 'cursive'], // For ritual transitions
      },
    },
    sizes: {
      // Optical sizing based on manuscript proportions
      xs: 'clamp(0.75rem, 0.7rem + 0.25vw, 0.875rem)',     // 12px base
      sm: 'clamp(0.875rem, 0.8rem + 0.35vw, 1rem)',          // 14px base
      base: 'clamp(1rem, 0.95rem + 0.25vw, 1.125rem)',       // 16px base
      lg: 'clamp(1.125rem, 1rem + 0.5vw, 1.25rem)',          // 18px base
      xl: 'clamp(1.25rem, 1.1rem + 0.75vw, 1.5rem)',         // 20px base
      '2xl': 'clamp(1.5rem, 1.25rem + 1.25vw, 2rem)',        // 24px base
      '3xl': 'clamp(2rem, 1.5rem + 2.5vw, 3rem)',            // 32px base
      '4xl': 'clamp(2.5rem, 2rem + 2.5vw, 4rem)',            // 40px base
      '5xl': 'clamp(3rem, 2.5rem + 2.5vw, 5rem)',            // 48px base
    },
    lineHeight: {
      manuscript: 1.618,  // Golden ratio for readability
      annotation: 1.333,  // 4:3 ratio for marginalia
      heading: 1.25,      // Tighter for headings
    },
  },
  spacing: {
    // Based on Renaissance manuscript margins - not 8px grid
    '3xs': '0.125rem',    // 2px - hairline space
    '2xs': '0.25rem',     // 4px - fine detail
    xs: '0.5rem',         // 8px - small margin
    sm: '0.75rem',        // 12px - medium margin  
    md: '1rem',           // 16px - standard margin
    lg: '1.5rem',         // 24px - large margin
    xl: '2rem',           // 32px - section margin
    '2xl': '3rem',        // 48px - major section margin
    '3xl': '4rem',        // 64px - page margin
    '4xl': '6rem',        // 96px - dramatic space
    '5xl': '8rem',        // 128px - epic space
    '6xl': '12rem',       // 192px - cinematic space
    
    // Organic spacing for asymmetric layouts
    organic: {
      top: '1.618rem',    // Golden ratio top margin
      right: '1.333rem',  // 4:3 ratio right margin
      bottom: '2.236rem', // sqrt(5) ratio bottom margin
      left: '1rem',       // Standard left margin
    },
  },
  borderRadius: {
    sm: '0.125rem',     // 2px - sharp corners
    md: '0.25rem',      // 4px - slightly rounded
    lg: '0.5rem',       // 8px - standard rounded
    xl: '1rem',         // 16px - soft rounded
    '2xl': '2rem',      // 32px - deeply rounded
    '3xl': '4rem',      // 64px - organic rounded
    full: '9999px',     // Circular
    manuscript: '0.375rem', // Hand-drawn imperfection
  },
  shadows: {
    sm: '0 1px 2px rgba(42, 45, 38, 0.05)',                // Subtle shadow
    md: '0 4px 12px rgba(42, 45, 38, 0.08)',               // Medium shadow
    lg: '0 8px 24px rgba(42, 45, 38, 0.1)',                // Large shadow
    xl: '0 16px 48px rgba(42, 45, 38, 0.12)',              // Extra large shadow
    gold: '0 0 40px rgba(201, 167, 105, 0.2)',             // Gold leaf shimmer
    ritual: '0 0 30px rgba(105, 97, 85, 0.15)',            // Ritual glow
  },
  transitions: {
    micro: '150ms ease',            // Micro-interactions
    fast: '300ms ease',             // Standard interactions
    base: '500ms ease',             // Major transitions
    slow: '800ms ease',             // Deliberate transitions
    bounce: '600ms cubic-bezier(0.34, 1.56, 0.64, 1)', // Bouncy transitions
    ritual: '1200ms cubic-bezier(0.64, 0, 0.35, 1)',    // Ritual transitions
  },
  zIndex: {
    base: 1,                        // Base layer
    elevated: 10,                    // Elevated elements
    sticky: 100,                     // Sticky elements (header)
    overlay: 1000,                   // Overlay elements (dropdowns)
    modal: 2000,                     // Modal dialogs
    toast: 3000,                     // Toast notifications (wax seals)
    ritual: 4000,                    // Ritual elements (floating botanicals)
  },
} as const;

export type Theme = typeof theme;

// Sensory design tokens for multi-sensory experience
export const sensoryTokens = {
  haptics: {
    intensity: {
      subtle: 20,    // Gentle pulse for micro-interactions
      medium: 50,    // Noticeable pulse for primary actions
      strong: 80,    // Strong pulse for important events
    },
    duration: {
      micro: 50,     // 50ms - imperceptible but felt
      short: 100,    // 100ms - distinct pulse
      medium: 200,   // 200ms - sustained vibration
      long: 500,     // 500ms - extended vibration
    },
  },
  audio: {
    spatialization: {
      near: 0.8,     // Close proximity
      medium: 0.5,   // Medium distance
      far: 0.2,      // Far distance
    },
    volume: {
      whisper: 0.2,  // Barely audible
      soft: 0.4,     // Soft background
      medium: 0.6,   // Noticeable
      loud: 0.8,     // Prominent
    },
  },
  motion: {
    reduced: {
      prefersReducedMotion: true, // System preference
      disableFloating: true,      // Disable floating animations
      disableParallax: true,      // Disable parallax effects
      simplifyTransitions: true,  // Use simple fade transitions
    },
  },
} as const;
```

#### 5.4.2 Tailwind Configuration
```typescript
// tailwind.config.ts
import type { Config } from 'tailwindcss';
import { theme } from './src/styles/theme';
import plugin from 'tailwindcss/plugin';

const config: Config = {
  darkMode: ['class'],
  content: [
    './src/pages/**/*.{js,ts,jsx,tsx,mdx}',
    './src/components/**/*.{js,ts,jsx,tsx,mdx}',
    './src/app/**/*.{js,ts,jsx,tsx,mdx}',
  ],
  theme: {
    extend: {
      colors: theme.colors,
      fontFamily: {
        // Manuscript typography system
        'manuscript-display': theme.typography.fonts.manuscript.display,
        'manuscript-body': theme.typography.fonts.manuscript.body,
        'manuscript-ornament': theme.typography.fonts.manuscript.ornament,
        
        // Alchemical typography system
        'alchemical-symbols': theme.typography.fonts.alchemical.symbols,
        'alchemical-measurements': theme.typography.fonts.alchemical.measurements,
        'alchemical-transitions': theme.typography.fonts.alchemical.transitions,
      },
      fontSize: theme.typography.sizes,
      lineHeight: theme.typography.lineHeight,
      spacing: theme.spacing,
      borderRadius: theme.borderRadius,
      boxShadow: theme.shadows,
      transitionDuration: {
        micro: '150ms',
        fast: '300ms',
        base: '500ms',
        slow: '800ms',
        ritual: '1200ms',
      },
      zIndex: theme.zIndex,
      keyframes: {
        // Manuscript animations
        'fade-in': {
          from: { opacity: '0' },
          to: { opacity: '1' },
        },
        'fade-out': {
          from: { opacity: '1' },
          to: { opacity: '0' },
        },
        'slide-in-right': {
          from: { transform: 'translateX(100%)' },
          to: { transform: 'translateX(0)' },
        },
        'slide-out-right': {
          from: { transform: 'translateX(0)' },
          to: { transform: 'translateX(100%)' },
        },
        'slide-in-up': {
          from: { transform: 'translateY(100%)', opacity: '0' },
          to: { transform: 'translateY(0)', opacity: '1' },
        },
        'scale-in': {
          from: { transform: 'scale(0.95)', opacity: '0' },
          to: { transform: 'scale(1)', opacity: '1' },
        },
        
        // Ritual animations
        'rotate-seal': {
          from: { transform: 'rotate(0deg)' },
          to: { transform: 'rotate(360deg)' },
        },
        'float-botanical': {
          '0%, 100%': { transform: 'translateY(0) rotate(0deg)' },
          '50%': { transform: 'translateY(-20px) rotate(5deg)' },
        },
        'liquid-wave': {
          '0%, 100%': { transform: 'translateY(0) scaleY(1)' },
          '50%': { transform: 'translateY(-10px) scaleY(1.05)' },
        },
        'write-scroll': {
          '0%': { opacity: '0', transform: 'translateX(-100%)' },
          '100%': { opacity: '1', transform: 'translateX(0)' },
        },
        'wax-seal': {
          '0%': { 
            transform: 'scale(0) rotate(-180deg)',
            opacity: '0',
          },
          '70%': { 
            transform: 'scale(1.1) rotate(10deg)',
          },
          '100%': { 
            transform: 'scale(1) rotate(0deg)',
            opacity: '1',
          },
        },
        'gold-shimmer': {
          '0%, 100%': { opacity: '0.8' },
          '50%': { opacity: '1' },
        },
        'quill-write': {
          '0%': { strokeDashoffset: '1000' },
          '100%': { strokeDashoffset: '0' },
        },
      },
      animation: {
        // Manuscript animations
        'fade-in': 'fade-in 0.3s ease-out',
        'fade-out': 'fade-out 0.3s ease-out',
        'slide-in-right': 'slide-in-right 0.5s ease-out',
        'slide-out-right': 'slide-out-right 0.5s ease-out',
        'slide-in-up': 'slide-in-up 0.5s ease-out',
        'scale-in': 'scale-in 0.3s ease-out',
        
        // Ritual animations
        'rotate-seal': 'rotate-seal 30s linear infinite',
        'float-botanical': 'float-botanical 6s ease-in-out infinite',
        'liquid-wave': 'liquid-wave 8s ease-in-out infinite',
        'write-scroll': 'write-scroll 2s ease-in-out infinite',
        'wax-seal': 'wax-seal 0.6s cubic-bezier(0.34, 1.56, 0.64, 1)',
        'gold-shimmer': 'gold-shimmer 4s ease-in-out infinite',
        'quill-write': 'quill-write 3s ease-out forwards',
      },
    },
  },
  plugins: [
    require('tailwindcss-animate'),
    require('@tailwindcss/typography'),
    require('@tailwindcss/forms'),
    plugin(({ addUtilities }) => {
      // Manuscript-specific utilities
      addUtilities({
        '.manuscript-text': {
          fontFamily: 'var(--font-manuscript-body)',
          lineHeight: theme.typography.lineHeight.manuscript,
          '@supports (font-variation-settings: "opsz")': {
            fontVariationSettings: '"opsz" 24',
            '@media (min-width: 1024px)': {
              fontVariationSettings: '"opsz" 18',
            },
          },
        },
        '.alchemical-text': {
          fontFamily: 'var(--font-alchemical-symbols)',
          fontSize: theme.typography.sizes['2xl'],
        },
        '.ritual-border': {
          border: '1px dashed var(--color-ink-muted)',
          borderRadius: theme.borderRadius.manuscript,
          padding: theme.spacing.md,
        },
        '.parchment-background': {
          backgroundImage: `url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noiseFilter'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.65' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noiseFilter)'/%3E%3C/svg%3E")`,
          backgroundColor: theme.colors.parchment.DEFAULT,
        },
        '.gold-accent': {
          position: 'relative',
          '&:before': {
            content: '""',
            position: 'absolute',
            top: '0',
            left: '0',
            right: '0',
            bottom: '0',
            background: `linear-gradient(90deg, transparent, ${theme.colors.gold.muted}, transparent)`,
            opacity: '0.3',
            animation: 'gold-shimmer 4s ease-in-out infinite',
          },
        },
      });
    }),
  ],
};

export default config;
```

### 5.5 Routing Structure
```typescript
// config/navigation.ts
export const navigation = {
  main: [
    {
      id: 'compendium',
      label: 'Compendium',
      href: '/compendium',
      number: 'I', // Roman numeral for manuscript authenticity
      description: 'Botanical essences classified by alchemical humours',
      icon: '☽', // Calming humour symbol
    },
    {
      id: 'alchemy',
      label: 'Alchemy',
      href: '/alchemy',
      number: 'II',
      description: 'The four-fold path of botanical transformation',
      icon: '☿', // Alchemical mercury symbol
    },
    {
      id: 'atelier',
      label: 'The Atelier',
      href: '/atelier',
      number: 'III',
      description: 'Meet the artisans and visit our workshop',
      icon: '☽', // Artisan symbol
    },
    {
      id: 'manuscript',
      label: 'Manuscript',
      href: '/manuscript',
      number: 'IV',
      description: 'Illuminated entries on scent and memory',
      icon: '✎', // Quill pen symbol
    },
  ],
  account: [
    { 
      id: 'orders',
      label: 'Dispatch Records', 
      href: '/patron/orders',
      description: 'Your alchemical dispatch history'
    },
    { 
      id: 'addresses', 
      label: 'Correspondence Locations', 
      href: '/patron/addresses',
      description: 'Addresses for dispatch and correspondence'
    },
    { 
      id: 'folios', 
      label: 'Manuscript Subscriptions', 
      href: '/patron/folios', 
      description: 'Your quarterly manuscript subscriptions'
    },
    { 
      id: 'settings', 
      label: 'Patron Settings', 
      href: '/patron/settings',
      description: 'Account preferences and settings'
    },
  ],
  footer: {
    folios: [
      { label: 'Compendium', href: '/compendium', description: 'Essence catalogue' },
      { label: 'Alchemy', href: '/alchemy', description: 'Process and philosophy' },
      { label: 'The Atelier', href: '/atelier', description: 'Our story and craft' },
      { label: 'Manuscript', href: '/manuscript', description: 'Journal and insights' },
    ],
    legal: [
      { label: 'Manuscript Rights', href: '/legal/privacy', description: 'Privacy policy' },
      { label: 'Correspondence Terms', href: '/legal/terms', description: 'Terms of service' },
      { label: 'Atelier Visits', href: '/appointments', description: 'Schedule a visit' },
    ],
    correspondence: [
      { label: 'Quill & Ink', href: 'mailto:correspondence@atelierarome.com', description: 'Email correspondence' },
      { label: 'Telegram', href: 'https://t.me/atelierarome', description: 'Telegram channel' },
    ],
  },
} as const;

export type Navigation = typeof navigation;

// Ritual routing configuration
export const ritualRouting = {
  scrollThresholds: [
    { position: 0.25, folio: 'I', symbol: '☽', section: 'compendium' }, // Calming essences
    { position: 0.50, folio: 'II', symbol: '☿', section: 'alchemy' }, // Alchemical process
    { position: 0.75, folio: 'III', symbol: '♁', section: 'atelier' }, // Atelier wisdom
  ],
  hapticFeedback: {
    sectionTransitions: true,
    interactionPoints: true,
    reducedMotionFallback: 'visual-only',
  },
  audioSpatialization: {
    parchmentRustle: true,
    quillScratching: true,
    liquidPouring: true,
    volume: 0.3,
  },
} as const;
```

---

## 6. Backend Architecture

### 6.1 Service Layer Architecture
```mermaid
flowchart TB
    subgraph ServiceLayer["Service Layer Architecture"]
        direction TB
        
        subgraph APILayer["API LAYER"]
            NextJSAPI[Next.js API Routes + Server Actions]
            NextJSAPI --> APIRoutes
            NextJSAPI --> ServerActions
            NextJSAPI --> RouteHandlers
            NextJSAPI --> RSCFetches
            NextJSAPI --> MiddlewareAuth
            NextJSAPI --> RitualEndpoints[Ritual Endpoints]
        end
        
        subgraph ServiceLayer["SERVICE LAYER"]
            direction TB
            BusinessLogic[Business Logic + Validation + External Service Integration]
            
            subgraph CoreServices["Core Services"]
                ProductService[ProductService]
                OrderService[OrderService]
                UserService[UserService]
                VialService[VialService]
            end
            
            subgraph RitualServices["Ritual Services"]
                ScrollRitualService[ScrollRitualService]
                HapticService[HapticService]
                AudioService[AudioService]
                SensoryService[SensoryService]
            end
            
            subgraph AdditionalServices["Additional Services"]
                SubscriptionService[SubscriptionService]
                EmailService[EmailService]
                InventoryService[InventoryService]
                PaymentService[PaymentService]
                ContentService[ContentService]
            end
        end
        
        subgraph RepositoryLayer["REPOSITORY LAYER"]
            PrismaORM[Prisma ORM + Data Access Patterns]
            PrismaORM --> PrismaClient[Prisma Client]
            PrismaClient --> TypeSafeQueries
            PrismaClient --> Transactions
            PrismaClient --> Migrations
            PrismaORM --> RedisCache[Redis Cache]
        end
        
        APILayer --> ServiceLayer
        ServiceLayer --> RepositoryLayer
    end
```

### 6.2 Service Implementation Examples

#### 6.2.1 Product Service with Ritual Integration
```typescript
// services/product.service.ts
import { prisma } from '@/lib/prisma';
import { redis } from '@/lib/redis';
import { sanity } from '@/lib/sanity';
import type {
  Essence,
  EssenceFilter,
  EssenceSort,
  PaginatedResponse
} from '@/types';
import { triggerRitualEvent } from '@/services/ritual.service';

const CACHE_TTL = 60 * 60; // 1 hour
const CACHE_PREFIX = 'products:';

export class ProductService {
  /**
   * Get all essences with optional filtering, sorting, and pagination
   * Includes ritual metadata for sensory experience
   */
  static async getAll(options: {
    filter?: EssenceFilter;
    sort?: EssenceSort;
    page?: number;
    limit?: number;
    includeRitualData?: boolean; // Include haptic/audio metadata
  }): Promise<PaginatedResponse<Essence[]>> {
    const {
      filter = {},
      sort = { field: 'createdAt', order: 'desc' },
      page = 1,
      limit = 12,
      includeRitualData = false
    } = options;

    // Create cache key with ritual data flag
    const cacheKey = `${CACHE_PREFIX}list:${JSON.stringify({ 
      filter, 
      sort, 
      page, 
      limit,
      includeRitualData
    })}`;
    
    // Check cache first
    const cached = await redis.get<PaginatedResponse<Essence[]>>(cacheKey);
    if (cached) {
      // Trigger ritual event for cache hit
      await triggerRitualEvent('product_list_cached', {
        count: cached.items.length,
        page,
        limit
      });
      return cached;
    }

    // Build where clause with manuscript authenticity
    const where: Prisma.EssenceWhereInput = {
      isActive: true,
      ...(filter.humour && { humour: filter.humour }),
      ...(filter.rarity && { rarity: filter.rarity }),
      ...(filter.season && { season: filter.season }),
      ...(filter.minPrice && { price: { gte: filter.minPrice } }),
      ...(filter.maxPrice && { price: { lte: filter.maxPrice } }),
      ...(filter.inStock && { stockQuantity: { gt: 0 } }),
      // Manuscript authenticity filter
      ...(filter.manuscriptAuthentic && { 
        OR: [
          { extractionMethod: { contains: 'traditional' } },
          { batchNumber: { not: null } },
          { harvestDate: { not: null } }
        ]
      }),
    };

    // Build order by with manuscript-aware sorting
    const orderBy: Prisma.EssenceOrderByWithRelationInput = {
      ...(sort.field === 'folioNumber' 
        ? { folioNumber: 'asc' as const } // Special handling for Roman numerals
        : { [sort.field]: sort.order }),
    };

    // Execute query with count
    const [essences, total] = await prisma.$transaction([
      prisma.essence.findMany({
        where,
        orderBy,
        skip: (page - 1) * limit,
        take: limit,
        include: {
          category: true,
          botanicalInfo: true,
          images: {
            orderBy: { order: 'asc' },
            take: 3 // Limit to 3 images for performance
          },
          // Include ritual metadata if requested
          ...(includeRitualData && {
            ritualMetadata: true
          }),
        },
      }),
      prisma.essence.count({ where }),
    ]);

    // Enrich essences with ritual metadata if requested
    const enrichedEssences = includeRitualData 
      ? await this.enrichWithRitualMetadata(essences)
      : essences;

    const result: PaginatedResponse<Essence[]> = {
      items: enrichedEssences,
      pagination: {
        page,
        limit,
        total,
        totalPages: Math.ceil(total / limit),
        hasMore: page * limit < total,
      },
    };

    // Cache result
    await redis.set(cacheKey, result, { ex: CACHE_TTL });

    // Trigger ritual event for cache miss
    await triggerRitualEvent('product_list_fetched', {
      count: enrichedEssences.length,
      page,
      limit,
      fromCache: false
    });

    return result;
  }

  /**
   * Enrich essences with ritual metadata for multi-sensory experience
   */
  private static async enrichWithRitualMetadata(essences: Essence[]): Promise<Essence[]> {
    return Promise.all(essences.map(async (essence) => {
      // Get ritual metadata from database
      const ritualMetadata = await prisma.essenceRitualMetadata.findUnique({
        where: { essenceId: essence.id }
      });

      // Default ritual metadata if none exists
      const defaultRitual = {
        haptic: {
          frequency: 100 + Math.random() * 200, // Unique frequency per essence
          duration: 100,
          intensity: 50
        },
        audio: {
          pitch: 440 + Math.random() * 200, // Unique pitch per essence
          volume: 0.5,
          spatialization: 0.7
        },
        visual: {
          waveFrequency: 0.5 + Math.random() * 0.5,
          waveAmplitude: 10 + Math.random() * 10,
          colorIntensity: 0.8
        }
      };

      return {
        ...essence,
        ritualMetadata: ritualMetadata || defaultRitual
      };
    }));
  }

  /**
   * Get a single essence by slug with full ritual integration
   */
  static async getBySlug(slug: string, includeRitualData = true): Promise<Essence | null> {
    const cacheKey = `${CACHE_PREFIX}slug:${slug}:${includeRitualData}`;
    // Check cache
    const cached = await redis.get<Essence>(cacheKey);
    if (cached) {
      await triggerRitualEvent('essence_detail_cached', {
        essenceId: cached.id,
        slug
      });
      return cached;
    }

    // Query database with ritual data
    const essenceQuery = prisma.essence.findUnique({
      where: { slug, isActive: true },
      include: {
        category: true,
        botanicalInfo: true,
        images: {
          orderBy: { order: 'asc' }
        },
        relatedEssences: {
          take: 4,
          where: { isActive: true },
          include: { 
            images: { take: 1, orderBy: { order: 'asc' } }
          }
        },
        // Include ritual metadata if requested
        ...(includeRitualData && {
          ritualMetadata: true
        }),
        alchemicalProcess: true, // Historical process documentation
        artisanNotes: true       // Artisan commentary
      },
    });

    // Execute query
    const essence = await essenceQuery;

    if (essence) {
      // Enrich with ritual metadata if requested
      const enrichedEssence = includeRitualData && !essence.ritualMetadata
        ? await this.enrichWithRitualMetadata([essence]).then(results => results[0])
        : essence;

      // Cache enriched result
      await redis.set(cacheKey, enrichedEssence, { ex: CACHE_TTL });

      // Trigger ritual event for essence view
      await triggerRitualEvent('essence_detail_viewed', {
        essenceId: enrichedEssence.id,
        slug,
        fromCache: false,
        ritualEnabled: includeRitualData
      });

      return enrichedEssence;
    }

    return null;
  }

  /**
   * Invalidate product cache
   */
  static async invalidateCache(slug?: string): Promise<void> {
    if (slug) {
      await redis.del(`${CACHE_PREFIX}slug:${slug}:true`);
      await redis.del(`${CACHE_PREFIX}slug:${slug}:false`);
      await triggerRitualEvent('product_cache_invalidated', { slug });
    }
    // Invalidate list caches (pattern delete)
    const keys = await redis.keys(`${CACHE_PREFIX}list:*`);
    if (keys.length > 0) {
      await redis.del(...keys);
      await triggerRitualEvent('product_cache_bulk_invalidated', { count: keys.length });
    }
  }
}
```

#### 6.2.2 Scroll Ritual Service
```typescript
// services/ritual.service.ts
import { redis } from '@/lib/redis';
import type { RitualEvent, RitualConfig } from '@/types/ritual.types';

export class RitualService {
  /**
   * Trigger a ritual event with sensory feedback
   */
  static async triggerRitualEvent(event: RitualEvent, metadata: Record<string, any> = {}): Promise<void> {
    try {
      // Log ritual event for analytics
      await this.logRitualEvent(event, metadata);
      
      // Get user ritual preferences
      const userId = metadata.userId || 'anonymous';
      const ritualConfig = await this.getUserRitualConfig(userId);
      
      // Process event based on config
      if (ritualConfig.enabled) {
        switch (event.type) {
          case 'scroll':
            await this.processScrollEvent(event, ritualConfig, metadata);
            break;
          case 'interaction':
            await this.processInteractionEvent(event, ritualConfig, metadata);
            break;
          case 'transition':
            await this.processTransitionEvent(event, ritualConfig, metadata);
            break;
          case 'notification':
            await this.processNotificationEvent(event, ritualConfig, metadata);
            break;
        }
      }
    } catch (error) {
      console.error('Ritual service error:', error);
      // Never fail the main application flow due to ritual errors
    }
  }

  /**
   * Process scroll ritual events
   */
  private static async processScrollEvent(
    event: RitualEvent, 
    config: RitualConfig, 
    metadata: Record<string, any>
  ): Promise<void> {
    const { position, threshold, direction } = metadata;
    
    // Haptic feedback for scroll thresholds
    if (config.haptics.enabled && threshold && config.haptics.scrollThresholds) {
      const intensity = Math.min(100, Math.max(0, threshold * 100));
      await this.triggerHapticFeedback({
        type: 'scroll-threshold',
        intensity,
        duration: config.haptics.duration || 100
      });
    }
    
    // Audio feedback for scroll position
    if (config.audio.enabled && config.audio.scrollPosition) {
      const volume = Math.min(1, position * config.audio.volume);
      await this.triggerAudioFeedback({
        type: 'scroll-position',
        volume,
        pitch: 440 + (position * 400), // Pitch increases with scroll
        spatialization: 0.7
      });
    }
    
    // Visual feedback for scroll direction
    if (config.visual.enabled && config.visual.scrollDirection) {
      await this.triggerVisualFeedback({
        type: 'scroll-direction',
        direction,
        intensity: 0.3
      });
    }
  }

  /**
   * Trigger haptic feedback
   */
  private static async triggerHapticFeedback(params: {
    type: string;
    intensity: number;
    duration: number;
  }): Promise<void> {
    // Store in Redis for client-side processing
    await redis.rpush('ritual:haptics:queue', JSON.stringify({
      ...params,
      timestamp: Date.now()
    }));
    
    // Set TTL for queue cleanup
    await redis.expire('ritual:haptics:queue', 60);
  }

  /**
   * Trigger audio feedback
   */
  private static async triggerAudioFeedback(params: {
    type: string;
    volume: number;
    pitch: number;
    spatialization: number;
  }): Promise<void> {
    // Store in Redis for client-side processing
    await redis.rpush('ritual:audio:queue', JSON.stringify({
      ...params,
      timestamp: Date.now()
    }));
    
    // Set TTL for queue cleanup
    await redis.expire('ritual:audio:queue', 60);
  }

  /**
   * Trigger visual feedback
   */
  private static async triggerVisualFeedback(params: {
    type: string;
    direction?: 'up' | 'down' | 'left' | 'right';
    intensity: number;
  }): Promise<void> {
    // Store in Redis for client-side processing
    await redis.rpush('ritual:visual:queue', JSON.stringify({
      ...params,
      timestamp: Date.now()
    }));
    
    // Set TTL for queue cleanup
    await redis.expire('ritual:visual:queue', 60);
  }

  /**
   * Get user ritual configuration
   */
  private static async getUserRitualConfig(userId: string): Promise<RitualConfig> {
    // Check cache first
    const cacheKey = `ritual:config:${userId}`;
    const cached = await redis.get<RitualConfig>(cacheKey);
    if (cached) return cached;
    
    // Default config if no user preferences
    const defaultConfig: RitualConfig = {
      enabled: true,
      haptics: {
        enabled: true,
        intensity: 50,
        duration: 100,
        scrollThresholds: true
      },
      audio: {
        enabled: true,
        volume: 0.3,
        scrollPosition: true,
        interactionSounds: true
      },
      visual: {
        enabled: true,
        scrollDirection: true,
        parallax: true,
        floatingElements: true
      },
      reducedMotion: false,
      accessibilityMode: false
    };
    
    // TODO: Fetch from database when user preferences are implemented
    await redis.set(cacheKey, defaultConfig, { ex: 3600 }); // 1 hour cache
    
    return defaultConfig;
  }

  /**
   * Log ritual event for analytics
   */
  private static async logRitualEvent(event: RitualEvent, metadata: Record<string, any>): Promise<void> {
    // Store event in Redis for batch processing
    await redis.rpush('ritual:events:log', JSON.stringify({
      event,
      metadata,
      timestamp: Date.now()
    }));
    
    // Set TTL for log cleanup
    await redis.expire('ritual:events:log', 86400); // 24 hours
  }
}

// Export utility function for ease of use
export const triggerRitualEvent = async (type: string, metadata: Record<string, any> = {}): Promise<void> => {
  await RitualService.triggerRitualEvent({ type, timestamp: Date.now() }, metadata);
};
```

### 6.3 Authentication Configuration with Ritual Integration
```typescript
// lib/auth.ts
import NextAuth from 'next-auth';
import { PrismaAdapter } from '@auth/prisma-adapter';
import CredentialsProvider from 'next-auth/providers/credentials';
import GoogleProvider from 'next-auth/providers/google';
import { prisma } from '@/lib/prisma';
import { compare, hash } from 'bcryptjs';
import { z } from 'zod';
import { triggerRitualEvent } from '@/services/ritual.service';

const loginSchema = z.object({
  email: z.string().email(),
  password: z.string().min(8),
  ritualConsent: z.boolean().optional() // User consent for ritual experience
});

export const {
  handlers: { GET, POST },
  auth,
  signIn,
  signOut,
} = NextAuth({
  adapter: PrismaAdapter(prisma),
  session: {
    strategy: 'jwt',
    maxAge: 30 * 24 * 60 * 60, // 30 days
    updateAge: 24 * 60 * 60, // 24 hours
  },
  pages: {
    signIn: '/login',
    signOut: '/logout',
    error: '/login',
    newUser: '/welcome',
    verifyRequest: '/verify-email',
  },
  providers: [
    CredentialsProvider({
      name: 'credentials',
      credentials: {
        email: { label: 'Email', type: 'email' },
        password: { label: 'Password', type: 'password' },
        ritualConsent: { 
          label: 'Enable ritual experience', 
          type: 'checkbox',
          placeholder: 'Allow haptic and audio feedback for enhanced experience'
        },
      },
      async authorize(credentials) {
        const parsed = loginSchema.safeParse(credentials);
        if (!parsed.success) {
          throw new Error('Invalid credentials');
        }

        const { email, password, ritualConsent = false } = parsed.data;

        const user = await prisma.user.findUnique({
          where: { email },
          select: {
            id: true,
            email: true,
            name: true,
            password: true,
            image: true,
            role: true,
            emailVerified: true,
            ritualPreferences: true, // Include ritual preferences
          },
        });

        if (!user) {
          await triggerRitualEvent('auth_failed', { reason: 'user_not_found', email });
          throw new Error('No user found with this email');
        }

        if (!user.password) {
          await triggerRitualEvent('auth_failed', { reason: 'no_password', userId: user.id });
          throw new Error('User does not have a password set');
        }

        const isValid = await compare(password, user.password);
        if (!isValid) {
          await triggerRitualEvent('auth_failed', { reason: 'invalid_password', userId: user.id });
          throw new Error('Invalid password');
        }

        // Update ritual preferences if consent given
        if (ritualConsent && !user.ritualPreferences?.enabled) {
          await prisma.user.update({
            where: { id: user.id },
            data: {
              ritualPreferences: {
                upsert: {
                  create: { 
                    enabled: true,
                    haptics: { enabled: true },
                    audio: { enabled: true },
                    visual: { enabled: true }
                  },
                  update: { enabled: true }
                }
              }
            }
          });
          
          await triggerRitualEvent('ritual_enabled', { userId: user.id });
        }

        await triggerRitualEvent('auth_success', { 
          userId: user.id, 
          ritualEnabled: ritualConsent,
          role: user.role
        });

        return {
          id: user.id,
          email: user.email,
          name: user.name,
          image: user.image,
          role: user.role,
          ritualPreferences: user.ritualPreferences || { enabled: ritualConsent }
        };
      },
    }),
    GoogleProvider({
      clientId: process.env.GOOGLE_CLIENT_ID!,
      clientSecret: process.env.GOOGLE_CLIENT_SECRET!,
      authorization: {
        params: {
          prompt: 'consent',
          access_type: 'offline',
          response_type: 'code',
          scope: 'openid email profile',
        },
      },
      profile(profile) {
        return {
          id: profile.sub,
          email: profile.email,
          name: profile.name,
          image: profile.picture,
          role: 'customer',
          ritualPreferences: { enabled: false }, // Default to disabled for OAuth
        };
      }
    }),
  ],
  callbacks: {
    async jwt({ token, user, trigger, session }) {
      if (user) {
        token.id = user.id;
        token.role = user.role;
        token.emailVerified = user.emailVerified;
        token.ritualPreferences = user.ritualPreferences;
      }

      if (trigger === 'update' && session) {
        if (session.name) token.name = session.name;
        if (session.email) token.email = session.email;
        
        // Handle ritual preference updates
        if (session.ritualPreferences) {
          token.ritualPreferences = session.ritualPreferences;
          await triggerRitualEvent('ritual_preferences_updated', {
            userId: token.id,
            preferences: session.ritualPreferences
          });
        }
      }

      // Revalidate session periodically and ritual preferences
      if (Date.now() - (token.iat ?? 0) * 1000 > 24 * 60 * 60 * 1000) {
        const freshUser = await prisma.user.findUnique({
          where: { id: token.id as string },
          select: { 
            role: true, 
            emailVerified: true,
            ritualPreferences: true
          },
        });
        if (freshUser) {
          token.role = freshUser.role;
          token.emailVerified = freshUser.emailVerified;
          token.ritualPreferences = freshUser.ritualPreferences;
        }
      }

      return token;
    },
    async session({ session, token }) {
      if (token) {
        session.user.id = token.id as string;
        session.user.role = token.role as string;
        session.user.emailVerified = token.emailVerified as Date | null;
        session.user.ritualPreferences = token.ritualPreferences as any;
      }
      return session;
    },
    async signIn({ user, account, profile }) {
      // Only allow verified email addresses for Google sign-in
      if (account?.provider === 'google' && profile?.email_verified === false) {
        await triggerRitualEvent('auth_blocked', { 
          reason: 'unverified_email', 
          provider: account.provider,
          email: profile.email
        });
        return false;
      }
      
      // Log successful sign-in for ritual tracking
      await triggerRitualEvent('auth_signed_in', {
        userId: user.id,
        provider: account?.provider || 'credentials',
        isNewUser: !user.emailVerified
      });
      
      return true;
    },
  },
  events: {
    async signIn({ user }) {
      // Log successful sign-ins for security monitoring
      await prisma.auditLog.create({
        data: {
          userId: user.id,
          event: 'USER_SIGN_IN',
          metadata: { method: 'password' },
        },
      });
    },
    async createUser({ user }) {
      // Send verification email
      await triggerRitualEvent('user_created', { userId: user.id });
      
      // Log user creation
      await prisma.auditLog.create({
        data: {
          userId: user.id,
          event: 'USER_CREATED',
          metadata: { email: user.email },
        },
      });
    },
    async linkAccount({ user, account }) {
      // Log social account linking
      await prisma.auditLog.create({
        data: {
          userId: user.id,
          event: 'ACCOUNT_LINKED',
          metadata: { provider: account.provider },
        },
      });
      
      await triggerRitualEvent('account_linked', {
        userId: user.id,
        provider: account.provider
      });
    },
  },
  secret: process.env.NEXTAUTH_SECRET,
});

// Type augmentation for NextAuth
declare module 'next-auth' {
  interface Session {
    user: {
      id: string;
      role: string;
      email: string;
      name: string;
      image?: string;
      emailVerified?: Date | null;
      ritualPreferences?: {
        enabled: boolean;
        haptics?: { enabled: boolean };
        audio?: { enabled: boolean };
        visual?: { enabled: boolean };
      };
    };
  }
  interface User {
    role: string;
    emailVerified?: Date | null;
    ritualPreferences?: {
      enabled: boolean;
      haptics?: { enabled: boolean };
      audio?: { enabled: boolean };
      visual?: { enabled: boolean };
    };
  }
}
declare module 'next-auth/jwt' {
  interface JWT {
    id: string;
    role: string;
    emailVerified?: Date | null;
    ritualPreferences?: {
      enabled: boolean;
      haptics?: { enabled: boolean };
      audio?: { enabled: boolean };
      visual?: { enabled: boolean };
    };
  }
}
```

---

## 7. Data Architecture

### 7.1 Entity Relationship Diagram
```mermaid
erDiagram
    USER ||--o{ ORDER : "places"
    USER ||--o{ ADDRESS : "has"
    USER ||--o{ SUBSCRIPTION : "subscribes_to"
    USER ||--o{ VIAL : "maintains"
    USER ||--o{ RITUAL_PREFERENCE : "configures"
    
    USER {
        string id PK
        string email
        string name
        string password
        string role
        datetime createdAt
        datetime updatedAt
        datetime emailVerified
        string image
        json ritualPreferences
    }
    
    ADDRESS {
        string id PK
        string userId FK
        string type
        string street
        string city
        string state
        string postalCode
        string country
        boolean isDefault
        datetime createdAt
        datetime updatedAt
    }
    
    ORDER ||--o{ ORDER_ITEM : "contains"
    ORDER ||--o{ PAYMENT : "has"
    ORDER ||--o{ SHIPMENT : "has"
    
    ORDER {
        string id PK
        string orderNumber
        string userId FK
        string stripePaymentIntentId
        decimal subtotal
        decimal shippingCost
        decimal taxAmount
        decimal total
        string currency
        string status
        datetime paidAt
        datetime shippedAt
        datetime deliveredAt
        datetime createdAt
        datetime updatedAt
        json metadata
    }
    
    ORDER_ITEM {
        string id PK
        string orderId FK
        string essenceId FK
        integer quantity
        decimal unitPrice
        decimal totalPrice
        datetime createdAt
        datetime updatedAt
    }
    
    ESSENCE ||--o{ ORDER_ITEM : "sold_in"
    ESSENCE ||--o{ ESSENCE_IMAGE : "has"
    ESSENCE ||--o{ ESSENCE_RITUAL_METADATA : "configured_with"
    ESSENCE ||--o{ BOTANICAL_INFO : "described_by"
    
    ESSENCE {
        string id PK
        string folioNumber
        string slug
        string latinName
        string commonName
        string description
        string humour
        string rarity
        string season
        string extractionMethod
        string[] notes
        decimal price
        integer volumeMl
        integer stockQuantity
        boolean isActive
        string batchNumber
        datetime harvestDate
        integer distillationHours
        datetime createdAt
        datetime updatedAt
    }
    
    ESSENCE_IMAGE {
        string id PK
        string essenceId FK
        string url
        string altText
        integer width
        integer height
        integer order
        datetime createdAt
    }
    
    ESSENCE_RITUAL_METADATA {
        string id PK
        string essenceId FK
        json haptic
        json audio
        json visual
        datetime createdAt
        datetime updatedAt
    }
    
    BOTANICAL_INFO {
        string id PK
        string essenceId FK
        string origin
        string cultivationMethod
        string historicalNotes
        string chemicalComposition
        json sustainabilityInfo
        datetime createdAt
        datetime updatedAt
    }
    
    SUBSCRIPTION {
        string id PK
        string userId FK
        string stripeSubscriptionId
        string status
        string plan
        decimal price
        datetime startDate
        datetime nextBillingDate
        datetime cancelledAt
        datetime createdAt
        datetime updatedAt
        json metadata
    }
    
    VIAL {
        string id PK
        string userId FK
        string sessionId
        json items
        datetime expiresAt
        datetime createdAt
        datetime updatedAt
    }
    
    VIAL_ITEM {
        string id PK
        string vialId FK
        string essenceId FK
        integer quantity
        datetime addedAt
    }
    
    AL_CHEMICAL_PROCESS {
        string id PK
        string essenceId FK
        string stepNumber
        string title
        string description
        string illustrationUrl
        datetime createdAt
        datetime updatedAt
    }
    
    ARTISAN_NOTE {
        string id PK
        string essenceId FK
        string artisanId
        string content
        datetime createdAt
        datetime updatedAt
    }
    
    TESTIMONIAL {
        string id PK
        string userId FK
        string author
        string title
        string quote
        string folioEntry
        boolean verified
        boolean illuminated
        boolean featured
        integer order
        datetime approvedAt
        datetime publishedAt
        datetime createdAt
        datetime updatedAt
    }
    
    FOLIO {
        string id PK
        string title
        string slug
        string edition
        json content
        string excerpt
        string status
        datetime sentAt
        float openRate
        float clickRate
        datetime createdAt
        datetime updatedAt
        datetime publishedAt
    }
    
    RITUAL_PREFERENCE {
        string id PK
        string userId FK
        boolean enabled
        json haptics
        json audio
        json visual
        boolean reducedMotion
        boolean accessibilityMode
        datetime createdAt
        datetime updatedAt
    }
    
    AUDIT_LOG {
        string id PK
        string userId FK
        string event
        json metadata
        datetime createdAt
    }
```

### 7.2 Database Schema (DDL)
```sql
-- Users Table
CREATE TABLE "User" (
  "id" TEXT NOT NULL PRIMARY KEY,
  "email" TEXT NOT NULL,
  "name" TEXT,
  "password" TEXT,
  "role" TEXT NOT NULL DEFAULT 'customer',
  "emailVerified" DATETIME,
  "image" TEXT,
  "createdAt" DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  "updatedAt" DATETIME NOT NULL,
  "ritualPreferences" JSONB DEFAULT '{"enabled": false}'
);

CREATE UNIQUE INDEX "User_email_key" ON "User"("email");

-- Ritual Preferences Table
CREATE TABLE "RitualPreference" (
  "id" TEXT NOT NULL PRIMARY KEY,
  "userId" TEXT NOT NULL,
  "enabled" BOOLEAN NOT NULL DEFAULT false,
  "haptics" JSONB DEFAULT '{"enabled": false}',
  "audio" JSONB DEFAULT '{"enabled": false}',
  "visual" JSONB DEFAULT '{"enabled": false}',
  "reducedMotion" BOOLEAN NOT NULL DEFAULT false,
  "accessibilityMode" BOOLEAN NOT NULL DEFAULT false,
  "createdAt" DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  "updatedAt" DATETIME NOT NULL,
  CONSTRAINT "RitualPreference_userId_fkey" FOREIGN KEY ("userId") REFERENCES "User"("id") ON DELETE CASCADE ON UPDATE CASCADE
);

CREATE UNIQUE INDEX "RitualPreference_userId_key" ON "RitualPreference"("userId");

-- Addresses Table
CREATE TABLE "Address" (
  "id" TEXT NOT NULL PRIMARY KEY,
  "userId" TEXT NOT NULL,
  "type" TEXT NOT NULL DEFAULT 'shipping',
  "street" TEXT NOT NULL,
  "city" TEXT NOT NULL,
  "state" TEXT,
  "postalCode" TEXT NOT NULL,
  "country" TEXT NOT NULL,
  "isDefault" BOOLEAN NOT NULL DEFAULT false,
  "createdAt" DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  "updatedAt" DATETIME NOT NULL,
  CONSTRAINT "Address_userId_fkey" FOREIGN KEY ("userId") REFERENCES "User"("id") ON DELETE CASCADE ON UPDATE CASCADE
);

-- Essences Table
CREATE TABLE "Essence" (
  "id" TEXT NOT NULL PRIMARY KEY,
  "folioNumber" TEXT NOT NULL, -- Roman numerals: I, II, III
  "slug" TEXT NOT NULL,
  "latinName" TEXT NOT NULL,
  "commonName" TEXT NOT NULL,
  "description" TEXT NOT NULL,
  "humour" TEXT NOT NULL CHECK ("humour" IN ('CALMING', 'UPLIFTING', 'GROUNDING', 'CLARIFYING')),
  "rarity" TEXT NOT NULL CHECK ("rarity" IN ('COMMON', 'RARE', 'LIMITED')),
  "season" TEXT NOT NULL CHECK ("season" IN ('SPRING', 'SUMMER', 'AUTUMN', 'WINTER')),
  "extractionMethod" TEXT NOT NULL,
  "notes" TEXT[] NOT NULL DEFAULT ARRAY[]::TEXT[],
  "price" DECIMAL(10,2) NOT NULL,
  "volumeMl" INTEGER NOT NULL DEFAULT 5,
  "stockQuantity" INTEGER NOT NULL DEFAULT 0,
  "isActive" BOOLEAN NOT NULL DEFAULT true,
  "batchNumber" TEXT,
  "harvestDate" DATETIME,
  "distillationHours" INTEGER,
  "createdAt" DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  "updatedAt" DATETIME NOT NULL
);

CREATE UNIQUE INDEX "Essence_slug_key" ON "Essence"("slug");
CREATE UNIQUE INDEX "Essence_folioNumber_key" ON "Essence"("folioNumber");
CREATE INDEX "Essence_humour_idx" ON "Essence"("humour");
CREATE INDEX "Essence_rarity_idx" ON "Essence"("rarity");
CREATE INDEX "Essence_season_idx" ON "Essence"("season");
CREATE INDEX "Essence_price_idx" ON "Essence"("price");
CREATE INDEX "Essence_createdAt_idx" ON "Essence"("createdAt" DESC);

-- Essence Images Table
CREATE TABLE "EssenceImage" (
  "id" TEXT NOT NULL PRIMARY KEY,
  "essenceId" TEXT NOT NULL,
  "url" TEXT NOT NULL,
  "altText" TEXT,
  "width" INTEGER NOT NULL,
  "height" INTEGER NOT NULL,
  "order" INTEGER NOT NULL DEFAULT 0,
  "createdAt" DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  CONSTRAINT "EssenceImage_essenceId_fkey" FOREIGN KEY ("essenceId") REFERENCES "Essence"("id") ON DELETE CASCADE ON UPDATE CASCADE
);

CREATE INDEX "EssenceImage_essenceId_order_idx" ON "EssenceImage"("essenceId", "order");

-- Essence Ritual Metadata Table
CREATE TABLE "EssenceRitualMetadata" (
  "id" TEXT NOT NULL PRIMARY KEY,
  "essenceId" TEXT NOT NULL,
  "haptic" JSONB NOT NULL DEFAULT '{"frequency": 150, "duration": 100, "intensity": 50}',
  "audio" JSONB NOT NULL DEFAULT '{"pitch": 440, "volume": 0.5, "spatialization": 0.7}',
  "visual" JSONB NOT NULL DEFAULT '{"waveFrequency": 0.7, "waveAmplitude": 15, "colorIntensity": 0.8}',
  "createdAt" DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  "updatedAt" DATETIME NOT NULL,
  CONSTRAINT "EssenceRitualMetadata_essenceId_fkey" FOREIGN KEY ("essenceId") REFERENCES "Essence"("id") ON DELETE CASCADE ON UPDATE CASCADE
);

CREATE UNIQUE INDEX "EssenceRitualMetadata_essenceId_key" ON "EssenceRitualMetadata"("essenceId");

-- Botanical Info Table
CREATE TABLE "BotanicalInfo" (
  "id" TEXT NOT NULL PRIMARY KEY,
  "essenceId" TEXT NOT NULL,
  "origin" TEXT NOT NULL,
  "cultivationMethod" TEXT NOT NULL,
  "historicalNotes" TEXT,
  "chemicalComposition" TEXT,
  "sustainabilityInfo" JSONB,
  "createdAt" DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  "updatedAt" DATETIME NOT NULL,
  CONSTRAINT "BotanicalInfo_essenceId_fkey" FOREIGN KEY ("essenceId") REFERENCES "Essence"("id") ON DELETE CASCADE ON UPDATE CASCADE
);

CREATE UNIQUE INDEX "BotanicalInfo_essenceId_key" ON "BotanicalInfo"("essenceId");

-- Vials Table (Cart)
CREATE TABLE "Vial" (
  "id" TEXT NOT NULL PRIMARY KEY,
  "userId" TEXT,
  "sessionId" TEXT,
  "items" JSONB NOT NULL DEFAULT '[]',
  "expiresAt" DATETIME,
  "createdAt" DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  "updatedAt" DATETIME NOT NULL,
  CONSTRAINT "Vial_userId_fkey" FOREIGN KEY ("userId") REFERENCES "User"("id") ON DELETE SET NULL ON UPDATE CASCADE
);

CREATE INDEX "Vial_sessionId_idx" ON "Vial"("sessionId");
CREATE INDEX "Vial_expiresAt_idx" ON "Vial"("expiresAt") WHERE "expiresAt" IS NOT NULL;

-- Orders Table
CREATE TABLE "Order" (
  "id" TEXT NOT NULL PRIMARY KEY,
  "orderNumber" TEXT NOT NULL,
  "userId" TEXT NOT NULL,
  "stripePaymentIntentId" TEXT,
  "subtotal" DECIMAL(10,2) NOT NULL,
  "shippingCost" DECIMAL(10,2) NOT NULL,
  "taxAmount" DECIMAL(10,2) NOT NULL DEFAULT 0,
  "total" DECIMAL(10,2) NOT NULL,
  "currency" TEXT NOT NULL DEFAULT 'EUR',
  "status" TEXT NOT NULL DEFAULT 'PENDING_PAYMENT' CHECK ("status" IN ('DRAFT', 'PENDING', 'CONFIRMED', 'DISPATCHED', 'COMPLETED', 'CANCELLED')),
  "paidAt" DATETIME,
  "shippedAt" DATETIME,
  "deliveredAt" DATETIME,
  "createdAt" DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  "updatedAt" DATETIME NOT NULL,
  "metadata" JSONB,
  CONSTRAINT "Order_userId_fkey" FOREIGN KEY ("userId") REFERENCES "User"("id") ON DELETE RESTRICT ON UPDATE CASCADE
);

CREATE UNIQUE INDEX "Order_orderNumber_key" ON "Order"("orderNumber");
CREATE UNIQUE INDEX "Order_stripePaymentIntentId_key" ON "Order"("stripePaymentIntentId");
CREATE INDEX "Order_userId_status_idx" ON "Order"("userId", "status");
CREATE INDEX "Order_createdAt_idx" ON "Order"("createdAt" DESC);

-- Order Items Table
CREATE TABLE "OrderItem" (
  "id" TEXT NOT NULL PRIMARY KEY,
  "orderId" TEXT NOT NULL,
  "essenceId" TEXT NOT NULL,
  "quantity" INTEGER NOT NULL,
  "unitPrice" DECIMAL(10,2) NOT NULL,
  "totalPrice" DECIMAL(10,2) NOT NULL,
  "createdAt" DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  "updatedAt" DATETIME NOT NULL,
  CONSTRAINT "OrderItem_orderId_fkey" FOREIGN KEY ("orderId") REFERENCES "Order"("id") ON DELETE CASCADE ON UPDATE CASCADE,
  CONSTRAINT "OrderItem_essenceId_fkey" FOREIGN KEY ("essenceId") REFERENCES "Essence"("id") ON DELETE RESTRICT ON UPDATE CASCADE
);

CREATE INDEX "OrderItem_orderId_idx" ON "OrderItem"("orderId");
CREATE INDEX "OrderItem_essenceId_idx" ON "OrderItem"("essenceId");

-- Subscriptions Table
CREATE TABLE "Subscription" (
  "id" TEXT NOT NULL PRIMARY KEY,
  "userId" TEXT NOT NULL,
  "stripeSubscriptionId" TEXT NOT NULL,
  "status" TEXT NOT NULL CHECK ("status" IN ('ACTIVE', 'PAUSED', 'CANCELLED', 'PAST_DUE')),
  "plan" TEXT NOT NULL CHECK ("plan" IN ('QUARTERLY', 'ANNUAL')),
  "price" DECIMAL(10,2) NOT NULL,
  "startDate" DATETIME NOT NULL,
  "nextBillingDate" DATETIME NOT NULL,
  "cancelledAt" DATETIME,
  "createdAt" DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  "updatedAt" DATETIME NOT NULL,
  "metadata" JSONB,
  CONSTRAINT "Subscription_userId_fkey" FOREIGN KEY ("userId") REFERENCES "User"("id") ON DELETE CASCADE ON UPDATE CASCADE
);

CREATE UNIQUE INDEX "Subscription_stripeSubscriptionId_key" ON "Subscription"("stripeSubscriptionId");
CREATE INDEX "Subscription_userId_status_idx" ON "Subscription"("userId", "status");
CREATE INDEX "Subscription_nextBillingDate_idx" ON "Subscription"("nextBillingDate");

-- Alchemical Process Table
CREATE TABLE "AlchemicalProcess" (
  "id" TEXT NOT NULL PRIMARY KEY,
  "essenceId" TEXT NOT NULL,
  "stepNumber" INTEGER NOT NULL,
  "title" TEXT NOT NULL,
  "description" TEXT NOT NULL,
  "illustrationUrl" TEXT,
  "createdAt" DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  "updatedAt" DATETIME NOT NULL,
  CONSTRAINT "AlchemicalProcess_essenceId_fkey" FOREIGN KEY ("essenceId") REFERENCES "Essence"("id") ON DELETE CASCADE ON UPDATE CASCADE
);

CREATE INDEX "AlchemicalProcess_essenceId_stepNumber_idx" ON "AlchemicalProcess"("essenceId", "stepNumber");

-- Artisan Notes Table
CREATE TABLE "ArtisanNote" (
  "id" TEXT NOT NULL PRIMARY KEY,
  "essenceId" TEXT NOT NULL,
  "artisanId" TEXT NOT NULL,
  "content" TEXT NOT NULL,
  "createdAt" DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  "updatedAt" DATETIME NOT NULL,
  CONSTRAINT "ArtisanNote_essenceId_fkey" FOREIGN KEY ("essenceId") REFERENCES "Essence"("id") ON DELETE CASCADE ON UPDATE CASCADE,
  CONSTRAINT "ArtisanNote_artisanId_fkey" FOREIGN KEY ("artisanId") REFERENCES "User"("id") ON DELETE CASCADE ON UPDATE CASCADE
);

CREATE INDEX "ArtisanNote_essenceId_idx" ON "ArtisanNote"("essenceId");
CREATE INDEX "ArtisanNote_artisanId_idx" ON "ArtisanNote"("artisanId");

-- Testimonials Table
CREATE TABLE "Testimonial" (
  "id" TEXT NOT NULL PRIMARY KEY,
  "userId" TEXT,
  "author" TEXT NOT NULL,
  "title" TEXT NOT NULL,
  "quote" TEXT NOT NULL,
  "folioEntry" TEXT,
  "verified" BOOLEAN NOT NULL DEFAULT false,
  "illuminated" BOOLEAN NOT NULL DEFAULT false,
  "featured" BOOLEAN NOT NULL DEFAULT false,
  "order" INTEGER NOT NULL DEFAULT 0,
  "approvedAt" DATETIME,
  "publishedAt" DATETIME,
  "createdAt" DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  "updatedAt" DATETIME NOT NULL,
  CONSTRAINT "Testimonial_userId_fkey" FOREIGN KEY ("userId") REFERENCES "User"("id") ON DELETE SET NULL ON UPDATE CASCADE
);

CREATE INDEX "Testimonial_publishedAt_idx" ON "Testimonial"("publishedAt");
CREATE INDEX "Testimonial_featured_idx" ON "Testimonial"("featured");
CREATE INDEX "Testimonial_order_idx" ON "Testimonial"("order");

-- Folios Table (Manuscript Subscriptions)
CREATE TABLE "Folio" (
  "id" TEXT NOT NULL PRIMARY KEY,
  "title" TEXT NOT NULL,
  "slug" TEXT NOT NULL,
  "edition" TEXT NOT NULL, -- e.g., "Spring Equinox MMXXIV"
  "content" JSONB NOT NULL,
  "excerpt" TEXT,
  "status" TEXT NOT NULL DEFAULT 'DRAFT' CHECK ("status" IN ('DRAFT', 'SCHEDULED', 'SENDING', 'SENT', 'ARCHIVED')),
  "sentAt" DATETIME,
  "openRate" DECIMAL(5,2),
  "clickRate" DECIMAL(5,2),
  "createdAt" DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  "updatedAt" DATETIME NOT NULL,
  "publishedAt" DATETIME
);

CREATE UNIQUE INDEX "Folio_slug_key" ON "Folio"("slug");
CREATE INDEX "Folio_publishedAt_idx" ON "Folio"("publishedAt");
CREATE INDEX "Folio_status_idx" ON "Folio"("status");

-- Audit Log Table
CREATE TABLE "AuditLog" (
  "id" TEXT NOT NULL PRIMARY KEY,
  "userId" TEXT,
  "event" TEXT NOT NULL,
  "metadata" JSONB,
  "createdAt" DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  CONSTRAINT "AuditLog_userId_fkey" FOREIGN KEY ("userId") REFERENCES "User"("id") ON DELETE SET NULL ON UPDATE CASCADE
);

CREATE INDEX "AuditLog_createdAt_idx" ON "AuditLog"("createdAt" DESC);
CREATE INDEX "AuditLog_event_idx" ON "AuditLog"("event");
```

### 7.3 Prisma Schema
```prisma
// prisma/schema.prisma
generator client {
  provider = "prisma-client-js"
  previewFeatures = ["fullTextSearch", "relationJoins"]
}

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

model User {
  id             String    @id @default(auto()) @map("_id")
  email          String    @unique
  name           String?
  password       String?
  role           String    @default("customer")
  emailVerified  DateTime?
  image          String?
  createdAt      DateTime  @default(now())
  updatedAt      DateTime  @updatedAt
  ritualPreferences Json?  @default("{\"enabled\": false}")

  addresses      Address[]
  orders         Order[]
  subscriptions  Subscription[]
  vial           Vial?
  testimonials   Testimonial[]
  artisanNotes   ArtisanNote[]
  ritualPreference RitualPreference?

  @@map("User")
}

model RitualPreference {
  id             String  @id @default(auto()) @map("_id")
  userId         String  @unique
  user           User    @relation(fields: [userId], references: [id], onDelete: Cascade)
  enabled        Boolean @default(false)
  haptics        Json?   @default("{\"enabled\": false}")
  audio          Json?   @default("{\"enabled\": false}")
  visual         Json?   @default("{\"enabled\": false}")
  reducedMotion  Boolean @default(false)
  accessibilityMode Boolean @default(false)
  createdAt      DateTime @default(now())
  updatedAt      DateTime @updatedAt

  @@map("RitualPreference")
}

model Address {
  id          String   @id @default(auto()) @map("_id")
  userId      String
  user        User     @relation(fields: [userId], references: [id], onDelete: Cascade)
  type        String   @default("shipping")
  street      String
  city        String
  state       String?
  postalCode  String
  country     String
  isDefault   Boolean  @default(false)
  createdAt   DateTime @default(now())
  updatedAt   DateTime @updatedAt

  @@map("Address")
}

model Essence {
  id               String            @id @default(auto()) @map("_id")
  folioNumber      String            @unique // Roman numerals: I, II, III
  slug             String            @unique
  latinName        String
  commonName       String
  description      String
  humour           HumourType
  rarity           RarityType
  season           SeasonType
  extractionMethod String
  notes            String[]
  price            Decimal @db.Decimal(10, 2)
  volumeMl         Int     @default(5)
  stockQuantity    Int     @default(0)
  isActive         Boolean @default(true)
  batchNumber      String?
  harvestDate      DateTime?
  distillationHours Int?
  createdAt        DateTime @default(now())
  updatedAt        DateTime @updatedAt

  images           EssenceImage[]
  ritualMetadata   EssenceRitualMetadata?
  botanicalInfo    BotanicalInfo?
  orderItems       OrderItem[]
  alchemicalProcess AlchemicalProcess[]
  artisanNotes     ArtisanNote[]
  testimonials     Testimonial[]

  @@map("Essence")
  @@index([humour])
  @@index([rarity])
  @@index([season])
  @@index([price])
  @@index([createdAt])
}

enum HumourType {
  CALMING
  UPLIFTING
  GROUNDING
  CLARIFYING
}

enum RarityType {
  COMMON
  RARE
  LIMITED
}

enum SeasonType {
  SPRING
  SUMMER
  AUTUMN
  WINTER
}

model EssenceImage {
  id        String   @id @default(auto()) @map("_id")
  essenceId String
  essence   Essence  @relation(fields: [essenceId], references: [id], onDelete: Cascade)
  url       String
  altText   String?
  width     Int
  height    Int
  order     Int      @default(0)
  createdAt DateTime @default(now())

  @@map("EssenceImage")
  @@index([essenceId, order])
}

model EssenceRitualMetadata {
  id        String   @id @default(auto()) @map("_id")
  essenceId String   @unique
  essence   Essence  @relation(fields: [essenceId], references: [id], onDelete: Cascade)
  haptic    Json     @default("{\"frequency\": 150, \"duration\": 100, \"intensity\": 50}")
  audio     Json     @default("{\"pitch\": 440, \"volume\": 0.5, \"spatialization\": 0.7}")
  visual    Json     @default("{\"waveFrequency\": 0.7, \"waveAmplitude\": 15, \"colorIntensity\": 0.8}")
  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt

  @@map("EssenceRitualMetadata")
}

model BotanicalInfo {
  id                 String   @id @default(auto()) @map("_id")
  essenceId          String   @unique
  essence            Essence  @relation(fields: [essenceId], references: [id], onDelete: Cascade)
  origin             String
  cultivationMethod  String
  historicalNotes    String?
  chemicalComposition String?
  sustainabilityInfo Json?
  createdAt          DateTime @default(now())
  updatedAt          DateTime @updatedAt

  @@map("BotanicalInfo")
}

model Vial {
  id         String    @id @default(auto()) @map("_id")
  userId     String?
  user       User?     @relation(fields: [userId], references: [id], onDelete: SetNull)
  sessionId  String?
  items      Json      @default("[]")
  expiresAt  DateTime?
  createdAt  DateTime  @default(now())
  updatedAt  DateTime  @updatedAt

  @@map("Vial")
  @@index([sessionId])
  @@index([expiresAt])
}

model Order {
  id                 String         @id @default(auto()) @map("_id")
  orderNumber        String         @unique
  userId             String
  user               User           @relation(fields: [userId], references: [id])
  stripePaymentIntentId String?
  subtotal           Decimal        @db.Decimal(10, 2)
  shippingCost       Decimal        @db.Decimal(10, 2)
  taxAmount          Decimal        @db.Decimal(10, 2) @default(0)
  total              Decimal        @db.Decimal(10, 2)
  currency           String         @default("EUR")
  status             OrderStatus    @default(PENDING_PAYMENT)
  paidAt             DateTime?
  shippedAt          DateTime?
  deliveredAt        DateTime?
  createdAt          DateTime       @default(now())
  updatedAt          DateTime       @updatedAt
  metadata           Json?

  items              OrderItem[]
  payments           Payment[]
  shipments          Shipment[]

  @@map("Order")
  @@index([userId, status])
  @@index([createdAt])
}

enum OrderStatus {
  DRAFT
  PENDING
  CONFIRMED
  DISPATCHED
  COMPLETED
  CANCELLED
}

model OrderItem {
  id         String   @id @default(auto()) @map("_id")
  orderId    String
  order      Order    @relation(fields: [orderId], references: [id], onDelete: Cascade)
  essenceId  String
  essence    Essence  @relation(fields: [essenceId], references: [id])
  quantity   Int
  unitPrice  Decimal  @db.Decimal(10, 2)
  totalPrice Decimal  @db.Decimal(10, 2)
  createdAt  DateTime @default(now())
  updatedAt  DateTime @updatedAt

  @@map("OrderItem")
  @@index([orderId])
  @@index([essenceId])
}

model Subscription {
  id                String          @id @default(auto()) @map("_id")
  userId            String
  user              User            @relation(fields: [userId], references: [id], onDelete: Cascade)
  stripeSubscriptionId String        @unique
  status            SubscriptionStatus @default(ACTIVE)
  plan              SubscriptionPlan @default(QUARTERLY)
  price             Decimal         @db.Decimal(10, 2)
  startDate         DateTime
  nextBillingDate   DateTime
  cancelledAt       DateTime?
  createdAt         DateTime        @default(now())
  updatedAt         DateTime        @updatedAt
  metadata          Json?

  @@map("Subscription")
  @@index([userId, status])
  @@index([nextBillingDate])
}

enum SubscriptionStatus {
  ACTIVE
  PAUSED
  CANCELLED
  PAST_DUE
}

enum SubscriptionPlan {
  QUARTERLY
  ANNUAL
}

model AlchemicalProcess {
  id            String   @id @default(auto()) @map("_id")
  essenceId     String
  essence       Essence  @relation(fields: [essenceId], references: [id], onDelete: Cascade)
  stepNumber    Int
  title         String
  description   String
  illustrationUrl String?
  createdAt     DateTime @default(now())
  updatedAt     DateTime @updatedAt

  @@map("AlchemicalProcess")
  @@index([essenceId, stepNumber])
}

model ArtisanNote {
  id         String   @id @default(auto()) @map("_id")
  essenceId  String
  essence    Essence  @relation(fields: [essenceId], references: [id], onDelete: Cascade)
  artisanId  String
  artisan    User     @relation(fields: [artisanId], references: [id], onDelete: Cascade)
  content    String
  createdAt  DateTime @default(now())
  updatedAt  DateTime @updatedAt

  @@map("ArtisanNote")
  @@index([essenceId])
  @@index([artisanId])
}

model Testimonial {
  id            String   @id @default(auto()) @map("_id")
  userId        String?
  user          User?    @relation(fields: [userId], references: [id], onDelete: SetNull)
  author        String
  title         String
  quote         String   @db.Text
  folioEntry    String?
  verified      Boolean  @default(false)
  illuminated   Boolean  @default(false)
  featured      Boolean  @default(false)
  order         Int      @default(0)
  approvedAt    DateTime?
  publishedAt   DateTime?
  createdAt     DateTime @default(now())
  updatedAt     DateTime @updatedAt

  @@map("Testimonial")
  @@index([publishedAt])
  @@index([featured])
  @@index([order])
}

model Folio {
  id           String          @id @default(auto()) @map("_id")
  title        String
  slug         String          @unique
  edition      String          // e.g., "Spring Equinox MMXXIV"
  content      Json
  excerpt      String?
  status       FolioStatus     @default(DRAFT)
  sentAt       DateTime?
  openRate     Float?          @db.Decimal(5, 2)
  clickRate    Float?          @db.Decimal(5, 2)
  createdAt    DateTime        @default(now())
  updatedAt    DateTime        @updatedAt
  publishedAt  DateTime?

  @@map("Folio")
  @@index([publishedAt])
  @@index([status])
}

enum FolioStatus {
  DRAFT
  SCHEDULED
  SENDING
  SENT
  ARCHIVED
}

model AuditLog {
  id        String   @id @default(auto()) @map("_id")
  userId    String?
  user      User?    @relation(fields: [userId], references: [id], onDelete: SetNull)
  event     String
  metadata  Json?
  createdAt DateTime @default(now())

  @@map("AuditLog")
  @@index([createdAt])
  @@index([event])
}
```

### 7.4 Data Access Patterns
```typescript
// lib/prisma.ts - Prisma Client Singleton with Ritual Instrumentation
import { PrismaClient } from '@prisma/client'
import { triggerRitualEvent } from '@/services/ritual.service'

declare global {
  var prisma: PrismaClient | undefined
}

export const prisma = 
  global.prisma ||
  new PrismaClient({
    log: process.env.NODE_ENV === 'development' 
      ? ['query', 'error', 'warn'] 
      : ['error'],
    errorFormat: 'pretty',
    // Add custom instrumentation for ritual events
    hooks: {
      beforeRequest: async (context) => {
        // Log slow queries for performance monitoring
        if (context.query?.startsWith('SELECT') && context.args?.take && context.args.take > 100) {
          await triggerRitualEvent('database_query_start', {
            operation: context.query.split(' ')[0],
            model: context.model,
            count: context.args.take,
            timestamp: Date.now()
          });
        }
      },
      afterResponse: async (context) => {
        // Track query performance
        const duration = Date.now() - (context.timestamp || Date.now());
        if (duration > 100) {
          await triggerRitualEvent('database_query_slow', {
            operation: context.query?.split(' ')[0],
            model: context.model,
            duration,
            timestamp: Date.now()
          });
        }
      }
    }
  })

if (process.env.NODE_ENV !== 'production') global.prisma = prisma
```

### 7.5 Indexing Strategy
```sql
-- Performance Indexing Strategy for Atelier Arôme
-- Created: 2024
-- Purpose: Optimize query performance for high-traffic operations

-- Orders Table Indexes
CREATE INDEX "Order_userId_status_idx" ON "Order"("userId", "status");
CREATE INDEX "Order_createdAt_idx" ON "Order"("createdAt" DESC);
CREATE INDEX "Order_status_idx" ON "Order"("status");

-- Essences Table Indexes
CREATE INDEX "Essence_slug_active_idx" ON "Essence"("slug", "isActive");
CREATE INDEX "Essence_humour_rarity_season_idx" ON "Essence"("humour", "rarity", "season");
CREATE INDEX "Essence_price_idx" ON "Essence"("price");
CREATE INDEX "Essence_createdAt_idx" ON "Essence"("createdAt" DESC);
CREATE INDEX "Essence_manuscript_authentic_idx" ON "Essence"("batchNumber", "harvestDate", "distillationHours") 
WHERE "batchNumber" IS NOT NULL OR "harvestDate" IS NOT NULL OR "distillationHours" IS NOT NULL;

-- Users Table Indexes
CREATE INDEX "User_email_verified_idx" ON "User"("email", "emailVerified");
CREATE INDEX "User_createdAt_idx" ON "User"("createdAt" DESC);
CREATE INDEX "User_role_idx" ON "User"("role");

-- Order Items Table Indexes
CREATE INDEX "OrderItem_orderId_idx" ON "OrderItem"("orderId");
CREATE INDEX "OrderItem_essenceId_idx" ON "OrderItem"("essenceId");

-- Subscriptions Table Indexes
CREATE INDEX "Subscription_userId_status_idx" ON "Subscription"("userId", "status");
CREATE INDEX "Subscription_nextBillingDate_idx" ON "Subscription"("nextBillingDate");

-- Testimonials Table Indexes
CREATE INDEX "Testimonial_isFeatured_idx" ON "Testimonial"("featured", "createdAt" DESC);
CREATE INDEX "Testimonial_userId_idx" ON "Testimonial"("userId");

-- Ritual Preferences Indexes
CREATE INDEX "RitualPreference_userId_idx" ON "RitualPreference"("userId");
CREATE INDEX "RitualPreference_enabled_idx" ON "RitualPreference"("enabled");

-- Full-text search indexes
CREATE INDEX "Essence_search_idx" ON "Essence" USING GIN (
  to_tsvector('english', "commonName" || ' ' || "latinName" || ' ' || "description" || ' ' || array_to_string("notes", ' '))
);

CREATE INDEX "Folio_search_idx" ON "Folio" USING GIN (
  to_tsvector('english', "title" || ' ' || "content"::text || ' ' || "excerpt")
);

CREATE INDEX "Testimonial_search_idx" ON "Testimonial" USING GIN (
  to_tsvector('english', "author" || ' ' || "title" || ' ' || "quote")
);

-- Vial/Cart performance indexes
CREATE INDEX "Vial_userId_sessionId_idx" ON "Vial"("userId", "sessionId");
CREATE INDEX "Vial_expiresAt_idx" ON "Vial"("expiresAt") WHERE "expiresAt" IS NOT NULL;
```

### 7.6 Data Migration Plan
```typescript
// prisma/migrations/seed.ts
import { prisma } from '@/lib/prisma'
import { hash } from 'bcryptjs'
import { triggerRitualEvent } from '@/services/ritual.service'

async function main() {
  console.log('🌱 Seeding database with artisanal data...');

  // Create admin user with ritual preferences
  const adminPassword = await hash('admin123', 12)
  const admin = await prisma.user.upsert({
    where: { email: 'curator@atelierarome.com' },
    update: {},
    create: {
      email: 'curator@atelierarome.com',
      name: 'Master Perfumer',
      password: adminPassword,
      role: 'ADMIN',
      emailVerified: new Date(),
      ritualPreferences: {
        enabled: true,
        haptics: { enabled: true },
        audio: { enabled: true },
        visual: { enabled: true }
      }
    },
  })

  console.log('👑 Admin user created:', admin.name);

  // Create humours with ritual metadata
  const humours = await prisma.$transaction([
    prisma.humour.upsert({
      where: { id: 'calming' },
      update: {},
      create: {
        id: 'calming',
        name: 'Calming',
        symbol: '☽',
        color: '#B8A9C9',
        ritualMetadata: {
          haptic: { frequency: 100, intensity: 30 },
          audio: { pitch: 300, volume: 0.4 }
        }
      }
    }),
    prisma.humour.upsert({
      where: { id: 'uplifting' },
      update: {},
      create: {
        id: 'uplifting', 
        name: 'Uplifting',
        symbol: '☀',
        color: '#F5D489',
        ritualMetadata: {
          haptic: { frequency: 200, intensity: 60 },
          audio: { pitch: 600, volume: 0.6 }
        }
      }
    }),
    prisma.humour.upsert({
      where: { id: 'grounding' },
      update: {},
      create: {
        id: 'grounding',
        name: 'Grounding', 
        symbol: '♁',
        color: '#7C6354',
        ritualMetadata: {
          haptic: { frequency: 150, intensity: 40 },
          audio: { pitch: 400, volume: 0.5 }
        }
      }
    }),
    prisma.humour.upsert({
      where: { id: 'clarifying' },
      update: {},
      create: {
        id: 'clarifying',
        name: 'Clarifying',
        symbol: '☿',
        color: '#7CB9A0', 
        ritualMetadata: {
          haptic: { frequency: 250, intensity: 50 },
          audio: { pitch: 500, volume: 0.5 }
        }
      }
    }),
  ])

  console.log('💧 Humours created with ritual metadata:', humours.length);

  // Create sample essences with full ritual integration
  const essences = [
    {
      folioNumber: 'I',
      slug: 'provence-lavender',
      latinName: 'Lavandula × intermedia',
      commonName: 'Provence Lavender',
      description: 'Harvested at dawn in the Provençal hills, this lavender possesses a sweetness found only in blossoms kissed by the morning\'s first light. Its effect is one of profound calm, like the silence between breaths.',
      humour: 'CALMING',
      rarity: 'RARE',
      season: 'SUMMER',
      extractionMethod: 'Steam Distillation',
      notes: ['Floral', 'Herbaceous', 'Sweet'],
      price: 42.00,
      volumeMl: 5,
      stockQuantity: 50,
      batchNumber: 'N° 724',
      harvestDate: new Date('2024-06-15'),
      distillationHours: 72,
      ritualMetadata: {
        haptic: { frequency: 120, duration: 150, intensity: 40 },
        audio: { pitch: 350, volume: 0.5, spatialization: 0.7 },
        visual: { waveFrequency: 0.6, waveAmplitude: 12, colorIntensity: 0.8 }
      },
      botanicalInfo: {
        origin: 'Provence, France',
        cultivationMethod: 'Organic, hand-harvested at dawn',
        historicalNotes: 'Lavender has been used since Roman times for its calming properties. The name comes from Latin "lavare" (to wash), as Romans used it in their baths.',
        chemicalComposition: 'Linalool (30-40%), Linalyl acetate (25-38%), Terpinen-4-ol (2-5%)',
        sustainabilityInfo: {
          waterUsage: 'Low - drought resistant',
          carbonFootprint: 'Minimal - local harvesting',
          biodiversity: 'Supports local bee population'
        }
      },
      alchemicalProcess: [
        {
          stepNumber: 1,
          title: 'Solve',
          description: 'The lavender blossoms are gently placed in the still with pure spring water.',
          illustrationUrl: '/illustrations/lavender-solve.jpg'
        },
        {
          stepNumber: 2,
          title: 'Coagula',
          description: 'Steam rises through the botanical matter, carrying the volatile oils.',
          illustrationUrl: '/illustrations/lavender-coagula.jpg'
        },
        {
          stepNumber: 3,
          title: 'Separate',
          description: 'The essential oil separates from the hydrosol in the separator.',
          illustrationUrl: '/illustrations/lavender-separate.jpg'
        },
        {
          stepNumber: 4,
          title: 'Conjoin',
          description: 'The pure essence is bottled under moonlight for maximum potency.',
          illustrationUrl: '/illustrations/lavender-conjoin.jpg'
        }
      ]
    },
    {
      folioNumber: 'II',
      slug: 'tasmanian-eucalyptus',
      latinName: 'Eucalyptus globulus',
      commonName: 'Tasmanian Eucalyptus', 
      description: 'The crisp, clean scent of Tasmania\'s ancient forests. This essence clears the mind as morning mist clears from mountain valleys. Harvested from 100-year-old trees in untouched wilderness.',
      humour: 'CLARIFYING',
      rarity: 'COMMON',
      season: 'AUTUMN',
      extractionMethod: 'Steam Distillation',
      notes: ['Camphorous', 'Fresh', 'Clean'],
      price: 36.00,
      volumeMl: 5,
      stockQuantity: 75,
      batchNumber: 'N° 842',
      harvestDate: new Date('2024-03-22'),
      distillationHours: 48,
      ritualMetadata: {
        haptic: { frequency: 230, duration: 120, intensity: 50 },
        audio: { pitch: 550, volume: 0.6, spatialization: 0.8 },
        visual: { waveFrequency: 0.8, waveAmplitude: 18, colorIntensity: 0.7 }
      },
      botanicalInfo: {
        origin: 'Tasmania, Australia',
        cultivationMethod: 'Wild-harvested from ancient forests',
        historicalNotes: 'Eucalyptus was introduced to Europe in the 1850s. Aboriginal Australians used it for thousands of years for respiratory ailments.',
        chemicalComposition: '1,8-Cineole (70-85%), α-Pinene (5-15%), Limonene (1-3%)',
        sustainabilityInfo: {
          waterUsage: 'Moderate - native species',
          carbonFootprint: 'Low - wild harvest',
          biodiversity: 'Ancient forest ecosystem preservation'
        }
      }
    },
    {
      folioNumber: 'III',
      slug: 'calabrian-bergamot',
      latinName: 'Citrus bergamia',
      commonName: 'Calabrian Bergamot',
      description: 'From Italy\'s sun-drenched Calabrian coast, this essence captures the joyful brightness of citrus groves at harvest. A note of pure sunlight, hand-picked during the Winter Solstice when the oils are most concentrated.',
      humour: 'UPLIFTING',
      rarity: 'LIMITED',
      season: 'WINTER',
      extractionMethod: 'Cold Press',
      notes: ['Citrus', 'Bright', 'Spicy'],
      price: 48.00,
      volumeMl: 5,
      stockQuantity: 30,
      batchNumber: '

## 7. Data Architecture

### 7.1 Entity Relationship Diagram
```mermaid
erDiagram
    USER ||--o{ ORDER : "places"
    USER ||--o{ ADDRESS : "has"
    USER ||--o{ SUBSCRIPTION : "subscribes_to"
    USER ||--o{ VIAL : "maintains"
    USER ||--o{ RITUAL_PREFERENCE : "configures"
    
    USER {
        string id PK
        string email
        string name
        string password
        string role
        datetime createdAt
        datetime updatedAt
        datetime emailVerified
        string image
        json ritualPreferences
    }
    
    ADDRESS {
        string id PK
        string userId FK
        string type
        string street
        string city
        string state
        string postalCode
        string country
        boolean isDefault
        datetime createdAt
        datetime updatedAt
    }
    
    ORDER ||--o{ ORDER_ITEM : "contains"
    ORDER ||--o{ PAYMENT : "has"
    ORDER ||--o{ SHIPMENT : "has"
    
    ORDER {
        string id PK
        string orderNumber
        string userId FK
        string stripePaymentIntentId
        decimal subtotal
        decimal shippingCost
        decimal taxAmount
        decimal total
        string currency
        string status
        datetime paidAt
        datetime shippedAt
        datetime deliveredAt
        datetime createdAt
        datetime updatedAt
        json metadata
    }
    
    ORDER_ITEM {
        string id PK
        string orderId FK
        string essenceId FK
        integer quantity
        decimal unitPrice
        decimal totalPrice
        datetime createdAt
        datetime updatedAt
    }
    
    ESSENCE ||--o{ ORDER_ITEM : "sold_in"
    ESSENCE ||--o{ ESSENCE_IMAGE : "has"
    ESSENCE ||--o{ ESSENCE_RITUAL_METADATA : "configured_with"
    ESSENCE ||--o{ BOTANICAL_INFO : "described_by"
    
    ESSENCE {
        string id PK
        string folioNumber
        string slug
        string latinName
        string commonName
        string description
        string humour
        string rarity
        string season
        string extractionMethod
        string[] notes
        decimal price
        integer volumeMl
        integer stockQuantity
        boolean isActive
        string batchNumber
        datetime harvestDate
        integer distillationHours
        datetime createdAt
        datetime updatedAt
    }
    
    ESSENCE_IMAGE {
        string id PK
        string essenceId FK
        string url
        string altText
        integer width
        integer height
        integer order
        datetime createdAt
    }
    
    ESSENCE_RITUAL_METADATA {
        string id PK
        string essenceId FK
        json haptic
        json audio
        json visual
        datetime createdAt
        datetime updatedAt
    }
    
    BOTANICAL_INFO {
        string id PK
        string essenceId FK
        string origin
        string cultivationMethod
        string historicalNotes
        string chemicalComposition
        json sustainabilityInfo
        datetime createdAt
        datetime updatedAt
    }
    
    SUBSCRIPTION {
        string id PK
        string userId FK
        string stripeSubscriptionId
        string status
        string plan
        decimal price
        datetime startDate
        datetime nextBillingDate
        datetime cancelledAt
        datetime createdAt
        datetime updatedAt
        json metadata
    }
    
    VIAL {
        string id PK
        string userId FK
        string sessionId
        json items
        datetime expiresAt
        datetime createdAt
        datetime updatedAt
    }
    
    VIAL_ITEM {
        string id PK
        string vialId FK
        string essenceId FK
        integer quantity
        datetime addedAt
    }
    
    AL_CHEMICAL_PROCESS {
        string id PK
        string essenceId FK
        string stepNumber
        string title
        string description
        string illustrationUrl
        datetime createdAt
        datetime updatedAt
    }
    
    ARTISAN_NOTE {
        string id PK
        string essenceId FK
        string artisanId
        string content
        datetime createdAt
        datetime updatedAt
    }
    
    TESTIMONIAL {
        string id PK
        string userId FK
        string author
        string title
        string quote
        string folioEntry
        boolean verified
        boolean illuminated
        boolean featured
        integer order
        datetime approvedAt
        datetime publishedAt
        datetime createdAt
        datetime updatedAt
    }
    
    FOLIO {
        string id PK
        string title
        string slug
        string edition
        json content
        string excerpt
        string status
        datetime sentAt
        float openRate
        float clickRate
        datetime createdAt
        datetime updatedAt
        datetime publishedAt
    }
    
    RITUAL_PREFERENCE {
        string id PK
        string userId FK
        boolean enabled
        json haptics
        json audio
        json visual
        boolean reducedMotion
        boolean accessibilityMode
        datetime createdAt
        datetime updatedAt
    }
    
    AUDIT_LOG {
        string id PK
        string userId FK
        string event
        json metadata
        datetime createdAt
    }
```

### 7.2 Database Schema (DDL)
```sql
-- Users Table
CREATE TABLE "User" (
  "id" TEXT NOT NULL PRIMARY KEY,
  "email" TEXT NOT NULL,
  "name" TEXT,
  "password" TEXT,
  "role" TEXT NOT NULL DEFAULT 'customer',
  "emailVerified" DATETIME,
  "image" TEXT,
  "createdAt" DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  "updatedAt" DATETIME NOT NULL,
  "ritualPreferences" JSONB DEFAULT '{"enabled": false}'
);

CREATE UNIQUE INDEX "User_email_key" ON "User"("email");

-- Ritual Preferences Table
CREATE TABLE "RitualPreference" (
  "id" TEXT NOT NULL PRIMARY KEY,
  "userId" TEXT NOT NULL,
  "enabled" BOOLEAN NOT NULL DEFAULT false,
  "haptics" JSONB DEFAULT '{"enabled": false}',
  "audio" JSONB DEFAULT '{"enabled": false}',
  "visual" JSONB DEFAULT '{"enabled": false}',
  "reducedMotion" BOOLEAN NOT NULL DEFAULT false,
  "accessibilityMode" BOOLEAN NOT NULL DEFAULT false,
  "createdAt" DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  "updatedAt" DATETIME NOT NULL,
  CONSTRAINT "RitualPreference_userId_fkey" FOREIGN KEY ("userId") REFERENCES "User"("id") ON DELETE CASCADE ON UPDATE CASCADE
);

CREATE UNIQUE INDEX "RitualPreference_userId_key" ON "RitualPreference"("userId");

-- Addresses Table
CREATE TABLE "Address" (
  "id" TEXT NOT NULL PRIMARY KEY,
  "userId" TEXT NOT NULL,
  "type" TEXT NOT NULL DEFAULT 'shipping',
  "street" TEXT NOT NULL,
  "city" TEXT NOT NULL,
  "state" TEXT,
  "postalCode" TEXT NOT NULL,
  "country" TEXT NOT NULL,
  "isDefault" BOOLEAN NOT NULL DEFAULT false,
  "createdAt" DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  "updatedAt" DATETIME NOT NULL,
  CONSTRAINT "Address_userId_fkey" FOREIGN KEY ("userId") REFERENCES "User"("id") ON DELETE CASCADE ON UPDATE CASCADE
);

-- Essences Table
CREATE TABLE "Essence" (
  "id" TEXT NOT NULL PRIMARY KEY,
  "folioNumber" TEXT NOT NULL, -- Roman numerals: I, II, III
  "slug" TEXT NOT NULL,
  "latinName" TEXT NOT NULL,
  "commonName" TEXT NOT NULL,
  "description" TEXT NOT NULL,
  "humour" TEXT NOT NULL CHECK ("humour" IN ('CALMING', 'UPLIFTING', 'GROUNDING', 'CLARIFYING')),
  "rarity" TEXT NOT NULL CHECK ("rarity" IN ('COMMON', 'RARE', 'LIMITED')),
  "season" TEXT NOT NULL CHECK ("season" IN ('SPRING', 'SUMMER', 'AUTUMN', 'WINTER')),
  "extractionMethod" TEXT NOT NULL,
  "notes" TEXT[] NOT NULL DEFAULT ARRAY[]::TEXT[],
  "price" DECIMAL(10,2) NOT NULL,
  "volumeMl" INTEGER NOT NULL DEFAULT 5,
  "stockQuantity" INTEGER NOT NULL DEFAULT 0,
  "isActive" BOOLEAN NOT NULL DEFAULT true,
  "batchNumber" TEXT,
  "harvestDate" DATETIME,
  "distillationHours" INTEGER,
  "createdAt" DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  "updatedAt" DATETIME NOT NULL
);

CREATE UNIQUE INDEX "Essence_slug_key" ON "Essence"("slug");
CREATE UNIQUE INDEX "Essence_folioNumber_key" ON "Essence"("folioNumber");
CREATE INDEX "Essence_humour_idx" ON "Essence"("humour");
CREATE INDEX "Essence_rarity_idx" ON "Essence"("rarity");
CREATE INDEX "Essence_season_idx" ON "Essence"("season");
CREATE INDEX "Essence_price_idx" ON "Essence"("price");
CREATE INDEX "Essence_createdAt_idx" ON "Essence"("createdAt" DESC);

-- Essence Images Table
CREATE TABLE "EssenceImage" (
  "id" TEXT NOT NULL PRIMARY KEY,
  "essenceId" TEXT NOT NULL,
  "url" TEXT NOT NULL,
  "altText" TEXT,
  "width" INTEGER NOT NULL,
  "height" INTEGER NOT NULL,
  "order" INTEGER NOT NULL DEFAULT 0,
  "createdAt" DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  CONSTRAINT "EssenceImage_essenceId_fkey" FOREIGN KEY ("essenceId") REFERENCES "Essence"("id") ON DELETE CASCADE ON UPDATE CASCADE
);

CREATE INDEX "EssenceImage_essenceId_order_idx" ON "EssenceImage"("essenceId", "order");

-- Essence Ritual Metadata Table
CREATE TABLE "EssenceRitualMetadata" (
  "id" TEXT NOT NULL PRIMARY KEY,
  "essenceId" TEXT NOT NULL,
  "haptic" JSONB NOT NULL DEFAULT '{"frequency": 150, "duration": 100, "intensity": 50}',
  "audio" JSONB NOT NULL DEFAULT '{"pitch": 440, "volume": 0.5, "spatialization": 0.7}',
  "visual" JSONB NOT NULL DEFAULT '{"waveFrequency": 0.7, "waveAmplitude": 15, "colorIntensity": 0.8}',
  "createdAt" DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  "updatedAt" DATETIME NOT NULL,
  CONSTRAINT "EssenceRitualMetadata_essenceId_fkey" FOREIGN KEY ("essenceId") REFERENCES "Essence"("id") ON DELETE CASCADE ON UPDATE CASCADE
);

CREATE UNIQUE INDEX "EssenceRitualMetadata_essenceId_key" ON "EssenceRitualMetadata"("essenceId");

-- Botanical Info Table
CREATE TABLE "BotanicalInfo" (
  "id" TEXT NOT NULL PRIMARY KEY,
  "essenceId" TEXT NOT NULL,
  "origin" TEXT NOT NULL,
  "cultivationMethod" TEXT NOT NULL,
  "historicalNotes" TEXT,
  "chemicalComposition" TEXT,
  "sustainabilityInfo" JSONB,
  "createdAt" DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  "updatedAt" DATETIME NOT NULL,
  CONSTRAINT "BotanicalInfo_essenceId_fkey" FOREIGN KEY ("essenceId") REFERENCES "Essence"("id") ON DELETE CASCADE ON UPDATE CASCADE
);

CREATE UNIQUE INDEX "BotanicalInfo_essenceId_key" ON "BotanicalInfo"("essenceId");

-- Vials Table (Cart)
CREATE TABLE "Vial" (
  "id" TEXT NOT NULL PRIMARY KEY,
  "userId" TEXT,
  "sessionId" TEXT,
  "items" JSONB NOT NULL DEFAULT '[]',
  "expiresAt" DATETIME,
  "createdAt" DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  "updatedAt" DATETIME NOT NULL,
  CONSTRAINT "Vial_userId_fkey" FOREIGN KEY ("userId") REFERENCES "User"("id") ON DELETE SET NULL ON UPDATE CASCADE
);

CREATE INDEX "Vial_sessionId_idx" ON "Vial"("sessionId");
CREATE INDEX "Vial_expiresAt_idx" ON "Vial"("expiresAt") WHERE "expiresAt" IS NOT NULL;

-- Orders Table
CREATE TABLE "Order" (
  "id" TEXT NOT NULL PRIMARY KEY,
  "orderNumber" TEXT NOT NULL,
  "userId" TEXT NOT NULL,
  "stripePaymentIntentId" TEXT,
  "subtotal" DECIMAL(10,2) NOT NULL,
  "shippingCost" DECIMAL(10,2) NOT NULL,
  "taxAmount" DECIMAL(10,2) NOT NULL DEFAULT 0,
  "total" DECIMAL(10,2) NOT NULL,
  "currency" TEXT NOT NULL DEFAULT 'EUR',
  "status" TEXT NOT NULL DEFAULT 'PENDING' CHECK ("status" IN ('DRAFT', 'PENDING', 'CONFIRMED', 'DISPATCHED', 'COMPLETED', 'CANCELLED')),
  "paidAt" DATETIME,
  "shippedAt" DATETIME,
  "deliveredAt" DATETIME,
  "createdAt" DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  "updatedAt" DATETIME NOT NULL,
  "metadata" JSONB,
  CONSTRAINT "Order_userId_fkey" FOREIGN KEY ("userId") REFERENCES "User"("id") ON DELETE RESTRICT ON UPDATE CASCADE
);

CREATE UNIQUE INDEX "Order_orderNumber_key" ON "Order"("orderNumber");
CREATE UNIQUE INDEX "Order_stripePaymentIntentId_key" ON "Order"("stripePaymentIntentId");
CREATE INDEX "Order_userId_status_idx" ON "Order"("userId", "status");
CREATE INDEX "Order_createdAt_idx" ON "Order"("createdAt" DESC);

-- Order Items Table
CREATE TABLE "OrderItem" (
  "id" TEXT NOT NULL PRIMARY KEY,
  "orderId" TEXT NOT NULL,
  "essenceId" TEXT NOT NULL,
  "quantity" INTEGER NOT NULL,
  "unitPrice" DECIMAL(10,2) NOT NULL,
  "totalPrice" DECIMAL(10,2) NOT NULL,
  "createdAt" DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  "updatedAt" DATETIME NOT NULL,
  CONSTRAINT "OrderItem_orderId_fkey" FOREIGN KEY ("orderId") REFERENCES "Order"("id") ON DELETE CASCADE ON UPDATE CASCADE,
  CONSTRAINT "OrderItem_essenceId_fkey" FOREIGN KEY ("essenceId") REFERENCES "Essence"("id") ON DELETE RESTRICT ON UPDATE CASCADE
);

CREATE INDEX "OrderItem_orderId_idx" ON "OrderItem"("orderId");
CREATE INDEX "OrderItem_essenceId_idx" ON "OrderItem"("essenceId");

-- Subscriptions Table
CREATE TABLE "Subscription" (
  "id" TEXT NOT NULL PRIMARY KEY,
  "userId" TEXT NOT NULL,
  "stripeSubscriptionId" TEXT NOT NULL,
  "status" TEXT NOT NULL CHECK ("status" IN ('ACTIVE', 'PAUSED', 'CANCELLED', 'PAST_DUE')),
  "plan" TEXT NOT NULL CHECK ("plan" IN ('QUARTERLY', 'ANNUAL')),
  "price" DECIMAL(10,2) NOT NULL,
  "startDate" DATETIME NOT NULL,
  "nextBillingDate" DATETIME NOT NULL,
  "cancelledAt" DATETIME,
  "createdAt" DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  "updatedAt" DATETIME NOT NULL,
  "metadata" JSONB,
  CONSTRAINT "Subscription_userId_fkey" FOREIGN KEY ("userId") REFERENCES "User"("id") ON DELETE CASCADE ON UPDATE CASCADE
);

CREATE UNIQUE INDEX "Subscription_stripeSubscriptionId_key" ON "Subscription"("stripeSubscriptionId");
CREATE INDEX "Subscription_userId_status_idx" ON "Subscription"("userId", "status");
CREATE INDEX "Subscription_nextBillingDate_idx" ON "Subscription"("nextBillingDate");

-- Alchemical Process Table
CREATE TABLE "AlchemicalProcess" (
  "id" TEXT NOT NULL PRIMARY KEY,
  "essenceId" TEXT NOT NULL,
  "stepNumber" INTEGER NOT NULL,
  "title" TEXT NOT NULL,
  "description" TEXT NOT NULL,
  "illustrationUrl" TEXT,
  "createdAt" DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  "updatedAt" DATETIME NOT NULL,
  CONSTRAINT "AlchemicalProcess_essenceId_fkey" FOREIGN KEY ("essenceId") REFERENCES "Essence"("id") ON DELETE CASCADE ON UPDATE CASCADE
);

CREATE INDEX "AlchemicalProcess_essenceId_stepNumber_idx" ON "AlchemicalProcess"("essenceId", "stepNumber");

-- Artisan Notes Table
CREATE TABLE "ArtisanNote" (
  "id" TEXT NOT NULL PRIMARY KEY,
  "essenceId" TEXT NOT NULL,
  "artisanId" TEXT NOT NULL,
  "content" TEXT NOT NULL,
  "createdAt" DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  "updatedAt" DATETIME NOT NULL,
  CONSTRAINT "ArtisanNote_essenceId_fkey" FOREIGN KEY ("essenceId") REFERENCES "Essence"("id") ON DELETE CASCADE ON UPDATE CASCADE,
  CONSTRAINT "ArtisanNote_artisanId_fkey" FOREIGN KEY ("artisanId") REFERENCES "User"("id") ON DELETE CASCADE ON UPDATE CASCADE
);

CREATE INDEX "ArtisanNote_essenceId_idx" ON "ArtisanNote"("essenceId");
CREATE INDEX "ArtisanNote_artisanId_idx" ON "ArtisanNote"("artisanId");

-- Testimonials Table
CREATE TABLE "Testimonial" (
  "id" TEXT NOT NULL PRIMARY KEY,
  "userId" TEXT,
  "author" TEXT NOT NULL,
  "title" TEXT NOT NULL,
  "quote" TEXT NOT NULL,
  "folioEntry" TEXT,
  "verified" BOOLEAN NOT NULL DEFAULT false,
  "illuminated" BOOLEAN NOT NULL DEFAULT false,
  "featured" BOOLEAN NOT NULL DEFAULT false,
  "order" INTEGER NOT NULL DEFAULT 0,
  "approvedAt" DATETIME,
  "publishedAt" DATETIME,
  "createdAt" DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  "updatedAt" DATETIME NOT NULL,
  CONSTRAINT "Testimonial_userId_fkey" FOREIGN KEY ("userId") REFERENCES "User"("id") ON DELETE SET NULL ON UPDATE CASCADE
);

CREATE INDEX "Testimonial_publishedAt_idx" ON "Testimonial"("publishedAt");
CREATE INDEX "Testimonial_featured_idx" ON "Testimonial"("featured");
CREATE INDEX "Testimonial_order_idx" ON "Testimonial"("order");

-- Folios Table (Manuscript Subscriptions)
CREATE TABLE "Folio" (
  "id" TEXT NOT NULL PRIMARY KEY,
  "title" TEXT NOT NULL,
  "slug" TEXT NOT NULL,
  "edition" TEXT NOT NULL, -- e.g., "Spring Equinox MMXXIV"
  "content" JSONB NOT NULL,
  "excerpt" TEXT,
  "status" TEXT NOT NULL DEFAULT 'DRAFT' CHECK ("status" IN ('DRAFT', 'SCHEDULED', 'SENDING', 'SENT', 'ARCHIVED')),
  "sentAt" DATETIME,
  "openRate" DECIMAL(5,2),
  "clickRate" DECIMAL(5,2),
  "createdAt" DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  "updatedAt" DATETIME NOT NULL,
  "publishedAt" DATETIME
);

CREATE UNIQUE INDEX "Folio_slug_key" ON "Folio"("slug");
CREATE INDEX "Folio_publishedAt_idx" ON "Folio"("publishedAt");
CREATE INDEX "Folio_status_idx" ON "Folio"("status");

-- Audit Log Table
CREATE TABLE "AuditLog" (
  "id" TEXT NOT NULL PRIMARY KEY,
  "userId" TEXT,
  "event" TEXT NOT NULL,
  "metadata" JSONB,
  "createdAt" DATETIME NOT NULL DEFAULT CURRENT_TIMESTAMP,
  CONSTRAINT "AuditLog_userId_fkey" FOREIGN KEY ("userId") REFERENCES "User"("id") ON DELETE SET NULL ON UPDATE CASCADE
);

CREATE INDEX "AuditLog_createdAt_idx" ON "AuditLog"("createdAt" DESC);
CREATE INDEX "AuditLog_event_idx" ON "AuditLog"("event");
```

### 7.3 Prisma Schema
```prisma
// prisma/schema.prisma
generator client {
  provider = "prisma-client-js"
  previewFeatures = ["fullTextSearch", "relationJoins", "interactiveTransactions"]
}

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
  directUrl = env("DIRECT_URL")
}

model User {
  id             String    @id @default(auto()) @map("_id")
  email          String    @unique
  name           String?
  password       String?
  role           String    @default("customer")
  emailVerified  DateTime?
  image          String?
  createdAt      DateTime  @default(now())
  updatedAt      DateTime  @updatedAt
  ritualPreferences Json?  @default("{\"enabled\": false}")

  addresses      Address[]
  orders         Order[]
  subscriptions  Subscription[]
  vial           Vial?
  testimonials   Testimonial[]
  artisanNotes   ArtisanNote[]
  ritualPreference RitualPreference?

  @@map("User")
}

model RitualPreference {
  id             String  @id @default(auto()) @map("_id")
  userId         String  @unique
  user           User    @relation(fields: [userId], references: [id], onDelete: Cascade)
  enabled        Boolean @default(false)
  haptics        Json?   @default("{\"enabled\": false}")
  audio          Json?   @default("{\"enabled\": false}")
  visual         Json?   @default("{\"enabled\": false}")
  reducedMotion  Boolean @default(false)
  accessibilityMode Boolean @default(false)
  createdAt      DateTime @default(now())
  updatedAt      DateTime @updatedAt

  @@map("RitualPreference")
}

model Address {
  id          String   @id @default(auto()) @map("_id")
  userId      String
  user        User     @relation(fields: [userId], references: [id], onDelete: Cascade)
  type        String   @default("shipping")
  street      String
  city        String
  state       String?
  postalCode  String
  country     String
  isDefault   Boolean  @default(false)
  createdAt   DateTime @default(now())
  updatedAt   DateTime @updatedAt

  @@map("Address")
}

model Essence {
  id               String            @id @default(auto()) @map("_id")
  folioNumber      String            @unique // Roman numerals: I, II, III
  slug             String            @unique
  latinName        String
  commonName       String
  description      String
  humour           HumourType
  rarity           RarityType
  season           SeasonType
  extractionMethod String
  notes            String[]
  price            Decimal @db.Decimal(10, 2)
  volumeMl         Int     @default(5)
  stockQuantity    Int     @default(0)
  isActive         Boolean @default(true)
  batchNumber      String?
  harvestDate      DateTime?
  distillationHours Int?
  createdAt        DateTime @default(now())
  updatedAt        DateTime @updatedAt

  images           EssenceImage[]
  ritualMetadata   EssenceRitualMetadata?
  botanicalInfo    BotanicalInfo?
  orderItems       OrderItem[]
  alchemicalProcess AlchemicalProcess[]
  artisanNotes     ArtisanNote[]
  testimonials     Testimonial[]

  @@map("Essence")
  @@index([humour])
  @@index([rarity])
  @@index([season])
  @@index([price])
  @@index([createdAt])
}

enum HumourType {
  CALMING
  UPLIFTING
  GROUNDING
  CLARIFYING
}

enum RarityType {
  COMMON
  RARE
  LIMITED
}

enum SeasonType {
  SPRING
  SUMMER
  AUTUMN
  WINTER
}

model EssenceImage {
  id        String   @id @default(auto()) @map("_id")
  essenceId String
  essence   Essence  @relation(fields: [essenceId], references: [id], onDelete: Cascade)
  url       String
  altText   String?
  width     Int
  height    Int
  order     Int      @default(0)
  createdAt DateTime @default(now())

  @@map("EssenceImage")
  @@index([essenceId, order])
}

model EssenceRitualMetadata {
  id        String   @id @default(auto()) @map("_id")
  essenceId String   @unique
  essence   Essence  @relation(fields: [essenceId], references: [id], onDelete: Cascade)
  haptic    Json     @default("{\"frequency\": 150, \"duration\": 100, \"intensity\": 50}")
  audio     Json     @default("{\"pitch\": 440, \"volume\": 0.5, \"spatialization\": 0.7}")
  visual    Json     @default("{\"waveFrequency\": 0.7, \"waveAmplitude\": 15, \"colorIntensity\": 0.8}")
  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt

  @@map("EssenceRitualMetadata")
}

model BotanicalInfo {
  id                 String   @id @default(auto()) @map("_id")
  essenceId          String   @unique
  essence            Essence  @relation(fields: [essenceId], references: [id], onDelete: Cascade)
  origin             String
  cultivationMethod  String
  historicalNotes    String?
  chemicalComposition String?
  sustainabilityInfo Json?
  createdAt          DateTime @default(now())
  updatedAt          DateTime @updatedAt

  @@map("BotanicalInfo")
}

model Vial {
  id         String    @id @default(auto()) @map("_id")
  userId     String?
  user       User?     @relation(fields: [userId], references: [id], onDelete: SetNull)
  sessionId  String?
  items      Json      @default("[]")
  expiresAt  DateTime?
  createdAt  DateTime  @default(now())
  updatedAt  DateTime  @updatedAt

  @@map("Vial")
  @@index([sessionId])
  @@index([expiresAt])
}

model Order {
  id                 String         @id @default(auto()) @map("_id")
  orderNumber        String         @unique
  userId             String
  user               User           @relation(fields: [userId], references: [id])
  stripePaymentIntentId String?
  subtotal           Decimal        @db.Decimal(10, 2)
  shippingCost       Decimal        @db.Decimal(10, 2)
  taxAmount          Decimal        @db.Decimal(10, 2) @default(0)
  total              Decimal        @db.Decimal(10, 2)
  currency           String         @default("EUR")
  status             OrderStatus    @default(PENDING)
  paidAt             DateTime?
  shippedAt          DateTime?
  deliveredAt        DateTime?
  createdAt          DateTime       @default(now())
  updatedAt          DateTime       @updatedAt
  metadata           Json?

  items              OrderItem[]
  payments           Payment[]
  shipments          Shipment[]

  @@map("Order")
  @@index([userId, status])
  @@index([createdAt])
}

enum OrderStatus {
  DRAFT
  PENDING
  CONFIRMED
  DISPATCHED
  COMPLETED
  CANCELLED
}

model OrderItem {
  id         String   @id @default(auto()) @map("_id")
  orderId    String
  order      Order    @relation(fields: [orderId], references: [id], onDelete: Cascade)
  essenceId  String
  essence    Essence  @relation(fields: [essenceId], references: [id])
  quantity   Int
  unitPrice  Decimal  @db.Decimal(10, 2)
  totalPrice Decimal  @db.Decimal(10, 2)
  createdAt  DateTime @default(now())
  updatedAt  DateTime @updatedAt

  @@map("OrderItem")
  @@index([orderId])
  @@index([essenceId])
}

model Payment {
  id                String       @id @default(auto()) @map("_id")
  orderId           String
  order             Order        @relation(fields: [orderId], references: [id], onDelete: Cascade)
  stripePaymentId   String       @unique
  paymentMethod     String
  amount            Decimal      @db.Decimal(10, 2)
  currency          String
  status            PaymentStatus @default(PENDING)
  createdAt         DateTime     @default(now())
  updatedAt         DateTime     @updatedAt
  metadata          Json?

  @@map("Payment")
}

enum PaymentStatus {
  PENDING
  PROCESSING
  SUCCEEDED
  FAILED
  REFUNDED
}

model Shipment {
  id                String       @id @default(auto()) @map("_id")
  orderId           String
  order             Order        @relation(fields: [orderId], references: [id], onDelete: Cascade)
  trackingNumber    String
  carrier           String
  status            ShipmentStatus @default(PENDING)
  shippedAt         DateTime
  estimatedDelivery DateTime?
  deliveredAt       DateTime?
  trackingEvents    Json?
  createdAt         DateTime     @default(now())
  updatedAt         DateTime     @updatedAt

  @@map("Shipment")
}

enum ShipmentStatus {
  PENDING
  SHIPPED
  IN_TRANSIT
  OUT_FOR_DELIVERY
  DELIVERED
  RETURNED
}

model Subscription {
  id                String          @id @default(auto()) @map("_id")
  userId            String
  user              User            @relation(fields: [userId], references: [id], onDelete: Cascade)
  stripeSubscriptionId String        @unique
  status            SubscriptionStatus @default(ACTIVE)
  plan              SubscriptionPlan @default(QUARTERLY)
  price             Decimal         @db.Decimal(10, 2)
  startDate         DateTime
  nextBillingDate   DateTime
  cancelledAt       DateTime?
  createdAt         DateTime        @default(now())
  updatedAt         DateTime        @updatedAt
  metadata          Json?

  @@map("Subscription")
  @@index([userId, status])
  @@index([nextBillingDate])
}

enum SubscriptionStatus {
  ACTIVE
  PAUSED
  CANCELLED
  PAST_DUE
}

enum SubscriptionPlan {
  QUARTERLY
  ANNUAL
}

model AlchemicalProcess {
  id            String   @id @default(auto()) @map("_id")
  essenceId     String
  essence       Essence  @relation(fields: [essenceId], references: [id], onDelete: Cascade)
  stepNumber    Int
  title         String
  description   String
  illustrationUrl String?
  createdAt     DateTime @default(now())
  updatedAt     DateTime @updatedAt

  @@map("AlchemicalProcess")
  @@index([essenceId, stepNumber])
}

model ArtisanNote {
  id         String   @id @default(auto()) @map("_id")
  essenceId  String
  essence    Essence  @relation(fields: [essenceId], references: [id], onDelete: Cascade)
  artisanId  String
  artisan    User     @relation(fields: [artisanId], references: [id], onDelete: Cascade)
  content    String
  createdAt  DateTime @default(now())
  updatedAt  DateTime @updatedAt

  @@map("ArtisanNote")
  @@index([essenceId])
  @@index([artisanId])
}

model Testimonial {
  id            String   @id @default(auto()) @map("_id")
  userId        String?
  user          User?    @relation(fields: [userId], references: [id], onDelete: SetNull)
  author        String
  title         String
  quote         String   @db.Text
  folioEntry    String?
  verified      Boolean  @default(false)
  illuminated   Boolean  @default(false)
  featured      Boolean  @default(false)
  order         Int      @default(0)
  approvedAt    DateTime?
  publishedAt   DateTime?
  createdAt     DateTime @default(now())
  updatedAt     DateTime @updatedAt

  @@map("Testimonial")
  @@index([publishedAt])
  @@index([featured])
  @@index([order])
}

model Folio {
  id           String          @id @default(auto()) @map("_id")
  title        String
  slug         String          @unique
  edition      String          // e.g., "Spring Equinox MMXXIV"
  content      Json
  excerpt      String?
  status       FolioStatus     @default(DRAFT)
  sentAt       DateTime?
  openRate     Float?          @db.Decimal(5, 2)
  clickRate    Float?          @db.Decimal(5, 2)
  createdAt    DateTime        @default(now())
  updatedAt    DateTime        @updatedAt
  publishedAt  DateTime?

  @@map("Folio")
  @@index([publishedAt])
  @@index([status])
}

enum FolioStatus {
  DRAFT
  SCHEDULED
  SENDING
  SENT
  ARCHIVED
}

model AuditLog {
  id        String   @id @default(auto()) @map("_id")
  userId    String?
  user      User?    @relation(fields: [userId], references: [id], onDelete: SetNull)
  event     String
  metadata  Json?
  createdAt DateTime @default(now())

  @@map("AuditLog")
  @@index([createdAt])
  @@index([event])
}
```

### 7.4 Data Access Patterns
```typescript
// lib/prisma.ts - Prisma Client Singleton with Ritual Instrumentation
import { PrismaClient } from '@prisma/client'
import { triggerRitualEvent } from '@/services/ritual.service'

declare global {
  var prisma: PrismaClient | undefined
}

export const prisma = 
  global.prisma ||
  new PrismaClient({
    log: process.env.NODE_ENV === 'development' 
      ? ['query', 'error', 'warn'] 
      : ['error'],
    errorFormat: 'pretty',
    // Add custom instrumentation for ritual events
    hooks: {
      beforeRequest: async (context) => {
        // Log slow queries for performance monitoring
        if (context.query?.startsWith('SELECT') && context.args?.take && context.args.take > 100) {
          await triggerRitualEvent('database_query_start', {
            operation: context.query.split(' ')[0],
            model: context.model,
            count: context.args.take,
            timestamp: Date.now()
          });
        }
      },
      afterResponse: async (context) => {
        // Track query performance
        const duration = Date.now() - (context.timestamp || Date.now());
        if (duration > 100) {
          await triggerRitualEvent('database_query_slow', {
            operation: context.query?.split(' ')[0],
            model: context.model,
            duration,
            timestamp: Date.now()
          });
        }
      }
    }
  })

if (process.env.NODE_ENV !== 'production') global.prisma = prisma
```

### 7.5 Indexing Strategy
```sql
-- Performance Indexing Strategy for Atelier Arôme
-- Created: 2024
-- Purpose: Optimize query performance for high-traffic operations

-- Orders Table Indexes
CREATE INDEX "Order_userId_status_idx" ON "Order"("userId", "status");
CREATE INDEX "Order_createdAt_idx" ON "Order"("createdAt" DESC);
CREATE INDEX "Order_status_idx" ON "Order"("status");

-- Essences Table Indexes
CREATE INDEX "Essence_slug_active_idx" ON "Essence"("slug", "isActive");
CREATE INDEX "Essence_humour_rarity_season_idx" ON "Essence"("humour", "rarity", "season");
CREATE INDEX "Essence_price_idx" ON "Essence"("price");
CREATE INDEX "Essence_createdAt_idx" ON "Essence"("createdAt" DESC);
CREATE INDEX "Essence_manuscript_authentic_idx" ON "Essence"("batchNumber", "harvestDate", "distillationHours") 
WHERE "batchNumber" IS NOT NULL OR "harvestDate" IS NOT NULL OR "distillationHours" IS NOT NULL;

-- Users Table Indexes
CREATE INDEX "User_email_verified_idx" ON "User"("email", "emailVerified");
CREATE INDEX "User_createdAt_idx" ON "User"("createdAt" DESC);
CREATE INDEX "User_role_idx" ON "User"("role");

-- Order Items Table Indexes
CREATE INDEX "OrderItem_orderId_idx" ON "OrderItem"("orderId");
CREATE INDEX "OrderItem_essenceId_idx" ON "OrderItem"("essenceId");

-- Subscriptions Table Indexes
CREATE INDEX "Subscription_userId_status_idx" ON "Subscription"("userId", "status");
CREATE INDEX "Subscription_nextBillingDate_idx" ON "Subscription"("nextBillingDate");

-- Testimonials Table Indexes
CREATE INDEX "Testimonial_isFeatured_idx" ON "Testimonial"("featured", "createdAt" DESC);
CREATE INDEX "Testimonial_userId_idx" ON "Testimonial"("userId");

-- Ritual Preferences Indexes
CREATE INDEX "RitualPreference_userId_idx" ON "RitualPreference"("userId");
CREATE INDEX "RitualPreference_enabled_idx" ON "RitualPreference"("enabled");

-- Full-text search indexes
CREATE INDEX "Essence_search_idx" ON "Essence" USING GIN (
  to_tsvector('english', "commonName" || ' ' || "latinName" || ' ' || "description" || ' ' || array_to_string("notes", ' '))
);

CREATE INDEX "Folio_search_idx" ON "Folio" USING GIN (
  to_tsvector('english', "title" || ' ' || "content"::text || ' ' || "excerpt")
);

CREATE INDEX "Testimonial_search_idx" ON "Testimonial" USING GIN (
  to_tsvector('english', "author" || ' ' || "title" || ' ' || "quote")
);

-- Vial/Cart performance indexes
CREATE INDEX "Vial_userId_sessionId_idx" ON "Vial"("userId", "sessionId");
CREATE INDEX "Vial_expiresAt_idx" ON "Vial"("expiresAt") WHERE "expiresAt" IS NOT NULL;
```

### 7.6 Data Migration Plan
```typescript
// prisma/migrations/seed.ts
import { prisma } from '@/lib/prisma'
import { hash } from 'bcryptjs'
import { triggerRitualEvent } from '@/services/ritual.service'

async function main() {
  console.log('🌱 Seeding database with artisanal data...');

  // Create admin user with ritual preferences
  const adminPassword = await hash('admin123', 12)
  const admin = await prisma.user.upsert({
    where: { email: 'curator@atelierarome.com' },
    update: {},
    create: {
      email: 'curator@atelierarome.com',
      name: 'Master Perfumer',
      password: adminPassword,
      role: 'ADMIN',
      emailVerified: new Date(),
      ritualPreferences: {
        enabled: true,
        haptics: { enabled: true },
        audio: { enabled: true },
        visual: { enabled: true }
      }
    },
  })

  console.log('👑 Admin user created:', admin.name);

  // Create humours with ritual metadata
  const humours = await prisma.$transaction([
    prisma.humour.upsert({
      where: { id: 'calming' },
      update: {},
      create: {
        id: 'calming',
        name: 'Calming',
        symbol: '☽',
        color: '#B8A9C9',
        ritualMeta {
          haptic: { frequency: 100, intensity: 30 },
          audio: { pitch: 300, volume: 0.4 }
        }
      }
    }),
    prisma.humour.upsert({
      where: { id: 'uplifting' },
      update: {},
      create: {
        id: 'uplifting', 
        name: 'Uplifting',
        symbol: '☀',
        color: '#F5D489',
        ritualMeta {
          haptic: { frequency: 200, intensity: 60 },
          audio: { pitch: 600, volume: 0.6 }
        }
      }
    }),
    prisma.humour.upsert({
      where: { id: 'grounding' },
      update: {},
      create: {
        id: 'grounding',
        name: 'Grounding', 
        symbol: '♁',
        color: '#7C6354',
        ritualMeta {
          haptic: { frequency: 150, intensity: 40 },
          audio: { pitch: 400, volume: 0.5 }
        }
      }
    }),
    prisma.humour.upsert({
      where: { id: 'clarifying' },
      update: {},
      create: {
        id: 'clarifying',
        name: 'Clarifying',
        symbol: '☿',
        color: '#7CB9A0', 
        ritualMeta {
          haptic: { frequency: 250, intensity: 50 },
          audio: { pitch: 500, volume: 0.5 }
        }
      }
    }),
  ])

  console.log('💧 Humours created with ritual meta', humours.length);

  // Create sample essences with full ritual integration
  const essences = [
    {
      folioNumber: 'I',
      slug: 'provence-lavender',
      latinName: 'Lavandula × intermedia',
      commonName: 'Provence Lavender',
      description: 'Harvested at dawn in the Provençal hills, this lavender possesses a sweetness found only in blossoms kissed by the morning\'s first light. Its effect is one of profound calm, like the silence between breaths.',
      humour: 'CALMING',
      rarity: 'RARE',
      season: 'SUMMER',
      extractionMethod: 'Steam Distillation',
      notes: ['Floral', 'Herbaceous', 'Sweet'],
      price: 42.00,
      volumeMl: 5,
      stockQuantity: 50,
      batchNumber: 'N° 724',
      harvestDate: new Date('2024-06-15'),
      distillationHours: 72,
      ritualMeta {
        haptic: { frequency: 120, duration: 150, intensity: 40 },
        audio: { pitch: 350, volume: 0.5, spatialization: 0.7 },
        visual: { waveFrequency: 0.6, waveAmplitude: 12, colorIntensity: 0.8 }
      },
      botanicalInfo: {
        origin: 'Provence, France',
        cultivationMethod: 'Organic, hand-harvested at dawn',
        historicalNotes: 'Lavender has been used since Roman times for its calming properties. The name comes from Latin "lavare" (to wash), as Romans used it in their baths.',
        chemicalComposition: 'Linalool (30-40%), Linalyl acetate (25-38%), Terpinen-4-ol (2-5%)',
        sustainabilityInfo: {
          waterUsage: 'Low - drought resistant',
          carbonFootprint: 'Minimal - local harvesting',
          biodiversity: 'Supports local bee population'
        }
      },
      alchemicalProcess: [
        {
          stepNumber: 1,
          title: 'Solve',
          description: 'The lavender blossoms are gently placed in the still with pure spring water.',
          illustrationUrl: '/illustrations/lavender-solve.jpg'
        },
        {
          stepNumber: 2,
          title: 'Coagula',
          description: 'Steam rises through the botanical matter, carrying the volatile oils.',
          illustrationUrl: '/illustrations/lavender-coagula.jpg'
        },
        {
          stepNumber: 3,
          title: 'Separate',
          description: 'The essential oil separates from the hydrosol in the separator.',
          illustrationUrl: '/illustrations/lavender-separate.jpg'
        },
        {
          stepNumber: 4,
          title: 'Conjoin',
          description: 'The pure essence is bottled under moonlight for maximum potency.',
          illustrationUrl: '/illustrations/lavender-conjoin.jpg'
        }
      ]
    },
    {
      folioNumber: 'II',
      slug: 'tasmanian-eucalyptus',
      latinName: 'Eucalyptus globulus',
      commonName: 'Tasmanian Eucalyptus', 
      description: 'The crisp, clean scent of Tasmania\'s ancient forests. This essence clears the mind as morning mist clears from mountain valleys. Harvested from 100-year-old trees in untouched wilderness.',
      humour: 'CLARIFYING',
      rarity: 'COMMON',
      season: 'AUTUMN',
      extractionMethod: 'Steam Distillation',
      notes: ['Camphorous', 'Fresh', 'Clean'],
      price: 36.00,
      volumeMl: 5,
      stockQuantity: 75,
      batchNumber: 'N° 842',
      harvestDate: new Date('2024-03-22'),
      distillationHours: 48,
      ritualMeta {
        haptic: { frequency: 230, duration: 120, intensity: 50 },
        audio: { pitch: 550, volume: 0.6, spatialization: 0.8 },
        visual: { waveFrequency: 0.8, waveAmplitude: 18, colorIntensity: 0.7 }
      },
      botanicalInfo: {
        origin: 'Tasmania, Australia',
        cultivationMethod: 'Wild-harvested from ancient forests',
        historicalNotes: 'Eucalyptus was introduced to Europe in the 1850s. Aboriginal Australians used it for thousands of years for respiratory ailments.',
        chemicalComposition: '1,8-Cineole (70-85%), α-Pinene (5-15%), Limonene (1-3%)',
        sustainabilityInfo: {
          waterUsage: 'Moderate - native species',
          carbonFootprint: 'Low - wild harvest',
          biodiversity: 'Ancient forest ecosystem preservation'
        }
      }
    },
    {
      folioNumber: 'III',
      slug: 'calabrian-bergamot',
      latinName: 'Citrus bergamia',
      commonName: 'Calabrian Bergamot',
      description: 'From Italy\'s sun-drenched Calabrian coast, this essence captures the joyful brightness of citrus groves at harvest. A note of pure sunlight, hand-picked during the Winter Solstice when the oils are most concentrated.',
      humour: 'UPLIFTING',
      rarity: 'LIMITED',
      season: 'WINTER',
      extractionMethod: 'Cold Press',
      notes: ['Citrus', 'Bright', 'Spicy'],
      price: 48.00,
      volumeMl: 5,
      stockQuantity: 30,
      batchNumber: 'N° 917',
      harvestDate: new Date('2024-12-21'),
      distillationHours: null,
      ritualMeta {
        haptic: { frequency: 200, duration: 180, intensity: 60 },
        audio: { pitch: 600, volume: 0.7, spatialization: 0.9 },
        visual: { waveFrequency: 0.9, waveAmplitude: 22, colorIntensity: 0.9 }
      },
      botanicalInfo: {
        origin: 'Calabria, Italy',
        cultivationMethod: 'Organic, hand-harvested during Winter Solstice',
        historicalNotes: 'Bergamot has been cultivated in Calabria since the 18th century. The name may derive from the Turkish "beg armudi" (lord\'s pear) or from the city of Bergamo where it was first sold.',
        chemicalComposition: 'Limonene (35-45%), Linalyl acetate (25-35%), Linalool (5-15%)',
        sustainabilityInfo: {
          waterUsage: 'High - citrus requires irrigation',
          carbonFootprint: 'Medium - traditional harvesting methods',
          biodiversity: 'Family-owned orchards with intercropping'
        }
      }
    }
  ]

  for (const essence of essences) {
    await prisma.essence.upsert({
      where: { slug: essence.slug },
      update: {},
      create: essence,
    });
    console.log(`🌿 Essence created: ${essence.commonName}`);
  }

  console.log('📚 Creating manuscript folios...');
  const folios = [
    {
      title: 'The Alchemy of Scent',
      slug: 'alchemy-of-scent',
      edition: 'Autumn Equinox MMXXIV',
      excerpt: 'An exploration of how scents transform memory and emotion through alchemical principles.',
      status: 'SENT',
      sentAt: new Date('2024-09-22'),
      openRate: 68.5,
      clickRate: 42.3,
      content: {
        sections: [
          {
            type: 'header',
            content: 'The Solve et Coagula of Fragrance'
          },
          {
            type: 'image',
            url: '/folios/autumn-equinox/header.jpg',
            alt: 'Ancient alchemical manuscript with distillation apparatus'
          },
          {
            type: 'text',
            content: 'In the sacred tradition of alchemy, the principle of "solve et coagula" (dissolve and reconstitute) serves as the foundation for transformation. This same principle governs the creation of our essences, where botanical matter is dissolved through steam or cold press, and the volatile oils are reconstituted into pure aromatic expression.'
          },
          {
            type: 'quote',
            content: 'The perfume maker is not merely a craftsman, but a philosopher who works with the very essence of transformation.',
            author: 'Paracelsus'
          }
        ]
      }
    }
  ]

  for (const folio of folios) {
    await prisma.folio.upsert({
      where: { slug: folio.slug },
      update: {},
      create: folio,
    });
    console.log(`📜 Folio created: ${folio.title}`);
  }

  console.log('✨ Database seeded successfully with ritual integration!');
}

main()
  .catch((e) => {
    console.error('Error seeding database:', e);
    process.exit(1);
  })
  .finally(async () => {
    await prisma.$disconnect();
  });
```

## 8. API Specification

### 8.1 API Endpoints Overview

| Category | Endpoint | Method | Description | Authentication |
|----------|----------|--------|-------------|----------------|
| **Authentication** | /api/auth/signin | POST | User sign in with credentials | None |
| | /api/auth/signout | POST | User sign out | Bearer Token |
| | /api/auth/signup | POST | User registration | None |
| | /api/auth/forgot-password | POST | Request password reset | None |
| | /api/auth/reset-password | POST | Reset password with token | None |
| | /api/auth/session | GET | Get current session | Bearer Token |
| **Products** | /api/products | GET | Get all essences with filtering/pagination | None |
| | /api/products/[slug] | GET | Get single essence by slug | None |
| | /api/products/search | GET | Search essences | None |
| | /api/products/[slug]/related | GET | Get related essences | None |
| **Vial (Cart)** | /api/vial | GET | Get current vial contents | Session/Bearer |
| | /api/vial | POST | Add item to vial | Session/Bearer |
| | /api/vial/[itemId] | PUT | Update vial item quantity | Session/Bearer |
| | /api/vial/[itemId] | DELETE | Remove item from vial | Session/Bearer |
| | /api/vial/clear | POST | Clear vial | Session/Bearer |
| **Orders** | /api/orders | GET | Get user's order history | Bearer Token |
| | /api/orders/[id] | GET | Get single order details | Bearer Token |
| | /api/orders | POST | Create new order (dispatch) | Bearer Token |
| | /api/orders/[id]/status | PUT | Update order status | ADMIN only |
| **Dispatch (Checkout)** | /api/dispatch/payment-intent | POST | Create Stripe payment intent | Session/Bearer |
| | /api/dispatch/webhook | POST | Stripe webhook handler | Stripe Signature |
| **Subscriptions** | /api/subscriptions | GET | Get user's subscriptions | Bearer Token |
| | /api/subscriptions | POST | Create new subscription | Bearer Token |
| | /api/subscriptions/[id]/pause | PUT | Pause subscription | Bearer Token |
| | /api/subscriptions/[id]/resume | PUT | Resume subscription | Bearer Token |
| | /api/subscriptions/[id]/cancel | PUT | Cancel subscription | Bearer Token |
| **Users** | /api/users/me | GET | Get current user profile | Bearer Token |
| | /api/users/me | PUT | Update user profile | Bearer Token |
| | /api/users/me/addresses | GET | Get user's addresses | Bearer Token |
| | /api/users/me/addresses | POST | Add new address | Bearer Token |
| | /api/users/me/addresses/[id] | PUT | Update address | Bearer Token |
| | /api/users/me/addresses/[id] | DELETE | Delete address | Bearer Token |
| **Content** | /api/folios | GET | Get published folios | None |
| | /api/folios/[slug] | GET | Get single folio | None |
| | /api/testimonials | GET | Get testimonials | None |
| | /api/testimonials/featured | GET | Get featured testimonials | None |
| **Ritual** | /api/ritual/preferences | GET | Get user ritual preferences | Bearer Token |
| | /api/ritual/preferences | PUT | Update ritual preferences | Bearer Token |
| | /api/ritual/haptic | POST | Trigger haptic feedback | Session/Bearer |
| | /api/ritual/audio | POST | Trigger audio feedback | Session/Bearer |
| **Admin** | /api/admin/products | GET | Get all products (admin) | ADMIN |
| | /api/admin/products | POST | Create new product | ADMIN |
| | /api/admin/products/[id] | PUT | Update product | ADMIN |
| | /api/admin/products/[id] | DELETE | Delete product | ADMIN |
| | /api/admin/orders | GET | Get all orders (admin) | ADMIN |
| | /api/admin/orders/[id] | GET | Get order details (admin) | ADMIN |
| | /api/admin/users | GET | Get all users (admin) | ADMIN |
| | /api/admin/stock | GET | Get inventory report | ADMIN |

### 8.2 OpenAPI Specification (Sample)

```yaml
openapi: 3.0.0
info:
  title: Atelier Arôme API
  version: 1.0.0
  description: API for artisanal aromatherapy e-commerce platform with ritual integration
servers:
  - url: https://api.atelierarome.com
    description: Production server
  - url: http://localhost:3000
    description: Development server
tags:
  - name: authentication
    description: User authentication
  - name: products
    description: Essence products
  - name: vial
    description: Alchemical collection vial (shopping cart)
  - name: orders
    description: Order management
  - name: dispatch
    description: Checkout and dispatch
  - name: ritual
    description: Multi-sensory ritual experience
paths:
  /api/products:
    get:
      tags:
        - products
      summary: Get all essences
      description: Retrieve a list of essences with optional filtering and pagination
      parameters:
        - in: query
          name: filter
          schema:
            type: string
            enum: [all, calming, uplifting, grounding, clarifying]
          description: Filter by humour
        - in: query
          name: sort
          schema:
            type: string
            enum: [folio, humour, rarity, season, price_asc, price_desc]
          description: Sort results
        - in: query
          name: page
          schema:
            type: integer
            minimum: 1
            default: 1
          description: Page number
        - in: query
          name: limit
          schema:
            type: integer
            minimum: 1
            maximum: 50
            default: 12
          description: Items per page
        - in: query
          name: includeRitualData
          schema:
            type: boolean
            default: false
          description: Include ritual metadata for multi-sensory experience
      responses:
        '200':
          description: Successful operation
          content:
            application/json:
              schema:
                type: object
                properties:
                  items:
                    type: array
                    items:
                      $ref: '#/components/schemas/Essence'
                  pagination:
                    $ref: '#/components/schemas/Pagination'
        '400':
          description: Invalid parameters
  /api/products/{slug}:
    get:
      tags:
        - products
      summary: Get essence by slug
      description: Retrieve a single essence by its slug
      parameters:
        - in: path
          name: slug
          required: true
          schema:
            type: string
          description: Essence slug
        - in: query
          name: includeRitualData
          schema:
            type: boolean
            default: true
          description: Include ritual metadata for multi-sensory experience
      responses:
        '200':
          description: Successful operation
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Essence'
        '404':
          description: Essence not found
  /api/ritual/preferences:
    get:
      tags:
        - ritual
      summary: Get user ritual preferences
      description: Retrieve current user's ritual preferences for multi-sensory experience
      security:
        - bearerAuth: []
      responses:
        '200':
          description: Successful operation
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/RitualPreferences'
        '401':
          description: Unauthorized
    put:
      tags:
        - ritual
      summary: Update user ritual preferences
      description: Update user's ritual preferences for multi-sensory experience
      security:
        - bearerAuth: []
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/RitualPreferencesInput'
      responses:
        '200':
          description: Preferences updated successfully
        '400':
          description: Invalid input
        '401':
          description: Unauthorized
components:
  schemas:
    Essence:
      type: object
      required:
        - id
        - slug
        - latinName
        - commonName
        - price
        - humour
        - folioNumber
      properties:
        id:
          type: string
          format: uuid
        slug:
          type: string
        folioNumber:
          type: string
          example: "I"
        latinName:
          type: string
          example: "Lavandula × intermedia"
        commonName:
          type: string
          example: "Provence Lavender"
        description:
          type: string
        humour:
          type: string
          enum: [calming, uplifting, grounding, clarifying]
        rarity:
          type: string
          enum: [common, rare, limited]
        season:
          type: string
          enum: [spring, summer, autumn, winter]
        extractionMethod:
          type: string
          example: "Steam Distillation"
        notes:
          type: array
          items:
            type: string
          example: ["Floral", "Herbaceous", "Sweet"]
        price:
          type: number
          format: float
        volumeMl:
          type: integer
          default: 5
        stockQuantity:
          type: integer
        isActive:
          type: boolean
          default: true
        batchNumber:
          type: string
          example: "N° 724"
        harvestDate:
          type: string
          format: date-time
        distillationHours:
          type: integer
        images:
          type: array
          items:
            $ref: '#/components/schemas/EssenceImage'
        ritualMetadata:
          $ref: '#/components/schemas/RitualMetadata'
        botanicalInfo:
          $ref: '#/components/schemas/BotanicalInfo'
    EssenceImage:
      type: object
      properties:
        id:
          type: string
          format: uuid
        url:
          type: string
          format: uri
        altText:
          type: string
        width:
          type: integer
        height:
          type: integer
        order:
          type: integer
          default: 0
    RitualMeta
      type: object
      properties:
        id:
          type: string
          format: uuid
        haptic:
          type: object
          properties:
            frequency:
              type: number
              default: 150
            duration:
              type: number
              default: 100
            intensity:
              type: number
              default: 50
        audio:
          type: object
          properties:
            pitch:
              type: number
              default: 440
            volume:
              type: number
              default: 0.5
            spatialization:
              type: number
              default: 0.7
        visual:
          type: object
          properties:
            waveFrequency:
              type: number
              default: 0.7
            waveAmplitude:
              type: number
              default: 15
            colorIntensity:
              type: number
              default: 0.8
    BotanicalInfo:
      type: object
      properties:
        origin:
          type: string
        cultivationMethod:
          type: string
        historicalNotes:
          type: string
        chemicalComposition:
          type: string
        sustainabilityInfo:
          type: object
          properties:
            waterUsage:
              type: string
            carbonFootprint:
              type: string
            biodiversity:
              type: string
    RitualPreferences:
      type: object
      properties:
        enabled:
          type: boolean
          default: true
        haptics:
          type: object
          properties:
            enabled:
              type: boolean
              default: true
            intensity:
              type: number
              default: 50
            duration:
              type: number
              default: 100
            scrollThresholds:
              type: boolean
              default: true
        audio:
          type: object
          properties:
            enabled:
              type: boolean
              default: true
            volume:
              type: number
              default: 0.3
            scrollPosition:
              type: boolean
              default: true
            interactionSounds:
              type: boolean
              default: true
        visual:
          type: object
          properties:
            enabled:
              type: boolean
              default: true
            scrollDirection:
              type: boolean
              default: true
            parallax:
              type: boolean
              default: true
            floatingElements:
              type: boolean
              default: true
        reducedMotion:
          type: boolean
          default: false
        accessibilityMode:
          type: boolean
          default: false
    RitualPreferencesInput:
      type: object
      properties:
        enabled:
          type: boolean
        haptics:
          type: object
          properties:
            enabled:
              type: boolean
            intensity:
              type: number
              minimum: 0
              maximum: 100
            duration:
              type: number
              minimum: 50
              maximum: 500
            scrollThresholds:
              type: boolean
        audio:
          type: object
          properties:
            enabled:
              type: boolean
            volume:
              type: number
              minimum: 0
              maximum: 1
            scrollPosition:
              type: boolean
            interactionSounds:
              type: boolean
        visual:
          type: object
          properties:
            enabled:
              type: boolean
            scrollDirection:
              type: boolean
            parallax:
              type: boolean
            floatingElements:
              type: boolean
        reducedMotion:
          type: boolean
        accessibilityMode:
          type: boolean
    Pagination:
      type: object
      properties:
        page:
          type: integer
        limit:
          type: integer
        total:
          type: integer
        totalPages:
          type: integer
        hasMore:
          type: boolean
  securitySchemes:
    bearerAuth:
      type: http
      scheme: bearer
      bearerFormat: JWT
security:
  - bearerAuth: []
```

## 9. Security Architecture

### 9.1 Authentication & Authorization

#### 9.1.1 Multi-Layered Authentication Strategy
```typescript
// lib/auth.ts - Ritual-Enhanced Authentication
import NextAuth from 'next-auth';
import { PrismaAdapter } from '@auth/prisma-adapter';
import CredentialsProvider from 'next-auth/providers/credentials';
import GoogleProvider from 'next-auth/providers/google';
import { prisma } from '@/lib/prisma';
import { compare, hash } from 'bcryptjs';
import { z } from 'zod';
import { triggerRitualEvent } from '@/services/ritual.service';
import { generateTOTP, verifyTOTP } from '@/lib/totp';
import { sendTwoFactorCode } from '@/services/email.service';

const loginSchema = z.object({
  email: z.string().email(),
  password: z.string().min(8),
  ritualConsent: z.boolean().optional(), // User consent for ritual experience
  twoFactorCode: z.string().optional(),
});

export const {
  handlers: { GET, POST },
  auth,
  signIn,
  signOut,
} = NextAuth({
  adapter: PrismaAdapter(prisma),
  session: {
    strategy: 'jwt',
    maxAge: 30 * 24 * 60 * 60, // 30 days
    updateAge: 24 * 60 * 60, // 24 hours
  },
  pages: {
    signIn: '/login',
    signOut: '/logout',
    error: '/auth/error',
    newUser: '/welcome',
    verifyRequest: '/verify-email',
    checkYourEmail: '/check-your-email',
  },
  providers: [
    CredentialsProvider({
      name: 'credentials',
      credentials: {
        email: { label: 'Email', type: 'email' },
        password: { label: 'Password', type: 'password' },
        ritualConsent: { 
          label: 'Enable ritual experience', 
          type: 'checkbox',
          placeholder: 'Allow haptic and audio feedback for enhanced experience'
        },
        twoFactorCode: { label: 'Two-Factor Code', type: 'text' },
      },
      async authorize(credentials) {
        const parsed = loginSchema.safeParse(credentials);
        if (!parsed.success) {
          throw new Error('Invalid credentials');
        }

        const { email, password, ritualConsent = false, twoFactorCode } = parsed.data;

        const user = await prisma.user.findUnique({
          where: { email },
          select: {
            id: true,
            email: true,
            name: true,
            password: true,
            image: true,
            role: true,
            emailVerified: true,
            ritualPreferences: true, // Include ritual preferences
            twoFactorEnabled: true,
            twoFactorSecret: true,
          },
        });

        if (!user) {
          await triggerRitualEvent('auth_failed', { reason: 'user_not_found', email });
          throw new Error('No user found with this email');
        }

        if (!user.password) {
          await triggerRitualEvent('auth_failed', { reason: 'no_password', userId: user.id });
          throw new Error('User does not have a password set');
        }

        const isValid = await compare(password, user.password);
        if (!isValid) {
          await triggerRitualEvent('auth_failed', { reason: 'invalid_password', userId: user.id });
          
          // Add rate limiting after failed attempts
          const failedAttempts = await prisma.failedLoginAttempt.count({
            where: { 
              userId: user.id, 
              createdAt: { gt: new Date(Date.now() - 15 * 60 * 1000) } // 15 minutes
            }
          });
          
          if (failedAttempts >= 3) {
            await prisma.user.update({
              where: { id: user.id },
               { lockedUntil: new Date(Date.now() + 30 * 60 * 1000) } // 30 minutes lock
            });
            throw new Error('Account temporarily locked due to multiple failed attempts');
          }
          
          await prisma.failedLoginAttempt.create({
            data: { userId: user.id, ipAddress: '127.0.0.1' } // TODO: Get real IP
          });
          
          throw new Error('Invalid password');
        }

        // Two-factor authentication
        if (user.twoFactorEnabled && user.twoFactorSecret) {
          if (!twoFactorCode) {
            throw new Error('Two-factor authentication required');
          }

          const isValidCode = verifyTOTP(twoFactorCode, user.twoFactorSecret);
          if (!isValidCode) {
            await triggerRitualEvent('auth_failed', { reason: 'invalid_2fa', userId: user.id });
            throw new Error('Invalid two-factor code');
          }
        }

        // Update ritual preferences if consent given
        if (ritualConsent && !user.ritualPreferences?.enabled) {
          await prisma.user.update({
            where: { id: user.id },
            data: {
              ritualPreferences: {
                upsert: {
                  create: { 
                    enabled: true,
                    haptics: { enabled: true },
                    audio: { enabled: true },
                    visual: { enabled: true }
                  },
                  update: { enabled: true }
                }
              }
            }
          });
          
          await triggerRitualEvent('ritual_enabled', { userId: user.id });
        }

        // Clear failed attempts on successful login
        await prisma.failedLoginAttempt.deleteMany({
          where: { userId: user.id }
        });

        await triggerRitualEvent('auth_success', { 
          userId: user.id, 
          ritualEnabled: ritualConsent || user.ritualPreferences?.enabled,
          role: user.role
        });

        return {
          id: user.id,
          email: user.email,
          name: user.name,
          image: user.image,
          role: user.role,
          emailVerified: user.emailVerified,
          ritualPreferences: user.ritualPreferences || { enabled: ritualConsent }
        };
      },
    }),
    GoogleProvider({
      clientId: process.env.GOOGLE_CLIENT_ID!,
      clientSecret: process.env.GOOGLE_CLIENT_SECRET!,
      authorization: {
        params: {
          prompt: 'consent',
          access_type: 'offline',
          response_type: 'code',
          scope: 'openid email profile',
        },
      },
      profile(profile) {
        return {
          id: profile.sub,
          email: profile.email,
          name: profile.name,
          image: profile.picture,
          role: 'customer',
          ritualPreferences: { enabled: false }, // Default to disabled for OAuth
        };
      }
    }),
  ],
  callbacks: {
    async jwt({ token, user, trigger, session, account }) {
      if (user) {
        token.id = user.id;
        token.role = user.role;
        token.emailVerified = user.emailVerified;
        token.ritualPreferences = user.ritualPreferences;
        token.twoFactorEnabled = user.twoFactorEnabled;
      }

      // Handle OAuth accounts
      if (account?.provider === 'google' && user) {
        // Check if user exists in database
        const dbUser = await prisma.user.findUnique({
          where: { email: user.email },
          select: { id: true, emailVerified: true }
        });
        
        if (!dbUser) {
          // Create user if doesn't exist
          await prisma.user.create({
            data: {
              email: user.email,
              name: user.name,
              image: user.image,
              emailVerified: new Date(),
              role: 'customer',
            }
          });
        } else if (!dbUser.emailVerified) {
          // Verify email if not verified
          await prisma.user.update({
            where: { id: dbUser.id },
             { emailVerified: new Date() }
          });
        }
      }

      if (trigger === 'update' && session) {
        if (session.name) token.name = session.name;
        if (session.email) token.email = session.email;
        
        // Handle ritual preference updates
        if (session.ritualPreferences) {
          token.ritualPreferences = session.ritualPreferences;
          await triggerRitualEvent('ritual_preferences_updated', {
            userId: token.id,
            preferences: session.ritualPreferences
          });
        }
        
        // Handle two-factor updates
        if (session.twoFactorEnabled !== undefined) {
          token.twoFactorEnabled = session.twoFactorEnabled;
          if (session.twoFactorEnabled) {
            // Generate new 2FA secret
            const secret = generateTOTP();
            await prisma.user.update({
              where: { id: token.id as string },
              data: { twoFactorSecret: secret }
            });
            token.twoFactorSecret = secret;
          }
        }
      }

      // Revalidate session periodically and ritual preferences
      if (Date.now() - (token.iat ?? 0) * 1000 > 24 * 60 * 60 * 1000) {
        const freshUser = await prisma.user.findUnique({
          where: { id: token.id as string },
          select: { 
            role: true, 
            emailVerified: true,
            ritualPreferences: true,
            twoFactorEnabled: true,
            lockedUntil: true
          },
        });
        if (freshUser) {
          token.role = freshUser.role;
          token.emailVerified = freshUser.emailVerified;
          token.ritualPreferences = freshUser.ritualPreferences;
          token.twoFactorEnabled = freshUser.twoFactorEnabled;
          
          // Check if account is locked
          if (freshUser.lockedUntil && freshUser.lockedUntil > new Date()) {
            throw new Error('Account is temporarily locked');
          }
        }
      }

      return token;
    },
    async session({ session, token }) {
      if (token) {
        session.user.id = token.id as string;
        session.user.role = token.role as string;
        session.user.emailVerified = token.emailVerified as Date | null;
        session.user.ritualPreferences = token.ritualPreferences as any;
        session.user.twoFactorEnabled = token.twoFactorEnabled as boolean;
      }
      return session;
    },
    async signIn({ user, account, profile }) {
      // Only allow verified email addresses for Google sign-in
      if (account?.provider === 'google' && profile?.email_verified === false) {
        await triggerRitualEvent('auth_blocked', { 
          reason: 'unverified_email', 
          provider: account.provider,
          email: profile.email
        });
        return false;
      }
      
      // Log successful sign-in for security monitoring
      await prisma.auditLog.create({
         {
          userId: user.id,
          event: 'USER_SIGN_IN',
          meta { 
            method: account?.provider || 'password',
            ipAddress: '127.0.0.1' // TODO: Get real IP
          },
        },
      });
      
      return true;
    },
  },
  events: {
    async signIn({ user }) {
      // Log successful sign-ins for security monitoring
      await prisma.auditLog.create({
         {
          userId: user.id,
          event: 'USER_SIGN_IN',
          meta { method: 'password' },
        },
      });
    },
    async createUser({ user }) {
      // Send verification email
      await triggerRitualEvent('user_created', { userId: user.id });
      
      // Log user creation
      await prisma.auditLog.create({
        data: {
          userId: user.id,
          event: 'USER_CREATED',
          meta { email: user.email },
        },
      });
    },
    async linkAccount({ user, account }) {
      // Log social account linking
      await prisma.auditLog.create({
         {
          userId: user.id,
          event: 'ACCOUNT_LINKED',
          meta { provider: account.provider },
        },
      });
      
      await triggerRitualEvent('account_linked', {
        userId: user.id,
        provider: account.provider
      });
    },
    async session: {
      strategy: 'jwt',
      maxAge: 30 * 24 * 60 * 60, // 30 days
      updateAge: 24 * 60 * 60, // 24 hours
    },
    events: {
      signOut: async ({ token }) => {
        await triggerRitualEvent('user_signed_out', { userId: token.id });
      }
    }
  },
  secret: process.env.NEXTAUTH_SECRET,
});

// Type augmentation for NextAuth
declare module 'next-auth' {
  interface Session {
    user: {
      id: string;
      role: string;
      email: string;
      name: string;
      image?: string;
      emailVerified?: Date | null;
      ritualPreferences?: {
        enabled: boolean;
        haptics?: { enabled: boolean };
        audio?: { enabled: boolean };
        visual?: { enabled: boolean };
      };
      twoFactorEnabled?: boolean;
    };
  }
  interface User {
    role: string;
    emailVerified?: Date | null;
    ritualPreferences?: {
      enabled: boolean;
      haptics?: { enabled: boolean };
      audio?: { enabled: boolean };
      visual?: { enabled: boolean };
    };
    twoFactorEnabled?: boolean;
    twoFactorSecret?: string;
    lockedUntil?: Date;
  }
  interface Account {
    provider: string;
  }
}
declare module 'next-auth/jwt' {
  interface JWT {
    id: string;
    role: string;
    emailVerified?: Date | null;
    ritualPreferences?: {
      enabled: boolean;
      haptics?: { enabled: boolean };
      audio?: { enabled: boolean };
      visual?: { enabled: boolean };
    };
    twoFactorEnabled?: boolean;
    twoFactorSecret?: string;
    lockedUntil?: Date;
  }
}
```

#### 9.1.2 Role-Based Access Control (RBAC)
```typescript
// lib/auth/rbac.ts
import { auth } from '@/lib/auth';

export const permissions = {
  // Admin permissions
  ADMIN: [
    'manage:users',
    'manage:products',
    'manage:orders',
    'manage:inventory',
    'manage:content',
    'view:analytics',
    'manage:settings'
  ],
  // Curator permissions
  CURATOR: [
    'manage:products',
    'manage:content',
    'view:orders',
  ],
  // Alchemist permissions
  ALCHEMIST: [
    'manage:inventory',
    'view:products',
    'view:orders',
  ],
  // Customer permissions
  CUSTOMER: [
    'manage:profile',
    'manage:addresses',
    'manage:cart',
    'manage:orders',
    'view:products',
  ],
} as const;

export type Role = keyof typeof permissions;

export async function hasPermission(permission: string): Promise<boolean> {
  const session = await auth();
  if (!session?.user?.role) return false;
  
  const rolePermissions = permissions[session.user.role as Role];
  return rolePermissions.includes(permission) || rolePermissions.includes('*');
}

export async function requirePermission(permission: string): Promise<void> {
  const hasPerm = await hasPermission(permission);
  if (!hasPerm) {
    throw new Error('Unauthorized: Insufficient permissions');
  }
}

// Middleware for API routes
export function withRBAC(handler: any, requiredPermission: string) {
  return async (req: Request, context: any) => {
    try {
      await requirePermission(requiredPermission);
      return handler(req, context);
    } catch (error) {
      return new Response(JSON.stringify({ error: 'Unauthorized' }), {
        status: 403,
        headers: { 'Content-Type': 'application/json' },
      });
    }
  };
}

// Next.js middleware for page protection
export async function middleware(req: Request) {
  const session = await auth();
  
  // Public routes
  const publicRoutes = ['/login', '/register', '/forgot-password', '/api/auth'];
  
  if (publicRoutes.some(route => req.url.includes(route))) {
    return;
  }
  
  // Admin routes protection
  const adminRoutes = ['/admin', '/atelier'];
  if (adminRoutes.some(route => req.url.includes(route)) && session?.user?.role !== 'ADMIN') {
    return new Response('Unauthorized', { status: 403 });
  }
  
  // Customer account protection
  const accountRoutes = ['/account', '/vial', '/dispatch'];
  if (accountRoutes.some(route => req.url.includes(route)) && !session) {
    return new Response('Unauthorized', { status: 401 });
  }
  
  return;
}
```

### 9.2 Security Headers & CSP
```typescript
// middleware.ts - Security-focused middleware
import { NextResponse } from 'next/server';
import type { NextRequest } from 'next/server';
import { auth } from '@/lib/auth';

export async function middleware(request: NextRequest) {
  const session = await auth();
  const response = NextResponse.next();

  // Security headers
  response.headers.set('X-Content-Type-Options', 'nosniff');
  response.headers.set('X-Frame-Options', 'DENY');
  response.headers.set('X-XSS-Protection', '1; mode=block');
  response.headers.set('Referrer-Policy', 'strict-origin-when-cross-origin');
  response.headers.set('Permissions-Policy', 'geolocation=(), camera=(), microphone=()'); // Disable sensitive APIs

  // Content Security Policy with ritual experience support
  const csp = `
    default-src 'self';
    script-src 'self' 'unsafe-eval' 'unsafe-inline' https://*.stripe.com https://*.vercel.com https://*.sentry.io https://*.clarity.ms;
    style-src 'self' 'unsafe-inline' https://fonts.googleapis.com https://*.vercel.com;
    img-src 'self'  https://*.googleusercontent.com https://*.cloudinary.com https://*.stripe.com blob:;
    font-src 'self' https://fonts.gstatic.com ;
    connect-src 'self' https://*.stripe.com https://*.resend.com https://*.upstash.io https://*.sentry.io https://*.clarity.ms https://vercel.com;
    frame-src 'self' https://*.stripe.com;
    media-src 'self' blob: ;
    object-src 'none';
    base-uri 'self';
    form-action 'self';
    manifest-src 'self';
  `.replace(/\s{2,}/g, ' ').trim();

  // Add CSP header
  response.headers.set('Content-Security-Policy', csp);

  // Rate limiting headers
  response.headers.set('X-RateLimit-Limit', '100');
  response.headers.set('X-RateLimit-Remaining', '99');
  response.headers.set('X-RateLimit-Reset', '60');

  // Cache control for sensitive pages
  const sensitivePaths = ['/account', '/dispatch', '/admin', '/api'];
  if (sensitivePaths.some(path => request.nextUrl.pathname.startsWith(path))) {
    response.headers.set('Cache-Control', 'no-store, no-cache, must-revalidate, proxy-revalidate');
    response.headers.set('Pragma', 'no-cache');
    response.headers.set('Expires', '0');
  }

  // HSTS header for production
  if (process.env.NODE_ENV === 'production') {
    response.headers.set('Strict-Transport-Security', 'max-age=63072000; includeSubDomains; preload');
  }

  // Security cookies
  if (session?.user) {
    response.cookies.set('atelier_session', 'active', {
      httpOnly: true,
      secure: process.env.NODE_ENV === 'production',
      sameSite: 'lax',
      maxAge: 30 * 24 * 60 * 60, // 30 days
      path: '/',
    });
  }

  return response;
}

export const config = {
  matcher: [
    /*
     * Match all request paths except for the ones starting with:
     * - api (API routes)
     * - _next/static (static files)
     * - _next/image (image optimization files)
     * - favicon.ico (favicon file)
     */
    '/((?!api|_next/static|_next/image|favicon.ico).*)',
  ],
};
```

### 9.3 Rate Limiting
```typescript
// lib/rate-limit.ts
import { Redis } from '@upstash/redis';
import { Ratelimit } from '@upstash/ratelimit';

const redis = new Redis({
  url: process.env.UPSTASH_REDIS_URL!,
  token: process.env.UPSTASH_REDIS_TOKEN!,
});

const ratelimit = new Ratelimit({
  redis,
  limiter: Ratelimit.slidingWindow(10, '10 s'), // 10 requests per 10 seconds
  analytics: true,
});

export async function checkRateLimit(identifier: string) {
  const result = await ratelimit.limit(identifier);
  
  return {
    success: result.success,
    limit: result.limit,
    remaining: result.remaining,
    reset: result.reset,
    retryAfter: result.retryAfter,
  };
}

// Usage example in API routes
export async function withRateLimit(
  request: NextRequest, 
  options: { 
    points?: number; 
    duration?: string;
    identifier?: string;
  } = {}
) {
  const { points = 10, duration = '10 s', identifier = request.ip } = options;
  
  // Create custom rate limiter for this request
  const customRatelimit = new Ratelimit({
    redis,
    limiter: Ratelimit.slidingWindow(points, duration),
    analytics: true,
  });

  const result = await customRatelimit.limit(identifier);
  
  if (!result.success) {
    return NextResponse.json(
      { 
        error: 'Too many requests', 
        retryAfter: result.retryAfter 
      },
      {
        status: 429,
        headers: {
          'Retry-After': result.retryAfter.toString(),
          'X-RateLimit-Limit': result.limit.toString(),
          'X-RateLimit-Remaining': '0',
          'X-RateLimit-Reset': result.reset.toString(),
        },
      }
    );
  }
  
  return result;
}

// Apply rate limiting to specific endpoints
export const rateLimitedEndpoints = {
  auth: {
    signin: { points: 5, duration: '1 m' }, // 5 attempts per minute
    signup: { points: 3, duration: '1 h' }, // 3 signups per hour
    forgotPassword: { points: 2, duration: '1 h' }, // 2 password resets per hour
  },
  products: {
    search: { points: 20, duration: '1 m' }, // 20 searches per minute
  },
  checkout: {
    createPaymentIntent: { points: 3, duration: '1 m' }, // 3 payment attempts per minute
  }
};
```

### 9.4 Data Encryption & Security
```typescript
// lib/crypto.ts - Application-level encryption
import crypto from 'crypto';
import { z } from 'zod';

const encryptionKey = process.env.ENCRYPTION_KEY;
if (!encryptionKey || encryptionKey.length < 32) {
  throw new Error('ENCRYPTION_KEY must be at least 32 characters long');
}

const algorithm = 'aes-256-gcm';
const ivLength = 16;
const authTagLength = 16;
const key = Buffer.from(encryptionKey, 'utf8');

export interface EncryptedData {
  iv: string;
  authTag: string;
  encryptedData: string;
}

export function encryptData(data: any): EncryptedData {
  try {
    const iv = crypto.randomBytes(ivLength);
    const cipher = crypto.createCipheriv(algorithm, key, iv);
    
    const stringified = JSON.stringify(data);
    const encrypted = Buffer.concat([
      cipher.update(stringified, 'utf8'),
      cipher.final()
    ]);
    
    const authTag = cipher.getAuthTag();
    
    return {
      iv: iv.toString('hex'),
      authTag: authTag.toString('hex'),
      encryptedData: encrypted.toString('hex')
    };
  } catch (error) {
    console.error('Encryption failed:', error);
    throw new Error('Failed to encrypt data');
  }
}

export function decryptData(encryptedData: EncryptedData): any {
  try {
    const iv = Buffer.from(encryptedData.iv, 'hex');
    const authTag = Buffer.from(encryptedData.authTag, 'hex');
    const encrypted = Buffer.from(encryptedData.encryptedData, 'hex');
    
    const decipher = crypto.createDecipheriv(algorithm, key, iv);
    decipher.setAuthTag(authTag);
    
    const decrypted = Buffer.concat([
      decipher.update(encrypted),
      decipher.final()
    ]);
    
    return JSON.parse(decrypted.toString('utf8'));
  } catch (error) {
    console.error('Decryption failed:', error);
    throw new Error('Failed to decrypt data or data has been tampered with');
  }
}

// Sensitive data schema validation
export const sensitiveDataSchema = z.object({
  // Personal identifiable information
  firstName: z.string().optional(),
  lastName: z.string().optional(),
  email: z.string().email().optional(),
  phone: z.string().optional(),
  address: z.object({
    street: z.string(),
    city: z.string(),
    state: z.string(),
    postalCode: z.string(),
    country: z.string()
  }).optional(),
  
  // Payment information (never stored directly)
  paymentMethod: z.object({
    last4: z.string(),
    brand: z.string(),
    expMonth: z.number(),
    expYear: z.number()
  }).optional(),
  
  // Health information (for aromatherapy recommendations)
  healthConditions: z.array(z.string()).optional(),
  allergies: z.array(z.string()).optional(),
  preferences: z.object({
    scents: z.array(z.string()).optional(),
    intensity: z.enum(['light', 'medium', 'strong']).optional()
  }).optional()
});

// PII encryption service
export class PIIEncryptionService {
  static encryptPII( any): EncryptedData {
    const validated = sensitiveDataSchema.parse(data);
    return encryptData(validated);
  }
  
  static decryptPII(encrypted: EncryptedData): any {
    const decrypted = decryptData(encrypted);
    return sensitiveDataSchema.parse(decrypted);
  }
  
  static maskPII( any): any {
    // Create a masked version for logging/display
    const masked = { ...data };
    
    if (masked.email) {
      const [local, domain] = masked.email.split('@');
      masked.email = `${local.charAt(0)}${'*'.repeat(local.length - 2)}${local.charAt(local.length - 1)}@${domain}`;
    }
    
    if (masked.phone) {
      masked.phone = '***-***-' + masked.phone.slice(-4);
    }
    
    if (masked.address) {
      masked.address = {
        ...masked.address,
        street: '*** ' + masked.address.street.split(' ').slice(-1)[0]
      };
    }
    
    return masked;
  }
}

// GDPR compliance utilities
export class GDPRService {
  static async anonymizeUserData(userId: string) {
    try {
      // Anonymize user data for GDPR compliance
      await prisma.user.update({
        where: { id: userId },
         {
          name: 'Anonymous User',
          email: `anonymous-${crypto.randomBytes(8).toString('hex')}@atelierarome.com`,
          image: null,
          ritualPreferences: null,
          // Keep order history for business purposes but anonymize personal details
        }
      });
      
      // Anonymize order personal information
      await prisma.order.updateMany({
        where: { userId },
        data: {
          customerEmail: 'anonymous@example.com',
          customerName: 'Anonymous Customer',
          shippingAddress: PIIEncryptionService.maskPII({
            // Keep essential shipping data but anonymize personal details
          }),
          billingAddress: PIIEncryptionService.maskPII({
            // Keep essential billing data but anonymize personal details
          })
        }
      });
      
      console.log(`GDPR anonymization completed for user ${userId}`);
    } catch (error) {
      console.error('GDPR anonymization failed:', error);
      throw new Error('Failed to anonymize user data');
    }
  }
  
  static async exportUserData(userId: string) {
    try {
      const user = await prisma.user.findUnique({
        where: { id: userId },
        include: {
          orders: true,
          addresses: true,
          subscriptions: true,
          testimonials: true
        }
      });
      
      if (!user) throw new Error('User not found');
      
      // Create GDPR-compliant data export
      const exportData = {
        personalInformation: {
          name: user.name,
          email: user.email,
          createdAt: user.createdAt,
          lastLogin: user.updatedAt
        },
        orderHistory: user.orders.map(order => ({
          orderNumber: order.orderNumber,
          date: order.createdAt,
          status: order.status,
          items: order.items.map(item => ({
            essence: item.essence.commonName,
            quantity: item.quantity,
            price: item.unitPrice
          })),
          total: order.total
        })),
        addresses: user.addresses,
        subscriptions: user.subscriptions,
        preferences: {
          ritualPreferences: user.ritualPreferences,
          // Add other preferences
        },
        dataProcessing: {
          purposes: [
            'Order fulfillment',
            'Customer support',
            'Personalized experience',
            'Legal compliance'
          ],
          retentionPeriod: '2 years after last order',
          dataController: 'Atelier Arôme GmbH',
          contactEmail: 'privacy@atelierarome.com'
        }
      };
      
      return exportData;
    } catch (error) {
      console.error('GDPR data export failed:', error);
      throw new Error('Failed to export user data');
    }
  }
}
```

## 10. DevOps & Infrastructure

### 10.1 Infrastructure Diagram
```mermaid
graph TD
    subgraph CDN["Content Delivery Network"]
        VercelEdge[Vercel Edge Network]
        VercelEdge -->|Static Asset Caching| StaticAssets
        VercelEdge -->|Image Optimization| Images
        VercelEdge -->|Edge Functions| Functions
        VercelEdge -->|DDoS Protection| Security
        CloudflareDNS[Cloudflare DNS]
    end

    subgraph Client["Client Devices"]
        Desktop[Desktop Browser]
        Mobile[Mobile Browser]
        Tablet[Tablet Browser]
        Kiosk[Kiosk (Atelier)]
    end

    subgraph Application["Application Layer"]
        VercelProd[Vercel Production]
        VercelPreview[Vercel Preview]
        VercelDev[Vercel Development]
        NextJS[Next.js 14 Application]
        NextJS -->|React Server Components| RSC
        NextJS -->|API Routes| API
        NextJS -->|Server Actions| Actions
        NextJS -->|Middleware| Middleware
        NextJS -->|Authentication| Auth
    end

    subgraph Database["Database Layer"]
        NeonPrimary[Neon PostgreSQL Primary]
        NeonBranch[Neon PostgreSQL Branches]
        UpstashRedis[Upstash Redis]
        NeonPrimary -->|Read Replicas| NeonReplicas
        UpstashRedis -->|Cache| CachedData
    end

    subgraph Storage["Storage Layer"]
        CloudinaryMedia[Cloudinary Media Storage]
        VercelBlob[Vercel Blob Storage]
        CloudinaryMedia -->|Optimized Images| OptimizedAssets
    end

    subgraph External["External Services"]
        Stripe[Stripe Payments]
        Resend[Resend Email]
        Sanity[Sanity CMS]
        Sentry[Sentry Monitoring]
        GitHub[GitHub Repository]
        GitHub -->|CI/CD| VercelProd
        GitHub -->|CI/CD| VercelPreview
        GitHub -->|CI/CD| VercelDev
    end

    Client --> CDN
    CDN --> Application
    Application --> Database
    Application --> Storage
    Application --> External
    Database --> External
    Storage --> External
```

### 10.2 Vercel Configuration
```json
{
  "version": 2,
  "buildCommand": "pnpm run build",
  "installCommand": "pnpm install",
  "framework": "nextjs",
  "devCommand": "pnpm run dev",
  "outputDirectory": ".next",
  
  "buildEnv": {
    "PRISMA_CLIENT_ENGINE_TYPE": "library"
  },
  
  "env": {
    "DATABASE_URL": "@database_url",
    "NEXTAUTH_URL": "@nextauth_url",
    "NEXTAUTH_SECRET": "@nextauth_secret",
    "STRIPE_SECRET_KEY": "@stripe_secret_key",
    "STRIPE_PUBLIC_KEY": "@stripe_public_key",
    "RESEND_API_KEY": "@resend_api_key",
    "CLOUDINARY_URL": "@cloudinary_url",
    "UPSTASH_REDIS_URL": "@upstash_redis_url",
    "UPSTASH_REDIS_TOKEN": "@upstash_redis_token",
    "SENTRY_DSN": "@sentry_dsn",
    "SANITY_PROJECT_ID": "@sanity_project_id",
    "SANITY_DATASET": "@sanity_dataset",
    "SANITY_TOKEN": "@sanity_token"
  },
  
  "regions": ["fra1"], // Frankfurt for EU customers
  
  "crons": [
    {
      "path": "/api/cron/inventory-check",
      "schedule": "0 2 * * *" // Every day at 2 AM
    },
    {
      "path": "/api/cron/subscription-billing",
      "schedule": "0 3 1 * *" // Every month on the 1st at 3 AM
    },
    {
      "path": "/api/cron/cleanup-expired-vials",
      "schedule": "0 4 * * *" // Every day at 4 AM
    }
  ],
  
  "headers": [
    {
      "source": "/(.*)",
      "headers": [
        {
          "key": "X-Content-Type-Options",
          "value": "nosniff"
        },
        {
          "key": "X-Frame-Options",
          "value": "DENY"
        },
        {
          "key": "X-XSS-Protection",
          "value": "1; mode=block"
        },
        {
          "key": "Referrer-Policy",
          "value": "strict-origin-when-cross-origin"
        },
        {
          "key": "Permissions-Policy",
          "value": "geolocation=(), camera=(), microphone=()"
        }
      ]
    }
  ],
  
  "redirects": [
    {
      "source": "/old-path",
      "destination": "/new-path",
      "permanent": true
    }
  ],
  
  "rewrites": [
    {
      "source": "/api/health",
      "destination": "/api/health"
    }
  ]
}
```

### 10.3 GitHub Actions CI/CD Pipeline
```yaml
# .github/workflows/deploy.yml
name: Deploy to Vercel

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v4
      
      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'pnpm'
      
      - name: Install dependencies
        run: pnpm install
      
      - name: Run type checking
        run: pnpm typecheck
      
      - name: Run linting
        run: pnpm lint
      
      - name: Run unit tests
        run: pnpm test --coverage
        env:
          DATABASE_URL: ${{ secrets.TEST_DATABASE_URL }}
          NEXTAUTH_SECRET: test-secret
          NEXTAUTH_URL: http://localhost:3000
      
      - name: Upload coverage to Codecov
        uses: codecov/codecov-action@v4
        with:
          token: ${{ secrets.CODECOV_TOKEN }}
          files: ./coverage/lcov.info
  
  build:
    runs-on: ubuntu-latest
    needs: test
    steps:
      - name: Checkout code
        uses: actions/checkout@v4
      
      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'pnpm'
      
      - name: Install dependencies
        run: pnpm install
      
      - name: Build project
        run: pnpm build
        env:
          DATABASE_URL: ${{ secrets.PRODUCTION_DATABASE_URL }}
          NEXTAUTH_SECRET: ${{ secrets.NEXTAUTH_SECRET }}
          NEXTAUTH_URL: https://atelierarome.com
          NEXT_PUBLIC_STRIPE_PUBLIC_KEY: ${{ secrets.NEXT_PUBLIC_STRIPE_PUBLIC_KEY }}
  
  analyze:
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Checkout code
        uses: actions/checkout@v4
      
      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'pnpm'
      
      - name: Install dependencies
        run: pnpm install
      
      - name: Analyze bundle size
        run: pnpm analyze
        env:
          ANALYZE: true
      
      - name: Run Lighthouse audit
        run: pnpm lighthouse
        env:
          BASE_URL: ${{ github.event_name == 'push' && 'https://atelierarome.com' || 'https://atelierarome-git-' + github.head_ref + '.vercel.app' }}
      
      - name: Security scan
        run: pnpm security-scan
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
  
  deploy-preview:
    if: github.event_name == 'pull_request'
    runs-on: ubuntu-latest
    needs: analyze
    steps:
      - name: Checkout code
        uses: actions/checkout@v4
      
      - name: Deploy to Vercel Preview
        uses: amondnet/vercel-action@v30
        with:
          vercel-token: ${{ secrets.VERCEL_TOKEN }}
          github-token: ${{ secrets.GITHUB_TOKEN }}
          vercel-org-id: ${{ secrets.VERCEL_ORG_ID }}
          vercel-project-id: ${{ secrets.VERCEL_PROJECT_ID }}
          working-directory: .
          alias-domains: preview-${{ github.event.number }}.atelierarome.com
  
  deploy-production:
    if: github.ref == 'refs/heads/main'
    runs-on: ubuntu-latest
    needs: analyze
    steps:
      - name: Checkout code
        uses: actions/checkout@v4
      
      - name: Deploy to Vercel Production
        uses: amondnet/vercel-action@v30
        with:
          vercel-token: ${{ secrets.VERCEL_TOKEN }}
          github-token: ${{ secrets.GITHUB_TOKEN }}
          vercel-org-id: ${{ secrets.VERCEL_ORG_ID }}
          vercel-project-id: ${{ secrets.VERCEL_PROJECT_ID }}
          working-directory: .
          production: true
          alias-domains: atelierarome.com www.atelierarome.com
      
      - name: Run production smoke tests
        run: pnpm test:e2e
        env:
          BASE_URL: https://atelierarome.com
          STRIPE_PUBLIC_KEY: ${{ secrets.NEXT_PUBLIC_STRIPE_PUBLIC_KEY }}
          TEST_EMAIL: ${{ secrets.TEST_EMAIL }}
          TEST_PASSWORD: ${{ secrets.TEST_PASSWORD }}
      
      - name: Deploy to staging
        if: always()
        uses: amondnet/vercel-action@v30
        with:
          vercel-token: ${{ secrets.VERCEL_TOKEN }}
          github-token: ${{ secrets.GITHUB_TOKEN }}
          vercel-org-id: ${{ secrets.VERCEL_ORG_ID }}
          vercel-project-id: ${{ secrets.VERCEL_PROJECT_ID }}
          working-directory: .
          alias-domains: staging.atelierarome.com
          production: true
  
  notify:
    runs-on: ubuntu-latest
    needs: [deploy-production, deploy-preview]
    if: always()
    steps:
      - name: Slack notification
        uses: slackapi/slack-github-action@v1.24.0
        with:
          payload: |
            {
              "text": "Deployment completed for ${GITHUB_REF}",
              "blocks": [
                {
                  "type": "header",
                  "text": {
                    "type": "plain_text",
                    "text": "🚀 Deployment Completed"
                  }
                },
                {
                  "type": "section",
                  "fields": [
                    {
                      "type": "mrkdwn",
                      "text": "*Repository:*\n${GITHUB_REPOSITORY}"
                    },
                    {
                      "type": "mrkdwn",
                      "text": "*Branch:*\n${GITHUB_REF}"
                    },
                    {
                      "type": "mrkdwn",
                      "text": "*Status:*\n${{ job.status }}"
                    },
                    {
                      "type": "mrkdwn",
                      "text": "*Deployed by:*\n${GITHUB_ACTOR}"
                    }
                  ]
                },
                {
                  "type": "actions",
                  "elements": [
                    {
                      "type": "button",
                      "text": {
                        "type": "plain_text",
                        "text": "View Deployment"
                      },
                      "url": "${{ github.event_name == 'push' && 'https://atelierarome.com' || 'https://atelierarome-git-' + github.head_ref + '.vercel.app' }}"
                    },
                    {
                      "type": "button",
                      "text": {
                        "type": "plain_text",
                        "text": "View GitHub Actions"
                      },
                      "url": "${{ github.server_url }}/${{ github.repository }}/actions/runs/${{ github.run_id }}"
                    }
                  ]
                }
              ]
            }
        env:
          SLACK_WEBHOOK_URL: ${{ secrets.SLACK_WEBHOOK_URL }}
```

### 10.4 Environment Variables Management
```bash
# .env.example
# This file should NOT be committed to version control
# Copy this file to .env.local and fill in the values

# Database
DATABASE_URL="postgresql://user:password@localhost:5432/atelier_arome"
DIRECT_URL="postgresql://user:password@localhost:5432/atelier_arome"

# Authentication
NEXTAUTH_URL="http://localhost:3000"
NEXTAUTH_SECRET="your_nextauth_secret_here"

# Stripe
STRIPE_SECRET_KEY="sk_test_..."
STRIPE_PUBLIC_KEY="pk_test_..."
STRIPE_WEBHOOK_SECRET="whsec_..."

# Redis
UPSTASH_REDIS_URL="https://..."
UPSTASH_REDIS_TOKEN="..."

# Email
RESEND_API_KEY="re_..."

# Media
CLOUDINARY_URL="cloudinary://..."

# Monitoring
SENTRY_DSN="https://..."

# CMS
SANITY_PROJECT_ID="..."
SANITY_DATASET="production"
SANITY_TOKEN="..."

# Encryption
ENCRYPTION_KEY="your_32_character_encryption_key_here"

# Application
NODE_ENV="development"
PORT=3000

# Ritual Experience
ENABLE_RITUAL_EXPERIENCE=true
HAPTIC_FEEDBACK_ENABLED=true
AUDIO_FEEDBACK_ENABLED=true
VISUAL_EFFECTS_ENABLED=true

# Development
NEXT_PUBLIC_API_MOCKING="enabled"
```

## 11. Development Guidelines

### 11.1 Coding Standards & Best Practices

#### 11.1.1 TypeScript Standards
```typescript
/**
 * ATLAS: Atelier TypeScript Standards
 * =====================================
 * 
 * These standards ensure type safety, readability, and maintainability
 * across the entire codebase. They are enforced through ESLint and
 * code review processes.
 */

// 1. Type Safety First
// ✅ GOOD: Explicit return types for all functions
const calculateTotal = (items: OrderItem[]): number => {
  return items.reduce((total, item) => total + item.price * item.quantity, 0);
};

// ❌ BAD: Missing return type
const badCalculateTotal = (items: OrderItem[]) => {
  return items.reduce((total, item) => total + item.price * item.quantity, 0);
};

// 2. Prefer Interfaces for Object Shapes
// ✅ GOOD: Interface for complex objects
interface Essence {
  id: string;
  slug: string;
  commonName: string;
  latinName: string;
  price: number;
  humour: 'calming' | 'uplifting' | 'grounding' | 'clarifying';
  // ... other properties
}

// ❌ BAD: Type alias for complex objects
type BadEssence = {
  id: string;
  slug: string;
  commonName: string;
  latinName: string;
  price: number;
  humour: string; // Not type-safe
};

// 3. Use Readonly for Immutable Data
// ✅ GOOD: Readonly arrays and properties
interface Cart {
  readonly items: readonly CartItem[];
  readonly updatedAt: Date;
  addItem(item: CartItem): void;
}

// 4. Avoid Any Type
// ✅ GOOD: Use unknown with type guards
const parseJSON = ( unknown): ParsedData | null => {
  if (typeof data === 'string') {
    try {
      return JSON.parse(data) as ParsedData;
    } catch (error) {
      console.error('Failed to parse JSON:', error);
      return null;
    }
  }
  return null;
};

// 5. Type Guards for Runtime Validation
const isEssence = (item: unknown): item is Essence => {
  return (
    typeof item === 'object' &&
    item !== null &&
    'id' in item &&
    'slug' in item &&
    'commonName' in item &&
    'price' in item &&
    typeof (item as Essence).price === 'number'
  );
};

// 6. Generic Types for Reusable Components
interface PaginatedResponse<T> {
  items: T[];
  pagination: {
    page: number;
    limit: number;
    total: number;
    totalPages: number;
    hasMore: boolean;
  };
}

// 7. Enumerations for Finite Sets
enum PaymentStatus {
  PENDING = 'pending',
  PROCESSING = 'processing',
  SUCCEEDED = 'succeeded',
  FAILED = 'failed',
  REFUNDED = 'refunded'
}

// 8. Utility Types for Common Patterns
type Optional<T, K extends keyof T> = Pick<Partial<T>, K> & Omit<T, K>;
type DeepPartial<T> = T extends object
  ? {
      [P in keyof T]?: DeepPartial<T[P]>;
    }
  : T;

// 9. Function Overloading for Multiple Signatures
function formatPrice(amount: number, currency?: string): string;
function formatPrice(amount: number, locale?: string, currency?: string): string;
function formatPrice(amount: number, localeOrCurrency?: string, currency?: string): string {
  const locale = currency ? localeOrCurrency : 'en-US';
  const finalCurrency = currency || localeOrCurrency || 'EUR';
  
  return new Intl.NumberFormat(locale, {
    style: 'currency',
    currency: finalCurrency,
  }).format(amount);
}

// 10. Error Handling with Custom Error Classes
class AtelierError extends Error {
  constructor(
    message: string,
    public code: string,
    public metadata?: Record<string, any>
  ) {
    super(message);
    this.name = 'AtelierError';
  }
}

// Usage
try {
  // Some operation
} catch (error) {
  if (error instanceof AtelierError) {
    console.error(`Atelier error ${error.code}: ${error.message}`, error.metadata);
  } else {
    console.error('Unexpected error:', error);
  }
}
```

#### 11.1.2 React & Next.js Standards
```typescript
/**
 * AURUM: Atelier React & Next.js Standards
 * =========================================
 * 
 * These standards ensure component consistency, performance, and
 * accessibility across the application. They align with Next.js best
 * practices and the unique ritual experience requirements.
 */

// 1. Component Structure
// ✅ GOOD: Complete component structure with proper exports
'use client';

import { useState, useEffect, useMemo } from 'react';
import { cn } from '@/lib/utils';
import { EssenceCardProps } from './essence-card.types';

export function EssenceCard({ 
  essence, 
  variant = 'default', 
  onAddToVial,
  className 
}: EssenceCardProps) {
  // State management
  const [isAdding, setIsAdding] = useState(false);
  const [isHovered, setIsHovered] = useState(false);
  
  // Derived state with useMemo
  const liquidLevel = useMemo(() => {
    return essence.stockQuantity > 0 ? 
      Math.min(1, essence.stockQuantity / 100) : 0;
  }, [essence.stockQuantity]);
  
  // Effects for side effects
  useEffect(() => {
    if (isAdding) {
      const timer = setTimeout(() => setIsAdding(false), 1000);
      return () => clearTimeout(timer);
    }
  }, [isAdding]);
  
  // Event handlers
  const handleAddToVial = async () => {
    if (isAdding || essence.stockQuantity === 0) return;
    
    setIsAdding(true);
    try {
      await onAddToVial?.(essence);
      // Trigger ritual feedback
      triggerRitualEvent('essence_added_to_vial', {
        essenceId: essence.id,
        liquidLevel
      });
    } catch (error) {
      console.error('Failed to add to vial:', error);
      setIsAdding(false);
    }
  };
  
  // JSX with proper semantics
  return (
    <article 
      className={cn(
        'rounded-xl border border-ink/10 bg-parchment p-6 shadow-md transition-all',
        'hover:shadow-lg hover:border-gold/30',
        'focus-within:ring-2 focus-within:ring-gold focus-within:ring-offset-2',
        variant === 'featured' && 'border-2 border-gold bg-parchment-darker',
        isHovered && 'scale-[1.02]',
        className
      )}
      onMouseEnter={() => setIsHovered(true)}
      onMouseLeave={() => setIsHovered(false)}
      aria-labelledby={`essence-${essence.id}-title`}
    >
      <div className="flex flex-col md:flex-row gap-6">
        <div className="flex-1 min-w-[200px]">
          <div className="relative mb-4">
            <div 
              className={cn(
                'absolute inset-0 bg-gradient-to-t from-gold/20 to-transparent',
                'rounded-lg opacity-0 transition-opacity',
                isHovered && 'opacity-100'
              )}
            />
            <img
              src={essence.images[0]?.url}
              alt={essence.images[0]?.altText || `${essence.commonName} essence`}
              width={200}
              height={300}
              className={cn(
                'w-full h-64 object-cover rounded-lg transition-transform',
                isHovered && 'scale-105'
              )}
              loading="lazy"
              decoding="async"
            />
            <div 
              className={cn(
                'absolute bottom-0 left-0 right-0 h-8 bg-ink/10 rounded-b-lg overflow-hidden',
                'transition-all duration-500 ease-in-out'
              )}
              style={{ height: `${liquidLevel * 100}%` }}
            >
              {/* Liquid wave animation */}
              <div 
                className="absolute inset-0 bg-gold/30"
                style={{ 
                  clipPath: 'polygon(0% 100%, 25% 90%, 50% 100%, 75% 90%, 100% 100%)',
                  animation: 'liquid-wave 8s ease-in-out infinite'
                }}
              />
            </div>
          </div>
          
          <div className="mb-4">
            <span className="inline-block px-2 py-1 text-xs font-medium bg-gold/20 text-ink rounded-full mb-2">
              {essence.humour.charAt(0).toUpperCase() + essence.humour.slice(1)}
            </span>
            <h3 
              id={`essence-${essence.id}-title`}
              className="text-xl font-display text-ink mb-1"
            >
              {essence.commonName}
            </h3>
            <p className="text-sm text-ink/70 font-body italic">
              {essence.latinName}
            </p>
          </div>
          
          <p className="text-ink/80 mb-4 line-clamp-3">{essence.description}</p>
          
          <div className="flex items-center justify-between">
            <span className="text-2xl font-display text-gold">
              €{essence.price.toFixed(2)}
            </span>
            <button
              onClick={handleAddToVial}
              disabled={isAdding || essence.stockQuantity === 0}
              aria-label={`Add ${essence.commonName} to collection vial`}
              className={cn(
                'px-4 py-2 bg-gold text-parchment rounded-lg font-medium',
                'hover:bg-gold-dark transition-colors',
                'disabled:opacity-50 disabled:cursor-not-allowed',
                'focus:outline-none focus:ring-2 focus:ring-gold focus:ring-offset-2',
                isAdding && 'opacity-75 cursor-wait'
              )}
            >
              {isAdding ? (
                <span className="flex items-center justify-center">
                  <svg className="animate-spin -ml-1 mr-2 h-4 w-4 text-parchment" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24">
                    <circle className="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" strokeWidth="4"></circle>
                    <path className="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path>
                  </svg>
                  Adding...
                </span>
              ) : essence.stockQuantity === 0 ? (
                'Out of Stock'
              ) : (
                'Add to Vial'
              )}
            </button>
          </div>
        </div>
        
        {variant === 'featured' && (
          <div className="flex-1 min-w-[200px] border-l border-ink/10 pl-6">
            <h4 className="font-display text-lg text-ink mb-3">Botanical Notes</h4>
            <div className="space-y-2">
              {essence.notes.map((note, index) => (
                <div key={index} className="flex items-center">
                  <span className="text-gold mr-2">•</span>
                  <span className="text-ink/80 font-body">{note}</span>
                </div>
              ))}
            </div>
            
            <div className="mt-6">
              <h4 className="font-display text-lg text-ink mb-3">Extraction</h4>
              <p className="text-ink/80 font-body italic">{essence.extractionMethod}</p>
            </div>
          </div>
        )}
      </div>
    </article>
  );
}

// 2. Server Components
// ✅ GOOD: Server component with proper data fetching
import { prisma } from '@/lib/prisma';
import { EssenceDetail } from './essence-detail';

export default async function EssencePage({ params }: { params: Promise<{ slug: string }> }) {
  const { slug } = await params;
  
  // Server-side data fetching with error handling
  const essence = await prisma.essence.findUnique({
    where: { slug },
    include: {
      images: true,
      botanicalInfo: true,
      alchemicalProcess: true,
      artisanNotes: true,
      relatedEssences: {
        take: 4,
        include: { images: { take: 1 } }
      }
    }
  });
  
  if (!essence) {
    notFound();
  }
  
  return <EssenceDetail essence={essence} />;
}

// 3. Error Boundaries
'use client';

import { ErrorBoundary } from 'react-error-boundary';

export function EssenceErrorBoundary({ children }: { children: React.ReactNode }) {
  return (
    <ErrorBoundary
      FallbackComponent={EssenceFallback}
      onReset={() => window.location.reload()}
      resetKeys={[children]}
    >
      {children}
    </ErrorBoundary>
  );
}

function EssenceFallback({ error, resetErrorBoundary }: { error: Error; resetErrorBoundary: () => void }) {
  return (
    <div className="border border-rose-200 bg-rose-50 text-rose-700 p-4 rounded-lg">
      <div className="flex">
        <div className="flex-shrink-0">
          <svg className="h-5 w-5 text-rose-400" viewBox="0 0 20 20" fill="currentColor">
            <path fillRule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zM8.707 7.293a1 1 0 00-1.414 1.414L8.586 10l-1.293 1.293a1 1 0 101.414 1.414L10 11.414l1.293 1.293a1 1 0 001.414-1.414L11.414 10l1.293-1.293a1 1 0 00-1.414-1.414L10 8.586 8.707 7.293z" clipRule="evenodd" />
          </svg>
        </div>
        <div className="ml-3">
          <h3 className="text-sm font-medium">Essence loading failed</h3>
          <div className="mt-2 text-sm">
            <p>{error.message || 'An error occurred while loading this essence.'}</p>
          </div>
          <div className="mt-4">
            <button
              type="button"
              onClick={resetErrorBoundary}
              className="inline-flex items-center px-3 py-2 border border-transparent text-sm font-medium rounded-md shadow-sm text-white bg-rose-600 hover:bg-rose-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-rose-500"
            >
              Try again
            </button>
          </div>
        </div>
      </div>
    </div>
  );
}

// 4. Loading States
export function EssenceCardSkeleton() {
  return (
    <article className="rounded-xl border border-ink/10 bg-parchment p-6 shadow-md animate-pulse">
      <div className="flex flex-col md:flex-row gap-6">
        <div className="flex-1 min-w-[200px]">
          <div className="relative mb-4">
            <div className="w-full h-64 bg-parchment-dark rounded-lg" />
          </div>
          
          <div className="mb-4">
            <div className="h-4 bg-parchment-dark rounded w-1/4 mb-2" />
            <div className="h-6 bg-parchment-dark rounded w-3/4 mb-1" />
            <div className="h-4 bg-parchment-dark rounded w-1/2" />
          </div>
          
          <div className="h-4 bg-parchment-dark rounded w-2/3 mb-4" />
          
          <div className="flex items-center justify-between">
            <div className="h-8 w-20 bg-parchment-dark rounded" />
            <div className="h-10 w-24 bg-gold rounded-lg" />
          </div>
        </div>
      </div>
    </article>
  );
}

// 5. Testing Standards
import { render, screen, fireEvent, waitFor } from '@testing-library/react';
import { vi } from 'vitest';
import { EssenceCard } from './essence-card';

describe('EssenceCard', () => {
  const mockEssence = {
    id: '1',
    slug: 'lavender',
    commonName: 'Lavender',
    latinName: 'Lavandula',
    price: 42.00,
    humour: 'calming' as const,
    stockQuantity: 50,
    description: 'Calming lavender essence',
    images: [{ url: '/lavender.jpg', altText: 'Lavender essence' }],
    notes: ['floral', 'herbaceous'],
    extractionMethod: 'Steam Distillation'
  };
  
  it('renders essence information correctly', () => {
    render(<EssenceCard essence={mockEssence} />);
    
    expect(screen.getByText('Lavender')).toBeInTheDocument();
    expect(screen.getByText('Lavandula')).toBeInTheDocument();
    expect(screen.getByText('€42.00')).toBeInTheDocument();
    expect(screen.getByText('Calming')).toBeInTheDocument();
    expect(screen.getByAltText('Lavender essence')).toBeInTheDocument();
  });
  
  it('calls onAddToVial when button is clicked', async () => {
    const mockOnAddToVial = vi.fn();
    render(<EssenceCard essence={mockEssence} onAddToVial={mockOnAddToVial} />);
    
    const button = screen.getByRole('button', { name: /Add to Vial/i });
    fireEvent.click(button);
    
    await waitFor(() => {
      expect(mockOnAddToVial).toHaveBeenCalledWith(mockEssence);
      expect(button).toBeDisabled();
    });
  });
  
  it('shows loading state when adding to vial', async () => {
    const mockOnAddToVial = vi.fn().mockImplementation(() => new Promise(resolve => setTimeout(resolve, 1000)));
    render(<EssenceCard essence={mockEssence} onAddToVial={mockOnAddToVial} />);
    
    const button = screen.getByRole('button', { name: /Add to Vial/i });
    fireEvent.click(button);
    
    expect(button).toBeDisabled();
    expect(screen.getByText('Adding...')).toBeInTheDocument();
    
    await waitFor(() => {
      expect(button).not.toBeDisabled();
      expect(screen.queryByText('Adding...')).not.toBeInTheDocument();
    });
  });
  
  it('handles out of stock state', () => {
    const outOfStockEssence = { ...mockEssence, stockQuantity: 0 };
    render(<EssenceCard essence={outOfStockEssence} />);
    
    const button = screen.getByRole('button', { name: /Out of Stock/i });
    expect(button).toBeDisabled();
    expect(button).toHaveTextContent('Out of Stock');
  });
  
  it('triggers ritual events on interaction', async () => {
    const mockTriggerRitualEvent = vi.spyOn(require('@/services/ritual.service'), 'triggerRitualEvent');
    const mockOnAddToVial = vi.fn();
    
    render(<EssenceCard essence={mockEssence} onAddToVial={mockOnAddToVial} />);
    
    const button = screen.getByRole('button', { name: /Add to Vial/i });
    fireEvent.click(button);
    
    await waitFor(() => {
      expect(mockTriggerRitualEvent).toHaveBeenCalledWith(
        'essence_added_to_vial', 
        expect.objectContaining({
          essenceId: '1',
          liquidLevel: 0.5 // 50/100
        })
      );
    });
  });
});
```

### 11.2 Git Workflow & Collaboration

#### 11.2.1 Branching Strategy
```
ATLAS BRANCHING STRATEGY
========================

MAIN BRANCH
- Protected branch with production-ready code
- Only updated via pull requests from develop
- Tagged releases for deployments
- Strict CI/CD pipeline: tests, builds, security scans must pass

DEVELOP BRANCH
- Integration branch for features
- Merged into main for releases
- Regular builds and testing
- Feature branches merged here first

FEATURE BRANCHES (feature/*)
- Created from develop for new features
- Named: feature/[feature-name]-[issue-number]
- Example: feature/vial-animation-123
- Merged back to develop via PR

BUGFIX BRANCHES (bugfix/*)
- Created from develop for bug fixes
- Named: bugfix/[description]-[issue-number]
- Example: bugfix/cart-total-calculation-456
- Merged back to develop via PR

HOTFIX BRANCHES (hotfix/*)
- Created from main for critical production fixes
- Named: hotfix/[description]-[issue-number]
- Example: hotfix/payment-failure-789
- Merged to both main and develop
- Bypasses normal review process for critical issues

RELEASE BRANCHES (release/*)
- Created from develop for release preparation
- Named: release/v[version-number]
- Example: release/v1.2.3
- Final testing, version bumping, changelog updates
- Merged to main and develop after release

GITFLOW LIFECYCLE
=================

1. Start new feature:
   git checkout develop
   git pull origin develop
   git checkout -b feature/my-feature-123

2. Work on feature:
   git add .
   git commit -m "feat(vial): add liquid wave animation"
   git push origin feature/my-feature-123

3. Create pull request to develop
   - Review code
   - Run tests
   - Check coverage
   - Merge to develop

4. Prepare release:
   git checkout develop
   git pull origin develop
   git checkout -b release/v1.2.3
   # Update version numbers, changelog
   git push origin release/v1.2.3
   # Create PR to main

5. Release to production:
   git checkout main
   git merge --no-ff release/v1.2.3
   git tag -a v1.2.3 -m "Version 1.2.3"
   git push origin main
   git push origin --tags
   # Deploy to production

6. Merge release back to develop:
   git checkout develop
   git merge --no-ff release/v1.2.3
   git push origin develop
   git branch -d release/v1.2.3
```

#### 11.2.2 Commit Message Convention
```
ATLAS COMMIT MESSAGE CONVENTION
===============================

FORMAT:
<type>(<scope>): <subject>
<BLANK LINE>
<body>
<BLANK LINE>
<footer>

EXAMPLE:
feat(vial): add liquid wave animation for essence levels

Implement CSS-based liquid wave animation that responds to stock quantity.
The animation uses CSS keyframes with hardware acceleration for smooth
performance on all devices.

The liquid level is calculated as a percentage of available stock, capped
at 100% for visual consistency.

Closes #123
Refs #456

TYPES:
- feat: New feature for the user
- fix: Bug fix for the user
- docs: Documentation changes
- style: Code style changes (formatting, etc.)
- refactor: Code refactoring without feature changes
- perf: Performance improvements
- test: Adding or updating tests
- chore: Build process or auxiliary tool changes
- ci: CI pipeline changes
- revert: Revert previous changes

SCOPES:
- vial: Cart/vial system
- essence: Product/essence components
- ritual: Multi-sensory experience
- auth: Authentication system
- checkout: Dispatch/checkout flow
- admin: Atelier administration
- design: Design system components
- utils: Utility functions
- types: TypeScript definitions
- tests: Test utilities and setup

SUBJECT:
- Concise description (50 chars max)
- Imperative mood ("add" not "added" or "adds")
- No period at the end

BODY:
- Detailed explanation of changes
- Motivation for changes
- Contrast with previous behavior
- Wrap at 72 characters

FOOTER:
- Breaking changes (BREAKING CHANGE: ...)
- Issue references (Closes #123, Fixes #456)
- Co-authors (Co-authored-by: name <email>)
```

## 12. Implementation Roadmap

### 12.1 Phase 1: Foundation (Weeks 1-4)

#### Week 1: Project Setup & Architecture
- [x] Initialize Next.js 14 project with TypeScript
- [x] Configure Tailwind CSS 4.0 with custom manuscript theme
- [x] Set up Prisma ORM with PostgreSQL database
- [x] Configure authentication with NextAuth.js and ritual integration
- [x] Set up Redis for caching and session management
- [x] Configure Stripe integration for payments
- [x] Set up Storybook for component documentation
- [x] Configure ESLint, Prettier, and Husky for code quality
- [x] Create initial project architecture document
- [x] Set up GitHub repository with branch protection rules

#### Week 2: Core UI Components & Design System
- [x] Implement design system (colors, typography, spacing, animations)
- [x] Create layout components (Header, Footer, Navigation)
- [x] Build decorative components (GoldLeaf, ParchmentTexture, ManuscriptBorder)
- [x] Implement vial drawer and toast notifications with ritual integration
- [x] Create form components with Zod validation
- [x] Build responsive navigation system with folio numbers
- [x] Implement accessibility enhancements (keyboard nav, screen reader support)
- [x] Create initial set of ritual components (scroll indicator, haptic feedback)
- [x] Set up audio spatialization engine
- [x] Implement CSS containment strategies for performance

#### Week 3: Product Catalog & Ritual Integration
- [x] Create essence card component with liquid wave animation
- [x] Implement product grid layout with asymmetric positioning
- [x] Build filtering and sorting system with alchemical symbols
- [x] Create product detail page with multi-sensory experience
- [x] Implement search functionality with fuzzy matching
- [x] Set up product data model and seed database with initial essences
- [x] Implement caching strategy for products with ritual metadata
- [x] Create floating botanical specimens with physics
- [x] Implement scroll-triggered animations for narrative flow
- [x] Add haptic feedback for product interactions
- [x] Set up audio feedback for essence exploration

#### Week 4: Vial System & Ritual Experience
- [x] Implement vial store with Zustand and Redis persistence
- [x] Build vial UI components with liquid simulation
- [x] Create wax seal toast notifications with ritual animations
- [x] Implement quill-pen scroll indicator with momentum physics
- [x] Build checkout form with manuscript styling
- [x] Implement Stripe payment integration with ritual feedback
- [x] Create order confirmation page with illuminated design
- [x] Set up webhook handlers for payment events
- [x] Implement inventory management with low-stock alerts
- [x] Add reduced motion support for accessibility
- [x] Create initial performance budgeting and monitoring

### 12.2 Phase 2: Content & Engagement (Weeks 5-8)

#### Week 5: Content Management & Storytelling
- [ ] Set up Sanity CMS integration for content management
- [x] Create content components (HeroSection, TestimonialEntry, ManuscriptCard)
- [x] Implement manuscript/journal section with folio navigation
- [ ] Build content management interface for atelier staff
- [x] Create folio newsletter subscription with wax seal design
- [ ] Set up content scheduling and publishing workflows
- [ ] Implement content preview functionality for editors
- [x] Create alchemical process visualization components
- [ ] Set up editorial calendar integration
- [ ] Implement content versioning and audit trails

#### Week 6: User Accounts & Subscriptions
- [x] Complete user profile management with ritual preferences
- [ ] Implement subscription service (quarterly folio) with Stripe
- [x] Build order history and tracking with manuscript styling
- [ ] Create subscription management interface with pause/cancel options
- [ ] Implement recurring billing with Stripe webhooks
- [ ] Set up email notifications for subscriptions with illuminated design
- [x] Build customer dashboard with patron status
- [ ] Implement gift subscription functionality
- [ ] Set up subscription analytics and reporting
- [ ] Add trial period management for new subscribers

#### Week 7: Alchemy Process & Educational Content
- [x] Create alchemy process section with four-step visualization
- [x] Build interactive storytelling components for botanical origins
- [x] Implement botanical illustrations with SVG animations
- [ ] Create behind-the-scenes content about distillation process
- [ ] Build artisan profiles with illuminated portraits
- [ ] Implement educational content about aromatherapy benefits
- [ ] Create seasonal content calendar with automatic scheduling
- [ ] Set up content recommendation engine based on user preferences
- [ ] Implement social sharing with manuscript-style previews
- [ ] Add print stylesheet for physical manuscript preservation

#### Week 8: Mobile & Performance Optimization
- [ ] Complete mobile-responsive design with touch optimizations
- [ ] Optimize page load performance with code splitting
- [ ] Implement image optimization pipeline with Cloudinary
- [ ] Set up advanced caching strategies (stale-while-revalidate)
- [ ] Implement lazy loading for images and components
- [ ] Optimize animations for performance with will-change
- [ ] Conduct accessibility audit and fixes with axe-core
- [ ] Set up performance monitoring with Lighthouse CI
- [ ] Implement bundle analysis and size optimization
- [ ] Add offline support with service workers for manuscript reading

### 12.3 Phase 3: Scale & Operations (Weeks 9-12)

#### Week 9: Admin & Operations
- [ ] Build admin dashboard with illuminated interface
- [ ] Implement order management system with dispatch tracking
- [ ] Create inventory management tools with batch tracking
- [ ] Build customer management interface with patron profiles
- [ ] Implement analytics dashboard with ritual engagement metrics
- [ ] Create reporting tools for business intelligence
- [ ] Set up monitoring and alerting for critical systems
- [ ] Implement audit logging for all admin actions
- [ ] Add role-based access control for staff members
- [ ] Set up backup and disaster recovery procedures

#### Week 10: Marketing & Growth
- [ ] Implement email marketing integrations with Resend
- [ ] Build referral program functionality with illuminated invites
- [ ] Create gift card system with wax seal design
- [ ] Implement social sharing features with manuscript previews
- [ ] Set up SEO optimization tools with structured data
- [ ] Build abandoned cart recovery with ritual notifications
- [ ] Implement seasonal promotions engine with alchemical themes
- [ ] Create customer segmentation for personalized experiences
- [ ] Set up A/B testing framework for conversion optimization
- [ ] Implement affiliate program with commission tracking

#### Week 11: Advanced Features
- [ ] Implement atelier appointment booking system
- [ ] Create custom product blending tool with alchemical interface
- [ ] Build scent profile quiz with ritual experience
- [ ] Implement AR/VR product previews for immersive exploration
- [ ] Create community features for patron discussions
- [ ] Build loyalty program with illuminated rewards
- [ ] Implement wholesale pricing tiers for practitioners
- [ ] Set up multi-currency support for international customers
- [ ] Implement multi-language support with localization
- [ ] Create API for third-party integrations

#### Week 12: Launch Preparation
- [ ] Conduct full security audit and penetration testing
- [ ] Perform load testing and auto-scaling configuration
- [ ] Final accessibility compliance review (WCAG AAA)
- [ ] Complete legal compliance (GDPR, CCPA, cookie consent)
- [ ] Set up comprehensive monitoring and incident response
- [ ] Create launch marketing campaign with illuminated assets
- [ ] Prepare customer support documentation and training
- [ ] Implement feature flags for gradual rollout
- [ ] Set up staging environment for final testing
- [ ] Create post-launch roadmap and maintenance plan

## 13. Appendices

### 13.1 Technical Debt Register
```
ATLAS TECHNICAL DEBT REGISTER
==============================

HIGH PRIORITY (Must address before launch)
- [ ] Implement comprehensive error boundaries throughout application
- [ ] Add proper rate limiting to all API endpoints
- [ ] Implement comprehensive audit logging for all user actions
- [ ] Add comprehensive unit test coverage for all services (target: 80%)
- [ ] Implement comprehensive E2E test suite for critical user flows
- [ ] Complete accessibility audit with WCAG AAA compliance
- [ ] Implement security headers and CSP for all pages
- [ ] Add comprehensive caching invalidation strategy
- [ ] Implement database indexing optimization plan
- [ ] Set up proper monitoring and alerting for production

MEDIUM PRIORITY (Address in first 3 months post-launch)
- [ ] Migrate remaining class components to functional components
- [ ] Implement comprehensive caching invalidation strategy
- [ ] Add comprehensive accessibility testing suite
- [ ] Implement comprehensive performance monitoring
- [ ] Add comprehensive security scanning in CI pipeline
- [ ] Create automated backup and recovery procedures
- [ ] Implement comprehensive logging and tracing
- [ ] Set up staging environment with production-like data
- [ ] Create disaster recovery runbook
- [ ] Implement feature flags for gradual rollouts

LOW PRIORITY (Future enhancements)
- [ ] Refactor CSS to use CSS modules for component-scoped styles
- [ ] Implement dark mode support with manuscript variants
- [ ] Add internationalization (i18n) support for multiple languages
- [ ] Implement offline support with service workers
- [ ] Add comprehensive analytics tracking
- [ ] Create design system documentation site
- [ ] Implement component regression testing
- [ ] Set up automated accessibility testing in CI
- [ ] Create performance budget monitoring
- [ ] Implement serverless functions for heavy computations
```

### 13.2 Risk Register
```
ATLAS RISK REGISTER
==================

HIGH RISK (Requires immediate mitigation)
- Payment processing failure: 
  Mitigation: Implement comprehensive error handling, fallback payment methods, 
  manual order processing workflow, and transaction monitoring
  Owner: Payment Team
  Review: Weekly

- Data breach: 
  Mitigation: Regular security audits, encryption at rest and in transit, 
  access controls, incident response plan, and security training
  Owner: Security Team
  Review: Monthly

- Downtime during peak traffic: 
  Mitigation: Load testing, auto-scaling, CDN caching, failover systems, 
  and 24/7 monitoring with alerting
  Owner: DevOps Team
  Review: Weekly

MEDIUM RISK (Requires active monitoring)
- Third-party service failures (Stripe, Redis, etc.): 
  Mitigation: Circuit breakers, fallback mechanisms, monitoring and alerting, 
  and service degradation strategies
  Owner: Backend Team
  Review: Bi-weekly

- Performance degradation: 
  Mitigation: Performance budgeting, regular performance audits, 
  optimization pipeline, and real-user monitoring
  Owner: Frontend Team
  Review: Bi-weekly

- Accessibility compliance failures: 
  Mitigation: Regular accessibility audits, automated testing, 
  manual testing with screen readers, and accessibility champions
  Owner: UX Team
  Review: Monthly

LOW RISK (Monitor and review quarterly)
- Browser compatibility issues: 
  Mitigation: Cross-browser testing, feature detection, polyfills, 
  and progressive enhancement
  Owner: Frontend Team
  Review: Quarterly

- SEO ranking issues: 
  Mitigation: Regular SEO audits, sitemap generation, 
  structured data implementation, and content optimization
  Owner: Marketing Team
  Review: Quarterly

- Content management workflow issues: 
  Mitigation: Training documentation, content governance policies, 
  review workflows, and editorial calendar
  Owner: Content Team
  Review: Quarterly
```

### 13.3 Success Metrics
```
ATLAS SUCCESS METRICS
====================

BUSINESS METRICS
- Revenue: €500K ARR Year 1
- Customer Acquisition Cost: < €50 per customer
- Customer Lifetime Value: > €300
- Conversion Rate: > 3%
- Average Order Value: > €120
- Repeat Purchase Rate: > 40%
- Subscription Retention: > 70%
- Customer Satisfaction (NPS): > 50
- Organic Traffic Growth: 20% month-over-month

TECHNICAL METRICS
- Page Load Time: < 2.5s LCP
- Core Web Vitals: > 90% passing
- API Response Time: < 200ms 95th percentile
- Error Rate: < 0.1%
- Uptime: 99.95%
- Test Coverage: > 80%
- Deployment Frequency: Multiple times per day
- Lead Time for Changes: < 1 hour
- Mean Time to Recovery: < 30 minutes
- Security Vulnerabilities: Zero critical/high severity

USER EXPERIENCE METRICS
- Task Success Rate: > 95%
- User Satisfaction (NPS): > 50
- Accessibility Score: WCAG AAA compliance
- Mobile Usability Score: > 95
- User Engagement: > 3 minutes average session duration
- Bounce Rate: < 40%
- Ritual Engagement Rate: > 70% opt-in
- Haptic Feedback Satisfaction: > 85%
- Audio Feedback Satisfaction: > 80%
- Visual Effects Satisfaction: > 90%

DEVELOPMENT METRICS
- Lead Time for Features: < 2 weeks
- Bug Fix Time: < 24 hours for critical, < 1 week for minor
- Code Review Time: < 24 hours
- Test Coverage Growth: +5% per sprint
- Technical Debt Reduction: -10% per quarter
- Developer Satisfaction: > 8/10
- Deployment Success Rate: > 99%
- Rollback Frequency: < 1% of deployments
- Documentation Coverage: 100% of critical paths
- Knowledge Sharing Sessions: Weekly
```

---

**Document Status:** Complete  
**Next Review Date:** 2026-06-27  
**Approved By:** Technical Lead & Product Owner  
**Version History:** 1.0.0 (Initial), 2.0.0 (Complete Architecture), 3.0.0 (Ritual Integration)

This Project Architecture Document serves as the single source of truth for the Atelier Arôme platform development. All implementation decisions must align with this document, and any deviations require formal change approval through the project governance process. The architecture balances aesthetic integrity with technical excellence, ensuring the final product will be both visually distinctive and technically robust—a true digital alchemical manuscript that transforms botanical commerce into an experiential journey.
