## Why do we use reference models
- Guarantee compatibility
- Integrity

# Data Transmission
- Parallel
- Serial
	- Synchronous
	- Asynchronous
---
## Parallel Transmission
- All bits are sent together at the same time
- Each bit needs a communication channel
- Parallel transmission is effecient but is rarely used due to its cost
- used in dual computer bus communication
- --
## Serial Transmission
- bit - by - bit transmission
![5a683d2a999578391b48175bb5762f0f.png](../_resources/5a683d2a999578391b48175bb5762f0f.png)
- This tramission can have data loss in order to a lost bit
- In order to fix this a flag is added at the start and end of each bye
- The flag is called start bit and end bit
- act is a notification for the reciever of incoming data
- Start bit is usually one bit only 
- Stop bit can be 1 bit or 2 bit or 1 and a half bit 
	- 1 and a half bit : a Pulse is sent whose width is equal to one and half bit and It's preferrable because it's special in its width in compare to other bits
- The stop and start bits are called overhead bits and are sent in through the user's bandwidth which lead to reduction in the expected speed
- I.E: Overhead bits &uarr; will lead to Data transmission efficiency &darr;
- Overhead percentage: percentage of data lost due to overhead bits
	-  % = No. of overhead bits / Total No. of transmitted bits
- The following transmittion explained is called <u>**Asynchronous Transmission**</u>
- Asynchronous transmissions are not dependant on in terms of networks
- only used in real time communication (real time chat)
# Synchronous transmission
- same as asynchronous but instead of adding overhead bits to a byte we add them to a large block of data (frame)

# Physical layer of OSI-Model
- uses:
	- determines the signal
	- determines the network
	- cable type
	- cable length
	- bit rate
	- mechanism of transmission 
## DTE - DCE Interface
- DTE: 	Data terminal equipment
	- can be simplified as a router
	- takes data and sends it to the netowrk
- **RS232 Standard**:
	- one of the most common physical standard protocol in the market
	- Data:
		- 
		- 0 -> positive value ranging from +3 to +15
		- 1 -> negative value ranging from -3 to -15
		- the reason behind neglecting the valus from +3 to -3 (undefined area) : 
		  - 
			- to avoid the noise from inverting positive values to negative values and vice versa
			- minimizing error				
![31bd02258915f4cf1124d390d7acb1d8.png](../_resources/31bd02258915f4cf1124d390d7acb1d8-1.png)
	- Control Signal:
		-
		- Two states: on or off
		- Can be affected by noise therefor the area from +3 to -3 is also neglected
		
## DTE- DCE Serial Connectors
- DTE is always male
- DCE is always female
- Ex: EIA/TIA-232 , EIA/TIA-449 , V.35

### EIA-232 / RS-232(مش حفظ):
- 25 pins
- Data pins:
	-  2 = transmite data
	-  3 = recieve data 
	-  14 = secondary transmission data
	-  16 = secondary recieption data
	-  ![593b0f818e34234dd5b32a16db52729b.png](../_resources/593b0f818e34234dd5b32a16db52729b-1.png)
- Control Pins:
	- 4 = Request to send (on signal, off deactivate)
	- 6 = DCE ready (on signal activate , off deactivate)
- 1 = shield (protects from overcurrent)
- 7 = signal ground (common ground) , 0V -> life pin is 220V more than ground

### Transmission steps (Important):
#### _Synchronous full duplex transmission_:
1. shield & ground (both)
2. DTE - DCE ready (both)
3. Request to send (device 1)
4. Clear to send (device 1)
5. Recieved line signal detector (on device 2)
6. Request to send (device 2)
7. Clear to send (device 2)
8. Recieved line signal detector (on device 1)
9. transmit data (device 1)
10. transmitter signal timing (devcie 1)
11. Recieve data (device 2)
12. reciever signal timing (device 2)

---
# Error Detection and correction
- Error: alteration of condition of the signal (ex: bit with value 0 turn to value 1)
## Types of error:
- Single bit error:
	- alteration of one bit from 0 to 1 or vice versa. 
- multiple bit error
	-  alteration at different bits with <u>**varying distances**</u>
- burst error
	- alteration of multpile bits <u>**close to each other**</u>
	- i.e: occurs at a block of bits
## Error Detection process
1. Data goes from the transmitter through a process
2. the output (Redundancy check bits) of that process is then sent to the reciever
3. then it's passed through the same process 
4. the output is then passed through a comparator along with the first result of the process from the transmitter
5. the comparator then compares the 2 results , if there's a mismatch then there's an error

- The idea here is to find a process with high detection capability and low amount of overhead bits

### Error Detection methods:
- Cyclic Redundancy check (CRC)
- --
## Error Correction
- Forward error correction:
	- used in critical systems where there's no time vacancy to ask the transmitter to resend the data
	- similar to detection process but the the output of the comparator is a code determining the location of the error 
	- disadvantages:
		- the resultant number of bits is large (not larger than the hardware but still considered large)
		- very complex hardware
- Backward error correction:
	-  error can't be fixed and the transmitter is asked to resend the data
