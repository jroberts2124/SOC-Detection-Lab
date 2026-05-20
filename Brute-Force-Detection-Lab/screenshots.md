<img width="1041" height="119" alt="image" src="https://github.com/user-attachments/assets/93c69e84-6002-4b0f-86c3-0f81140122c7" />

This screenshot shows Invoke-AtomicRedTeam executing MITRE ATT&CK brute-force attack simulations using technique `T1110.001`, which focuses on password guessing against Active Directory accounts. The tests attempt to brute-force credentials for a user account named `Josh` through SMB and LDAP authentication methods to generate realistic failed authentication activity for SOC detection testing. One of the tests failed because the LDAP server or domain controller was unavailable, but the attack simulation still demonstrates how brute-force login attempts can be generated and monitored in Splunk Enterprise.


<img width="1237" height="493" alt="image" src="https://github.com/user-attachments/assets/cf390668-a006-40f8-815c-e0a626651b08" />

This screenshot shows a combined Splunk Enterprise query searching for both failed logon events (`EventCode=4625`) and Sysmon process creation activity. The query extracts executable names from raw Sysmon XML logs and displays process activity such as `svchost.exe`, `LocationNotificationWindows.exe`, and multiple Splunk Universal Forwarder processes running on the endpoint. This type of detection helps SOC analysts correlate authentication activity with process execution to identify suspicious behavior or possible brute-force and persistence activity on a system.


