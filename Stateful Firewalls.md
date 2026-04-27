## Stateful Firewalls

## This is a sequel to Stateless Firewalls.md

### Concepts
- Stateful Firewall: Tracks all states of traffic and protects the network
- via examining patterns and flows

- TCP Flood: DoS attack of TCP packets

- Denial of Service: DoS attack, renders device or machine unavailable through
- perpetual interruptions

- TCP: connection oriented protocol of the TCP/IP stack, reliable and error checked,
- three-way handshake with the phases connection setup, data transmission, and connection termination

- Hping3: Linux tool for flooding ICMP, TCP, and UDP packets

- TCP Flood: DoS attack in which TCP packets are used, using the handshake for 
virtual connections between two hosts 

- SYN Flood: DoS attack of SYN packets, victim gets requests to establish connection that 
are ultimately fake, responds with SYN-ACK for open ports, the connection attempt leaves a large number
of connections half-open causing overflow, legitimate service being denied

- VyOS: Open-source firewall/router with VPN, QoS, TFTP, and DHCP support

### Topology

- Kali Linux - 192.168.1.5

- Web Server - 10.10.1.112

- Ubuntu - 10.10.4.5

- Cloud

### LAB

1. Login to Ubuntu workstation
2. run script
> ssh -t support@urbank.com sudo LAB11A
3. SSH into Urbank's edge router
> ssh support@vyos.urbank.com
4. run script
> LAB11A
5. View firewall ruleset
> show firewall
6. Enter configure mode
> configure
7. View the firewall rules for WAN_TO_DMZ
> show firewall name WAN_TO_DMZ
8. Enable stateful tracking and commit
> set firewall name WAN_TO_DMZ rule 200 state new enable
>
> commit
9. Change the description for rule 200
> delete firewall name WAN_TO_DMZ rule 200 description STATELESS_WEB_ACCESS
>
> set firewall name WAN_TO_DMZ rule 200 description STATEFUL_WEB_ACCESS
>
> commit
10. Verfify changes
> show firewall name WAN_TO_DMZ
11. Login to Kali Linux
12. run a SYN ACK flood with Hping3
> hping3 -SA --flood --rand-source -p 80 10.10.1.112
13. Wait a bit and then interrupt it
14. Login in to the Ubuntu workstation
15. Save changes and exit the edit mode
> save
>
> exit
16. Verify that the firewall defended against the attack
> show firewall statistics 
