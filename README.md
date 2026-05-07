# Wazuh-FIM-Lab-GRC
# Lab Report: Implementing File Integrity Monitoring (FIM) with Wazuh

## 1. Executive Summary
This lab demonstrates the practical implementation of File Integrity Monitoring (FIM), a critical detective control in modern cybersecurity and GRC (Governance, Risk, and Compliance) strategies. By configuring Wazuh to monitor sensitive directories in real-time, we transition from theoretical risk management to active monitoring.This capability is vital for protecting the Integrity and **Confidentiality of organizational data and meeting regulatory requirements like PCI DSS, HIPAA, and GDPR.

---

## 2. Technical Implementation Steps

### Step 1: Agent Connectivity
The Wazuh agent was successfully installed and connected to the Ubuntu-based Wazuh Manager.
Agent Connection Status(174).png
*Figure 1: Wazuh Agent showing "Running" status and successful connection to the Manager IP.*

### Step 2: Configuring the Detective Control
I modified the `ossec.conf` file to monitor the `SensitiveFiles` directory in real-time. This is where the specific GRC policy is translated into a technical rule.
ossec.conf Configuration(183).png
*Figure 2: Adding the directory path to the <syscheck> section for real-time monitoring.*

### Step 3: Simulating a Risk Event
To verify the control, I created a simulated "Financial Forecast" document and performed unauthorized actions (Modify and Delete).
File Creation and Modification(190).png
*Figure 3: Creating the sensitive document in the monitored Windows directory.*

---

## 3. Results & Monitoring (The Evidence)

### Step 4: Verification via Wazuh Dashboard
The most critical part of the lab was verifying that the Manager captured the events. The dashboard successfully logged the lifecycle of the risk event.
Wazuh Dashboard Alerts(193).png)
*Figure 4: Audit trail showing the file being added, modified, and deleted.*

---

## 4. GRC Analysis & Reflections

### Risk Identification & Analysis
Business Impact: Unauthorized changes to financial documents could lead to significant financial loss, regulatory fines (e.g., SOX non-compliance), and reputational damage with stakeholders.
Risk Quantification: By analyzing Figure 4, we can quantify risk based on frequency. Multiple alerts in a short window indicate a high-probability risk event.

### Control Evaluation
Detective vs. Preventive: While FIM is a detective control (tells us what happened), a complementary preventive control would be restricted NTFS permissions (limiting who can open the file).
Corrective Trigger: If an alert is triggered, a corrective control would be an automated incident response play-book to isolate the host and restore the file from a secure backup.

### Compliance Mapping
Audit Evidence: This implementation provides the "Audit Trail" required by frameworks like **PCI DSS (Req. 11.5)** and **HIPAA**.
Evidence of Integrity: To prove to an auditor that a file was not touched, I would generate a report from the "Inventory" tab showing no "modified" events for the document over the requested audit period.

---
Author: Ebere Emilia Ikechukwu
Lab: Risk Assessment and Management Techniques

