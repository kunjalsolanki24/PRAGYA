# PRAGYA - Technical Requirements Document (TRD)

## 1. Technology Stack
- **Frontend:** Next.js 14+ (App Router), React, TypeScript, Tailwind CSS, Recharts, MapLibre GL.
- **Backend:** Python 3.10+, FastAPI.
- **Database:** PostgreSQL (with PostGIS if geospatial querying is needed later).
- **ORM / Migrations:** SQLAlchemy, Alembic.
- **Authentication:** JWT (JSON Web Tokens).
- **AI Engine:** Google Gemini 3.7 Flash (for multimodal reasoning, NOT physics calculations).

## 2. APIs & Integrations
- **Google Earth Engine (GEE):** Sentinel-1, Sentinel-2, DEM, CHIRPS, ERA5.
- **Meteorological Data:** NOAA / GFS, IBTrACS.
- **AI API:** Google Gemini API.

## 3. Data Pipeline
- Background tasks (Celery/Redis or simple FastAPI BackgroundTasks for Phase 1) will fetch and process external meteorological data.
- Processed data is stored locally in PostgreSQL or a timeseries store.
- Fallback mechanisms exist if external APIs fail (using the latest cached data).

## 4. Security
- API keys and secrets stored ONLY in environment variables (`.env`).
- Passwords hashed using bcrypt.
- JWT-based authentication for all protected endpoints.
- No secrets pushed to version control.

## 5. Deployment
- Docker and Docker Compose for local development and eventual production deployment.
- CI/CD pipeline (e.g., GitHub Actions) for linting, testing, and deployment.
