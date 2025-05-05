# 🔐 Small Business Network Simulation with Security and Attack Blocking (Cisco Packet Tracer)

## 🧩 Project Overview

This project demonstrates a simple business network topology built in Cisco Packet Tracer. It includes basic security configurations such as:

- Static IP addressing
- Remote SSH access to the router
- Detection of a simulated DoS attack
- Blocking the attacker's computer using an Access Control List (ACL)

---
### IP Addressing:

| Device        | IP Address      | Role                |
|---------------|------------------|---------------------|
| PC1           | 192.168.1.10     | Regular user        |
| PC2           | 192.168.1.11     | Regular user        |
| PC3           | 192.168.1.12     | Simulated attacker  |
| Router G0/0   | 192.168.1.1      | Default gateway     |

---

## ⚙️ Router Configuration

### 1. Basic settings:

```bash
enable
configure terminal
hostname xfunofearRouter
ip domain-name xfunofear.com
