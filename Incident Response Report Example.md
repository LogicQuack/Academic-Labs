## Incident Response Report Example

### Incident Report #: 
IR-1

### Reported Date and Time: 
April 21, 2026

### Technician: 
Jesse

### Site Location:
Windows Workstation 2016 as part of a virtual environment which is part of a lab offered by Jones and Bartlette Learning 

### Identification (Type and how detected): 
A deep scan was run via the AVG antivirus as part of a checking up on a system’s health. Malware was thus flagged. 

Virus Scan detected achtung.exe and KEYCOPY.COM

### Triage (Impact): 
Only the one machine was infected, and it fortunately did not spread outward into the network. 

### Containment (Steps taken): 
1)	Ran an antivirus deep scan and placed the malware into quarantine for later inspection.

### Investigation (Cause): 
There is no definitive answer on why these were on the machine as this is a lab environment
where I am given the infected machine. However, based on the typical behavior of trojans, achtung.exe and KEYCOPY.COM probably
entered the machine via deceptive social engineering tactics or through obfuscating the malicious intent behind the malware, making
 it seem like an innocuous file to download. The answer could be both as well. 

### Recovery and Repair (Resolution): 

Use the AVG antivirus to detect and quarantine the malware. It can then be deleted upon later analysis.  
Scan corporate e-mails for any other malware and subsequently scan the same machine later for anything that could be lingering. 

### Lessons Learned (Debriefing and Feedback): 
Antivirus scans should be scheduled periodically to catch any potential malware.
Scans should encompass hardware to storage medias to software to ensure a comprehensive coverage
Policies should be implemented for improving employees’ cybersecurity and malware awareness. 
There can thus be training so they understand how to look for suspicious signs. 
