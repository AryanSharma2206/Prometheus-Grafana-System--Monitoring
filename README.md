# 🖥️ SysMon360 – Real-Time Linux System Monitoring

**SysMon360** is a personal system monitoring dashboard using **Prometheus**, **Node Exporter**, and **Grafana**. It enables real-time visualization of vital Linux system metrics including CPU, memory, disk usage, uptime, and more — all hosted and running locally.

---

## 🛠️ Tech Stack

- **Prometheus** – Time-series database and scraper  
- **Node Exporter** – Exposes system metrics  
- **Grafana** – Dashboard & visualization tool  
- **PromQL** – Query language for Prometheus  
- **Linux Shell**, **YAML**

---

## 📁 Project Structure

```
sysmon360/
│
├── node_exporter/                  # Node Exporter binary & service
├── prometheus/
│   ├── prometheus.yml              # Configuration for scraping
│   └── data/                       # TSDB data
├── grafana/ (optional if needed)
├── README.md
```

---

## 🧱 Architecture Overview

```
                ┌────────────────────────────┐
                │        Your System         │
                │   (Ubuntu/Linux Machine)   │
                └────────────┬───────────────┘
                             │
                             ▼
                ┌────────────────────────────┐
                │      Node Exporter         │
                │ Exposes system metrics     │
                │  → http://localhost:9100   │
                └────────────┬───────────────┘
                             │
                             ▼
                ┌────────────────────────────┐
                │        Prometheus          │
                │ Scrapes & stores metrics   │
                │  → http://localhost:9090   │
                └────────────┬───────────────┘
                             │
                             ▼
                ┌────────────────────────────┐
                │          Grafana           │
                │ Dashboard visualizations   │
                │  → http://localhost:3000   │
                └────────────────────────────┘
```

---

## 🚀 Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/AryanSharma2206/sysmon360
cd sysmon360
```

### 2. Extract Prometheus & Node Exporter

```bash
tar -xvf prometheus-*.tar.gz
tar -xvf node_exporter-*.tar.gz
mv prometheus-* prometheus
mv node_exporter-* node_exporter
```

### 3. Start Node Exporter

```bash
cd node_exporter
./node_exporter
```

### 4. Configure and Start Prometheus

Update `prometheus/prometheus.yml`:

```yaml
scrape_configs:
  - job_name: 'prometheus'
    static_configs:
      - targets: ['localhost:9090']

  - job_name: 'node_exporter'
    static_configs:
      - targets: ['localhost:9100']
```

Then run:

```bash
cd prometheus
./prometheus --config.file=prometheus.yml
```

### 5. Install & Run Grafana

```bash
sudo apt update
sudo apt install -y grafana
sudo systemctl start grafana-server
sudo systemctl enable grafana-server
```

---

## 🌐 Access Interfaces

- **Prometheus** → [http://localhost:9090](http://localhost:9090)  
- **Node Exporter** → [http://localhost:9100](http://localhost:9100)  
- **Grafana** → [http://localhost:3000](http://localhost:3000)  
  *(Default login: `admin` / `admin`)*

---

## 📈 Useful PromQL Queries

```promql
node_cpu_seconds_total
node_memory_MemAvailable_bytes
node_filesystem_avail_bytes
node_load1
rate(node_network_receive_bytes_total[1m])
```

---

## 👨‍💻 Author

**Aryan Sharma**  
B.Tech CSE (AI & DS) | Poornima University  
GitHub: [@AryanSharma2206](https://github.com/AryanSharma2206)  
LinkedIn: [linkedin.com/in/aryan-sharma-a2a240353](https://www.linkedin.com/in/aryan-sharma-a2a240353)  
Location: Jaipur, India
