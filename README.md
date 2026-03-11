<div align="center">

# 🔍 Splunk SIEM Integration with Sophos Central

![Type](https://img.shields.io/badge/Type-SIEM%20Integration-blue?style=for-the-badge)
![Splunk](https://img.shields.io/badge/Platform-Splunk%20Enterprise-black?style=for-the-badge&logo=splunk&logoColor=white)
![Sophos](https://img.shields.io/badge/Endpoint-Sophos%20Central-red?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)

> A hands-on SIEM deployment integrating Splunk Enterprise with Sophos Central for real-time malware threat visibility, centralized log collection, dashboard reporting, and automated high-severity alerting.

</div>

---

## 📌 Project Overview

This project demonstrates the deployment of **Splunk Enterprise** and its integration with **Sophos Central** for centralized security event collection, monitoring, and alerting. The setup enables real-time visibility into malware threats and security alerts, with custom dashboards and automated email notifications.

| Field | Details |
|---|---|
| **SIEM Platform** | Splunk Enterprise (Trial) |
| **Event Source** | Sophos Central Endpoint Protection |
| **Integration Method** | Sophos SIEM Script → Syslog (CEF) → Splunk UDP 514 |
| **Environment** | Isolated local lab — personally owned systems |

---

## 🏗️ Lab Environment

| Component | Role |
|---|---|
| **Splunk Enterprise** | SIEM platform — log ingestion, dashboards, alerting |
| **Sophos Central** | Endpoint protection and security event source |
| **Sophos SIEM Script** | API-to-syslog bridge (CEF format) |
| **Network** | Local lab / isolated testing environment |

---

## 🔬 Integration Architecture

```
Sophos Central API
       ↓
Sophos SIEM Integration Script (config.ini)
       ↓
Syslog Output — CEF Format — UDP 514
       ↓
Splunk Enterprise — Log Ingestion
       ↓
Dashboards + Automated Alerts
```

---

## 📋 Deployment Phases

### Phase 1 — Splunk Installation
- Installed Splunk Enterprise Trial on Windows/Linux host
- Accessed Splunk Web via `https://localhost:8000`
- Verified successful login with admin account

📸 `screenshots/splunk enterproce.png`

---

### Phase 2 — Sophos Central API Configuration
- Registered Sophos Central Trial account
- Created API credentials:

| Credential | Purpose |
|---|---|
| Client ID | API authentication identity |
| Client Secret | API authentication secret |
| Tenant ID | Sophos tenant identifier |
| API Region URL | Regional endpoint for API calls |

- Stored credentials securely in integration config file

📸 `screenshots/API Credentials management sophos.png` · `screenshots/sophos central dashboard.png` · `screenshots/sophos health check.png`

---

### Phase 3 — SIEM Integration
- Downloaded Sophos SIEM Integration Script from GitHub
- Configured `config.ini` with API credentials, syslog output (CEF format), and Splunk syslog port (UDP 514)
- Verified logs were successfully ingested into Splunk

📸 `screenshots/siem.py.png` · `screenshots/siem integration script and terminal.png`

---

### Phase 4 — Dashboards & Alerting

#### Dashboard 1 — Blocked Malware Events
```spl
index=* sourcetype="syslog" "Event::Threat"
| stats count by deviceUserName, filePath, severity
| sort - count
```
📸 `screenshots/blocked malware.png`

#### Dashboard 2 — Top Users with Security Alerts
```spl
index=* sourcetype="syslog" "Event::Alert"
| stats count by deviceUserName
| sort - count
```
📸 `screenshots/top users with alerts.png`

#### Automated Alert
- **Trigger:** High-severity Sophos Threat events
- **Action:** Email notification to security administrator

---

## 🛠️ Challenges & Troubleshooting

| Challenge | Resolution |
|---|---|
| **API Authentication** | Careful setup of Client ID and Client Secret required |
| **Syslog Binding** | Configured Splunk to bind and listen on UDP 514 |
| **Event Parsing** | Ensured CEF-format logs were correctly recognized by Splunk |

---

## 📄 Report

| File | Description |
|---|---|
| [`splunk-report.pdf`](splunk-report.pdf) | Full integration report with configuration details and evidence |

> **Note:** PDF files will download rather than preview directly on GitHub.

---

## 🧠 Security Concepts Demonstrated

- Centralized log collection and aggregation
- API-based security tool integration
- Event correlation and CEF format parsing
- Threat visualization via custom SPL dashboards
- Automated alerting for high-severity incidents
- Hands-on SIEM deployment and troubleshooting

---

## 📈 Professional Relevance

This project directly demonstrates skills relevant to:

| Role | Relevant Skills |
|---|---|
| **SOC Analyst** | Log monitoring, alert triage, dashboard analysis |
| **Security Analyst** | Threat detection, event correlation, reporting |
| **SIEM Engineer** | Splunk deployment, syslog integration, SPL queries |
| **Threat Detection Engineer** | Real-time alerting, endpoint event ingestion |

---

## ⚖️ Ethical Statement

> All testing and integration were performed in a **controlled lab environment** on personally owned systems for educational and professional development purposes only.
>
> No production systems, real user data, or unauthorized networks were accessed at any point during this project.