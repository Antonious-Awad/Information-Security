# Information Security
- Securiity can be done to:
	- data
	- program
	- hardware
	- network
- Responsible for protecting:
	- data
	- databases
	- programs
	- assets
	- technologies
	- hardware
	- system
1. Protects the organization's ability to function
	- functionality of the whole system is protected so that the organization can perform its normal day-to-day jobs
2. safe operation of applications implemented in the organization's IT system
		- ex: Transaction process must be protected
3. Protects the data collected & used by the organization
4. Safeguard the technology assets in use at the organization
	- technologies: software, applications
	- should be protected
- --
# Security Attack
- action compromising the security of information
- action damaging any part of the system or the whole system
# Security Mechanism
- Process , device or algorithm designed to detect , prevent or recover from a security attack
- Many mechanisms present
- a combination of security mechanism produce a security service
# Security Service
- a service to counter security attacks
- implementing one or more security mechanism
___
# Ideal Security System
1. Must Satisfy Security requirements
	- a system that can block all attacks with all of its types
2. Efficient
	- i.e can block the attack by what percent?
	- Example:
		- DOS Attack (Denial of service)
		- overloading the server with requests, therefore if you send a request it's lost due to overload
		- efficiency appear in the amount of the requests blocked from the overall number of requests
3. Robust (قوي)
	- Security attacks are always changing
	- the ability of your security algorithm to coop with these changes 
		- cooping can be:
			- immediate blocking of the changed security attack
			- time taken to understand the nature of the attack & block it
4. Easy to implement, easy to use, flexible
	- authentication factors not too much
5. Difficult to satisfy all points
	- every point contradict the other (ex: robust and easy to implement)
---
# Information Security Features
1.  Confidentiality
	- المحافظه علي سريه البيانات و المعلومات الخاصه بجميع منسوبي النظام
	- keeping all system users data safe & protected
	- data is shared only among authorized users
2. Integrity
	- ensure the data is in the order it was input in ,authentic & complete
	- maintaining accuracy  & consistency of data
3. Availability
	- اتاحيه الوظائف الخاصه بالنظام في كل وقت و مكان
	- ensure that the services provided by the system are accessible when needed
# Security Requirements (CIA)
1. Confidentiality
2. Integrity
	- preventing attackers from knowing information about clients
	- preventing clients from modifying unmodifiable data
3. Availability
	- can be breaken by a DOS attack
---
# Vulnerabilities
- main cause for security attacks
- vulnerabilities are classified according the asset class they're related to:
	- Hardware
	- Software
	- Network
	- Personnel:
		- people's behavior can lead to a vulnerabilities
		- ex: employees leaving their user & pass in a note in an obvious area
	- Physical sites:
		- if the area not guarded well
		- Physical security
			- putting your assets in a place accessible to authorized users
			- & not subject to natural disasters
	- Organizational:
		- lack of understanding of managers in the organisation about what security
		- They think they're paying for nothing physical, just some softwares & applications
---
# Threats & Attacks
- Threat: any event of process that can cause harm to any element or part of your system
	- ex: modification or removal of data
	- might be unintended or unplanned
- Attack: event planned & intended to cause harm any to any part of the system
	- Someone studied the system & listed its vulnerabilities & Planned an attack
---
# Security Threats
- Types of threats:
	- Interruption threat
		- ![](_resources/Pasted%20image%2020221226165158.png)
		- Cut of flow of data
		- Simplest Threat
	- Interception threat
		- ![](_resources/Pasted%20image%2020221226165254.png)
		- Flow is not interrupted
		- Intruder gets a copy of each message sent
		- therefore confidentiality of data is lost
	- Modification Threat
		- ![](_resources/Pasted%20image%2020221226165509.png)
		- Intruder receives data, modifies it & sends it to receiver
		- receiver see that the message is sent from the transmitter as normal
	- Fabrication Threat
		- ![](_resources/Pasted%20image%2020221226165704.png)
		- Intruder sends a message to receiver without the need to modify a message from transmitter
		- Intruder fabricates a message stealing the identity of transmitter
		- receiver see that the message is sent from the transmitter
- Threat (keywords)
	-  Malware
	- Trojan
	- Cookie
	- Spam
	- Spoofing
	- bugs
	- spyware
	- sniffing
- **Threats operates on vulnerabilities**
 ---
 # Security Attack
 - Type of Threats
 - **Attacks operates on vulnerabilities but in a planned manner**
 - Attacker can intercept traffic to collect required data to initiate an attack
	 - data collected is analysed to be extract needed data
	 - this data is used in initiating the attack
 - Attacks are classified into 2 types
	 - # passive attack
		 - Data Interception
		 - reading content of messages
		 - traffic analysis
		 - ![](_resources/Pasted%20image%2020221226180155.png)
		-  instead of reading messages
		- attacker starts storing the messages
		- analyzes the message using a software
		- extract sensitive information from analysis
			- ex: ip address, mac address
			- Username, password
			- Account number
		- attacker can be unqualified to use this information & can sell it to a qualified
	- # active attack
		-  attacker can be qualified & use this information in **Identity-theft**
		- ## Masquerade attack
			- Attacker start generating messages sent as the client to the system
			- This is done while the attacker is hidden behind the true client identity
			- Darth send messages sent to alice as bob
		- ## Replay Attack
			- Attacker starts modifying messages sent by the client to the system
			- The attacker is also hidden behind the identity of the client
			- Darth intercepts message sent by bob, modifies it, sends it to alice as bob
			- Examples of modifications that can be done
				- change recepient of a transaction process (change the person meant to receive the money)
				- change the type of process
			- Replay attack can sometime be intercepting the message and sending it at a later time without modifying it (**This doesn't occur in modification attack**)
	
		 - ![](_resources/Pasted%20image%2020221226182242.png)
		- ## Modification Attack
			- Similar to replay attack
		- ## DOS Attack
			- Denial of service attack
			- Attacker over-flood the servers of the system with requests
			- Therefore when the clients try to make a request, servers won't respond
		- ![](_resources/Pasted%20image%2020221226180315.png)
		- ## DDOS Attack
			- Distributed Denial of service attack
			-  Attacker starts hacking servers unrelated to the targeted server
			- these servers are at different locations
			- then the attack commands the hacked servers to send a stream of requests at the same time into the targeted server
		- ## Spoofing Attack
			- IP spoofing: attacker sends a packet with an authorized IP instead of the attacker IP or any other IP
			- ![](_resources/Pasted%20image%2020221226183415.png)
		- ## Sniffing attack
		- ## Man-in-the-middle Attack
			-  Attacker is between transmitter & receiver intercepting their messages to extract **Secret Keys**
			- Attacker starts generate message with the extracted Secret keys
			- ![](_resources/Pasted%20image%2020221226183736.png)
- --
# Protective Measures
1. Bolster Access Control
	- Whether it's Physical or logical access control
		- Physical: physical protection of the assets
		- Logical: Strong password or secret questions or secret codes send to email or phone number
2. Software Updates
	- Software updates usually includes security updates & fixes for software vulnerabilities
	- so it's preferable to keep all softwares updated
	- Manual Update or Automatic update (preferable)
3. Standardize Software
	- Do not use any software from unknown sources
	- this software can be malicious & break up your system or extract data from your device
	- Only use standard software
4. Use network Protection measure
	- Installing a firewall
		- firewall: device that act a monitor
		- Installed on the network
		- monitor all outgoing & incoming traffic
		- firewall should be teached what to allow & what to not allow
		- through 2 concepts:
			- add a list of IPs & URLs where they're the only one allowed to receive & transmit (this list act as a white list & anything else is blocked)
			- add a list of IPs & URLs where they're the only one blocked from receiving or transmitting (this list act as a black list & anything else is allowed)
		- If an attacker was able to have access to an allowed IP address then the firewall is bypassed in this cased
	- Ensure Proper access control
		- a bunch of policies to ensure authorized access
	- IDS (Intrusion Detection System)/IPS (Intrusion Protection system)
		- Analyzes traffic for any suspicious activity
		- if any suspicion is found, block traffic
	- Use Network Segmentation
		-  Each segment has a security policy
	- Use Virtual Private Network (VPN)
	- Conduct proper maintenance
		- Cyclic technical checkup on the network at least every 3 months
5.  Employee training
	- train organization's personnel on the network security
6. Schedule Backups
	- can be:
		- Image of the current network (Duplicate Network)
		- Backup of the data
			- Do not put the backup in the same device or server of the original data
			- put in a different device or system (preferable in a different location)
	- Should Scheduled in a regular manner
		- maybe even in the same moment of inputting the data to the server, it's being backed up