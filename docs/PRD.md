# PRAGYA - Product Requirements Document (PRD)

## 1. Problem Statement
Coastal APAC regions face devastating impacts from cyclones. Existing systems often lack real-time infrastructure vulnerability assessments and predictive reasoning to proactively guide disaster-management authorities before landfall.

## 2. Target Users
- Disaster Management Authorities
- Government Planners and Responders
- Infrastructure Operators (Power, Roads, Hospitals)

## 3. Objectives
Build PRAGYA: an AI-powered Cyclone Impact & Infrastructure Vulnerability Forecaster that combines meteorological data, satellite/GIS data, hazard modeling, and AI reasoning to deliver actionable insights BEFORE landfall.

## 4. Key Features (Phase 1 & 2)
- **Authentication:** Secure user accounts and sessions.
- **Command Dashboard:** Overview of cyclone tracks, intensity, and risk summaries.
- **Interactive Risk Map:** Multi-layer geospatial mapping (path, rainfall, surge, infrastructure).
- **Vulnerability Scoring:** Automated assessment of infrastructure exposure.
- **AI Reasoning:** Natural language generation of early warning advisories and mitigation actions (powered by Gemini 3.7 Flash).

## 5. User Journeys
1. **Onboarding:** User signs up, logs in, and views the personalized dashboard.
2. **Monitoring:** User monitors live cyclone tracks and infrastructure exposure layers on the interactive map.
3. **Actioning:** User receives critical alerts and AI-generated advisories to coordinate evacuation and mitigation efforts.

## 6. Success Criteria
- The application is highly reliable and performs real, meaningful operations.
- The UI is premium, responsive, and visually represents complex data clearly.
- Data pipelines degrade gracefully if external sources are unavailable.
- Clear separation of concerns between frontend, backend, and AI/GIS services.
