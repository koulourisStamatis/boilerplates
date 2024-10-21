# Prometheus Docker Compose Setup
https://prometheus.io/
This setup uses Docker Compose to run **Prometheus** for collecting and querying metrics.

## Prerequisites

- Docker installed
- Docker Compose installed

## File Structure

Ensure the following structure exists on your host machine:

```plaintext
/
├── docker-compose.yml       # Docker Compose file
└── etc/
    └── prometheus/
        └── prometheus.yaml  # Prometheus configuration file
