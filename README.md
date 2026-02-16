#🛡️ Cloud SIEM & Detection Lab (Microsoft Sentinel)

#Objective
To deploy a cloud-native SIEM (Security Information and Event Management) system using Microsoft Sentinel to provide 24/7 visibility into Azure cloud infrastructure. I simulated an "Unauthorized Resource Deletion" attack and tuned detection logic to successfully alert on the event.

#Technologies & Tools Used
-Microsoft Sentinel (SIEM/SOAR)
-Log Analytics Workspace (SOC-Workspace)
-Kusto Query Language (KQL)
-Microsoft Defender for Cloud (Unified SecOps)
-Azure Activity Logs

#Project Walkthrough

#Step 1: Environment Setup
I deployed a Log Analytics Workspace and enabled Microsoft Sentinel to serve as the centralized "brain" for security telemetry.
[Insert Screenshot #1: Sentinel Overview/Workspace Active]

#Step 2: Data Ingestion & Governance
I connected the Azure Activity data source and applied a global Azure Policy to ensure all resource logs are automatically streamed to the SIEM.
[Insert Screenshot #2: Data Connector Status "Connected"]
[Insert Screenshot #3: Policy Assignment & Scope]

#Step 3: Log Verification (KQL)
Using the Kusto Query Language (KQL), I verified that telemetry was flowing correctly from the Azure platform into the workspace.
[Insert Screenshot #4: AzureActivity KQL Results Table]

#Step 4: Custom Detection Rule & Rule Tuning
I created a scheduled analytics rule to detect unauthorized resource changes.
Critical Skill Demonstrated: During testing, I identified that Azure logs were using Success while my initial rule looked for Succeeded. I tuned the KQL logic to account for both, ensuring 100% detection reliability.

[Insert Screenshot #5: Rule General Tab with MITRE Tactics]
[Insert Screenshot #6: Final Tuned KQL Logic]
[Insert Screenshot #7: Validation Passed Screen]

#Step 5: Incident Lifecycle & Verification
I triggered the alert by creating and deleting a test resource group (Testing-Final-Test). The SIEM successfully detected the "attack" and generated an incident in the Microsoft Defender portal.
[Insert Screenshot #8: The "Money Shot" - Triggered Incident in Defender]

Conclusion
This lab demonstrates the end-to-end SOC lifecycle: ingestion, detection engineering, and incident response. Navigating the 2026 migration to the Unified Defender Portal also highlights my ability to adapt to the latest industry standards in SecOps.
