<img width="975" height="370" alt="image" src="https://github.com/user-attachments/assets/29ac2972-c50d-4d5a-93d4-69261d67fbb9" />

Windows LOLBins (Living Off the Land Binaries) such as certutil.exe, bitsadmin.exe, rundll32.exe, and regsvr32.exe being executed to simulate attacker techniques commonly used for file hashing, command execution, persistence, and malware delivery in a SOC detection lab.

<img width="975" height="350" alt="image" src="https://github.com/user-attachments/assets/77b9429e-8b1a-4d4a-be89-9534a52ca9b0" />

Splunk Enterprise query detecting the execution of multiple Windows LOLBins (Living Off the Land Binaries) including certutil.exe, bitsadmin.exe, rundll32.exe, and regsvr32.exe from Sysmon logs

<img width="975" height="306" alt="image" src="https://github.com/user-attachments/assets/55af6b51-21ed-49fe-8352-056403d396ff" />

detailed Sysmon event in Splunk Enterprise capturing the execution of regsvr32.exe, a Windows LOLBin commonly abused by attackers for malicious script execution, persistence, and defense evasion, along with the associated command line, parent process, and user context from the endpoint.

