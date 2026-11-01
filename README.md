# Task Management Application - Full-Stack Monorepo

**Course:** Advanced Web Development Frameworks (ITUE301) | **Semester:** 5th  
**Student ID:** 24IT098 | **Student Name:** Deep Tandel  

This repository combines the entire full-stack Task Management application into a single unified repository containing both the React frontend and the Express/Node.js backend.

---

## Repository Structure

```text
task-manager-fullstack/
├── student-portfolio/          # React + Vite Frontend Client
│   ├── src/
│   │   ├── components/         # Tasks (with AI Integration), Login, Register, Navbar
│   │   ├── api.js              # Centralized API service layer
│   │   └── App.jsx
│   ├── Dockerfile              # Multi-stage production container image
│   └── package.json
├── task-manager-api/           # Node.js + Express Backend REST API
│   ├── models/                 # Mongoose Data Models (User, Task)
│   ├── middleware/             # JWT Authentication & Validation Middleware
│   ├── aiRoute.js              # AI Description Generator (OpenAI & Gemini + Graceful Fallback)
│   ├── server.js               # Express application entrypoint
│   ├── tests/                  # Automated integration tests (Jest & Supertest)
│   ├── Dockerfile              # Backend container image
│   └── package.json
├── .github/workflows/ci.yml    # Full-Stack Continuous Integration Pipeline
├── docker-compose.yml          # Multi-container orchestration (Frontend, Backend, MongoDB)
├── .gitignore                  # Monorepo ignore rules
└── README.md                   # Project documentation
```

---

## Key Features Implemented

1. **AI API Integration (Practical 13):**
   - Auto-generates concise, actionable task descriptions and priority recommendations using OpenAI / Google Gemini.
   - Built with server-side API key protection and **Graceful Degradation** fallback to keep the app working even if external AI APIs are offline.
2. **Automated CI/CD Pipeline (Practical 12):**
   - Configured via GitHub Actions to automatically run backend test suites and frontend builds on every push to `main`.
3. **Containerization with Docker Compose (Practical 11):**
   - Orchestrates all 3 services (`frontend`, `backend`, `mongodb`) with a single command.
4. **Background Event System (Practical 10):**
   - Asynchronous background notifications using Node.js built-in `EventEmitter`.
5. **In-Memory Caching (Practical 9):**
   - Cache layer using `node-cache` for instant `GET /tasks` responses.
6. **Authentication & Security (Practical 7 & 8):**
   - Password hashing with `bcryptjs`, JWT session tokens, and route protection middleware.

---

## Quick Start Guide

### Option A: Run with Docker Compose (Recommended)
Prerequisite: Docker Desktop running.

```bash
# Build and start all services (Frontend, Backend, MongoDB)
docker compose up --build

# Access services:
# Frontend Client: http://localhost:5173
# Backend REST API: http://localhost:5000
```

### Option B: Run Locally (Without Docker)

1. **Start MongoDB:** Ensure local MongoDB server is running on `mongodb://127.0.0.1:27017`.
2. **Start Backend:**
   ```bash
   cd task-manager-api
   npm install
   # Create .env based on .env.example
   node server.js
   ```
3. **Start Frontend:**
   ```bash
   cd student-portfolio
   npm install
   npm run dev
   ```
   Open `http://localhost:5173/tasks` in your browser.

---

## Running Automated Tests

```bash
cd task-manager-api
npm test
```
