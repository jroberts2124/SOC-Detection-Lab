<img width="975" height="370" alt="image" src="https://github.com/user-attachments/assets/29ac2972-c50d-4d5a-93d4-69261d67fbb9" />

Windows LOLBins (Living Off the Land Binaries) such as certutil.exe, bitsadmin.exe, rundll32.exe, and regsvr32.exe being executed to simulate attacker techniques commonly used for file hashing, command execution, persistence, and malware delivery in a SOC detection lab.

<img width="975" height="350" alt="image" src="https://github.com/user-attachments/assets/77b9429e-8b1a-4d4a-be89-9534a52ca9b0" />

Splunk Enterprise query detecting the execution of multiple Windows LOLBins (Living Off the Land Binaries) including certutil.exe, bitsadmin.exe, rundll32.exe, and regsvr32.exe from Sysmon logs

<img width="975" height="306" alt="image" src="https://github.com/user-attachments/assets/55af6b51-21ed-49fe-8352-056403d396ff" />

detailed Sysmon event in Splunk Enterprise capturing the execution of regsvr32.exe, a Windows LOLBin commonly abused by attackers for malicious script execution, persistence, and defense evasion, along with the associated command line, parent process, and user context from the endpoint.

<img width="975" height="282" alt="image" src="https://github.com/user-attachments/assets/7f9611c7-37d5-425c-920e-adf868cce4f1" />

execution of bitsadmin.exe, a Windows LOLBin commonly abused by attackers for file transfers, malware downloads, and persistence techniques. The event includes the command bitsadmin /list, along with the executable path, parent process (cmd.exe), user account, and process metadata collected from the monitored endpoint.

<img width="975" height="303" alt="image" src="https://github.com/user-attachments/assets/67e6c585-ddc4-4195-a118-5226b2a21687" />

Splunk Enterprise capturing the execution of certutil.exe, a Windows LOLBin commonly abused by attackers for file downloads, encoding/decoding, and malware delivery techniques. The event logs the command certutil.exe -hashfile C:\Windows\System32\notepad.exe SHA256, along with the parent process (cmd.exe), executable path, user context, and generated SHA256 hash value from the monitored endpoint.






