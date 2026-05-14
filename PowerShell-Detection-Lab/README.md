# PowerShell Detection Lab

## Objective
Simulate PowerShell-based attack activity and detect malicious execution using Splunk and Sysmon telemetry.

---

## Tools Used
- Splunk
- Sysmon
- Splunk Universal Forwarder
- Atomic Red Team
- PowerShell
- Windows 10 VM

---

## Lab Setup

VM1:
- Splunk Enterprise

VM2:
- Sysmon
- Splunk Universal Forwarder
- Atomic Red Team

---

## Attack Simulation

Executed PowerShell commands designed to mimic attacker behavior and generate endpoint telemetry.

Example:
```powershell
powershell.exe -ExecutionPolicy Bypass
