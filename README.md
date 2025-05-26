# OwnCloud Docker Setup

This repository documents the full deployment of my self-hosted OwnCloud server using Docker Compose. The setup includes reverse proxying with Traefik (for HTTPS), database support via MariaDB, caching with Redis, and monitoring with Grafana and Promtail.

---

##  Features

- OwnCloud cloud storage via Docker
- HTTPS automatically configured with Traefik and Let's Encrypt
- Real-time monitoring via Grafana + Promtail
- Redis caching for performance improvements
- External domain support via DuckDNS
- Secure environment for personal or business use

---

##  Tech Stack

- **OwnCloud** – File hosting and cloud storage
- **Docker & Docker Compose** – Container orchestration
- **Traefik** – Reverse proxy and automatic HTTPS
- **MariaDB** – MySQL-compatible database backend
- **Redis** – Caching backend for OwnCloud
- **Grafana** – Monitoring dashboards
- **Promtail** – Log aggregation for Grafana
- **DuckDNS** – Free dynamic DNS service

---

## Folder Structure

```text
owncloud-docker-setup/
├── docker-compose.yml
├── .env.example
├── traefik/
│   └── traefik.yml
├── grafana/
│   └── dashboards/
├── docs/
│   ├── setup-instructions.md
│   ├── troubleshooting.md
│   └── architecture.png
├── README.md
