---
layout: default
title: WPScan Audit
---

# 🔍 WPScan – WordPress Vulnerability Scan

## 🎯 Target:
**https://www.depravebhp.pl**

## 🛠 Tools Used:
- Kali Linux (VirtualBox)
- WPScan
- GitHub (report and publishing)

## ⚙️ Scan Parameters:


wpscan --url https://www.depravebhp.pl \
  --user-agent "Mozilla/5.0" \
  --enumerate vp,vt,u \
  --api-token YOUR_API_TOKEN \
  --output wynik_scanowania.txt
## 📋 Key Findings:
✅ WordPress version: 6.8 (latest)

⚠️ Plugins detected:

Elementor v3.28.3 (latest: 3.28.4)

WooCommerce v9.8.1 (latest: 9.8.2)

Google Site Kit v1.150.0 (latest: 1.151.0)

⚠️ XML-RPC interface enabled: /xmlrpc.php

⚠️ MU-Plugins directory visible

⚠️ WP Cron accessible: /wp-cron.php

✅ Theme: Astra v4.10.0 (latest: 4.10.1)

✅ Server: LiteSpeed

📁 Exported Output:
Scan result was saved as wynik_scanowania.txt and uploaded to this repository.

[See the results of scanning](wynik_scanowania.txt)

[Back to Projects](projects.html)

