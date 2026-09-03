# 🛠️ Monorepo Environment Setup Tutorial

This guide provides step-by-step instructions to set up and run this fullstack monorepo project on any machine (**Windows**, **macOS**, or **Linux**).

---

## 📋 Prerequisites

Before starting, ensure you have the following installed on your machine:

1. **Node.js** (v20 or higher recommended)
   - Check version: `node -v`
   - Download: [nodejs.org](https://nodejs.org/)

2. **pnpm** (Package Manager)
   - Install globally via Corepack or npm:
     ```bash
     npm install -g pnpm
     ```
   - Check version: `pnpm -v`

3. **PostgreSQL Database**
   - You need a running PostgreSQL database. You can use any of the following:
     - **Option A (Easiest Cloud)**: Create a free database on [Neon.tech](https://neon.tech) or [Supabase.com](https://supabase.com).
     - **Option B (Docker)**: Run `docker run --name pg-local -e POSTGRES_PASSWORD=postgres -p 5432:5432 -d postgres`
     - **Option C (Local Installer)**: Install PostgreSQL locally via [postgresql.org](https://www.postgresql.org/download/) or XAMPP/pgAdmin.

---

## 🚀 Step-by-Step Setup Instructions

### Step 1: Clone the Repository & Install Dependencies

Open your terminal, navigate to your desired directory, and run:

```bash
# Clone the repository
git clone <YOUR_GIT_REPOSITORY_URL> fullstack
cd fullstack

# Install all workspace dependencies
pnpm install
```

---

### Step 2: Configure Environment Variables

1. Navigate to `apps/api/` or create a `.env` file inside `apps/api/`:
   ```bash
   # Create .env file inside apps/api/
   ```

2. Add your PostgreSQL database connection string to `apps/api/.env`:

   ```env
   # PostgreSQL Connection String Format:
   # postgresql://<user>:<password>@<host>:<port>/<database_name>

   DATABASE_URL="postgresql://postgres:postgres@localhost:5432/fullstack_db"
   PORT=8000
   ```

   *(If using Neon or Supabase, paste the connection string provided in your database dashboard).*

---

### Step 3: Run Database Migrations

Use **Drizzle Kit** to generate and apply your database tables:

```bash
# 1. Generate SQL migration files from Drizzle schema
pnpm --filter api db:generate

# 2. Push / apply schema migrations to your PostgreSQL database
pnpm --filter api db:migrate
```

*(Optional)* To view your database tables visually in your browser:
```bash
pnpm --filter api db:studio
```

---

### Step 4: Start the Development Environment

Run the root dev command to start both the **Fastify Backend API** and the **Vite React Frontend** concurrently:

```bash
pnpm dev
```

You should see output indicating both servers are live:
- 🟢 **Fastify Backend API**: [http://localhost:8000](http://localhost:8000)
- 🔵 **React Frontend App**: [http://localhost:5173](http://localhost:5173)

---

## 🛠️ Essential Workspace Commands

| Task | Command | Description |
| :--- | :--- | :--- |
| **Start Dev Servers** | `pnpm dev` | Starts API (`:8000`) and Frontend (`:5173`) simultaneously |
| **Install New Package (Frontend)** | `pnpm --filter web add <pkg-name>` | Adds a npm package to `apps/web` |
| **Install New Package (Backend)** | `pnpm --filter api add <pkg-name>` | Adds a npm package to `apps/api` |
| **Generate Migrations** | `pnpm --filter api db:generate` | Creates SQL files from schema changes |
| **Apply Migrations** | `pnpm --filter api db:migrate` | Runs pending migrations on PostgreSQL |
| **Database GUI Studio** | `pnpm --filter api db:studio` | Opens visual database editor in browser |

---

## ❓ Troubleshooting & FAQs

### 1. `pnpm: command not found`
Enable Corepack or re-install pnpm globally:
```bash
corepack enable
npm install -g pnpm
```

### 2. Database Connection Failed (`econnrefused`)
- Ensure PostgreSQL is running on your machine or Docker container.
- Check that your `DATABASE_URL` in `apps/api/.env` has the correct username, password, host, and port.

### 3. Port `8000` or `5173` is already in use
- Kill any existing node processes running on those ports, or change `PORT` in `apps/api/.env`.
