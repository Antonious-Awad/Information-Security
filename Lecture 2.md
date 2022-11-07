# Network
## Benefits of network
1.  Share Data
2.  Share Hardware
3.  Share Software
4.  Share applications
5.  Share Services
6.  Share Information
---
## Terminology
- Station: Terminal (end Device / Host) used by user to access the network
-  Network: collection of interconnected <u>stations</u>
-  Node: a point where one or more connection line terminates
-  Subscriber line: a line that holds traffic of the station(Terminal -> network)
-  Trunk: a line that holds traffic of all data recieved by the switch or router(Within network , between nodes and each other)
-  Topology: logical manner in which nodes are linked together by information transmitting channels to form a network هندسيه توصيل الشبكه
---
## Main Components on network
## These devices are essential for any network:
- End Devices: Stations / hosts / terminal used by users of the network to login in to it (Any device that can transmit and recieve data)
- Network Devices: ex switch , router
	-  Consist of 2 types :
		-  one used to build the network
		-  one used to connect the network (internetworking devices)
- Connectivity:
	- Wired:
		- Copper (Unshielded twisted pair cable UTP)
		- Fiber
	- Wireless:
		- requires extra devices: access points, wireless card

## Restrictions of network Media:
1. <u>Distance</u> from source to destination
	- UTP: max distance 80m - 100m
	- Fiber: >100m
2. <u>Environment</u> it works in
3. <u>Bandwidth</u>
	- depens on the use of the network
5. Cost of medium
6. Cost of connectorst & equipment
## Network criteria
1. Performance:
	-  response time &darr; , performance &darr;
	-  extendable
	-  scalabe
3. Reliability
	- Frequency of failure (ex: once per month)
		-  frequency &uarr; , reliability &darr;
	- Time it requires for a link to recover from failure (recovery time)
		- Recovery time &uarr; , reliability &darr;
5. Security
	- secure network
	- secure information
---
# Configurations
## Line configuarion (Link configuration)
-  Direct Link : line connecting transmitter and reciever directly
-  Point - to - point: line connecting transmitter and reciever with intermediate stages in between
-  Multi-Point: more than 2 devices sharing same medium

## Network Topology
- How devices are connected together
- Two types:
	- Physical Topology: how devices are physically cabled
	- Logical Topology: how devices communicate or how data moves across physical topology
---
# Physical Topologies
1. ### Bus Topology:
	- Single Backbone cable
	- all hosts are connected to backbone
	- logical topology: one host send data, data move through the bus and reaches all hosts 
2. ### Ring Topology:
	- physical ring of cables
	- connects first host to the next and the last one to the first one
	-  logical topology: if first sends to last, data must pass through all hosts till it reaches the last
	-  if one host fails the whole network fails
 ![edb1747a7d482c9db9964299c3925dac.png](../../../_resources/edb1747a7d482c9db9964299c3925dac.png)
 3. ### Star Topology:
	 - contains a switch
	 - logical topology: point - to - point / star
	 -  It also can be a bus logical topology if all ports leading to hosts are open
	 -  It also can be a ring logical topology if a port leads to then next one and so on and the last port leads to the first port
	 -  has a single point of failure: if the switch fails
	  ![8880c75a67455fb3aa6ab9425a3b598d.png](../../../_resources/8880c75a67455fb3aa6ab9425a3b598d.png)

4. ### Tree Topology:
	- Called Extended start and in a hierarchical form
5. ### Mesh Topology:
	- All Devices are connected to each other
	- Not used because it's so costly
	- can be used in very small networks and contains crucial data because it has high security
6. ### Hybrid Topology:
	- Hierarchical form containing different topologies
---
# Transmittion Mode
- depends on the end devices of the network
- Types:
	1. Simplex:
		- one transmitter and one reciever
		-  data flow in one direction
		-  ex: humidity sensor , pressure detector
	2.  Half Duplex:
		- both stations are transmitter and reciever
		- only one transmit at a time
		- data flow in both directions but at different timestamps
		- phone call
	3.  Full Duplex:
		- both stations are transmitter and reciever
		- both can transmit simultaneously
		- data flow is in both directions
		-  Maching to machine communication
---
# Network Types
## Based on coverage area
- Local Area Network (LAN):
	-  Small geographical area (<= 500m) 
- Metropolitan Area Network (MAN):
	-  Group of LAN networks within a small area
- Wide Area Network (WAN):
	- Group of LAN networks with a large area
	- made using Digital Subscriber line (DSL)

```cpp
Internet: Internetworking
internet: internet service
```