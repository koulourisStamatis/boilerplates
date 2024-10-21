# Node Exporter Docker Compose Setup

This setup uses Docker Compose to run **Prometheus Node Exporter**, which is used for exposing hardware and OS-level metrics of a host machine. These metrics can be scraped by Prometheus and visualized in Grafana. For more information about Node Exporter, visit the official Node Exporter page: [https://prometheus.io/docs/guides/node-exporter/](https://prometheus.io/docs/guides/node-exporter/).

## Prerequisites

- Docker installed
- Docker Compose installed

## File Structure

The following structure can be used to organize your project:

```plaintext
/
└── docker-compose.yml       # Docker Compose file for Node Exporter
