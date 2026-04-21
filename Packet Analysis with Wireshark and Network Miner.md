## Packet Analysis with Wireshark and Network Miner

### Tools 
- FTP - file transfer protocol, clear text, transfers files between systems
- Telnet - clear text, helpful to remotely connect to and administer a machine
- SSH - Secure Shell, transfers files between systems securely
- DNS - Domain name system, converts IPs to understandable names and vice versa
- ARP - MAC address discovery
- IP - connectionless protocol for transfering packets from source to destination
- IPv6 - IPv4 upgrade with more addressing and a 128-bit address space
- ICMP - Supporting protocol and used in ping and traceroute, allows diagnostic info
- TCP - reliable, connection oriented, and ordered protocol, reliably sending packets over a network
- UDP - connectionless protocol, minimal error checking, allows communication between ports and application layer protocols
- POP3 - allows users to read e-mail from a server
- SMTP - allows users to send e-mails from a server
- Wireshark - protocol analyzer allowing packet capturing and inspection
- Network Miner - Network forensic analysis tool (NFAT) and available as a packet sniffer or for network anlysis

### Topology
- Windows 8.1 - Attack Machine

### LAB
1. Open the Windows 8.1 Attack Machine
2. Open .pcap file in Wireshark
3. Apply IPv6 filter with `ipv6` to display traffic of IPv6
4. Apply the filter `ip and !ipv6` to display traffic of IPv4
5. Apply the filter `ip.addr == 224.0.0.0/8` for multicast traffic
6. Apply the filter `ip.addr == 172.16.200.255` for broadcast traffic
7. Apply the filter `icmp` to display traffic of ICMP
8. Apply the filter `arp` to display traffic of ARP
9. Apply the filter `tcp` to display traffic of TCP
10. Open the Transmission Control Protocol section of a packet and view the TCP flags
11. Apply the filter `udp` to display traffic of UDP
12. Apply the filter `ftp` to display traffic of FTP
13. Apply the filter `pop` to display traffic of POP
14. Apply the filter `smtp` to display traffic of SMTP
15. Apply the filter `dns` to display traffic of DNS
16. Apply the filter `tcp.port == 17` to display the traffic of QOTD
17. Follow the TCP stream of the first frame
18. Apply the filter `telnet` to display the traffic of Telnet
19. Follow the TCP stream of the first frame
20. Apply the filter `tcp.port == 19` to display the traffic of CHARGEN
21. Follow the TCP stream of the first frame
22. Apply the filter `tcp.port == 13` to display the traffic of DAYTIME
23. Follow the TCP stream of the first frame
24. Apply the filter `tcp.port == 7` to display the traffic of ECHO
25. Follow the TCP stream of the first frame
26. Apply the filter `ssh` for the traffic of Secure Shell
27. Apply the filter `rdp` for the traffic of Remote Desktop Protocol
28. Apply the filter `smb` for the traffic of Server Message Block
29. Apply the filter `nbns` for the traffic of NetBIOS Name Service
30. Apply the filter `http` for the traffic of Hypertext Transfer Protocol
31. Export HTTP objects and save all
32. Open lab11 file which contains the exported content
33. Find the icon of a picure and open it
34. Open a new Wireshark session called flags.pcap and apply the QOTD filter of `tcp.port == 17`
35. Follow TCP stream of first frame
36. Filter for FTP traffic and follow TCP stream
37. Filter for POP traffic and follow TCP stream
38. Filter for Telnet traffic and follow TCP stream
39. Open Network Miner and import the Wireshark session lab11.pcap
40. View the hosts running the Microsoft operating systems
41. Examine captured images
42. Look at messages and examine e-mail message
43. Look at credentials
44. Look at files and open one
45. Open a new session of Network Miner and drag in the Wireshark session flag2.pcap
46. Examine images
