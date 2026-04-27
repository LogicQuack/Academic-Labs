## Stateless Firewalls

### Tools
Denial of Service: DoS attack, renders device or resource unavailable due
due to perpetual interruptions

Firewall: allows or rejects traffic based on a set of rules

VyOS: open-source firewall/router, has DHCP, VPN, TFTP, and QoS support along with other protocols

TCPDump: Linux tool for packet capture

Ifconfig: enumerates interfaces on Linux 

UDP: User Datagram Protocol, connectionless protocol on the TCP/IP stack
minimal error checking, allows communication between ports and application-layer protocols

Hping3: tool for testing firewall rules, can send flood of ICMP, UDP, or TCP packets

UDP Flood: DoS attack via many UDP datagrams overwhelming the port

### Topology
Kali Linux - 192.168.1.5

Web Server - 10.10.1.112

Ubuntu - 10.10.4.5

Cloud

### LAB

1. Login to Ubuntu workstation 
2. run setup script
> ssh -t support@urbank.com sudo LAB10A
3. Login
4. Login to Kali Linux
5. SSH into urbank.com
> ssh support@urbank.com
6. Start a capture session 
> sudo tcpdump -i eth0 -n udp > udp
7. Flood web server using UDP packets with Hping3
> hping3 --flood --rand-source --udp -p 80 urbank.com
8. Wait a bit and then interrupt the flooding and capturing sessions
9. view the the number of lines in the file
> wc -l udp
10. view the packets, -v removes NTP chatter
> cat udp | grep -v "10.10.1.113"
11. Login to Ubuntu worksation 
12. Create a session for the edge router of VyOS through Putty

Host Name: vyos_urbank.com
Saved Sessions: SSH_VyOS.UrBank.com

13. Open the session, logging in as support
14. View interfaces
> show interfaces
15. Configure the firewall
> configure

> set firewall name WAN_TO_DMZ description "ETH0 TO ETH1"

> set firewall name WAN_TO_DMZ enable-default-log

> set firewall name WAN_TO_DMZ rule 200 action accept

> set firewall name WAN_TO_DMZ rule 200 protocol tcp

> set firewall name WAN_TO_DMZ rule 200 destination port 80,443

> set firewall name WAN_TO_DMZ rule 200 destination address 10.10.1.112

> set firewall name WAN_TO_DMZ rule 200 description STATELESS_WEB_ACCESS

> commit

16. Apply the firewall rules in the inbound direction to the interface facing
the Internet

> set interfaces ethernet eth0 firewall in name WAN_TO_DMZ

> commit

> save

17. Verify the additions

> show firewall 

18. Login to Kali Linux
19. Attempt the same flood as before except with a different target
and interupt after 30 seconds or so

> hping3 --flood --rand-source --udp -p 80 10.10.1.112

20. SSH into Support

> ssh support@209.1.1.1

21. Verify the firewall changes again

> show firewall 

22. Ensure webpage access is still available 

> wget 10.10.1.112

