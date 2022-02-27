# Chapter 6 
# Vulnerabilities

Enterprise systems are composed of many different parts, with multiple technologies and numerous elements that can be less than perfect. 


## Cloud-based vs. On-premises Vulnerabilities
Cloud computing can best be described as computing on someone else's com
puter. 

**Def: On-premise vulnerabilities means the enterprise has unfettered access to the infrastructure elements, making the discovery and remediation of vulnerabilities a problem defined by scope and resources.**

**Def: Cloud-based vulnerabilities mean the economies of scale and standardized environments give cloud providers an advantage in the scope and resource side of the equation. What is lacking in vulnerability management from the enterprise point of view is visibility into the infrastructure element itself.**

No matter where data is stored (cloud or on-premise), there will always be vulnerabilities

### Zero Day
**Def: Vulnerabilities that are newly discovered and not yet addressed by a patch.**

These are dangerous because they are unkown and unpredicatable in regards to what damage they can inflict

One way to help mitigate against zero days is using compensating controls

## Weak Configurations
Most systems have significant configuration options that administrators can adjust to enable or disable functionality based on usage. 

When a system suffers from misconfiguration or **weak configuration**, it may not achieve all of the desired performance or security objectives.

Examples:
- Configuring a database server to build a complete replica of all actions would bog down the system
- Support for legacy protocols can lead to more vulnerabilites
- Misconfigurations can result from omissions as well

### Open Permissions
**Def: permissions is the term used to describe the range of activities permitted on an object by an actor in a system.**

Properly configured permissions is one of the best defenses that can be employed by an enterpise

When permissions are not properly set, the condition of **open permissions** exists.

### Unsecure Root Accounts
These are like leaving master keys to the enterprise outside on the curb.

Root accounts have access to everything and the ability to do virtually any activity on a network. These accounts should all be monitored.

A way to protect high-value accounts is through access control vaults, where credentials are checked out before use.

### Errors
**Def: The condition where something has gone wrong**

Its important to have strong error handling controls. Unhandled errors will be handled less correctly the higher it goes up in a system.

Errors should be trapped by the program and appropriate log files generated

### Weak Ecryptionn
Never develop your own crpytographic algorithm.

Cryptographic algorithmns endure years of tests and take long periods of time until they are formally recognized and implemented

Weak algorithmns are also an issue since they tend to be less secure and easier to crack

### Unsecure Protocols
Improperly secured communication protocols and services have a large potential to become a vulnerablity. 

It can also be a risk since it increases the risk of unauthorized access to the enterprise Network infastructure

### Default Settings
Don't forget about the inate system settings in a laptop or pohne

### Open Ports and Servces 
For service to response to a request, its port must be open for communication.

Having open ports is like having open doors in a building. Having excess open services only leads to pathways into your systems that must be protected. 

Disabling unnecessary services, closing ports, and using firewalls to prevent communications except on approved channels creates a barrier to entry by unauthorized users. 

---
## Third-Party Risks

The enterprise computing environment is full of third parties, and their risks become enterpise risks. Common **third-party risks** that are often overlooked are issues of vendor management, system integration, and lack of vendor support.

This is all related in the fact that when you choose a vendor as part of your enterprise solution, it made sense but over time, enterprises change, vendors change etc

Supply chains come with risk from elements such as outsourced code dvelopment, maintenance of systems, and data storage on another's computer

It is important to have an inventory of what the software is by version, and where it is used. 

### Vendor Management 
A vendor is a supplier or firm that has a business relationship with the enterprise. 

**Def: the challenge of vendor management is one of determining one's own needs and then finding the vendors that offer the best value proposition against those needs**

### System Integration
**Def: The connecting of these components, each representing a portion of the system into a complete functioning unit.**

Vulnerabilities can exist if pieces of the system have gaps or if capabilities do not manifest given the desired specification.


### Lack of Vendor Suppot
This can be an issue at several different levels. The most obvious scenario is when the original manufacturer of the item, be it hardware or software, no longer offers support.

When an item reaches its end of life (EOL) from the original manufacturer's standpoint, this signifies the finality of its life under almost all circumstances

Note: EOL and EOSL are different things, EOSL is when the manufacturer quits selling an item. In most cases the manfuacturer no longer provides maintenance services or updates. EOL is just the end of its 'useful life'

### Supply Chain 
**Def: a risk that is caused by the vulnerabilities that lie within the supply chain.**

A supply chain attack typically occurs at the weakest security link in the supply chain, and this is common during the manufacturing process or even in the product delivery phase.

#### Outsourced Code Development
Code is the glue that holds the enterprise together

If code is outsourced the visibility and control over the risks associated with it become harder to manage with every step away from the source. 

It is important to have conditions in contracts requiring appropriate development measures be in place for third-party code, including the rights to inspect and verify security functionality. 

Ensuring third-party-developers have appropriately secure coding practices and having their code reviewed by independent testers and placed in escrow for safekeeping are considered best practices

#### Data Storage
Data storage is distributed across the enterprise in different capacities and configurations.

It would not be wise to store all data in one place but rather throughout multiple enclaves with differing requirements and criticalities.

Always have a standardized data storage policy and checklist for good practice

## Improper or Weak Patch Management 
Once a patch is released hackers can reverse engineer it and learn where to attack.

Having an **improper or weak patch management system** is an open invitation to having vulnerabilities exploited.

To minimize the risks associated with applying patches to production systems, it is recommended that the enterprise change control process be used. It is important to have defined periods of time when patches must be installed as well as an automated means of determining what patches are needed, where they are needed and the status of the current patch level.

### Firmware
**Def: Another form of software with one noted distinction: it is stored in hardware to be present when the system boots up**

Treat it just like software (it can get bugs, vulnerablities, patches)

Updates and patching are used to ensure software and firmware are up to date and secure. 

### Operating System (OS)
Today, major OS can patch themselves, and with very little automation, the tracking and mangement of patches is easy. There are only a couple of steps to get this right.

First, have a patch management policy, and make it patch everything and track all patches. 
Second, follow up on that policy. 

### Applications
**Def: The programs that comprise the funcational aspect of the enterprise.**

Applications are tools that can handle data and add value to the system. Like all software they require updating and patching to fix vulnerabilities and bugs

Example of applications: web servers, database servers, desktop apps like Microsoft Office

The hard part of application patching is tracking all the applications used even small seemingly meaningless programs that are installed on desktops

Part of a security professional's responsibilities is to keep up with current Common Vulnerabilities and Exposures (CVEs) and update or patch systems to keep the enterprise environment secure. This applies to firmware, operating stesms, apploications, virtual machines, and devices. 

---
## Legacy Platforms
**Def: Systems that are no longer being marketed or supported.**

They are also considered old, which in IT terms could mean just a few years

Legacy systems are an interesting vulnerability because since they are no longer supported, new vulnerabilities can only be dealt with using componsating controls.

## Impacts
**Def: The resulting effects of a risk that is realized. They are the items that an organization is trying to avoid**

These can be categoized in the sections that follow

### Data Loss
**Def: When an organization actually loses information. 

Files are overwritten, deleted or even misplaced. 

Ransomware is the most dangerous form of data loss since it is driven by outside forces and its very nature is to make the data unavailable to the enterprise until the ransom is paid

### Data Breaches
**Def: The Release of data to unauthorized parties.**

Attackers that break into a system are constantly looking to steal Personally identifiable information (PII)

Strong access controls, encryption of data at rest, and data loss prevention (DLP) elements can lessen the impact

### Data Exfiltration
**Def: The exporting of stolen data from an enterprise.**

Data can be copied and then stolen without affecting the original data

### Identity Theft
**Def: A crime where someone uses information on another party to impersonate them.**

This is a secondary impact once data is exfiltrated.

The loss of data can come from commerical systems and even home systems, and the results are the same: people can lose money, property, and time cleaning up an identity theft claim

### Financial
At the end of the day, risk is measured in financial terms and the impact from vulnerabilities can be expressed in financial terms as well. 

Here is a list of items that can contribute to the financial costs of a cyber attack:
- Costs associated with investigating and fixing enterprise systems
- Lost orders/revenue due to system downtime
- Fines for regulatory noncomplicane on privacy laws
- Attorney fees from lawsuits
- Ransom payments made for ransomware
- Losses due to stolen intellectural property
- Share price decline and market capitalization loss

An average cybersecurity loss can cost a small to medium-sized business $400,000. For many businesses, that number is large enough to destroy them.

### Reputation
This comes into two main forms: loss of customer confidence and in cases where skilled workforce is involved, a competitive field loss of key employees. 

Companies that have highly skilled workforce members who are in short supply also have to be concerned with their reputation in the eyes of their employees. 

### Availability Loss
When the impact of a cyber attack affects infrastructure elements, either by system damage, data loss, or loss of systems during recovery efforts, the effect is one that results in the loss of system capability. 

The loss of availability on the part of a system will have an impact on the 

# Questions
1. A B D
2. A D
3. A  D (firmware has fixed configuration)
4. A B C D
5. A  C
6. B
7. A B C 
8. D
9. C
10. C 






