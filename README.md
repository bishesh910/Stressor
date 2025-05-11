# Stresser (Syslog Flood Script)

This Python script is designed to simulate high-volume syslog traffic by sending custom log messages to a specified syslog server over TCP. It supports concurrent threads and continuous operation, making it useful for testing SIEM ingestion, rate-limiting, or log-processing pipelines.

---

## 🚀 Features

- Sends structured syslog-like log messages to a remote server
- Configurable number of messages and threads
- Supports continuous traffic generation (until manually stopped)
- Logs sent over TCP for reliable delivery

---

## 🛠 Requirements

- Python 3.x
- A reachable syslog server accepting TCP connections on the specified port

---

## 📄 Usage

### 1. Configure the script:

Edit the variables at the bottom of the script:

```python
log_message = "..."         # Your CEF or raw syslog message
syslog_server = "IP_ADDR"   # Destination syslog server IP
port = 514                  # Destination TCP port (default for syslog)
count = 1500                # Number of logs to send per iteration
num_threads = 5             # Number of concurrent threads
````

### 2. Run the script:

```bash
python3 syslog_flood.py
```

Press `Ctrl+C` to stop the script.

---

## 🔁 How It Works

* `send_log_to_syslog`: Sends `count` logs over TCP to the syslog server with a small delay.
* `send_logs_concurrently`: Splits the load across multiple threads.
* `run_infinite_loop`: Continuously sends logs in batches for stress testing or ingestion benchmarking.

---

## ⚠️ Warning

Use responsibly. This script can generate significant traffic and may impact the target system or network. It should only be used in controlled environments (e.g., labs or test networks).

---

## 📌 Example Log Format

The included log message follows the [CEF (Common Event Format)](https://community.microfocus.com/cyberres/productdocs/w/arcsighttips/22170/cef-the-common-event-format-log-management) used by many security appliances like F5 ASM.

---

## 👤 Author

Created by **bishesh910**.
