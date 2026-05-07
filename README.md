# Wazuh-FIM-Lab-GRC
# Lab Report: Implementing File Integrity Monitoring (FIM) with Wazuh

## 1. Executive Summary
This lab demonstrates the practical implementation of File Integrity Monitoring (FIM), a critical detective control in modern cybersecurity and GRC (Governance, Risk, and Compliance) strategies. By configuring Wazuh to monitor sensitive directories in real-time, we transition from theoretical risk management to active monitoring. This capability is vital for protecting the Integrity and Confidentiality of organizational data and meeting regulatory requirements like PCI DSS, HIPAA, and GDPR.
## Lab Environment

| Component | Technology |
|---|---|
| SIEM Platform | Wazuh |
| Wazuh Manager OS | Ubuntu Server |
| Endpoint OS | Windows 11 |
| Virtualization Platform | VMware Workstation |
| Monitoring Capability | File Integrity Monitoring (FIM) |
| Attack Simulation | File Modification & Deletion |

---

## 2. Technical Implementation Steps

### Step 1: Agent Connectivity
The Wazuh agent was successfully installed and connected to the Ubuntu-based Wazuh Manager.
![Agent Connection Status](Agent%20Connection%20Status(174).png)
*Figure 1: Wazuh Agent showing "Running" status and successful connection to the Manager IP.*

### Step 2: Configuring the Detective Control
I modified the `ossec.conf` file to monitor the `SensitiveFiles` directory in real-time. This is where the specific GRC policy is translated into a technical rule.
![ossec.conf Configuration](ossec.conf%20Configuration(183).png)
*Figure 2: Adding the directory path to the `<syscheck>` section for real-time monitoring.*

### Step 3: Simulating a Risk Event
To verify the control, I created a simulated "Financial Forecast" document and performed unauthorized actions (Modify and Delete).
![File Creation and Modification](File%20Creation%20and%20Modification(190).png)
*Figure 3: Creating the sensitive document in the monitored Windows directory.*

---

## 3. Results & Monitoring (The Evidence)

### Step 4: Verification via Wazuh Dashboard
The most critical part of the lab was verifying that the Manager captured the events. The dashboard successfully logged the lifecycle of the risk event.
![Wazuh Dashboard Alerts](Wazuh%20Dashboard%20Alerts(193).png)
*Figure 4: Audit trail showing the file being added, modified, and deleted.*

---

## 4. GRC Analysis & Reflections

### Risk Identification & Analysis
**Business Impact:** Unauthorized changes to financial documents could lead to significant financial loss, regulatory fines (e.g., SOX non-compliance), and reputational damage with stakeholders.
**Risk Quantification:** By analyzing Figure 4, we can quantify risk based on frequency. Multiple alerts in a short window indicate a high-probability risk event.

### Control Evaluation
**Detective vs. Preventive:** While FIM is a detective control (tells us what happened), a complementary preventive control would be restricted NTFS permissions (limiting who can open the file).
**Corrective Trigger:** If an alert is triggered, a corrective control would be an automated incident response play-book to isolate the host and restore the file from a secure backup.

### Compliance Mapping
**Audit Evidence:** This implementation provides the "Audit Trail" required by frameworks like **PCI DSS (Req. 11.5)** and **HIPAA**.
**Evidence of Integrity:** To prove to an auditor that a file was not touched, I would generate a report from the "Inventory" tab showing no "modified" events for the document over the requested audit period.

### Tools & Technologies Used
- Wazuh SIEM & XDR Platform
- Ubuntu Server (Wazuh Manager)
- Windows 11 (Monitored Endpoint)
- VMware Workstation
- File Integrity Monitoring (FIM)
- PowerShell
- Sysmon
- ossec.conf Configuration File
- Linux Command Line Interface (CLI)

 ### Key Skills Demonstrated
 - Security Information and Event Management (SIEM)
- File Integrity Monitoring (FIM)
- Endpoint Monitoring and Detection
- Risk Assessment and Analysis
- Governance, Risk, and Compliance (GRC)
- Security Control Evaluation
- Incident Detection and Monitoring
- Windows and Linux System Administration
- Security Alert Analysis
- Compliance Mapping (PCI DSS, HIPAA, GDPR)
- Audit Trail Validation
- Cybersecurity Documentation and Reporting

### Lessons Learned
- Learned how to deploy and configure Wazuh Manager and Agents in a virtualized lab environment.
- Gained practical experience implementing File Integrity Monitoring (FIM) as a detective security control.
- Understood the importance of centralized logging and real-time alert monitoring in cybersecurity operations.
- Learned how unauthorized file modifications can impact business operations, compliance posture, and data integrity.
- Improved understanding of the relationship between detective, preventive, and corrective security controls.
- Developed hands-on experience analyzing security alerts and validating audit evidence through the Wazuh Dashboard.
- Recognized the importance of proper endpoint configuration, agent connectivity, and monitoring policies in a SOC environment.
- Strengthened documentation, reporting, and technical communication skills through structured lab reporting.
  
---

## 5. Conclusion

This lab successfully demonstrated the implementation of File Integrity Monitoring (FIM) using Wazuh in a virtualized SOC environment. The project highlighted how centralized monitoring, real-time alerting, and audit trails support both cybersecurity operations and regulatory compliance requirements. Through this implementation, practical experience was gained in SIEM monitoring, endpoint visibility, risk analysis, and security control evaluation.

---

Author: Ebere Emilia Ikechukwu
Lab: Risk Assessment and Management Techniques

