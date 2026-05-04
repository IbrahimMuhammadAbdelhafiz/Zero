# Zero - Dark Space Science Hub

A production-ready, full-stack scientific web platform for physics, astronomy, astrophysics, space science, cosmology, and quantum physics research.

## Features

- **Zero AI**: RAG-powered scientific research assistant with Chat, Deep Research, and Summary modes
- **Research Explorer**: Live search across arXiv, Crossref, OpenAlex, and NASA ADS
- **Articles**: Educational science communication content
- **Research**: Verified research contributions with review workflow
- **Resources**: Curated scientific gateways and databases
- **Admin Dashboard**: Full management interface with analytics
- **Multi-language**: English primary with Arabic support structure
- **Role-based access**: Visitor, Registered, Contributor, Reviewer, Admin

## Tech Stack

- **Frontend**: Next.js 15 + React 19 + TypeScript + Tailwind CSS v4
- **Backend**: Next.js API Routes (App Router)
- **Database**: PostgreSQL + Prisma ORM
- **Auth**: JWT + bcryptjs + jose
- **AI**: Provider-agnostic (DeepSeek, OpenRouter, Groq, Mistral, Ollama, etc.)
- **Research APIs**: arXiv, Crossref, OpenAlex, NASA ADS

## Prerequisites

- Node.js 18+
- PostgreSQL database (local or cloud)
- (Optional) AI API key for DeepSeek or other providers

## Installation

```bash
# Clone the repository
git clone <repo-url>
cd zero

# Install dependencies
npm install

# Set up environment variables
cp .env.example .env.local
# Edit .env.local with your database URL and other settings

# Set up database
npx prisma migrate dev
npx prisma db seed

# Run development server
npm run dev
```

## Environment Variables

```env
DATABASE_URL="postgresql://user:password@localhost:5432/zero_db"
JWT_SECRET="your-super-secret-key"

# AI Provider (optional - app works without it)
AI_PROVIDER=deepseek
AI_BASE_URL=https://api.deepseek.com
AI_API_KEY=your-api-key
AI_MODEL=deepseek-r1

# Alternative providers (optional)
OPENROUTER_API_KEY=
GROQ_API_KEY=
MISTRAL_API_KEY=
OLLAMA_BASE_URL=http://localhost:11434

# Research APIs (optional)
NASA_ADS_API_KEY=
SEMANTIC_SCHOLAR_API_KEY=

# Contact
ADMIN_EMAIL=admin@zero.science
```

## Database Setup

### Local PostgreSQL
```bash
# Create database
createdb zero_db

# Run migrations
npx prisma migrate dev

# Seed data
npx prisma db seed
```

### Cloud (Supabase/Neon/Railway)
1. Create a new PostgreSQL project
2. Copy the connection string
3. Set `DATABASE_URL` in `.env.local`
4. Run migrations: `npx prisma migrate dev`

## Deployment

### Vercel
```bash
# Install Vercel CLI
npm i -g vercel

# Deploy
vercel --prod
```

### Database Connection
For serverless deployments, use connection pooling (e.g., Supabase pooler or Neon serverless driver).

## Default Login Credentials (from seed)

- **Admin**: admin@zero.science / admin123
- **Contributor**: contributor@zero.science / contributor123
- **Reviewer**: reviewer@zero.science / reviewer123

## AI Provider Setup

### DeepSeek
1. Get API key from [DeepSeek Platform](https://platform.deepseek.com)
2. Set `AI_PROVIDER=deepseek` and `AI_API_KEY=your-key`

### Ollama (Local)
1. Install Ollama: https://ollama.com
2. Pull a model: `ollama pull deepseek-r1`
3. Set `AI_PROVIDER=ollama` and `OLLAMA_BASE_URL=http://localhost:11434`

### OpenRouter
1. Get key from [OpenRouter](https://openrouter.ai)
2. Set `AI_PROVIDER=openrouter` and `OPENROUTER_API_KEY=your-key`

## Folder Structure

```
zero/
├── prisma/
│   ├── schema.prisma
│   └── seed.ts
├── src/
│   ├── app/
│   │   ├── api/           # API routes
│   │   ├── (pages)/       # Page routes
│   │   ├── layout.tsx
│   │   ├── page.tsx
│   │   └── globals.css
│   ├── components/
│   │   ├── layout/        # Navbar, Hero, StarsBackground
│   │   ├── ui/            # Reusable UI components
│   │   ├── ai/            # AI-specific components
│   │   ├── research/      # Research components
│   │   └── admin/         # Admin components
│   ├── lib/
│   │   ├── services/      # API services (arXiv, Crossref, etc.)
│   │   ├── auth.ts
│   │   ├── db.ts
│   │   ├── utils.ts
│   │   └── translations.ts
│   ├── context/
│   │   ├── AuthContext.tsx
│   │   └── LanguageContext.tsx
│   └── types/
│       └── index.ts
├── .env.example
├── .env.local
├── next.config.ts
├── package.json
├── postcss.config.mjs
├── tsconfig.json
└── README.md
```

## Available Scripts

```bash
npm run dev          # Start development server
npm run build        # Build for production
npm run start        # Start production server
npm run lint         # Run ESLint
npm run db:migrate   # Run Prisma migrations
npm run db:generate  # Generate Prisma client
npm run db:seed      # Seed database
npm run db:studio    # Open Prisma Studio
```

## Troubleshooting

### Database connection errors
- Verify `DATABASE_URL` is correct
- Ensure PostgreSQL is running
- Check firewall/network settings

### AI not working
- The app works without AI keys - it will show search results without summaries
- Check that your AI provider API key is valid
- Verify `AI_BASE_URL` matches your provider

### Build errors
- Ensure all dependencies are installed: `npm install`
- Check Node.js version: `node -v` (should be 18+)
- Clear `.next` folder and rebuild: `rm -rf .next && npm run build`

## License

MIT

## Contributing

Contributions welcome! Please follow the existing code style and add tests for new features.

## Contact

- Email: admin@zero.science
- Platform: https://zero.science
