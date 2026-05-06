## Securing the Network with an Intrusion Detection System (IDS)

### Tools
- Snort: open-source intrusion prevention detection system with analysis of traffic
in real time with packet logging, protocol analysis, content matching, and attack detection
- Snorby: web-based front-end for applications like Snort, provides a clean interface to examine the threats and logs that an IDS captures
- Nessus: A toolkit of services and tools for vulnerability scanning, testing systems against known exploits and weaknesses

### Topology
- Windows Workstation - 192.168.0.1
- Snort Server - 172.30.0.8
- Snorby
- Remote Windows Workstation - 172.30.0.10

### LAB
1. Open a Snort SSH connection
2. give yourself root access
3. start Snort 
> nsm_sensor_ps-start
4. change the working directory to the Snort configuration files
> cd /etc/nsm/SCO-eth0
5. Open snort.conf
> vi snort.conf
6. enter edit mode with `i` and alter the ipvar HOME_NET line:
remove 10.0.0.0/8 and replace 172.16.0.0/12 with 172.30.0.0/24
<img width="1332" height="828" alt="image" src="https://github.com/user-attachments/assets/8beab6b2-5b15-4fbd-b21e-a60f56f1c885" />

7. exit and save with `:wq!`
8. move to directory with the IDS rules
> cd /etc/nsm/rules
9. read the contents of reference.config
> cat reference.config
10. open local.rules
> vi local.rules
11. write a TCP alert that reads: alert tcp any any -> $HOME_NET 22
(msg:"yourname SSH connection atempt"; sid:1000002; rev:1;)
<img width="643" height="67" alt="Screenshot 2026-05-05 at 9 18 17 AM" src="https://github.com/user-attachments/assets/b9efce7c-f8ae-49f8-b746-5a286a8bee76" />

12. reboot the Snort device
13. go back into the Snort device and execute the command for root privileges
> sudo -i
14. open Snorby and from the dashboard, click on the Events tab,
15. An event should be generated from step 12, click on it and select view rule
<img width="979" height="522" alt="Screenshot 2026-05-05 at 9 25 11 AM" src="https://github.com/user-attachments/assets/a4a4eef0-27d6-46fc-a7ea-1b0e1a150795" />

16. open connecton to remote Windows workstation and open the Nessus web client
17. create a basic network scan with 172.30.8 as the target
18. launch the created scan
19. Watch Snorby as the the scan proceeds
<img width="771" height="403" alt="Screenshot 2026-05-05 at 9 54 14 AM" src="https://github.com/user-attachments/assets/b1c5bfbc-8258-4a1c-b7cd-2a92bcc353d2" />

20. After the scan completes, from the Snorby dashboard, go to the High Severity report
21. Review the high security events
<img width="760" height="474" alt="Screenshot 2026-05-05 at 9 57 25 AM" src="https://github.com/user-attachments/assets/3949e172-0d05-479b-8d61-70b492a2cb97" />

22. export the report to a PDF
23. open the PDF report and examine the top 15 signatures
<img width="726" height="616" alt="Screenshot 2026-05-05 at 10 00 04 AM" src="https://github.com/user-attachments/assets/5e2e0afa-a930-4d59-8200-62a8397b1ce9" />

24. Describe three of the signatures in step 23

I will specifically highlight ‘ET SCAN Potential SSH Scan’, ‘GPL SNMP public access udp’, and ‘ET POLICY Suspicious inbound to PostgreSQL port 5432’. 
To understand each signature, we should break it up into chunks.
First, in the context of signature alerts, ET scan refers to a rule about scanning from the Emerging Threats (ET) project (Suricata Documentation, n.d.).
Potential SSH Scan implies that a device is likely being scanned for its SSH port. 
Thus, from both pieces, this is a  alert about an SSH scan from the ET project. 
Second, using the same format as the previous alert, ‘GPL SNMP’ refers to a rule from GPL about Simple Network Management Protocol. 
‘Public access udp’ implies that SNMP packets are using UDP for data transfer and are exposed to the public meaning important data could be leaking for hackers to pick up.
SNMP often has public read-only community strings (Cisco, 2024). This is enabled by default and thus causing the above alert. 

Lastly, we can use the same logic for the final alert as before. 
‘ET POLICY’ means that it is an alert from the ET project about policies. 
‘Suspicious inbound’ implies traffic coming into the device, and PostgreSQL port 5432 shows the service and port it may be entering through.

### Reference

https://www.cisco.com/c/en/us/support/docs/ip/simple-network-management-protocol-snmp/7282-12.html  

https://docs.suricata.io/en/suricata-6.0.0/make-sense-alerts.html  
