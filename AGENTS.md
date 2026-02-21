# AGENTS.md

## Repository overview
This repository is a collection of Docker Compose stacks and related configuration for services running on an OpenMediaVault/Plex host. Each top-level folder generally represents a service and contains its own `docker-compose.yml` and any service-specific config or data.

## Layout
Top-level service directories (most have a `docker-compose.yml`):
- `audiobookshelf/`
- `calibre/`
- `gitlab/` (includes `config/` and GitLab SSH host keys)
- `joplin-server/` (includes `.env` and `.envrc`)
- `kavita/` (includes `config/` with SQLite DB files)
- `litellm/` (includes `.env`, `.envrc`, and `schema/schema.prisma`)
- `monitoring/` (includes `config/` for Prometheus/Loki/Promtail/Telegraf/Grafana dashboards)
- `nextcloud/` (includes `Dockerfile`, `.env*` secrets, and `config/`)
- `nginx/` (includes `nginx.conf`)
- `paperless-ng/` (includes `config/db.sqlite3`)
- `plex/`
- `redisinsight/`

Additional directories:
- `cryze/` (contains a README, tools, and its own `docker/docker-compose.yml`)
- `jenkins/` (currently empty)

## Common tasks
Most services are managed per-directory with Docker Compose.

Start a service (example):
```bash
cd plex
sudo docker compose up -d
```

Stop a service:
```bash
cd plex
sudo docker compose down
```

Check logs:
```bash
cd plex
sudo docker compose logs -f
```

## Environment and secrets
Several stacks rely on `.env` files that contain credentials or secrets:
- `joplin-server/.env`
- `litellm/.env`
- `nextcloud/.env*`

Handle these with care. If adding new services, follow the same pattern and avoid committing secrets unless the repo is explicitly private and intended to hold them.

## Data and state
Some stacks keep state directly in this repo (for example `kavita/config/` and `paperless-ng/config/db.sqlite3`). Be cautious with destructive actions like `docker compose down -v` or deleting config directories.

## Adding new services
Preferred pattern:
- Create a new top-level directory named for the service.
- Add `docker-compose.yml` and any config under a `config/` subfolder.
- Add an `.env` file if secrets are required.
- Document any special setup in a `README.md` inside the service directory.

## Notes
If a service has a non-standard compose location (e.g. `cryze/docker/docker-compose.yml`), call it out in its local README so it is easy to find.
