## Breaking WEP and WPA and Decrypting the Traffic

### Tools
- FTP: file transfer protocol in plain text for transfering files
- Telnet: remote administration protocol in plain text
- WEP: wired equivilent privacy wireless network security protocol, WEP keys are passwords
- for Wi-Fi devices
- SSID: service set identifier, identifies a network, in header of packets sent over a WLAN
- DNS: domain name system, converts IPs into understandable names
- Iwconfig: view interfaces with wireless support on Linux
- Airmon-ng: puts wireless cards into monitor mode
- Aircrack-ng: cracks WEP keys and WPA passphrases
- Airdecap-ng: decrypts WPA and WEP traffic

### Topology
- Kali 2 Linux 192.168.1.101

### LAB
1. Login to the Kali 2 Linux
2. check interfaces with wireless support
> iwconfig

there are none

3. examine options of airmon-ng
> airmon-ng --help
4. examine options of aircrack-ng 
> aircrack-ng --help
<img width="634" height="544" alt="Screenshot 2026-05-04 at 9 43 16 PM" src="https://github.com/user-attachments/assets/85980649-5f23-4984-aa1e-f81ad344a0c2" />

5. examine options of airdecap-ng
> airdecap-ng --help
6. go to the Captures directory
> ls
>
> cd Captures
7. open the encrypted capture file wepcapture.cap with Wireshark
> wireshark wepcapture.cap
8. apply 'ip' filter

there are no results
<img width="642" height="234" alt="Screenshot 2026-05-04 at 9 44 02 PM" src="https://github.com/user-attachments/assets/8da357c4-16ac-4a1d-af82-80ac4db52a17" />


9. get the WEP key from wepcapture.cap
> aircrack-ng wepcapture.cap
<img width="640" height="265" alt="Screenshot 2026-05-04 at 9 44 58 PM" src="https://github.com/user-attachments/assets/15b1daef-3269-4def-b591-c6eae09988d0" />

10. use key to decrypt wepcapture.cap
> airdecap-ng -w 39:B0:35:D5:9C wepcapture.cap
11. open the newly decrypted file with Wireshark
> wireshark wepcapture-dec.cap
12. apply 'ip' filter to now see results
<img width="641" height="237" alt="Screenshot 2026-05-04 at 9 45 47 PM" src="https://github.com/user-attachments/assets/23d4fcd0-41b0-4fc5-a296-4228ee941a1a" />

13. apply 'ftp' filter for FTP traffic
14. apply 'pop' filter for email traffic and follow TCP stream for the password in plain text
15. click 'Filter Out This Stream Button' and then follow the TCP stream of the subsequent packet
16. Read the email
<img width="642" height="278" alt="Screenshot 2026-05-04 at 9 46 26 PM" src="https://github.com/user-attachments/assets/6f80ef64-51dd-4592-87ae-cde6314df1ae" />

18. apply 'telnet' filter for Telnet traffic and follow TCP stream and filter it out
19. follow the TCP stream of the next packet
20. apply 'tcp.port == 17' for QOTD traffic
21. follow TCP stream, filter out the stream, and follow the TCP stream of the next packet
22. export objcts with HTTP and save all
23. examine saved folder
<img width="590" height="363" alt="Screenshot 2026-05-04 at 9 47 58 PM" src="https://github.com/user-attachments/assets/a3c87732-6451-4a7d-a634-e60ebebedeed" />

25. do the same as steps 7-11 except with wpacapture.cap, also for the aircrack-ng command,
add '-w Wordlist.txt'
<img width="642" height="367" alt="Screenshot 2026-05-04 at 9 48 47 PM" src="https://github.com/user-attachments/assets/d71f1349-9ac5-40a3-bf0e-7f5e16af11a1" />

for the airdecap-ng, type:
> airdecap-ng -e SECURETWO -p boneless wpacapture.cap 
24. view 'ip', 'ftp', and 'pop' traffic
25. follow the TCP stream of the first POP packet and read the email
<img width="601" height="326" alt="Screenshot 2026-05-04 at 9 49 57 PM" src="https://github.com/user-attachments/assets/ec304a3d-89eb-4d2e-b03b-1540092229e8" />

26. export objects with HTTP and save all
27. examine saved folder 
