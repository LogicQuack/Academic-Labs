## Investigating and Responding to Security Incidents

### Tools
- AVG Antivirus
- Remote Desktop Protocol (RDP)

### Topology
- vWorkstation 172.30.0.2
- TargetWindows02 172.30.0.10

### LAB
1. Examine an example Incident Response Report
<img width="229" height="242" alt="image" src="https://github.com/user-attachments/assets/4658264b-67a2-4701-ba0c-45c502ae81d7" />
2. Run a deep scan with the AVG antivirus software
<img width="274" height="169" alt="image" src="https://github.com/user-attachments/assets/e1ea7464-7612-4710-8268-b2bfd7e15b34" />
3. Find an achtung.exe threat
<img width="468" height="24" alt="image" src="https://github.com/user-attachments/assets/c0c05b0b-0bc5-41fa-a37a-1a68dd096434" />
4. What is an achtung.exe threat?

It is a trojan against Windows that can allow an attacker to break into your system and either collect sensitive data or execute malicious commands/programs
(Spy-Emergency, n.d.). In our case, it is in C:\vDos\DPTEST\achtung.exe. Removal can be done with various antivirus software.
For example, AVG in our lab can detect and remove it. Overall, the process is initiating a scan, then the software likely detects the malware,
then you can choose to remove it through a scan summary page or whatever interface the antivirus software provides after a scan. 

5. Go to the antivirus' Quarantine and empty it.
<img width="151" height="174" alt="image" src="https://github.com/user-attachments/assets/38c532e1-78a2-43ae-a7ac-b78afa649f17" />
6. Repeat steps 2-5 but with the remote administration server avg.securelabs.com selected and focusing on the threat KEYCOPY.COM
<img width="335" height="155" alt="image" src="https://github.com/user-attachments/assets/ffb1db35-b5c7-4382-a949-15970fa7ee86" />
<img width="468" height="49" alt="image" src="https://github.com/user-attachments/assets/43eead47-5af9-4184-987c-44d03d8941c9" />

The KEYCOPY.COM threat is a trojan with various capabilities. These include remote access, denial of service, distributed denial of service, 
capturing keyboard inputs, deleting objects, and terminating processes. The best way to remove it is through a an antivirus software with a fully 
updated database (FortiGuard, 2013). This is possible with AVG as it had detected it. You can then go into the quarantine and delete the malware. 

<img width="169" height="131" alt="image" src="https://github.com/user-attachments/assets/788767f0-2ddf-41da-9773-cd0bf9bd76b0" />

6. Write Incident Response Report based on example, see the relevant file.
7. Explain how to isolate an infected and what data can be lost from such an action, see the relevant file.

### References

https://www.fortiguard.com/encyclopedia/virus/5911817/w32-dos-keycopy-tr  

https://www.spy-emergency.com/research/T/Trojan.Win32.Achtung.html 
