# AI CFO - Smart Financial Intelligence Platform

## Overview

AI CFO is a modern SaaS financial tool that leverages artificial intelligence to automate invoice processing and provide intelligent financial insights through conversational AI. The application combines automated document parsing with an AI-powered chat assistant to help businesses make smarter financial decisions faster.

The platform features:
- Automated invoice upload and parsing using OpenAI's vision capabilities
- Real-time financial dashboard with KPI tracking and visualizations
- Conversational AI assistant for financial queries and insights
- Modern, professional UI inspired by Linear, Stripe Dashboard, and Ramp

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

**Framework**: React 18+ with TypeScript, using Vite as the build tool

**Routing**: Wouter for client-side routing, providing a lightweight alternative to React Router

**State Management**: 
- TanStack Query (React Query) for server state management, data fetching, and caching
- React hooks for local component state
- Query client configured with infinite stale time and disabled automatic refetching for predictable data freshness

**UI Component System**:
- Radix UI primitives for accessible, unstyled components
- shadcn/ui design system (New York style variant) for pre-built, customizable components
- Tailwind CSS for utility-first styling with custom design tokens
- CSS variables for theming support (light/dark modes)

**Design System**:
- Primary font: Inter for UI elements and headings
- Monospace font: JetBrains Mono for financial figures and invoice numbers
- Color palette optimized for financial applications with professional blue primary colors
- Custom spacing scale using Tailwind's unit system (2, 4, 6, 8, 12, 16)
- Hover and active state elevations for interactive elements

**Key Pages**:
- Landing page with hero section and feature showcase
- Dashboard with KPI cards and financial visualizations (using Recharts)
- Invoices page with drag-and-drop upload and table view
- Chat interface for AI assistant interactions

### Backend Architecture

**Runtime**: Node.js with Express.js framework

**Language**: TypeScript with ESM module system

**API Structure**:
- RESTful API endpoints under `/api` prefix
- File upload handling via Multer middleware with 10MB size limit
- Custom request logging middleware for API calls
- Raw body preservation for webhook/payment processing scenarios

**Key API Endpoints**:
- `GET /api/invoices` - Retrieve all invoices
- `GET /api/invoices/:id` - Retrieve single invoice
- `POST /api/invoices/upload` - Upload and parse invoice image
- `GET /api/chat/messages` - Retrieve chat history
- `POST /api/chat/send` - Send message to AI assistant
- `GET /api/insights` - Retrieve AI-generated financial insights

**Development Setup**:
- Vite integration in middleware mode for HMR during development
- Custom error overlay plugin for development
- Separate production build process using esbuild for server bundling

### Data Storage

**ORM**: Drizzle ORM for type-safe database queries and schema management

**Database**: PostgreSQL (configured via Neon serverless driver)

**Schema Design**:

1. **Invoices Table**:
   - UUID primary key with automatic generation
   - File metadata (fileName, fileUrl)
   - Parsed invoice data (vendor, amount, currency, dates, invoice number)
   - Status tracking (pending, processed, error)
   - JSONB column for line items with structured data
   - Raw text field for complete parsed data
   - Timestamp for creation tracking

2. **Chat Messages Table**:
   - UUID primary key
   - Role field (user or assistant)
   - Message content
   - Creation timestamp

3. **Insights Table**:
   - Storage for AI-generated financial insights
   - Linked to invoice data for context

**Storage Abstraction**:
- IStorage interface defining all data operations
- MemStorage implementation for development/testing with in-memory Map storage
- Database storage implementation using Drizzle ORM (production-ready)
- Migration system via drizzle-kit for schema versioning

### Authentication & Authorization

Currently implemented with session-based approach:
- Session storage configured for PostgreSQL via connect-pg-simple
- Cookie-based session management
- Credential inclusion in API requests

### External Dependencies

**AI Services**:
- OpenAI API (GPT-5 model) for:
  - Invoice image parsing and data extraction
  - Conversational AI chat responses
  - Financial insight generation
- Vision API for processing invoice images
- Structured JSON responses for parsed invoice data

**Cloud Services**:
- Neon Database for PostgreSQL hosting (serverless)
- Environment variable: `DATABASE_URL` for database connection
- Environment variable: `OPENAI_API_KEY` for AI services

**Development Tools**:
- Replit-specific plugins for development (cartographer, dev banner, error modal)
- Hot Module Replacement (HMR) via Vite
- TypeScript strict mode for type safety

**Frontend Libraries**:
- react-dropzone for file upload UI
- Recharts for financial data visualization
- date-fns for date manipulation
- react-hook-form with zod resolvers for form validation
- Lucide React for icon system

**Validation & Type Safety**:
- Zod for runtime type validation and schema definition
- drizzle-zod for automatic schema-to-Zod conversion
- TypeScript for compile-time type checking
- Shared type definitions between client and server via `/shared` directory

**Build & Bundling**:
- Vite for frontend development and production builds
- esbuild for server-side bundling with ESM output
- Path aliases configured: `@/` for client source, `@shared/` for shared types, `@assets/` for static assets