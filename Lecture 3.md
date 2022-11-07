# Network Reference Models

- open system interconnection model (OSI-model)
    - Made by ISO
    - 7 Layers
- Transmission control protocol over internet protocol (TCP/IP Model)
    - Made by darba
- IEEE Model

* * *

## <u>OSI Model</u>

- Consist of 7 layers
- Started as 3 layers ↓ :
    1.  Network Access layer
    2.  Communication Service layer
    3.  File transfer layer
- 3 layers were not enough
- ISO settled on 7 layers:
- From bottom to top ↓ :
    1.  Physical layer
    2.  Data link layer
    3.  Network layer
    4.  Transport layer
    5.  Session layer
    6.  Presentation layer
    7.  Application layer
- 1<sup>st</sup> and 2<sup>nd</sup> layer consist of hardware and software
- other layers consist of software only
- Layer 1,2 and 3 are called network support layers
- Layer 4,5,6 and 7 are called user support layers
    ![a8720f852c28548b00f14d3da5d5dd18.png](../../../_resources/a8720f852c28548b00f14d3da5d5dd18.png)

### <u>7\. Application Layer:</u>

It's the service provided through an application (ex: Email, Web Browser ), it's used to represent a user interface to the network.
Each application uses a set of known instructions (Protocol).

- Email --> SMTP (Simple Mail Transfer Protocol)
- FTP (File Transfer Protocol)

### <u>6\. Presentation Layer:</u>

- Has Two main jobs:
    - Compression
    - Encryption

### <u>5\. Session Layer:</u>

- Establish session
- Ensure that all information required for opening a sessions is available
- Manage session
- Terminate session
- Each session contain user data

### <u>4\. Transport Layer:</u>

- Collects all available sessions in a single connection
- Data segmentation
    - segments data into frames to be sent to the network
- Data Sequencing
    - rearrange the frames sent in order to be understood by the reciever
- End - to - end check
    - happens between first source and final destination
    - check: data analysis between the 2 ends in terms or errors and data flow
- Error detection
- Error correction at both ends
- Data Flow Control
    - both source and destination must equalize their data transport speed
    - Flow : Control speed and Control the amount of data transported

### <u>3\. Network Layer:</u>

- End - to - end Delivery
- Routing (Choosing the optimal route to destination)
- Logical address (IP Address)(ex: IPV4, IPV6)
    - adds logical address of destination and source

### <u>2\. Data Link Layer:</u>

- Hop - to - Hop :
    - From a device to another
- Does the following:
    1.  Hop - to - hop data delivery
    2.  Hop - to - hop addressing(adding Physical address *mac adress* for source and destination)
    3.  Hop - to - hop Error detection & correction
    4.  Hop - to - hop flow control
- Finalizing the frame form (standard frame format)

### <u>1\. Physical Layer:</u>

- responsible for all physical properties:
    - cable length
    - cable type
    - bit rate (speed)
    - voltage levels
    - Hardware interface types
- recieves the frame

Transmitter: data moves from layer 7 -> layer 1
Reciever: data moves from layer 1->layer 7

* * *

## <u>TCP/IP Model</u>

- Developed by DARPA
- UDP model before
    ![4cd385daf913992352547b21516fb2a0.png](../../../_resources/4cd385daf913992352547b21516fb2a0.png)
- 5 layers:
    1.  Network access layer
    2.  Internet Layer
    3.  Transport Layer
    4.  Application Layer
        ![d6e23668d4b2088181a34a522ff1ff3b.png](../../../_resources/d6e23668d4b2088181a34a522ff1ff3b.png)
- OSI model and TCP/IP model are different in the protocols used for each action

* * *

# Encapsulation Process

## OSI Model

- only first source and final destination will need the user support layers(4,5,6,7)
- every node and device must have a network support layer (1,2,3)
    ![46724bc90a915b4d49426bb66d894237.png](../../../_resources/46724bc90a915b4d49426bb66d894237.png)
- Each layer adds its own header as we go down the layer of transmitter device
- only the application layer and the physical layer that do not add it's headers(layer 1 & 7)
- Data link layer is the only layer that adds a header and a <u>trailer</u> (Layer 2)
    ![91d99f71a713c2cc7580e0f1127d5e06.png](../../../_resources/91d99f71a713c2cc7580e0f1127d5e06.png)

# Decapsulation process

- reversing the encapsulation process
- happens at the reciever
    ![0fd548c47f97fb26665204e5407b518c.png](../../../_resources/0fd548c47f97fb26665204e5407b518c.png)

* * *

## Physcial vs logical address

Physical (Mac / Hardware) address:
\- only 1 version of it exists
\- made during manufacturing of the device

Logical (IP) Address :
\- Assigned when you first sign in to the network
\- if you change networks you will get a new address

- both addresses are used when sending and recieving data
- physical layer : data communication in bits format
- data link layer: data communication in frame format
- network layer: packet format
- transport layer: segment format
- session. presentation, application: data format

* * *

# Network Devices capabilites

- Hubs -> undestands physical layer only
- amplifier, repeater, poster-> physical layer only
- bridge, switch -> physical , data link layers
- Router -> physical , data link layers and can reach ip address and understands routing