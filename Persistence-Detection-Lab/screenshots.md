<img width="975" height="102" alt="image" src="https://github.com/user-attachments/assets/1fc781a4-1bdf-4ec9-a4f8-f85b46e8280e" />

This screenshot shows a simulated persistence attack being executed through Invoke-AtomicRedTeam using the Windows `schtasks` utility. The command creates a scheduled task named `UpdaterTask` that launches PowerShell in a hidden window with `SYSTEM` privileges whenever a user logs on, which is a common persistence technique used by attackers. The task is then manually executed with `schtasks /run`, confirming the persistence mechanism was successfully created and triggered on the system.

