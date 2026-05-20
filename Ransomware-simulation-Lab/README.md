# Ransomware Simulation & Detection Lab using Splunk, Sysmon, and Atomic Red Team

## Objective

Simulate ransomware-style behavior in a controlled Windows homelab environment and detect suspicious activity using Splunk, Sysmon telemetry, and Atomic Red Team methodologies.

This project focused on:
- PowerShell execution monitoring
- ransomware-like file modification behavior
- fake ransom note creation
- suspicious command-line activity
- ransomware indicator detection in Splunk

---

# Lab Environment

## VM1 — SIEM Server
- Splunk Enterprise

## VM2 — Windows Endpoint
- Sysmon
- Splunk Universal Forwarder
- Atomic Red Team
- PowerShell
- Windows Event Logging
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

## Step 1 — Create Test Directory

```powershell
New-Item -Path "C:\AtomicRansomLab" -ItemType Directory -Force
```

---

## Step 2 — Generate Test Files

```powershell
1..20 | ForEach-Object {
    "Test file $_" | Out-File "C:\AtomicRansomLab\file$_.txt"
}
```

---

## Step 3 — Simulate Encryption-Like File Modifications

Safely simulated ransomware behavior by renaming files:

```powershell
Get-ChildItem C:\AtomicRansomLab\*.txt | ForEach-Object {
    Rename-Item $_.FullName ($_.FullName + ".encrypted")
}
```

---

## Step 4 — Create Fake Ransom Note

```powershell
"Your files have been encrypted. Simulation only." | Out-File "C:\AtomicRansomLab\READ_ME.txt"
```

---

## Step 5 — Simulate Suspicious PowerShell Activity

```powershell
powershell.exe -ExecutionPolicy Bypass -NoProfile -Command "Get-ChildItem C:\AtomicRansomLab"
```

This generated:
- Sysmon process creation telemetry
- PowerShell command-line logging
- suspicious execution activity

---

## Step 6 — Simulate Backup Deletion Behavior Safely

Generated ransomware-style telemetry without deleting anything:

```cmd
cmd.exe /c echo vssadmin delete shadows /all /quiet
```

---

# Splunk Detection Queries

## Detect PowerShell Activity

```spl
index=main sourcetype="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational"
| rex field=_raw "Name=[\"']Image[\"']>(?<Image>[^<]+)"
| rex field=_raw "Name=[\"']CommandLine[\"']>(?<CommandLine>[^<]+)"
| search Image="*powershell.exe"
| table _time Image CommandLine
```

---

## Detect Suspicious Backup Deletion Commands

```spl
index=main sourcetype="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational"
| rex field=_raw "Name=[\"']CommandLine[\"']>(?<CommandLine>[^<]+)"
| search CommandLine="*vssadmin*" OR CommandLine="*delete shadows*"
| table _time CommandLine
```

---

## Detect Ransom Note Activity

```spl
index=main sourcetype="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational"
| rex field=_raw "Name=[\"']CommandLine[\"']>(?<CommandLine>[^<]+)"
| search CommandLine="*READ_ME.txt*"
| table _time CommandLine
```

---

# Detection Logic

The detection strategy focused on identifying:
- suspicious PowerShell execution
- ransomware-style command-line behavior
- fake backup deletion activity
- file extension modifications
- ransom note creation attempts

---

# Example Detection Results

Observed:
- PowerShell process execution
- suspicious command-line arguments
- simulated ransomware behaviors
- file modification telemetry

---

# MITRE ATT&CK Mapping

- T1486 — Data Encrypted for Impact
- T1490 — Inhibit System Recovery
- T1059.001 — PowerShell
- T1565 — Data Manipulation

---

# Skills Demonstrated

- SIEM Operations
- Splunk SPL Query Development
- Sysmon Telemetry Analysis
- Ransomware Behavior Analysis
- Endpoint Monitoring
- Threat Detection
- Detection Engineering
- PowerShell Analysis
- MITRE ATT&CK Mapping
- SOC Investigation Workflow

---

# Project Workflow

Ransomware Simulation  
↓  
PowerShell Execution  
↓  
Sysmon Telemetry  
↓  
Splunk Universal Forwarder  
↓  
Splunk SIEM  
↓  
Detection Queries  
↓  
Threat Analysis



# Cleanup

```powershell
Remove-Item C:\AtomicRansomLab -Recurse -Force
```

No permanent system modifications or real encryption were performed during this simulation.
