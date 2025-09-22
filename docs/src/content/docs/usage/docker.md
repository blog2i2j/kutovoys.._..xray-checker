---
title: Docker
description: Running Xray Checker with Docker and Docker Compose
---

### Basic Docker Usage

Pull the latest image:

```bash
docker pull kutovoys/xray-checker
```

Run with minimal configuration:

```bash
docker run -d \
  -e SUBSCRIPTION_URL=https://your-subscription-url/sub \
  -p 2112:2112 \
  kutovoys/xray-checker
```

### Full Docker Configuration

```bash
docker run -d \
  -e SUBSCRIPTION_URL=https://your-subscription-url/sub \
  -e SUBSCRIPTION_UPDATE=true \
  -e SUBSCRIPTION_UPDATE_INTERVAL=300 \
  -e PROXY_CHECK_INTERVAL=300 \
  -e PROXY_CHECK_METHOD=ip \
  -e PROXY_TIMEOUT=30 \
  -e PROXY_IP_CHECK_URL=https://api.ipify.org?format=text \
  -e PROXY_STATUS_CHECK_URL=http://cp.cloudflare.com/generate_204 \
  -e PROXY_DOWNLOAD_URL=https://proof.ovh.net/files/1Mb.dat \
  -e PROXY_DOWNLOAD_TIMEOUT=60 \
  -e PROXY_DOWNLOAD_MIN_SIZE=51200 \
  -e SIMULATE_LATENCY=true \
  -e XRAY_START_PORT=10000 \
  -e XRAY_LOG_LEVEL=none \
  -e METRICS_HOST=0.0.0.0 \
  -e METRICS_PORT=2112 \
  -e METRICS_PROTECTED=true \
  -e METRICS_USERNAME=custom_user \
  -e METRICS_PASSWORD=custom_pass \
  -e METRICS_INSTANCE=node-1 \
  -e METRICS_PUSH_URL=https://push.example.com \
  -e METRICS_BASE_PATH=/xray/monitor \
  -e RUN_ONCE=false \
  -p 2112:2112 \
  kutovoys/xray-checker
```

### Docker Compose

Basic docker-compose.yml:

```yaml
services:
  xray-checker:
    image: kutovoys/xray-checker
    environment:
      - SUBSCRIPTION_URL=https://your-subscription-url/sub
    ports:
      - "2112:2112"
```

Full docker-compose.yml:

```yaml
services:
  xray-checker:
    image: kutovoys/xray-checker
    environment:
      - SUBSCRIPTION_URL=https://your-subscription-url/sub
      - SUBSCRIPTION_UPDATE=true
      - SUBSCRIPTION_UPDATE_INTERVAL=300
      - PROXY_CHECK_INTERVAL=300
      - PROXY_CHECK_METHOD=ip
      - PROXY_TIMEOUT=30
      - PROXY_IP_CHECK_URL=https://api.ipify.org?format=text
      - PROXY_STATUS_CHECK_URL=http://cp.cloudflare.com/generate_204
      - PROXY_DOWNLOAD_URL=https://proof.ovh.net/files/1Mb.dat
      - PROXY_DOWNLOAD_TIMEOUT=60
      - PROXY_DOWNLOAD_MIN_SIZE=51200
      - SIMULATE_LATENCY=true
      - XRAY_START_PORT=10000
      - XRAY_LOG_LEVEL=none
      - METRICS_HOST=0.0.0.0
      - METRICS_PORT=2112
      - METRICS_PROTECTED=true
      - METRICS_USERNAME=custom_user
      - METRICS_PASSWORD=custom_pass
      - METRICS_INSTANCE=node-1
      - METRICS_PUSH_URL=https://push.example.com
      - METRICS_BASE_PATH=/xray/monitor
      - RUN_ONCE=false
    ports:
      - "2112:2112"
    restart: unless-stopped
```

### Docker Network Configuration

Custom network setup:

```yaml
services:
  xray-checker:
    networks:
      - monitoring
    ports:
      - "2112:2112"

networks:
  monitoring:
    name: monitoring-network
```

### Docker Health Checks

Add health check to docker-compose.yml:

```yaml
services:
  xray-checker:
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:2112/health"]
      interval: 30s
      timeout: 10s
      retries: 3
      start_period: 40s
```

### Download Check Method Example

Example using the download check method:

```bash
docker run -d \
  -e SUBSCRIPTION_URL=https://your-subscription-url/sub \
  -e PROXY_CHECK_METHOD=download \
  -e PROXY_DOWNLOAD_URL=https://proof.ovh.net/files/1Mb.dat \
  -e PROXY_DOWNLOAD_TIMEOUT=60 \
  -e PROXY_DOWNLOAD_MIN_SIZE=51200 \
  -p 2112:2112 \
  kutovoys/xray-checker
```

This configuration will:

- Download a test file through each proxy
- Consider the check successful if at least 10MB is downloaded
- Timeout after 5 minutes
- Test actual data transfer performance through proxies
