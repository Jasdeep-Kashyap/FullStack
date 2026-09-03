🎨 1. Frontend Projects & Resources (React 19 + Vite + TypeScript + Tailwind CSS)

💡 Project 1: Personal Habit & Task Streak Tracker (Level: Beginner)
Objective: Learn state management, components, props, event handling, and TypeScript interfaces.

Features:
Add, edit, and mark daily habits as complete.
Streak counter (e.g., 🔥 5 Days) stored in browser localStorage.
Filter habits by category (Work, Fitness, Learning).
Dynamic progress bar showing completion rate.

Key Skills Learned: useState, useEffect, dynamic Tailwind classes, client-side persistence.

💡 Project 2: Weather & Air Quality Dashboard (Level: Beginner-Intermediate)
Objective: Learn API data fetching, handling loading/error UI states, and responsive styling.

Features:
Search bar for searching cities using a free weather API (e.g., OpenWeatherMap or Open-Meteo).
Current weather card displaying temperature, humidity, wind speed, and weather icon.
Celsius/Fahrenheit toggle button.
5-day forecast card grid styled with Tailwind CSS v4.

Key Skills Learned: async/await in React, component breakdown, conditional rendering (isLoading, isError).

📺 Recommended YouTube Playlists for Frontend
React 19 & TypeScript:
🎓 FreeCodeCamp — React & TypeScript Full Course
🎓 Net Ninja — React & TypeScript Tutorial Series
Tailwind CSS v4 & Modern UI:
🎓 Traversy Media — Tailwind CSS Crash Course
🎓 Web Dev Simplified — Learn Tailwind CSS in 45 Minutes


⚡ 2. Backend Projects & Resources (Fastify + Node.js + TypeScript + Drizzle ORM + PostgreSQL)

💡 Project 1: Simple Bookmark & Note Manager API (Level: Beginner)
Objective: Learn HTTP routing, request parsing, database CRUD operations, and schema validation.

Features:
POST /api/notes – Create a note with title, content, tags, and url (validated via Zod).
GET /api/notes – Get all notes with optional tag filtering (GET /api/notes?tag=work).
PUT /api/notes/:id – Update note content.
DELETE /api/notes/:id – Remove a note.

Key Skills Learned: Fastify request/reply objects, Drizzle ORM db.select(), db.insert(), db.delete(), Zod validation.

💡 Project 2: Expense & Budget Tracker API (Level: Beginner-Intermediate)
Objective: Learn relational database tables, route query parameters, and aggregation queries.

Features:
POST /api/expenses – Log an expense (amount, category, type: income | expense, date).
GET /api/expenses – Fetch transactions within a date range.
GET /api/expenses/summary – Calculate total balance, total income, and spending per category.
Key Skills Learned: Drizzle ORM table definitions, grouping/aggregation queries, route error handling.

📺 Recommended YouTube Playlists for Backend
Fastify API Development:
🎓 Traversy Media — Fastify Crash Course
🎓 Fastify Official Guides — Getting Started with Fastify
PostgreSQL & Drizzle ORM:
🎓 Fireship — Drizzle ORM in 100 Seconds
🎓 FreeCodeCamp — Node.js, Drizzle ORM & PostgreSQL Tutorial
Zod Validation & TypeScript:
🎓 Web Dev Simplified — Learn Zod in 30 Minutes