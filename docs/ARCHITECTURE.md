# PRAGYA - System Architecture

## 1. System Overview
PRAGYA is a client-server architecture consisting of a Next.js frontend, a FastAPI Python backend, and a PostgreSQL database.

## 2. Frontend Architecture
- **Framework:** Next.js (App Router).
- **State Management:** React hooks + context (or Zustand if complexity increases).
- **Styling:** Tailwind CSS + shadcn/ui.
- **Routing:** `/` (Landing), `/login`, `/register`, `/dashboard`, `/dashboard/profile`.
- **Data Fetching:** Axios/fetch with SWR or React Query for caching.

## 3. Backend Architecture
- **Framework:** FastAPI.
- **Layers:**
  - `/api`: Route handlers and controllers.
  - `/core`: Configuration, security, middleware.
  - `/db`: Database connection and ORM models.
  - `/schemas`: Pydantic models for request/response validation.
  - `/services`: Business logic (Auth, Geospatial, ML).

## 4. Data Flow
1. Client requests data via REST API.
2. FastAPI validates request via Pydantic.
3. Service layer accesses database via SQLAlchemy or calls external APIs (GEE, NOAA).
4. Data is transformed and returned to the client.

## 5. ML & Gemini Pipeline (Phase 2)
- Extracted infrastructure exposure data is formatted into structured prompts.
- Prompts are sent to Gemini 3.7 Flash for analysis.
- Gemini returns structured JSON insights, which are rendered as "Early Warning Advisories" in the dashboard.
