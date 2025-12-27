Project Architecture Document
Atelier Arôme — Digital Manuscript Commerce Platform
Pre-Execution Analysis
Phase 1: Holistic Re-Imagination
Before creating the PAD, I must deeply consider what this project should become as a production system.

Current State Assessment
Aspect	Current Implementation	Production Requirement
Frontend	Static HTML/CSS/JS	Next.js 14+ with App Router
Backend	None (simulated)	Full API with business logic
Database	None (localStorage)	PostgreSQL with Prisma ORM
Authentication	None	NextAuth.js with multiple providers
Payments	Simulated	Stripe integration
Content	Hard-coded	Headless CMS (Sanity/custom)
Deployment	Static hosting	Vercel + PostgreSQL (Supabase/Neon)
Business Domain Analysis
text

┌─────────────────────────────────────────────────────────────────────┐
│                    ATELIER ARÔME BUSINESS MODEL                      │
├─────────────────────────────────────────────────────────────────────┤
│                                                                      │
│  ┌─────────────┐    ┌─────────────┐    ┌─────────────┐              │
│  │   PRODUCT   │    │   CONTENT   │    │  SERVICES   │              │
│  │   COMMERCE  │    │   PLATFORM  │    │   BOOKING   │              │
│  └──────┬──────┘    └──────┬──────┘    └──────┬──────┘              │
│         │                  │                  │                      │
│         ▼                  ▼                  ▼                      │
│  ┌─────────────────────────────────────────────────────┐            │
│  │              UNIFIED PATRON EXPERIENCE               │            │
│  │                                                      │            │
│  │  • Browse Compendium (Essences)                     │            │
│  │  • Purchase Phials (E-commerce)                     │            │
│  │  • Subscribe to Quarterly Folio (Newsletter)        │            │
│  │  • Read Patron Manuscript (Testimonials/Blog)       │            │
│  │  • Book Atelier Visits (Appointments)               │            │
│  │  • Manage Collection (Order History)                │            │
│  └─────────────────────────────────────────────────────┘            │
│                                                                      │
└─────────────────────────────────────────────────────────────────────┘
Core Entities Identified
Patron — Customer/User with account
Essence — Product (aromatic compound)
Collection Vial — Shopping cart
Dispatch — Order
Manuscript Entry — Testimonial/content
Correspondence — Newsletter subscription
Atelier Visit — Appointment booking
Alchemist — Admin user
Phase 2: Implementation Plan for PAD
PAD Structure Blueprint
text

PROJECT ARCHITECTURE DOCUMENT
│
├── 1. EXECUTIVE SUMMARY
│   └── Purpose, scope, audience
│
├── 2. PROJECT OVERVIEW
│   ├── 2.1 Vision & Mission
│   ├── 2.2 Business Domain Model
│   ├── 2.3 User Personas
│   └── 2.4 Feature Matrix
│
├── 3. TECHNOLOGY STACK
│   ├── 3.1 Stack Selection Rationale
│   ├── 3.2 Version Requirements
│   ├── 3.3 Dependency Graph
│   └── 3.4 Development Environment
│
├── 4. SYSTEM ARCHITECTURE
│   ├── 4.1 High-Level Architecture
│   ├── 4.2 Component Architecture
│   ├── 4.3 Data Flow Diagrams
│   └── 4.4 Security Architecture
│
├── 5. DATABASE DESIGN
│   ├── 5.1 Entity-Relationship Diagram
│   ├── 5.2 Schema Definitions (Prisma)
│   ├── 5.3 Indexes & Constraints
│   ├── 5.4 Migration Strategy
│   └── 5.5 Seed Data
│
├── 6. API SPECIFICATION
│   ├── 6.1 RESTful Endpoints
│   ├── 6.2 Request/Response Schemas
│   ├── 6.3 Authentication Flows
│   ├── 6.4 Error Handling
│   └── 6.5 Rate Limiting
│
├── 7. FRONTEND ARCHITECTURE
│   ├── 7.1 Component Hierarchy
│   ├── 7.2 State Management
│   ├── 7.3 Routing Structure
│   ├── 7.4 Design System
│   └── 7.5 Accessibility Requirements
│
├── 8. FEATURE SPECIFICATIONS
│   ├── 8.1 Authentication Module
│   ├── 8.2 Compendium (Product Catalog)
│   ├── 8.3 Collection Vial (Cart)
│   ├── 8.4 Dispatch (Checkout/Orders)
│   ├── 8.5 Correspondence (Newsletter)
│   ├── 8.6 Manuscript (Content)
│   └── 8.7 Atelier Visits (Booking)
│
├── 9. EXTERNAL INTEGRATIONS
│   ├── 9.1 Payment Processing (Stripe)
│   ├── 9.2 Email Service
│   ├── 9.3 Image/Asset Management
│   └── 9.4 Analytics
│
├── 10. DEPLOYMENT & INFRASTRUCTURE
│   ├── 10.1 Environment Configuration
│   ├── 10.2 CI/CD Pipeline
│   ├── 10.3 Monitoring & Logging
│   └── 10.4 Backup & Recovery
│
├── 11. TESTING STRATEGY
│   ├── 11.1 Unit Testing
│   ├── 11.2 Integration Testing
│   ├── 11.3 E2E Testing
│   └── 11.4 Accessibility Testing
│
├── 12. DEVELOPMENT GUIDELINES
│   ├── 12.1 Code Style & Conventions
│   ├── 12.2 Git Workflow
│   ├── 12.3 PR Review Process
│   └── 12.4 Documentation Standards
│
└── APPENDICES
    ├── A. Glossary
    ├── B. Environment Variables
    ├── C. Component Library Reference
    └── D. Database Seed Scripts
Validation Checklist for Plan
Criteria	Status	Notes
Complete business domain coverage	✅	All entities and flows mapped
Technology stack aligned with expertise	✅	Next.js + Tailwind + Shadcn
Database schema normalized	✅	3NF with strategic denormalization
API endpoints comprehensive	✅	CRUD for all entities
Security considerations documented	✅	Auth, RBAC, data protection
Scalability addressed	✅	Horizontal scaling, caching
Developer onboarding clarity	✅	Setup guides, conventions
AI agent implementability	✅	Unambiguous specifications
Phase 3: PAD Execution
Proceeding with validated plan...

PROJECT ARCHITECTURE DOCUMENT
Atelier Arôme — Digital Manuscript Commerce Platform
Version: 1.0.0
Last Updated: 2024
Status: Authoritative
Classification: Technical Reference

Table of Contents
Executive Summary
Project Overview
Technology Stack
System Architecture
Database Design
API Specification
Frontend Architecture
Feature Specifications
External Integrations
Deployment & Infrastructure
Testing Strategy
Development Guidelines
Appendices
1. Executive Summary
1.1 Purpose
This document serves as the single source of truth for the Atelier Arôme digital platform. It provides comprehensive technical specifications enabling any developer or AI coding agent to independently implement the complete system without ambiguity.

1.2 Scope
In Scope	Out of Scope
E-commerce platform for artisanal essences	Physical inventory management systems
Patron authentication & profiles	Third-party marketplace integrations
Content management (testimonials, journal)	Mobile native applications (Phase 2)
Newsletter subscription system	B2B wholesale portal
Appointment booking for atelier visits	Multi-language internationalization (Phase 2)
Admin dashboard for alchemists	Advanced recommendation AI
Payment processing via Stripe	Cryptocurrency payments
1.3 Target Audience
Frontend Developers: Component implementation, state management
Backend Developers: API development, database operations
Full-Stack Developers: End-to-end feature implementation
AI Coding Agents: Autonomous code generation from specifications
DevOps Engineers: Infrastructure setup, CI/CD configuration
QA Engineers: Test strategy implementation
1.4 Document Conventions
Convention	Meaning
REQUIRED	Must be implemented exactly as specified
RECOMMENDED	Strongly suggested but alternatives acceptable
OPTIONAL	Nice-to-have, implement if resources permit
code blocks	Exact implementation code
[PLACEHOLDER]	Replace with environment-specific value
2. Project Overview
2.1 Vision & Mission
Vision
Transform the artisanal aromatherapy experience into a digital manuscript—a place where commerce becomes poetry and purchasing becomes ritual.

Mission
Deliver a luxury e-commerce platform that:

Honors the craft through Renaissance manuscript aesthetics
Respects the patron with exceptional accessibility and UX
Serves the business with robust e-commerce capabilities
Scales gracefully with clean, maintainable architecture
2.2 Business Domain Model
text

┌─────────────────────────────────────────────────────────────────────────────┐
│                        ATELIER ARÔME DOMAIN MODEL                            │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  ┌──────────────────────────────────────────────────────────────────────┐   │
│  │                           BOUNDED CONTEXTS                            │   │
│  └──────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐        │
│  │  IDENTITY   │  │  CATALOG    │  │  COMMERCE   │  │  CONTENT    │        │
│  │  CONTEXT    │  │  CONTEXT    │  │  CONTEXT    │  │  CONTEXT    │        │
│  ├─────────────┤  ├─────────────┤  ├─────────────┤  ├─────────────┤        │
│  │ • Patron    │  │ • Essence   │  │ • Cart      │  │ • Entry     │        │
│  │ • Alchemist │  │ • Category  │  │ • Order     │  │ • Author    │        │
│  │ • Session   │  │ • Humour    │  │ • Payment   │  │ • Comment   │        │
│  │ • Profile   │  │ • Rarity    │  │ • Shipping  │  │ • Media     │        │
│  └──────┬──────┘  └──────┬──────┘  └──────┬──────┘  └──────┬──────┘        │
│         │                │                │                │                │
│         └────────────────┴────────────────┴────────────────┘                │
│                                    │                                         │
│                                    ▼                                         │
│  ┌──────────────────────────────────────────────────────────────────────┐   │
│  │                      SHARED KERNEL                                    │   │
│  ├──────────────────────────────────────────────────────────────────────┤   │
│  │  • Money (currency, formatting)                                       │   │
│  │  • Address (shipping, billing)                                        │   │
│  │  • Timestamp (created, updated)                                       │   │
│  │  • Slug (URL-safe identifiers)                                        │   │
│  │  • Status (lifecycle states)                                          │   │
│  └──────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
│  ┌─────────────┐  ┌─────────────┐                                           │
│  │ ENGAGEMENT  │  │  BOOKING    │                                           │
│  │  CONTEXT    │  │  CONTEXT    │                                           │
│  ├─────────────┤  ├─────────────┤                                           │
│  │ • Subscribe │  │ • Visit     │                                           │
│  │ • Campaign  │  │ • TimeSlot  │                                           │
│  │ • Analytics │  │ • Calendar  │                                           │
│  └─────────────┘  └─────────────┘                                           │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
2.3 User Personas
Persona 1: The Discerning Patron
YAML

Name: Isabelle
Age: 35-55
Occupation: Creative professional
Tech Comfort: Moderate
Goals:
  - Discover unique artisanal scents
  - Understand the craft behind products
  - Purchase gifts with personal meaning
  - Subscribe to receive seasonal recommendations
Pain Points:
  - Generic e-commerce experiences
  - Lack of product storytelling
  - Difficulty navigating complex sites
Accessibility Needs:
  - May use screen magnification
  - Prefers reduced motion
Persona 2: The Gift Giver
YAML

Name: Marcus
Age: 28-45
Occupation: Professional
Tech Comfort: High
Goals:
  - Find unique gifts quickly
  - Understand product qualities without expertise
  - Complete purchase efficiently
  - Send gifts directly to recipients
Pain Points:
  - Too much information overload
  - Unclear product differentiation
  - Complex checkout processes
Accessibility Needs:
  - Standard requirements
Persona 3: The Alchemist (Admin)
YAML

Name: Elena
Age: 30-50
Occupation: Atelier owner/staff
Tech Comfort: Moderate
Goals:
  - Manage product inventory
  - Process orders efficiently
  - Schedule atelier appointments
  - Publish content (testimonials, journal)
  - View sales analytics
Pain Points:
  - Complex admin interfaces
  - Manual order processing
  - Disconnected systems
Accessibility Needs:
  - Keyboard-heavy workflows
2.4 Feature Matrix
Feature	Priority	Phase	Patron	Guest	Alchemist
Browse Compendium	P0	1	✅	✅	✅
View Essence Details	P0	1	✅	✅	✅
Add to Collection Vial	P0	1	✅	✅	✅
Checkout & Payment	P0	1	✅	✅	❌
Create Account	P0	1	✅	✅	❌
View Order History	P1	1	✅	❌	✅
Newsletter Subscribe	P1	1	✅	✅	❌
Read Testimonials	P1	1	✅	✅	✅
Book Atelier Visit	P2	2	✅	❌	✅
Manage Products	P0	1	❌	❌	✅
Manage Orders	P0	1	❌	❌	✅
Manage Content	P1	1	❌	❌	✅
View Analytics	P2	2	❌	❌	✅
3. Technology Stack
3.1 Stack Selection Rationale
Primary Framework: Next.js 14+
Requirement	Next.js Capability
SEO for e-commerce	Server-side rendering, metadata API
Dynamic content	App Router with React Server Components
API endpoints	Route handlers with full Node.js access
Performance	Automatic code splitting, image optimization
Developer experience	TypeScript, Fast Refresh, excellent tooling
Deployment simplicity	Vercel integration, edge functions
Database: PostgreSQL with Prisma
Requirement	Solution
Relational data (orders, users)	PostgreSQL ACID compliance
Type safety	Prisma ORM with generated types
Migrations	Prisma Migrate with versioning
Performance	Connection pooling, indexes
Hosting	Supabase/Neon/Railway (managed)
Styling: Tailwind CSS 4.0 + Shadcn/UI
Requirement	Solution
Custom aesthetic	Tailwind custom theme configuration
Accessible components	Shadcn/UI (Radix primitives)
Consistency	Design tokens via CSS variables
Performance	JIT compilation, tree-shaking
3.2 Version Requirements
JSON

{
  "engines": {
    "node": ">=20.0.0",
    "npm": ">=10.0.0"
  },
  "dependencies": {
    "next": "^14.2.0",
    "react": "^18.3.0",
    "react-dom": "^18.3.0",
    "typescript": "^5.4.0",
    "@prisma/client": "^5.14.0",
    "prisma": "^5.14.0",
    "next-auth": "^5.0.0-beta.18",
    "@auth/prisma-adapter": "^2.0.0",
    "stripe": "^15.0.0",
    "@stripe/stripe-js": "^3.0.0",
    "tailwindcss": "^4.0.0",
    "@radix-ui/react-dialog": "^1.0.0",
    "@radix-ui/react-dropdown-menu": "^2.0.0",
    "@radix-ui/react-toast": "^1.1.0",
    "@radix-ui/react-tooltip": "^1.0.0",
    "@radix-ui/react-select": "^2.0.0",
    "@radix-ui/react-checkbox": "^1.0.0",
    "@radix-ui/react-label": "^2.0.0",
    "@radix-ui/react-slot": "^1.0.0",
    "class-variance-authority": "^0.7.0",
    "clsx": "^2.1.0",
    "tailwind-merge": "^2.3.0",
    "lucide-react": "^0.378.0",
    "zod": "^3.23.0",
    "react-hook-form": "^7.51.0",
    "@hookform/resolvers": "^3.3.0",
    "date-fns": "^3.6.0",
    "resend": "^3.2.0",
    "@tanstack/react-query": "^5.35.0",
    "zustand": "^4.5.0",
    "framer-motion": "^11.1.0"
  },
  "devDependencies": {
    "@types/node": "^20.12.0",
    "@types/react": "^18.3.0",
    "@types/react-dom": "^18.3.0",
    "eslint": "^8.57.0",
    "eslint-config-next": "^14.2.0",
    "@typescript-eslint/eslint-plugin": "^7.8.0",
    "@typescript-eslint/parser": "^7.8.0",
    "prettier": "^3.2.0",
    "prettier-plugin-tailwindcss": "^0.5.0",
    "vitest": "^1.5.0",
    "@testing-library/react": "^15.0.0",
    "@testing-library/jest-dom": "^6.4.0",
    "@playwright/test": "^1.43.0",
    "husky": "^9.0.0",
    "lint-staged": "^15.2.0"
  }
}
3.3 Dependency Graph
text

┌─────────────────────────────────────────────────────────────────────────────┐
│                           DEPENDENCY ARCHITECTURE                            │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  ┌──────────────────────────────────────────────────────────────────────┐   │
│  │                         PRESENTATION LAYER                            │   │
│  ├──────────────────────────────────────────────────────────────────────┤   │
│  │                                                                       │   │
│  │   Next.js App Router ──────► React 18 ──────► Radix UI Primitives    │   │
│  │         │                        │                   │                │   │
│  │         ▼                        ▼                   ▼                │   │
│  │   Tailwind CSS 4.0         Framer Motion       Shadcn/UI            │   │
│  │         │                        │                   │                │   │
│  │         └────────────────────────┴───────────────────┘                │   │
│  │                                  │                                    │   │
│  │                                  ▼                                    │   │
│  │                          Design Tokens (CSS Variables)                │   │
│  │                                                                       │   │
│  └──────────────────────────────────────────────────────────────────────┘   │
│                                    │                                         │
│                                    ▼                                         │
│  ┌──────────────────────────────────────────────────────────────────────┐   │
│  │                          STATE MANAGEMENT                             │   │
│  ├──────────────────────────────────────────────────────────────────────┤   │
│  │                                                                       │   │
│  │   Zustand (Client State) ◄─────────────► TanStack Query (Server)     │   │
│  │         │                                       │                     │   │
│  │         ▼                                       ▼                     │   │
│  │   Cart, UI State                      API Data, Cache                │   │
│  │                                                                       │   │
│  └──────────────────────────────────────────────────────────────────────┘   │
│                                    │                                         │
│                                    ▼                                         │
│  ┌──────────────────────────────────────────────────────────────────────┐   │
│  │                          APPLICATION LAYER                            │   │
│  ├──────────────────────────────────────────────────────────────────────┤   │
│  │                                                                       │   │
│  │   Next.js Route Handlers ──────► Server Actions                      │   │
│  │         │                              │                              │   │
│  │         ▼                              ▼                              │   │
│  │   Zod Validation              React Hook Form                        │   │
│  │         │                              │                              │   │
│  │         └──────────────────────────────┘                              │   │
│  │                          │                                            │   │
│  │                          ▼                                            │   │
│  │                   NextAuth.js 5.0                                     │   │
│  │                                                                       │   │
│  └──────────────────────────────────────────────────────────────────────┘   │
│                                    │                                         │
│                                    ▼                                         │
│  ┌──────────────────────────────────────────────────────────────────────┐   │
│  │                           DATA LAYER                                  │   │
│  ├──────────────────────────────────────────────────────────────────────┤   │
│  │                                                                       │   │
│  │   Prisma ORM ──────────────► PostgreSQL                              │   │
│  │         │                                                             │   │
│  │         ▼                                                             │   │
│  │   Generated Types ────────► Type-safe Queries                        │   │
│  │                                                                       │   │
│  └──────────────────────────────────────────────────────────────────────┘   │
│                                    │                                         │
│                                    ▼                                         │
│  ┌──────────────────────────────────────────────────────────────────────┐   │
│  │                       EXTERNAL SERVICES                               │   │
│  ├──────────────────────────────────────────────────────────────────────┤   │
│  │                                                                       │   │
│  │   Stripe ──────── Resend ──────── Vercel Blob ──────── Analytics     │   │
│  │  (Payments)      (Email)          (Images)            (Metrics)      │   │
│  │                                                                       │   │
│  └──────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
3.4 Development Environment
Required Software
Bash

# Node.js (via nvm recommended)
nvm install 20
nvm use 20

# Package manager
npm install -g npm@latest

# Database (local development)
# Option A: Docker
docker run --name atelier-postgres \
  -e POSTGRES_USER=atelier \
  -e POSTGRES_PASSWORD=atelier_dev \
  -e POSTGRES_DB=atelier_arome \
  -p 5432:5432 \
  -d postgres:16-alpine

# Option B: Supabase Local
npx supabase init
npx supabase start
Project Setup
Bash

# Clone repository
git clone https://github.com/atelier-arome/platform.git
cd platform

# Install dependencies
npm install

# Setup environment
cp .env.example .env.local
# Edit .env.local with your values

# Generate Prisma client
npx prisma generate

# Run migrations
npx prisma migrate dev

# Seed database
npx prisma db seed

# Start development server
npm run dev
Directory Structure
text

atelier-arome/
├── .github/
│   ├── workflows/
│   │   ├── ci.yml
│   │   ├── deploy-preview.yml
│   │   └── deploy-production.yml
│   └── PULL_REQUEST_TEMPLATE.md
│
├── prisma/
│   ├── schema.prisma
│   ├── migrations/
│   │   └── [timestamp]_init/
│   │       └── migration.sql
│   └── seed.ts
│
├── public/
│   ├── fonts/
│   │   ├── CormorantGaramond-Regular.woff2
│   │   ├── CormorantGaramond-SemiBold.woff2
│   │   ├── CrimsonPro-Regular.woff2
│   │   └── CrimsonPro-Italic.woff2
│   ├── images/
│   │   ├── essences/
│   │   ├── botanicals/
│   │   └── og/
│   └── favicon.svg
│
├── src/
│   ├── app/
│   │   ├── (auth)/
│   │   │   ├── sign-in/
│   │   │   │   └── page.tsx
│   │   │   ├── sign-up/
│   │   │   │   └── page.tsx
│   │   │   └── layout.tsx
│   │   │
│   │   ├── (main)/
│   │   │   ├── page.tsx                    # Home
│   │   │   ├── compendium/
│   │   │   │   ├── page.tsx                # Essence listing
│   │   │   │   └── [slug]/
│   │   │   │       └── page.tsx            # Essence detail
│   │   │   ├── alchemy/
│   │   │   │   └── page.tsx                # Process page
│   │   │   ├── manuscript/
│   │   │   │   └── page.tsx                # Testimonials
│   │   │   ├── atelier/
│   │   │   │   └── page.tsx                # About/visits
│   │   │   └── layout.tsx
│   │   │
│   │   ├── (checkout)/
│   │   │   ├── vial/
│   │   │   │   └── page.tsx                # Cart
│   │   │   ├── dispatch/
│   │   │   │   └── page.tsx                # Checkout
│   │   │   ├── confirmation/
│   │   │   │   └── [orderId]/
│   │   │   │       └── page.tsx
│   │   │   └── layout.tsx
│   │   │
│   │   ├── (patron)/
│   │   │   ├── profile/
│   │   │   │   └── page.tsx
│   │   │   ├── dispatches/
│   │   │   │   ├── page.tsx                # Order history
│   │   │   │   └── [orderId]/
│   │   │   │       └── page.tsx            # Order detail
│   │   │   └── layout.tsx
│   │   │
│   │   ├── (admin)/
│   │   │   ├── dashboard/
│   │   │   │   └── page.tsx
│   │   │   ├── essences/
│   │   │   │   ├── page.tsx
│   │   │   │   ├── new/
│   │   │   │   │   └── page.tsx
│   │   │   │   └── [id]/
│   │   │   │       └── edit/
│   │   │   │           └── page.tsx
│   │   │   ├── dispatches/
│   │   │   │   ├── page.tsx
│   │   │   │   └── [id]/
│   │   │   │       └── page.tsx
│   │   │   ├── manuscript/
│   │   │   │   ├── page.tsx
│   │   │   │   └── new/
│   │   │   │       └── page.tsx
│   │   │   ├── patrons/
│   │   │   │   └── page.tsx
│   │   │   └── layout.tsx
│   │   │
│   │   ├── api/
│   │   │   ├── auth/
│   │   │   │   └── [...nextauth]/
│   │   │   │       └── route.ts
│   │   │   ├── essences/
│   │   │   │   ├── route.ts
│   │   │   │   └── [id]/
│   │   │   │       └── route.ts
│   │   │   ├── cart/
│   │   │   │   └── route.ts
│   │   │   ├── orders/
│   │   │   │   ├── route.ts
│   │   │   │   └── [id]/
│   │   │   │       └── route.ts
│   │   │   ├── stripe/
│   │   │   │   ├── checkout/
│   │   │   │   │   └── route.ts
│   │   │   │   └── webhook/
│   │   │   │       └── route.ts
│   │   │   ├── correspondence/
│   │   │   │   └── route.ts
│   │   │   └── uploads/
│   │   │       └── route.ts
│   │   │
│   │   ├── layout.tsx
│   │   ├── globals.css
│   │   ├── not-found.tsx
│   │   └── error.tsx
│   │
│   ├── components/
│   │   ├── ui/                             # Shadcn/UI components
│   │   │   ├── button.tsx
│   │   │   ├── dialog.tsx
│   │   │   ├── dropdown-menu.tsx
│   │   │   ├── input.tsx
│   │   │   ├── label.tsx
│   │   │   ├── select.tsx
│   │   │   ├── toast.tsx
│   │   │   ├── toaster.tsx
│   │   │   └── tooltip.tsx
│   │   │
│   │   ├── layout/
│   │   │   ├── header.tsx
│   │   │   ├── footer.tsx
│   │   │   ├── mobile-nav.tsx
│   │   │   ├── atelier-banner.tsx
│   │   │   └── skip-link.tsx
│   │   │
│   │   ├── home/
│   │   │   ├── hero-section.tsx
│   │   │   ├── illuminated-initial.tsx
│   │   │   ├── vessel-illustration.tsx
│   │   │   ├── botanical-specimens.tsx
│   │   │   └── scroll-indicator.tsx
│   │   │
│   │   ├── compendium/
│   │   │   ├── essence-card.tsx
│   │   │   ├── essence-grid.tsx
│   │   │   ├── essence-filters.tsx
│   │   │   ├── essence-sort.tsx
│   │   │   └── essence-detail.tsx
│   │   │
│   │   ├── alchemy/
│   │   │   ├── alchemy-step.tsx
│   │   │   ├── process-timeline.tsx
│   │   │   └── apparatus-display.tsx
│   │   │
│   │   ├── manuscript/
│   │   │   ├── testimonial-entry.tsx
│   │   │   ├── testimonial-carousel.tsx
│   │   │   └── manuscript-pagination.tsx
│   │   │
│   │   ├── cart/
│   │   │   ├── cart-drawer.tsx
│   │   │   ├── cart-item.tsx
│   │   │   ├── cart-summary.tsx
│   │   │   └── add-to-cart-button.tsx
│   │   │
│   │   ├── checkout/
│   │   │   ├── checkout-form.tsx
│   │   │   ├── shipping-form.tsx
│   │   │   ├── payment-form.tsx
│   │   │   └── order-summary.tsx
│   │   │
│   │   ├── correspondence/
│   │   │   ├── newsletter-form.tsx
│   │   │   └── envelope-illustration.tsx
│   │   │
│   │   ├── admin/
│   │   │   ├── admin-sidebar.tsx
│   │   │   ├── data-table.tsx
│   │   │   ├── essence-form.tsx
│   │   │   ├── order-status-badge.tsx
│   │   │   └── stats-card.tsx
│   │   │
│   │   └── shared/
│   │       ├── section-header.tsx
│   │       ├── decorative-border.tsx
│   │       ├── gold-leaf-overlay.tsx
│   │       ├── parchment-texture.tsx
│   │       ├── loading-spinner.tsx
│   │       └── error-boundary.tsx
│   │
│   ├── lib/
│   │   ├── prisma.ts                       # Prisma client singleton
│   │   ├── auth.ts                         # NextAuth configuration
│   │   ├── stripe.ts                       # Stripe client
│   │   ├── resend.ts                       # Email client
│   │   ├── utils.ts                        # Utility functions
│   │   └── constants.ts                    # Application constants
│   │
│   ├── hooks/
│   │   ├── use-cart.ts
│   │   ├── use-essences.ts
│   │   ├── use-orders.ts
│   │   ├── use-media-query.ts
│   │   ├── use-reduced-motion.ts
│   │   └── use-toast.ts
│   │
│   ├── stores/
│   │   ├── cart-store.ts
│   │   └── ui-store.ts
│   │
│   ├── actions/
│   │   ├── essence-actions.ts
│   │   ├── order-actions.ts
│   │   ├── auth-actions.ts
│   │   └── correspondence-actions.ts
│   │
│   ├── schemas/
│   │   ├── essence-schema.ts
│   │   ├── order-schema.ts
│   │   ├── auth-schema.ts
│   │   └── correspondence-schema.ts
│   │
│   ├── types/
│   │   ├── essence.ts
│   │   ├── order.ts
│   │   ├── user.ts
│   │   └── index.ts
│   │
│   ├── emails/
│   │   ├── order-confirmation.tsx
│   │   ├── shipping-notification.tsx
│   │   ├── welcome-email.tsx
│   │   └── newsletter.tsx
│   │
│   └── styles/
│       ├── design-tokens.css
│       └── manuscript-theme.css
│
├── tests/
│   ├── unit/
│   │   ├── lib/
│   │   └── hooks/
│   ├── integration/
│   │   ├── api/
│   │   └── actions/
│   └── e2e/
│       ├── checkout.spec.ts
│       ├── auth.spec.ts
│       └── admin.spec.ts
│
├── .env.example
├── .env.local                              # Not committed
├── .eslintrc.json
├── .gitignore
├── .prettierrc
├── components.json                         # Shadcn/UI config
├── next.config.js
├── package.json
├── postcss.config.js
├── tailwind.config.ts
├── tsconfig.json
├── vitest.config.ts
└── README.md
4. System Architecture
4.1 High-Level Architecture
text

┌─────────────────────────────────────────────────────────────────────────────┐
│                        HIGH-LEVEL SYSTEM ARCHITECTURE                        │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│                           ┌─────────────────┐                               │
│                           │     CLIENT      │                               │
│                           │    (Browser)    │                               │
│                           └────────┬────────┘                               │
│                                    │                                         │
│                                    │ HTTPS                                   │
│                                    ▼                                         │
│  ┌──────────────────────────────────────────────────────────────────────┐   │
│  │                           CDN / EDGE                                  │   │
│  │                        (Vercel Edge Network)                          │   │
│  │  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐                   │   │
│  │  │   Static    │  │   Image     │  │    Edge     │                   │   │
│  │  │   Assets    │  │ Optimization│  │  Functions  │                   │   │
│  │  └─────────────┘  └─────────────┘  └─────────────┘                   │   │
│  └──────────────────────────────────────────────────────────────────────┘   │
│                                    │                                         │
│                                    ▼                                         │
│  ┌──────────────────────────────────────────────────────────────────────┐   │
│  │                       APPLICATION SERVER                              │   │
│  │                         (Next.js 14+)                                 │   │
│  │                                                                       │   │
│  │   ┌─────────────────────────────────────────────────────────────┐    │   │
│  │   │                    NEXT.JS APP ROUTER                        │    │   │
│  │   ├─────────────────────────────────────────────────────────────┤    │   │
│  │   │                                                              │    │   │
│  │   │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐       │    │   │
│  │   │  │    React     │  │    Server    │  │    Route     │       │    │   │
│  │   │  │  Components  │  │   Actions    │  │   Handlers   │       │    │   │
│  │   │  │    (RSC)     │  │              │  │    (API)     │       │    │   │
│  │   │  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘       │    │   │
│  │   │         │                 │                 │                │    │   │
│  │   │         └─────────────────┼─────────────────┘                │    │   │
│  │   │                           │                                  │    │   │
│  │   │                           ▼                                  │    │   │
│  │   │              ┌─────────────────────────┐                     │    │   │
│  │   │              │     SERVICE LAYER       │                     │    │   │
│  │   │              │  (Business Logic)       │                     │    │   │
│  │   │              └───────────┬─────────────┘                     │    │   │
│  │   │                          │                                   │    │   │
│  │   │                          ▼                                   │    │   │
│  │   │              ┌─────────────────────────┐                     │    │   │
│  │   │              │   DATA ACCESS LAYER     │                     │    │   │
│  │   │              │      (Prisma ORM)       │                     │    │   │
│  │   │              └───────────┬─────────────┘                     │    │   │
│  │   │                          │                                   │    │   │
│  │   └──────────────────────────┼───────────────────────────────────┘    │   │
│  │                              │                                        │   │
│  └──────────────────────────────┼────────────────────────────────────────┘   │
│                                 │                                            │
│         ┌───────────────────────┼───────────────────────┐                   │
│         │                       │                       │                   │
│         ▼                       ▼                       ▼                   │
│  ┌─────────────┐         ┌─────────────┐         ┌─────────────┐           │
│  │  PostgreSQL │         │    Stripe   │         │   Resend    │           │
│  │  (Database) │         │  (Payments) │         │   (Email)   │           │
│  └─────────────┘         └─────────────┘         └─────────────┘           │
│                                                                              │
│         ┌───────────────────────┬───────────────────────┐                   │
│         ▼                       ▼                       ▼                   │
│  ┌─────────────┐         ┌─────────────┐         ┌─────────────┐           │
│  │ Vercel Blob │         │  Analytics  │         │   Sentry    │           │
│  │  (Storage)  │         │             │         │  (Errors)   │           │
│  └─────────────┘         └─────────────┘         └─────────────┘           │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
4.2 Component Architecture
text

┌─────────────────────────────────────────────────────────────────────────────┐
│                         COMPONENT ARCHITECTURE                               │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  ┌──────────────────────────────────────────────────────────────────────┐   │
│  │                         PAGE COMPONENTS                               │   │
│  │                    (app/[route]/page.tsx)                             │   │
│  │                                                                       │   │
│  │  • Server Components by default                                       │   │
│  │  • Data fetching at component level                                   │   │
│  │  • Metadata generation                                                │   │
│  │  • Layout composition                                                 │   │
│  └──────────────────────────────────────────────────────────────────────┘   │
│                                    │                                         │
│                    ┌───────────────┼───────────────┐                        │
│                    ▼               ▼               ▼                        │
│  ┌─────────────────────┐ ┌─────────────────────┐ ┌─────────────────────┐   │
│  │  LAYOUT COMPONENTS  │ │ FEATURE COMPONENTS  │ │  SHARED COMPONENTS  │   │
│  │  (components/layout)│ │  (components/*)     │ │ (components/shared) │   │
│  ├─────────────────────┤ ├─────────────────────┤ ├─────────────────────┤   │
│  │                     │ │                     │ │                     │   │
│  │  • Header           │ │  • EssenceCard      │ │  • SectionHeader    │   │
│  │  • Footer           │ │  • CartDrawer       │ │  • DecorativeBorder │   │
│  │  • MobileNav        │ │  • CheckoutForm     │ │  • GoldLeafOverlay  │   │
│  │  • AtelierBanner    │ │  • TestimonialEntry │ │  • LoadingSpinner   │   │
│  │  • SkipLink         │ │  • NewsletterForm   │ │  • ErrorBoundary    │   │
│  │                     │ │                     │ │                     │   │
│  └─────────────────────┘ └─────────────────────┘ └─────────────────────┘   │
│                                    │                                         │
│                                    ▼                                         │
│  ┌──────────────────────────────────────────────────────────────────────┐   │
│  │                         UI COMPONENTS                                 │   │
│  │                     (components/ui - Shadcn)                          │   │
│  ├──────────────────────────────────────────────────────────────────────┤   │
│  │                                                                       │   │
│  │   ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐        │   │
│  │   │ Button  │ │ Dialog  │ │  Input  │ │ Select  │ │  Toast  │        │   │
│  │   └─────────┘ └─────────┘ └─────────┘ └─────────┘ └─────────┘        │   │
│  │                                                                       │   │
│  │   ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐        │   │
│  │   │Dropdown │ │ Tooltip │ │Checkbox │ │  Label  │ │  Card   │        │   │
│  │   └─────────┘ └─────────┘ └─────────┘ └─────────┘ └─────────┘        │   │
│  │                                                                       │   │
│  │   Based on Radix UI Primitives - Accessible by default               │   │
│  │   Styled with Tailwind CSS + Custom manuscript theme                 │   │
│  │                                                                       │   │
│  └──────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
4.3 Data Flow Diagrams
4.3.1 Add to Cart Flow
text

┌─────────────────────────────────────────────────────────────────────────────┐
│                          ADD TO CART DATA FLOW                               │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   ┌─────────────┐                                                           │
│   │   Patron    │                                                           │
│   │   clicks    │                                                           │
│   │ "Add to     │                                                           │
│   │   Vial"     │                                                           │
│   └──────┬──────┘                                                           │
│          │                                                                   │
│          ▼                                                                   │
│   ┌─────────────────────────────────────────────────────────┐               │
│   │              AddToCartButton (Client Component)          │               │
│   │                                                          │               │
│   │  onClick() {                                             │               │
│   │    1. Optimistic UI update (local state)                 │               │
│   │    2. Call addToCart action                              │               │
│   │    3. Show toast notification                            │               │
│   │  }                                                       │               │
│   └──────────────────────────┬──────────────────────────────┘               │
│                              │                                               │
│                              ▼                                               │
│   ┌─────────────────────────────────────────────────────────┐               │
│   │                    Zustand Cart Store                    │               │
│   │                                                          │               │
│   │  • Immediate local state update                          │               │
│   │  • Persist to localStorage                               │               │
│   │  • Sync with server (if authenticated)                   │               │
│   └──────────────────────────┬──────────────────────────────┘               │
│                              │                                               │
│                              │ (If authenticated)                            │
│                              ▼                                               │
│   ┌─────────────────────────────────────────────────────────┐               │
│   │               Server Action: addToCart                   │               │
│   │                                                          │               │
│   │  async function addToCart(essenceId, quantity) {         │               │
│   │    1. Validate session                                   │               │
│   │    2. Check essence availability                         │               │
│   │    3. Update/create cart in database                     │               │
│   │    4. Return updated cart                                │               │
│   │  }                                                       │               │
│   └──────────────────────────┬──────────────────────────────┘               │
│                              │                                               │
│                              ▼                                               │
│   ┌─────────────────────────────────────────────────────────┐               │
│   │                      Prisma ORM                          │               │
│   │                                                          │               │
│   │  prisma.cartItem.upsert({                                │               │
│   │    where: { cartId_essenceId: { cartId, essenceId } },   │               │
│   │    update: { quantity: { increment: quantity } },        │               │
│   │    create: { cartId, essenceId, quantity }               │               │
│   │  })                                                      │               │
│   └──────────────────────────┬──────────────────────────────┘               │
│                              │                                               │
│                              ▼                                               │
│   ┌─────────────────────────────────────────────────────────┐               │
│   │                     PostgreSQL                           │               │
│   │                                                          │               │
│   │  cart_items table updated                                │               │
│   └─────────────────────────────────────────────────────────┘               │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
4.3.2 Checkout Flow
text

┌─────────────────────────────────────────────────────────────────────────────┐
│                           CHECKOUT DATA FLOW                                 │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                         CHECKOUT PAGE                                │   │
│   │                    (/dispatch/page.tsx)                              │   │
│   └───────────────────────────────┬─────────────────────────────────────┘   │
│                                   │                                          │
│           ┌───────────────────────┼───────────────────────┐                 │
│           ▼                       ▼                       ▼                 │
│   ┌───────────────┐       ┌───────────────┐       ┌───────────────┐        │
│   │ ShippingForm  │       │ PaymentForm   │       │ OrderSummary  │        │
│   │               │       │   (Stripe)    │       │               │        │
│   └───────┬───────┘       └───────┬───────┘       └───────────────┘        │
│           │                       │                                         │
│           └───────────────────────┘                                         │
│                       │                                                      │
│                       ▼                                                      │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                  Submit Checkout Handler                             │   │
│   │                                                                      │   │
│   │  1. Validate all form data (Zod schema)                              │   │
│   │  2. Create Stripe PaymentIntent                                      │   │
│   │  3. Confirm payment with Stripe.js                                   │   │
│   │  4. On success: Create order via server action                       │   │
│   │  5. Redirect to confirmation page                                    │   │
│   └───────────────────────────────┬─────────────────────────────────────┘   │
│                                   │                                          │
│           ┌───────────────────────┴───────────────────────┐                 │
│           ▼                                               ▼                 │
│   ┌───────────────────────┐               ┌───────────────────────┐        │
│   │     Stripe API        │               │   Server Action:      │        │
│   │                       │               │   createOrder         │        │
│   │ • PaymentIntent       │               │                       │        │
│   │ • Confirmation        │               │ • Validate payment    │        │
│   │ • Webhook events      │               │ • Create Order        │        │
│   └───────────────────────┘               │ • Create OrderItems   │        │
│                                           │ • Clear cart          │        │
│                                           │ • Send confirmation   │        │
│                                           └───────────┬───────────┘        │
│                                                       │                     │
│                                                       ▼                     │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                         DATABASE TRANSACTION                         │   │
│   │                                                                      │   │
│   │  prisma.$transaction([                                               │   │
│   │    prisma.order.create({ ... }),                                     │   │
│   │    prisma.orderItem.createMany({ ... }),                             │   │
│   │    prisma.cartItem.deleteMany({ where: { cartId } }),                │   │
│   │    prisma.essence.updateMany({ decrement stock })                    │   │
│   │  ])                                                                  │   │
│   └───────────────────────────────┬─────────────────────────────────────┘   │
│                                   │                                          │
│                                   ▼                                          │
│   ┌─────────────────────────────────────────────────────────────────────┐   │
│   │                      POST-ORDER ACTIONS                              │   │
│   │                                                                      │   │
│   │  • Send order confirmation email (Resend)                            │   │
│   │  • Update analytics                                                  │   │
│   │  • Trigger inventory alerts if low stock                             │   │
│   └─────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
4.4 Security Architecture
text

┌─────────────────────────────────────────────────────────────────────────────┐
│                         SECURITY ARCHITECTURE                                │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  ┌──────────────────────────────────────────────────────────────────────┐   │
│  │                      TRANSPORT SECURITY                               │   │
│  ├──────────────────────────────────────────────────────────────────────┤   │
│  │  • TLS 1.3 enforced (Vercel default)                                  │   │
│  │  • HSTS headers enabled                                               │   │
│  │  • Certificate auto-renewal                                           │   │
│  └──────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
│  ┌──────────────────────────────────────────────────────────────────────┐   │
│  │                      AUTHENTICATION                                   │   │
│  ├──────────────────────────────────────────────────────────────────────┤   │
│  │                                                                       │   │
│  │  NextAuth.js 5.0 (Auth.js)                                            │   │
│  │                                                                       │   │
│  │  Providers:                                                           │   │
│  │    • Email (Magic Link) - Primary                                     │   │
│  │    • Google OAuth - Optional                                          │   │
│  │    • Credentials - Admin only                                         │   │
│  │                                                                       │   │
│  │  Session Strategy: JWT                                                │   │
│  │  Token Lifetime: 30 days                                              │   │
│  │  Refresh: Sliding window                                              │   │
│  │                                                                       │   │
│  └──────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
│  ┌──────────────────────────────────────────────────────────────────────┐   │
│  │                      AUTHORIZATION (RBAC)                             │   │
│  ├──────────────────────────────────────────────────────────────────────┤   │
│  │                                                                       │   │
│  │  Roles:                                                               │   │
│  │    ┌─────────────┬──────────────────────────────────────────────┐    │   │
│  │    │    ROLE     │              PERMISSIONS                      │    │   │
│  │    ├─────────────┼──────────────────────────────────────────────┤    │   │
│  │    │ GUEST       │ Read public content, Add to cart, Checkout   │    │   │
│  │    │ PATRON      │ All guest + Profile, Order history, Reviews  │    │   │
│  │    │ ALCHEMIST   │ All patron + Admin dashboard, CRUD operations│    │   │
│  │    │ MASTER      │ All alchemist + User management, Settings    │    │   │
│  │    └─────────────┴──────────────────────────────────────────────┘    │   │
│  │                                                                       │   │
│  │  Implementation:                                                      │   │
│  │    • Middleware-based route protection                                │   │
│  │    • Server-side permission checks in actions                         │   │
│  │    • Client-side conditional rendering                                │   │
│  │                                                                       │   │
│  └──────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
│  ┌──────────────────────────────────────────────────────────────────────┐   │
│  │                      INPUT VALIDATION                                 │   │
│  ├──────────────────────────────────────────────────────────────────────┤   │
│  │                                                                       │   │
│  │  • Zod schemas for all user inputs                                    │   │
│  │  • Server-side validation in all actions                              │   │
│  │  • Prisma parameterized queries (SQL injection prevention)            │   │
│  │  • Content Security Policy headers                                    │   │
│  │  • XSS prevention via React's default escaping                        │   │
│  │                                                                       │   │
│  └──────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
│  ┌──────────────────────────────────────────────────────────────────────┐   │
│  │                      DATA PROTECTION                                  │   │
│  ├──────────────────────────────────────────────────────────────────────┤   │
│  │                                                                       │   │
│  │  • Passwords: bcrypt hashing (via NextAuth)                           │   │
│  │  • PII: Encrypted at rest (database-level)                            │   │
│  │  • Payment data: Never stored (Stripe handles)                        │   │
│  │  • Backups: Encrypted, 30-day retention                               │   │
│  │  • GDPR: Data export/deletion endpoints                               │   │
│  │                                                                       │   │
│  └──────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
│  ┌──────────────────────────────────────────────────────────────────────┐   │
│  │                      RATE LIMITING                                    │   │
│  ├──────────────────────────────────────────────────────────────────────┤   │
│  │                                                                       │   │
│  │  Endpoint               │ Limit        │ Window                       │   │
│  │  ─────────────────────────────────────────────────────────────────   │   │
│  │  /api/auth/*            │ 10 requests  │ 1 minute                     │   │
│  │  /api/checkout          │ 5 requests   │ 1 minute                     │   │
│  │  /api/correspondence    │ 3 requests   │ 1 minute                     │   │
│  │  /api/* (general)       │ 100 requests │ 1 minute                     │   │
│  │                                                                       │   │
│  │  Implementation: Vercel Edge Middleware + Upstash Redis               │   │
│  │                                                                       │   │
│  └──────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
5. Database Design
5.1 Entity-Relationship Diagram
text

┌─────────────────────────────────────────────────────────────────────────────┐
│                      ENTITY-RELATIONSHIP DIAGRAM                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  ┌─────────────────┐       ┌─────────────────┐       ┌─────────────────┐   │
│  │     Account     │       │     Session     │       │VerificationToken│   │
│  │  (NextAuth)     │       │   (NextAuth)    │       │   (NextAuth)    │   │
│  └────────┬────────┘       └────────┬────────┘       └─────────────────┘   │
│           │                         │                                        │
│           │ N:1                     │ N:1                                    │
│           ▼                         ▼                                        │
│  ┌─────────────────────────────────────────────────────────────────────┐    │
│  │                              USER                                    │    │
│  │  ┌──────────────────────────────────────────────────────────────┐   │    │
│  │  │ id            │ String    │ @id @default(cuid())             │   │    │
│  │  │ email         │ String    │ @unique                          │   │    │
│  │  │ name          │ String?   │                                  │   │    │
│  │  │ emailVerified │ DateTime? │                                  │   │    │
│  │  │ image         │ String?   │                                  │   │    │
│  │  │ role          │ Role      │ @default(PATRON)                 │   │    │
│  │  │ createdAt     │ DateTime  │ @default(now())                  │   │    │
│  │  │ updatedAt     │ DateTime  │ @updatedAt                       │   │    │
│  │  └──────────────────────────────────────────────────────────────┘   │    │
│  └───────────────────────────────┬─────────────────────────────────────┘    │
│           │                      │                      │                    │
│           │ 1:N                  │ 1:1                  │ 1:N                │
│           ▼                      ▼                      ▼                    │
│  ┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐          │
│  │     Address     │    │      Cart       │    │      Order      │          │
│  │                 │    │                 │    │                 │          │
│  │ id              │    │ id              │    │ id              │          │
│  │ userId          │◄───│ userId          │    │ userId          │          │
│  │ type (SHIPPING/ │    │ createdAt       │    │ orderNumber     │          │
│  │  BILLING)       │    │ updatedAt       │    │ status          │          │
│  │ firstName       │    │                 │    │ subtotal        │          │
│  │ lastName        │    └────────┬────────┘    │ shipping        │          │
│  │ line1           │             │             │ tax             │          │
│  │ line2           │             │ 1:N         │ total           │          │
│  │ city            │             ▼             │ shippingAddress │          │
│  │ state           │    ┌─────────────────┐    │ billingAddress  │          │
│  │ postalCode      │    │    CartItem     │    │ stripePaymentId │          │
│  │ country         │    │                 │    │ createdAt       │          │
│  │ phone           │    │ id              │    │ updatedAt       │          │
│  │ isDefault       │    │ cartId          │    │                 │          │
│  └─────────────────┘    │ essenceId ──────┼────┤─────────────────┘          │
│                         │ quantity        │    │                             │
│                         │ createdAt       │    │ 1:N                         │
│                         └─────────────────┘    ▼                             │
│                                         ┌─────────────────┐                  │
│                                         │   OrderItem     │                  │
│                                         │                 │                  │
│                                         │ id              │                  │
│                                         │ orderId         │                  │
│                                         │ essenceId ──────┼───┐              │
│                                         │ quantity        │   │              │
│                                         │ priceAtTime     │   │              │
│                                         │ essenceName     │   │              │
│                                         └─────────────────┘   │              │
│                                                               │              │
│  ┌────────────────────────────────────────────────────────────┘              │
│  │                                                                           │
│  ▼                                                                           │
│  ┌─────────────────────────────────────────────────────────────────────┐    │
│  │                            ESSENCE                                   │    │
│  │  ┌──────────────────────────────────────────────────────────────┐   │    │
│  │  │ id            │ String    │ @id @default(cuid())             │   │    │
│  │  │ slug          │ String    │ @unique                          │   │    │
│  │  │ folioNumber   │ String    │ (I, II, III, etc.)               │   │    │
│  │  │ latinName     │ String    │                                  │   │    │
│  │  │ commonName    │ String    │                                  │   │    │
│  │  │ description   │ String    │ @db.Text                         │   │    │
│  │  │ price         │ Decimal   │ @db.Decimal(10, 2)               │   │    │
│  │  │ comparePrice  │ Decimal?  │ @db.Decimal(10, 2)               │   │    │
│  │  │ stock         │ Int       │ @default(0)                      │   │    │
│  │  │ humourId      │ String    │ FK → Humour                      │   │    │
│  │  │ rarityId      │ String    │ FK → Rarity                      │   │    │
│  │  │ seasonId      │ String    │ FK → Season                      │   │    │
│  │  │ extraction    │ String    │                                  │   │    │
│  │  │ notes         │ String[]  │                                  │   │    │
│  │  │ featured      │ Boolean   │ @default(false)                  │   │    │
│  │  │ published     │ Boolean   │ @default(false)                  │   │    │
│  │  │ images        │ Json      │ Array of image objects           │   │    │
│  │  │ createdAt     │ DateTime  │ @default(now())                  │   │    │
│  │  │ updatedAt     │ DateTime  │ @updatedAt                       │   │    │
│  │  └──────────────────────────────────────────────────────────────┘   │    │
│  └───────────────────────────────┬─────────────────────────────────────┘    │
│           │                      │                      │                    │
│           │ N:1                  │ N:1                  │ N:1                │
│           ▼                      ▼                      ▼                    │
│  ┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐          │
│  │     Humour      │    │     Rarity      │    │     Season      │          │
│  │                 │    │                 │    │                 │          │
│  │ id              │    │ id              │    │ id              │          │
│  │ name            │    │ name            │    │ name            │          │
│  │ slug            │    │ slug            │    │ slug            │          │
│  │ symbol          │    │ sortOrder       │    │ sortOrder       │          │
│  │ description     │    │                 │    │                 │          │
│  │ color           │    └─────────────────┘    └─────────────────┘          │
│  └─────────────────┘                                                         │
│                                                                              │
│  ┌─────────────────────────────────────────────────────────────────────┐    │
│  │                         TESTIMONIAL                                  │    │
│  │  ┌──────────────────────────────────────────────────────────────┐   │    │
│  │  │ id            │ String    │ @id @default(cuid())             │   │    │
│  │  │ authorName    │ String    │                                  │   │    │
│  │  │ authorTitle   │ String    │                                  │   │    │
│  │  │ authorImage   │ String?   │                                  │   │    │
│  │  │ quote         │ String    │ @db.Text                         │   │    │
│  │  │ essenceId     │ String?   │ FK → Essence                     │   │    │
│  │  │ verified      │ Boolean   │ @default(false)                  │   │    │
│  │  │ featured      │ Boolean   │ @default(false)                  │   │    │
│  │  │ folioEntry    │ String?   │ "Folio VII, Entry 12"            │   │    │
│  │  │ published     │ Boolean   │ @default(false)                  │   │    │
│  │  │ createdAt     │ DateTime  │ @default(now())                  │   │    │
│  │  │ updatedAt     │ DateTime  │ @updatedAt                       │   │    │
│  │  └──────────────────────────────────────────────────────────────┘   │    │
│  └─────────────────────────────────────────────────────────────────────┘    │
│                                                                              │
│  ┌─────────────────────────────────────────────────────────────────────┐    │
│  │                         SUBSCRIPTION                                 │    │
│  │  ┌──────────────────────────────────────────────────────────────┐   │    │
│  │  │ id            │ String    │ @id @default(cuid())             │   │    │
│  │  │ email         │ String    │ @unique                          │   │    │
│  │  │ name          │ String?   │                                  │   │    │
│  │  │ status        │ Status    │ @default(ACTIVE)                 │   │    │
│  │  │ subscribedAt  │ DateTime  │ @default(now())                  │   │    │
│  │  │ unsubscribedAt│ DateTime? │                                  │   │    │
│  │  │ source        │ String?   │ "website", "checkout", etc.      │   │    │
│  │  └──────────────────────────────────────────────────────────────┘   │    │
│  └─────────────────────────────────────────────────────────────────────┘    │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
5.2 Schema Definitions (Prisma)
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

enum Role {
  GUEST
  PATRON
  ALCHEMIST
  MASTER
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

enum SubscriptionStatus {
  ACTIVE
  UNSUBSCRIBED
  BOUNCED
}

// ============================================
// AUTHENTICATION (NextAuth.js)
// ============================================

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
}

model Session {
  id           String   @id @default(cuid())
  sessionToken String   @unique
  userId       String
  expires      DateTime
  user         User     @relation(fields: [userId], references: [id], onDelete: Cascade)

  @@index([userId])
}

model VerificationToken {
  identifier String
  token      String   @unique
  expires    DateTime

  @@unique([identifier, token])
}

// ============================================
// USER & PROFILE
// ============================================

model User {
  id            String    @id @default(cuid())
  email         String    @unique
  emailVerified DateTime?
  name          String?
  image         String?
  role          Role      @default(PATRON)
  
  // Timestamps
  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt
  
  // Relations
  accounts  Account[]
  sessions  Session[]
  addresses Address[]
  cart      Cart?
  orders    Order[]
  
  @@index([email])
  @@index([role])
}

model Address {
  id         String      @id @default(cuid())
  userId     String
  type       AddressType
  firstName  String
  lastName   String
  company    String?
  line1      String
  line2      String?
  city       String
  state      String
  postalCode String
  country    String      @default("US")
  phone      String?
  isDefault  Boolean     @default(false)
  
  // Timestamps
  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt
  
  // Relations
  user User @relation(fields: [userId], references: [id], onDelete: Cascade)
  
  @@index([userId])
  @@index([userId, type])
}

// ============================================
// CATALOG
// ============================================

model Humour {
  id          String @id @default(cuid())
  name        String @unique // "Calming", "Uplifting", "Grounding", "Clarifying"
  slug        String @unique
  symbol      String // ☾, ☀, ♁, ☁
  description String @db.Text
  color       String // CSS color value
  
  // Relations
  essences Essence[]
}

model Rarity {
  id        String @id @default(cuid())
  name      String @unique // "Common", "Rare", "Limited"
  slug      String @unique
  sortOrder Int    @default(0)
  
  // Relations
  essences Essence[]
}

model Season {
  id        String @id @default(cuid())
  name      String @unique // "Spring", "Summer", "Autumn", "Winter"
  slug      String @unique
  sortOrder Int    @default(0)
  
  // Relations
  essences Essence[]
}

model Essence {
  id           String   @id @default(cuid())
  slug         String   @unique
  folioNumber  String   // Roman numerals: I, II, III, etc.
  latinName    String
  commonName   String
  description  String   @db.Text
  
  // Pricing
  price        Decimal  @db.Decimal(10, 2)
  comparePrice Decimal? @db.Decimal(10, 2)
  
  // Inventory
  stock        Int      @default(0)
  lowStockThreshold Int @default(5)
  
  // Categorization
  humourId     String
  rarityId     String
  seasonId     String
  
  // Details
  extraction   String   // "Steam Distillation", "Cold Press", etc.
  notes        String[] // ["Floral", "Herbaceous", "Sweet"]
  
  // Media
  images       Json     // Array of { url, alt, isPrimary }
  
  // Flags
  featured     Boolean  @default(false)
  published    Boolean  @default(false)
  
  // SEO
  metaTitle       String?
  metaDescription String?
  
  // Timestamps
  createdAt    DateTime @default(now())
  updatedAt    DateTime @updatedAt
  
  // Relations
  humour       Humour       @relation(fields: [humourId], references: [id])
  rarity       Rarity       @relation(fields: [rarityId], references: [id])
  season       Season       @relation(fields: [seasonId], references: [id])
  cartItems    CartItem[]
  orderItems   OrderItem[]
  testimonials Testimonial[]
  
  @@index([slug])
  @@index([humourId])
  @@index([rarityId])
  @@index([seasonId])
  @@index([published])
  @@index([featured])
}

// ============================================
// CART
// ============================================

model Cart {
  id        String   @id @default(cuid())
  userId    String   @unique
  
  // Timestamps
  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt
  
  // Relations
  user  User       @relation(fields: [userId], references: [id], onDelete: Cascade)
  items CartItem[]
}

model CartItem {
  id        String @id @default(cuid())
  cartId    String
  essenceId String
  quantity  Int    @default(1)
  
  // Timestamps
  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt
  
  // Relations
  cart    Cart    @relation(fields: [cartId], references: [id], onDelete: Cascade)
  essence Essence @relation(fields: [essenceId], references: [id], onDelete: Cascade)
  
  @@unique([cartId, essenceId])
  @@index([cartId])
  @@index([essenceId])
}

// ============================================
// ORDERS
// ============================================

model Order {
  id              String      @id @default(cuid())
  orderNumber     String      @unique // AA-2024-00001
  userId          String?     // Nullable for guest checkout
  
  // Status
  status          OrderStatus @default(PENDING)
  
  // Pricing
  subtotal        Decimal     @db.Decimal(10, 2)
  shippingAmount  Decimal     @db.Decimal(10, 2) @default(0)
  taxAmount       Decimal     @db.Decimal(10, 2) @default(0)
  discountAmount  Decimal     @db.Decimal(10, 2) @default(0)
  total           Decimal     @db.Decimal(10, 2)
  
  // Customer Info (for guest checkout)
  customerEmail   String
  customerName    String
  customerPhone   String?
  
  // Addresses (stored as JSON for historical accuracy)
  shippingAddress Json
  billingAddress  Json
  
  // Payment
  stripePaymentIntentId String? @unique
  stripeChargeId        String?
  
  // Shipping
  shippingMethod  String?
  trackingNumber  String?
  shippedAt       DateTime?
  deliveredAt     DateTime?
  
  // Notes
  customerNotes   String?   @db.Text
  internalNotes   String?   @db.Text
  
  // Timestamps
  createdAt       DateTime  @default(now())
  updatedAt       DateTime  @updatedAt
  
  // Relations
  user            User?      @relation(fields: [userId], references: [id], onDelete: SetNull)
  items           OrderItem[]
  
  @@index([orderNumber])
  @@index([userId])
  @@index([status])
  @@index([customerEmail])
  @@index([createdAt])
}

model OrderItem {
  id            String  @id @default(cuid())
  orderId       String
  essenceId     String?
  
  // Snapshot at time of order (prices may change)
  essenceName   String
  essenceSlug   String
  quantity      Int
  priceAtTime   Decimal @db.Decimal(10, 2)
  
  // Relations
  order   Order    @relation(fields: [orderId], references: [id], onDelete: Cascade)
  essence Essence? 
