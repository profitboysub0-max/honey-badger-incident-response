# honey-badger-incident-response
Real-world SOC-style investigation detecting unauthorized remote access. Correlated processes with network activity, identified malicious software, and executed full incident response lifecycle.

🐝 Project Honey Badger – Security Incident Response Project
📌 Overview

Honey Badger is a real-world cybersecurity incident response project where a suspicious remote-control executable was detected, analyzed, and removed from a Windows system.

This project demonstrates hands-on skills in threat detection, network analysis, and incident response using native Windows tools.

🚨 Incident Summary
Observed abnormal system behavior (unauthorized mouse movement and navigation)
Identified suspicious outbound network traffic to an unknown external IP
Traced activity to a non-standard executable: client32.exe

Located file in:

C:\Users\<user>\AppData\Roaming\WinHPC
🔍 Investigation Process
1. Process Enumeration
tasklist
2. Network Analysis
netstat -ano
3. Process Correlation
tasklist | findstr <PID>
4. Path Identification
wmic process where name="client32.exe" get ExecutablePath
🧠 Key Findings
Executable was associated with NetSupport (remote control software)
Established connection to external IP over a non-standard port
Behavior consistent with unauthorized remote access activity
🛠️ Remediation Steps
Terminated malicious process:
taskkill /PID <PID> /F
Removed malicious directory:
AppData\Roaming\WinHPC
Verified no persistence:
Startup programs
Scheduled tasks
Registry autoruns
✅ Outcome
Eliminated unauthorized remote access
Restored full system control
Verified no reinfection after reboot
🧰 Tools Used
Windows Command Prompt
tasklist
netstat
wmic
Task Manager
🧠 Skills Demonstrated
Incident Response (IR Lifecycle)
Threat Detection & Triage
Network Traffic Analysis
Endpoint Process Investigation
System Remediation
🔐 Lessons Learned
Executables running from AppData/Roaming should be treated as high-risk
Correlating process IDs with network connections is critical
Early detection prevents deeper compromise
