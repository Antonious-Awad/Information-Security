# Local Area Network (Switching)
## contents:
- LAN application
- LAN Architecture
- Who are meant to make a standard for LAN
- Ethernet
- Token Ring
	- used in large establishments
- FDDI
	- used in Industrial areas (petrol fields, electric networks)
- LAN Design

---
# Applications
- Personal Computer LAN
	- router with a limited no. of ports accompanied with **RJ45** ethernet cable
- small companies
- Backbone Network
	- used in large buildings
- Back end network
	- multiple device interconnected which share processing power
	- high data rates
- SAN
	- data is stored in a storage device
	- servers access storage device
	- server- based storage
		- ![](Information-Security/_resources/20221215123346.png)
		- this architecture's disadvantage is that if a server fails you've lost access to the storage device connected to it
	- storage area network
		- storage devices are connected in a network with each other
		  which is called **storage area network**
		- ![](Information-Security/_resources/20221215123524.png)
		- if a server fails the storage device can still be accessed by other servers
- high speed office network

---
# Architecture
- topology
	1. bus
	2. ring
	3. star
	4. tree
- transmission medium
	1. twisted pair
		- shielded
		- unshielded (UTP)
			- one used in industry
			- used in short distances
			- range 80m-90m
			- limited data rate (100mbps)
	2. Optical fiber
		- ranges >90m
		- multi node fiber
			-  ranges > 90m but not so long (doesn't reach 1 km)
		- single node fiber
			-  range can reach kilometers
			- expensive
		- high data rate
	-  <u>Choice of transmission meduim based on:</u>
		- topology
		- capacity(bandwidth)
		- Reliability(الاعتماديه)
			- sensitive data: 
				- Wireless option is excluded
				- UTP is excluded also (unsecure) (wire can be easily split and connected to another device)
				- Fiber is the optimal solution 
		- types of data supported
			- text
			- VoIP (voice over IP)
			- MMS
			- video
			- documentation
		- Environmental scope
			-  some environments force you to choose a specific transmission medium ex: Hospital
---
# LAN Protocol Standard
- IEEE are the responsible group 
- Group 802 works on a specific issue and the goal is to release a standard for the issue
- they choose OSI model as a reference model for their model
# IEEE 802 Reference Model
- based on OSI reference model
-  User support layers in OSI Model (Application, Presentation, Session &transport) are left unchanged in IEEE 802 Model
- Network support layers in OSI model (network, data link, physical)
	-  Network layer:
		- responsible for routing, routing is unchanged in IEEE 802
		- logical address is also unchanged
		- the only thing changed is the addition of **Inter networking Protocol (802.1)**
			- Inter networking protocol: connection between various devices
	- Data Link Layer:
		-  contain multiple standards
		-  data link layer separated into 2 sub layers
			- Logical Link control (LLC)(upper sublayer)(802.2):
				- things that are common in LAN networks
			- Medium access control (MAC) (lower sub layer)(802.3):
				- things that differentiate each lan network
	- Physical layer
		- meduim and cable type are choosen according to data link layer
- 802.3 uses ethernet
- starting from 802.11 are wireless LANs(wi-fi)
- 802.16 is wi-max
	- wi-fi's max range 50m-100m
	- wi-max can reach kilometers of range
	- wi-max is only used in military and didn't reach the public

# IEEE LLC layer(802.2)
- Interfaces with higher layer (network)
- Flow control using sliding window
- error control
# IEEE MAC Layer
- responsible for frame formation
- adding hardware address (MAC address)
	- mac address is names like this because it's put by the MAC Layer
- Access control
	- a network have limited number of resources and unlimited number of users
	- all of these users wants to access the network
	- MAC Layer organizes access to the network
	- MAC is short for **M**edia **A**ccess **C**ontrol

---
# Encapsulation
## LLC
- once the data reaches the LLC layer
	- it starts adding its own header
	- which consists of:
		- DSAP (destination service access point) - 1 byte
		- SSAP (source service access point) - 1 byte
		- Control - 1 byte
	- DSAP
		- only first bit is used
		- bit #1 = 0 &rarr; frame sent to individual station
		- bit #1 = 1 &rarr;  frame sent to group of stations
	- SSAP
		- only first bit is used
		- bit #1 = 0 &rarr; frame is a command frame
		- bit #1 = 1 &rarr;  frame is a response frame
	- control field
		- same as HDLC control field
- data is put into information field
- LLC header + information = Packet Data Unit PDU
- ![](Information-Security/_resources/30221216010724.png)
## MAC
- MAC layer starts adding its own header & trailer
	- header consists of:
		- Destination MAC address
		- Source MAC address
			- both these addresses are hardware physical addresses
- in HDLC header & trailer had a flag at their beggining and end
- in IEEE 802 header starts with a flag but no flag at the end
-  IEEE 802 provided the length of the frame along with start flag
- flag is composed into 2
	1. preamble
		- 56 bits (7 bytes) sequence
	2. start field delimiter
		- 1 byte
- address fields are 48 bits each (6 bytes)
- frame length field
	- contain length of the frame
- Trailer:
	- Cyclic Redundancy check (CRC)
		-  = FCS in HDLC
		- error detection & control
___
# MAC naming
- Media access control
- how does it control access?
	- where is the control?
		- centralized control: 1 unit controlling the whole system called control unit, all information about the network is at this centralized unit
			- advantages: fast response 
			- disadvantages: single point of failure
		- distributed control: all devices share in decision making, share in data
			- advantages: no single point of failure, multiple devices if one fails network isn't affected
			- disadvantages: hard & complex
	- how is it done?
		- synchronous
		- asynchronous
			- round robin: gives a turn to each station
			- Reservation: gives priority to each station and reserves a specific place for them
			- contention: random order
				-  all stations contend for time