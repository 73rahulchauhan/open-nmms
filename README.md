# Network Monitoring and Management System

## Overview
This repository contains a **comprehensive network monitoring and management system** designed for **real-time monitoring, alerting, and management** of network nodes and resources. The system integrates **SNMP, Prometheus, Grafana, and WireGuard** to provide detailed visibility into network performance, security, and system health.

## Features
✅ **Real-time Monitoring** – Track CPU usage, memory, disk space, network traffic, and node health.  
✅ **SNMP Integration** – Collect and analyze network device metrics.  
✅ **Prometheus & Grafana Dashboards** – Visualize system performance and generate alerts.  
✅ **Secure VPN (WireGuard)** – Ensure secure communication between nodes.  
✅ **Custom Node Management** – Add, remove, and configure nodes dynamically.  
✅ **Logging & Alerting** – Detect anomalies and receive alerts for critical events.  

## Tech Stack
- **Prometheus** – Data collection and alerting  
- **Grafana** – Interactive dashboards  
- **SNMP** – Device monitoring  
- **WireGuard** – VPN for secure access  
- **Docker & Kubernetes** – Deployment and scalability  

## Prerequisites
Before setting up the system, ensure you have the following installed:
- **Docker & Docker Compose**
- **Prometheus & Grafana**
- **SNMP & WireGuard** (optional for VPN security)

## Installation
Clone the repository:
```bash
# Clone the repo
git clone https://github.com/73rahulchauhan/open-nmms.git
cd network-monitoring-system
```

Run the system using Docker Compose:
```bash
# Start all services
docker-compose up -d
```

## Configuration
### **Prometheus Configuration**
Modify `prometheus.yml` to add SNMP devices:
```yaml
scrape_configs:
  - job_name: 'snmp_devices'
    static_configs:
      - targets:
        - '192.168.1.1:161'
        - '192.168.1.2:161'
    metrics_path: /snmp
    params:
      module: ["if_mib"]
```
Restart Prometheus to apply changes:
```bash
docker restart prometheus
```

### **Grafana Dashboard Setup**
1. Open Grafana: `http://localhost:3000`
2. Login with **admin/admin** (change password after login)
3. Add a new data source: Select **Prometheus** and set URL as `http://prometheus:9090`
4. Import a pre-configured dashboard (`dashboard.json` provided in this repo)

## Monitoring & Security
- Use **Grafana alerts** to trigger notifications for unusual network behavior.
- Enable **WireGuard VPN** for securing connections between monitored nodes.
- Use **Prometheus Alertmanager** to send alerts via email, Slack, or Telegram.

## Stopping Services
To stop all containers:
```bash
docker-compose down
```

## Future Enhancements
🚀 AI-based anomaly detection  
🚀 Enhanced security with firewall policies  
🚀 Automated configuration via Ansible  

---
**Contributors**: [Your Name](https://github.com/your-username)  
**License**: MIT  

