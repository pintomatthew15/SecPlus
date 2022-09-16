# Chapter 22
# Implementing Cloud Security

Securing cloud systems is in one respect no different from securing a traditional IT system: protect the data form unauthorized reading and manipulation. But the tools, techniques, and procedures vary greatly from standard IT, and while clouds can be secure, it is by the application of the correct set of security controls, not by happenstance.

## Cloud Security Controls
Security issues in the cloud are shared between the cloud provider and the user. What is important to remember is to define the requirements up from and have them written into the service agreement with the cloud provider, because unless they are part of the package, they will not occur.

### High Availability Across Zones
Cloud computing environments can be configured to provide nearly full-time availability (that is, a high availability system). 
- This is done by using redundant hardware and software that make the system available despite individual element failures.
- Architecting these failover components across zones provides **high availability across zones**. 
- As with all cloud security issues, the details are in your terms of service with your cloud provider; you cannot just assume it will be high availability. 

**EXAM TIP: Remember that zones can be used for replication and provide load balancing as well as high availability.**

### Resource Policies
Cloud-based resources are controlled via a set of policies. 
- The integration between the enterprise identity access management (IAM) system and the cloud-based IAM system is a configuration element of utmost importance when setting up the cloud environment.
- The level of integration between the cloud-based IAM system and the enterprise-based IAM system will determine the level of work required for regular maintenance activities.

### Secrets Management
A common mistake is to leave data unencrypted on the cloud. Cloud providers offer encryption tools and management services, yet too many companies don't implement them, which sets the scene for a data breach.

**Def: Secrets management is the term used to denote the policies and procedures employed to connect the IAM systems of the enterprise and the cloud to enable communication with the data.**
- Encryption should be treated as a failsafe.
- True secrecy depends on the security of the encryption keys, not the scheme itself.

The secrets used for system-to-system access should be maintained separately from other configuration data and handled according to the strictest principles of confidentiality because these secrets allow access to the data in the cloud.

**EXAM TIP: Use of secrets manager can enable secrets management by providing a central trusted storage location for certificates, passwords, and even application programming interface (API) keys.

### Integration and Auditing 
The moving of computing resources to the cloud does not change the need or intent of audit functions.

Cloud computing audits have become a standard as enterprises are realizing that unique cloud-based risks exist with their data being hosted by other organizations. 
- Organizations used specific cloud computing audits to gain assurance and to understand the risks of information loss.
- Cloud specific audits have two specific requirements:
	1. Understanding of the cloud security environment as deployed,
	2. Related to the data security requirements

Cloud computing audits can be in different forms such as: SOC 1 and SOC 2 reporting, HITRUST, PCI, and FedRAMP.

### Storage
Cloud-based **storage** was one of the first uses of cloud computing. Security requirements related to storage in the cloud environment are actually based on the same fundamentals as in the enterprise environment.

- #### Permissions
Permissions for data access and modifications are handled in the same manner as in an on-premises IT environment. Identity access management (IAM) systems are employed to manage the details of who can do what with each object.
The key to managing this in the cloud is the integration of the on-premises IAM system with the cloud-based IAM system. 

- #### Encryption
Encryption of data in the cloud is one of the fundamental elements to securing one's data when it is on another system. Data should be encrypted in the cloud and the keys maintained by the enterprise, not the cloud provider.
Keys should be managed in accordance with the same level of security afforded keys in the enterprise.

- #### Replication
Data may replicate across the cloud as part of a variety of cloud-based activities. The act of replicating data across multiple systems is part of the resiliency of the cloud, in that single points of failure will not have the same effects that occur in the standard IT enterprise.

- #### High Availability
High availability storage works in the same manner as high availability systems described earlier in the chapter. What's more, the cloud-based IAM system can use encryption protections to keep your data secret, while high availability keeps it available. 

### Network
Cloud-based systems are made up of machines connected using a network. Typically this network is under the control of the cloud service provider (CSP). 

In this fashion, many cloud service providers offer a virtual network that delivers the required functions without providing direct access to the actual network environment.

- #### Virtual Network
Most networking in cloud environments is via a virtual network operating in an overlay on top of a physical network. The virtual network can be used and manipulated by users, whereas the actual network underneath cannot.
This allows the cloud service provider to manage and service network functionality independent of the cloud instance with respect to a user.
The virtual network technology used in cloud environments can include software-defined networking (SDN) and network function virtualization (NFV) as elements that make it easier to perform the desired networking tasks in the cloud. 

- #### Private and Public Subnets
The cloud comes with the capability to use both public-facing and private subnets; in other words, just because something is "in the cloud" does not change the business architecture of some having machines connected to the internet and some not. The cloud-based IAM system can determine who is authorized to access which parts of the cloud's virtual network. 

- #### Segmentation
**Def: Segmentation is the network process of separating network elements into segments and regulating traffic between the segments.** The presence of a segmented network creates security barriers for unauthorized accessors through the inspection of packets as they move from one segment to another.

- #### API Inspection and Integration
**Def: APIs are software interfaces that allow various software components to communicate with each other.** This is true in the cloud just as it is in the traditional IT enterprise. 
**Def: Content inspection refers to the examination of the contents of a request to an API by applying rules to determine whether a request is legitimate and should be accepted.**
The use of API content inspection is an active measure to prevent errors from propagating through a system and causing trouble.

**EXAM TIP: Cloud security controls provide the same functionality as normal network security controls; they just do it in a different environment. The cloud is not a system without controls.**

## Compute
The cloud has become a service operation where applications can be deployed, providing a form of cloud-based computing. The compute aspects of a cloud system have the same security issues as a traditional IT system. 

### Security Groups
**Def: Security groups are composed of the set of rules and policies associated with a cloud instance.**
- These rules can be network rules, such as rules for passing a firewall, or they can be IAM rules with respect to who can access or interact with an object on the system.

### Dynamic Resource Allocation
A cornerstone of cloud computing is having resource that can grow or shrink as the compute requirements change, without the need to buy new servers, expand systems, and so on. 

**Def: dynamic resource allocation software is something that monitors the levels of performance and increases/decreases resources as needed.**

### Instance Awareness
**Def: Instance Awareness is the name of a capability that must be enabled on firewalls, secure web gateways, and cloud-access security brokers (CASBs) to determine if the next system in a communication chain is legitimate or not.**

### Virtual Private Cloud (VPC) Endpoint
**Def: A Virtual private cloud endpoint (VPC) allows connections to and from a virtual private cloud instance.**
- VPC endpoints are virtual elements that can scale. They are also redundant and typically highly available. 
- VPC endpoints can be programmable to enable integration with IAM and other security solutions, enabling cross-cloud connections securely. 

**EXAM TIP: A VPC endpoint provides a means to connect a VPC to other resources without going out over the Internet. In other words, you don't need additional VPN connection technologies or even an Internet gateway

### Container Security
**Def: Container Security is the process of implementing security tools and policies to ensure your container is running as intended.** 
- Container technologies allow your applications and their dependencies to be packaged together into one operational element. 
- This element, also commonly called a manifest, can be version controlled, deployed, replicated, and managed across an environment.
- Running containers in cloud-based environments is a common occurrence because the ease of managing and deploying the containers fits the cloud model well.

**EXAM TIP: Cloud-based computing has requirements to define who can do what (security groups) and what can happen and when (dynamic resource allocation) as well as to manage the security of embedded entities such as containers. Some of these controls are the same (security groups and containers) while other controls are unique to the cloud environment (dynamic resource allocations).


## Solutions
Cloud security solutions are similar to traditional IT security solutions in one simple way: there is no easy, magic solution. Security is achieved through multiple actions designed to ensure the security policies are being followed. 

With respect to the cloud, some specific elements need to be considered, mostly in interfacing existing enterprise IT security efforts with the methods employed in the cloud instance.

### CASB
**Def: Cloud access security broker (CASB) is a security policy enforcement point that is placed between cloud service consumers and cloud service providers to manage enterprise security policies as cloud-based resources are accessed.**
- Can be on-premises or cloud-based item; the key is that it exists between the cloud provider and customer connection, thus enabling it to mediate all access.
- Enterprises use CASB vendors to address cloud service risks, enforce security policies, and comply with regulations. 

**EXAM TIP: Remember that a CASB is a security policy enforcement point that is placed between cloud service consumers and cloud service providers to manage enterprise security policies as cloud-based resources are accessed.**

### Application Security
When applications are provided by the cloud, application security is part of the equation. 
- It all depends on the shared responsibility of the cloud deployment model chosen.
- The responsibilities do not change just because its the cloud, only who is responsible

### Next-Generation Web Gateway (SWG)
**Def: A next-generation secure web gateway (SWG) is a network security service located between the users and the Internet.**
- SWGs work by inspecting web requests against company policy to ensure malicious applications and websites are blocked and inaccessible.
- An SWG includes essential security technologies such as URL filtering, application control, data loss prevention, antivirus, and HTTPS inspection rolled into a comprehensive service to deliver strong web security

Secure web gateways and next-generation firewalls (NGFWs) are similar because they both provide advanced network protection and are able to identify friendly versus malicious traffic. 
- The strength in SWG lies in their ability to use application layer inspection to identify and protect against advanced Internet-based attacks. 


### Firewall Considerations in a Cloud Environment
Firewalls are needed in cloud environments in the same manner they are needed in traditional IT environments. In cloud computing, the network perimeter has essentially disappeared; it is a series of services running outside the traditional IT environment and connected via internet. 

- #### Cost
The cost of a firewall is not just in the procurement but also the deployment and operation. And all of these factors need to be included, not just for firewalls around the cloud perimeter, but internal firewalls used for segmentation as well.

- #### Need for Segmentation
Segmentation can provide additional opportunities for security checks between critical elements of a system. 
Segmenting off appropriate areas of the network and only allowing access to a small set of defined users at the local segment is a strong security protection against attackers traversing your network. 

- #### Open Systems Interconnection (OSI) Layers
**Def: The open systems interconnection (OSI) layers act as a means of describing the different levels of communication across a network.**
- From the physical layer (layer 1) to the network layer (layer 3) is the standard realm of networking.
- Layer 4, the transport layer, is where TCP and UDP function, and through level 7, the application layer, is where applications work. 
- Most modern application-level attacks do not occur at layers 1-3, but rather at layers 4-7. This makes traditional IT firewalls inadequately prepared to see and stop most modern attacks.
- Next Generation firewalls operate up to the application layer (7) to make access decisions. 

**EXAM TIP: Most modern-generation firewalls and secure web gateways operate higher in the OSI model, using application layer data to make access decisions.**


## Cloud-Native Controls vs. Third-Party Solutions
There are two sources for cloud security automation and orchestration tools:
1. The set provided by the cloud service provider.
2. Third-party tools 

Not just a binary choice, each requires real analysis and is situation dependent. 

# Questions
1. B
2. C
3. C (Cost is not a part of the resource policies. Resource policies describe how the elements of IAM, both in the enterprise and in the cloud, work together to provision resources)
4. A (VPC endpoints are not part of the virtual network; although they are virtual applications, they are not part of the network per se)
5. D
6. C
7. B
8. A,B,C,D
9. B
10. A

