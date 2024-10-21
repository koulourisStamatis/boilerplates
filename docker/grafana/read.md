# Grafana Docker Compose Setup

This setup uses Docker Compose to run **Grafana** for visualizing metrics and logs. Grafana allows you to connect to various data sources, including Prometheus, to build and share dashboards. For more information about Grafana, visit the official website: [https://grafana.com/](https://grafana.com/).

## Prerequisites

- Docker installed
- Docker Compose installed

## File Structure

The recommended file structure for this setup:

```plaintext
/
├── docker-compose.yml       # Docker Compose file
└── etc/
    └── grafana/
        └── grafana.ini      # Grafana configuration file (optional)
