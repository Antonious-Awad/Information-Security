- Mac layer is made up of different protocol
- the first one is 802.3 CSMA/CD
# 802.3 CSMA/CD
-  Carrier sense multiple access with collision detection
- uses **Ethernet** networks
	- at the beginning it started with data rate = 10 mbps
	- now, data rate can reach 100 gbps
- Protocol used with mac layer
- this protocol can do medium access control
# ALOHA:
-  created by norman from Hawaii university
- consists of two types
	- Pure ALOHA
		- ex:
			- a network with 4 stations & 1 channel
			- all 4 stations wants to send data through this channel
			- all 4 stations will send data to this channel when ready
			- if more than one station sends a frame at the same time
			  or send a frame while another is still being sent will interference **(collision)**
			- time at which interference happened is called collision duration
			- interfered frames are corrupted therefore unusable
		- utilization rate is 18%, 18 frames successfully sent in every 100 frame sent
	- Slotted ALOHA
		- time slots are declared for frames
		- if a station has a frame ready, it holds onto it till the beginning of a time slot
		- if the frame is ready during a time slot, it wait for beginning of the the other time slot
		- 2 stations can have a frame ready at the beginning of the same time slot which will cause collision
		- therefor if 2 frames are sent in the same time slot it will collide and become unusable
		- utilization rate is 37%
# CSMA/CD
- **IEEE decided they will not use ALOHA protocol as an access control protocol**
- Topology used by IEEE is **bus topology**
## MA
- protocol used must provide multiple access
	- all stations should access the network
## CS
- stations can listen to the bus to check if there's any frame being sent before sending its own frame
- this can be done by sensing a signal in the bus cable
- If there's a signal the station won't send its frame
- this process is called **sensing**
- it's called carrier sense not data sense
	- because frame doesn't only contain data
- case:
	- if the bus is empty (no frames being sent)
	- 2 stations do carrier sensing at the same time
	- both will see that the bus is empty
	- both stations will send their frames leading to collision
## CD
- If a collision occurs this will lead to corruption of all frames
- collided frames will reach other stations
- stations receive the collided frames as normal frames which might lead to a disaster
- Collision detection is essential
- collision detection doesn't fix the problem but detects collison only
- only the devices that caused the collision are able to detect the collision
	- after the device sent a frame
	- it senses the bus again after 2 tau
	- if the frame being sent at the bus matches the frame copy at the transmitter station
	- then there's no collision
	- at this point the station start sending the remaining frames it has to send
	  as the bus is acquired to that station
	- if there's a mismatch then there's a collision
	- therefore the station removes the collided frame
	- and the station sends a jamming signal along the bus
		- **jamming signal**: signal with high power
	- other stations will read the jamming signal as notification to reject the incoming frame as it is a collided frame
	- these process occurs also on the other station that  coused the collision
	- after jamming signal is sent
		- both devices might sense at the same time again causing another collision as both devices will see the bus free
		- ### Backoff Algorithm
			-  the solution is to not make them both sense the line at the same time again
				- **HOW?**
					- after the jamming signal is sent
					- a **random time generator** applies random timings to sense the bus for both stations
			- this doesn't prevent collision in overall but prevents collision for these 2 stations only
			- collision is still possible with any other 2 devices
			- therefore, backoff algorithm prevents a second collision after the first one
		- if attempts are too many, and every time there's a collision this will lead to abortion of transmission
# Tau
- **Tau**: time of arrival of a frame from the very beginning of the network to the very end of the network
- reason behind 2 tau is to prevent collision 
	- if it is 1 tau then the signal sent might have not reached the port of the receiver, at this point if the receiver wants to send the data
	- it will sense for carriers and it will find the bus free
# How to implement Ethernet
- ethernet at its beginning was using twisted pair cable
- its feature was called **10 Base T**
	- 10 Base T:
		- 10 &rarr; means the maximum transmitted by this cable is 10 mbps
		- T &rarr; Twisted pair cable (100m theo. / 80m parctilcally)
		- Base &rarr; Base band transmission
		- ![](Information-Security/_resources/Pasted%20image%2020221217145018.png) 
- Communication has two types of sending signals
```markdown
Base band transmission: takes the signal form the transmitter and sends it directly to the channel
	 - Base: اساسي
	 - Band: group of frequencies in the signal
- taking the signal it its baseband form and sending it to the channel
- used as long as the distance to send a signal is short(<=100m theortically) (<=80m Practically)

Transmission With Modulation:
- used with distances (>80m)
```

- Coaxial cables:
	-  10 Base 5:
		- 5 &rarr; 500m
	- 10 Base 2:
		- 2 &rarr; 185m
		- 2 instead of 185 because it's only a 1 digit slot
- Fast Ethernet:
	- transfers at 100mbps
	- uses twisted pair or fiber cable
- Giga Ethernet:
	- transfers at 1,10,40,100 gbps
# 802.3 Frame Format
- ![](Information-Security/_resources/Pasted%20image%2020221217154532.png)
- frame format is based on HDLC frame format
## Flag
- beginning of frame
- similar to flag in HDLC
- the reason behind not using a flag at the beginning and end of frame (like HDLC) is to reduce overhead
	- this overhead can be varying and immeasurable as it can decrease or increase according to the amount of bit stuffing 
- at the beginning, they deduced that if the flag size is 64 bit(8 bytes) is is impossible to be repeated in the data divided into 2 sections
	- 1<sub>st</sub> section is 56 bits(7 bytes) &rarr; preamble
	- 2<sub>nd</sub> section is 8 bits (1 byte)&rarr; start frame delimeter (SFD)
## Destination Address
- 6 bytes
- Physical address
## Source Address
- 6 bytes
- Physical address(MAC)
## Length (type) Field
- 2 bytes
- contains length of the frame
## LLC Data
- contains user data
- minimum size: 46 byte
- maximum size: 1500 byte
- if the data is larger than 1500 byte is can be separated into more than one frame
- if data is less than 46 byte, then use the PAD
## Packet Assembler Disassembler (PAD)
- used with dummy signals (data less than 46 byte)
- used to make the dummy bits size = 46 byte
	- ex: 1 byte dummy signal, therefor the PAD size is 45 byte
## Frame Check Sequence (FCS) (CRC)
- error control

## MAC address
- MAC address is found in the NIC of the device
- 6 bytes for both fields (DA, SA)
- 48 bits divided into 2 parts (24 bits each)
- first 24 bits are called vendor ID (distributed to each vendor)
- 2<sup>24</sup> different vendor ID
- second 24 bits are called card ID (one code for each card produced by one specific vendor)
- Hexadecimal format
- ![](Information-Security/_resources/Pasted%20image%2020221217172617.png)