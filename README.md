# ELK Stack for Cybersecurity Education

A complete ELK (Elasticsearch, Logstash, Kibana) stack using Docker Compose, designed for cybersecurity monitoring and telemetry collection. This project supports both macOS and Windows environments and provides practical hands-on experience with security monitoring.

## 📥 Getting Started

### 1. Download the Project

**Option A: Clone with Git (Recommended)**
```bash
git clone <repository-url>
cd ELK-Docker
```

**Option B: Download ZIP**
1. Click the green "Code" button on GitHub
2. Select "Download ZIP"
3. Extract the ZIP file
4. Open terminal/command prompt and navigate to the extracted folder:
   ```bash
   cd path/to/extracted/ELK-Docker
   ```

### 2. Prerequisites

- [Docker Desktop](https://docs.docker.com/get-docker/) installed and running
- Basic familiarity with command line tools

## 🚀 Quick Start

### 3. Start the ELK Stack

```bash
docker compose up -d
```

### 4. Verify the Stack is Running

Check Elasticsearch:
```bash
curl -X GET "localhost:9200"
```

Access Kibana: http://localhost:5601

### 5. Start Collecting Security Telemetry

**For macOS:**
```bash
# Basic security metrics
./scripts/telemetry/cyber_security_mvp.sh

# Enhanced syslog collection
./scripts/telemetry/syslog_mac.sh
```

**For Windows:**
```powershell
# Run in PowerShell as Administrator
.\scripts\telemetry\windows_telemetry.ps1
```

## 📊 What Gets Monitored

The telemetry scripts collect key cybersecurity indicators:

- **Authentication Events**: Failed login attempts
- **Network Activity**: Active TCP connections and processes
- **File System Changes**: New files in temporary directories
- **System Performance**: CPU/load metrics (potential DoS indicators)
- **Process Monitoring**: Network-connected processes

## 🔧 Stack Components

| Service | Port | Purpose |
|---------|------|---------|
| Elasticsearch | 9200 | Data storage and search |
| Kibana | 5601 | Visualization and dashboards |
| Logstash | 514 | Syslog ingestion (TCP/UDP) |

## 📁 Project Structure

```
├── docker-compose.yml          # ELK stack configuration
├── logstash/
│   └── pipeline/
│       └── logstash.conf       # Log processing configuration
├── scripts/
│   ├── telemetry/
│   │   ├── cyber_security_mvp.sh    # macOS security telemetry
│   │   ├── syslog_mac.sh           # macOS syslog collection
│   │   └── windows_telemetry.ps1   # Windows security telemetry
│   └── setup/
│       ├── run-elasticsearch.sh    # Standalone Elasticsearch setup
│       └── syslog_alert.sh         # Alert configuration helper
└── README.md                   # This file
```

## 🛠️ Managing the Stack

**View logs:**
```bash
docker logs -f es01           # Elasticsearch
docker logs -f kibana01       # Kibana
docker logs -f logstash01     # Logstash
```

**Stop/Start services:**
```bash
docker compose down           # Stop all services
docker compose up -d          # Start all services
docker compose restart       # Restart all services
```

**Clean up (removes all data):**
```bash
docker compose down -v
```

## 🎯 Learning Objectives

This project helps you learn:
- Security Information and Event Management (SIEM) concepts
- Real-time security telemetry collection
- Docker-based infrastructure deployment
- Log parsing and data visualization
- Security metric analysis and monitoring

## 🔗 Resources

- [Cyber Desserts Blog Post](https://cyberdesserts.com/lab-building-a-cybersecurity-monitoring-stack-with-elk)
- [ELK Stack Documentation](https://www.elastic.co/guide/index.html)
- [Docker Compose Reference](https://docs.docker.com/compose/)

---

**Note**: This is a development/education environment. For production use, enable authentication, TLS, and proper security hardening.
