# Chapter 17 
# Secure Protocols

## Protocols
**Def: Protocols act as a common language, allowing different components to talk using a shared, known set of commands.**

Secure protocols are those that have built-in security mechanisms so that, by default, security can be enforced via the protocol. Many different protocols exist to achieve specific communication goals.

**Exam Tip: During the exam, you should expect to be asked to implement common protocols and services when given a basic scenario. Pay very close attention to protocol details and port numbers.**

### Domain Name System Security Extensions (DNSSEC)
The Domain Name System (DNS) is a protocol for the translation of names into IP addresses. When a user enters a name such as www.example.com, DNS converts this name into the actual numerical IP address. DNS records are also used for e-mail delivery. 

DNS protocol uses UDP over port 53 for standard queries, although TCP can be used for large transfers such as zone transfers. 

DNS is a hierarchy system of servers, ranging from local copies of records IP through Internet providers to root-level servers. 

DNS is one of the primary underlying protocols used on the Internet and is involved in almost all addressing lookups. 

DNS requests and replies are sent in plaintext and are subject to spoofing. 

**Def: Domain Name System Security Extensions (DNSSEC) is a set of extensions to the DNS protocol that, through the use of cryptography, enables origin authentication of DNS data, authenticated denial of existence, and data integrity, but does not extend to availability or confidentiality.**

DNSSEC records are signed so that all DNSSEC responses are authenticated but not encrypted. 

Data transfers over UDP port 53 are limited to 512 bytes in size, the DNSSEC packets can be larger. For this reason, DNSSEC typically uses TCP port 53 for its work. 

**Exam Tip: DNSSEC validates DNS data, this providing integrity, but it does not provide controls for availability or confidentiality.**

---
### SSH
**Def: The Secure Shell (SSH) protocol is an encrypted remote terminal connection program used for remote connections to a server.**

SSH uses asymmetric encryption but generally requires an independent source of trust with a server, such as manually receiving a server key, to operate. 

SSH uses TCP port 22 as its default port.

**Exam Tip: SSH uses public key cryptography for secure remote terminal access and was designed as a secure replacement for Telnet.**

---
### Secure/Multipurpose Internet Mail Extensions (S/MIME)
**Def: Multipurpose Internet Mail Extensions (MIME) is a standard for transmitting binary data via e-mail.**

E-mails are sent as plaintext files, and any attachments need to be encoded so as to fit the plaintext format. MIMIE specifies how this is done with Base64 encoding. 

Because it is plaintext, there is no security associated with the attachments; they can be seen by any machine between sender and receiver. 

**Def: Secure MIMIE (S/MIME) is a standard for public key encryption and signing of MIME data in e-mails.**

S/MIME is designed to provide cryptographic protections to e-mails and is built into the majority of modern e-mail software to facilitate interoperability. 

**Exam Tip: Remember that S/MIME is the standard for e-mail encryption. It provides authentication, message integrity, and nonrepudiation in e-mails.**

---
### Secure Real-time Transport Protocol (STRP)
**Def: The Secure Real-time Transport Protocol (SRTP) is a network protocol for securely delivering audio and video over IP networks.**

SRTP uses cryptography to provide encryption, message authentication and integrity, and replay protection to the Real-time Transport Protocol (RTP) data. 

---
### Lightweight Directory Access Protocol over SSL (LDAPS)
**Def: Lightweight Directory Access Protocol (LDAP) is the primary protocol for transmitting directory information.** 

Directory services may provide any organized set or records, often with a hierarchical structure, and are used in a wide variety of situations, including Active Directory (AD) datasets. 

By default, LDAP traffic is transmitted insecurely. You can make LDAP traffic secure by using it with SSL/TLS, known as LDAP over SSL (LDAPS).

Commonly, LDAP is enabled over SSL/TLS by using a certificate from a trusted certificate authority (CA).

LDAPS uses an SSL/TLS tunnel to connect LDAP services. Technically, this method was retired with LDAPv2 and replaced with Simple Authentication and Security Layer (SASL) in LDAPv3/ SALS (which is not listed in the exam objectives) is a standard method of using TLS to secure services across the internet. 

**Exam Tip: LDAPS communication occurs over port TCP 636. LDAPS communication to a global catalog server occurs over TCP 3269. When connecting to port 636 or 3269, SSL/TLS is negotiated before any LDAP traffic is exchanged.**

---
### File Transfer Protocol, Secure (FTPS)
**Def: File Transfer Protocol, Secure (FTPS) is the implementation of FTP over an SSL/TLS secured channel.**

This supports complete FTP compatibility, yet provides the encryption protections enabled by SSL/TLS. 

FTPS uses TCP port 989 (data connection port) and port 990 (control connection port). As SSL has been deprecated, under RFC 7568, now only TLS is used in FTPS. 

---
### SSH File Transfer Protocol (SFTP)
**Def:  SSH File Transfer Protocol (SFTP) is the implementation of FTP over an an SSH channel.**

This leverages the encryption protections of SSH to secure FTP transfers. Because of its reliance on SSH, SFTP uses TCP port 22. 

---
### Simple Network Management Protocol, Version 3 (SNMPv3)
**Def: The Simple Network Management Protocol, version 3 (SNMPv3) is a standard for managing devices on IP-based networks.**

SNMPv3 was developed specifically to address the security concerns and vulnerabilities of SNMPv1 and SNMPv2. 

SNMP is an application layer protocol, part of the IP suite of protocols, and can be used to manage and monitor devices, including network devices, computers, and other devices connected to the IP network.

All versions of SNMP require ports 161 and 162 to be open on a firewall. 

**Exam Tip: If presented with a network device management scenario, remember the only secure version of SNMP is SNMPv3.**

---
### Hypertext Transfer Protocol over SSL/TLS (HTTPS)
**Def: Hypertext Transfer Protocol Secure (HTTPS) is the use of SSL or TLS to encrypt a channel over which HTTP traffic is transmitted.**

Because of issues with all versions of SSL, only TLS is recommended for use. HTTPS uses TCP port 443 and is the most widely used method to secure HTTP traffic. 

**Def: Secure Sockets Layer (SSL) is a deprecated application of encryption technology developed for transport-layer protocols across the Web.**

This protocol used public key encryption methods to exchange a symmetric key for use in confidentiality and integrity protection as well as authentication. 

The last version, v3, is outdated, having been replaced by the IETF standard TLS. All versions of SSL have been deprecated due to security issues, and in the vast majority of commercial servers employing SSL/TLS, SSL has been retired. 

Outside of term conventions, TLS does all the encryption nowadays. 

**Def: Transport Layer Security (TLS) is an IETF standard for the employment of encryption technology and replaces SSL.** 

Using the same basic principles, TLS updates the mechanisms employed by SSL. 

The standard port for SSL and TLS is undefined because it depends on what the protocol being protected uses; for example, port 80 for HTTP becomes port 443 when it is HTTPS.

**Exam Tip: HTTPS is used for secure web communications. Using port 443 offers integrity and confidentiality.** 

---
### IPSec 
**Def: IPSec is a set of protocols developed by the IETF to securely exchange packets at the network layer (layer 3) of the OSI model (RFCs 2401-2412).**

Once an IPSec connection is established, it is possible to tunnel across other networks at lower levels of the OSI model. 

The set of security services provided by IPSec occurs at the network layer of the OSI model, so higher-layer protocols, such as TCP, UDP, Internet Control Message Protocol (ICMP), Border Gateway Protocol (BGP) and the like, are not functionally altered by the implementation of IPSec services. 

The IPSec protocol series has a sweeping array of services it is designed to provide, including but not limited to access control, connectionless integrity, traffic-flow confidentiality, rejection of replayed packets, data security (encryption), and data origin authentication. 

IPSec has two defined modes--transport and tunnel--that provide different levels of security. IPSec also has three modes of connection: host-to-server, server-to-server, and host-to-host. 

It is possible to use both methods at the same time, such as using transport within one's own network to reach an IPSec server, which then tunnels to the target server's network, connecting to an IPSec server there, and then using the transport method from the target network's IPSec server to the target host. 

IPSec uses the term security association (SA) to describe a unidirectional combination of specific algorithm and key selection to provide a protected channel. If the traffic is bidirectional, two SAs are needed and can in fact be different.

#### Authentication Header (AH) / Encapsulated Security Payload (ESP)
IPSec uses two protocols to provide traffic security:
1. Authentication Header (AH)
2. Encapsulating Security Payload (ESP)

IPSec does not define specific security algorithms, nor does it require specific methods of implementation. IPSec is an open framework that allows vendors to implement existing industry-standard algorithms suited for specific tasks. 

IPSec allows several security technologies to be combined into a comprehensive solution for network-based confidentiality, integrity, and authentication. IPSec uses the following:
- Diffie-Hellman and ECDH key exchange between peers on a public network
- Public key signing of Diffie-Hellman key exchanges to guarantee identity and avoid man-in-the-middle attacks 
- Cryptographic algorithms defined for use with IPSec:
	- HMAC-SHA1/SHA2 for integrity protection
	- TripleDES-CBC for confidentiality
	- AES-CBC for confidentiality
	- AES-GCM for providing confidentiality and authentication together efficiently 
	- ChaCha20 + Poly1305 for providing confidentiality and authentication together efficiently
- Authentication Algorithms:
	- RSA
	- ECDSA (RFC 4754)
	- PSK (RFC 6617)
- Digital Certificates to act as digital ID cards between parties

 To provide traffic security, two header extensions have been defined for IP datagrams. The AH, when added to an IP datagram, ensures the integrity of the data and also the authenticity of the data' origin. 

By protecting the nonchanging elements in the IP header, the AH protects the IP address, which enables data origin authentication. 

The ESP provides security services for the higher-level protocol portion of the packet only, not the IP header. 

**Exam Tip: IPSec AH protects integrity, but it does not provide privacy because only the header is secured. IPSec ESP provides confidentiality, but it does not protect integrity of the packet. To cover both privacy privacy and integrity, both headers can be used at the same time.**

AH and ESP can be used separately or in combination, depending on the level and types of security desired. Both also work with the transport and tunnel modes of IPSec protocols. 

#### Tunnel/Transport
**Def: The transport mode encrypts only the data portion of a packet, thus enabling an outsider to see source and destination IP addresses.**

The transport mode protects the higher-level protocols associated with a packet and protects the data being transmitted but allows knowledge of the transmission itself. 

Protection of the data portion of the packet is referred to as content protection.

Tunnel mode provides encryption of source and destination IP addresses as well as the data itself. This provides the greatest security, but it can be done only between IPSec servers (or routers) because the final destination needs to be known for delivery.

Protection of the header information is known as context protection.

**Exam Tip: In transport mode (end-to-end), security of packet traffic is provided by the endpoint computers. In tunnel mode (portal-to-portal), security of packet traffic is provided between endpoint node machines in each network and not at the terminal hosts machines.**

---

### Post Office Protocol (POP)/ Internet Message Access Protocol (IMAP)
**Def: Post Office Protocol (POP)/ Internet Message Access Protocol (IMAP) refers to POP3 and IMAP4, respectively, using ports 110 for POP3 and 143 for IMAP.**

When POP and IMAP are sent over an SSL/TLS session, secure POP3 utilizes TCP port 995 and secure IMAP4 uses TCP port 993. 

Encrypted data from the e-mail client is sent to the e-mail server over an SSL/TLS session. With the deprecation of SSL, TLS is the preferred protocol today. 

The other mail protocol Simple Mail Transfer Protocol (SMTP), uses a variety of ports, depending on usage. SMTP servers' default port is TCP port 25. Mail clients use SMTP only when communicating with a mail relay server, and then they use TCP port 587 or, when SSL/TLS encrypted, TCP port 465. 

**Exam Tip: IMAP uses port 143, but secure IMAP4 uses port 993. POP3 uses port 110, but secure POP3 uses port 995.**

**Exam Tip: SMTP between servers is TCP port 25, but when clients are involved, it is TCP port 587 or, if encrypted, TCP port 465.** 

---
## Use Cases
Protocols enable parties to have a common understanding of how communications will be handled, and they define the expectations for each party. Since different use cases have different communication needs, different protocols are used in different use cases. 

**Exam Tip: Given a use case on the exam, you need to be able to identify the correct protocol(s) as well as be able to do the same in reverse: identify use cases for a given protocol.**


### Voice and Video 
Voice and video are frequently streaming media and, as such, have their own protocols for the encoding of the data streams. To securely transfer this material, you can use the Secure Real-time Transport Protocol (SRTP), which securely delivers audio and video over IP networks. 

SRTP is covered in RFC 3711. 

**Exam Tip: Remember that SRTP is a secure version of RTP. It is often used for VoIP as well as multimedia application streaming.**

### Time Synchronization
**Def: Network Time Protocol (NTP) is the standard for time synchronization across servers and clients.**

NTP is transmitted over UDP port 123. NTP has no assurance against a man-in-the-middle attack, and although this has raised concerns over the implications, to data, nothing has been done to secure NTP directly.

If you are hypersensitive to this risk, you could enclose all time communications using a TLS tunnel, although this is not an industry practice. 

### E-mail and Web
E-mail and the Web are both native plaintext-based systems. HTTPS, which relies on SSL/TLS, is used to secure web connections. 

E-mail is a bit more complicated to secure, and the best option is via S/MIME. 

### File Transfer 
Secure file transfer can be accomplished via a wide range of methods, ensuring the confidentiality and integrity of file transfers across networks. 

FTP is not secure, but as previously discussed, SFTP and FTPS are secure alternatives that can be used. 

### Directory Services
Directory services use LDAP as the primary protocol. When security is required, LDAPS is a common option, as described previously. 

Directory services are frequently found behind the scenes with respect to logon information. 

### Remote Access 
**Def: Remote access is the means by which users can access computer resources across a network.**

Some security involves securing the authentication process and others for the actual data itself. 

As with many situations that require securing communication channels or data in transit, organizations commonly use SSL/TLS to secure remote access. 

For networking equipment such as routers and switches, SSH is a secure alternative to Telnet. 

For servers and other computer connections, access via VPN, or use of IPSec is common. 

### Domain Name Resolution
**Def: Domain name resolution, is performed primarily by the DNS protocol.**

DNS is a plaintext protocol and the secure version, DNSSEC, is not widely deployed as yet.

For local deployments, DNSSEC has been available in Windows Active Directory domains since 2012. 

Both UCP and TCP port 53 can be used for DNS, with the need of firewall protection between the Internet and TCP port 53 to prevent attackers from accessing zone transfers. 

### Routing and Switching
**Routing and switching are the backbone functions of networking in a system.**

Managing the data associated with networking is the province of SNMPv3. SNMPv3 enables applications to manage data associated with networking and devices. 

### Network Address Allocation
Managing network address allocation functions in a network requires multiple decision criteria, including the reduction of complexity and the management of device names and locations. 

SNMPv3 has many functions that can be employed to manage the data flows of this information to management applications that can assist administrators in network assignments. 

IP addresses can be allocated either statically, which means manually configuring a fixed IP address for each device, or via DHCP, which allows for the automation of assigning IP addresses. 

In some cases, a mix of static and DHCP is used. IP address allocation is part of proper network design, which is crucial to the performance and expandability of a network. 

Learn how to properly allocate IP addresses for a new network--and know your options if you run out of IP addresses. 

**Exam Tip: The past several use cases are related but different. Pay careful attention to the exact wording of the question being asked when you have to choose among options such as domain name resolution, routing, and address allocation. These are all associated with IP networking, but they perform separate functions.**

### Subscriptions Services 
**Def: Subscription services involve the management of data flows to and from a system based on either a push (publish) or pull (subscribe) model.**

Managing what data elements are needed by which nodes is a problem you can tackle by using directory services such as LDAP. 

Another use of subscription services is the Software as a Service (SaaS) model, where software is licensed on a subscription basis. The actual software is hosted centrally, commonly in the cloud, and user access is based on subscriptions. 

# Questions
1. B DNSSEC enables origin of authentication, authenticated denial of existence, and data integrity
2. A
3. C
4. A
5. D
6. B
7. C FTPS uses port 990
8. A
9. D
10. B


