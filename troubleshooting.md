# 🐛 Troubleshooting Guide: OwnCloud Docker Setup

This guide provides solutions to common issues encountered while deploying OwnCloud using Docker Compose with Traefik, MariaDB, Redis, and Grafana.

---

## ❌ Error: "Failed to connect to the database"

### 🔍 Symptoms
OwnCloud fails to initialize and shows:
Error while trying to create admin user: Failed to connect to the database:
An exception occurred in driver: SQLSTATE[HY000] [1045]
Access denied for user 'trivers23'@'172.19.0.4' (using password: YES)

### ✅ Fix
- Double-check the database credentials in your `.env` file:
  - `OWNCLOUD_DB_USERNAME`
  - `OWNCLOUD_DB_PASSWORD`
- Ensure that the `OWNCLOUD_DB_HOST` matches the name of the MariaDB service (e.g., `mariadb`)
- Restart Docker after fixing credentials:
  ```bash
  docker-compose down
  docker-compose up -d

  Error: ACME Rate Limit - Too Many Failed Authorizations
  shows: acme: error: 429 :: POST :: https://acme-v02.api.letsencrypt.org/acme/new-order :: too many failed authorizations (5) for "yourdomain.duckdns.org"

This happens when Traefik fails to validate your domain too many times in 1 hour.

Wait at least 60 minutes before retrying.

Make sure:

DuckDNS is correctly pointing to your public IP

Port 80 and 443 are open and forwarded in your router

ERROR: Your domain in traefik.yml matches the one in your .env OwnCloud Web UI Loads but File Upload Fails
 Symptoms:
You can log in but cannot upload or create files.

Log might show permissions errors or missing volumes.

Fix:
Ensure the files volume is mounted correctly:

yaml
volumes:
  - files:/mnt/data
Check ownership of the volume:

bash
docker exec -it owncloud_server bash
ls -l /mnt/data
chown -R www-data:www-data /mnt/data

Restart container:
docker-compose restart owncloud
