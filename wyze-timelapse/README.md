# Wyze Timelapse Stack

This stack builds the app from `/usr/local/src/wyze-timelapse` and runs it as a local container.

## Start
```bash
docker-compose up -d --build
```

The UI will be available at `http://<host>:8095`.

## Data
- Image archive: `/home/sthinds/data/Images`
- App config: `./config/config.json`

The service writes date-partitioned snapshots and applies retention cleanup from the app configuration.
