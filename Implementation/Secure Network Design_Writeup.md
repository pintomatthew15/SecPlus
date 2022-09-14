# Chapter 19
# Secure Network Design

Networks connect the components of an enterprise IT system, carrying signals and data and enabling the IT system to function in the desired manner for the business. 

Having minimal risk come from the network is important, and the methods to achieve this are through secure network system design. 

**Exam Tip: Preparing for scenario-based questions requires more than simply learning the terms associated with network-based security solutions such as routers, switches, proxies, and load balancers. You should be familiar with how and when to configure each device based on a given scenario.**

## Load Balancing
Certain systems, such as servers, are more critical to business operations and should therefore be the object of fault-tolerance measures.

**Def: Load balancing involves the use of devices that move loads across a set of resources in an effort not to overload individual servers.**
- This technique is designed to distribute the processing load over two or more systems. 
- It is used to help improve resource utilization and throughput but also has the added advantage of increasing fault tolerance of the overall system since a critical process may be split across several systems.

Load balancing is often utilized for systems handling websites, high-bandwidth file transfers, and large Internet Relay Chat (IRC) networks. 

**How it works:** Load balancing works by a series of health checks that tell the load balancer which machines are operating, and by a scheduling mechanism to spread work evenly. 

Load balancing is best for stateless systems, as subsequent requests can be handled by any server, not just the one that processed the previous request. 

### Active/Active
**Def: In an active/active scheme, all the load balancers are active, sharing the load-balancing duties.**
- This offers performance efficiencies, but it is important to watch the overall load. 
- If the overall load cannot covered by by N-1 load balancers (that is, one fails), then the failure of a load balancer will lead to session interruption and traffic loss. 

Without a standby passive system to recover the lost load, the system will trim the load based on capacity, dropping requests that the system lacks capacity to service.

**Exam Tip: Two or more servers work together to distribute the load in an active/active load-balancing configuration. If a server fails, service interruption or traffic loss may result.**


### Active/Passive
For high-availability solutions, having a single load balancer creates a single point of failure (SPOF). Therefore it is common to have multiple load balancers involved in the balancing work. 

**Def: In an active/passive scheme, the primary load balancer is actively doing the balancing while the secondary load balancer passively observes and is ready to step in any time the primary system fails.**

**Exam Tip: All traffic is sent to the active server in an active/passive configuration. If the active server fails, the passive server is promoted to active.**

### Scheduling
When a load balancer moves loads across a set of resources, it decides which machine gets a request via a **scheduling algorithm**. There are a couple of commonly used scheduling algorithms: affinity-based scheduling and round-robin-scheduling. 

#### Affinity
**Def: Affinity-based scheduling is designed to keep a host connected to the same server across a session.**
- The method used by affinity-based scheduling is to have the load balancer keep track of where it last balanced a particular session and direct all continuing session traffic to the same server.
- New connections are assigned to the next server in the available rotation.

#### Round-Robin
**Def: Round-robin scheduling involves sending each new request to the next server in rotation.**
- All requests are sent to servers in equal amounts, regardless of the server load. 
- Round-robin schemes are frequently modified with a weighting factor, known as weighted round-robin, to take the server load or other criteria into account when assigning the next server.

**Exam Tip: Round-robin and weighted round-robin are scheduling used for load-balancing strategies.**

### Virtual IP
In a load balanced environment, the IP addresses for the target servers of a load balancer will not necessarily match the address associated with the router sending the traffic. 

**Def: Virtual IP addresses or virtual IP allow multiple systems to be reflected back as a single IP address.**

### Persistence
**Def: The condition where a system connects to the same target in a load-balanced system.**
- This can be important for maintaining state and integrity of multiple round-trip events. 
- Persistence is achieved through affinity-based scheduling of server assets in load balancing. 

## Network Segmentation
**Def: Network segmentation is where you have configured the network devices to limit traffic access across different parts of a network.**
- This can be done to prevent access to sensitive machines, but also aids in network traffic management.

Dividing a network into segments generally does not take more equipment, but rather is done in how the networking equipment is configured to communicate across the defined segments. 

A screened subnet (DMZ) is an example of a segment, one that is accessible form the Internet, and from the internal network, but cannot be crossed directly. 

### Virtual Local Area Network (VLAN)
**Def: A LAN is a set of devices with similar functionality and similar communication needs, typically co-located and operated off a single switch.**
- This is the lowest level of a network hierarchy and defines the domain for certain protocols at the data link layer (layer 2) for communication. 

**Def: A virtual LAN (VLAN) is a logical implementation of a LAN and allows computers connected to different physical networks to act and communicate as if they were on the same physical network.**
- Very similar to a LAN, but is implemented with switches and software.
- Allows for significant network flexibility, scalability, and performance and allows administrators to perform network reconfigurations without having to physically relocate or re-cable systems. 

**Def: Trunking is the process of spanning a single VLAN across multiple switches.**
- A trunk-based connection between switches allows packets from a single VLAN to travel between switches. 
- Trunks enable network administrators to set up VLANs across multiple switches with minimal effort.

With a combination of trunks and VLANs, network administrators can subnet a network by user functionality without regard to host location on the network or the need to re-cable machines. 

VLANs are used to divide a single network into multiple subnets based on functionality.
- This permits accounting and marketing departments, for example, to share a switch because of proximity yet still have separate traffic domains. 
- Both a purpose and a security strength of VLANs is that systems on separate VLANs cannot directly communicate with each other.

**Exam Tip: Physical segregation requires creating two or more physical networks, each with its own servers, switches, and routers. Logical segregation uses one physical network with firewalls and/or routers separating and facilitating communication between the logical networks. **

### Screened Subnet (Previously Known as Demilitarized Zone)
**Def: The zone that is between the untrusted Internet and the trusted internal network is called the screened subnet.**
- This was previously known by the term DMZ, after its military counterpart of the same name, where neither side has any specific controls. 
- Within the inner, secure network, separate branches are frequently cared out to provide specific functional areas.

A screened subnet in a computer network is used in the same way; it acts as a buffer zone between the Internet, where no controls exist, and the inner, secure network, where an organization has security policies in place.
- To demarcate the zones and enforce separation, a firewall is used on each side of the screened subnet. 
- The area between these firewalls is accessible from either the inner, secure network or the internet. 
- These firewalls are specifically designed to prevent direct access across the screened subnet from the Internet to the inner, secure network.

Special attention is required for the security settings of devices placed in the screened subnet (between the outer and inner firewalls), as you should consider them to always be compromised by unauthorized users. 
- **Def: Machines whose functionality is locked down to preserve security are commonly called hardened operating systems**.

 Many types of servers belong in the screened subnet, including web servers that are serving content to Internet users, as well as remote-access servers and external e-mail servers. 
- In general, any server directly accessed from the outside, untrusted Internet zone needs to be in the screened subnet.
- Domain name servers for your inner, trusted network and database servers that house corporate databases should not be accessible from the outside.
- Application servers, file servers, print servers --all of the standard servers used in the trust network -- should be behind both the inner and outer firewalls, along with the routers and switches used to connect these machines. 

The idea behind the use of the screened subnet topology is to force an outside user to make at least one hop in the screened subnet before he can access information inside the trusted network. 
- If the outside user makes a request for a resource from the trusted network, such as a data element form a database via a web page, then this request needs to follow this scenario:
	1. A user from the untrusted network (the internet) requests data via a web page from a web server in the screened subnet.
	2. The web server in the screened subnet requests the data from the application server, which can be in the screened subnet or in the inner, trusted network. 
	3. The application server requests the data from the database server in the trusted network.
	4. The database server returns the data to the requesting application server.
	5. The application server returns the data to the requesting web server.
	6. The web server returns the data to the requesting user from the untrusted network. 

This separation accomplishes two specific, independent tasks. First, the user is separated from the request for data on a secure network. Second, scalability is more easily realized. 

**Exam Tip: Screened subnets act as a buffer zone between unprotected areas of a network (the internet) and protected areas (sensitive company data stores), allowing for the monitoring and regulation of traffic between these two zones.**

### East-West Traffic
Data flows in an enterprise can be described in patterns, such as north-south and east-west. 
- Data flowing into and out of a data center or enterprise is called north-south traffic.
- East-West traffic is the data flow pattern between devices within a portion of the enterprise (that is, between functionally related boxes to support north-south traffic). 

**Exam Tip: East-west traffic refers to network data flows within an enterprise network. North-south traffic refers to data flowing between the enterprise network or data center and the outside of the network.**

### Extranet
**Def: An extension of a selected portion of a company's intranet to external partners.**
- This allows a business to share information with customers, suppliers, partners, and other trusted groups while using a common set of Internet protocols to facilitate operations. 
- Extranets can use public networks to extend their reach beyond a company's own internal network, and some form of security, typically CPN is used to secure this channel. 
- Extranets utilizes privacy and security

**Exam Tip: An extranet is a semiprivate network that uses common network technologies (HTTP, HTP, and so on) to share information and provide resources to business partners. Extranets can be accessed by more than one company because they share information between organizations.**

### Intranet
**Def: An intranet describes a network that has the same functionality as the internet for users but lies completely inside the trusted area of a network and is under the security control of the system and network administrators.**
- Content on intranet web servers is not available over the internet to untrusted users.
- intranets allow the full set of protocols --HTTP, FTP, IM with the added benefit of trust from the network security. 

Two methods can be used to make information available to outside users: 
1. Duplication of information onto machines in the screened subnet can make it available to other users. 
2. Extranets can be used to publish material to trusted partners. 

**Exam Tip: An intranet is a private, internal network that uses common network technologies (HTTP, FTP, and so on) to share information and provide resources to integral organizational users.**
- All internet requests from an intranet use a proxy server to mask the IP.

### Zero Trust
**Def: A security model centered on the belief that you should not trust any request without verifying authentication and authorization.**
- Zero trust implementations require strict identity verification for every account trying to access resources, regardless of their location. 
- Zero trust requires a holistic approach to security that incorporates several additional layers of defense and technologies.

## Virtual Private Networks (VPNs)
**Def: Allow two networks to connect securely across an unsecure stretch of network by tunneling across the intermediate connections.**
- VPN technology enable two sites, such as a remote work's home network and the corporate network, to communicate across unsecure networks, including the Internet, at a much lower risk profile.
- Two main uses for tunneling/VPN technologies are site-to-site communications and remote access to a network. 

VPN's work because only the endpoints have the information to decrypt the packets being sent across the network. At all of the intermediate hops, if a packet is intercepted, it cannot be read. This enables secure network communication between two endpoints of a circuit. 

### Always On
One of the challenges associated with VPNs is the establishment of the secure connection. 
- In many cases, this requires additional end-user involvement, in the form of launching a program, entering credentials or both. 
- **Def: Always-on VPNS use pre-established connection parameters and automation to self-configure and connect once an Internet connection sensed and provide VPN functionality without user intervention.**

**Exam Tip: When an internet connection is made, an always-on VPN client automatically establishes a VPN connection.** 

### Split Tunnel vs. Full Tunnel 
**Def: Split tunnel is a form of VPN where not all traffic is routed via the VPN.**
- Split tunneling allows multiple connection paths, some via a protected route such as the VPN, whereas other traffic from, say, public Internet sources is routed via non-VPN paths.
- The advantage of split tunneling is the ability to avoid bottlenecks from all traffic having to be encrypted across the VPN. 
- A split tunnel would allow a user private access to information from locations over the VPN and less secure access to information from other sites. 
- The disadvantage is that attacks from the non-VPN side of the communication channel can affect the traffic requests from the VPN side. 

**Def: A full tunnel solution routes all traffic over the VPN, providing protection to all networking traffic.**

**Exam Tip: For performance-based questions, simply learning the terms associated with VPNs and IPSec in particular is insufficient. You should be familiar with the configuration and use of IPSec components, including the types of configurations and their use to support organizational security.**

### Remote Access vs. Site-to-Site
**Def: Site-to-site communication links are network connections to two or more networks across an intermediary network layer.**
- In almost all cases, this intermediary network is the Internet or some other public network. 
- To secure the traffic that is going from site to site, encryption in the form of either a VPN or a tunnel can be employed. 
- In essence, this makes all of the packets between the endpoints in the two networks unreadable to nodes between the two sites. 

**Def: Remote access is when a user requires access to a network and its resources but is not able to make a physical connection.**
- Remote access via a tunnel or VPN has the same effect as directly connecting the remote system to the network--it's as if the remote user just plugged a network cable directly into their machine. 

**Exam Tip: Tunneling/VPN technology is a means of extending a network either to include remote users or to connect two sites. Once the connection is made, its is like the connected machines are locally on the network.**

### IPSEC
**Def: A set of protocols developed by the IETF to securely exchange packets at the network layer (layer 3).**
- It is possible to tunnel across other networks at lower levels of the OSI model
- The set of security services provided by IPSec occurs at the network layer of the OSI model, so higher-layer protocols, such as TCP, UDP, Internet Control Message Protocol (ICMP), Border Gateway Protocol (BGP), and the like are not functionally altered by the implementation of IPSec services.  

The IPSec protocol series has a sweeping array of services it is designed to provide, including but not limited to access control, connectionless integrity, traffic-flow, confidentiality, rejection of replayed packets, data security (encryption), and data-origin authentication. 
- IPSec also has three modes of connection: host-to-server, server-to-server, and host-to-host. 

The transport mode encrypts only the data portion of the packet, thus enabling an outsider to see source and destination IP address.
- The transport mode protects the higher-level protocols associated with a packet and protects the data being transmitted but allows knowledge of the transmission itself. 
- Protection of the data portion of a packet is referred to as content protection.

Tunnel mode provides encryption of source and destination IP addresses, as well as of the data itself.
- This can only be done between IPSec servers (or routers) because the final destination needs to be known for delivery. 
- Protection of header information is known as content protection. 

**Exam Tip: In transport mode (end-to-end), security of packet traffic is provided by the endpoint computers. In tunnel mode (portal-to-portal), security of packet traffic is provided between endpoint node machines in each network and not at the terminal host machines.**

### SSL/TLS
**Def: Secure Sockets Layer (SSL)/ Transport Layer Security (TLS) is an application of encryption technology developed for transport-layer protocols across the Web.**
- This protocol uses public key encryption methods to exchange a symmetric key for use in confidentiality and integrity protection as well as authentication.
- All versions of SSL have been deprecated due to security issues, and in the vast majority of commercial servers employing SSL/TLS, SSL has been retired. 
- TLS can be used to affect a VPN between a client browser and the web server and is one of the most common methods of protecting web traffic. 

The standard port for SSL and TLS is undefined because it depends on what the protocol being protected uses; for example, port 80 for HTTP becomes port 443 when it is for HTTPS. If the connection is for FTP, then FTPS uses TCP ports 989 and 990. 

### HTML5
**Def: HTML5 is the current version of the HTML protocol standard, and this version was developed to handle the modern web content of audio and video as well s to enhance the ability of a browser to function without add-ins such as Flash, Java, and browser helped objects for common function.**
- One of the areas this has enhanced is the ability to connect to a VPN by implementing a secure HTML5-based remote access solution. 
- This does not require Java or other plugins, thus removing compatibility and updating of accessories issues. 
- As HTML5 was designed to operate across a wide range of devices, including mobile platforms, functionality such as this can advance security across multiple-platforms.

**Exam Tip: HTML5 doesn't require browser plugins and is considered a secure remote access alternative to using SSL/TLS VPNs.**

### Layer 2 Tunneling Protocol (L2TP)
**Def: Layer 2 Tunneling Protocol (L2TP) is an internet standard and came from the Layer 2 Forwarding (L2F) protocol, a Cisco initiative designed to address issues with Point-to-Point Tunneling Protocol (PPTP).**
- Whereas PPTP is designed around Point-to-Point Protocol (PPP) and IP networks, L2F (and hence L2TP) is designed for use across all kinds of networks, including ATM and Frame Relay. 
- L2TP can be configured in software and is in Microsoft's Routing and Remote Access Service (RRAS), which uses L2TP to create a VPN.

L2TP works in much the same way as PPTP, but it opens up several items for expansion
- In L2TP, routers can be enabled to concentrate VPN traffic over higher-bandwidth lines, creating hierarchical networks of VPN traffic that can be more efficiently managed across an enterprise. 
- L2TP is established via UDP port 1701, so this is an essential port to leave open across firewalls supporting L2TP traffic.

## DNS
**Def: The Domain Name System (DNS) is a protocol for the translation of names into IP addresses.**
- When users enter a name such as www.example.com, the DNS system converts this name into the actual numerical IP address. 
- DNS records are also used for email delivery
- DNS uses UDP over port 53 for standard queries, although TCP can be used for large transfers such as zone transfers. 
- DNS is a hierarchical system of servers, from local copies of records, up through Internet providers to root-level servers.
- **DNS requests and replies are sent through plaintext, making it subject to spoofing**

DNSSEC (Domain Name System Security Extensions) is a set of extensions to the DNS protocol that, through the use of cryptography, enables origin authentication of DNS data, authenticated denial of existence, and data integrity but does not extend to availability and confidentiality. 
- DNSSEC records are signed so responses are authenticated but not encrypted.

Data transfers over UDP port 53 are limited to 512 bytes in size, and DNSSEC packets can be larger. For this reason DNSSEC typically uses TCP port 53 for its work. It is possible to extend UDP packet size to 4096 bytes to cope with DNSSEC, and this is covered in RFC 6891.

## Network Access Control (NAC)
Networks comprise connected workstations and servers. Managing security on a network involves managing a wide range of issues related not only to the various connected hardware but also to the software operating those devices. 

**Def: Managing the endpoints on  case-by-case basis as they connect is a security methodology known as network access control.**

Two main competing methodologies exists:
1. Network Access Protection (NAP): a Microsoft  technology for controlling network access to a computer host.
2. Network Admission Control (NAC): Cisco's technology for controlling network admission. 

Neither Cisco NAC nor Microsoft NAP is widely adopted across enterprises. The client pieces are all in place, but enterprises have been slow to fully deploy the server side of this technology. 

**Exam Tip: For Sec+, NAC refers to network access control. The Microsoft and Cisco solutions referenced in this section are examples of this type of control-- their names and acronyms are not relevant to the Sec+. The concept of network access control (NAC) and what it accomplishes is relevant and testable.**

### Agent and Agentless
**Def: In agent-based solutions, the code resides on the network and is deployed to memory for use in a machine requesting connections, but since it never persists on the host machine, it is referred to as agentless.**
- No real performance differences between agent and agentless 
- The real difference comes in the issues of having agents on boxes versus persistent network connections for agentless. 

Agentless NAC is often implemented in a Microsoft domain through an Active Directory (AD) controller. 
- For example, NAC code verifies devices are in compliance with access policies when a domain is joined by a user or when they log in or log out. 
- Agentless NAC is also often implemented through the use of intrusion prevention systems. 

**Exam Tip: NAC agents are installed on devices that connect to networks in order to produce secure network environments. With agentless NAC, the NAC code resides not on the connecting devices, but on the network, and its deployed to memory for use in a machine requesting connection to the network.**

## Out-of-Band Management
Management of a system across a network can be either in-band or out-of-band. 
- In-band: The management channel is the same channel as the data channel
- **Def: out-band management channels are physically separate connections, via separate interfaces that permit the active management of a device even when the data channel is blocked for some reason.**

## Port Security
**Def: A capability provided by switches that enables you to control which devices and how many of them are allowed to connect via each port on a switch.**
- Operates through MAC addresses (MAC addresses can be spoofed)

Port address security based on MAC addresses can determine whether a packet is allowed or blocked from a connection. 
- This is the same idea behind what a firewall uses for its determination and what 802.1X devices use to act as an "edge device"

There are three variants of port security:

**Static Learning**: A specific MAC address is assigned to a port. 
	-Useful for fixed dedicated hardware connections. Good for defined not visiting connections
	
**Dynamic Learning:** Switch learns MAC addresses as they connect. Good for small, limited number of machines to connect to a port.

**Sticky learning**: Allows multiple devices to a port, but also stores the info in memory that persists through reboots.
	- Prevents attacker from changing settings through power cycling the switch.

### Broadcast Storm Prevention

Flooding attacks are used as a form of denial of service (DoS) to a network or a system. 
- There are ping floods, SYN floods, ICMP floods, and traffic flooding. 

**Def: Flood guards act by managing traffic flows and detect when to block traffic to prevent flooding.**

**Exam Tip: Flood guards are commonly implemented in firewalls and IDS/IPS solutions to prevent DoS and DDoS attacks.**

### Bridge Protocol Data Unit (BPDU) Guard
**Def: Bridge Protocol Data Unit (BPDU) packets are specially crafted messages with frames that contain information about the Spanning Tree Protocol (STP).**
- Their use results in a recalculation in the STP.
- Attackers can spam multiple BPDU packets to force recalculation and serve as a network DoS attack. 

**Def: Bridge Protocol Data Unit Guards (BPDU) guards are edge devices that can be configured to detect and drop these packets.**

### Loop Prevention
Switches operate at level 2 of the OSI model, and at this level there is no countdown mechanism to kill packets that get caught in loops or on paths that will never resolve.
- This means a mechanism is needed for loop prevention

On layer 3 a time to live (TTL) counter is used, but there is no equivalent on layer 2. The layer 2 space acts as a mesh, where potentially the addition of a new device can create loops in the existing device interconnections. 

To prevent loops switches use a technology called spanning trees. 
- STP allows for multiple, redundant paths, while breaking loops to ensure a proper broadcast pattern.
- STP is a data link layer protocol
- STP trims connections that are not part of the spanning tree connecting all of the nodes. 
- STP messages are carried in BPDU frames

**Exam Tip: Remember that BPDU guards, MAC filtering, and loop detection are all mechanisms used to provide port security. Understand the differences in their actions. MAC filtering verifies MAC addresses before allowing connection, BPDU guards prevent tampering with BPDU packets, and loop detection detects loops in local networks.**

## Dynamic Host Configuration (DHCP) Snooping
Administrators assign IP addresses to systems in one of two ways:
- statically, the admin chooses an IP assigns it to a system and it stays that way till the admin changes it
- dynamically through DHCP 

**Def: Under Dynamic Host Configuration (DHCP), when a system boots up or is connected to the network, the client uses the one whose answer reaches them first.**
- From this DHCP server, the client then receives the address assignment. 
- DHCP works best when IP assignment becomes too complex 

The weakness of using the first response received allows a rogue DNS server to reconfigure the network. A rogue DHCP server can route the client to a different gateway, known as DHCP spoofing. 
- Incorrect addresses can lead to a DoS attack blocking key network services

**Def: DHCP snooping is a defensive measure against an attacker that attempts to use a rogue DHCP device.**
- DHCP snooping prevents malicious DHCP servers from establishing a contact by examining DHCP responses at the switch level and not sending those from unauthorized DHCP servers. 

## Media Access Control (MAC) Filtering
**Def: MAC filtering is the selective admission of packets based on a list of approved Media Access Control (MAC) addresses.**
- This provides a means of machine authentication, using switches (level 2)

**Exam Tip: MAC filtering can be employed on wireless access points but can be bypassed by attackers observing allowed MAC addresses and spoofing the allowed MAC address for the wireless card.**

## Network Appliances
**Def: Machines that provide services across a network.**
- Examples include: jump servers, network-based IDS, VPN endpoints, collectors, and aggregators. 

### Jump Servers 
**Def: A jump server is a hardened system on a network specifically used to access devices in a separate security zone.**
- This works as a safer alternative than allowing direct access outside. 

**Exam Tip: Jump servers are hardened systems often used to protect and provide a means to access resources in a screened subnet, for example.**

### Proxy Servers
**Def: A proxy server can be used to filter out undesirable traffic and prevent employees from accessing potentially hostile websites, they take requests from a client system and forwards them to the destination server on behalf of the client.**

Deploying a proxy solution within a network environment is usually done either by setting up the proxy and requiring all client systems to configure their browsers to use the proxy or by deploying an intercepting proxy that actively intercepts all requests without requiring client-side configuration. 

**Proxies are most useful in their ability to control and filter outbound requests.**

#### Types of Proxies
Proxies operate in 2 directions.
- **Def: A forward proxy operates to forward requests to servers based on a variety of parameters.**
	- They can be used to bypass firewall restrictions, act as a cache server, and change your IP address.
- **Def: A reverse proxy is typically installed on the server side of a network connection, often in front of a group of web servers, and intercepts all incoming web requests.
	- It can perform a number of functions, including traffic filtering, SSL/TLS decryption, serving a common static content such as graphics, and load balancing. 

**Exam Tip: A forward proxy is internet-facing and acts on behalf of the client. It protects the client. A reverse proxy is internally facing and acts on behalf of the server, which it protects.**

### Network-based Intrusion Detection System (NIDS)/Network-based Intrusion Prevention System (NIPS)

NIDS detect but NIPS prevent

**Exam Tip: Recognize that a NIPS has all the same characteristics as a NIDS but, unlike a NIDS, can automatically respond to certain events without operator intervention.**

Whether network-based or host-based, an IDS will typically consist of several specialized components working together. The components are often logical and software-based rather than physical and will vary slightly from vendor to vendor and product to product. Typically an IDS will have the following logical components:

- **Traffic Collector (or sensor)**: This component activity/events for the IDS to examine. On a host-based IDS, this could be log files, audit logs, or traffic coming to or leaving a specific system. On a network based IDS, this is typically a mechanism for copying traffic off the network link-basically functioning as a sniffer. This component is often referred to as the sensor.

- **Analysis Engine**: This component examines the collected network traffic and compares it to known patterns of suspicious or malicious activity stored in the signature database. The analysis engine is the "brains" of the IDS.

- **Signature Database**: The signature database is a collection of patterns and definitions of known suspicious or malicious activity.

- **User Interface and Reporting**: This component interfaces with the human element, providing alerts when appropriate and giving the user a means to interact with and operate the IDS. 

NIDS/NIPS can be divided into three categories based on primary methods of detection used: signature based, heuristic/behavioral based, and anomaly based. 

#### Signature Based
- Relies on predefined set of patterns
- IDS needs to know what is bad before it can identify and act upon suspicious or malicious traffic
- Hard to scale because of predefined signatures 

**Def: Signature based systems work by matching signatures in the network stream to defined patterns stored in the system.**

**Exam Tip: False negatives often happen when alerts that should be generated aren't. False positives occur when expected behavior is identified as malicious.**

#### Heuristic/Behavior
**Def: behavioral model relies on a collected set of "normal behavior"--what should happen on the network and is considered "normal" or "acceptable" traffic.**
- This carries a high false-positive rate because any new traffic pattern can be labeled as "suspect".

**Def: A heuristic model uses artificial intelligence (AI) to detect intrusions and malicious traffic.**
- Falls between signature based and heuristic based

#### Anomaly
This model is similar to the behavioral-based methods. The IDS is first taught what "normal" traffic looks like and then looks for deviations from those "normal" patterns.

**Def: An anomaly is a deviation from an expected pattern or behavior.**

**Exam Tip: Anomaly detection identifies deviations from normal behavior.**

#### Incline vs. Passive
Decisions for NIPS/NIDS are made "in band". 
- This has high security but also has implications related to traffic levels and traffic complexity
- In-band works great for network segments that have high-value systems and a limited number of traffic types. 

Out-of-band systems rely on passive sensors
	- Provides greater flexibility but a delay in reacting to positive findings

### Hardware Security Model
**Def: A hardware security model (HSM) is a device used to manage or store encryption keys.**
- It can also assist in cryptographic operations
- Pretty secure all around

**Exam Tip: Storing private keys anywhere on a networked system is a recipe for loss. HMS are designed to allow the use of the key without exposing it to the wide range of host-based threats.**

### Sensors
**Def: Sensors are devices that capture data and act upon it.**
- Two types: network and host
	- Network based provide coverage across multiple machines; but limited by traffic engineering to systems that packets pass them. Also have limited knowledge of what the host is ultimately doing. 
	-  Host-based sensors provide more specific and accurate information in relation to what the host machine is seeing and doing, but they are limited to just that host. 

### Collectors
**Def: Collectors are collections of sensors and collect data for processing by other systems.**

### Aggregators
**Def: Aggregators are devices that take multiple inputs and combines them to a single output.** 


### Firewalls 
**Def: Hardware, software, or a combination of both whose purpose is to enforce a set of network security policies across network connections.**

**Def: Security policies are rules that define what traffic is permissible and what traffic is to be blocked or denied.**

**Exam Tip: The Security+ exam objectives list many firewall types--from web application firewalls to appliance, host-based and virtual firewalls. Be able to distinguish them for each other and know how they might be implemented in a given scenario.**

#### Web Application Firewall (WAF)
**Def: A device that performs restrictions based on rules associated with HTTP/HTTPS traffic.**
- A form of content filters 
- WAFs can detect and block disclosure of critical data, such as account numbers, credit card numbers, and so on.
- WAFs also prevent against cross-site scripting, fuzzing, and buffer overflow attacks.

#### Next-Generation Firewalls (NGFW)
**Def: NGFWs keep track of the state associated with a communication, and they can filter based on behaviors that are not properly associated with the state of the communication.**
- They employ stateful packet filtering to prevent several types of undesired communications.

#### Stateful
**Def: A stateful packet inspection firewall can act upon the state condition of a conversation--is this a new conversation or a continuation of a conversation, and did it originate inside or outside the firewall?**
- Better capability at the cost of processing that can't scale well.
- To look at all the packets and determine the need for each and its data requires stateful packet filtering.

Stateful means that the firewall maintains, or knows, the context of a conversation. 

#### Stateless 
A typical network firewall operates on IP addresses and ports, in essence a **stateless** interaction with the traffic.
- Useful but limited in their abilities 

#### Unified Threat Management (UTM)
**Def: Unified Threat Management (UTM) is a marketing term used to describe all-in-one devices employed in network security.**
- Provide a wide range of services including switching, firewall, IDS/IPS, anti-malware, anti-spam, content filtering, and traffic shaping 
- Devices are designed to simplify security administration and target mid-sized to small networks. 
- They are typically located at the edge of the network, managing traffic in and out of the network. 

**Exam Tip: UTM devices provide a wide range of services, including switching, firewall, IDS/IPS, anti-malware, anti-spam, content filtering, and traffic shaping. This can simplify administration. However, a UTM device can also be a single point of failure (SPOF).**

#### Network Address Translation (NAT) Gateway
32-bit address space chopped up and subnetted isn't enough to handle all the systems in the world. While IPv4 address blocks are assigned to organizations such as companies and universities, there usually aren't enough Internet-visible IP addresses to assign to every system on the planet a unique, Internet routable IP address. 

**Def: Network Address Translations (NAT) translate private (nonroutable) IP addresses into public (routable) IP address.**

Most organizations build their internal networks using the private IP address ranges (such as 10.1.1.X) to prevent outsiders from directly accessing those internal networks.
- These systems still need to reach the internet which is where NAT comes in

The NAT device translates the many internal IP addresses into one of a small number of public IP addresses.

NAT devices can work as a default gateway. When internal hosts need to send packets outside the company, they send them to the NAT device. The NAT device removes the internal source IP address and uses the device's public routable address. 

While the underlying concept of NAT remains the same, there are actually several different approaches to implementing NAT, including the following:

- **Static NAT**: Maps an internal, private address to an external, public address. The same public address is always used for that private address. This technique is often used when hosting something you wish the public to be able to get to, such as a webserver behind a firewall.

- **Dynamic NAT**: Maps an internal, private IP address to a public IP address selected from a pool of registered (public) IP addresses. This technique is often used when translating addresses for end-user workstations and the NAT device must keep track of internal/external address mappings.

- **Port Address Translation (PAT)**: Allows many different internal, private addresses to share a single external IP address. Devices performing PAT replace the source IP address with the NAT IP address and replace the source port field with a port from an available connection pool. PAT devices keep a translation table to track which internal hosts are using which ports so that subsequent packets can be stamped with the same port number. When response packets are received, the PAT device reverses the process and forwards the packet to the correct internal host. PAT is a very popular NAT technique and in use at many organizations. 

#### Content/URL Filter
**Def: Content/URL Filters are used to limit specific types of content across the Web to users.**
- A common use is to block sites not work related such as Facebook and online games.
- Sometimes content blocked can be too broad

#### Open Source vs. Proprietary
One method of differentiating firewalls is to separate them into open source and proprietary solutions. 
- Open source is exemplified in iptables on Linux
- Proprietary offers ease of maintenance and rule management which drives long-term use

#### Hardware vs. Software
For use on a host, a software solution like Microsoft Windows Defender or iptables on a Linux host works well. For use in an enterprise setting at a network level, with a need to separate different security zones, a dedicated hardware device is more efficient and economical. 

#### Appliance vs. Host Based vs. Virtual
Firewalls can be located on a host, either as a separate application or part of the operating system itself. In software-defined networking (SDN) networks, firewalls can be instantiated as virtual network functions, providing all of the features under a virtual software solution. Firewalls can also be instantiated via an appliance, acting as a network segregation device, separating portions of a network based on firewall rules.

## Access Control List (ACL)
**Def: Access Control Lists provide the system information as to what objects are permitted which actions.**
- ACL's control who gets to change the network parameters via configurations, who gets to pass specific firewalls, and a host of other decisions.

## Route Security
Routing is the basis of interconnecting networks that comprise the Internet. Packets cross the networks to move information from source to destination. Depending on where the source and destination are with respect to each other, the route a packet takes can be wide ranging. 

## Quality of Service (QoS)
**Def: The use of specific technologies on a network to guarantee its ability to manage traffic based on a variety of indicators.**
- High-bandwidth, real-time traffic, such as Voice over IP (VoIP), video conferencing, and video-on-demand, has a high sensitivity to network issues such as latency and jitter. 
- QoS technologies are used to manage network conditions such as bandwidth (throughput), latency (delay, jitter (variance in latency), and error rates.
- QoS enables network administrators to assign the priority in which packets are handled as well as the amount of bandwidth afforded to that application or traffic flow.

## Implications of IPv6
Most common noted change with IPv6 over IPv4 is the increased addressing range, from 32-bit addresses to 128-bit addresses, offering virtually an unlimited address space, but this is far from the only advance.
- IPv6 enables end-to-end encryption
- IPv6 uses SEND protocol which alleviates ARP poisoning attacks
- No NAT in IPv6


## Port Spanning/Port Mirroring
**Def: Port mirror also known as a Switch Port Analyzer (SPAN) port, allows enterprise switches the ability to copy activity of one or more ports.**


### Port Taps
**Def: A passive signal-copying mechanism installed between two points on the network.**
- TAPs copy all packets it receives, rebuilding a copy of all messages
- Provide the one distinct advantage of not being overwhelmed by traffic levels during data collection
- Disadvantage: TAP is a separate piece of hardware

**Exam Tip: Port taps, when placed between sending and receiving devices, can be used to carry out man-in-the-middle attacks. Thus, when placed by an unauthorized party, they can be a security risk.**

## Monitoring Services
**Def: Network security monitoring (NSM) is the process of collecting and analyzing network data to detect unauthorized activity.**
- Detects where other defenses have failed
- Watches to see if defenses fail

## File Integrity Monitors
**Def: A series of internal processes that can validate the integrity of OS and application files.**
- Operate by taking a hash of the file and comparing this value to an offline store of correct values. If the hashes match, the file in unaltered. 
- On Microsoft Windows machine a system file integrity check can be performed using the command **sfc /scannow**. 
- On Debian Linux systems, the command **debsums** is used to verify hashes values of installed package components.

**Exam Tip: To work properly every security device covered in this section must be placed inline with the traffic flow that it is intended to interact with. If there are network paths around the device, it will not perform as designed. Understanding the network architecture is important when placing devices.**


# Questions
1. B
2. B
3. B
4. D
5. A
6. C
7. D
8. A
9. A
10. B

100% ! 
































