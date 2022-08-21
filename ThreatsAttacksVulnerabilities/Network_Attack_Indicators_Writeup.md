# Chapter 4
# Network Attack 

---
## What is Wireless? 
**Def: A common networking technology that has a substantial number of standards and processes to connect users to networks via a radio signal, thus freeing machines from wires.**

- wireless networking is a target for hackers since it removes physical barriers

## Wireless Attacks
---
### Evil Twin
**Def: an attack against the wireless protocol via substitue hardware.**

- This attack uses an access point (AP) owned by an attacker that usually has been enhanced with higher-power and higher-gain antennas to look like a better connection to the users and computers attaching to it.
- By having users connect to the "evil twin" attackers can more easily launch DoS or man in the middle-type attacks
---
### Rogue Access Point
**Def: by setting one up, an attacker can attempt to get clients to connect to it as if it were authorized and then simply authenticate to the real AP.**

- This gives an easy way to access the network and the client's credientals.
- Rogue AP's can act as a man in the middle and easily steal uer's credentials.
- They are usually placed on an internal network by accident or for nefarious reasons
- They are not administered by the network owner or administrator

#### The difference between Evil Twin's and RAPs
An evil twin is an AP that appears to be legitimate but isn't and is often used to eavesdrop on wireless communications while a RAP is is something on the network placed there on purpose or by accident

---
### Bluesnarfing
**Def: similar to bluejacking, instead of sending an unsolicated message to the victim's phone, the attacker copies off the victim's information**

- This attack is employed via bluetooth
---
### Bluejacking
**Def: Sending unauthorized messages to another bluetooth device. 

- Typically involves sending a message as a phonebook contact and then the attacker sends the message to the possible recipient via Bluetooth.
---
### Disassociation
**Def: an attack designed to disassociate the host from the wireless access point and from the wireless network.**

- Stem from the the de-authentication frame that is in the IEEE 802.11 (Wi-Fi) standard

- Originally, the de-authentication frame acts as a tool to remove unauthorized stations from a Wi-Fi access point, but because of the design protocol, these frames can be implemented by virtually anyone. 
	- The attacker only needs to have the MAC address of the intended victim, which enables them to send a spoofed message to the access point, specifically spoofing the MAC address of the victim machine.
- This results in the disconnection of the victim machine, making this attack a form of denial of service

- These attacks are not typically used alone. For instance, if you disassociate a connection and then sniff the reconnect, you can steal passwords.

- Note: Wifiphisher is a security tool often used by the red team in penetration testing that mounts automated phishing attacks against Wi-Fi networks in order to obtain credentials or infect victims with malware.
---
## Jamming & Jamming Attacks
**Def: A form of denial of service that specifically targets the radio spectrum aspect of wireless. **

---
### Radio Frequency Identification 
**Def: Used in a wide range of use cases. From tracking devices to keys, the unique serialization of these remotely sensible devices has made them useful in a wide range of applications.**

- Can be classified as either active or passive
	- Active tags have a power source while passive have the RF energy transmitted to them for power. 
- RFID tags are used as a means of identification and they have an advantage over barcodes because they do not have to be visible, just within radio wave range

- There are multiple security concerns
	1. Because they are connected via RF energy, physical security is a challenge
	2. Several standards are associated with securing the RFID data flow including the ISO/IEC 180000, ISO/IEC 29167

Several different attack types can be performed against RFID systems:
- Against the RFID devices themselves (the chips and the readers)
- Against the communication channel between the device and the reader
- Against the reader and back-end system

- The two main attacks are replay and eavesdropping
	- **Replay: the RFID info is recorded and then replayed later.**
	- **Eavesdropping: Data can be collected monitoring the movement of tags for whatever purpose needed by an unauthorized party**
	- Both can be defeated using the ISO/IEC security standards previously discused
---
### Near Field Communication (NFC)
**Def: A set of wireless technologies that enables smartphones and other devices to establish radio communication over a short distance.**

- Has become the mainstream method of making payments via mobile phones and is directly connected to financial information. 
- **Exam Tip: RFID is a process by which a credit card or phone communicates with a reader using radio waves and NFC is a high-frequency subset of RFID and acts over a much shorter discance**
---
### Initialization Vector (IV)
**Def: is used in wireless systems as the randomization element at the beginning of a connection.**

- Attacks against it are aimed at determining the IV, thus finding the repeating key sequence. 
- The IV is the primary reason for the weakenss in the Wired Equivalent Privacy (WEP)
- The biggest weakness of WEP is that the IV problem exists regardless of key length because the IV always remains at 24 bits.
---
### On-Path Attack
**Def: a man in the middle (MITM) attack generally occurs when an attacker is able to place himself in the middle of two other hosts that are communicating.**

- This is done by ensuring that all communication going to or from the target host is routed through the attacker's host (which can be accomplished if the attacker can compromise the router for the target host)
- The attacker can modify/alter all network traffic
- There are numerous methods of instantiating a man in the middle attack. 
	- One of the common methods is via session hijacking, which occurs when information such as a cookie is stolen, allowing the attacker to impersonate the legitimate session
- Can be accmplish through cross-site scripting attack, which tricks user into executing code resulting in cookie theft.
- Amount of information that gets compromised depends on whether or not information is encrpyted. 

**Def: a main in the browser (MITB) attack is a variant of a man in the middle attack. In an MITB attack, the first element is a malware attack that places a trojan element that can act as a proxy on the target machine.**

- This malware changes browser behavior through browser helper objects or extensions.
- A famous example of a malware attack was Zeus, which targeted financial transactions on users' machines, manipulating and changing them after the users had entered password credentials

**Exam Tip: MITM and MITB are similar, yet different. Be able to differentitate between the two based on the details of the question.** 

---
## Layer 2 Attacks:
**Def: Layer 2 of a network is where local addressing decisions are made. Switches operate at layer 2, or media access control (MAC) addresses. There are many ways of tampering with this level of addressing, and Security+ identifies three of significance: Address Resolution Protocol (ARP) poisoning, media access control (MAC) flooding, and MAC cloning. **

---
### Address Resolution Protocol (ARP) Poisoning
- When moving packets between machines, a device needs to know wheere to send a packet using the MAC or layer 2 address.

- Address Resolution Protocol (ARP) handles this problem through four basic messages:
	- ARP request: "Who has this IP address?"
	- ARP reply: "I have the IP address; my MAC address is..."
	- Reverse ARP request (RARP): "Who has this MAC address?"
	- RARP reply: "I have that MAC address; my IP is..."

- These messages are using in conjunction with a device's ARP table, where a form of short-term memory associated with these data elements resides.

- When an ARP tables gets a reply, it automatically trusts the reply and updates the table.

**Def:  When an attacker sends messages, corrupts the ARP table and results in malicious address redirection. This can allow a mechanism whereby an attacker can inject himself into the middle of a conversation between two devices --a man in the middle attack**

---
### Media Access Control (MAC) Flooding
**Def: an attack where an attacker floods the table with addresses, making the switch unable to find the correct address for a packet.**

- The switch responds by sending the packet to all addresses, making it act more like a hub.
- The switch also asks for the correct device to give it its address, thus setting the switch up for ARP poisioning, as described in the previous section.
----
### MAC Cloning
**Def: the act of changing a MAC address to bypass security checks based on the MAC address.**

- This works when the return packets are being routed by IP address and can be properly linked to the correct MAC address.

- Not all MAC cloning is an attack, small firewall routers commonly have a MAC clone function
---
## Domain Name System (DNS) & Types of DNS Attacks 
**Def: The phone book for addressing. When you need to know where to send a packet that is not local to your netowork, DNS provides the correct address to get the packet to its destination. **

- One of the primary targets for attackers because if your corrupt a DNS, you can control where all the packets go.

- Used to convert a name into an IP address. There is not a single DNS system but rather a hierarchy of DNS servers.

- DNS exists at layer 3 of the OSI model
---
### Domain Hijacking
**Def: the act of changing the registration of a domain name without the permission of its original registrant**

- While technically a crime, this can have terrible effects since the DNS system will spread the false domain location far and wide automatically. 

- The original owner can request it to be corrected, but this takes time
---
### DNS Poisoning

- DNS is used to convert a name into an IP address. There is not a single DNS system but rather a hierarchy of DNS servers.

- To examine a DNS query for a specific address, you can use the **nslookup** command


**Def: The changing of where DNS is resolved can be a DNS poisioning attack.**

- The challenge in detecting these attacks is knowing what the authoritative DNS entry should be and then detecing when it changes in an unauthorized fashion. 

- Using a VPN can change a DNS source, and this may be desired, but unauthorized changes can be attacks

- At times, **nslookup** will return a nonauthoritative answer. This typically means the result is from a cache as opposed to a server that has an authoritative answer.

- There are other commands you can use to examine and manipulate the DNS cache on a system. In Windows, the **ipconfig/displaydns** command will show the current DNS cache on a machine. 

- DNS poisoning is a variant of a larger attack class referred to as DNS sppofing. In DNS spoofing, an attacker changes a DNS record through any of a multitude of means.
---
### Universal Resource Locator (URL) Redirection
**Def: the method of describing where you want a browser to go, and it is the main interface to the DNS process that converts it to a machine-readable address.**

- If the attacker has registered a different site in the DNS based off of the slightl misspelling or typo of a more popular site, they may accidentally be subjected to a man-in-the-middle attack.
---
### Domain Reputation
**Def: If you address is associated with spam or other neferious actions, you ip reputation will suffer**

- This is very similar to real-world reputations. Therefore it is important that no one else is using your machine and commiting poor actions. 
---
## Distributed Denial-of-Service (DDoS)
- In a denial-of-service (DoS) attack, the attacker attempts to deny authorized users access either to specfic information or to the computer system or network itself. 
	- This can be accomplished by crashing the system, taking it offline, or by sending so many requests that the machine is overwhelmed.
	
- **Def: A DoS attack employing multiple attacking systems.**

- Has the same goal as a DoS attack

- The attack agents are not willing agents--they are systems taht have been compromised and on which the DDoS attack software has been installed. w

- You can't prevent an attack on your network but you can prevent your network from being used in an attack
---
### Network
- A network of attack agents, sometimes called zombies, is created by the attacker, and upon receiving the attack command from the attacker, the attack agents commence sending a specific type of traffic against the target.

- Example attacks
	1.  400 Gbps CloudFlare attack (2014)
	2. Connectionless Lightweight Directory Access Protocol (CLDAP)
		1. 1.35 Tbps attack against Github
		2. 1.7 Tbps attack mitigated by Abor (2018)
		3. 2.3 Tbps attack mitigated by Amazon Web Services (2020)

- Purpose of these attacks is to prevent access to the target system, and blocking network connnections will do this

- One method, a SYN flooding attack, can be used to prevent service to a system temporarily in order to take advantage of a trusted relationship that exists between that system and another.
	- They take advantage of the way TCP/IP networks were designed to function, and it can be used to demonstrate the basic principles of any DoS attack.
	
	- Uses the TCP three-way handshake that establishes a connection between two systems. Under normal circumstances, the first system sends a SYN packet to the system with which it wants to communicate.
	
	- The second system responds with a SYN/ACK if it is able to accept the request.
	
	- When the initial system receives the SYN/ACK from the second system, it responds with an ACK packet, and communication can then proceed. 
	
	- In a SYN flooding attack, the attacker sends fake communication requests to the targeted system. Each of those requests will be answered by the target system, which then waits for the third part of the handshake. 

	- Since the requests are fake (a nonexistant ip), the target will wait for responses that never come. Eventually the target system will drop these responses but if the requests come in faster than the time-out period, the system will quickly overfill.
	
- Another attack is the ping of death (POD). This is when a ping request exceeds 64 KB. This is not a naturally occuring size for a ping request so some systems hang or crash.
---
### Application
- An objective of an application level DDoS attack is to consume all the resources or to put the system into a failed state.

- One of them most common targets is HTTP since detection of attack vs regular packets is challenging. 
---

### Operational Technology (OT)
**Def: The name given to networks of industrial devices in cyber-physical systems. These devices use computers to control physical processes.**

- Examples: traffic lights, refineries, manufacturing plants.

- Difference between IT and OT systems is protocols. OT systems have OT-specific protocols that are used to perform the communications of equipment control.

- They have a heavy reliance on timed signals. A DoS attack of any kind including DDoS can result in significant problems if these timed signals are interupted.
---
## Malicious Code and Script Execution
**Def: Using scripts and automation in systems to automate attacks**

### Powershell
- Powershell is a built-in command-line tool suite that has a rich set of Microsoft Windows commands. It is completely integrated with the windows environment. It is so integrated into Windows that it is a primary target for attackers.

- A popular tool to exploit Powershell is PowerSploit, which includes routines such as Invoke-Mimikatz

### Python
- Python is a widely used programming language/scripting language. Python is an effective scripting tool that is easy to learn, widely supported, and good at automating tasks. 

- Github has many Python-related attack toolsets and utilities

### Bash
- Bash (Bourne Again Shell) is an interpreter that processes shell commands on Linux systems.

- Bash takes commands in plaintext format and calls OS services to perform the specified tasks. 

- Hackers use Bash to search through linux systems and perform tasks on Linux systems.

### Macros
- Macros are recorded sets of instructions, typically presented to an application to automate their function. 

- unwanted macros can call system and perform system level activities. It is important to restrict macros to the application they are being used in.

### Virtual Basic for Applications (VBA)
- Older technology from Microsoft that was used to automate many internal processes in applications. 

- Can still be used as an attack vector, make sure to disable unwanted VBAs 
---
# Questions
1.B
2.A
3.B
4.D
5.B
6.B
7.C
8.B
9.C
10.A














