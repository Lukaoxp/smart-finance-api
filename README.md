# smart-finance-api

[![Go Version](https://img.shields.io/badge/Go-1.26+-blue)](https://go.dev/)
[![Project Status](https://img.shields.io/badge/status-WIP-yellow)](https://github.com/lukaoxp/smart-finance-api)

Production-grade personal finance backend in Go. Built around observability, resilience, and AI integration.

---

## Architecture

```
smart-finance-api/
├── cmd/api/
│   └── main.go              # Entry point, graceful shutdown
├── internal/
│   ├── auth/                # JWT from scratch (no third-party libs)
│   ├── transactions/        # Domain logic + repository pattern
│   ├── insights/            # AI integration with circuit breaker
│   └── middleware/          # Rate limiting, logging, auth
├── migrations/              # Versioned SQL via golang-migrate
├── Dockerfile               # Multi-stage build
└── docker-compose.yml       # Local dev: API + PostgreSQL + Redis
```

**Key decisions:**

* **JWT from scratch** — manual implementation of `header.payload.signature` (HMAC-SHA256). No jwt-go, no third-party libs.
* **Circuit breaker around AI API** — when Gemini is slow, return financial data without the insight (no 500). Graceful degradation.
* **Redis dual-purpose** — rate limiting (sliding window, 100 req/min per user) + AI response cache (TTL: 7 days).
* **Prometheus metrics** — latency (p50/p99), cache hit rate, AI cost tracking, circuit breaker state.
* **Graceful shutdown** — waits for in-flight requests (30s timeout) before terminating.

---

## Features

| Feature | Status |
|---|---|
| Auth (JWT from scratch, refresh tokens) | Planned |
| Transactions CRUD | Planned |
| Budgets & Goals | Planned |
| Redis rate limiting (sliding window) | Planned |
| AI-powered spending insights (Gemini API) | Planned |
| Circuit breaker around AI API | Planned |
| Prometheus metrics | Planned |
| Structured logging (log/slog) | Planned |
| Docker multi-stage build | Planned |
| GitHub Actions CI/CD | Planned |
| Google Cloud Run deploy | Planned |

---

## Running locally

> Development environment not set up yet. Coming in Week 3.

Prerequisites:
- Go 1.26+
- Docker & Docker Compose

```bash
# Coming soon
docker-compose up
```

---

## Tests

```bash
# Coming soon
go test ./...
```

---

## Roadmap

- [ ] Week 1–4: Go fundamentals, auth, database, migrations
- [ ] Week 5–8: CRUD, Redis caching & rate limiting
- [ ] Week 9–12: AI integration, circuit breaker, Prometheus, deploy
- [ ] Week 13–16: Full observability, monitoring
- [ ] Week 17–24: Production hardening, interviews

---

Built by [Lucas Carturani](https://github.com/lukaoxp)
