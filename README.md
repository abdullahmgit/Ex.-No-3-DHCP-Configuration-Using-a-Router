## Ex. No: 3  DHCP Configuration Using a Router

________________________________________
# Objective
To configure a router to automatically assign IP addresses to client PCs using the Dynamic Host Configuration Protocol (DHCP).
________________________________________
# Apparatus/Tools Required
•	Cisco Packet Tracer<br>
•	1 Router<br>
•	1 Switch<br>
•	2 PCs<br>
•	Straight-through Ethernet cables<br>
________________________________________
# Network Topology Diagram
Description:<br>
•	PC0 and PC1 are connected to Switch0.<br>
•	Switch0 is connected to Router0 on FastEthernet0/0.<br>
•	The router acts as a DHCP server for the connected LAN.<br>
(Insert screenshot of your Packet Tracer setup here)<br>
________________________________________
# IP Addressing Table
Device	Interface	IP Address	Subnet Mask<br>
Router0	FastEthernet0/0	192.168.50.1	255.255.255.0<br>
PC0	NIC	DHCP (Auto)	Assigned by DHCP<br>
PC1	NIC	DHCP (Auto)	Assigned by DHCP<br>
DHCP Pool:<br>
•	Network Address: 192.168.50.0<br>
•	Subnet Mask: 255.255.255.0<br>
•	Default Gateway: 192.168.50.1<br>
•	DNS Server: 8.8.8.8<br>
•	Excluded IP Range: 192.168.50.1 to 192.168.50.9<br>
________________________________________
# Procedure
1.	Open Cisco Packet Tracer and add 2 PCs, 1 Switch, and 1 Router.<br>
2.	Connect both PCs to the Switch using straight-through cables.<br>
3.	Connect the Switch to Router0’s FastEthernet0/0.<br>
4.	Assign the IP address 192.168.50.1 to the router’s FastEthernet0/0 interface.<br>
5.	Enable the interface using the no shutdown command.<br>
6.	Configure the router as a DHCP server:<br>
o	Define the DHCP pool with network address, default gateway, and DNS.<br>
o	Exclude gateway and reserved addresses from the pool.<br>
7.	Set both PC0 and PC1 to obtain their IP address via DHCP (auto).<br>
8.	Verify that each PC receives an IP address dynamically.<br>
9.	Use the ping command to test connectivity between the two PCs.<br>
________________________________________
# Commands Used (Router CLI)
bash<br>
CopyEdit<br>
Router> enable<br>
Router# configure terminal<br>
Router(config)# interface fastethernet0/0<br>
Router(config-if)# ip address 192.168.50.1 255.255.255.0<br>
Router(config-if)# no shutdown<br>
Router(config-if)# exit<br>

Router(config)# ip dhcp excluded-address 192.168.50.1 192.168.50.9<br>

Router(config)# ip dhcp pool MYPOOL<br>
Router(dhcp-config)# network 192.168.50.0 255.255.255.0<br>
Router(dhcp-config)# default-router 192.168.50.1<br>
Router(dhcp-config)# dns-server 8.8.8.8<br>
Router(dhcp-config)# exit<br>
________________________________________
# Output (Screenshots)
<img width="1917" height="1071" alt="Screenshot 2026-10-27 160627" src="https://github.com/user-attachments/assets/7bc3ea5d-a7b9-4a69-9425-d90c934ca215" />
<img width="1920" height="1080" alt="Screenshot 2026-10-24 104712" src="https://github.com/user-attachments/assets/fae6f08e-ee4b-4f0d-8f95-5de57c029266" />
<img width="1912" height="1076" alt="Screenshot 2026-10-27 160736" src="https://github.com/user-attachments/assets/8bf4f641-5bdf-45ab-b8e1-83b8d6b20d19" />
<img width="1920" height="1080" alt="Screenshot 2026-10-24 105003" src="https://github.com/user-attachments/assets/e128d44d-0e45-4c75-b015-6ded560f6d20" />
<img width="1920" height="1080" alt="Screenshot 2026-10-24 105324" src="https://github.com/user-attachments/assets/f26c48c8-6b28-4b56-83ca-5e01a9a20784" />
<img width="1917" height="1076" alt="Screenshot 2026-10-24 105546" src="https://github.com/user-attachments/assets/690d8c2e-23c3-497b-84bb-36baed12c4c8" />
<img width="907" height="900" alt="Screenshot 2026-10-27 161010" src="https://github.com/user-attachments/assets/a4c6445c-b5c8-49fb-8cff-610d06698c5f" />

________________________________________
# Result
Successfully configured a DHCP server on the router. PCs were dynamically assigned IP addresses and were able to communicate over the network.
