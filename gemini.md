# System Resource Monitor

## 0. General Instructions
- **Bilingual Output Required:** All explanations, responses, and technical documentation must be provided in English first, followed by a Korean translation directly below. This applies to all agent interactions and generated content.

## 1. Project Overview
The **System Resource Monitor** is a Flask-based web application designed for real-time monitoring of system resources. It provides a dashboard for visualizing performance metrics and includes functionality to track data over time and generate comprehensive PDF reports.

### 1.1 Key Features
- **Real-time Monitoring:** Tracks CPU, Memory, Disk, Network, Temperature, GPU, and active processes.
- **Data Tracking:** Background worker capable of tracking system stats for a specified duration (default: 5 minutes).
- **PDF Reporting:** Generates detailed PDF reports with matplotlib charts and tabular data.
- **Modern Dashboard:** A web-based interface for visualizing current system state and managing tracking sessions.

### 1.2 Architecture & Technologies
- **Backend:** Python / Flask
- **Monitoring Tools:** `psutil` (general stats), `GPUtil` (GPU), `wmi` / `pywin32` (Windows-specific metrics).
- **Reporting:** `reportlab` (PDF structure) and `matplotlib` (data visualization).
- **Frontend:** HTML/CSS/JS (Vanilla) with real-time API polling.

### 1.3 Repository & Synchronization
- **GitHub Repository:** https://github.com/ease10004-AI/AI-Edu-2.git
- **Branch:** main
- **Synchronization Policy:** All updates should be pushed to the `main` branch of this repository.

## 2. Getting Started
### 2.1 Prerequisites
- Python 3.8 or higher.
- Windows OS (recommended for full hardware monitoring support like Temperature/WMI).

### 2.2 Installation
- Install the required Python packages:
   ```bash
   pip install -r requirements.txt
   ```

### 2.3 Running the Application
- Start the Flask server:
   ```bash
   python app.py
   ```
- Open your browser and navigate to:
   ```
   http://localhost:5000
   ```

## 3. Project Structure
- `app.py`: Main entry point and Flask API server.
- `pdf_generator.py`: Logic for creating PDF reports from tracked data.
- `monitors/`: Modular scripts for individual resource monitoring:
  - `cpu_monitor.py`: CPU usage, frequency, and load.
  - `memory_monitor.py`: RAM and Swap usage.
  - `disk_monitor.py`: Disk I/O and partition usage.
  - `network_monitor.py`: Throughput and interface stats.
  - `gpu_monitor.py`: GPU utilization and memory (NVIDIA focused).
  - `temperature_monitor.py`: Hardware temperature sensors.
  - `process_monitor.py`: Top processes by resource usage.
- `static/` & `templates/`: Frontend assets and dashboard template.
- `reports/`: Automatically created directory where generated PDF reports are stored.

## 4. Development Conventions
### 4.1 Adding New Monitors
- Create a new module in the `monitors/` directory.
- Implement a `get_X_info()` function that returns a dictionary of metrics.
- Import and integrate the new monitor into `get_all_stats()` in `app.py`.

### 4.2 API Design
- The backend follows a RESTful JSON API pattern under the `/api/` prefix.
- All monitoring data should be serializable to JSON.

### 4.3 PDF Generation
- Use `matplotlib` with the 'Agg' backend for thread-safe chart generation.
- Ensure any text intended for the PDF handles encoding correctly (especially for Korean font support in `Malgun`).

## 5. Communication Policy
- **Bilingual Output:** All explanations and responses must be provided in English, followed by a Korean translation below.
