# Communication system

- a simple communication system consists of 5 main components:

1.  Sources
    
    - Produce data
    - not necessecarilly ready signal
    - can sometime produce ready for transmission signals (ex: if it is produced from a computer)
2.  Transmitter (Transducer)
    
    - Turns data into transmittable signal
        
    - transmitter can turn data into various signal types
        
        - optical signal in case of fiber wired communication
        - electrical signal in case of copper wired communication
        - electromagnetic signal in case of wireless communication
    - contains modulator which does modulation of data
        
    - contains multiplexer which can turn multpile signals into a single signal (ex: 1000 signal into 1 signal)
        
    - contains compressor which does data compression
        
    - contains encryptor which encrypts data(encryption)
        
3.  Transmission channel "Medium"
    
    - transmits signal from transmitter to receiver
    - can contain <u>channel impairments</u>
        - phase shift
        - attenuation
        - distortion
        - drop delay
        - acceleration
    - external signals can interfere causing noise
    
4.  Receiver
	- reverses all processes done by transmitter to return the signal into its original data form
	- contains:
		- demodulator
		- demultiplexer
		- decompressor
		- decryptor
5.  Destination
	- receives data

* * *
# Types of communication
1. Human - to - human communication
	- doesn't require maintainance
2. Machine - to - machine communication
	- contains a **communication protocol**:
		- communication protocol: a set of instructions that control the process of sending and receiving the data 

---
# Analog & Digital data transmission
- data
	- can be analog or digital 
- Signaling(اشارات اشرافيه):
	- Physical representaion of the signal moving along a medium
- Signal:
	- Representaion of data
- Transmission:
	- communication of data by propagation and processing of signals

---
# Compression
- reducing the size of data through an algorithm
---
# Multiplexing
- sending more than one signal over a single channel
- not confused with Adder (adds signals to each other without differentiating them) which cannot seperate signals after adding them
- done by a multiplexer
- the signal emitted from multiplexer is called multiplexed signal
- many to one device
- there are many dimensions which can mark each signal to differntiate it from another:
	- code 
		-  Code division multiplexing (cdm)
		-  each signal is sent with a specific code that defines the receiver
	- frequency
		-  Frequency division multplexing (fdm)
		-  depends on the amount of availabe bandwidth
	- wavelength
		-  Wavelength division multiplexing (WDM)
		-  Optical signals only
	- time
		- Time dvision multiplexing (TDM)
		- every signal is sent at a different time
	- voltage
		-  Voltage division multiplexing (VDM)
		-  used in tv
		-  every signal is sent in a different voltage 
# Demultiplexing
- seperating multpilexed signal into many signals
- one to many device
- done by a demultiplexer