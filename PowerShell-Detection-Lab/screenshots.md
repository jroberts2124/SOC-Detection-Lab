
<img width="975" height="755" alt="image" src="https://github.com/user-attachments/assets/fd2920a3-342c-4a94-9e9a-b672719c905d" />

This screenshot shows multiple attack simulations from Invoke-AtomicRedTeam executing MITRE ATT&CK technique `T1059.003`, which focuses on Windows Command Shell abuse. The tests simulate attacker behaviors such as creating and running batch scripts, executing suspicious `cmd.exe` commands, launching programs like `calc.exe`, and mimicking ransomware-related activity to generate realistic security telemetry. These actions produce logs that can be collected by Sysmon and analyzed in Splunk Enterprise to build and test SOC detection rules.


<img width="1236" height="537" alt="image" src="https://github.com/user-attachments/assets/d1446a21-6f6b-49d3-981e-9a1614ae3c4e" />



This screenshot shows a custom Splunk Enterprise query detecting PowerShell-related activity from Sysmon logs. The query extracts the executable path (`Image`) and command-line arguments (`CommandLine`) from raw Sysmon events and filters for processes containing `powershell`, allowing suspicious PowerShell executions to be identified. The results confirm that PowerShell activity was successfully generated on the endpoint, collected through the Splunk Universal Forwarder, indexed in Splunk, and detected through your custom SPL detection rule.


<img width="1065" height="305" alt="image" src="https://github.com/user-attachments/assets/0b5c1f4b-8c06-4bf9-baa1-2e0b63526b18" />











