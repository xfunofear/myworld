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

## 🔐 Security Observations

During the scan, it was noted that the website does not respond to default WPScan probes without a custom user-agent. This suggests that the server has protections in place to block automated or unauthenticated scanners — a positive sign of basic hardening.

### ✅ Detected Protections
- The default WPScan scan was blocked.
- Only when a custom `User-Agent` header (mimicking a browser) was used, did the scanner retrieve data.
- Certain paths are disabled or return empty responses.

---

## 🛡️ Recommendations for Further Hardening

As a site administrator, you can take additional steps to improve security:

1. **Disable XML-RPC**, unless explicitly required — it's a common attack vector.
2. **Hide WordPress version info** from meta tags and RSS feeds.
3. **Limit plugin exposure**:
   - Restrict access to `/wp-content/plugins/` and `/wp-content/themes/` folders.
   - Disable directory listing on the server.
4. **Enable a Web Application Firewall (WAF)** (e.g. Cloudflare, Wordfence).
5. **Use security headers**, such as:
   - `X-Content-Type-Options: nosniff`
   - `Content-Security-Policy`
   - `Strict-Transport-Security`
6. **Monitor logs** for unusual scanning behavior or IP-based brute-force attempts.

---

By implementing the above, the attack surface can be reduced significantly.


[Back to Projects](../projects.html)

