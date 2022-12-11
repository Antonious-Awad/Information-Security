# Data Link Control
- Line Discipline protocol:
	- Deciding who has the permission to send data accross the network
	- Who should send now?
-  Flow Control:
	-  decides the amount of data sent through the netwok
	-  How much data may be sent?
-  Error Control:
	- Controling errors in data
	- How can errors be detected?

- Each of these protocols may seem separated but in fact are collect in one standard protocol
---
##  **_Line Discipline_**
-  no one can send data in a network unless authorized
- Two types of networks uses two types of Line Discpline:
	- Peer to Peer (point to point)
		- uses enquiry acknowledgment protocol
	- Client Server:
		- uses pull select protocol
### ENQ/ACK
- used in peer to peer communications
![[_resources/Pasted image 20221126140006.png]]
#### Connection establishment
- The device that wants to send data sends an  enquiry (ENQ) message first
- ENQ msg & ACK msg are codes.
- Device waits for response in order to be able to send data.
- The response can be a rejection. 
	- Rejection can be for various reasons, ex:
		- Destination device can be involved in another communication
- If the station is clear to recieve the data it will send an acknowldgment (ACK) message
- if the response is positive (positive acknowldgment) then the connection is established 
#### Data transfer phase
- after **connection establishment** the transmitter starts sending the data
- the transmitter cannot continue to send the data unless a response (+ve acknowldgment) has been recieved 
#### Connection Termination
- after sending all data the transmitter sends an EOT (end of transmission) which terminates communication from <u>the transmitter side</u>
### Poll/Select
- used in client server communications
- server is called primary, end devices(client) are called secondary
#### Select
- when the server wants to send data to one of the clients
- server send a select method (which contains the address of the user of interest to receive the data)
- the select message passes to all clients in the network
- only one will recognize the address and sends the acknowldgment (ACK)
- the client can also respond by refusing the SELECT method 
#### Poll
- used when a user wants to send to another user or the server
- server sends a POLL message containing the address of one user
- The server doesn't which user wants to send data
	- Therefor, the server will send a poll message each time with a different user address 
	- The order in which the users are arranged can differ (ex: round robin algorithm, priority list)
	- If the user responds with NAK (negative acknowledgment) then this user doesn't want to send data, or doesn't have data to send
	- The user will start sending data if It has data to send after receiving the poll message
---
## **_Flow Control_**
- Control flow of data
- control the amount of data sent by any user 
- Two Different Protocols:
	- Stop & Wait
	- Sliding Window
### Stop & Wait
- also known as: Send one frame, stop transmission & wait for acknowledgement
- sends one frame and waits for acknowledgment
- destination can stop flow by not sending acknowledgment

- continuous transmission is not preferable because in case of error receiver may ask sender to send data again which maybe lost

### Sliding Window
- Window: a varying amount of frames sent together (window size)
- window size (W): 3, 7, 15, 31 or 63 frames (2<sup>k</sup> - 1)
- numbering of frames starts from 0
- If W=7, transmitter sends 7 frames (from 0 &rarr; 6)
	- Receiver send the acknowledgment as soon as it receives the first frame
	-  this ACK verifies that the first frame has reached the receiver successfully
	- the ACK can reach the transmitter at any time as long as it is received before sending the last frame(frame number 6 in our example)
	- once the transmitter receives ACK 0 (that verifies receiving of frame 0 ) it means that frame 0 is no longer needed by the transmitter and can get rid of it
	- therefore, the window slides and the starting frame become frame 1 not frame 0 and the final frame become frame 7 instead of frame 6 
	- ACK 1 recieved &rarr; windows slides &rarr; frame 1 removed &rarr; start: frame 2, end: frame 8
	- if ACK 0 is not received at the first place(after sending frame 6), transmission stops
	-  through this means flow of control is achieved + transmission continuously
	- 1 ACK received = you can send one more frame
	- 3 ACK received= you can send 3 more frames
- <u> **round trip delay** </u>: the time required for one frame to reach the receiver after being sent from the transmitter, then processing it and sending back the ACK to the transmitter (زمن ارسال فريم و الرد عليه )
- *window transmission time* = round trip delay * W(window size)
- window transmission time must be larger than the round trip delay
	- if this is achieved you guarantee that there's at least one acknowledgment received before reaching the end of the window
- **Heavy traffic** can affect largely on round trip delay.
	- Round trip delay with heavy traffic > expected round trip delay
	- Round trip delay with heavy traffic > window transmission time
- can lead to Increase in Waiting time
- in Stop & wait, you send a frame then wait for ACK
- in Sliding Window, you send W frames then wait for ACK
- Sliding window is more commonly used 
---
## **_Error Control_**
- _Error Free Transmission_: a complete transmission without errors
-  Errors:
	- Lost frames
		- ex: switch receiving frames while having a full storage capacity
	- Damaged Frames
	- lost ack
	- damaged ack
### _ARQ_
- Automatic Repeat Request
- applied to flow control protocols (stop & wait, sliding window)
- backward error control (resending of data)
- steps:
	1. error detected(in a frame or in an ack)
	2. receiver request from current transmitter to repeat frame with the error

#### Stop & wait
- If receiver finds an error in received frame, he will
	-  send -ve ACK
		- then the transmitter receives the ack and resend the frame
		![[_resources/Pasted image 20221210192056.png]]
- If receiver didn't receive the frame (frame lost):
	- transmitter waits for maximum waiting time (which is the time of round trip delay) 
	- if transmitter didn't receive an ACK during waiting he will resend the data
- if transmitter didn't receive the ACK (ACK lost):
	- transmitter might resend the data because it didn't receive the ACK after waiting time 
	- in this case there will be a **Duplicated Frame**
	- this **Duplicated Frame** must be identified
	- after identifying this frame, the receiver reject this frame & reply with ACK
- if transmitter received an ACK with an error:
	- same as ACK lost leaving it for the receiver to identify the **Duplicated Frame**
#### Sliding Window
##### selective reject / selective repeat
- If W=7
-  w = 2<sup>k</sup> -1 is due to:
	- if w = 2<sup>k</sup> alone then the final frame in the window will not be recognizable in the new window
	- ex:
		- if w = 8, it will send from frame 0 &rarr; frame 7, if there's an error and the transmitter is resending data then the receiver will be anticipating frame 0, in this casa the receiver will never know if there's any duplicated window
		- if w = 7, it will send from frame 0 &rarr; frame 6, if there's are an error and the transmitter is resending data then the receiver will be anticipating frame 7, which helps in detecting duplication
- frame 3 has an error
	- transmitter will get a NAK (-ve acknowledgment) at frame 3
	- transmitter will resend frame 3
	- receiver must have a sorting algorithm in order to reorder the frames in their right way
	- sorting must happen after receiving all frames
	- costs high processing power as processing occurs after receiving all frames and sorting them in the right order
- if frame 3 was lost:
	- receiver will sends a NAK when it receiver frame 2 &rarr; frame 4
	- then the same as frame damage occurs
- ACK Lost/ Damaged:
	- transmitter waits the waiting time
	- transmitter resend data
	- receiver receives data thinking it's new data (**Duplicated Window**)
	- receiver detects duplication based on Window Size (2<sup>k</sup>-1)
##### Go Back N
- once an error is found in a frame N, receiver dumps the frame and any other frame received after it
- receiver sends a NAK to transmitter
- transmitter sends frames again starting from frame N
- doesn't require sorting
- if frame N was lost:
	- receiver will sends a NAK when it receiver frame 2 &rarr; frame 4
	- then the same as frame damage occurs
----


- ACK are overhead bits
- In Sliding window:
	- the receiver doesn't send ACK for ever frame sent (to reduce overhead)
	- receiver sends ACK N 
		- which means receiver received previous frames and is waiting for frame N
		- ex: ACK 3 = I'm waiting for frame 3 and I received the previous frames (0,1,2) successfully
	- This is called **Multiple frame Acknowledgment**
	- this should be optimized as the ACK is sent before the transmitter reaches EOT