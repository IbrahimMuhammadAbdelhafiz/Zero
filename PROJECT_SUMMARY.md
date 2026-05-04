# Zero - Complete Project Summary

## Project Overview
Zero is a production-ready full-stack scientific web platform built with Next.js 15, React 19, TypeScript, Tailwind CSS v4, and PostgreSQL.

## Architecture

### Frontend (App Router)
- **Home** (`/`): Minimal hero with animated stars background, logo, and CTAs
- **Zero AI** (`/zero-ai`): Chat, Deep Research, and Summary modes with RAG pipeline
- **Research Explorer** (`/research-explorer`): Live search with filters, sorting, and export
- **Articles** (`/articles`): Science communication content with Markdown support
- **Research** (`/research`): Verified research with review workflow
- **Resources** (`/resources`): Curated scientific gateways
- **About** (`/about`): Platform and founder information
- **Contact** (`/contact`): Contact form with social links
- **Auth** (`/login`, `/register`): JWT-based authentication
- **Dashboard** (`/dashboard`): Admin panel with 9 management sections
- **Submit** (`/submit-research`, `/submit-article`): Contribution forms

### Backend (API Routes)
- **Auth**: `/api/auth/*` - Register, login, logout, me
- **AI**: `/api/ai/*` - Chat, deep-research, summarize (RAG pipeline)
- **Search**: `/api/search/papers` - Aggregated search across sources
- **Research**: `/api/research/*` - CRUD + review workflow
- **Articles**: `/api/articles/*` - CRUD operations
- **Resources**: `/api/resources` - List resources
- **Contact**: `/api/contact` - Submit/view messages
- **Admin**: `/api/admin/*` - Overview, users, AI logs

### Database (Prisma + PostgreSQL)
- User (with roles: VISITOR, REGISTERED, CONTRIBUTOR, REVIEWER, ADMIN)
- Article (with status workflow)
- ResearchItem (with review workflow and citations)
- ResearchSource, SavedSearch, AIChat, ContactMessage
- FeaturedPost, Resource

### Research Source Services
- **arXiv Service**: XML API parsing for preprints
- **Crossref Service**: DOI and publication metadata
- **OpenAlex Service**: Works, authors, citations
- **NASA ADS Service**: Astrophysics Data System (optional)
- **Search Aggregation**: Deduplication, relevance scoring, filtering

### AI Service (Provider-Agnostic)
- Supports: DeepSeek, OpenRouter, DeepInfra, Together AI, Fireworks AI, Groq, Mistral, HuggingFace, Ollama
- RAG pipeline: Search → Normalize → Rank → Cache → Generate
- Structured prompts with source grounding
- Graceful degradation when AI keys missing

### Security
- Password hashing with bcrypt (12 rounds)
- JWT tokens with jose (7-day expiry)
- HTTP-only cookies
- Input validation with Zod
- Role-based route protection via middleware
- XSS protection via React's built-in escaping

### UI/UX
- Dark space theme with cyan/blue accents
- Animated starfield background (Canvas API)
- Glassmorphism cards with glow effects
- Responsive mobile-first design
- Framer Motion animations
- Lucide icons throughout

## Key Features Implemented

1. ✅ RAG AI Assistant with real source retrieval
2. ✅ Multi-provider AI support (not dependent on Gemini)
3. ✅ arXiv, Crossref, OpenAlex integration
4. ✅ Research submission and review workflow
5. ✅ Role-based access control (5 roles)
6. ✅ Admin dashboard with analytics
7. ✅ Citation generation (APA, Vancouver)
8. ✅ Reliability labeling system
9. ✅ Relevance scoring algorithm
10. ✅ Export to CSV/JSON
11. ✅ Arabic language toggle structure
12. ✅ Contact form with database storage
13. ✅ Seed data for testing
14. ✅ Complete README with deployment guide

## Running the Project

```bash
# 1. Install dependencies
npm install

# 2. Set up database (PostgreSQL)
# Create database and set DATABASE_URL in .env.local

# 3. Run migrations
npx prisma migrate dev

# 4. Seed database
npx prisma db seed

# 5. Start development
npm run dev

# 6. Open http://localhost:3000
```

## Default Logins (from seed)
- Admin: admin@zero.science / admin123
- Contributor: contributor@zero.science / contributor123
- Reviewer: reviewer@zero.science / reviewer123

## Deployment
- Vercel-ready with `next.config.ts`
- Database: Supabase, Neon, or Railway recommended
- Set environment variables in hosting dashboard
