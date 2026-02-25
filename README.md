# 🔍 Splunk SIEM Integration with Sophos Central

## 📌 Project Overview

This project demonstrates the deployment of **Splunk Enterprise** and its integration with **Sophos Central** for centralized security event collection, monitoring, and alerting. The setup enables real-time visibility into malware threats and security alerts, with dashboards and automated notifications.

---

# 🏗 Lab Environment

| Component | Role |
|------------|--------|
| Splunk Enterprise | SIEM platform |
| Sophos Central | Endpoint protection & event source |
| Network | Local lab / isolated testing environment |

---

# 🔹 Phase 1 – Splunk Installation

- Installed Splunk Enterprise Trial on Windows/Linux host
- Accessed Splunk Web via: `https://localhost:8000`
- Verified successful login with admin account

📸 Evidence: Splunk Web login dashboard screenshot

---

# 🔹 Phase 2 – Sophos Central API Configuration

- Registered Sophos Central Trial account
- Created API credentials:
  - Client ID
  - Client Secret
  - Tenant ID
  - API Region URL
- Stored credentials in integration config file

---

# 🔹 Phase 3 – SIEM Integration

- Downloaded Sophos SIEM Integration Script from GitHub
- Configured `config.ini` with:
  - API credentials
  - Syslog output (CEF format)
  - Targeted Splunk syslog port (UDP 514)
- Verified logs were successfully ingested

---

# 🔹 Phase 4 – Dashboards & Reporting

## Dashboards Created

1. **Blocked Malware Events**
```spl
index=* sourcetype="syslog" "Event::Threat"
| stats count by deviceUserName, filePath, severity
| sort - count
```

2. **Top Users with Security Alerts**
```spl
index=* sourcetype="syslog" "Event::Alert"
| stats count by deviceUserName
| sort - count
```

## Alerts

- Trigger: High-severity Sophos Threat events  
- Action: Email notification to security administrator

📸 Evidence: Dashboard screenshots with sample event counts

---

# 🔹 Challenges & Troubleshooting

- **API Authentication:** Careful setup of Client ID/Secret was required  
- **Syslog Binding:** Allowed Splunk to bind to UDP 514  
- **Event Parsing:** Ensured logs were correctly recognized in CEF format  

---

# 🧠 Security Concepts Demonstrated

- Centralized log collection and aggregation  
- Event correlation and parsing  
- Threat visualization via dashboards  
- Automated alerting for high-severity incidents  
- Hands-on troubleshooting of SIEM integration  

---

# 📈 Professional Relevance

Demonstrates skills for roles such as:

- SOC Analyst  
- Security Analyst  
- SIEM Engineer  
- Threat Detection / Monitoring Engineer  

Highlights:

- Enterprise SIEM deployment  
- Endpoint event integration  
- Proactive security monitoring  
- Alerting & dashboard configuration  

---

# 🔐 Ethical Statement

All testing and integration were performed in a controlled lab environment on personally owned systems for educational and professional development purposes.
