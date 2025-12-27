Project Architecture Document: Atelier Arôme
Comprehensive Technical Specification & Implementation Blueprint
Implementation Plan for PAD Creation
Before executing, I've developed and validated this implementation plan:

PAD Implementation Plan
text

┌─────────────────────────────────────────────────────────────────────────────┐
│                        PAD CREATION METHODOLOGY                              │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  PHASE 1: FOUNDATION          PHASE 2: ARCHITECTURE        PHASE 3: DATA   │
│  ├─ Executive Summary         ├─ System Overview           ├─ ERD Design   │
│  ├─ Vision & Goals            ├─ C4 Diagrams               ├─ Table Specs  │
│  ├─ Business Requirements     ├─ Tech Stack                ├─ Migrations   │
│  └─ User Personas             └─ Infrastructure            └─ Seeders      │
│                                                                             │
│  PHASE 4: FRONTEND            PHASE 5: BACKEND             PHASE 6: OPS    │
│  ├─ Component Tree            ├─ API Specification         ├─ CI/CD        │
│  ├─ State Management          ├─ Service Architecture      ├─ Deployment   │
│  ├─ Design Tokens             ├─ Auth & Security           ├─ Monitoring   │
│  └─ Route Structure           └─ Integration Points        └─ Testing      │
│                                                                             │
│  PHASE 7: VALIDATION                                                        │
│  ├─ Cross-reference all sections for consistency                           │
│  ├─ Verify completeness against requirements                               │
│  └─ Ensure no ambiguity for independent development                        │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
Validation Checklist (Pre-Execution)
Requirement	Coverage	Status
Independent development capability	Full specs, no external dependencies	✅
Database schema completeness	All entities, relationships, constraints	✅
API specification clarity	OpenAPI-style with examples	✅
Frontend component specifications	Props, states, behaviors defined	✅
No ambiguity	Explicit decisions, no "TBD" items	✅
Diagram clarity	ASCII/text-based for universal rendering	✅
Plan Validated. Proceeding with execution.

ATELIER ARÔME
Project Architecture Document (PAD)
Version 2.0.0 | Single Source of Truth
Table of Contents
Executive Summary
Project Overview
System Architecture
Technology Stack
Frontend Architecture
Backend Architecture
Database Schema
API Specification
Authentication & Authorization
Third-Party Integrations
DevOps & Infrastructure
Testing Strategy
Development Guidelines
Appendices
1. Executive Summary
1.1 Document Purpose
This Project Architecture Document (PAD) serves as the single source of truth for the Atelier Arôme e-commerce platform. It provides complete specifications enabling any developer or AI coding agent to independently implement the entire system without ambiguity.

1.2 Project Vision
Atelier Arôme is a luxury artisanal aromatherapy e-commerce platform that transforms the digital shopping experience into an illuminated manuscript journey. The platform celebrates the craft of botanical essence creation through a Renaissance-inspired aesthetic while delivering a modern, accessible, and performant shopping experience.

1.3 Core Differentiators
Aspect	Implementation
Aesthetic	Renaissance illuminated manuscript theme throughout
Narrative	Products presented as "documented specimens" in a compendium
Craft Focus	Emphasis on alchemical process, batch provenance, and artisanal quality
Experience	Sensory-rich digital journey that mirrors the physical product experience
1.4 Success Metrics
text

┌─────────────────────────────────────────────────────────────────┐
│                      KEY PERFORMANCE INDICATORS                  │
├─────────────────────────────────────────────────────────────────┤
│  PERFORMANCE          │  ACCESSIBILITY      │  BUSINESS         │
│  ├─ LCP < 2.0s        │  ├─ WCAG AAA        │  ├─ Conv. > 3.5%  │
│  ├─ FID < 100ms       │  ├─ 100% keyboard   │  ├─ AOV > $85     │
│  ├─ CLS < 0.1         │  ├─ Screen reader   │  ├─ NPS > 70      │
│  └─ TTI < 3.5s        │  └─ Reduced motion  │  └─ Return > 40%  │
└─────────────────────────────────────────────────────────────────┘
2. Project Overview
2.1 Business Requirements
2.1.1 Functional Requirements
ID	Category	Requirement	Priority
FR-001	Catalog	Display products with rich botanical information	P0
FR-002	Catalog	Filter by humour (calming, uplifting, grounding, clarifying)	P0
FR-003	Catalog	Filter by season, rarity, extraction method	P1
FR-004	Catalog	Sort by folio order, price, newest, popularity	P0
FR-005	Cart	Add/remove products with quantity management	P0
FR-006	Cart	Persist cart across sessions	P0
FR-007	Cart	Display real-time totals and item counts	P0
FR-008	Checkout	Guest checkout option	P0
FR-009	Checkout	Account checkout with saved addresses	P0
FR-010	Checkout	Multiple payment methods (Stripe)	P0
FR-011	Checkout	Order confirmation with manuscript styling	P0
FR-012	Account	User registration and authentication	P0
FR-013	Account	Order history with tracking	P0
FR-014	Account	Saved addresses management	P1
FR-015	Account	Wishlist / "Desired Essences"	P1
FR-016	Subscription	Newsletter signup ("Quarterly Folio")	P0
FR-017	Subscription	Preference management	P1
FR-018	Content	Alchemy process educational content	P1
FR-019	Content	Testimonials / "Patron's Manuscript"	P1
FR-020	Admin	Product management (CRUD)	P0
FR-021	Admin	Order management and fulfillment	P0
FR-022	Admin	Customer management	P1
FR-023	Admin	Inventory and batch tracking	P1
FR-024	Admin	Analytics dashboard	P2
2.1.2 Non-Functional Requirements
ID	Category	Requirement	Target
NFR-001	Performance	Page load time (LCP)	< 2.0s
NFR-002	Performance	Time to Interactive	< 3.5s
NFR-003	Performance	API response time (p95)	< 200ms
NFR-004	Availability	System uptime	99.9%
NFR-005	Scalability	Concurrent users	10,000+
NFR-006	Security	OWASP Top 10 compliance	Full
NFR-007	Security	PCI-DSS compliance (via Stripe)	Level 1
NFR-008	Accessibility	WCAG compliance	AAA
NFR-009	Accessibility	Reduced motion support	Full
NFR-010	SEO	Core Web Vitals	All green
NFR-011	Compatibility	Browser support	Last 2 versions
NFR-012	Mobile	Responsive design	320px - 2560px
2.2 User Personas
2.2.1 Primary Personas
text

┌─────────────────────────────────────────────────────────────────────────────┐
│  PERSONA 1: THE CONNOISSEUR                                                 │
├─────────────────────────────────────────────────────────────────────────────┤
│  Name: Isabelle, 42                                                         │
│  Occupation: Art Historian & Writer                                         │
│  Income: €120,000/year                                                      │
│                                                                             │
│  GOALS                           │  PAIN POINTS                             │
│  ├─ Find unique, artisanal      │  ├─ Generic e-commerce experiences       │
│  │   products                   │  ├─ Lack of provenance information       │
│  ├─ Understand craft process    │  ├─ Mass-produced "luxury" products      │
│  ├─ Support small artisans      │  └─ Overwhelming product choices         │
│  └─ Gift refined products       │                                          │
│                                                                             │
│  BEHAVIORS                       │  EXPECTATIONS                            │
│  ├─ Researches extensively      │  ├─ Rich storytelling                    │
│  ├─ Values quality over price   │  ├─ Beautiful presentation               │
│  ├─ Reads testimonials          │  ├─ Transparent sourcing                 │
│  └─ Shares discoveries          │  └─ Seamless checkout                    │
└─────────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────────┐
│  PERSONA 2: THE WELLNESS SEEKER                                             │
├─────────────────────────────────────────────────────────────────────────────┤
│  Name: Marco, 35                                                            │
│  Occupation: Executive Chef                                                 │
│  Income: €85,000/year                                                       │
│                                                                             │
│  GOALS                           │  PAIN POINTS                             │
│  ├─ Reduce stress naturally     │  ├─ Synthetic fragrances                 │
│  ├─ Create calming rituals      │  ├─ Unclear ingredient lists             │
│  ├─ Find specific scent         │  ├─ Inconsistent quality                 │
│  │   profiles                   │  └─ Complicated subscriptions            │
│  └─ Subscribe for convenience   │                                          │
│                                                                             │
│  BEHAVIORS                       │  EXPECTATIONS                            │
│  ├─ Impulse purchases on        │  ├─ Clear scent descriptions             │
│  │   recommendations            │  ├─ Easy reordering                      │
│  ├─ Mobile-first shopping       │  ├─ Fast checkout                        │
│  └─ Values expert curation      │  └─ Reliable delivery                    │
└─────────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────────┐
│  PERSONA 3: THE GIFT GIVER                                                  │
├─────────────────────────────────────────────────────────────────────────────┤
│  Name: Dr. Evelyn, 55                                                       │
│  Occupation: University Professor                                           │
│  Income: €95,000/year                                                       │
│                                                                             │
│  GOALS                           │  PAIN POINTS                             │
│  ├─ Find memorable gifts        │  ├─ Generic gift options                 │
│  ├─ Support academic/artisan    │  ├─ Poor gift wrapping                   │
│  │   endeavors                  │  ├─ No gift message options              │
│  └─ Easy gift shipping          │  └─ Complicated returns                  │
│                                                                             │
│  BEHAVIORS                       │  EXPECTATIONS                            │
│  ├─ Seasonal purchasing         │  ├─ Gift-ready presentation              │
│  ├─ Multiple shipping           │  ├─ Personalization options              │
│  │   addresses                  │  ├─ Quality guarantee                    │
│  └─ Values presentation         │  └─ Tracking notifications               │
└─────────────────────────────────────────────────────────────────────────────┘
2.2.2 Admin Personas
text

┌─────────────────────────────────────────────────────────────────────────────┐
│  ADMIN PERSONA: THE ATELIER MASTER                                          │
├─────────────────────────────────────────────────────────────────────────────┤
│  Name: The Perfumer                                                         │
│  Role: Owner/Operator                                                       │
│                                                                             │
│  NEEDS                                                                      │
│  ├─ Manage product catalog with rich botanical data                        │
│  ├─ Track inventory by batch with production dates                         │
│  ├─ Process orders efficiently                                             │
│  ├─ View sales analytics and trends                                        │
│  ├─ Manage customer communications                                          │
│  └─ Update content (alchemy process, testimonials)                         │
│                                                                             │
│  TECHNICAL PROFICIENCY: Low to Medium                                       │
│  Requires intuitive, visual interface with minimal technical knowledge      │
└─────────────────────────────────────────────────────────────────────────────┘
2.3 User Journey Maps
2.3.1 Primary Purchase Journey
text

┌─────────────────────────────────────────────────────────────────────────────┐
│                        CUSTOMER PURCHASE JOURNEY                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  ┌──────────┐    ┌──────────┐    ┌──────────┐    ┌──────────┐    ┌────────┐│
│  │ DISCOVER │───▶│ EXPLORE  │───▶│  DECIDE  │───▶│ PURCHASE │───▶│ DELIGHT││
│  └──────────┘    └──────────┘    └──────────┘    └──────────┘    └────────┘│
│       │              │               │               │              │       │
│       ▼              ▼               ▼               ▼              ▼       │
│  ┌──────────────────────────────────────────────────────────────────────┐  │
│  │ TOUCHPOINTS                                                          │  │
│  ├──────────────────────────────────────────────────────────────────────┤  │
│  │ • Landing page   • Product grid    • Product detail  • Cart         │  │
│  │ • Social media   • Filter/sort     • Reviews         • Checkout     │  │
│  │ • Search         • Alchemy process • Compare         • Confirmation │  │
│  └──────────────────────────────────────────────────────────────────────┘  │
│                                                                             │
│  ┌──────────────────────────────────────────────────────────────────────┐  │
│  │ EMOTIONAL STATE                                                      │  │
│  ├──────────────────────────────────────────────────────────────────────┤  │
│  │ Curiosity ──▶ Fascination ──▶ Trust ──▶ Excitement ──▶ Satisfaction │  │
│  └──────────────────────────────────────────────────────────────────────┘  │
│                                                                             │
│  ┌──────────────────────────────────────────────────────────────────────┐  │
│  │ SYSTEM ACTIONS                                                       │  │
│  ├──────────────────────────────────────────────────────────────────────┤  │
│  │ • Track visit    • Log browsing   • Save cart      • Process order  │  │
│  │ • Set cookie     • Build profile  • Validate stock • Send confirm   │  │
│  │ • Load catalog   • Cache prefs    • Apply discount • Update inv.    │  │
│  └──────────────────────────────────────────────────────────────────────┘  │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
3. System Architecture
3.1 High-Level Architecture Diagram
text

┌─────────────────────────────────────────────────────────────────────────────────────┐
│                              ATELIER ARÔME SYSTEM ARCHITECTURE                       │
├─────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                     │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                              CLIENT LAYER                                    │   │
│  ├─────────────────────────────────────────────────────────────────────────────┤   │
│  │                                                                             │   │
│  │   ┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌─────────────┐ │   │
│  │   │   Browser   │    │   Mobile    │    │   Tablet    │    │   Admin     │ │   │
│  │   │   (SPA)     │    │   Browser   │    │   Browser   │    │   Portal    │ │   │
│  │   └──────┬──────┘    └──────┬──────┘    └──────┬──────┘    └──────┬──────┘ │   │
│  │          │                  │                  │                  │         │   │
│  │          └──────────────────┴──────────────────┴──────────────────┘         │   │
│  │                                      │                                       │   │
│  └──────────────────────────────────────┼───────────────────────────────────────┘   │
│                                         │                                           │
│                                         ▼                                           │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                              CDN / EDGE LAYER                                │   │
│  ├─────────────────────────────────────────────────────────────────────────────┤   │
│  │   ┌─────────────────────────────────────────────────────────────────────┐   │   │
│  │   │                     Vercel Edge Network                              │   │   │
│  │   │   • Static asset caching       • Image optimization                  │   │   │
│  │   │   • Edge functions             • DDoS protection                     │   │   │
│  │   │   • Geo-routing                • SSL termination                     │   │   │
│  │   └─────────────────────────────────────────────────────────────────────┘   │   │
│  └──────────────────────────────────────┼───────────────────────────────────────┘   │
│                                         │                                           │
│                                         ▼                                           │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                           APPLICATION LAYER                                  │   │
│  ├─────────────────────────────────────────────────────────────────────────────┤   │
│  │                                                                             │   │
│  │   ┌───────────────────────────────┐    ┌───────────────────────────────┐   │   │
│  │   │      FRONTEND (Next.js 15)    │    │      BACKEND (Laravel 12)     │   │   │
│  │   ├───────────────────────────────┤    ├───────────────────────────────┤   │   │
│  │   │ • React 19 + TypeScript       │    │ • PHP 8.3+                    │   │   │
│  │   │ • App Router (RSC)            │◄──►│ • RESTful API                 │   │   │
│  │   │ • Tailwind CSS 4.0            │    │ • Laravel Sanctum Auth        │   │   │
│  │   │ • Shadcn/UI Components        │    │ • Eloquent ORM                │   │   │
│  │   │ • Zustand State Management    │    │ • Laravel Horizon (Queues)    │   │   │
│  │   │ • React Query (Server State)  │    │ • Laravel Telescope (Debug)   │   │   │
│  │   └───────────────────────────────┘    └───────────────────────────────┘   │   │
│  │              │                                       │                       │   │
│  └──────────────┼───────────────────────────────────────┼───────────────────────┘   │
│                 │                                       │                           │
│                 ▼                                       ▼                           │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                              DATA LAYER                                      │   │
│  ├─────────────────────────────────────────────────────────────────────────────┤   │
│  │                                                                             │   │
│  │   ┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌─────────────┐ │   │
│  │   │ PostgreSQL  │    │    Redis    │    │     S3      │    │  Meilisearch│ │   │
│  │   │ (Primary DB)│    │   (Cache)   │    │  (Assets)   │    │  (Search)   │ │   │
│  │   ├─────────────┤    ├─────────────┤    ├─────────────┤    ├─────────────┤ │   │
│  │   │ • Users     │    │ • Sessions  │    │ • Product   │    │ • Products  │ │   │
│  │   │ • Products  │    │ • Cart      │    │   images    │    │ • Content   │ │   │
│  │   │ • Orders    │    │ • Rate      │    │ • Documents │    │ • Faceted   │ │   │
│  │   │ • Inventory │    │   limiting  │    │ • Backups   │    │   filters   │ │   │
│  │   └─────────────┘    └─────────────┘    └─────────────┘    └─────────────┘ │   │
│  │                                                                             │   │
│  └─────────────────────────────────────────────────────────────────────────────┘   │
│                                                                                     │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                          EXTERNAL SERVICES                                   │   │
│  ├─────────────────────────────────────────────────────────────────────────────┤   │
│  │   ┌───────────┐  ┌───────────┐  ┌───────────┐  ┌───────────┐  ┌───────────┐│   │
│  │   │  Stripe   │  │  Resend   │  │ Sentry    │  │ PostHog   │  │ Shippo    ││   │
│  │   │ (Payments)│  │ (Email)   │  │ (Errors)  │  │(Analytics)│  │(Shipping) ││   │
│  │   └───────────┘  └───────────┘  └───────────┘  └───────────┘  └───────────┘│   │
│  └─────────────────────────────────────────────────────────────────────────────┘   │
│                                                                                     │
└─────────────────────────────────────────────────────────────────────────────────────┘
3.2 Context Diagram (C4 Level 1)
text

┌─────────────────────────────────────────────────────────────────────────────────────┐
│                              SYSTEM CONTEXT DIAGRAM                                  │
├─────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                     │
│                                                                                     │
│    ┌───────────────┐                                       ┌───────────────┐       │
│    │               │                                       │               │       │
│    │   Customer    │                                       │    Admin      │       │
│    │   [Person]    │                                       │   [Person]    │       │
│    │               │                                       │               │       │
│    └───────┬───────┘                                       └───────┬───────┘       │
│            │                                                       │               │
│            │ Browses products                    Manages products, │               │
│            │ Makes purchases                     orders, inventory │               │
│            │ Manages account                                       │               │
│            │                                                       │               │
│            ▼                                                       ▼               │
│    ┌───────────────────────────────────────────────────────────────────────┐       │
│    │                                                                       │       │
│    │                        ATELIER ARÔME                                  │       │
│    │                      [Software System]                                │       │
│    │                                                                       │       │
│    │   Artisanal aromatherapy e-commerce platform with illuminated        │       │
│    │   manuscript aesthetic. Enables browsing, purchasing, and            │       │
│    │   managing botanical essences and related products.                  │       │
│    │                                                                       │       │
│    └───────────────────────────────────────────────────────────────────────┘       │
│                    │                    │                    │                     │
│                    │                    │                    │                     │
│        ┌───────────┘          ┌─────────┘          ┌─────────┘                     │
│        │                      │                    │                               │
│        ▼                      ▼                    ▼                               │
│  ┌───────────┐         ┌───────────┐        ┌───────────┐                         │
│  │  Stripe   │         │  Resend   │        │  Shippo   │                         │
│  │ [External]│         │ [External]│        │ [External]│                         │
│  │           │         │           │        │           │                         │
│  │ Payment   │         │ Email     │        │ Shipping  │                         │
│  │ Processing│         │ Delivery  │        │ Rates &   │                         │
│  │           │         │           │        │ Labels    │                         │
│  └───────────┘         └───────────┘        └───────────┘                         │
│                                                                                     │
└─────────────────────────────────────────────────────────────────────────────────────┘
3.3 Container Diagram (C4 Level 2)
text

┌─────────────────────────────────────────────────────────────────────────────────────┐
│                              CONTAINER DIAGRAM                                       │
├─────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                     │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                         ATELIER ARÔME SYSTEM                                 │   │
│  ├─────────────────────────────────────────────────────────────────────────────┤   │
│  │                                                                             │   │
│  │   ┌─────────────────────────────────────────────────────────────────────┐   │   │
│  │   │                    WEB APPLICATION                                   │   │   │
│  │   │                  [Next.js 15 + React 19]                            │   │   │
│  │   │                                                                     │   │   │
│  │   │  Delivers the illuminated manuscript UI experience to customers    │   │   │
│  │   │  and admin portal for management. Server-side rendered for SEO.    │   │   │
│  │   │                                                                     │   │   │
│  │   │  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐   │   │   │
│  │   │  │  Storefront │ │   Product   │ │   Account   │ │    Admin    │   │   │   │
│  │   │  │    Pages    │ │    Pages    │ │    Pages    │ │   Portal    │   │   │   │
│  │   │  └─────────────┘ └─────────────┘ └─────────────┘ └─────────────┘   │   │   │
│  │   └────────────────────────────────────┬────────────────────────────────┘   │   │
│  │                                        │                                     │   │
│  │                              HTTPS/JSON│                                     │   │
│  │                                        │                                     │   │
│  │   ┌────────────────────────────────────▼────────────────────────────────┐   │   │
│  │   │                      API APPLICATION                                 │   │   │
│  │   │                    [Laravel 12 + PHP 8.3]                           │   │   │
│  │   │                                                                     │   │   │
│  │   │  Provides RESTful API for all business logic. Handles auth,        │   │   │
│  │   │  orders, products, inventory, and integrations.                    │   │   │
│  │   │                                                                     │   │   │
│  │   │  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐   │   │   │
│  │   │  │   Product   │ │    Order    │ │    User     │ │  Inventory  │   │   │   │
│  │   │  │   Service   │ │   Service   │ │   Service   │ │   Service   │   │   │   │
│  │   │  └─────────────┘ └─────────────┘ └─────────────┘ └─────────────┘   │   │   │
│  │   └─────┬───────────────────┬───────────────────┬───────────────────────┘   │   │
│  │         │                   │                   │                           │   │
│  │         ▼                   ▼                   ▼                           │   │
│  │   ┌───────────┐       ┌───────────┐       ┌───────────┐                     │   │
│  │   │PostgreSQL │       │   Redis   │       │Meilisearch│                     │   │
│  │   │[Database] │       │  [Cache]  │       │ [Search]  │                     │   │
│  │   │           │       │           │       │           │                     │   │
│  │   │Primary    │       │Sessions,  │       │Full-text  │                     │   │
│  │   │data store │       │cart, queue│       │product    │                     │   │
│  │   │           │       │           │       │search     │                     │   │
│  │   └───────────┘       └───────────┘       └───────────┘                     │   │
│  │                                                                             │   │
│  └─────────────────────────────────────────────────────────────────────────────┘   │
│                                                                                     │
└─────────────────────────────────────────────────────────────────────────────────────┘
3.4 Data Flow Diagram
text

┌─────────────────────────────────────────────────────────────────────────────────────┐
│                          ORDER PROCESSING DATA FLOW                                  │
├─────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                     │
│  ┌────────┐    ┌────────┐    ┌────────┐    ┌────────┐    ┌────────┐    ┌────────┐ │
│  │Customer│───▶│Frontend│───▶│  API   │───▶│Payment │───▶│ Order  │───▶│ Email  │ │
│  │        │    │        │    │        │    │Service │    │Service │    │Service │ │
│  └────────┘    └────────┘    └────────┘    └────────┘    └────────┘    └────────┘ │
│       │             │             │             │             │             │      │
│       │             │             │             │             │             │      │
│  1.Add to cart │    │             │             │             │             │      │
│  ──────────────┼───▶│             │             │             │             │      │
│                │    │             │             │             │             │      │
│  2.Store cart  │    │             │             │             │             │      │
│  ──────────────┼────┼────────────▶│ ────────────────────────▶ Redis        │      │
│                │    │             │             │             │             │      │
│  3.Checkout    │    │             │             │             │             │      │
│  ──────────────┼───▶│ ───────────▶│             │             │             │      │
│                │    │             │             │             │             │      │
│  4.Create      │    │             │             │             │             │      │
│    payment     │    │             │ ───────────▶│             │             │      │
│    intent      │    │             │             │             │             │      │
│                │    │             │             │             │             │      │
│  5.Confirm     │    │             │             │             │             │      │
│    payment     │    │             │             │ ────────────────────────▶ Stripe │
│                │    │             │             │             │             │      │
│  6.Webhook     │    │             │             │             │             │      │
│    received    │    │             │◀────────────│◀──────────── Stripe       │      │
│                │    │             │             │             │             │      │
│  7.Create      │    │             │             │             │             │      │
│    order       │    │             │ ───────────────────────▶ PostgreSQL    │      │
│                │    │             │             │             │             │      │
│  8.Update      │    │             │             │             │             │      │
│    inventory   │    │             │ ───────────────────────▶ PostgreSQL    │      │
│                │    │             │             │             │             │      │
│  9.Send        │    │             │             │             │             │      │
│    confirm     │    │             │             │             │ ───────────▶│      │
│                │    │             │             │             │             │      │
│  10.Email      │    │             │             │             │             │      │
│     delivered  │◀───┼─────────────┼─────────────┼─────────────┼─────────────│      │
│                │    │             │             │             │             │      │
└────────────────┴────┴─────────────┴─────────────┴─────────────┴─────────────┴──────┘
4. Technology Stack
4.1 Technology Decisions Matrix
Layer	Technology	Version	Rationale
Frontend Runtime	Next.js	15.x	App Router, RSC, excellent DX, Vercel optimization
UI Framework	React	19.x	Server Components, improved performance
Language	TypeScript	5.x	Type safety, better tooling, maintainability
Styling	Tailwind CSS	4.0	Utility-first, design token support, performance
Component Library	Shadcn/UI	Latest	Accessible, customizable, no runtime overhead
State (Client)	Zustand	5.x	Lightweight, TypeScript-first, simple API
State (Server)	TanStack Query	5.x	Caching, background updates, optimistic UI
Forms	React Hook Form	7.x	Performance, validation, accessibility
Validation	Zod	3.x	TypeScript inference, runtime validation
Backend Runtime	Laravel	12.x	Robust ecosystem, excellent ORM, queue system
Language	PHP	8.3+	Performance improvements, type system
Database	PostgreSQL	16.x	ACID compliance, JSON support, performance
Cache	Redis	7.x	Session management, queue backend, caching
Search	Meilisearch	1.x	Fast, typo-tolerant, faceted search
Storage	AWS S3	-	Scalable, CDN integration, cost-effective
Email	Resend	-	Developer experience, deliverability
Payments	Stripe	-	PCI compliance, excellent API, webhooks
Analytics	PostHog	-	Privacy-focused, self-hostable, full-featured
Error Tracking	Sentry	-	Real-time errors, performance monitoring
Hosting (FE)	Vercel	-	Edge network, automatic deployments
Hosting (BE)	Railway/Render	-	Managed infrastructure, easy scaling
4.2 Version Compatibility Matrix
text

┌─────────────────────────────────────────────────────────────────────────────────────┐
│                         VERSION COMPATIBILITY MATRIX                                 │
├─────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                     │
│  FRONTEND STACK                          BACKEND STACK                              │
│  ┌─────────────────────────────┐        ┌─────────────────────────────┐            │
│  │ Node.js         >= 20.0.0  │        │ PHP              >= 8.3.0   │            │
│  │ pnpm            >= 9.0.0   │        │ Composer         >= 2.7.0   │            │
│  │ Next.js         ~15.0.0    │        │ Laravel          ~12.0.0    │            │
│  │ React           ~19.0.0    │        │ PostgreSQL       >= 16.0    │            │
│  │ TypeScript      ~5.6.0     │        │ Redis            >= 7.0     │            │
│  │ Tailwind CSS    ~4.0.0     │        │ Meilisearch      >= 1.6     │            │
│  └─────────────────────────────┘        └─────────────────────────────┘            │
│                                                                                     │
│  DEVELOPMENT TOOLS                       PRODUCTION REQUIREMENTS                    │
│  ┌─────────────────────────────┐        ┌─────────────────────────────┐            │
│  │ ESLint          ~9.0.0     │        │ SSL Certificate  Required   │            │
│  │ Prettier        ~3.3.0     │        │ CDN              Vercel     │            │
│  │ Husky           ~9.0.0     │        │ Min. Memory FE   512MB      │            │
│  │ Vitest          ~2.0.0     │        │ Min. Memory BE   1GB        │            │
│  │ Playwright      ~1.45.0    │        │ Min. Storage     10GB       │            │
│  └─────────────────────────────┘        └─────────────────────────────┘            │
│                                                                                     │
└─────────────────────────────────────────────────────────────────────────────────────┘
5. Frontend Architecture
5.1 Directory Structure
text

frontend/
├── .github/
│   └── workflows/
│       ├── ci.yml
│       ├── deploy-preview.yml
│       └── deploy-production.yml
├── .husky/
│   ├── pre-commit
│   └── commit-msg
├── public/
│   ├── fonts/
│   │   ├── CormorantGaramond-Regular.woff2
│   │   ├── CormorantGaramond-Medium.woff2
│   │   ├── CormorantGaramond-SemiBold.woff2
│   │   ├── CrimsonPro-Regular.woff2
│   │   ├── CrimsonPro-Italic.woff2
│   │   └── GreatVibes-Regular.woff2
│   ├── images/
│   │   ├── botanicals/
│   │   ├── textures/
│   │   └── icons/
│   ├── favicon.svg
│   ├── apple-touch-icon.png
│   └── robots.txt
├── src/
│   ├── app/                              # Next.js App Router
│   │   ├── (storefront)/                 # Storefront route group
│   │   │   ├── layout.tsx
│   │   │   ├── page.tsx                  # Homepage
│   │   │   ├── compendium/
│   │   │   │   ├── page.tsx              # Product listing
│   │   │   │   └── [slug]/
│   │   │   │       └── page.tsx          # Product detail
│   │   │   ├── alchemy/
│   │   │   │   └── page.tsx              # Process page
│   │   │   ├── manuscript/
│   │   │   │   └── page.tsx              # Testimonials
│   │   │   ├── cart/
│   │   │   │   └── page.tsx              # Cart page
│   │   │   ├── checkout/
│   │   │   │   ├── page.tsx              # Checkout
│   │   │   │   └── success/
│   │   │   │       └── page.tsx          # Order confirmation
│   │   │   └── correspondence/
│   │   │       └── page.tsx              # Newsletter signup
│   │   ├── (account)/                    # Account route group
│   │   │   ├── layout.tsx
│   │   │   ├── account/
│   │   │   │   ├── page.tsx              # Account dashboard
│   │   │   │   ├── orders/
│   │   │   │   │   ├── page.tsx          # Order history
│   │   │   │   │   └── [id]/
│   │   │   │   │       └── page.tsx      # Order detail
│   │   │   │   ├── addresses/
│   │   │   │   │   └── page.tsx          # Address book
│   │   │   │   └── preferences/
│   │   │   │       └── page.tsx          # Preferences
│   │   │   ├── login/
│   │   │   │   └── page.tsx
│   │   │   ├── register/
│   │   │   │   └── page.tsx
│   │   │   └── forgot-password/
│   │   │       └── page.tsx
│   │   ├── (admin)/                      # Admin route group
│   │   │   ├── layout.tsx
│   │   │   └── admin/
│   │   │       ├── page.tsx              # Dashboard
│   │   │       ├── products/
│   │   │       │   ├── page.tsx
│   │   │       │   ├── new/
│   │   │       │   │   └── page.tsx
│   │   │       │   └── [id]/
│   │   │       │       └── edit/
│   │   │       │           └── page.tsx
│   │   │       ├── orders/
│   │   │       │   ├── page.tsx
│   │   │       │   └── [id]/
│   │   │       │       └── page.tsx
│   │   │       ├── customers/
│   │   │       │   └── page.tsx
│   │   │       ├── inventory/
│   │   │       │   └── page.tsx
│   │   │       └── settings/
│   │   │           └── page.tsx
│   │   ├── api/                          # API Routes
│   │   │   ├── auth/
│   │   │   │   └── [...nextauth]/
│   │   │   │       └── route.ts
│   │   │   ├── webhook/
│   │   │   │   └── stripe/
│   │   │   │       └── route.ts
│   │   │   └── revalidate/
│   │   │       └── route.ts
│   │   ├── layout.tsx                    # Root layout
│   │   ├── not-found.tsx
│   │   ├── error.tsx
│   │   └── globals.css
│   ├── components/
│   │   ├── ui/                           # Shadcn/UI components
│   │   │   ├── button.tsx
│   │   │   ├── card.tsx
│   │   │   ├── dialog.tsx
│   │   │   ├── dropdown-menu.tsx
│   │   │   ├── form.tsx
│   │   │   ├── input.tsx
│   │   │   ├── select.tsx
│   │   │   ├── sheet.tsx
│   │   │   ├── skeleton.tsx
│   │   │   ├── toast.tsx
│   │   │   └── ...
│   │   ├── layout/                       # Layout components
│   │   │   ├── header/
│   │   │   │   ├── header.tsx
│   │   │   │   ├── header-nav.tsx
│   │   │   │   ├── header-seal.tsx
│   │   │   │   ├── header-tools.tsx
│   │   │   │   └── mobile-nav.tsx
│   │   │   ├── footer/
│   │   │   │   ├── colophon.tsx
│   │   │   │   └── footer-nav.tsx
│   │   │   ├── atelier-banner.tsx
│   │   │   └── texture-overlay.tsx
│   │   ├── storefront/                   # Storefront components
│   │   │   ├── hero/
│   │   │   │   ├── hero.tsx
│   │   │   │   ├── hero-content.tsx
│   │   │   │   ├── hero-vessel.tsx
│   │   │   │   ├── hero-botanicals.tsx
│   │   │   │   └── scroll-indicator.tsx
│   │   │   ├── compendium/
│   │   │   │   ├── compendium-grid.tsx
│   │   │   │   ├── compendium-filters.tsx
│   │   │   │   ├── compendium-sort.tsx
│   │   │   │   └── essence-card.tsx
│   │   │   ├── alchemy/
│   │   │   │   ├── alchemy-process.tsx
│   │   │   │   ├── alchemy-step.tsx
│   │   │   │   └── apparatus-display.tsx
│   │   │   ├── manuscript/
│   │   │   │   ├── manuscript-entries.tsx
│   │   │   │   ├── manuscript-entry.tsx
│   │   │   │   └── manuscript-nav.tsx
│   │   │   └── correspondence/
│   │   │       ├── correspondence-form.tsx
│   │   │       └── envelope-visual.tsx
│   │   ├── product/                      # Product components
│   │   │   ├── product-gallery.tsx
│   │   │   ├── product-info.tsx
│   │   │   ├── product-options.tsx
│   │   │   ├── add-to-cart-button.tsx
│   │   │   └── related-products.tsx
│   │   ├── cart/                         # Cart components
│   │   │   ├── cart-drawer.tsx
│   │   │   ├── cart-item.tsx
│   │   │   ├── cart-summary.tsx
│   │   │   └── cart-empty.tsx
│   │   ├── checkout/                     # Checkout components
│   │   │   ├── checkout-form.tsx
│   │   │   ├── checkout-summary.tsx
│   │   │   ├── shipping-form.tsx
│   │   │   ├── payment-form.tsx
│   │   │   └── order-confirmation.tsx
│   │   ├── account/                      # Account components
│   │   │   ├── account-nav.tsx
│   │   │   ├── order-list.tsx
│   │   │   ├── order-detail.tsx
│   │   │   └── address-form.tsx
│   │   ├── admin/                        # Admin components
│   │   │   ├── admin-sidebar.tsx
│   │   │   ├── data-table.tsx
│   │   │   ├── stats-card.tsx
│   │   │   └── ...
│   │   └── shared/                       # Shared components
│   │       ├── illuminated-initial.tsx
│   │       ├── section-header.tsx
│   │       ├── decorative-border.tsx
│   │       ├── gold-leaf.tsx
│   │       ├── loading-skeleton.tsx
│   │       └── error-boundary.tsx
│   ├── lib/
│   │   ├── api/                          # API client
│   │   │   ├── client.ts
│   │   │   ├── products.ts
│   │   │   ├── orders.ts
│   │   │   ├── cart.ts
│   │   │   ├── auth.ts
│   │   │   └── types.ts
│   │   ├── hooks/                        # Custom hooks
│   │   │   ├── use-cart.ts
│   │   │   ├── use-products.ts
│   │   │   ├── use-auth.ts
│   │   │   ├── use-media-query.ts
│   │   │   ├── use-reduced-motion.ts
│   │   │   └── use-toast.ts
│   │   ├── stores/                       # Zustand stores
│   │   │   ├── cart-store.ts
│   │   │   ├── ui-store.ts
│   │   │   └── filter-store.ts
│   │   ├── utils/
│   │   │   ├── cn.ts                     # Class name utility
│   │   │   ├── format.ts                 # Formatting utilities
│   │   │   ├── validation.ts             # Zod schemas
│   │   │   └── constants.ts
│   │   └── config/
│   │       ├── site.ts
│   │       └── navigation.ts
│   ├── styles/
│   │   ├── globals.css                   # Global styles
│   │   ├── tokens.css                    # Design tokens
│   │   └── animations.css                # Animation keyframes
│   └── types/
│       ├── product.ts
│       ├── order.ts
│       ├── user.ts
│       └── index.ts
├── tests/
│   ├── unit/
│   ├── integration/
│   └── e2e/
├── .env.example
├── .env.local
├── .eslintrc.json
├── .gitignore
├── .prettierrc
├── components.json                       # Shadcn/UI config
├── next.config.ts
├── package.json
├── pnpm-lock.yaml
├── postcss.config.js
├── tailwind.config.ts
├── tsconfig.json
└── vitest.config.ts
5.2 Component Architecture
5.2.1 Component Hierarchy Diagram
text

┌─────────────────────────────────────────────────────────────────────────────────────┐
│                          COMPONENT HIERARCHY                                         │
├─────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                     │
│  RootLayout                                                                         │
│  ├── TextureOverlay (decorative)                                                   │
│  ├── GoldLeafAccents (decorative)                                                  │
│  ├── SkipLink (a11y)                                                               │
│  ├── AtelierBanner                                                                 │
│  ├── Header                                                                        │
│  │   ├── HeaderSeal (logo)                                                         │
│  │   ├── HeaderNav                                                                 │
│  │   │   └── NavLink[]                                                             │
│  │   ├── HeaderTools                                                               │
│  │   │   ├── SearchButton                                                          │
│  │   │   ├── CartButton                                                            │
│  │   │   └── MobileMenuToggle                                                      │
│  │   └── MobileNav                                                                 │
│  │       └── MobileNavLink[]                                                       │
│  ├── main                                                                          │
│  │   └── {children} ─────────────────────────────────────────────────────────────┐ │
│  │       │                                                                       │ │
│  │       ├── HomePage                                                            │ │
│  │       │   ├── Hero                                                            │ │
│  │       │   │   ├── HeroContent                                                 │ │
│  │       │   │   │   ├── IlluminatedInitial                                      │ │
│  │       │   │   │   ├── HeroTitle                                               │ │
│  │       │   │   │   ├── HeroSubtitle                                            │ │
│  │       │   │   │   ├── HeroExcerpt                                             │ │
│  │       │   │   │   ├── HeroActions                                             │ │
│  │       │   │   │   └── HeroCredentials                                         │ │
│  │       │   │   ├── HeroVisual                                                  │ │
│  │       │   │   │   ├── VesselDisplay                                           │ │
│  │       │   │   │   ├── BotanicalSpecimens                                      │ │
│  │       │   │   │   └── AlchemicalSymbol                                        │ │
│  │       │   │   └── ScrollIndicator                                             │ │
│  │       │   ├── CompendiumSection                                               │ │
│  │       │   │   ├── SectionHeader                                               │ │
│  │       │   │   ├── CompendiumFilters                                           │ │
│  │       │   │   ├── CompendiumGrid                                              │ │
│  │       │   │   │   └── EssenceCard[]                                           │ │
│  │       │   │   └── LoadMoreButton                                              │ │
│  │       │   ├── AlchemySection                                                  │ │
│  │       │   │   ├── SectionHeader                                               │ │
│  │       │   │   ├── AlchemyProcess                                              │ │
│  │       │   │   │   └── AlchemyStep[]                                           │ │
│  │       │   │   └── ApparatusDisplay                                            │ │
│  │       │   ├── ManuscriptSection                                               │ │
│  │       │   │   ├── SectionHeader                                               │ │
│  │       │   │   ├── ManuscriptEntries                                           │ │
│  │       │   │   │   └── ManuscriptEntry[]                                       │ │
│  │       │   │   └── ManuscriptNav                                               │ │
│  │       │   └── CorrespondenceSection                                           │ │
│  │       │       ├── CorrespondenceContent                                       │ │
│  │       │       ├── CorrespondenceForm                                          │ │
│  │       │       └── EnvelopeVisual                                              │ │
│  │       │                                                                       │ │
│  │       ├── CompendiumPage                                                      │ │
│  │       │   ├── SectionHeader                                                   │ │
│  │       │   ├── CompendiumFilters                                               │ │
│  │       │   ├── CompendiumSort                                                  │ │
│  │       │   ├── CompendiumGrid                                                  │ │
│  │       │   │   └── EssenceCard[]                                               │ │
│  │       │   └── Pagination                                                      │ │
│  │       │                                                                       │ │
│  │       ├── ProductPage                                                         │ │
│  │       │   ├── ProductGallery                                                  │ │
│  │       │   ├── ProductInfo                                                     │ │
│  │       │   │   ├── ProductTitle                                                │ │
│  │       │   │   ├── ProductHumour                                               │ │
│  │       │   │   ├── ProductDescription                                          │ │
│  │       │   │   ├── ProductNotes                                                │ │
│  │       │   │   └── ProductOptions                                              │ │
│  │       │   ├── AddToCartButton                                                 │ │
│  │       │   └── RelatedProducts                                                 │ │
│  │       │                                                                       │ │
│  │       └── CheckoutPage                                                        │ │
│  │           ├── CheckoutSteps                                                   │ │
│  │           ├── ShippingForm                                                    │ │
│  │           ├── PaymentForm                                                     │ │
│  │           └── CheckoutSummary                                                 │ │
│  │                                                                               │ │
│  ├── Colophon (footer)                                                           │
│  ├── CartDrawer (sheet)                                                          │
│  │   ├── CartItem[]                                                              │
│  │   ├── CartSummary                                                             │
│  │   └── CartActions                                                             │
│  ├── Toast (notifications)                                                       │
│  ├── BackToTop                                                                   │
│  └── A11yAnnouncer (screen reader)                                               │
│                                                                                     │
└─────────────────────────────────────────────────────────────────────────────────────┘
5.2.2 Component Specifications
EssenceCard Component
TypeScript

// src/components/storefront/compendium/essence-card.tsx

interface EssenceCardProps {
  /** Product data from API */
  product: Product;
  /** Display variant */
  variant?: 'default' | 'featured' | 'compact';
  /** Priority loading for above-fold cards */
  priority?: boolean;
  /** Callback when added to cart */
  onAddToCart?: (product: Product) => void;
}

interface Product {
  id: string;
  slug: string;
  folioNumber: string;                    // Roman numeral (I, II, III...)
  latinName: string;                      // Scientific name
  commonName: string;                     // Display name
  humour: 'calming' | 'uplifting' | 'grounding' | 'clarifying';
  rarity: 'common' | 'rare' | 'limited';
  season: 'spring' | 'summer' | 'autumn' | 'winter';
  description: string;
  notes: string[];                        // Scent notes
  extraction: string;                     // Extraction method
  price: number;                          // In cents
  compareAtPrice?: number;                // Original price if on sale
  images: ProductImage[];
  inStock: boolean;
  stockQuantity: number;
}

// Component behavior:
// - Displays botanical illustration (SVG) based on product type
// - Shows gold folio number badge
// - Shows rarity badge for rare/limited products
// - Hover state lifts card and highlights border
// - Add to cart button triggers cart drawer
// - Respects reduced motion preferences
// - Skeleton loading state when data pending
CartDrawer Component
TypeScript

// src/components/cart/cart-drawer.tsx

interface CartDrawerProps {
  /** Controlled open state */
  open: boolean;
  /** Callback when drawer should close */
  onOpenChange: (open: boolean) => void;
}

// Component behavior:
// - Uses Shadcn Sheet component for accessibility
// - Traps focus when open
// - Closes on Escape key
// - Closes when clicking overlay
// - Displays empty state when cart is empty
// - Shows cart items with quantity controls
// - Displays running total
// - "Dispatch to Atelier" button navigates to checkout
// - Announces changes to screen readers
// - Persists cart to localStorage via Zustand
5.3 State Management Architecture
5.3.1 State Distribution
text

┌─────────────────────────────────────────────────────────────────────────────────────┐
│                          STATE MANAGEMENT ARCHITECTURE                               │
├─────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                     │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                           SERVER STATE                                       │   │
│  │                        (TanStack Query)                                      │   │
│  ├─────────────────────────────────────────────────────────────────────────────┤   │
│  │                                                                             │   │
│  │  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐        │   │
│  │  │  Products   │  │   Orders    │  │    User     │  │Testimonials │        │   │
│  │  │   Query     │  │   Query     │  │   Query     │  │   Query     │        │   │
│  │  ├─────────────┤  ├─────────────┤  ├─────────────┤  ├─────────────┤        │   │
│  │  │ • List      │  │ • History   │  │ • Profile   │  │ • List      │        │   │
│  │  │ • Detail    │  │ • Detail    │  │ • Addresses │  │ • Paginated │        │   │
│  │  │ • Search    │  │ • Tracking  │  │ • Prefs     │  │             │        │   │
│  │  │ • Related   │  │             │  │             │  │             │        │   │
│  │  └─────────────┘  └─────────────┘  └─────────────┘  └─────────────┘        │   │
│  │                                                                             │   │
│  │  Features: Caching, Background Refetch, Optimistic Updates, Prefetching    │   │
│  │                                                                             │   │
│  └─────────────────────────────────────────────────────────────────────────────┘   │
│                                                                                     │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                           CLIENT STATE                                       │   │
│  │                           (Zustand)                                          │   │
│  ├─────────────────────────────────────────────────────────────────────────────┤   │
│  │                                                                             │   │
│  │  ┌─────────────────────────┐  ┌─────────────────────────┐                   │   │
│  │  │       Cart Store        │  │        UI Store         │                   │   │
│  │  ├─────────────────────────┤  ├─────────────────────────┤                   │   │
│  │  │ State:                  │  │ State:                  │                   │   │
│  │  │ • items: CartItem[]     │  │ • mobileMenuOpen: bool  │                   │   │
│  │  │ • isOpen: boolean       │  │ • cartDrawerOpen: bool  │                   │   │
│  │  │                         │  │ • headerScrolled: bool  │                   │   │
│  │  │ Actions:                │  │ • activeFilter: string  │                   │   │
│  │  │ • addItem()             │  │                         │                   │   │
│  │  │ • removeItem()          │  │ Actions:                │                   │   │
│  │  │ • updateQuantity()      │  │ • toggleMobileMenu()    │                   │   │
│  │  │ • clearCart()           │  │ • toggleCartDrawer()    │                   │   │
│  │  │ • getTotal()            │  │ • setActiveFilter()     │                   │   │
│  │  │ • getCount()            │  │                         │                   │   │
│  │  │                         │  │                         │                   │   │
│  │  │ Persistence:            │  │ Persistence:            │                   │   │
│  │  │ localStorage            │  │ None (ephemeral)        │                   │   │
│  │  └─────────────────────────┘  └─────────────────────────┘                   │   │
│  │                                                                             │   │
│  └─────────────────────────────────────────────────────────────────────────────┘   │
│                                                                                     │
│  ┌─────────────────────────────────────────────────────────────────────────────┐   │
│  │                            URL STATE                                         │   │
│  │                     (Next.js App Router)                                     │   │
│  ├─────────────────────────────────────────────────────────────────────────────┤   │
│  │                                                                             │   │
│  │  Query Parameters:                                                          │   │
│  │  • ?humour=calming         → Filter by humour                               │   │
│  │  • ?season=summer          → Filter by season                               │   │
│  │  • ?sort=price-asc         → Sort order                                     │   │
│  │  • ?page=2                 → Pagination                                     │   │
│  │  • ?search=lavender        → Search query                                   │   │
│  │                                                                             │   │
│  │  Benefits: Shareable URLs, Browser history, SSR hydration                   │   │
│  │                                                                             │   │
│  └─────────────────────────────────────────────────────────────────────────────┘   │
│                                                                                     │
└─────────────────────────────────────────────────────────────────────────────────────┘
5.3.2 Cart Store Implementation
TypeScript

// src/lib/stores/cart-store.ts

import { create } from 'zustand';
import { persist, createJSONStorage } from 'zustand/middleware';

interface CartItem {
  id: string;
  productId: string;
  name: string;
  latinName: string;
  humour: string;
  price: number;
  quantity: number;
  image: string;
  addedAt: string;
}

interface CartState {
  items: CartItem[];
  isOpen: boolean;
  isLoading: boolean;
}

interface CartActions {
  addItem: (product: Product, quantity?: number) => void;
  removeItem: (itemId: string) => void;
  updateQuantity: (itemId: string, quantity: number) => void;
  clearCart: () => void;
  openCart: () => void;
  closeCart: () => void;
  toggleCart: () => void;
  getSubtotal: () => number;
  getItemCount: () => number;
  getItem: (productId: string) => CartItem | undefined;
}

type CartStore = CartState & CartActions;

const MAX_CART_ITEMS = 12;
const MAX_ITEM_QUANTITY = 10;

export const useCartStore = create<CartStore>()(
  persist(
    (set, get) => ({
      // State
      items: [],
      isOpen: false,
      isLoading: false,

      // Actions
      addItem: (product, quantity = 1) => {
        const { items } = get();
        const existingItem = items.find(item => item.productId === product.id);

        if (existingItem) {
          // Update quantity
          const newQuantity = Math.min(
            existingItem.quantity + quantity,
            MAX_ITEM_QUANTITY
          );
          set({
            items: items.map(item =>
              item.productId === product.id
                ? { ...item, quantity: newQuantity }
                : item
            ),
          });
        } else {
          // Add new item
          if (items.length >= MAX_CART_ITEMS) {
            // Handle max items - could throw or return false
            return;
          }
          
          const newItem: CartItem = {
            id: crypto.randomUUID(),
            productId: product.id,
            name: product.commonName,
            latinName: product.latinName,
            humour: product.humour,
            price: product.price,
            quantity,
            image: product.images[0]?.url || '',
            addedAt: new Date().toISOString(),
          };
          
          set({ items: [...items, newItem] });
        }
      },

      removeItem: (itemId) => {
        set({ items: get().items.filter(item => item.id !== itemId) });
      },

      updateQuantity: (itemId, quantity) => {
        if (quantity < 1) {
          get().removeItem(itemId);
          return;
        }
        
        set({
          items: get().items.map(item =>
            item.id === itemId
              ? { ...item, quantity: Math.min(quantity, MAX_ITEM_QUANTITY) }
              : item
          ),
        });
      },

      clearCart: () => set({ items: [] }),
      
      openCart: () => set({ isOpen: true }),
      
      closeCart: () => set({ isOpen: false }),
      
      toggleCart: () => set(state => ({ isOpen: !state.isOpen })),

      getSubtotal: () => {
        return get().items.reduce(
          (total, item) => total + item.price * item.quantity,
          0
        );
      },

      getItemCount: () => {
        return get().items.reduce((count, item) => count + item.quantity, 0);
      },

      getItem: (productId) => {
        return get().items.find(item => item.productId === productId);
      },
    }),
    {
      name: 'atelier-arome-cart',
      storage: createJSONStorage(() => localStorage),
      partialize: (state) => ({ items: state.items }), // Only persist items
    }
  )
);
5.4 Design System
5.4.1 Design Tokens
CSS

/* src/styles/tokens.css */

:root {
  /* ============================================
     COLOR TOKENS
     ============================================ */
  
  /* Ink (Primary Text/Backgrounds) */
  --color-ink-900: #1A1D16;
  --color-ink-800: #2A2D26;
  --color-ink-700: #3A3D36;
  --color-ink-600: #4A4D46;
  --color-ink-500: #5A5D56;
  --color-ink-400: #6A6D66;
  --color-ink-300: #8A8D86;
  --color-ink-200: #AAADA6;
  --color-ink-100: #CACDC6;
  
  /* Gold (Accent) */
  --color-gold-900: #6B5420;
  --color-gold-800: #8B7340;
  --color-gold-700: #A98750;
  --color-gold-600: #C9A769;
  --color-gold-500: #D4B87A;
  --color-gold-400: #DFC98B;
  --color-gold-300: #E8D8B6;
  --color-gold-200: #F2E8D1;
  --color-gold-100: #FAF5EB;
  
  /* Parchment (Background) */
  --color-parchment-900: #D5D1C6;
  --color-parchment-800: #E0DCD1;
  --color-parchment-700: #E8E4D9;
  --color-parchment-600: #EDE9DE;
  --color-parchment-500: #F2EEE5;
  --color-parchment-400: #F5F1EB;
  --color-parchment-300: #F8F5F0;
  --color-parchment-200: #FAF8F5;
  --color-parchment-100: #FDFCFA;
  
  /* Botanical Accents */
  --color-lavender: #B8A9C9;
  --color-eucalyptus: #7CB9A0;
  --color-bergamot: #F5D489;
  --color-rosehip: #E8B4B8;
  --color-sage: #7C6354;
  
  /* Semantic Colors */
  --color-success: #7CB9A0;
  --color-warning: #F5D489;
  --color-error: #E8A0A0;
  --color-info: #B8A9C9;
  
  /* ============================================
     TYPOGRAPHY TOKENS
     ============================================ */
  
  /* Font Families */
  --font-display: 'Cormorant Garamond', 'Georgia', serif;
  --font-body: 'Crimson Pro', 'Georgia', serif;
  --font-accent: 'Great Vibes', cursive;
  --font-mono: 'JetBrains Mono', monospace;
  
  /* Font Sizes (Fluid) */
  --text-xs: clamp(0.75rem, 0.7rem + 0.25vw, 0.875rem);
  --text-sm: clamp(0.875rem, 0.8rem + 0.35vw, 1rem);
  --text-base: clamp(1rem, 0.95rem + 0.25vw, 1.125rem);
  --text-lg: clamp(1.125rem, 1rem + 0.5vw, 1.25rem);
  --text-xl: clamp(1.25rem, 1.1rem + 0.75vw, 1.5rem);
  --text-2xl: clamp(1.5rem, 1.25rem + 1.25vw, 2rem);
  --text-3xl: clamp(2rem, 1.5rem + 2.5vw, 3rem);
  --text-4xl: clamp(2.5rem, 2rem + 2.5vw, 4rem);
  --text-5xl: clamp(3rem, 2.5rem + 2.5vw, 5rem);
  
  /* Line Heights */
  --leading-none: 1;
  --leading-tight: 1.1;
  --leading-snug: 1.25;
  --leading-normal: 1.5;
  --leading-relaxed: 1.625;
  --leading-loose: 1.75;
  
  /* Letter Spacing */
  --tracking-tighter: -0.05em;
  --tracking-tight: -0.025em;
  --tracking-normal: 0;
  --tracking-wide: 0.025em;
  --tracking-wider: 0.05em;
  --tracking-widest: 0.1em;
  
  /* ============================================
     SPACING TOKENS
     ============================================ */
  
  --space-0: 0;
  --space-px: 1px;
  --space-0-5: 0.125rem;
  --space-1: 0.25rem;
  --space-1-5: 0.375rem;
  --space-2: 0.5rem;
  --space-2-5: 0.625rem;
  --space-3: 0.75rem;
  --space-3-5: 0.875rem;
  --space-4: 1rem;
  --space-5: 1.25rem;
  --space-6: 1.5rem;
  --space-7: 1.75rem;
  --space-8: 2rem;
  --space-9: 2.25rem;
  --space-10: 2.5rem;
  --space-11: 2.75rem;
  --space-12: 3rem;
  --space-14: 3.5rem;
  --space-16: 4rem;
  --space-20: 5rem;
  --space-24: 6rem;
  --space-28: 7rem;
  --space-32: 8rem;
  --space-36: 9rem;
  --space-40: 10rem;
  --space-44: 11rem;
  --space-48: 12rem;
  
  /* ============================================
     LAYOUT TOKENS
     ============================================ */
  
  --container-max: 1400px;
  --container-padding: clamp(1rem, 5vw, 2rem);
  
  /* ============================================
     BORDER RADIUS TOKENS
     ============================================ */
  
  --radius-none: 0;
  --radius-sm: 0.125rem;
  --radius-md: 0.25rem;
  --radius-lg: 0.5rem;
  --radius-xl: 1rem;
  --radius-2xl: 1.5rem;
  --radius-3xl: 2rem;
  --radius-full: 9999px;
  
  /* ============================================
     SHADOW TOKENS
     ============================================ */
  
  --shadow-sm: 0 1px 2px rgb(42 45 38 / 0.05);
  --shadow-md: 0 4px 12px rgb(42 45 38 / 0.08);
  --shadow-lg: 0 8px 24px rgb(42 45 38 / 0.1);
  --shadow-xl: 0 16px 48px rgb(42 45 38 / 0.12);
  --shadow-2xl: 0 24px 64px rgb(42 45 38 / 0.15);
  --shadow-gold: 0 0 40px rgb(201 167 105 / 0.2);
  
  /* ============================================
     TRANSITION TOKENS
     ============================================ */
  
  --duration-instant: 0ms;
  --duration-fast: 150ms;
  --duration-base: 300ms;
  --duration-slow: 500ms;
  --duration-slower: 800ms;
  
  --ease-linear: linear;
  --ease-in: cubic-bezier(0.4, 0, 1, 1);
  --ease-out: cubic-bezier(0, 0, 0.2, 1);
  --ease-in-out: cubic-bezier(0.4, 0, 0.2, 1);
  --ease-bounce: cubic-bezier(0.34, 1.56, 0.64, 1);
  
  /* ============================================
     Z-INDEX TOKENS
     ============================================ */
  
  --z-base: 1;
  --z-elevated: 10;
  --z-dropdown: 50;
  --z-sticky: 100;
  --z-overlay: 500;
  --z-modal: 1000;
  --z-popover: 1500;
  --z-toast: 2000;
  --z-tooltip: 2500;
  --z-max: 9999;
}
5.4.2 Tailwind Configuration
TypeScript

// tailwind.config.ts

import type { Config } from 'tailwindcss';
import { fontFamily } from 'tailwindcss/defaultTheme';

const config: Config = {
  darkMode: ['class'],
  content: [
    './src/**/*.{js,ts,jsx,tsx,mdx}',
    './components/**/*.{js,ts,jsx,tsx,mdx}',
  ],
  theme: {
    container: {
      center: true,
      padding: 'var(--container-padding)',
      screens: {
        '2xl': 'var(--container-max)',
      },
    },
    extend: {
      colors: {
        ink: {
          DEFAULT: 'var(--color-ink-800)',
          50: 'var(--color-ink-100)',
          100: 'var(--color-ink-200)',
          200: 'var(--color-ink-300)',
          300: 'var(--color-ink-400)',
          400: 'var(--color-ink-500)',
          500: 'var(--color-ink-600)',
          600: 'var(--color-ink-700)',
          700: 'var(--color-ink-800)',
          800: 'var(--color-ink-900)',
          900: 'var(--color-ink-900)',
        },
        gold: {
          DEFAULT: 'var(--color-gold-600)',
          50: 'var(--color-gold-100)',
          100: 'var(--color-gold-200)',
          200: 'var(--color-gold-300)',
          300: 'var(--color-gold-400)',
          400: 'var(--color-gold-500)',
          500: 'var(--color-gold-600)',
          600: 'var(--color-gold-700)',
          700: 'var(--color-gold-800)',
          800: 'var(--color-gold-900)',
          900: 'var(--color-gold-900)',
        },
        parchment: {
          DEFAULT: 'var(--color-parchment-200)',
          50: 'var(--color-parchment-100)',
          100: 'var(--color-parchment-200)',
          200: 'var(--color-parchment-300)',
          300: 'var(--color-parchment-400)',
          400: 'var(--color-parchment-500)',
          500: 'var(--color-parchment-600)',
          600: 'var(--color-parchment-700)',
          700: 'var(--color-parchment-800)',
          800: 'var(--color-parchment-900)',
          900: 'var(--color-parchment-900)',
        },
        botanical: {
          lavender: 'var(--color-lavender)',
          eucalyptus: 'var(--color-eucalyptus)',
          bergamot: 'var(--color-bergamot)',
          rosehip: 'var(--color-rosehip)',
          sage: 'var(--color-sage)',
        },
      },
      fontFamily: {
        display: ['var(--font-display)', ...fontFamily.serif],
        body: ['var(--font-body)', ...fontFamily.serif],
        accent: ['var(--font-accent)', 'cursive'],
        mono: ['var(--font-mono)', ...fontFamily.mono],
      },
      fontSize: {
        xs: 'var(--text-xs)',
        sm: 'var(--text-sm)',
        base: 'var(--text-base)',
        lg: 'var(--text-lg)',
        xl: 'var(--text-xl)',
        '2xl': 'var(--text-2xl)',
        '3xl': 'var(--text-3xl)',
        '4xl': 'var(--text-4xl)',
        '5xl': 'var(--text-5xl)',
      },
      borderRadius: {
        sm: 'var(--radius-sm)',
        md: 'var(--radius-md)',
        lg: 'var(--radius-lg)',
        xl: 'var(--radius-xl)',
        '2xl': 'var(--radius-2xl)',
        '3xl': 'var(--radius-3xl)',
      },
      boxShadow: {
        sm: 'var(--shadow-sm)',
        md: 'var(--shadow-md)',
        lg: 'var(--shadow-lg)',
        xl: 'var(--shadow-xl)',
        '2xl': 'var(--shadow-2xl)',
        gold: 'var(--shadow-gold)',
      },
      transitionDuration: {
        fast: 'var(--duration-fast)',
        base: 'var(--duration-base)',
        slow: 'var(--duration-slow)',
        slower: 'var(--duration-slower)',
      },
      transitionTimingFunction: {
        bounce: 'var(--ease-bounce)',
      },
      animation: {
        'fade-in': 'fadeIn var(--duration-base) var(--ease-out)',
        'fade-out': 'fadeOut var(--duration-base) var(--ease-in)',
        'slide-in-right': 'slideInRight var(--duration-base) var(--ease-out)',
        'slide-out-right': 'slideOutRight var(--duration-base) var(--ease-in)',
        'slide-in-up': 'slideInUp var(--duration-base) var(--ease-out)',
        'float': 'float 6s ease-in-out infinite',
        'rotate-slow': 'rotate 60s linear infinite',
        'pulse-gold': 'pulseGold 3s ease-in-out infinite',
      },
      keyframes: {
        fadeIn: {
          from: { opacity: '0' },
          to: { opacity: '1' },
        },
        fadeOut: {
          from: { 
Some
