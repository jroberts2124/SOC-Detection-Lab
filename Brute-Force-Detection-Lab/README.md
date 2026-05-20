# Brute-Force Detection Lab using Splunk, Sysmon & Atomic Red Team

## Objective

Simulate brute-force authentication activity in a Windows homelab environment and detect repeated failed login attempts using Splunk, Windows Security Logs, Sysmon telemetry, and Atomic Red Team methodologies.

---

# Lab Environment

## VM1 — SIEM Server
- Splunk Enterprise

## VM2 — Windows Endpoint
- Sysmon
- Splunk Universal Forwarder
- Atomic Red Team
- Windows Security Logging
- PowerShell
- VirtualBox

---

# Tools Used

- Splunk
- Sysmon
- Splunk Universal Forwarder
- Atomic Red Team
- PowerShell
- Windows Event Logs
- VirtualBox

---

# Attack Simulation

Used Atomic Red Team concepts aligned to MITRE ATT&CK brute-force techniques and generated repeated failed login attempts to simulate credential guessing activity.

Executed the following PowerShell loop:

```powershell
for ($i=1; $i -le 15; $i++) {
    net use \\localhost\IPC$ /user:FakeUser WrongPassword123
}
```

This generated:
- Windows Security Event ID 4625
- Failed authentication attempts
- Authentication telemetry for SIEM analysis

---

# Sysmon Telemetry Collection

Sysmon was configured to collect:
- process creation activity
- command-line execution
- PowerShell execution telemetry

Forwarded logs to Splunk using Splunk Universal Forwarder.

---

# Detection Query — Brute Force Activity

```spl
index=main EventCode=4625
| bucket _time span=5m
| stats count by _time Account_Name Source_Network_Address
| where count >= 10
```

---

# Detection Logic

The detection identifies:
- repeated failed login attempts
- high-volume authentication failures
- possible brute-force or password spraying activity

The query groups authentication attempts into 5-minute windows and flags suspicious activity when failures exceed a threshold.

---

# Additional Investigation Query

```spl
index=main EventCode=4625
| stats count by Account_Name Source_Network_Address
```

---

# Sysmon PowerShell Detection Query

```spl
index=main sourcetype="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational"
| rex field=_raw "Name=[\"']Image[\"']>(?<Image>[^<]+)"
| rex field=_raw "Name=[\"']CommandLine[\"']>(?<CommandLine>[^<]+)"
| search Image="*powershell.exe"
| table _time Image CommandLine
```

---

# Example Detection Results

Observed:
- repeated failed logon attempts
- Security Event ID 4625 activity
- PowerShell execution telemetry
- authentication event spikes within short timeframes


---

# MITRE ATT&CK Mapping

- T1110 — Brute Force
- T1110.001 — Password Guessing
- T1110.003 — Password Spraying
- T1059.001 — PowerShell

---

# Skills Demonstrated

- SIEM Operations
- Splunk SPL Query Development
- Windows Security Log Analysis
- Sysmon Telemetry Analysis
- Authentication Monitoring
- Threat Detection
- Detection Engineering
- Atomic Red Team Simulation
- MITRE ATT&CK Mapping
- SOC Investigation Workflow

---

# Project Workflow

Attack Simulation  
↓  
Windows Security Logs + Sysmon Telemetry  
↓  
Splunk Universal Forwarder  
↓  
Splunk SIEM  
↓  
Detection Queries  
↓  
Threat Analysis


