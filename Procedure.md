Step-by-Step Procedure for the Network Configuration in the Provided Topology
Objective:
To replicate and configure the network topology shown in the provided screenshot using Cisco Packet Tracer, and ensure successful communication across the networks.

1. Topology Design Overview
The topology consists of multiple LANs connected through a series of routers to form a WAN. Each LAN contains several PCs connected via switches, and the routers interconnect the different LANs.

LAN Networks: Multiple LAN segments with IP ranges such as 144.186.x.x, 50.152.x.x, and 50.153.x.x.
WAN Network: Interconnection of routers with IP addresses in the range 199.210.121.x.
2. Network Setup in Cisco Packet Tracer
Step 1: Device Placement and Connection
Add Routers:

Add five routers to the workspace.
Label them as Router0, Router1, Router2, Router3, and Router4.
Add Switches:

Add multiple switches to connect PCs in each LAN.
Label the switches accordingly.
Add PCs:

Add PCs to each LAN segment as shown in the image.
Connect PCs to the respective switches using copper straight-through cables.
Connect Routers:

Connect the routers using serial cables to form the WAN links.
Ensure proper connections following the image.
3. Configuration Steps
LAN Configuration
Assign IP Addresses to PCs:

LAN 1 (144.186.96.0/22):
Assign IP addresses within the range 144.186.96.x to 144.186.100.x.
LAN 2 (144.186.112.0/22):
Assign IP addresses within the range 144.186.112.x to 144.186.115.x.
LAN 3 (50.152.0.0/22):
Assign IP addresses within the range 50.152.0.x to 50.152.3.x.
LAN 4 (50.152.128.0/22):
Assign IP addresses within the range 50.152.128.x to 50.152.131.x.
LAN 5 (50.153.0.0/22):
Assign IP addresses within the range 50.153.0.x to 50.153.3.x.
Configure Switches:

No special configuration is needed for switches. Ensure they are correctly connected to PCs.
Connect Routers to Switches:

Use copper straight-through cables to connect the routers to their respective LAN switches.
WAN Configuration
Assign IP Addresses to Router Interfaces:

Router0:
Serial0/0/0: 199.210.121.160/30
Router1:
Serial0/0/0: 199.210.121.164/30
Serial0/0/1: 199.210.121.168/30
Router2:
Serial0/0/0: 199.210.121.172/30
Router3:
Serial0/0/0: 199.210.121.176/30
Router4:
Serial0/0/0: 199.210.121.180/30
Configure Routing on Routers:

Router0 Configuration:

bash
Copy code
Router0> enable
Router0# configure terminal
Router0(config)# interface Serial0/0/0
Router0(config-if)# ip address 199.210.121.160 255.255.255.252
Router0(config-if)# clock rate 64000
Router0(config-if)# no shutdown
Router0(config-if)# exit
Router0(config)# interface GigabitEthernet0/0
Router0(config-if)# ip address 144.186.96.1 255.255.252.0
Router0(config-if)# no shutdown
Router0(config-if)# exit
Router0(config)# ip route 50.152.0.0 255.255.252.0 199.210.121.164
Router0(config)# exit
Router1 Configuration:

bash
Copy code
Router1> enable
Router1# configure terminal
Router1(config)# interface Serial0/0/0
Router1(config-if)# ip address 199.210.121.164 255.255.255.252
Router1(config-if)# no shutdown
Router1(config-if)# exit
Router1(config)# interface Serial0/0/1
Router1(config-if)# ip address 199.210.121.168 255.255.255.252
Router1(config-if)# no shutdown
Router1(config-if)# exit
Router1(config)# interface GigabitEthernet0/0
Router1(config-if)# ip address 144.186.100.1 255.255.252.0
Router1(config-if)# no shutdown
Router1(config-if)# exit
Router1(config)# ip route 50.152.128.0 255.255.252.0 199.210.121.168
Router1(config)# ip route 144.186.96.0 255.255.252.0 199.210.121.160
Router1(config)# exit
Router2 Configuration:

bash
Copy code
Router2> enable
Router2# configure terminal
Router2(config)# interface Serial0/0/0
Router2(config-if)# ip address 199.210.121.172 255.255.255.252
Router2(config-if)# no shutdown
Router2(config-if)# exit
Router2(config)# interface GigabitEthernet0/0
Router2(config-if)# ip address 144.186.112.1 255.255.252.0
Router2(config-if)# no shutdown
Router2(config-if)# exit
Router2(config)# ip route 50.153.0.0 255.255.252.0 199.210.121.176
Router2(config)# exit
Router3 Configuration:

bash
Copy code
Router3> enable
Router3# configure terminal
Router3(config)# interface Serial0/0/0
Router3(config-if)# ip address 199.210.121.176 255.255.255.252
Router3(config-if)# no shutdown
Router3(config-if)# exit
Router3(config)# interface GigabitEthernet0/0
Router3(config-if)# ip address 50.152.0.1 255.255.252.0
Router3(config-if)# no shutdown
Router3(config-if)# exit
Router3(config)# ip route 50.153.128.0 255.255.252.0 199.210.121.180
Router3(config)# exit
Router4 Configuration:

bash
Copy code
Router4> enable
Router4# configure terminal
Router4(config)# interface Serial0/0/0
Router4(config-if)# ip address 199.210.121.180 255.255.255.252
Router4(config-if)# no shutdown
Router4(config-if)# exit
Router4(config)# interface GigabitEthernet0/0
Router4(config-if)# ip address 50.152.128.1 255.255.252.0
Router4(config-if)# no shutdown
Router4(config-if)# exit
Router4(config)# ip route 50.153.0.0 255.255.252.0 199.210.121.176
Router4(config)# exit
4. Simulation
Step 1: Use Simulation Mode
Switch to Simulation Mode:
Change the mode from Real-time to Simulation in Cisco Packet Tracer.
Step 2: Test Connectivity
Ping Across Networks:
Use the ping command from a PC in one LAN (e.g., PC0 in the 144.186.96.0/22 network) to another PC in a different LAN (e.g., PC10 in the 50.152.0.0/22 network).
Example Command:
bash
Copy code
ping 50.152.0.2
Step 3: Observe Packet Flow
Packet Flow:
Observe the packet flow through the switches, routers, and the successful reception of the packet at the destination.
Ensure all devices are correctly configured and routing is operational.
5. Final Configuration Verification
Check Connectivity:
Test connectivity between all LANs to ensure all routing configurations are correct.
Save Configuration:
Save the configuration on each router using the write memory command.
