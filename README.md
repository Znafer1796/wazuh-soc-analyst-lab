SOC Homelab Project
This project demonstrates a self-built Security Operations Center (SOC) lab environment designed to simulate real-world attack and detection scenarios.
🔥 Overview
The lab focuses on monitoring, detecting, and analyzing security events using SIEM, IDS, and endpoint logging tools. It simulates attacker behavior and defensive mechanisms in a controlled environment.
🏗️ Architecture
The lab consists of:
Kali Linux – Attacker machine (Nmap, Metasploit)
Windows 10 – Client endpoint (Sysmon installed)
Windows Server – Active Directory, Group Policy
pfSense – Firewall & network gateway
Wazuh – SIEM for log collection and analysis
Snort – IDS for network-based detection
🔄 Log Flow & Detection
Attacks are launched from Kali Linux
Endpoint activity is logged via Sysmon on Windows 10
Logs are forwarded to Wazuh SIEM
Network traffic is analyzed by Snort
Firewall events are handled by pfSense
🚨 Attack Scenarios
1. Nmap Scan Detection
Command:
nmap -sS <target-ip>
Detection:
Wazuh alert triggered for port scanning
Snort detected suspicious network activity

2. Metasploit Exploitation
Tool: Metasploit Framework
Scenario: Simulated exploitation against target machine
Detection:
Wazuh detected suspicious process activity
Alerts generated from Sysmon logs

🛠️ Tools & Technologies
SIEM: Wazuh
IDS: Snort
Firewall: pfSense
Endpoint Monitoring: Sysmon
OS: Windows Server, Windows 10, Kali Linux
Virtualization: VMware
🧠 Skills Demonstrated
Log analysis and correlation
Alert triage and investigation
Network traffic monitoring
Endpoint detection using Sysmon
Basic incident response workflow
📌 Notes
This is a continuously evolving project. More attack scenarios and screenshots will be added over time.
The goal is to simulate real SOC analyst tasks in a lab environment.
🔗 Author
GitHub: https://github.com/Znafer1796
