# Database Management Platform (RBAC Enabled)

## Overview
A full‑stack database management web application featuring Role‑Based Access Control (RBAC), comprehensive auditing, and an intuitive UI. It enables secure creation, retrieval, administration, and governance of data while ensuring full traceability of user actions.

Built with:
- Spring Boot (Auth, RBAC, persistence, auditing, JWT)
- Next.js + React + Tailwind CSS + Shadcn UI (interactive UI)
- MySQL (Storing app data)
- Nginx (reverse proxy / consolidation layer)
- Docker Compose (multi‑service orchestration)

## Key Features
- User / Role / Permission management (RBAC)
- Secure authentication & JWT (access + refresh)
- Database entity browsing & CRUD (target database connection)
- Operation auditing & activity analytics
- SQL Editor & execution with safety controls
- Data export tools (e.g. CSV)
- Dashboard & usage insights (heatmaps, charts, stats)
- Granular CORS & security configuration

## Related Services
- Backend: [db-management-be](https://github.com/ilias363/db-management-be)
- Frontend: [db-management-fe](https://github.com/ilias363/db-management-fe)

## Quick Start (All-in-One with Docker)
### Prerequisites
- Docker & Docker Compose
- (Optional) Make sure ports 80, 3000, 8080, 3307 are free

### 1. Clone
```
git clone https://github.com/ilias363/db-manager-app.git

cd db-manager-app

git clone https://github.com/ilias363/db-management-be.git
git clone https://github.com/ilias363/db-management-fe.git
```

### 2. Create Environment File
Copy the provided `.env.example` file to `.env` at the repository root (next to `docker-compose.yml`) and fill in the required values as needed:
```
cp .env.example .env
```

### 3. Build & Run
```
docker compose build
docker compose up -d
```

### 4. Access
- Application (UI): http://localhost
- Backend (exposed via proxy rules): http://localhost/api
- MySQL (host): 127.0.0.1:3307 (user: root / password: $PRIMARY_DB_PASSWORD)

### 5. Logs & Lifecycle
```
docker compose logs -f backend
docker compose logs -f frontend

docker compose down        # stop & remove containers
docker compose down -v     # also remove volume (resets DB)
```

## Local Development (Without Docker)
### Clone Repositories
```
git clone https://github.com/ilias363/db-manager-app.git

cd db-manager-app

git clone https://github.com/ilias363/db-management-be.git
git clone https://github.com/ilias363/db-management-fe.git
```

### Backend

Setup `application.properties` for DB connection & JWT secret.

```
cd db-management-be
./mvnw spring-boot:run
```
Runs at http://localhost:8080

### Frontend
```
cd db-management-fe
cp env.production.example .env
# Set NEXT_PUBLIC_API_URL=http://localhost:8080

npm install
npm run dev
```
UI at http://localhost:3000
