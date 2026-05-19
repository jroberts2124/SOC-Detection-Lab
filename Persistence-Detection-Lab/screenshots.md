<img width="975" height="102" alt="image" src="https://github.com/user-attachments/assets/1fc781a4-1bdf-4ec9-a4f8-f85b46e8280e" />

This screenshot shows a simulated persistence attack being executed through Invoke-AtomicRedTeam using the Windows `schtasks` utility. The command creates a scheduled task named `UpdaterTask` that launches PowerShell in a hidden window with `SYSTEM` privileges whenever a user logs on, which is a common persistence technique used by attackers. The task is then manually executed with `schtasks /run`, confirming the persistence mechanism was successfully created and triggered on the system.

<img width="975" height="301" alt="image" src="https://github.com/user-attachments/assets/07b3c2e8-89eb-4db8-b81b-12352da14181" />

This screenshot shows a custom Splunk Enterprise query detecting suspicious scheduled task activity from Sysmon logs. The query extracts command-line data from Sysmon events and filters for `schtasks` commands, which are commonly used by attackers to establish persistence on compromised systems. The results reveal the creation and execution of a scheduled task named `UpdaterTask` that launches hidden PowerShell commands with `SYSTEM` privileges, demonstrating a simulated persistence attack successfully detected in Splunk.



