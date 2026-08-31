# FertilizeIQ - Smart Farming Predictions

## Overview

FertilizeIQ is a data-driven agricultural productivity application that helps farmers predict fertilizer requirements and water needs based on soil and crop data. The application provides interactive visualizations, real-time predictions, and actionable recommendations to optimize farming operations.

**Core Purpose:** Enable farmers to make informed decisions about fertilizer application and water usage through scientific predictions based on soil composition, crop types, and environmental conditions.

**Key Features:**
- Fertilizer and water requirement predictions
- Multi-crop support (wheat, corn, rice, soybean, cotton, potato, tomato)
- NPK (Nitrogen, Phosphorus, Potassium) analysis
- Weather-adjusted recommendations
- Unit system flexibility (metric/imperial)
- Prediction history tracking
- Export capabilities (CSV/PDF)

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture

**Framework:** React with TypeScript using Vite as the build tool

**UI Component System:**
- **Design System:** Custom agricultural-focused design using shadcn/ui components with Radix UI primitives
- **Styling:** Tailwind CSS with custom theme optimized for outdoor readability (high contrast, agricultural color palette)
- **State Management:** TanStack Query (React Query) for server state, React hooks for local state
- **Routing:** Wouter for lightweight client-side routing
- **Form Handling:** React Hook Form with Zod validation

**Design Principles:**
- Data clarity over decorative elements
- High contrast for outdoor/bright light readability
- Form efficiency for quick field data entry
- Professional, scientific presentation to build trust

**Color Scheme:**
- Primary: Agricultural green (HSL: 142 65% 45%)
- Secondary: Earth tones (HSL: 30 25% 35%)
- Light and dark mode support
- Success/warning indicators for prediction severity

### Backend Architecture

**Server Framework:** Express.js with TypeScript

**API Design:**
- RESTful API structure
- Single prediction endpoint: `POST /api/predict`
- JSON request/response format
- Built-in request/response logging middleware

**Prediction Algorithm:**
- Crop-specific factors for water and fertilizer calculations
- NPK (Nitrogen, Phosphorus, Potassium) target-based recommendations
- Weather adjustment factors (temperature, rainfall)
- Soil moisture consideration
- Severity classification (low, medium, high)

**Data Validation:**
- Zod schemas for request validation
- Type-safe data flow using shared schema definitions

### Data Storage

**Current Implementation:** In-memory storage (MemStorage class)

**Data Models:**
- User authentication schema (prepared for future use)
- Prediction request/response types
- History entries (client-side localStorage)

**Future-Ready:**
- Drizzle ORM configured for PostgreSQL migration
- Database schema defined in `shared/schema.ts`
- Connection ready via Neon serverless driver

### State Management Strategy

**Server State:**
- TanStack Query for API data fetching and caching
- Optimistic updates disabled (staleTime: Infinity)
- Manual refetch control

**Client State:**
- React Hook Form for form state
- localStorage for prediction history (max 10 entries)
- Toast notifications for user feedback

**Data Flow:**
1. User inputs farm data via validated form
2. Data sent to `/api/predict` endpoint
3. Server calculates predictions using crop factors
4. Results displayed with visualizations
5. History saved to localStorage

### Component Architecture

**Page Structure:**
- Single-page application with `EnhancedHome` as main view
- Not Found fallback page

**Key Components:**
- `EnhancedFarmDataForm`: Input form with validation and tooltips
- `EnhancedPredictionResults`: Results display with severity badges
- `PredictionChart`: Chart.js visualizations
- `ComparisonView`: Side-by-side fertilizer/water comparison
- `HistoryPanel`: Collapsible recent predictions
- `AlertBanner`: Dynamic weather/condition alerts

**Shared UI Components:** Full shadcn/ui library implementation (40+ components)

## External Dependencies

### Third-Party Services

**None Currently Integrated** - The application runs standalone without external API dependencies.

### Key Libraries

**Frontend:**
- `@tanstack/react-query` (^5.60.5) - Server state management
- `react-hook-form` (via @hookform/resolvers ^3.10.0) - Form handling
- `chart.js` (^4.5.0) - Data visualization
- `zod` - Schema validation
- `date-fns` (^3.6.0) - Date formatting
- `wouter` - Routing
- Radix UI primitives (@radix-ui/*) - Accessible component foundation

**Backend:**
- `express` - HTTP server
- `drizzle-orm` (^0.39.1) - Database ORM (configured, not actively used)
- `@neondatabase/serverless` (^0.10.4) - PostgreSQL driver (ready for migration)
- `connect-pg-simple` (^10.0.0) - Session store (prepared)

**Build Tools:**
- `vite` - Frontend bundler and dev server
- `esbuild` - Backend bundler
- `tailwindcss` - CSS framework
- `typescript` - Type safety

**Database (Configured):**
- PostgreSQL via Neon serverless
- Drizzle ORM for type-safe queries
- Migration support via drizzle-kit

**Export Functionality:**
- CSV export (client-side generation)
- PDF export (client-side generation)

### Environment Configuration

**Required Variables:**
- `DATABASE_URL` - PostgreSQL connection string (for future database integration)
- `NODE_ENV` - Environment mode (development/production)

**Development Tools:**
- Replit-specific plugins for development banner and error overlay
- Hot module replacement (HMR) via Vite