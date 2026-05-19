
# Persistence Detection Lab

## Objective

Simulate Windows persistence using a scheduled task and detect the activity in Splunk using Sysmon telemetry.

---

## Lab Environment

### VM1 — SIEM Server
- Splunk Enterprise

### VM2 — Windows Endpoint
- Sysmon
- Splunk Universal Forwarder
- PowerShell
- Windows Event Logs

---

## Tools Used

- Splunk
- Sysmon
- Splunk Universal Forwarder
- PowerShell
- Windows Task Scheduler
- VirtualBox

---

## Attack Simulation

Created a scheduled task that launches PowerShell at user logon.

```powershell
schtasks /create /tn "UpdaterTask" /tr "powershell.exe -WindowStyle Hidden" /sc onlogon /ru SYSTEM
```

Triggered the scheduled task manually:

```powershell
schtasks /run /tn "UpdaterTask"
```

---

## Detection Query

```spl
index=main sourcetype="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational"
| rex field=_raw "Name=[\"']Image[\"']>(?<Image>[^<]+)"
| rex field=_raw "Name=[\"']CommandLine[\"']>(?<CommandLine>[^<]+)"
| search CommandLine="*schtasks*" OR CommandLine="*powershell*"
| table _time Image CommandLine
```

---

## Cleanup

```powershell
schtasks /delete /tn "UpdaterTask" /f
```

---

## MITRE ATT&CK Mapping

- T1053.005 — Scheduled Task/Job: Scheduled Task
- T1059.001 — PowerShell
- T1547 — Boot or Logon Autostart Execution

---

## Skills Demonstrated

- Persistence detection
- Splunk SPL query development
- Sysmon process analysis
- Windows scheduled task monitoring
- MITRE ATT&CK mapping
- SOC investigation workflow

---

## Project Workflow

Persistence Simulation  
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
