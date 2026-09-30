# PRAGYA - Engineering & Design Rules

## 1. Coding Rules
- Use TypeScript for frontend and strict type hints in Python backend.
- Keep components small, focused, and reusable.
- Follow functional programming principles where applicable.
- Do not over-engineer; build solid foundations first.

## 2. UI & Design Rules
- Premium, professional aesthetics with high information density.
- Use subtle glassmorphism and restrained micro-interactions.
- Every visible button and control MUST perform a functional operation (no dead links).
- Never use the word "demo" in the UI.
- Implement responsive design (Desktop, Tablet, Mobile).

## 3. Security & API Key Rules
- NEVER hardcode secrets or API keys in the source code.
- Use `.env` files for configuration.
- Add `.env` to `.gitignore`.

## 4. Error Handling & Data Integrity
- Frontend must gracefully handle network errors, displaying toasts or error states, not blank screens.
- Backend must validate all input data using Pydantic.
- If an external data source is down, the system must clearly indicate this and use cached data rather than faking live data.

## 5. Accessibility & Testing
- UI components should be accessible (ARIA roles, keyboard navigation).
- Write unit tests for critical business logic (e.g., vulnerability scoring, auth).
