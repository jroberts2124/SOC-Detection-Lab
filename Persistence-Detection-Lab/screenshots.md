<img width="975" height="102" alt="image" src="https://github.com/user-attachments/assets/1fc781a4-1bdf-4ec9-a4f8-f85b46e8280e" />

This screenshot shows a simulated persistence attack being executed through Invoke-AtomicRedTeam using the Windows `schtasks` utility. The command creates a scheduled task named `UpdaterTask` that launches PowerShell in a hidden window with `SYSTEM` privileges whenever a user logs on, which is a common persistence technique used by attackers. The task is then manually executed with `schtasks /run`, confirming the persistence mechanism was successfully created and triggered on the system.

<img width="975" height="301" alt="image" src="https://github.com/user-attachments/assets/07b3c2e8-89eb-4db8-b81b-12352da14181" />

This screenshot shows a custom Splunk Enterprise query detecting suspicious scheduled task activity from Sysmon logs. The query extracts command-line data from Sysmon events and filters for `schtasks` commands, which are commonly used by attackers to establish persistence on compromised systems. The results reveal the creation and execution of a scheduled task named `UpdaterTask` that launches hidden PowerShell commands with `SYSTEM` privileges, demonstrating a simulated persistence attack successfully detected in Splunk.

<img width="975" height="397" alt="image" src="https://github.com/user-attachments/assets/9e11d845-2183-4e73-a6b9-214a1e66e5a5" />


This screenshot shows a detailed Sysmon event captured in Splunk Enterprise after a scheduled task was executed on the endpoint. The event logs the command `schtasks.exe /run /tn UpdaterTask`, confirming that the persistence task named `UpdaterTask` was manually triggered on the system. The log also shows that the parent process was `powershell.exe`, demonstrating how PowerShell was used to execute a scheduled task persistence technique commonly associated with attacker behavior.

<img width="975" height="294" alt="image" src="https://github.com/user-attachments/assets/8c78ef3a-8b73-4777-aae2-17507ffe3ba1" />

This screenshot shows a Sysmon event in Splunk Enterprise capturing the creation of a malicious-style scheduled task using `schtasks.exe`. The logged command creates a task named `UpdaterTask` that launches hidden PowerShell with `SYSTEM` privileges at user logon, which is a common persistence technique used by attackers to maintain access on a compromised machine. The event also shows that the command was executed through `powershell.exe`, demonstrating how PowerShell and scheduled tasks can be combined to simulate persistence behavior in a SOC detection lab.






