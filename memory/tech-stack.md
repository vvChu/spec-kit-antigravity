# Tech Stack Reference

> Agents MUST read this file during `/architect`, `/execute`, and `/refactor` workflows.  
> Calibrate this file to match your specific project before using the kit.

---

## Frontend
- **Framework**: [e.g., Next.js 15 / React 18]
- **Styling**: [e.g., Tailwind CSS v4]
- **State Management**: [e.g., Zustand / TanStack Query v5]
- **Component Library**: [e.g., shadcn/ui / Radix UI]
- **Testing**: [e.g., Vitest + React Testing Library]

## Backend
- **Runtime**: [e.g., Node.js 22 / Python 3.12]
- **Framework**: [e.g., Hono / FastAPI / Express]
- **Database**: [e.g., PostgreSQL 16 + Prisma ORM]
- **Auth**: [e.g., Clerk / Auth.js v5 / Supabase Auth]
- **Testing**: [e.g., Vitest / pytest]

## DevOps & Deployment
- **CI/CD**: GitHub Actions
- **Hosting**: [e.g., Vercel / Railway / Fly.io]
- **Build command**: `[e.g., npm run build]`
- **Health-check endpoint**: `[e.g., GET /api/health]`
- **Environment variables file**: `.env.local` (never commit this file)

---

## ✅ Preferred Patterns
- `const` / `let` — never `var`
- `async/await` — never raw `.then()` chains
- React functional components with Hooks — never class components
- Named exports — avoid default exports for components
- Zod for runtime schema validation
- Environment variables via `process.env.VARIABLE_NAME` (validated at startup)

## ❌ Forbidden Patterns
- Hardcoded secrets, tokens, or API keys anywhere in source code
- `any` type in TypeScript (use `unknown` or a specific type)
- Direct DOM manipulation inside React components
- Inline SQL strings (use ORM query builders)
- `console.log` left in production code (use a structured logger)
- Synchronous file I/O in a Node.js request handler
