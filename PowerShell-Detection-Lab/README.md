# PowerShell Detection Lab

## Objective

Simulate suspicious PowerShell activity on a Windows endpoint and detect the execution using Sysmon telemetry in Splunk.

---

# Lab Environment

## VM1 — SIEM Server
- Splunk Enterprise

## VM2 — Endpoint System
- Sysmon
- Splunk Universal Forwarder
- Atomic Red Team
- Windows 10

---

# Tools Used

- Splunk
- Sysmon
- Splunk Universal Forwarder
- Atomic Red Team
- PowerShell
- VirtualBox

---

# Attack Simulation

Simulated suspicious PowerShell execution to generate endpoint telemetry.

Example commands:

```powershell
powershell.exe -ExecutionPolicy Bypass
```

```powershell
powershell.exe -NoProfile
```

---

# Sysmon Detection Query

```spl
index=main sourcetype="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational"
| rex field=_raw "Name=[\"']Image[\"']>(?<Image>[^<]+)"
| rex field=_raw "Name=[\"']CommandLine[\"']>(?<CommandLine>[^<]+)"
| search Image="*powershell.exe"
| table _time Image CommandLine
```

---

# Example Detection Results

The query successfully detected:
- PowerShell execution
- command-line arguments
- execution timestamps

Example:

```text
Image = C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
CommandLine = powershell.exe -ExecutionPolicy Bypass
```

---

# MITRE ATT&CK Mapping

- T1059.001 — PowerShell

---

# Skills Demonstrated

- SIEM Operations
- SPL Query Development
- Sysmon Telemetry Analysis
- Endpoint Monitoring
- Threat Detection
- Detection Engineering
- Windows Event Logging

---

# Project Workflow

Attack Simulation
↓
Sysmon Telemetry
↓
Splunk Universal Forwarder
↓
Splunk SIEM
↓
Detection Query
↓
Threat Analysis
