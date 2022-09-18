# Chapter 24
# Implement Authentication and Authorization
Authentication and authorization are important to control who has access to computer systems and resources. Principles of controlling access and properly authenticating apply to both internal access and remote access. Remote access requirements are more rigorous, but the smae principles can be applied to internal access.

Access control mechanisms work together with accounts and account policies to determine the proper level of access for users on systems. 

## Authentication Management
Authentication is one of the foundational elements of establishing and maintaining security.
- Authentication management is achieved through a combination of hardware and software elements, including passwords, password keys, vaults, Trust Platform Module (TPM) and hardware security module (HSM) solutions, as well as alternative authentication methods such as knowledge-based systems.

### Password Keys
Passwords represent a secret between a user and an authentication system. One of the challenges in maintaining passwords is for a user to have a system that maintains passwords as secrets, and does so securely. 
- The ususal method invovles managing the group of passwords collectively via a password manager solution, which encrypts the passworsd with a key. 
- This **password key** represents the access pathway to the passwords and changes the myriad of different passwords, which can be unique for every site or use, into a single server represented by the password key.

### Password Vaults
**Def: Software mechanisms designed to manage the problem of users having multiple passwords for the myriad of different systems.** 
- Vaults provide a means of storing the passwords until they are needed, and many password manager programs include addtional functionality such as password generation and password handling via a browser. 
- Vaults do represent a single point of failure because if an attacker gets the key, they have access to all the passwords in the vault

Another form of password vaults is the systems built into software and operating systems (OSs) to securely hold credentials.
- Examples of these are the keychain in macOS and iOS and the credential manager in Microsoft Windows.

### TPM
**Def: The Trust Platform Module (TPM) is a hardware solution on the motherboard, one that assists with key generation and storage as well as random number generation.**
- When the encryption keys are stored in the TPM, they are not accessible via normal software channels are physically separated from the hard drive or other encrypted data locations. 

**EXAM TIP: A TPM acts as a secure cryptoprocessor. It is a hardware solution that assists with key generation and secure, encrypted storage.**

### HSM
**Def: A hardware security module (HSM) is a device used to manage or store encryption keys.**
- It can also assist in cryptographic operations such as encryption, hashing, or the application of digital signatures.
- HSMs are typically peripheral devices connected via USB or a network connection. 

**EXAM TIP: Storing private keys anywhere on a networked system is a recipe for loss. HSMs are diesgned to allow the use of keys without exposing them to the wide range of host-based threats.**


### Knowledge-based Authentication
**Def: Knowledge-based Authentication is a method where the identity of a user is verified via a common set of knowledge.**
- Useful for identification without having a stored secret beforehand

A good example is when accessing a site such as a credit bureau to obtain infromation on yourself.
- The site has a vast array of knowledge associated with you, and it can see if you can identify an address you have lived at, a car you owned, a car or mrotage payment amount.
- In a timed quiz, a user is presented with a series of multiple-choice options. IF they get them all correct, then odds are they are the person they represent themselves to be. 

## Authentication
**Def: Authentication protocols are the standardized methods used to provide authentication services, and in case of wireless networks, these are provided remotely.** The following sections cover several key authentication protoocls and methods in use today. 

### EAP
**Def: The Extensbile Authentication Protocol (EAP) is a protocol for wireless entworks that expands on authentication methods used by the Point-to-Point (PPP) Protocol.**
- PPP is a protocol that was commonly used to directly connect devices to each other.
- EAP is designed to support multiple authentication mechanisms, including tokens, smart cards, certificates, one-time passwords, and public key encryption authentication. 

**Def: PEAP, or Protected EAP was developed to protect the EAP communication by encapsulating it with Trasnsport Layer Security (TLS).**
- EAP was designed assuming a secure communication channel. PEAP provides that protection as part of the protocol via a TLS tunnel.

**Def: EAP-FAST (EAP Flexible Authentication via Server Tunneling) was proposed by Cisco to be a replacement for LEAP, a previous CISCO version of EAP.**
- It offers a lightweight tunneling protocol to neable authentication.
- The distinguishing characterstic is the passing of a Protected Access Credential (PAC) that is used to esablish a TLS tunnel through which client credentials are verified. 

**Def: EAP-TLS is an IETF open standard that uses the TLS protocol to secure the authentication process.**
- EAP-TLS relies onTLS, an attempt to stnadardize the SSL structure to pass because common implementations employ client-side certificates.

**Def: EAP-TTLS is a varient of EAP-TLS that allows for legacy authentication protocols.**
- Easier to set up than EAP-TLS to clients without certifications

**NOTE: WPA3 was released by the Wi-Fi Alliance in 2018, and it specifically is designed to address WPA2 weaknesses, while still allowing older methods. Per the WPA3 specification, a WPA3 station shall perform server certificate validation when using EAP-TTLS, EAP-TLS, and other EAPs not discussed.**

**EXAM TIP: There are two key elements concerning EAP. First, it is only a framework to secure the authentication process. Second, it can support multiple methods and itself is not an actual encryption method.**

### Challenge-Handshake Authentication Protocol (CHAP)
**Def: Challenge-Handshake Authentication Protocol (CHAP) is used to provide authentication across a point-to-point link using PPP.**
- In this protocol, authentication after the link has been established is not mandatory.
- CHAP is designed to provide authentication periodically though the use of a challenge/response system sometimes described as a three-way handshake. 
- The inital challenge is sent to the client. The client uses a one-way hasing function to calculate what the response should be and then sends this back. If they match, communication continues, if not the connection is terminated. 

**EXAM TIP: CHAP uses PPP, which supports these three functions:**
- Encapsulate datagrams across serial links
- Establish, configure, and test links using LCP (Link Control Protocol)
- Establish and configure different network protocols using NCP (Network Control Protocol)

PPP supports two authentication protocols:
- Password Authentication Protocol (PAP)
- Challenge-Handshake Authentication Protocol (CHAP)


### Password Authentication Protocol (PAP)
**Def: Password Authentication Protocol (PAP) authentication involves a two-way handshake in which the username and password are sent across the link in clear text.**
- PAP authentication does not provide any protection against playback and line sniffing. PAP is now a deprecated standard.

**EXAM TIP: PAP is a cleartext authentication protocol and hence is subject to interception. CHAP uses a challenge/response handshake protocol to secure the channel.**

### 802.1X
**Def: 802.1X is an authentication standard that supports port-based authentication services between a user and an authorizatoin device, such as an edge router.**
- 802.1X is commonly used on wireless access points as a port-based authentication service prior to admission tothe wireless network.
- 802.1X over wireless uses either 802.11i or an EAP-based protocl, such as EAP-TLS or PEAP-TLS.

### RADIUS
**Def: Remote Authentication Dial-In User Service (RADIUS) is a protocol that was developed as an AAA protocol.**

RADIUS is designed as a connectionless protocol utilizing User Datagram Protocol (UDP) as its transport-level protocol.
- RADIUS handles conenction type issues such as timeouts instead of the transport layer.

RADIUS is a client-server protocol. 
- The RADIUS client is typically a network access server (NAS). 
- The RADIUS server is a process or daemon running on a Linux or Windows server machine. 
- Communication between RADIUS client and RADIUS server are encrypted using a shared secret that is manually configured into each entity and not shared over a connection. 

**EXAM TIP: Using UDP transport to a centralized network access server, RADIUS provides client systems with authentication and access control within an enterprise network.**

### Single Sign-On (SSO)
**Def: Single sign-on (SSO) is a form of authentication that invovles the transferring of credentails between systems.**
- Single sign-on allows a user to transfer her credentials so that loggin in to one system acfts to log her in to all of them.
- Advatnage: Reduces login hassles for the user.
- Disadvantage: Combines the authentication systems in such a way that if one login is compromised, then all of the user's logins are compromised. 

### Security Assertion Markup Language (SAML)
**Def: Security Assertion Markup Language (SAML) is a single sign-on capability used for web applications to ensure user identities can be shared and are protected.**
- It defines standards for exchanging authentication and authorization data between secuiry domains.
- It is becoming increasingly important with cloud-based solution and with Software as a Service (SaaS) applications, as it ensures interoperability across identity providers.

SAML is an XML-based protocol that uses security tokens and assertions to pass information about a "principal" (typically an end user) to a SAML authority (an "identity provider" or IdP) and the servicep provider (SP). 

**EXAM TIP: By allowing identity providers to pass on credentials to service providers, SAML allows you log in to many different websites using one set of credentials.**

### Terminal Access Controller Access Control System Plus (TACACS+)
**Def: The Terminal Access Controller Access Control System Plus (TACACS+) protcol is the current generation of the TACACS family and has extended attribute control and accounting processes.**

One of the fundamental design aspects is the separation of authentication, authorization, and accoutning in this protocol.
- Not backwards compatible with previous versions of the protocol series.

TACACS+ uses TCP as its transport protocol, typically operating over TCP port 49.
- This port is used for the login process. Both UDP and TCP port 49 are reserved for the TACACS+ login host protocol.

TACACS+ is a client/server protocol, with the client typically beign a network access server (NAS) and the server being a daemon process on a UNIX, Linux, or Windows server. 
- This is important to note because if the user's machine is not the client, then communications between the PC and NAS are typically not encrypted and passed in the clear.
- Communication between the TACACS+ client and TACACS+ server are encrypted using a shared secret that is manually configured into each entity and is noto shared over a connection. 

**EXAM TIP: TACACS+ is a protocol that takes a client/server model approach and handles authentication, authorization, and accounting (AAA) services. It is similar to RADIUS but uses TCP (port 49) as a transport method.**

### OAuth
**Def: Open Authorization (OAuth) is an open protocol that allows secure, token-based authorization on the Internet from web, mobile, and desktop applications via a simple and standard method.**
- OAuth is used by companies such as Google, Facebook, Microsoft, and Twitter to permit users to share information about their accounts with third-party applications or websites.
- OAuth's main strengh is that is can be used by an external partner site to allow access to protected data without having to re-authenticate the user.

OAuth was created to remove the need for users to share their passwords with third-party applications, instead of substituting a token. 

### OpenID
**Def: OpenID is a simple identity layer on top of the OAuth 2.0 protocol, just disccused.**
- OpenID allows clients of all types, inlcuding mobile, JS, and web-based clients, to rquest and receive information about authenticated sessions and end users.
- OpenID is intended to make the process of proving who you are easier, the first step in the authentication-authorization ladder. 
- OpenID was created for federated authentication that lets a third party such as Google or Facebook, authenticate your users for you, by using accounts tha the users already have.

**EXAM TIP: OpenID and OAuth are typically used together, yet have different purposes. OpenID is used for authentication, whereas OAuth is used for authorization.**

### Kerberos
**Def: Kerberos is a network authentication protocol designed for a client/server environment.**
- Kerberos securely passes a symmetric key over an insecure network using the NeedhamSchroeder symmetric key protocol.
- Kerberos is built around the idea of a trust third party, termed a key distribution center (KDC), which ocnsists of two logically separate parts: an authentication server (AS) and a ticket-granting server (TGS). 
- Kerberos communicates via "tickets" that serve to prove the identity of users.

Taking its name from the three-headed dog of Greek mythology, Kerberos is designed to work across the INternet, an inherently insecure environment. Kerbreros uses strong encryption so that a client can prove its identity to a server, and the server can in turn authenticate itself to the client. 
- A complete Kerberos environment is refered to as a Kerberos realm. 
- The Kerberos server contains user IDs and hashed passwords for all users that will have authorization to realm services. 
- The Kerberos server also has shared secret keys with every server to which it will grant access tickets

The basis for authentication in a Kerberos environment is the ticket. 
- Tickets are used in a two-step process with the client. The first ticket is a ticket-granting ticket (TGT) issued by the AS to a requesting client.
- The client can then present this ticket to the server with a request for a ticket to access a specific server.
- The client-to-server ticket is used to gain access to a server's service in the realm. Tickets are timestamped and have a lifetime, no reuse is possible.

The steps invovled in Kerberos authentication is as follows:
1. The user presents credentials and requests a ticket from the Key Distribution Server (KDS).
2. The KDS verifies credentials and usses a TGT.
3. The user present a TGT and request for service to the KDS.
4. The KDS verifies authorization and issues a client-to-server ticket.
5. The user presents a request and a client-to-server ticket to the desired service.
6. If the client-server ticket is valid, service is granted to the client.

**EXAM TIP: KErberos is a third-party authentication service that uses a series of tickets as tokens for authenticating users. The steps involved are protected using strong crytography.**

## Access Control Schemes
**Def: The term access control describes a variety of protection schemes.** It sometimes refers to all security features used to prevent unauthorized access to acomputer system or network. 
- In this sense, it may be confused with authentication.
- More properly, access is the ability of a subject to interact with an object
- Authentication, on the other hand, deals with verifying the identity of a subject.

**Def: Access is the ability of a subject (individual or process) to interact with an object (like a file or hardware device ).**

**Def: Access controls regulate what the individual can actually do on the system-- just because a person is granted entry to the system does not mean that he hsould have access to all data the system contains.**

No matter what specific mechanism is used to implement access controls in a computer system or network, the controls should be based on a specific model of access.

### Attribute-Based Access Control (ABAC)
**Def: Attribute-based access control (ABAC) is a form of access control based on attributes.**
- These attributes can be a wide variety of forms, such as user attributes, resource or object attributes, and environmental attributes. 
- The major difference between ABAC and role-based access control (discussed next) is the ability to include Boolean logic in the access control decision.

**EXAM TIP: The ABAC process of authorization evaluates specific rules and policies against attributes associated with a subject or object. ABAC is often used in large enterprises that use a federated structure. It is somewhat more complicated and costly to implement that other access control models.**


### Role-Based Access Control
ACLs can be cumbersome and can take time to administer properly. 

**Def: In role-based access control (RBAC) instead of each user being assigned specific access permissions for the objects associated with the computer system or network, each user is assigned a set of roles that he or she may perform.**
- The roles are in turn assigned the access permissions necessary to perform the tasks associated with those roles.
- Users will thus be granted permissions to objects in terms of the specific duties they must perform--not according to a security classification associated with individual objects.

### Rule-Based Access Control
The first thing you might notice is the ambiguity introduced with this access control method also using the acronym RBAC. 

**Def: Rule-based access control also use objects such as Access Control Lists (ACLS) to help determine whether or not access should be granted.**
- In this case, a series of rules is contained in the ACL, and the determination of whether to grant access will be made based on these rules.
- Rule-based access control can actually be used in addition to or as a method of implementing other access control methods.

**EXAM TIP: Do not become confused between rule-based and role-based access controls, even though they both have the same acronym. The name of each is descriptive of what it entails and will help you distinguish between them.**

### MAC
**Def: Mandatory Access Control is a means of restricting access to objects based on sensitivity of the information contained in the objects and the formal authorization of subjects to access information of such sensitivity.**
- In this case, the owner or subject can't determine whether access should be granted to another subject, it is the job of the operating system to decide.

**EXAM TIP: Common information classifications include High, Medium, Low, Confidential, Private, and Public.**

In MAC, the security mechanism controls access to all objects, and individual subjects cannot change that access.
- The key here is the label attached to every subject and object.
- The label will identify the level of classification for that object and the level to which the subject is entitled.
- Think of military classifications, it is basically multi-level security

Just because a subject has the appropriate level of clearance to view a document does not mean that she will be allowed to do so. The concept of least privilege, sometimes called "need to know", which is DAC concept (discussed next), also exists in MAC mechanisms. 

**Def: Least privilege means that a person is given access only to information that she needs in order to accomplish her job or mission.**

### DAC
Both discretionary access control (DAC) and mandatory access control are terms originally used by the military to describe two different approaches to controlling an individual's access to a system.

**Def: DACs are a means of restricting access to objects based on the identity of subjects and/or groups to which they belong.**
- The controls are discretionary in the sense that a subject with a certain access permission is capable of passing that permission to any other subject
- In systems that employ DACs, the owner of an object can decide which other subjects can have access to the object and what specific access they might have. Linux-based systems use permission bits that act similarly. 
- The owner of the file can specify what permission (read/write/execute) members in the same group can have and also what permissions all others can have.
- ACLs are also a common mechanism used to implement DAC.

**EXAM TIP: if you are trying to remember the difference between MAC and DAC, just remember that MAC is associated with multilevel security labels such as Top Secret and Secret, whereas DAC uses ACLs. 

### Conditional Access
**Def: Conditional Access is an access control scheme where specific conditions are examined before access is given.**
- Ex: if a user is local, then grant access, if remote deny access. 

Examples of conditional statements:
- If {client is using legacy authentication } then {block access}
- If {device is not compliant} then {block access}
- If {user is an admin} then {enable multifactor authentication}

Conditional access can be very useful when an entity has a wide array of different systems with differing access needs. 

### Privileged Access Management
**Def: Privileged accounts are any accounts with greater-than-normal user access.**
- Typically  root or administrative-level accounts that represent risk in that they are unlimited in their powers.
- They require regular real-time monitoring, if at all possible, and should always be monitored when operating remotely.

**Def: Privileged access management is a combination of the policies, procedures, and technologies for controlling access to and use of elevated or privileged accounts.**
- This enables the organization to log and control privileged access across the entire environment.
- The primary purpose is to limit the attack surface that these accounts have, and to minimize exposure based on current operational needs and conditions.

### File System Permissions
Files need security on systems, to prevent unauthorized access and unauthorized alterations.
- **Def: File system security is the set of mechanisms and processes employed to ensure this critical function.**

If multiple users share a computer system, the system administrator likely needs to control who is allowed to do what when it comes to viewing, using, or changing system resources. 
- Although operating systems vary in how they implement these types of controls, most operating systems use the concepts of permissions and rights to control and safeguard access to resources. 
- **permissions control what a user is allowed to do with objects on a system, and rights define the actions a user can perform on the system.**

The Windows operating system uses the concept of permissions and rights to control access to files, folders, and information resources.

Administrators can grant users and groups permission to perform certain tasks as they relate to files, folders, and registry keys. The basic categories of NTFS permissions are as follows:
- **Full Control**: A user/group can change permissions on the folder/file, take ownership if someone else owns the folder/file, delete subfolder and files, and perform actions permitted by all other NTFS folder permissions.
- **Modify**: A user/group can view and modify files/folders and their properties, can delete and add files/folders, and can delete properties from or add properties to a file/folder.
- **Read & Execute**: A user/group can view the file/folder and can execute scripts and executables, but they cannot make changes (files and folders are read-only).
- **List Folder Contents**: A user/group can list only what is inside the folder (applies to folders only)
- **Read:** A user/group can view the contents of the file/folder and the file/folder properties.
- **Write**: A user/group can write to the file or the folder.

**EXAMP TIP: Permissions can be applied to a specific user or group to control that user or group's ability to view, modify, access, use, or delete resources such as folders and files.**

Under UNIX operating systems, file permissions consist of three distinct parts:
1. **Owner Permissions (read, write, and execute)** - the owner
2. **Group Permissions (read, write, and execute)** - group the owner belongs to
3. **World Permissions (read, write, and execute)** - everybody else

**EXAM TIP: Discretionary access control restricts access based on the user's identity or group membership.**

In Linux, a file's permissions are usually displayed as a series of nine characters, with the first three characters representing the owner's permissions, the second three characters representing the group permissions, and the last three characters representing the permissions for everybody else. 

# Questions 
1. B
2. A (NTFS supports user-level access differentiation and allows you to assign user permissions to files and folders)
3. C
4. D
5. D (SAML is an XML-based protocol that uses security tokens and assertions to pass info about a principle.)
6. A
7. A
8. A (Typically OpenID is used for authentication, and OAuth is authorization)
9. B
10. D

