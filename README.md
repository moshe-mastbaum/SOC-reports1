# SOC Weekly Report -- README

**Version:** 1.3\
**Prepared by:** Security Operations Center (SOC)\
**Classification:** Internal Use Only

## 🧭 Purpose

This README provides context and structure for the SOC weekly report
included in this repository.

## 📂 Structure

    /incidents/          Detailed incident timelines
    /alerts/             Raw SIEM alert exports
    /threat-intel/       IOC feeds and intel notes
    /system-health/      Monitoring & log-source health checks
    /graphs/             Visual charts (PNG/PDF)
    /summary.md          Executive summary

## 📄 Executive Summary

High-level overview of major incidents, trends, and the organization's
security posture.

## 🔥 Incident Handling Summary

-   Incident ID\
-   Description\
-   Assets affected\
-   Severity (Critical/High/Medium/Low)\
-   Actions taken: Triage → Containment → Eradication → Recovery\
-   Escalations (if any)

**Example Event:**\
- *INC-2025-1043*: Unusual failed login attempts from a service account.
Root cause: misconfigured script. Classified as False Positive.

## 🛡 Security Events Overview

Includes: - Total alerts\
- Volume by severity\
- Top alert sources\
- Spikes or anomalies

## 🧠 Threat Intelligence Highlights

-   Relevant IOCs\
-   Blocked domains/IPs\
-   Campaigns impacting the sector\
-   New critical CVEs

## 🩺 SIEM & Monitoring Health

-   Log source connectivity\
-   Missing agents\
-   Delayed ingestion\
-   SIEM query performance

## 🔍 Forensic Investigation Notes

-   Evidence summary\
-   IOC list\
-   Process execution timeline\
-   Persistence mechanisms

## 📏 Compliance & Policy Deviations

-   Excessive permissions\
-   VPN anomalies\
-   Non‑compliant systems\
-   Missing security patches

## 🚀 Recommendations

-   Hardening actions\
-   New SIEM rules\
-   Blocking traffic\
-   User awareness activities

## 📧 Contact

**SOC Team:** security-operations@company.local\
24/7 response for critical issues.
