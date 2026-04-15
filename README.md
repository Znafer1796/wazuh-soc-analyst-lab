# 🔐 Wazuh SOC Analyst Lab (AD + pfSense + Sysmon + Nmap)

## 📌 Overview

This project is a full SOC (Security Operations Center) lab simulating a real enterprise environment with **Active Directory**, network segmentation, endpoint monitoring, and threat detection using **Wazuh SIEM**.

The lab is designed to:

* Monitor Windows endpoints in an AD domain
* Detect network scanning activities (Nmap/Zenmap)
* Collect and analyze logs using Wazuh
* Apply centralized policies using Group Policy (GPO)

---

## 🏗️ Lab Architecture

### 🔹 Components:

* **Kali Linux** → Wazuh Server (SIEM)
* **pfSense** → Firewall / Network segmentation
* **Windows Server** → Active Directory Domain Controller
* **Windows 10 Client** → Domain-joined endpoint
* **Attacker Machine (Kali)** → Nmap scanning

### 🔹 Network:

* Internal LAN managed by pfSense
* All machines communicate through pfSense
* Wazuh collects logs from endpoints via agents

---

## ⚙️ Technologies Used

* Wazuh (SIEM & Log Management)
* Sysmon (Windows Event Monitoring)
* Active Directory (Windows Server)
* Group Policy (GPO)
* pfSense (Firewall)
* Nmap / Zenmap (Network Scanning)
* Kali Linux
* VMware (Virtual Lab)

---

## 🚀 Implementation Steps

### 1. Network Setup (pfSense)

* Configured WAN & LAN interfaces
* Enabled internal network communication
* Allowed controlled outbound access

### 2. Active Directory Setup

* Installed AD DS on Windows Server
* Promoted to Domain Controller
* Created domain users & joined Windows 10 client

### 3. GPO Configuration

* Applied Group Policy to:

  * Enable logging
  * Configure security settings
  * Prepare endpoints for monitoring

### 4. Wazuh Deployment (Kali)

* Installed Wazuh Server on Kali Linux
* Accessed Wazuh Dashboard
* Connected agents from Windows machines

### 5. Sysmon Installation

* Installed Sysmon on Windows 10
* Configured to log:

  * Process creation (Event ID 1)
  * Network connections (Event ID 3)
  * File creation (Event ID 11)

### 6. Log Collection

* Verified logs from:

  * Sysmon
  * Windows Event Logs
  * Security events from AD

---

## 🔍 Detection Use Case: Nmap Scan

### Scenario:

An attacker machine (Kali Linux) performs a network scan using Nmap/Zenmap.

### Detection Flow:

1. Nmap scan initiated
2. Sysmon logs network connections (Event ID 3)
3. Logs forwarded to Wazuh
4. Wazuh triggers alert based on custom rule

---

## 🧠 Custom Wazuh Rules

Example rule to detect scanning activity:

```xml
<rule id="100001" level="10">
  <if_sid>sysmon_event3</if_sid>
  <field name="destination_port">22|80|443|3389</field>
  <description>Possible Nmap scanning activity detected</description>
</rule>
```

---

## 📊 Results

* Successfully deployed a SOC monitoring environment
* Integrated AD + endpoint logging
* Detected Nmap scanning activity in real-time
* Visualized alerts in Wazuh dashboard

---

## 📸 Screenshots

(Add your screenshots here)

* Wazuh dashboard alerts
* Agent status (connected)
* Sysmon logs
* Nmap scan results
* pfSense network configuration

---

## 🎯 Skills Demonstrated

* SIEM deployment (Wazuh)
* Windows Active Directory administration
* Log analysis & threat detection
* Network security (pfSense)
* Endpoint monitoring with Sysmon
* Detection engineering (custom rules)

---

## 📌 Future Improvements

* Add MITRE ATT&CK mapping
* Improve detection rules (reduce false positives)
* Add brute-force detection (RDP/SSH)
* Integrate alert automation (SOAR)

---

## 👤 Author

* Name: Nguyễn Thế Thái(Znafer)
* Role: SOC Analyst (Entry-level)
* Field: Cybersecurity / Blue Team

---

## ⭐ Notes

This lab simulates a real enterprise SOC environment including domain infrastructure, endpoint monitoring, and attack detection. It is designed for learning and practical cybersecurity experience.
