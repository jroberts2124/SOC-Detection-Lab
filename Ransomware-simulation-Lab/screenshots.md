<img width="975" height="680" alt="image" src="https://github.com/user-attachments/assets/f1e2069b-9824-4af6-ac5f-f96de5a8586f" />

Screenshot shows a simulated ransomware attack lab where PowerShell commands create test files, rename them with a .locked extension to mimic file encryption behavior, generate a fake ransom note (READ_ME.txt), and display the modified files inside the C:\RansomwareLab directory.

<img width="975" height="105" alt="image" src="https://github.com/user-attachments/assets/1ce6644c-b69f-47f8-8848-733c775e3403" />

Command commonly used in ransomware attacks to delete Windows Volume Shadow Copies with vssadmin delete shadows /all /quiet, preventing victims from restoring files through system backups or previous versions.

<img width="975" height="447" alt="image" src="https://github.com/user-attachments/assets/dce904b7-4d3e-4720-8b60-c15ec9d29a84" />

Sysmon and Windows Security logs in Splunk Enterprise capturing a simulated ransomware-style PowerShell command that creates a fake ransom note (READ_ME.txt) using an execution policy bypass

<img width="975" height="214" alt="image" src="https://github.com/user-attachments/assets/375148cc-cedd-43ba-a779-5038ff1fc1ca" />

Custom Splunk Enterprise query detecting the execution of the ransomware-related command vssadmin delete shadows /all /quiet, which attackers commonly use to delete Windows Volume Shadow Copies and prevent file recovery after encryption.

<img width="975" height="324" alt="image" src="https://github.com/user-attachments/assets/5d73975d-d9c9-4d2d-9fb5-89d959e838b6" />

<img width="975" height="305" alt="image" src="https://github.com/user-attachments/assets/ef5ab224-84bd-4630-963a-e3386ce21964" />





