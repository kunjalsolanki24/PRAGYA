# PRAGYA

**Predict. Protect. Act Before Impact.**

PRAGYA is a production-quality AI-powered Cyclone Impact & Infrastructure Vulnerability Forecaster designed for coastal APAC disaster-management authorities. It integrates meteorological data, GIS mapping, hazard modelling, infrastructure exposure analysis, and AI reasoning to evaluate cyclone risks before landfall.

## Features
- **Real-time Cyclone Tracking:** Monitor cyclone paths, intensity, and wind speeds dynamically.
- **Interactive Risk Map:** Multi-layered GIS interface showing storm surge, rainfall, and vulnerable infrastructure via MapLibre GL.
- **AI Copilot & Advisories:** Uses Gemini API to automatically generate early warning advisories and mitigation action plans.
- **Infrastructure Vulnerability Scoring:** Assesses risk to critical points (hospitals, roads, power grids) to optimize resource allocation.
- **Evacuation Planning:** Identifies safe routes, calculates route congestion risk, and analyzes shelter capacity.

## Architecture
- **Frontend:** Next.js 14, Tailwind CSS, Recharts, MapLibre GL.
- **Backend:** Python FastAPI, SQLAlchemy, PostgreSQL.
- **Data Integrations:** Google Earth Engine, NOAA/GFS.
- **AI Provider:** Google Gemini API.

## Tech Stack
- **Languages:** TypeScript, Python.
- **Frameworks:** Next.js, FastAPI.
- **Database:** PostgreSQL (with pgvector/postgis if required).
- **Tooling:** Docker, Uvicorn, SQLAlchemy.

## Setup

### Prerequisites
- Node.js (v18+)
- Python 3.10+
- Docker & Docker Compose (for the database)

### Environment Variables
Do not commit your secrets. Create a `.env` file in the root based on `.env.example`:
```env
# Backend Settings
SECRET_KEY=your-super-secret-jwt-key
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=30
CORS_ORIGINS=http://localhost:3000,http://localhost:8000

# Database Settings
DATABASE_URL=postgresql://pragya_user:pragya_password@localhost:5432/pragya

# External APIs
GEMINI_API_KEY=your_gemini_api_key_here
MAPBOX_ACCESS_TOKEN=your_mapbox_token_here_if_applicable
```

## Run Commands

1. **Start the Database:**
   ```bash
   docker-compose up -d
   ```

2. **Start the Backend:**
   ```bash
   cd backend
   python -m venv venv
   # Windows: venv\Scripts\activate
   # macOS/Linux: source venv/bin/activate
   pip install -r requirements.txt
   uvicorn main:app --reload
   ```

3. **Start the Frontend:**
   ```bash
   cd frontend
   npm install
   npm run dev
   ```

4. **Access the Application:** Open your browser to `http://localhost:3000`.

## Deployment
For production, the backend should be deployed using an ASGI server (like Gunicorn with Uvicorn workers) inside a Docker container. The frontend can be deployed to Vercel, Netlify, or Dockerized alongside the backend. Database connections should use connection pooling and TLS.

## Security Notes
- **API Keys & Secrets:** Kept purely in environment variables. `GEMINI_API_KEY` and other sensitive provider keys are never exposed to the frontend.
- **Authentication:** Uses JWT-based basic authentication and session protection with secure password hashing (`bcrypt`).
- **Data Validation:** All backend endpoints validate inputs via Pydantic schemas.
- **CORS:** Configured securely through `CORS_ORIGINS` environment variable.
- **Error Handling:** Standardized error responses to prevent sensitive stack traces or internal errors from leaking to users.
- **Rate Limiting:** Protects sensitive AI endpoints to minimize Gemini API calls and potential abuse.
