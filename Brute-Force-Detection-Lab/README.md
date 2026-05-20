# Brute-Force Detection Lab

## Objective

Simulate brute-force authentication activity in a Windows environment and detect repeated failed login attempts using Splunk and Windows Security Event Logs.

---

# Lab Environment

## VM1 — SIEM Server
- Splunk Enterprise

## VM2 — Windows Endpoint
- Sysmon
- Splunk Universal Forwarder
- Windows Security Logging
- PowerShell
- VirtualBox

---

# Tools Used

- Splunk
- Sysmon
- Splunk Universal Forwarder
- PowerShell
- Windows Event Logs
- VirtualBox

---

# Attack Simulation

Simulated repeated failed login attempts to generate brute-force authentication telemetry.

Executed the following PowerShell loop:

```powershell
for ($i=1; $i -le 15; $i++) {
    net use \\localhost\IPC$ /user:FakeUser WrongPassword123
}
```

This generated multiple:
- Windows Security Event ID 4625
- Failed authentication attempts

---

# Detection Query

```spl
index=main EventCode=4625
| bucket _time span=5m
| stats count by _time Account_Name Source_Network_Address
| where count >= 10
```

---

# Detection Logic

The query identifies:
- multiple failed logins
- repeated authentication failures
- suspicious login activity within a short timeframe

This behavior is commonly associated with:
- brute-force attacks
- password spraying
- credential guessing

---

# Additional Investigation Query

```spl
index=main EventCode=4625
| stats count by Account_Name Source_Network_Address
```

---

# Example Detection Results

Observed:
- repeated failed logins
- multiple authentication attempts
- Security Event ID 4625 activity

Example output:

```text
EventCode = 4625
Account_Name = FakeUser
Source_Network_Address = 127.0.0.1
```

---

# MITRE ATT&CK Mapping

- T1110 — Brute Force
- T1110.001 — Password Guessing
- T1110.003 — Password Spraying

---

# Skills Demonstrated

- SIEM Operations
- Splunk SPL Query Development
- Windows Security Log Analysis
- Authentication Monitoring
- Threat Detection
- Detection Engineering
- MITRE ATT&CK Mapping
- SOC Investigation Workflow

---

# Project Workflow

Brute-Force Simulation  
↓  
Windows Security Logs  
↓  
Splunk Universal Forwarder  
↓  
Splunk SIEM  
↓  
Detection Query  
↓  
Threat Analysis

---

# Screenshots to Include

- Failed login simulation execution
- Splunk brute-force detection query
- Detection results showing Event ID 4625
- Statistics showing repeated failed authentication attempts

---

# Cleanup

No permanent system modifications were made during this lab simulation.
