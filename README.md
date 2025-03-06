# Cowrie Honeypot Analysis

## 📌 Overview
This project sets up and analyzes a **Cowrie honeypot** to observe SSH brute-force attacks. The goal is to understand attack patterns, collect credential attempts, and explore forensic analysis using Cowrie logs.

## 🔧 Setup & Installation
Follow the steps in [setup.md](setup.md) to:
- Install Cowrie in a virtual machine
- Configure networking for external access
- Start Cowrie and monitor incoming SSH attempts

## 🎯 Attack Simulation
To simulate real-world attacks, I used **Hydra** to brute-force the honeypot. The command used:
```bash
hydra -l root -P rockyou.txt ssh://<honeypot-ip>:port
```

## 📊 Findings & Log Analysis
See [analysis.md](analysis.md) for detailed findings. Key observations:
- Most common credentials attempted
- IP addresses of attackers (private IPs for simulations, but could be public)
- No SSH client fingerprint detected when using Hydra (as expected)
- If an attack comes from inside a private network, it could indicate a compromised internal machine

## 📂 Repository Structure
```
📂 cowrie-honeypot-test
│── 📜 README.md          # Overview of the project
│── 📜 setup.md           # Step-by-step guide to configure Cowrie
│── 📜 analysis.md        # Key findings from log analysis
│── 📂 logs/              # Example logs
```

## 🚀 Next Steps
- Use ELK Stack / Splunk to visualize attack trends
- Deploy Cowrie on a VPS for real-world attack monitoring

