# Chapter 29
# Mitigation Techniques and Controls

Systems cannot be completely secure by design or use, but a series of elements can be used to increase the security posture of a system. These controls and mitigation elements work to reduce risk in the system. This chapter explores various controls and mitigations covered on the Sec+ exam. 

## Reconfigure Endpoint Security Solutions
**Def: Endpoint security solutions are controls that can mitigate risk at the endpoint.**
- Endpoint solutions must recognize the threat and then trigger a specific action to mitigate the risk. 
- Antivirus/antimalware solutions are the typical endpoint protection most users think of, as are elements such as firewalls and intrusion protection elements. 

Most integrated endpoint elements can be part of the operating system, or they can work with the operating system (OS) to alter behavior to enforce rules.
- Microsoft has two mechanisms that are part of the Windows OS to manage which applications can operate on their machines:
	- **Software restrictive policies**: Employed via group policies, software restrictive policies allow significant control over applications, scripts, and executable files. The primary mode is by machine and not by user account.
	- **User account level control**: Enforced via AppLocker, a service that allows granular control over which users can execute which programs. Through the use of rules, an enterprise can exert significant control over who can access and use installed software.
- On a Linux platform, similar capabilities are offered from third-party vendor applications.
- The last question is, what do you do when something is detected that's outside the desired specification? The typical response is to quarantine, which is described later in this chapter. 

### Application Approved List
Applications can be controlled at the OS at start time via verification of the application against a list of approved applications (whitelisting) and a list of blocked or denied applications (blacklisting).
- **Def: The application approved list consists of a list of allowed applications.**
- Gets more complicated for multipurpose machines

### Application Blocklist/Deny List
The use of an application block or deny list is essentially noting which applications should not be allowed to run on the machine.
- Basically a permanent "ignore" or "call block" type of capability
- Difficult if not impossible to use against dynamic threats

**EXAM TIP: Whitelisting, or the use of an application allow list, is the use of a list of approved applications. If an app, is not on the whitelist, access is denied and the app won't install or run. Blacklisting, or the use of an application blocklist/deny list, is a list of apps that are deemed undesirable. If an app is blacklisted, it won't be installed or allowed to run.**

### Quarantine
When a system detects a condition that meets a specific set of rules and determines that an action is required, one of the important decisions is the finality of that action. 
- **Def: Quarantining an item is to render it disabled but not permanently removed from the system.**
- A quarantine options gives the user the opportunity to undo the disablement. 

## Configuration
Configurations are the lifeblood of a system. Protecting a system from configuration changes is essential to secure the system in the specific configuration that the implementation intended. 

### Firewall Rules
Firewalls operate by enforcing a set of rules on the traffic attempting to pass.
- **Def: Firewall rules state whether the firewall should allow particular traffic to pass through or block it.**

Fire walls have a directionality; there are inbound and outbound rules. 
- Inbound: Protect against incoming traffic
- Outbound: protect against sending data to unauthorized or dangerous places. 

### MDM
Knowledge of **mobile device management (MDM)** concepts is essential in today's environment of connected devices.
- When viewed as a comprehensive set of security options for mobile devices, every corporation should have and enforce an MDM policy. The policy should require the following:
	- Device locking with a strong password
	- Encryption of data on the device
	- Device locking automatically after a certain period of inactivity
	- The capability to remotely lock the device if it is lost or stolen
	- The capability to wipe the device automatically after a certain number of failed login attempts
	- The capability to remotely wipe the device if it is lost or stolen

Password policies should extend to mobile devices, including lockout and, if possible, the automatic wiping of data.

**EXAM TIP: Mobile device management (MDM) is the term for a collective set of commonly employed protection elements associated with mobile devices.**

### DLP
**Def: Data loss prevention (DLP) refers to technology employed to detect and prevent transfers of data across an enterprise.**
- Employed at key locations, DLP technology can scan packets for specific data patterns. 
- This technology can be tuned to detect account numbers, secrets, specific markers, or files.

DLP began its life as an enterprise-level device or appliance, but the deployment of this technology has expanded to endpoints, including OSs and apps such as Microsoft 365.

**EXAM TIP: DLP can be classified as a technical control. Its primary goal is to detect breaches and prevent data loss.**

### Content Filter/URL Filter
**Def: Content filers/URL filters are used to limit specific types of content across the Web to users.**
- A common use is to block sites that are not work related, and to limit items such as Google searches and other methods of accessing content determined to be inappropriate.
- Big issue is making it too broad

### Update or Revoke Certificates
Certificates are used to pass cryptographic keys as part of a wide variety of processes--from signing data, to authentication services, to setting up cryptographic services between devices.
- Most of the work with certificates is automated and handled behind the scenes, but it is still reliant on a valid set of certificates and approved certificate chains.
- Most important goal is to protect certificate chain

**EXAM TIP: Certificates remain valid for a specific duration of time. When a certificate is about to expire, it should be renewed if needed. However, sometimes certificates are revoked because the owner is no longer trusted, the encryption keys have been compromised, or there are changes or other errors with the certificate.**


## Isolation
**Def: Isolation is the use of networking protocols and resultant connectivity to limit access to different parts of a network.**
- This limit can be partial or it can be complete, as offered by an air gap, and this method of separation is used to enforce different trust boundaries.

Isolation can also be employed as part of an incident response strategy, where affected systems are isolated from the rest of the network. 

## Containment
Containment is the key concept in incident response. 
- **Def: Containment is the act of performing specific actions that limit the damage potential of an incident, keeping the damage limited, and preventing further damage.**
- The objective is the same: limit the exposure of the system to the damaging element. 

## Segmentation
As networks have become more complex, with multiple layers of tiers and interconnections, a problem can arise in connectivity.
- One limitation of spanning tree protocol (STP) is its inability to manage layer 2 traffic efficiently across highly complex networks.
- STP was created to prevent loops in layer 2 networks and has been improved in its current version, called Rapid Spanning Tree Protocol (RSTP). 

One name associated with flat network topologies is **network fabric**, a term meant to describe a flat, depthless network. 
- Network fabrics are becoming increasingly popular in data centers and other areas of high-traffic density, as they can offer increased throughput and lower levels of network jitter and other disruptions. 

Modern networks, with their increasingly complex connections, result in systems where navigation can become complex between nodes. 
- Just as a DMZ-based architecture allows for differing levels of trust, the isolation of specific pieces of the network using security rules can provide differing trust environments.
- There are several terms used to describe the resultant architecture, including network segmentation, segregation, isolation, and enclaves. 
- **Enclaves** is the most commonly used term to describe sections of a network that are logically isolated by segmentation at the networking protocol.  

**EXAM TIP: Segmentation, as it applies to networking security, is a broad term. VLANs, firewalls, and even storage segmentation and containerization can be used for segmentation purposes.**

## Secure Orchestration, Automation, and Response (SOAR)
Security operations in an enterprise environment have a lot of moving parts. From a top-level view, you have vulnerability management, threat intelligence, incident response, and automated security operations. 
- All of these operate off of data--data that comes from a myriad of network appliances, intrusion detection system, firewalls, and other security devices. 
- This data is typically fed into a security information and event management (SIEM) system that can collect, aggregate, and apply pattern matching to the volumes of data. 
- **Def: Security Orchestration, automation, and response (SOAR) systems take SIEM data as well as data from other sources and assist in the creation of runbooks and playbooks.**

Security administrators can create a series of runbooks and playbooks that can be used in response to a wide range of incident response activities.
- Combinations of runbooks and playbooks can be used to document different security processes and can provide users with approved procedures for orchestrating even the most complex security workflows. 

**EXAM TIPS: SOAR systems are extremely valuable when it comes to incident mitigation of severe threats because they can automate data gathering and initiate threat response.**

### Runbooks
**Def: A runbook consists of a series of action-based conditional steps to perform specific actions associated with security automation.**
- These actions might involve data harvesting and enrichment, threat containment, alerts and notifications, and other other automatable elements of a security operations process. 
- Runbooks are typically focused on the systems and services and how they are actively managed.

### Playbooks
**Def: A playbook is a set of approved steps and actions required to successfully respond to a specific incident or threat.**
- Playbooks are commonly instantiated as itemized checklists, with all pertinent data prefilled in --systems, team members, actions, and so on. 

**EXAM TIP: A runbook typically focuses on technical aspects of computer systems or networks. A playbook is more comprehensive and has more of a people/general business focus.**

# Questions
1. D
2. B
3. B
4. D
5. A 
6. D
7. B (Because the item is an object, quarantine applies. Other methods of isolation belong to networks and systems.)
8. D (Application block listing by version number will prevent specific versions from being executed on selected machines.)
9. A
10. C
