# Creator Studio — AI Social Media Content Generator

Creator Studio is a full-stack AI-powered social media campaign generator that helps users create structured 7-day content campaigns for multiple platforms. It supports brand profiles, campaign planning, caption generation, hashtags, content calendars, brand guardrails, audience personas, conversion paths, source-document facts, performance insights, experiments, competitor analysis, and caption refinement.

The project is built with a FastAPI backend, React + TypeScript frontend, SQLite database, and Groq-powered AI generation.

---

## Features

* User authentication with JWT-based access tokens
* Brand profile management
* AI-powered 7-day campaign generation
* Platform-specific content for Instagram, LinkedIn, TikTok, Facebook, and X / Twitter
* Tone selection such as casual, professional, funny, luxury, Gen Z, and motivational
* Caption, hook, CTA, hashtag, and post idea generation
* Campaign calendar view
* Caption library with filters and search
* Campaign history and saved posts
* Brand guardrails for required phrases, forbidden words, restricted claims, legal disclaimers, tone rules, and hashtag limits
* Audience personas for targeted campaign generation
* Conversion paths for website, WhatsApp, booking forms, newsletters, and other destinations
* Source documents and approved source facts
* Content packs and reusable strategy templates
* Performance import and insights
* A/B experiments with variants and winner declaration
* Competitor content-gap analysis
* Content freshness and repetition detection
* Regional content settings including English, Urdu, Roman Urdu, and bilingual modes
* AI-powered caption refinement and regeneration
* Guest dashboard preview with locked authenticated features

---

## Tech Stack

### Backend

* Python
* FastAPI
* SQLAlchemy
* SQLite
* Pydantic
* JWT authentication
* Groq API
* Uvicorn

### Frontend

* React
* TypeScript
* Vite
* Tailwind CSS
* React Router
* Recharts
* Vitest

---

## Project Structure

```text
Social Media Content Generator/
├── backend/
│   ├── app/
│   │   ├── ai/
│   │   ├── api/
│   │   ├── models/
│   │   ├── modules/
│   │   ├── services/
│   │   └── main.py
│   ├── migrations/
│   ├── scripts/
│   ├── tests/
│   ├── .env.example
│   └── pyproject.toml
│
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── components/
│   │   ├── features/
│   │   ├── hooks/
│   │   ├── pages/
│   │   ├── routes/
│   │   └── services/
│   ├── package.json
│   ├── vite.config.ts
│   └── tailwind.config.ts
│
└── README.md
```

---

## Requirements

Install these before running the project:

* Python 3.10 or newer
* Node.js 18 or newer
* npm
* Groq API key

---

## Backend Setup

Open a terminal in the backend folder:

```bash
cd "Social Media Content Generator/backend"
```

Create and activate a virtual environment:

```bash
python -m venv .venv
```

Windows:

```bash
.venv\Scripts\activate
```

Install dependencies:

```bash
pip install -e ".[dev]"
```

If editable install is not configured in your local copy, install the required packages from the project dependency file.

Create your environment file:

```bash
copy .env.example .env
```

Update `.env` with your own values.

Example:

```env
APP_NAME="Social Media Content Generator"
APP_VERSION="1.0.0"
APP_DEBUG=true
APP_ENV=development

HOST=0.0.0.0
PORT=8000

CORS_ORIGINS=["http://localhost:5173","http://localhost:5174"]
FRONTEND_ORIGINS=["http://localhost:5173","http://localhost:5174"]

DATABASE_URL=sqlite:///./social_media.db

SECRET_KEY=replace_with_a_secure_secret
JWT_ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=15
REFRESH_TOKEN_EXPIRE_DAYS=7

GROQ_ENABLED=true
GROQ_API_KEY=your_groq_api_key_here
GROQ_MODEL=llama-3.1-8b-instant
GROQ_TIMEOUT_SECONDS=60
GROQ_MAX_RETRIES=2

GROQ_TPM_BUDGET=5000
GROQ_STRATEGY_MAX_OUTPUT_TOKENS=700
GROQ_CAMPAIGN_MAX_OUTPUT_TOKENS=2800
GROQ_REFINEMENT_MAX_OUTPUT_TOKENS=900
```

Run the backend:

```bash
python -m uvicorn app.main:app --host 0.0.0.0 --port 8000 --reload
```

Backend URL:

```text
http://localhost:8000
```

API docs:

```text
http://localhost:8000/docs
```

---

## Frontend Setup

Open a separate terminal in the frontend folder:

```bash
cd "Social Media Content Generator/frontend"
```

Install dependencies:

```bash
npm install
```

Start the frontend:

```bash
npm run dev
```

Frontend URL:

```text
http://localhost:5173
```

If port 5173 is already in use, Vite may start on another port such as:

```text
http://localhost:5174
```

Make sure that port is included in backend CORS settings.

---

## Common Run Commands

### Backend

```bash
cd "D:\OptimusAutomate_AIProductivitySuite\Social Media Content Generator\backend"
python -m uvicorn app.main:app --host 0.0.0.0 --port 8000 --reload
```

### Frontend

```bash
cd "D:\OptimusAutomate_AIProductivitySuite\Social Media Content Generator\frontend"
npm run dev
```

### Backend import check

```bash
python -c "from app.main import app; print('IMPORT_OK')"
```

### Groq environment check

```bash
python -c "from dotenv import load_dotenv; load_dotenv(); import os; print(os.getenv('GROQ_MODEL')); print(os.getenv('GROQ_ENABLED'))"
```

---

## Groq AI Configuration

This project uses Groq for campaign strategy, post generation, source-fact extraction, and caption refinement.

Recommended development model:

```env
GROQ_MODEL=llama-3.1-8b-instant
```

The application includes fallback generation when Groq is unavailable or a request fails. Fallback output should be clearly labeled and should not be presented as Groq-generated content.

Do not commit real API keys.

Never include `.env` in a public ZIP or GitHub repository.

---

## Main User Flow

1. Open the landing page.
2. Sign in or create an account.
3. Create a brand profile.
4. Add brand guardrails.
5. Add audience personas.
6. Add a conversion path.
7. Add source documents and approve facts.
8. Generate a 7-day campaign.
9. Review generated calendar posts.
10. Refine captions, hooks, CTAs, or hashtags.
11. View saved campaigns in History.
12. Analyze performance, experiments, and competitor gaps.

---

## Testing

### Backend tests

```bash
cd backend
pytest
```

### Backend linting

```bash
ruff check app tests
ruff format app tests --check
```

### Frontend tests

```bash
cd frontend
npm run test -- --run
```

### Frontend type check

```bash
npm run typecheck
```

### Frontend lint

```bash
npm run lint
```

### Frontend production build

```bash
npm run build
```

---

## Important Security Notes

Before sharing or uploading the project:

Do not include:

```text
.env
backend/social_media.db
backend/social_media_content.db
backend/uploads/
backend/backups/
backend/**/__pycache__/
backend/**/*.pyc
backend/.pytest_cache/
backend/.ruff_cache/
backend/*.log
frontend/node_modules/
frontend/dist/
frontend/*.tsbuildinfo
CONVERSATION_LOG.md
```

Also remove:

* Real Groq API keys
* JWT secrets
* Password hashes
* Personal profile data
* Uploaded avatars
* Database backups
* Terminal logs

Use `.env.example` with placeholder values instead.

---

## Known Limitations

* Social media publishing integrations are not included yet.
* Password reset may require email-provider configuration for production use.
* SQLite is used for local development.
* For production, PostgreSQL and a proper migration system are recommended.
* Groq token limits depend on the account tier and selected model.
* Some generation requests may use fallback if the AI provider is unavailable or rate-limited.
* Public deployment requires additional security hardening, especially around uploads, URL fetching, CORS, and authentication.

---

## Demo Recording Suggestions

For a project demo, show this order:

1. Landing page
2. Login
3. Dashboard overview
4. Brand profile
5. Guardrails
6. Personas
7. Conversion paths
8. Source documents and approved facts
9. Campaign generation
10. Generated 7-day calendar
11. Caption refinement
12. Captions page
13. Calendar page
14. Performance insights
15. A/B experiments
16. Competitor gap analysis
17. Campaign history

---

## Status

Creator Studio meets and exceeds the basic requirement of generating social media posts from brand input, platform selection, tone selection, and campaign goals.

It adds advanced features such as brand memory, guardrails, personas, source facts, performance learning, experiments, competitor-gap analysis, and refinement workflows.
