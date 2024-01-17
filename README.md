This project aims to provide an in-depth analysis of an ideal network configured with Cisco Packet Tracer. Cisco Packet Tracer is a simulation tool that mimics real-world network environments, offering a practical approach to network configuration. This article will provide detailed information about the network components, technologies, and subnets within the configured network.
![project](https://github.com/mock3ng/ciscoproject/blob/main/project.png)
Keywords: Cisco Packet Tracer, network configuration, ideal network, simulation tool, network components, technologies, subnets

Network Topology:
Understanding the network topology of the configured network is essential before diving into the analysis. The project consists of three main networks, namely Fen-R, Ede-R, and BiM-R. Each main network has different subnets, and communication between these subnets is facilitated through the use of the OSPF (Open Shortest Path First) routing protocol. The rest of the network comprises layer 2 network switches connected to these main networks.

Keywords: network topology, main networks, subnets, OSPF routing protocol

IP Addressing:
It is known that each subnet in the network has a unique IP address range. For example, the Fen-R main network uses the IP address 1.1.1.2 while the Ede-R main network uses 1.1.1.3. Each subnet is assigned unique IP addresses, and communication between subnets is established using the OSPF routing protocol.

Keywords: IP addressing, subnets, unique IP addresses, OSPF routing protocol

VLANs (Virtual Local Area Networks):
The project explores the utilization of VLANs for traffic routing between switches in the network. Each switch has designated ports assigned to different VLANs. For instance, the FEN-OMG switch has VLAN 10, 11, 12, and 19, while the EDE-OMG switch has VLAN 20, 21, 22, and 29. This enables devices from different subnets to communicate within the network.

Keywords: VLANs, network configuration, traffic management, network segmentation

VTP (VLAN Trunking Protocol):
The VLAN configurations in the network are centrally managed using the VTP (VLAN Trunking Protocol). The FEN-OMG switch is configured as the VTP server, sharing VLAN configurations with other switches. As a result, all switches in the network have the same VLAN configurations, facilitating unified network management.

Keywords: VTP, VLAN Trunking Protocol, VLAN configurations, network switches, efficient network management

Subnets:
The subnets in the network are defined with different IP address ranges and VLAN configurations. Each subnet represents an independent network segment with its own switch and router. For example, VLAN 19 supported by the FEN-OMG switch has the IP address range of 192.168.19.0/24, and devices from the Fen-R main network are connected to this subnet.

Keywords: subnets, network segmentation, independent network segments, switches, routers

OSPF Routing Protocol:
The OSPF routing protocol is utilized to facilitate communication between the main networks. Based on the "Open Shortest Path First" (OSPF) protocol, OSPF determines the most efficient path between main networks using the shortest path algorithm. OSPF enables dynamic routing in the network and automatically adapts to changes in the network topology.

Keywords: OSPF routing protocol, optimal paths, dynamic routing, network efficiency, network topology

Conclusion:
In this article, we have conducted a detailed analysis of a network configured with Cisco Packet Tracer. We have provided insights into network topology, IP addressing, VLAN configurations, VTP, and OSPF routing protocol. Simulation tools like Cisco Packet Tracer allow network administrators to test real-world scenarios and optimize their networks for better efficiency.

Keywords: Cisco Packet Tracer, network administrators, network configuration, IP addressing, VLANs, VTP, OSPF routing protocol, network optimization



Cisco Router and Switch Configurations

Fen-R: On the Fen-R router, three separate VLANs (10, 11, 12) and corresponding subnets are configured. Additionally, a trunk connection is established on VLAN 19, providing access to a subnet associated with this VLAN.

Ede-R: The Ede-R router has a similar structure to Fen-R. Three separate VLANs (20, 21, 22) and subnets associated with VLAN 29 are configured.

BiM-R: The BiM-R router has a slightly different structure. It is associated with four VLANs (100, 101, 102, and 109), each linked to a specific subnet.

FEN-OMG: On the FEN-OMG switch, a port is configured for VLAN 19, providing access to the 192.168.19.0/24 subnet.

EDE-OMG: On the EDE-OMG switch, a port is configured for VLAN 29, providing access to the 192.168.29.0/24 subnet.

BiM-OMG: The BiM-OMG switch is configured with both trunk and access ports. It accommodates ports associated with VLANs 100, 101, 102, and 109. F-Kat1, F-Kat2, F-Kat3: These three switches respectively house ports associated with VLANs 10, 11, and 12. E-Kat1, E-Kat2, E-Kat3:




1. Configuration for Fen-R:
```
conf t              # Enters configuration mode
host Fen-R          # Sets the hostname as Fen-R
int gi 0/3/0        # Switches to GigabitEthernet 0/3/0 interface
no sh               # Enables the interface (no shutdown)
ip add 1.1.1.2 255.255.255.0    # Assigns an IP address and subnet mask to the interface
exit                # Exits the interface configuration
int gi 0/1          # Switches to GigabitEthernet 0/1 interface
```

2. Configuration for Ede-R:
```
conf t              # Enters configuration mode
host Ede-R          # Sets the hostname as Ede-R
int gi 0/3/0        # Switches to GigabitEthernet 0/3/0 interface
no sh               # Enables the interface (no shutdown)
ip add 1.1.1.3 255.255.255.0    # Assigns an IP address and subnet mask to the interface
exit                # Exits the interface configuration
int gi 0/1          # Switches to GigabitEthernet 0/1 interface
```

3. Configuration for BiM-R:
```
conf t              # Enters configuration mode
host BiM-R          # Sets the hostname as BiM-R
int gi 0/3/0        # Switches to GigabitEthernet 0/3/0 interface
no sh               # Enables the interface (no shutdown)
ip add 1.1.1.1 255.255.255.0    # Assigns an IP address and subnet mask to the interface
exit                # Exits the interface configuration
int gi 0/1          # Switches to GigabitEthernet 0/1 interface
```

4. Configuration for FEN-OMG:
```
conf t              # Enters configuration mode
host FEN-OMG        # Sets the hostname as FEN-OMG
vlan 10             # Creates VLAN 10
vlan 11             # Creates VLAN 11
vlan 12             # Creates VLAN 12
vlan 19             # Creates VLAN 19
exit                # Exits VLAN configuration
vtp mode server     # Sets the VTP mode as server
vtp domain sinan    # Sets the VTP domain as sinan
vtp password cisco  # Sets the VTP password as cisco
int range gi 1/0/1-5 # Switches to range of GigabitEthernet 1/0/1-5 interfaces
switchport mode trunk    # Sets the interface mode as trunk
exit                # Exits interface configuration
int gi 1/0/4        # Switches to GigabitEthernet 1/0/4 interface
switchport trunk native vlan 19    # Sets the native VLAN for the trunk interface as VLAN 19
exit                # Exits interface configuration
int vlan 19         # Switches to VLAN 19
no sh               # Enables the VLAN interface (no shutdown)
ip add 192.168.19.2 255.255.255.0   # Assigns an IP address and subnet mask to the VLAN interface
exit                # Exits VLAN interface configuration
ip default-gateway 192.168.19.1     # Sets the default gateway for the device
```

5. Configuration for EDE-OMG:
```
conf t              # Enters configuration mode
host EDE-OMG        # Sets the hostname as EDE-OMG
vlan 20             # Creates VLAN 20
vlan 21             # Creates VLAN 21
vlan 22             # Creates VLAN 22
vlan 29             # Creates VLAN 29
exit                # Exits VLAN configuration
vtp mode server     # Sets the VTP mode as server
vtp domain sinan    # Sets the VTP domain as sinan
vtp password cisco  # Sets the VTP password as cisco
int range gi 1/0/1-5 # Switches to range of GigabitEthernet 1/0/1-5 interfaces
switchport mode trunk    # Sets the interface mode as trunk
exit                # Exits interface configuration
int gi 1/0/4        # Switches to GigabitEthernet 1/0/4 interface
switchport trunk native vlan 29    # Sets the native VLAN for the trunk interface as VLAN 29
exit                # Exits interface configuration
int vlan 29         # Switches to VLAN 29
no sh               # Enables the VLAN interface (no shutdown)
ip add 192.168.29.2 255.255.255.0   # Assigns an IP address and subnet mask to the VLANCertainly, let me explain the commands one by one:

1. Fen-R Configuration:
```
conf t              # Enters configuration mode
host Fen-R          # Sets the hostname as Fen-R
int gi 0/3/0        # Switches to GigabitEthernet 0/3/0 interface
no sh               # Enables the interface (no shutdown)
ip add 1.1.1.2 255.255.255.0    # Assigns an IP address and subnet mask to the interface
exit                # Exits the interface configuration
int gi 0/1          # Switches to GigabitEthernet 0/1 interface
```

2. Ede-R Configuration:
```
conf t              # Enters configuration mode
host Ede-R          # Sets the hostname as Ede-R
int gi 0/3/0        # Switches to GigabitEthernet 0/3/0 interface
no sh               # Enables the interface (no shutdown)
ip add 1.1.1.3 255.255.255.0    # Assigns an IP address and subnet mask to the interface
exit                # Exits the interface configuration
int gi 0/1          # Switches to GigabitEthernet 0/1 interface
```

3. BiM-R Configuration:
```
conf t              # Enters configuration mode
host BiM-R          # Sets the hostname as BiM-R
int gi 0/3/0        # Switches to GigabitEthernet 0/3/0 interface
no sh               # Enables the interface (no shutdown)
ip add 1.1.1.1 255.255.255.0    # Assigns an IP address and subnet mask to the interface
exit                # Exits the interface configuration
int gi 0/1          # Switches to GigabitEthernet 0/1 interface
```

4. FEN-OMG Configuration:
```
conf t              # Enters configuration mode
host FEN-OMG        # Sets the hostname as FEN-OMG
vlan 10             # Creates VLAN 10
vlan 11             # Creates VLAN 11
vlan 12             # Creates VLAN 12
vlan 19             # Creates VLAN 19
exit                # Exits VLAN configuration
vtp mode server     # Sets the VTP mode as server
vtp domain sinan    # Sets the VTP domain as sinan
vtp password cisco  # Sets the VTP password as cisco
int range gi 1/0/1-5 # Switches to range of GigabitEthernet 1/0/1-5 interfaces
switchport mode trunk    # Sets the interface mode as trunk
exit                # Exits interface configuration
int gi 1/0/4        # Switches to GigabitEthernet 1/0/4 interface
switchport trunk native vlan 19    # Sets the native VLAN for the trunk interface as VLAN 19
exit                # Exits interface configuration
int vlan 19         # Switches to VLAN 19
no sh               # Enables the VLAN interface (no shutdown)
ip add 192.168.19.2 255.255.255.0   # Assigns an IP address and subnet mask to the VLAN interface
exit                # Exits VLAN interface configuration
ip default-gateway 192.168.19.1     # Sets the default gateway for the device
```

5. EDE-OMG Configuration:
```
conf t              # Enters configuration mode
host EDE-OMG        # Sets the hostname as EDE-OMG
vlan 20             # Creates VLAN 20
vlan 21             # Creates VLAN 21
vlan 22             # Creates VLAN 22
vlan 29             # Creates VLAN 29
exit                # Exits VLAN configuration
vtp mode server     # Sets the VTP mode as server
vtp domain sinan    # Sets the VTP domain as sinan
vtp password cisco  # Sets the VTP password as cisco
int range gi 1/0/1-5 # Switches to range of GigabitEthernet 1/0/1-5 interfaces
switchport mode trunk    # Sets the interface mode as trunk
exit                # Exits interface configuration
int gi 1/0/4        # Switches to GigabitEthernet 1/0/4 interface
switchport trunk native vlan 29    # Sets the native VLAN for the trunk interface as VLAN 29
exit                # Exits interface configuration
int vlan 29         # Switches to VLAN 29
no sh               # Enables the VLAN interface (no shutdown)
ip add 192.168.29.2 255.255.255.0   # Assigns an IP address and subnet mask to the VLAN interface
exit                #
