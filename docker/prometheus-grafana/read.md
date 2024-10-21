# Monitoring Stack Docker Compose Setup

This Docker Compose setup brings together **Prometheus**, **Grafana**, **Node Exporter**, **cAdvisor**, and an **Alpine** container. These services work together to monitor your system and containers, collect metrics, and visualize them using Grafana.

## Services

### 1. **Prometheus**
Prometheus is responsible for scraping and storing time-series metrics from various endpoints.

- **Image**: `prom/prometheus:latest`
- **Ports**: Exposes Prometheus on `9090`.
- **Volumes**:
  - `C:/etc/prometheus:/config`: Mounts your Prometheus configuration file from the host machine.
  - `prometheus-data:/prometheus`: Named volume for storing Prometheus data.
- **Command**: Starts Prometheus using the configuration file at `/config/prometheus.yaml`.

Access Prometheus at [http://localhost:9090](http://localhost:9090).

### 2. **Grafana**
Grafana is used to visualize the metrics scraped by Prometheus and other sources.

- **Image**: `grafana/grafana-oss:latest`
- **Ports**: Exposes Grafana on `3000`.
- **Volumes**:
  - `grafana-data:/var/lib/grafana`: Named volume to store Grafana dashboards and configurations.

Access Grafana at [http://localhost:3000](http://localhost:3000). Default login credentials are `admin/admin`.
Import template 1860
### 3. **Node Exporter**
Node Exporter collects hardware and OS metrics from the host system, such as CPU, memory, and disk usage.

- **Image**: `quay.io/prometheus/node-exporter:v1.8.2`
- **Ports**: Exposes Node Exporter on `9100`.
- **Volumes**:
  - `/proc:/host/proc:ro`: Mounts the `/proc` directory for host metrics in read-only mode.
  - `/sys:/host/sys:ro`: Mounts the `/sys` directory for hardware information in read-only mode.
- **Command**: Runs Node Exporter with the root filesystem path set to `/host`.

Access Node Exporter metrics at [http://localhost:9100/metrics](http://localhost:9100/metrics).

### 4. **cAdvisor**
cAdvisor monitors container resource usage and system performance.

- **Image**: `gcr.io/cadvisor/cadvisor:v0.50.0`
- **Ports**: Exposes cAdvisor on `8080`.
- **Volumes**:
  - `/var/run:/var/run:ro`: Mounts necessary runtime files.
  - `/sys:/sys:ro`: Mounts system directories for gathering hardware information.
  - `/var/lib/docker:/var/lib/docker:ro`: Mounts Docker storage for container metrics.
- **Devices**:
  - `/dev/kmsg`: Provides access to kernel messages, required for cAdvisor.
- **Privileged Mode**: cAdvisor runs in privileged mode to access host metrics.

Access cAdvisor at [http://localhost:8080](http://localhost:8080).

### 5. **Alpine**
Alpine is a lightweight container that can be used as a utility container for running basic commands or for debugging purposes.

- **Image**: `alpine:latest`
- **Command**: Starts an interactive shell (`/bin/sh`).
- **TTY**: Enables keeping the container running interactively.

You can access the Alpine container using:

```bash
docker exec -it alpine /bin/sh
