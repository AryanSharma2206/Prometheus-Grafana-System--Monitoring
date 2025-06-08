# 🔧 SysMon360 – Real-Time Linux System Monitoring with Prometheus & Grafana

Monitor your system’s health in real time with **Prometheus**, **Node Exporter**, and **Grafana**. This project visualizes vital system metrics like CPU, memory, disk usage, uptime, and more — all from your local Linux environment.

---

## 👨‍💻 Author

**Aryan Sharma**  
B.Tech CSE (AI & DS) | DevOps Enthusiast  
📍 Jaipur, India  
🔗 [LinkedIn Profile](https://www.linkedin.com/in/aryan-sharma-a2a240353/)

---

## 📌 Features

- Collects system metrics via **Node Exporter**
- Stores and queries metrics using **Prometheus**
- Builds beautiful, customizable dashboards with **Grafana**
- Real-time visualizations for:
  - CPU, RAM, and disk usage
  - Uptime and system load
  - Network I/O and processes

---

## 🏗️ Architecture Diagram

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

## ⚙️ Technologies Used

- Prometheus
- Node Exporter
- Grafana
- Linux Shell
- YAML
- PromQL (Prometheus Query Language)

---

## 🚀 Setup Instructions

### 1. Clone the Repository
```bash
git clone https://github.com/AryanSharma2206/sysmon360
cd sysmon360
```

### 2. Extract Binaries
```bash
tar -xvf prometheus-*.tar.gz
tar -xvf node_exporter-*.tar.gz
mv prometheus-* prometheus
mv node_exporter-* node_exporter
```

### 3. Run Node Exporter
```bash
cd node_exporter
./node_exporter
```

### 4. Run Prometheus
Edit `prometheus/prometheus.yml` with your scrape configs:
```yaml
scrape_configs:
  - job_name: 'prometheus'
    static_configs:
      - targets: ['localhost:9090']

  - job_name: 'node_exporter'
    static_configs:
      - targets: ['localhost:9100']
```

Then start:
```bash
cd prometheus
./prometheus --config.file=prometheus.yml
```

### 5. Install & Start Grafana
```bash
sudo apt install -y grafana
sudo systemctl start grafana-server
sudo systemctl enable grafana-server
```

### 6. Access Dashboards

- Prometheus UI → [http://localhost:9090](http://localhost:9090)  
- Node Exporter → [http://localhost:9100](http://localhost:9100)  
- Grafana → [http://localhost:3000](http://localhost:3000)  
  *(Default login: `admin` / `admin`)*

---

## 📊 Sample Dashboard Screenshot

> _Include screenshots of your Grafana dashboard here_  
> *(You can paste here once uploaded to the repo or linked externally)*

---

## 📈 Example Queries (PromQL)

```promql
node_cpu_seconds_total
node_memory_MemAvailable_bytes
node_filesystem_avail_bytes
node_load1
rate(node_network_receive_bytes_total[1m])
```

---

## 📢 Connect With Me

Feel free to connect with me for project insights, internships, or collaboration!

🔗 [LinkedIn – Aryan Sharma](https://www.linkedin.com/in/aryan-sharma-a2a240353/)

---

## 📄 License

MIT License © Aryan Sharma
