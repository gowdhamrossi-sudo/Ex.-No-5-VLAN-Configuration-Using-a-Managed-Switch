## Ex. No: 5  VLAN Configuration Using a Managed Switch
Date:
________________________________________
# Objective
To configure Virtual Local Area Networks (VLANs) on a managed switch and verify that hosts within the same VLAN can communicate while others cannot.
________________________________________
# Apparatus/Tools Required
•	Cisco Packet Tracer<br>
•	1 Managed Switch (e.g., 2960)<br>
•	4 PCs<br>
•	Straight-through Ethernet cables<br>
________________________________________
# Network Topology Diagram
Description:<br>
•	PC0 and PC1 are assigned to VLAN 10.<br>
•	PC2 and PC3 are assigned to VLAN 20.<br>
•	All PCs are connected to different ports on the same switch.<br>
(Insert screenshot of your Packet Tracer setup here)<br>

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/f928c332-024e-4d2f-afae-72e20f5f5e67" />

________________________________________
# IP Addressing Table
Device	VLAN	IP Address	Subnet Mask	Port<br>
PC0	10	192.168.10.1	255.255.255.0	FastEthernet0/1<br>
PC1	10	192.168.10.2	255.255.255.0	FastEthernet0/2<br>
PC2	20	192.168.20.1	255.255.255.0	FastEthernet0/3<br>
PC3	20	192.168.20.2	255.255.255.0	FastEthernet0/4<br>
________________________________________
# Procedure
1.	Open Cisco Packet Tracer and add 4 PCs and 1 Switch.<br>
2.	Connect PC0–PC3 to switch ports FastEthernet0/1 to FastEthernet0/4 respectively.<br>
3.	Assign static IP addresses to each PC as per the IP table.<br>
4.	Enter the Switch CLI and create two VLANs:<br>
o	VLAN 10 for PC0 and PC1<br>
o	VLAN 20 for PC2 and PC3<br>
5.	Assign the respective switch ports to their VLANs.<br>
6.	Use the ping command from PC0 to PC1 (should succeed).<br>
7.	Try pinging from PC0 to PC2 (should fail — different VLANs).<br>
________________________________________
# Commands Used (Switch CLI)
bash<br>
CopyEdit<br>
Switch> enable<br>
Switch# configure terminal<br>

Switch(config)# vlan 10<br>
Switch(config-vlan)# name STAFF<br>
Switch(config-vlan)# exit<br>

Switch(config)# vlan 20<br>
Switch(config-vlan)# name STUDENTS<br>
Switch(config-vlan)# exit<br>

Switch(config)# interface range fastethernet0/1 - 2<br>
Switch(config-if-range)# switchport mode access<br>
Switch(config-if-range)# switchport access vlan 10<br>
Switch(config-if-range)# exit<br>

Switch(config)# interface range fastethernet0/3 - 4<br>
Switch(config-if-range)# switchport mode access<br>
Switch(config-if-range)# switchport access vlan 20<br>
Switch(config-if-range)# exit<br>
________________________________________
# Output (Screenshots)
# CONFIGURATION :
PC1
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/847e1ea0-23af-47e3-8ba4-3b9660797d9a" />



PC2

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/4e1e850c-3df1-4400-943c-0f562253616f" />




PC3


<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/430fec06-1c38-4bdd-b307-33b2482c697b" />


PC4

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/c40e9ec4-e6c8-43c7-9feb-a36f7a444f42" />



SWITCH

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/75b0cd91-60d2-4d0e-9bc0-9f598affc8e3" />



# PING


PC1


<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/aacc55be-a56e-4b29-bb65-d2828e139fdf" />




PC2


<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/0d3f56e7-f577-4a3d-b8ab-e02c25e25c44" />



PC3

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/4d2714b5-2328-4da9-98c8-732e27449d22" />




PC4



<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/36d92590-e98f-48c9-bef1-01e0a898d066" />



________________________________________
# Result
Successfully created and configured VLANs on a managed switch. Verified that only PCs within the same VLAN could communicate with each other.

