# Fullstack Monorepo Guide & Learning Roadmap

## Tech Stack Overview

This project is a modern, end-to-end type-safe fullstack monorepo built with:

- **Monorepo Management**: `pnpm` workspaces + `concurrently`
- **Backend (`apps/api`)**: Node.js, Fastify v5, Drizzle ORM, PostgreSQL (`pg`), Zod validation, `tsx` watcher
- **Frontend (`apps/web`)**: React 19, Vite 8, Tailwind CSS v4, TanStack React Query v5, shadcn / Base UI primitives

---

## Workspace Structure & Commands

### Architecture
```
fullstack/
├── apps/
│   ├── api/  --> Fastify + Drizzle ORM + PostgreSQL + Zod
│   └── web/  --> React 19 + Vite + Tailwind CSS v4 + React Query + shadcn/Base UI
```

### Essential Commands

| Task | Command | Description |
| :--- | :--- | :--- |
| **Start Everything** | `pnpm dev` | Starts both API server (`localhost:8000`) & Web app (`localhost:5173`) |
| **Generate Migrations** | `pnpm --filter api db:generate` | Generates SQL files from changes in `apps/api/src/db/schema.ts` |
| **Apply Migrations** | `pnpm --filter api db:migrate` | Applies migration files to PostgreSQL database |
| **Database Dashboard** | `pnpm --filter api db:studio` | Opens visual database interface in browser |

---

## Using This Project as a Base Template

To reuse this setup as a starter boilerplate for new projects:

1. **Copy directory** or click **"Use this template"** on GitHub.
2. **Reset Git & update project names**:
   - Remove `.git` folder and re-run `git init`.
   - Update `name` in root `package.json`, `apps/api/package.json`, and `apps/web/package.json`.
3. **Environment Setup**:
   - Create `.env` in `apps/api/` with your `DATABASE_URL`.
   - Run `pnpm install` and `pnpm dev`.

---

## 🗺️ Step-by-Step Beginner Learning Roadmap

> 📖 **Hands-on Project**: Check out [PROJECT_GUIDE.md](file:///e:/xampp/htdocs/img/fullstack/PROJECT_GUIDE.md) for a multi-part project (**FleetPulse Truck Analytics Platform**) designed to teach you this stack step-by-step!

```
Phase 1: Foundations (TypeScript & Modern JS)
      │
Phase 2: Backend Basics (Fastify & PostgreSQL)
      │
Phase 3: Database & Validation (Drizzle ORM & Zod)
      │
Phase 4: Frontend Basics (React 19 & Tailwind CSS v4)
      │
Phase 5: Fullstack Connection (TanStack React Query)
      │
Phase 6: Monorepo Workflows & Deployment
```

### **Phase 1: Modern JS & TypeScript Foundations**
- **Key Concepts**: `async`/`await`, Promises, ESM module imports (`./file.js`), TypeScript types, interfaces, and generics.
- **Practice Task**: Add helper functions with typed inputs and outputs in `apps/api/src/`.

### **Phase 2: Backend Basics (Fastify & PostgreSQL)**
- **Key Concepts**: HTTP methods (GET, POST, PUT, DELETE), Fastify routing, CORS configuration, relational database concepts (Tables, Keys).
- **Practice Task**: Create a new Fastify route `GET /ping` in `apps/api/src/index.ts` returning `{ message: "pong", timestamp: Date.now() }`.

### **Phase 3: Data Safety (Drizzle ORM & Zod)**
- **Key Concepts**: Drizzle schema definitions (`pgTable`, `serial`, `text`), generating/running migrations, Drizzle query API (`db.select()`, `db.insert()`), Zod payload validation.
- **Practice Task**: Define a new table in `apps/api/src/db/schema.ts`, run `pnpm --filter api db:generate`, and create a route to query it.

### **Phase 4: Frontend UI (React 19, Vite & Tailwind CSS v4)**
- **Key Concepts**: React hooks (`useState`, `useEffect`), components & props, Tailwind CSS v4 styling rules, accessible UI primitives.
- **Practice Task**: Create a reusable UI component in `apps/web/src/components/` styled with Tailwind.

### **Phase 5: Connecting Frontend & Backend (TanStack React Query)**
- **Key Concepts**: `useQuery` for fetching/caching server data, `useMutation` for form submissions, handling loading/error states.
- **Practice Task**: Fetch your API data inside a React component using `useQuery` and render it on the page.

### **Phase 6: Monorepo Workflows & Deployment**
- **Key Concepts**: Workspace CLI filtering (`pnpm --filter`), `.env` variable configuration, deploying PostgreSQL (Neon/Supabase), Backend (Render/Railway), Frontend (Vercel/Netlify).

---

## 📚 Resources & Documentation

- **TypeScript**: [TypeScript Handbook](https://www.typescriptlang.org/docs/handbook/intro.html)
- **Fastify**: [Fastify Docs](https://fastify.dev/docs/latest/Guides/Getting-Started/)
- **Drizzle ORM**: [Drizzle Docs](https://orm.drizzle.team/docs/overview)
- **React**: [React Docs](https://react.dev/learn)
- **TanStack React Query**: [React Query Quick Start](https://tanstack.com/query/latest/docs/framework/react/quick-start)
