# 🚚 FleetPulse — Multi-Part Fullstack Learning Project

Welcome to **FleetPulse**, a hands-on, 5-part fullstack project designed specifically to master your monorepo tech stack:

- **Monorepo**: `pnpm` Workspaces
- **Backend (`apps/api`)**: Node.js, Fastify v5, Drizzle ORM, PostgreSQL, Zod validation
- **Frontend (`apps/web`)**: React 19, Vite, Tailwind CSS v4, TanStack React Query v5, shadcn/UI

---

## 🎯 Project Goal
Build a **Smart Fleet & Truck Logistics Analytics System** that tracks vehicle health, telemetry data (speed, engine temperature, fuel level), active trips, and driver efficiency with real-time updates and interactive charts.

---

## 🗺️ Project Parts Overview

```
Part 1: Database & Fastify API (Schema, ORM & Validations)
   │
Part 2: React 19 Dashboard UI & Tailwind v4 Primitives
   │
Part 3: Data Synchronization with TanStack React Query v5
   │
Part 4: Fleet Telemetry Analytics & Data Visualization
   │
Part 5: Shared Types, Filtering & Advanced Monorepo Workflows
```

---

## 📌 Part 1: Backend Data Model & Fastify REST API

### 💡 What You Will Learn
- Defining relational schemas with **Drizzle ORM** (`pgTable`).
- Running Drizzle migrations (`drizzle-kit`).
- Request body validation using **Zod**.
- Fastify route parameters, handlers, and error handling.

### 🔨 Tasks & Deliverables
1. **Schema Design** (`apps/api/src/db/schema.ts`):
   - `trucks` table: `id` (uuid/serial), `vin` (unique string), `model`, `status` (`'active'` | `'idle'` | `'maintenance'`), `fuelLevel` (int %), `payloadCapacityKg` (int), `driverName` (string).
   - `telemetry` table: `id`, `truckId` (FK), `speedKmh` (int), `engineTempC` (int), `latitude` (float), `longitude` (float), `timestamp` (timestamp).
   - `trips` table: `id`, `truckId` (FK), `origin`, `destination`, `distanceKm`, `fuelConsumedLiters`, `status` (`'en_route'` | `'completed'` | `'scheduled'`).
2. **Database Seeding Script** (`apps/api/src/db/seed.ts`):
   - Populate database with 8–10 realistic truck profiles and telemetry history.
3. **API Routes** (`apps/api/src/routes/`):
   - `GET /api/trucks` – List all trucks with optional filtering by status.
   - `GET /api/trucks/:id` – Get single truck details with recent telemetry logs.
   - `POST /api/trucks` – Create a new truck profile (validated via Zod).
   - `PATCH /api/trucks/:id/status` – Update truck status.
   - `POST /api/telemetry` – Log incoming telemetry data point for a truck.

---

## 📌 Part 2: Interactive React 19 UI & Tailwind v4 Styling

### 💡 What You Learn
- **React 19** state management, props, and modular component hierarchy.
- Styling with **Tailwind CSS v4** design tokens and dynamic utility classes.
- Accessible component design with **shadcn / Base UI** primitives (Cards, Tables, Badges, Modals).

### 🔨 Tasks & Deliverables
1. **Summary Stat Cards**:
   - Total Fleet Size, Active Trucks, Idle Trucks, Maintenance Alerts, Average Fleet Fuel Level.
2. **Truck Fleet Table**:
   - Displays VIN, Model, Driver, Fuel Level (progress bar), and Status Badge (`Active`: Green, `Idle`: Yellow, `Maintenance`: Red).
   - Search bar by Driver/VIN and status filter tabs.
3. **Truck Detail Drawer / Modal**:
   - Detailed specs, current coordinates, live stats, and maintenance history.
4. **"Add New Truck" Modal Form**:
   - Input fields for VIN, Model, Capacity, and Driver Name with client-side form validation.

---

## 📌 Part 3: Fullstack Integration with TanStack React Query v5

### 💡 What You Learn
- Fetching & caching server state using `useQuery`.
- Submitting mutations with `useMutation`.
- Query cache invalidation (`queryClient.invalidateQueries`).
- Optimistic updates and graceful loading/error UI states.

### 🔨 Tasks & Deliverables
1. **Data Fetching Hook**:
   - Create custom React hooks like `useTrucks()`, `useTruckDetails(id)`, `useCreateTruck()`.
2. **Form Submission & Invalidation**:
   - On submitting "Add Truck" form, send POST request via `useMutation` and automatically refresh the truck table without full page reload.
3. **Live Telemetry Polling**:
   - Use `refetchInterval` in `useQuery` to simulate real-time GPS telemetry updates every 5 seconds.

---

## 📌 Part 4: Fleet Analytics & Data Visualization

### 💡 What You Learn
- Integrating chart libraries (e.g. `recharts`) with React 19.
- Computing derived data metrics (Fuel Efficiency in km/L, Fleet Utilization Rates).
- Visualizing real-time telemetry streams.

### 🔨 Tasks & Deliverables
1. **Fuel vs Distance Analytics Chart**:
   - Line chart comparing fuel consumption across recent trips.
2. **Fleet Status Breakdown**:
   - Donut / Pie chart displaying percentage of trucks currently active vs idle vs undergoing repair.
3. **Telemetry Health Gauge / Time-Series**:
   - Engine Temperature time-series chart highlighting high-heat warnings (>95°C).

---

## 📌 Part 5: Shared Contracts & Monorepo Optimization

### 💡 What You Learn
- Creating shared TypeScript interface packages across monorepo apps.
- Monorepo package filtering (`pnpm --filter`).
- Environment variable configuration (`.env`) for local and deployment environments.

### 🔨 Tasks & Deliverables
1. **Shared Types / Zod Schemas**:
   - Extract Zod schemas & TypeScript types into a shared package or shared module to ensure end-to-end type safety between Fastify API response and React frontend components.
2. **Export & Filter Features**:
   - Add CSV export functionality for fleet telemetry report logs.
3. **Monorepo Build Verification**:
   - Test full monorepo build pipeline (`pnpm build`).

---

## 🚀 How to Start

1. Start both servers in development mode:
   ```bash
   pnpm dev
   ```
2. Begin with **Part 1**: Open `apps/api/src/db/schema.ts` and define the `trucks` and `telemetry` tables!
