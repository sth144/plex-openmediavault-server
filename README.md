# Plex OpenMediaVault Server

![Build Status](https://img.shields.io/badge/build-manual-inactive)

Docker Compose stacks and configuration for services running on an OpenMediaVault/Plex host.

## Overview
This repository is organized as one folder per service. Most top-level service directories contain their own `docker-compose.yml` and any service-specific configuration under `config/`.

Top-level services:
- `audiobookshelf/`
- `calibre/`
- `gitlab/`
- `joplin-server/`
- `kavita/`
- `litellm/`
- `monitoring/`
- `nextcloud/`
- `nginx/`
- `paperless-ng/`
- `plex/`
- `redisinsight/`

Additional directories:
- `cryze/` (uses `cryze/docker/docker-compose.yml`)
- `jenkins/` (currently empty)

## Requirements
- Docker Engine
- Docker Compose plugin (`docker compose`)
- Linux host with sudo access

## Install
1. Clone the repository.
2. Change into the repo root:

```bash
cd /home/sthinds/Projects
```

## Setup
1. Review each service directory for its configuration and environment files.
2. For services that require secrets, create or update the `.env` files:
   - `joplin-server/.env`
   - `litellm/.env`
   - `nextcloud/.env*`
3. If a service stores state in-repo (for example `kavita/config/` or `paperless-ng/config/db.sqlite3`), avoid destructive commands like `docker compose down -v` unless you intend to wipe data.

## Run
Most services are managed per-directory. Examples below use `plex/`:

Start:
```bash
cd plex
sudo docker compose up -d
```

Stop:
```bash
cd plex
sudo docker compose down
```

Logs:
```bash
cd plex
sudo docker compose logs -f
```

## Notes
- `cryze/` uses a non-standard compose path: `cryze/docker/docker-compose.yml`.
- If you add a new service, create a new top-level directory, add `docker-compose.yml`, keep config under `config/`, and document any special setup in a local `README.md`.

## Build Status Badge
The current badge is a placeholder. If you add CI (GitHub Actions, GitLab CI, etc.), replace it with the provider’s badge URL.
