# Chapter 20
# Wireless Security

As wireless use increases, the security of the wireless protocols has become a more important factor in the security of the entire network. As a security professional, you need to understand wireless network applications because of the risks inherent in broad-casting a network signal where anyone can intercept it. 

## Cryptographic Protocols
**Def: Standards used to describe cryptographic methods and implementations to ensure interoperability between different vendors' equipment.**
- 802.11 is the protocol for WIFI
	- The designers of 802.11 attempted to maintain confidentiality in wireless systems by introducing WEP, which uses a cipher to encrypt the data as it is transmitted through the air. 
	- WEP worked at first but was eventually proven to be weak. 

WPA replaced WEP with the Temporal Key Integrity Protocol (TKIP)
- TKIP works by using a shared secret combined with the card's MAC address to generate a new key, which is mixed with the initialization vector (IV) to make per-packet keys that encrypt a single packet using the same RC4 cipher used by traditional WEP.
- WPA eventually becomes flawed

WPA2 and WPA3 are the newer versions that are still used today

**Note: WEP and WPA are no longer under Sec+ exam objectives, but the facts and background are relevant to WPA2 and illustrate the process.**

### Wi-Fi Protected Access 2 (WPA2)
IEEE 802.11i is the standard for security in wireless networks and is also known as Wi-Fi Protected Access 2 (WPA2). It uses 802.1X to provide authentication and uses Advanced Encryption Standard (AES) as the encryption protocol.
- WPA2 uses AES block cipher, a significant improvement over WEP and WPA's use of the RC4 stream cipher. 

While WPA2 addressed the flaws in WPA and was the de factor standard for many years on wireless networks that were serious about security, it too fell to a series of issues, leading to the development of WPA3. 
- The WPA2-Personal passphrase can be cracked using brute force attacks
- Once data is captured online, the guessing can be done offline

WPA2 comes in personal and enterprise version
- WPA2 personal is called WPA2-PSK because it uses authentication based on a pre-shared key (PSK), which allows home users without an enterprise authentication server to manage the keys.
- WPA2-Enterprise replaced the pre-shared key with IEEE 802.1X, which is discussed in its own section later in this chapter. 
	- This creates stronger keys, and the information is not subject to capture. 

In WPA2, an attacker can record the 4-way handshake between a client and the access point and use this data to crack the password. 

### Wi-Fi Protected Access 3 (WPA3) 
**Def: Wi-Fi Protected Access 3 (WPA3) is the successor to WPA2.**
- Developed in 2018 to combat weakness in WPA3
- Uses Simultaneous Authentication of Equals (SAE) instead of PSK authentication used in previous WPA versions.

Additional strengths:
- **Authenticated encryption**: 256-bit Galois/Counter Mode Protocol
- **Key derivation and confirmation**: 384-bit Hashed Message Authentication Code (HMAC) with Secure Hash Algorithm (HMAC-SHA-384)
- **Key establishment and authentication**: Elliptic Curve Diffie-Hellman (ECDH) exchange and Elliptic Curve Digital Signature Algorithm (ECDSA) using 384-bit elliptic curve
- **Robust Management Frame Protection**: 256-bit Broadcast/Multicast Integrity Protocol Galois Message Authentication Code (BIP-GMAC-256)

**Exam Tip: WPA2 uses pre-shared keys; WPA3 does not. If SAE is used, it is for WAP3-level authentication. Forward secrecy is only provided by WPA3.**

### Counter Mode/CBC-MAC Protocol (CCMP)
CCMP stands for Counter Mode with Cipher Block Chaining-Message Authentication Code Protocol(or Counter Mode with CBC-MAC Protocol). 

**Def: CCMP is a data encapsulation encryption mechanism designed for wireless use. CCMP is actually the mode in which the AES cipher is used to provide message integrity.**
- Unlike WPA/TKIP, WPA2/CCMP requires new hardware to perform the AES encryption.

### Simultaneous Authentication of Equals (SAE)
**Def: Simultaneous Authentication of Equals (SAE) is a password-based key exchange method developed for mesh networks.**
- Uses the Dragonfly protocol to perform a key exchange and is secure against passive monitoring. 
- Because of its zero knowledge key generation method, it is resistant to active, passive, and dictionary attacks. 
- To configure SAE, you must set the security parameter k to a value of at least 40, per the recommendation in RFC 7664, "Dragonfly Key Exchange", for all groups to prevent timing leaks. 

## Authentication Protocols
Wireless networks have a need for secure authentication protocols. The following authentication protocols should be understood for the Sec+ exam: EAP, PEAP, EAP-FAST, EAP-TLS, EAP-TTLS, IEE 802.IX, and RADIUS Federation. 

### Extensible Authentication Protocol (EAP)
**Def: The Extensible Authentication Protocol (EAP) is a protocol for wireless networks that expands on authentication methods used by the Point-to-Point Protocol (PPP).**
- PPP is a protocol that was commonly used to directly connect devices to each other. 
- EAP can support multiple authentication mechanisms, including tokens, smart cards, certificates, one-time passwords, and public key encryption authentication. EAP has been expanded into multiple versions. 

### Protected Extensible Authentication Protocol (PEAP)
**Def: PEAP, or Protected EAP, was developed to protect EAP communication by encapsulating it with Transport Layer Security (TLS).**
- PEAP provides that protection as part of the protocol via a TLS tunnel. 

### EAP-FAST
**Def: EAP-FAST (EAP Flexibile Authentication via Secure Tunneling) is described in RFC 4851 and proposed by Cisco to be a replacement for LEAP, a previous Cisco version of EAP.**
- It offers a lightweight tunneling protocol to enable authentication. 
- The distinguishing characteristic is the passing of a Protected Access Credential (PAC) that is used to establish a TLS tunnel through which client credentials are verified. 

### EAP-TLS
**Def: EAP-TLS is an internet Engineering Task Force (IETF) open standard (RFC 5216) that uses the TLS protocol to secure the authentication process.**
- EAP-TLS relies on TLS, an attempt to standardize the Secure Sockets Layer (SSL) structure to pass credentials. 
- This is still considered one of the most secure implementations, primarily because common implementations employ client-side certificates to break the TLS channel. 

**EXAM TIP: Sec+ has used questions concerning certificates and authentication protocols in the past. EAP-TLS for mutual authentication requires client and server certificates. PEAP and EAP-TTLS eliminate the requirement to deploy or use client certificates. EAP-FAST does not require certificates.**

### EAP-TTLS
**Def: A variant of the EAP-TLS protocol.**
- Server authentication to the client is the same, but the client is able to use legacy authentication protocols to the server
- The authentication process is protected by the tunnel from man-in-the-middle attacks, and although client-side certificates can be used, they are not required. 

**NOTE: WPA3 is designed to work together with a variety of EAP methods in an enterprise. A WPA3 station performs server certificate validation when using EAP-TTLS, EAP-TLS, EAP, and PEAP methods.**

**EXAM TIP: There are two key elements concerning EAP. First, it is only a framework to secure the authentication process, not an actual encryption method. Second, many variants exist, and understanding the differences, and how to recognize them in practice is important for the exam.**

### IEEE 802.1X
**Def: An authentication standard that supports port-based authentication services between a user and an authorization device, such as an edge router.**
- IEEE 802.1X is commonly used on wireless access points as a port-based authentication service prior to admission to the wireless network.

### Remote Authentication Dial-in User Service (RADIUS) Federation
Using a series of RADIUS servers in a federated connection has been employed in several worldwide RADIUS federation networks.
- Example is eduroam (short for education roaming) which connects users of education institutions worldwide.
- Because credentials must pass multiple different networks, the EAP methods are limited to those with certificates and credentials to prevent loss of credentials during transit. 

**EXAM TIP: RADIUS Federation allows users to use their normal credentials across trust networks. This allows users in one organization to authenticate and access resources on another trusted organization's network using one set of credentials.**

## Methods 
Authentication methods are used to provide authentication services (in the cases of wireless networks, remotely) through the configuration of the protocol used to protect the communication channel. This sections covers the configuration of the systems so that protocols can be employed in a secure manner.

### Pre-shared Key (PSK) vs. Enterprise vs. Open
When building a wireless network we must decide:
- How we plan to employ security on the network
- Who will be allowed to connect
- What level of protection will be provided in the transmission of data between devices and the access point.

WPA and WPA2 have two methods to establish a connection: PSK and Enterprise
- PSK is an up to 63 character passphrase that must be shared between users securely. It is also vulnerable to brute force
- In Enterprise, the devices use IEEE 802.1X and a RADIUS authentication server to enable a connection. 

In WEP-based systems, there are two options: Open System authentication and shared key authentication. 
- **Def: Open system authentication is not truly authentication; instead, it is merely a sharing of a secret key based on the SSID.**
	- Mobile client matches the SSID with the access point and requests a key (called authentication) to the access point.

**EXAM TIP: Understand the differences between PSK, Enterprise, and Open System Authentication.**

### Wi-Fi Protected Setup (WPS)
**Def: A network security standard created to provide users with an easy method of configuring wireless networks.**
- Designed for home and small business networks, this standard uses an eight-digit PIN to configure wireless devices.
- WPS used a series of EAP messages that can be susceptible to a brute force attack that reveals the PIN. 
- The Wi-Fi Alliance added Easy Connect to replace it. 

### Captive Portals
**Def: Captive portals refer to specific techniques of using an HTTP client to handle authentication on a wireless network.**
- A captive portal opens a web browser to an authentication page.
- This occurs before the user is granted admission to the network.

**EXAM TIP: Captive portals are common in coffee shops, airports, hotels, and stores. The user accepts the offered conditions, views, and advertisement, provides an e-mail address or other authentication requirement, and is granted access to the portal.**

## Installation Considerations
Elements that need to be considered are based on signal propagation and interference. Signal propagation is a function of antennas, signal strength, and the physical layout of a facility, including intervening structures. These are all addressed in site surveys, Wi-Fi analyzers, and software to optimize access point placement.  

### Site Surveys
You need take multiple factors into account when generating a coverage map.

**Def: A site survey involves several steps: mapping the floor plan, testing for RF interference, testing for RF coverage, and analyzing material via software.
- The software can suggest placement for access points.

Once AP are placed, you remap the site to compare results.
- This is also used when auditing existing wireless networks.

**Exam Tip: Wireless networks are dependent on radio signals to function. It is important to understand the antenna type, placement, and site surveys are used to ensure proper coverage of a site, including areas blocked by walls, interfering signals, and echoes.**

### Heat Maps
**Def: A Wi-Fi heat map is a map of wireless signal coverage and strength.**
- Typically a heat map shows a layout of a room, floor, or facility overlaid by a graphical representation of a wireless signal.

**Exam Tip: A site survey is a process for determining Wi-Fi signal strengths; the heat map is one of the outcomes and is part of the survey.**

### Wi-Fi Analyzers
**Def: Wi-Fi analyzers provide a means of determining signal strength and channel interference.**
- A Wi-Fi analyzer is a RF device used to measure signal strength and quality. 
- Determines if the Wi-Fi signal strength is sufficient

### Channel Overlays
Wi-Fi radio signals exist at specific frequencies: 2.4 GHz and 5.0 GHz. Each of these signals is broken into a series of channels,, and the actual data transmissions occur across these channels. 
- Wi-Fi versions of IEEE 802.11 work with channel frequencies of 2400 MHz and 2500 MHz, hence the term 2.4 GHz for the system. The 100 MHz in between is split into 14 channels of 20 MHz each.
	- As a result, each channel overlaps with up to four other channels.
	- For this reason most 2.4 GHz systems use channels 1, 6, and 11. 
	- If you find neighbors using channels 2 and 10, you would want to use 6.

Beyond just improving channel overlay issues, the Wi-Fi Alliance has improved system throughput through the use of newer standards, including 802.1 ac and 802.1 ax. 

### Wireless Access Point (WAP) Placement
**Def: Wireless access point (WAP) placement is seemingly simple, perform a site survey, mine the optimum placement based on RF signal strength, and you are done, but WAP also need power.**

For security reasons, you should be aware that Wi-Fi signals go through walls, so placing access points where they produce large areas of coverage outside a facility may lead to outsiders accessing your system. 

### Controller and Access Point Security
Hur dur physical security is important 


# Questions
1. D (WPS uses an eight-digit PIN to establish a connection between devices)
2. C (EAP is only a framework to secure the authentication process)
3. A 
4. D
5. B (SAE is currently the most secure way to establish connection via wireless)
6. B
7. C
8. B,C,D
9. D (EAP TTLS is not easy to setup since it requires legacy support )
10. A
