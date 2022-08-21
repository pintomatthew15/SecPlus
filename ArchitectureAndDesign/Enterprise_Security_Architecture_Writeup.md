# Chapter 9
# Enterprise Security Architecture



## Configuration Management
Configuration management is essential to secure the system using the specific configuration the implementation intended. 

Alterations to configurations can add functionality, remove functionality, and even completely change system functionality, remove functionality, and even completely change system functionality by altering elements of a program to include outside code. 

Monitoring and protecting a system from unauthorized configuration changes is important for security.

Because all enterprises are different, it is essential for each enterprise to define the standards and frameworks it uses to guide configuration management.

### Diagrams
**Def: Diagrams are commonly used in architectural specifications to communicate how the enterprise is configured --from network diagrams that describe physical and logical connections, to annotated diagrams that provide essential settings.**

Also, in the context-rich environment of specification lists, it is easier to digest and understand relationships when presented via diagram.

### Baseline Configuration
**Def: The baseline configuration is the starting point for all future baseline assessments.**

This baseline is originally created at system creation and is a representation of how the system is supposed to be configured. 

As time goes on and updates are applied, this configuration will require updating, making it current with the desired system configuration. 

A baseline deviation is a change from the original baseline value. This change can be positive, lowering risk, or negative, increasing risk.

The biggest challenge is in running the baseline scans, or automating them, to determine when deviations occur.

### Standard Naming Conventions
Standard naming convetions are important in an enterprise so that communications can be clear and understood. Enterprises adopt standard naming conventions to reduce sources of error and improve the clarity of communications

Having servers named in a manner that facilitates clear communication eliminates errors.

### Internet Protocol (IP) Schema
Internet protocol addresses in version 4 are 32-bit numbers hardly useful for someone to comprehend. Therefore a notation dividing the number into four sets of 8 bits, represented as xxx.xxx.xxx.xxx, where x is between 0 and 255, was created.

The actual address is composed of a network and host portion. 

Determining how to divide these portions up maximize the utilization of an address space is the process of subnetting. 

There are two main addressing schemes: The Class A/B/C scheme and the CIDR notation method. 
- The Class A/B/C scheme breaks the network and host at the decimal points of the notation listed earlier
- The CIDR notation is more granular with the address of the network portion being listed in bits preceded by a / symbol.

For an IP address that is broken into a Class A network, the leading bit by definition is 0, followed by 7 bits for the network space and 24 bits for the hosts. 
-  This allows 128 networks of 16,777,216 hosts and is denoted as /8 in CIDR notation

Class B networks begin with 10 for the first two bits, and then 14 bits for networks and 16 bits for hosts 
- For a total of 65,536 hosts. This is /16 in CIDR notation

Configuration management includes developing physical and logical diagrams, establishing secure baselines, creating understandable standard naming convetions, and implementing secure IP schemas. 

---
## Data Sovereignty
**Def: A relatively new type of legislation several countries have enacted recently that mandates data stored within their borders is subject to their laws, and in some cases that data originating within their borders must be stored there.**

Data sovereignty laws apply to data that is stored in a specific country.

---
## Data Protection
**Def: The set of policies, procedures, tools, and architectures used to ensure proper control over the data in the enterprise.**

Different data elements require different levels of protection and for different reasons.

Data is the most important element to protect in the enterprise. Equipment can be purchased, replaced, and shared without consequence; it is the information that is being processed that has the value. 

**Data security** refers to the actions taken in the enterprise to secure data, wherever it resides: in transit/motion, at rest, or in processing

### Data Loss Prevention (DLP)
Data Loss Prevention (DLP) solutions serve to prevent sensitive data from leaving the network without notice. 

As data is stored in the enterprise, typically in databases, it is thus subject to loss directly from these points. 

Enterprise-level DLP monitoring: where file activity is reported to centralized systems and to specialized DLP offerings such as the conent DLP appliances offered by numerous security companies.

DLP solutions are designed to protect data in transit/motion at rest, or in processing from unauthorized use or exfiltration. 

### Masking and Encrpytion
**Def: Involves the hiding of data by substituting altered values.**

A mirror version of a database is created, and data modification techniques such as character shuffling encrpytion, and word or character substitution are applied to change the data. 

Data masking makes reverse engineering or detection impossible. The use of data masking to make data sets for testing and to load honeypots with usable-yet fake data is a common practice.

Data encrpytion continues to be the best solution for data security. Properly encrypted, the data is not readable by an unauthorized party. 

**Def: Encrpytion is the use of sophisticated mathematical techniques to prevent persons with unauthorized access to data from actually reading the data**

Having key fields encrypted in storage prevents their loss, as any disclosure is unreadable. 

Employing encryption is one of the elements an enterprise can take that, when properly deployed, makes the loss of data a non-event.


### Data At Rest
**Def: Data at rest refers to data being stored.**

Data is stored in a variety of formats: in files, in databases, and as structured elements. 

Whether in ASCII, XML, JavaScript Object Notation (JSON), or a database, and regardless of what media it is stored on, data at rest still requires protection commensurate with its value. 

### In Transit/Motion
Data has value in the enterprise, but for the enterprise to fully realize the value, data elements need to be shared and moved between systems.

Whenever data is in transit/motion, being moved from one system to another, it needs to be protected. The most common method of protection is encrpytion 

What is important is to ensure that data is always protected in proportion to the degree of risk associated with a data security failure. 

### In Processing
**Def: data that is actively being used, either in a processor or other computational element.**

It is harder to protect data in use compared to it being in transit or storage 

Can't really use encrpytion here. 

Protected memory schemes and address space layout randomization are two tools that can be used to prevent data security failures during processing. 

**EXAM TIP: Remember the three important states of data and how it is protected at rest, in transit/motion, and in processing.**

---
## Sub Topics

### Tokenization
**Def: The use of a random value to take place of a data element that has traceable meaning.**

Example: Credit card approval process; you do not need to keep a record of the card number, the chardholder's name, or any of the sensitive data concerning the card verificiation code (CVC) because the transaction agent returns an approval code, which is a unique token to that transaction.

You can store this approval code, the token, in your system, and if there comes a time you need to reference the original transaction, this token provides you with complete traceability to it. 

Tokens are used all the time in data transmission systems involving commerce because they protect sensitive information from being reused or shared, yet they maintain the desired nonrepudiation characteristics of the event.

The use of tokenization in creating and testing data sets is another common use of the technology. 

### Rights Management
**Def: Rights management is the systemic establishment of rules and order to the various rights that users can invoke over digital objects.**


At the file level there is read, write, and other access control options

At a context level, there are editing, copying, replaying, etc

Digital rights mangement (DRM) is the term used to describe typical rights scenarios associated with various types of media files, including playing them, copying them, editing them, and saving them to your own device.

Major content platforms have the ability to manage rights on an enterprise-level scale; what is needed, however, is the definition of the rights scheme desired. 

### Geographical Considerations
It is important to consider laws and regulations that do not stop at physical borders.

### Response and Recovery Controls
Enterprises are designed with infrastructure that enables data to be the lifeblood of a modern organization. 

Two of the elements that have to be designed into the enterprise are disaster recovery (DR) and business continuity (BC). 

Having backups is great, but they are of no use if you cannot recover and restore them 

In many cases, a complete data recovery can be a multiday effort, and one that has to be designed in place to begin while still operating in DR/BC modes and then switch back once the data is synced up.

### Secure Sockets Layer (SSL)/ Transport Layer Security (TLS) Inspection
The use of **Transport Layer Security (TLS)** in an enterprise can provide a lot of protections to data, but it also can prevent security tools from inspecting data for exfiltration and other concerns. 

The TLS protocol is designed to allow applications to communicate across a network to ensure the confidentiality and integrity of the communication.

To perform the task of **Secure Sockets Layer (SSL)/Transport Layer Security (TLS) inspection,** the appliance must receive a set of proper keys to the encryption

The appliance can then receive the data, decrypt the data, perform its security task, re-encrypt the data using the same keys, and send the data on its way to the destination. 

It is common for next-generation firewalls (NGFWs) to have TLS inspection built in, providing this level of protection for both inbound and outbound data. 

TLS inspection consists of two connections:
1. Server protection: inspects incoming connections to servers
2. Client protection: one from the client to the firewall and one from the firewall to the server

By decrypting the data communication at the firewall, the appliance is able to perform deep packet inspection and other security functions before re-encrypting the data and sending it on its way. 

This feature prevents encrypted channels from bypassing security elements in a network.

---
## Hashing

**Def: A technology whereby the uniqueness of a data element can be represented in a fixed-length string.**

From an enterprise architecture point of view, one should look at hashing as a means of enabling data protection while still enabling the use of the underlying data.

The hash value of the data element can acts as a replacement for the data, and, if disclosed, the hash value cannot be reversed back to the data.

**EXAM TIP: A hash function is a special mathematical function that performs one-way encryption, which means that once the algorithm is processed, there is no feasible way to use the ciphertext to retrieve the plaintext that was used to generate it.**

---
## API Considerations
The application programming interface, or API, is a critical element in digital enterprises, allowing a method of integrating connections between different applications.

APIs are like the doors and windows of modern applications. 

They provide access to applications and the data behind them. Insecure or poorly implemented APIs can be equated to malfunctioning doors and windows, which make protection of the valuable items in the house much more difficult. 

Designing in the correct set of authentication and authorization protocols is essential to enable this needed technology with the ability to function reliably and securely in the enterprise.

---

## Site Resiliency
**Def: Site resiliency considerations can be connected to the idea of restoration sites and their availablility.**

Related to the location of backup storage is where the restoration services will be located

This data will need to be processed somewhere, which means that computing facilities similar to those used in normal operations are required.

The recovery problem can be approached in a number of ways, including hot sites, warm sites, and cold sites. 

### Hot Sites
**Def: A fully configured environment, similar to the normal operating environment that can be operational immediately or within a few hours, depending on its configuration and the needs of the organization.**

### Warm Sites
**Def: A partially configured, usually having the peripherals and software but perhaps not the more expensive main processing computer.**

It is designed to be operational within a few days.

### Cold Sites
**Def: A cold site will have the basic environmental controls necessary to operate but few of the computing components necessary for processing. 

Getting a cold site operational may take weeks. 

**EXAM TIP: Alternate sites have been highly tested on the exam. It is important to know whether the data is available or not at each location. For example, a hot site has duplicate data or a near-ready backup of the original site. A cold site has no current or backup copies of the original site data. A warm site has backups, but they are typically several days or weeks old.**

---

## Deception and Disruption
**Def: Decption and Disruption have become tools in the defender's arsenal against advanced threats.**

Because a threat actor has limited information about how a system is architected, the addition of deceptive elements such as honeypots/nets can lead to situations where the adversary is discovered.

This fake configuration is not part of your enterprise configurations, so no system or person should ever touch something fake unless they are actively seeking something or there is a misconfiguration.

### Honeypots
**Def: A server that is designed to act like a real server on a corporate network, but rather than having real data, the honeypot possesses fake data.**

A honeypot acts as a trap for attackers, as traffic in the honeypot can be assumed to be malicious. 

### Honeyfiles
**Def: a file that is designed to look like a real file on a server, but the data it possesses is fake.**

A honeyfile acts as a trap for attackers, and the data in the file can contain triggers to alert DLP solutions.

A variation of a honeyfile is honeyrecord in a database. There records serve the same purpose: they are fake and are never used, but if they are ever copied, you know there is unauthorized activity. 

### Honeynets
**Def: a network designed to look like a corporate network but is made attractive to attackers.**

A honeynet is a collection of honeypots. 

Honeynets will be visited or used by legitimate systems, as legitimate systems have connections to the real servers, so any traffic on a honeynet is presumed to be that of an attacker, or a misconfigured system. 

### Fake Telemetry
**Def: synthetic network traffic that resembles genuine communications, delivered at an appropriate volume to make honeynets and honeypots look real.**

Basically fake network traffic

### DNS Sinkhole
**Def: A DNS provider that returns specific DNS requests with fake results.**

 The results in the requester being sent to the wrong address, usually a nonroutable address. 
 
 When a computer visits a DNS server to resolve a domain name, the server will give a result, if available, otherwise, it will send the resolution request to a higher-level DNS server for resolution. 
- This means the higher the DNS sinkhole is in this chain, the more requests it will affect and the more beneficial the effect it can provide

**EXAM TIP: A DNS sinkhole is a deception and disruption technology that returns specific DNS requests with false results. DNS sinkholes can be used in both destructive and constructive ways. When used in a constructive fashion, a DNS sinkhole prevents users from accessing malicious domains.**

---

# Questions
1. B
2. C
3. D
4. C
5. A
6. D
7. A D (honeypots and DNS sinkholes are part of deception and disruption techniques not data protection)
8. B
9. D
10. A B C 
