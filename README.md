# 🔐 Wazuh SOC Analyst Lab

## 📌 Overview

This project is a hands-on SOC (Security Operations Center) lab built to simulate real-world monitoring and threat detection using **Wazuh**, **Sysmon**, and Windows environments.

The lab focuses on:

* Log collection & analysis
* Threat detection using custom rules
* Monitoring network activity (Zenmap/Nmap)
* Endpoint visibility with Sysmon

---

## 🏗️ Lab Architecture

* **Wazuh Server** (SIEM)
* **Windows 10 Client** (with Sysmon + Wazuh Agent)
* **Windows Server** (optional - AD environment)
* Network configured via virtual lab (VMware)

---

## ⚙️ Technologies Used

* Wazuh (SIEM & Log Management)
* Sysmon (System Monitoring)
* Windows 10 / Windows Server
* Nmap / Zenmap (Network Scanning)
* Virtualization (VMware)

---

## 🚀 Setup Steps

### 1. Install Wazuh Server

* Deployed Wazuh on Linux
* Accessed Wazuh dashboard via web UI

### 2. Add Agents

* Installed Wazuh Agent on:

  * Windows 10
  * Windows Server
* Connected agents to Wazuh manager

### 3. Install Sysmon

* Installed Sysmon on Windows machine
* Configured logging for:

  * Process creation
  * Network connections
  * File changes

### 4. Log Collection

* Verified logs from:

  * Sysmon
  * Windows Event Logs
  * Network activity

---

## 🔍 Detection Use Cases

### 1. Network Scanning Detection (Zenmap/Nmap)

* Performed scan using Zenmap
* Captured logs in Wazuh
* Created detection rule for:

  * Suspicious network connections
  * Port scanning behavior

### 2. Sysmon Event Monitoring

* Event ID 1: Process Creation
* Event ID 3: Network Connection
* Event ID 11: File Creation

---

## 🧠 Custom Rules (Wazuh)

* Created custom rules to detect:

  * Nmap scanning activity
  * Suspicious processes
  * Unusual network behavior

Example:

```
<rule id="100001" level="10">
  <if_sid>sysmon_event3</if_sid>
  <field name="destination_port">22|80|443</field>
  <description>Possible scanning activity detected</description>
</rule>
```

---

## 📊 Results

* Successfully collected logs from multiple endpoints
* Detected scanning activity from Zenmap
* Visualized events in Wazuh dashboard
* Built basic SOC detection pipeline

---

## 📸 Screenshots

(Add your screenshots here)

* Wazuh dashboard
* Agent status
* Detected alerts
* Sysmon logs

---

## 🎯 Skills Gained

* SIEM deployment (Wazuh)
* Log analysis & correlation
* Threat detection engineering
* Windows monitoring with Sysmon
* Basic SOC operations workflow

---

## 📌 Future Improvements

* Integrate Active Directory logging
* Improve detection rules (reduce false positives)
* Add MITRE ATT&CK mapping
* Automate alert responses

---

## 👤 Author

* Name: (Your Name)
* Role: SOC Analyst (Beginner)
* Field: Cybersecurity / Blue Team

---

## ⭐ Notes

This lab is built for learning purposes and simulates real SOC monitoring scenarios. It can be extended further with advanced threat detection and automation.
