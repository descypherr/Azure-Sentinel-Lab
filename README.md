# 🛡️ Cloud SIEM & Detection Lab: Microsoft Sentinel 

## Executive Summary
This project involved the end-to-end deployment of **Microsoft Sentinel** (SIEM) and **Microsoft Defender for Cloud** to secure a live Azure environment. The primary goal was to establish deep visibility into administrative actions and engineer custom detection logic to identify unauthorized resource deletions, simulating a common insider threat or credential compromise scenario.

---

## Technical Stack
* **SIEM/SOAR:** Microsoft Sentinel
* **Log Management:** Log Analytics Workspace (SOC-Workspace)
* **Governance:** Azure Policy (Activity Log Streaming)
* **Detection Engineering:** Kusto Query Language (KQL)
* **Incident Response:** Unified Microsoft Defender Portal (Unified SecOps)

---

## Project Walkthrough

### 1. Infrastructure & Governance
I deployed a **Log Analytics Workspace (SOC-Workspace)** in the South Africa North region to serve as the central repository for security data. To ensure persistent monitoring, I utilized **Azure Policy** to automatically stream all subscription-level Activity Logs to the SIEM, ensuring 100% visibility of administrative actions.
Screenshots:
[Setup Validation](https://github.com/descypherr/Azure-Sentinel-Lab/blob/main/screenshots/1.%20Setup.png)
[Policy Assignment](https://github.com/descypherr/Azure-Sentinel-Lab/blob/main/screenshots/2.%20Policy.png)

### 2. Telemetry Verification
Before building detection rules, I performed manual log verification using **KQL**. This ensured the "heartbeat" of the system was active and that data was being ingested correctly from the Azure platform.
Screenshots:
[Log Verification][(https://github.com/descypherr/Azure-Sentinel-Lab/blob/main/screenshots/1.%20Setup.png](https://github.com/descypherr/Azure-Sentinel-Lab/blob/main/screenshots/3.%20Log%20Verification.png))

### 3. Detection Engineering & Rule Tuning
I engineered a custom Analytic Rule, **"Unauthorized Resource Changes,"** to monitor for critical resource deletions.

* **Rule Tuning:** During testing, I identified a discrepancy where logs were flagged with an `ActivityStatusValue` of `Success`, whereas the initial rule logic only looked for `Succeeded`. I updated the KQL logic to account for both, significantly reducing **False Negatives** and ensuring 100% detection reliability.

![Rule Configuration](4. Rule General.png)
![KQL Logic](5. Rule Logic.png)
![Validation](6. Validation.png)

### 4. Attack Simulation & Incident Triage
I simulated an unauthorized deletion of a resource group (`Testing-final-test`). The system successfully generated a **Medium-severity Incident** in the Defender portal. I then triaged the incident to verify the attacker's identity (Caller) and the source IP address.

![Attack Simulation](7. The Attack.png)
![Detected Incident](8. The Alert.png)

---

## Professional Takeaways
* **Detection Efficacy:** Identified and resolved a critical log schema discrepancy (`Success` vs `Succeeded`) to prevent missed alerts in a production environment.
* **Unified SecOps:** Gained hands-on experience with the 2026 migration to the **Microsoft Defender Unified Portal**, demonstrating adaptability to current industry standards.
* **Governance at Scale:** Demonstrated how to use Azure Policy to enforce security logging standards across a cloud environment.
