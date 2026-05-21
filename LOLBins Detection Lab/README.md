# LOLBins Detection Lab using Splunk, Sysmon, and Atomic Red Team

## Objective

Simulate Living Off the Land Binary (LOLBins) abuse in a Windows homelab environment and detect suspicious process execution using Splunk, Sysmon telemetry, and Atomic Red Team methodologies.

This project focused on:
- legitimate Windows binary abuse
- command-line monitoring
- process execution telemetry
- Splunk detection engineering
- MITRE ATT&CK-aligned threat detection

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

Simulated LOLBins activity using legitimate Windows binaries commonly abused by attackers.

---

## Test 1 — certutil.exe

```cmd
certutil.exe -hashfile C:\Windows\System32\notepad.exe SHA256
```

Simulated:
- suspicious certutil usage
- file interaction activity
- LOLBin execution telemetry

---

## Test 2 — bitsadmin.exe

```cmd
bitsadmin /list
```

Simulated:
- background transfer utility execution
- potential malware staging behavior

---

## Test 3 — rundll32.exe

```cmd
rundll32.exe shell32.dll,Control_RunDLL
```

Simulated:
- suspicious rundll32 execution
- LOLBin process activity

---

## Test 4 — regsvr32.exe

```cmd
regsvr32.exe /?
```

Simulated:
- regsvr32 process execution
- command-line telemetry generation

---

# Sysmon Telemetry Collection

Sysmon was configured to collect:
- process creation events
- command-line execution
- parent-child process relationships

Telemetry was forwarded to Splunk using Splunk Universal Forwarder.

---

# Detection Logic

The detection strategy focused on identifying:
- suspicious usage of legitimate Windows binaries
- unusual command-line execution
- attacker tradecraft using trusted system tools
- potential defense evasion behavior

---

# Example Detection Results

Observed:
- certutil process execution
- bitsadmin process activity
- rundll32 command-line telemetry
- regsvr32 execution events

Example output:

```text
Image = C:\Windows\System32\certutil.exe
CommandLine = certutil.exe -hashfile C:\Windows\System32\notepad.exe SHA256
```

---

# MITRE ATT&CK Mapping

- T1218 — System Binary Proxy Execution
- T1059 — Command and Scripting Interpreter
- T1105 — Ingress Tool Transfer
- T1564 — Hide Artifacts

---

# Skills Demonstrated

- SIEM Operations
- Splunk SPL Query Development
- Sysmon Telemetry Analysis
- LOLBins Detection
- Threat Hunting
- Endpoint Monitoring
- Detection Engineering
- Windows Process Analysis
- MITRE ATT&CK Mapping
- SOC Investigation Workflow

---

# Project Workflow

LOLBins Execution  
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

---

# Screenshots to Include

- certutil.exe execution
- bitsadmin.exe execution
- Splunk LOLBins detection query
- Detection results showing process execution
- Command-line telemetry results
- Sysmon event logs

---

# Cleanup

No permanent system modifications or malicious payloads were executed during this simulation.
