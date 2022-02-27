# Chapter 5 
# Threat Actors, Vectors & Intelligence Sources
**Def: a threat actor is the source of the threat on the system**

**Def: Vectors are the methods that threat actors use to attack a vulnerability in a system in order to achieve their objective.**

**Def: Threat intelligence is knwoledge based on evidence that allows you to prevent or mitigate cyber threats.**

---
## Actors and Threats

### Unstructured Threats
**Def: Attacks that are performed typically by individuals or small groups.

Attacks at this level generally are conducted over short periods of time (lasting at most a few months)

They do not involve large numbers of individuals, have little financial backing, and are accomplished by insiders or outsiders who do not seek collusion with insiders. 

Attackers can be broken into these three categories with the following percentages
- Script Kiddies (86-91%)
- Script Writers (8-12%)
- Elite (1-2%)

### Advanced Persistent Threats (APTs)
**Def: A threat characterized by using toolkits to achieve a presence on a target netowrk and then, instead of moving to steal information, focusing on the long game by maintaining a persistant presence on the target network.**

Goal is longterm persistance on the network and avoiding detection

Example: Operation Night Dragon (2006)
- intellectual property attackon against oil, gas, and petrochemical companies in the US
- Attackers from China used a set of global servers and raided energy companies for proprietary and highly confidential information such as bidding data for leases

### Insider Threats

Insiders are far more dangerous in many respects to outside intruders due to their access and knowledge necessary to cause immediate danger to the organization.

One way to protect against a skilled hacker is to prevent any individual from performing crticial duties alone.

### State Actors

Often tend to be highly techncial individuals who are not only capable of writing their owns scripts but discovering new vulnerabilities as well. 

They are typically employed by a cybersecurity firm or governments

They also often carry out APT attacks and are part of groups capable of conducting information warfare

### Hacktivists

Typically found in the script writers group and account for about 8-12% of all hackers

**Def: Hackers who work together to forward a specific cause**

### Script Kiddies

**Def: Individuals who do not have the technical expertise to develop scripts or discover new vulnerabilities in software, but who have just enough understanding of computer systems to be able to download and run scripts that others have developed.**

Generally not interested in attacking specific targets but instead simply want to find an organization that may not have patched a newly discovered vulnerability for which the script kiddie has located a script to exploit.

### Criminal Syndicates

Organized crime has holds in the cyber domain

The same things that happen in the physical world happen in the cyber world, example: fraud, extortion, theft, etc

These groups tend to have more organization and money to spend  than the average hacker. 

Attacks from criminal organizations typically fall into the structured threat category

---
### Hackers 
**Def: Someone who spent time trying to figure out how somethingworked so that they could control it in ways it wasn't designed. Three main groups: authorized, unauthorized, sem-authorized.** 

#### Authorized
These individuals use their hacking skills for good and have the common name of "white hat" hackers. Same as malicious hackers but it at least has the permission to use their tools to help groups improve their security.

#### Unauthorized
Black hat hackers are the opposite of white hats. These individuals violate laws and cause risks to systems. They may have different motivations but what they are ultimately performing is illegal.

#### Semi-authorized
Gray hat hackers live with one foot in each world. This group of semi-authorized hackers works in both the legally sanctioned world of security and the illegal realm of criminal activity. 


### Shadow IT
**Def: parts of an organization that perform their own IT functions. These groups rise up out of a desire to "get things done" when central IT does not respond in what the unit considers to be a reasonable time frame.**

Often times leads to increased risk since it is generally less functioning compared to central IT. 

### Competitors
Competitors can also be a threat to a business on the field of battle: sales, markdowns, rivial products -- it is a battle for customers every day. 

Competitors hae been known to attack other firms' IT processes. The methods vary from simple false product reviews to more serious elements such as the actual hacking of a system. 

---
## Attributes of Actors
Actors can be divided into groups based on abilities. They can be differentiated by location, level of sophistication, level of resources, and intent

### Internal/External
Internal threat actors have one signficant advantage over external actors: they have access to the system.

External actors still need to go through establishing access to the target system

### Level of Sophistication/Capability
Within a group of threat actors, the skill level of the individual members of the group may well be mixed, with a few highly skilled individuals acting to move larger numbers of less skilled participants

More sophisticated attacks typically use more minimal methods of attack

### Resource/Funding
Criminal organizations and nation states have larger budgets, bigger teams, and the ability to pursue campaigns for longer periods of time.

Cyber operations require a continous support in regards to time, resources etc so only larger organizations will be able to sustain them

### Intent/Motivation
The intent or motivation behind an attack will vary with the skill level of the actor. For script kiddies, its testing out a technique, for more skilled threat actors its making a message or statement. For the top APTs there are three goals:
1. Drive to maintain continual access
2. Drive to remain undetected
3. Stealing something of value on the network
---
## Vectors
Threats are perpetuated by threat actors, and they use various vectors to exploit vulnerabilities in a system, giving them unauthorized access. 

**Def: Vectors are the term for the various methods that an attacker can use to get in --whether it is direct access via wireless or email channels, social media, supply chain,  an external data source, etc**

### Direct Access
The attacker has direct access to the system. 

This can be insdier attack or somehow outsiders are able to interact directly with the system

Direct access is why we use the principle of least privilege, only giving the necessary permissions and blocking all others

### Wireless
The attacker no longer needs to have direct physical access to the network, a wireless signal can bring it to the attacker instead.

### E-mail
E-mail is one of the preferred vectors for social engineering attacks. Sending an e-mail that includes links or attachments is a manner of interacting with a user

### Supply Chain
**Def: Using a company's supply chain as an unwitting agent in the attack.**

An attacker finds a means by which they can get their attack code into the supply chain for a product or an update. 

Microsoft has excelled in preventing this by having numerous security checks, making it virtually impossible to poison company updates 

Example: Solar Winds Attack (2020-2021)

- Solar Winds Orion was discoved to have been breached by a nation-state actor
- Breach was in the product chain and went unnoticed for 9 months

### Social Media
Social media can be a vector for social engineering attacks because it connects an attacker directly to the user, and many of the security checks seen with corporate e-mail and other communication channels are not present.

### Removable Media
This type of storage is small, ubiquitous, and takes no skill to attach to a PC. 

An attacker can take a USB storage and put the attacking module on it so it can be executed.

### Cloud
Do not view cloud as simply being connected to the internet. Make sure cloud includes antiviruse protections

---
## Threat Intelligence Sources
**Def: Threat intelligence is the gathering of information from a variety of sources, including nonpublic sources, to allow an entity to properly focus its defenses against the most likely threat actors. **

Threat Intelligence Sources are the palces where one can get this information. There are many types

### Open Source Intelligence (OSINT)
**Def: Intelligence data collected from public sources.** Below is a list of several sources and basic information about how their intelligence is vetted.

- #### Department of Homeland Security (DHS)
Automated Indicator Sharing is a collection of information such as malicious e-mail addresses, IP addresses, and other bad material reported by private companies to the DHS via its Automated Indicator Sharing (AIS) portal. 

- #### Federal Bureau of Investigation (FBI)
InfraGard Portal is a vetted access collection of security information reported to the FBI. It tends to focus on critical infrastructure and ca nhave significant time lags, as the FBI holds information involved in investigations.

- #### SANS
Internet Storm Center (ISC) is a distributed sensor network that processes over 20 million intrusion detection log entries per day and generates alerts concerning security threats.

- #### VirusTotal
Now operated by Google, VirusTotal uses feeds from a myriad of antivirus scanners to maintain a signature database of malware and related information. 

- #### Cisco
The Talos Intelligence team produces a feed of inofrmation for Cisco customers (a free version is also available). The breadth of Cisco's collection and the depth of its research team makes this an important feed for new and emerging dangers.

### Closed/Proprietary
Its important to consider the number and diversity of data feeds when considering proprietary or closed databases. 

### Vulnerability Databases
Vulnerabilities are the weaknesses in software that allow an attacker a means of entry. 

There are so many vulnerabilities it has become more of a data problem. These need to be kept in databases and logged

The most popular vulnerability database is the National Vulnerability Database (NVD) hosted at nvd.nist.gov

One major exception is the Metasploit vulnerability database

### Public/Private Information Sharing Centers
Information Sharing & Analysis Organizations (ISAO): include any organization whether an industry sector or geographic region, that is sharing cyber-related information for the purpose of enhancing their members' cybersecurity posture. 

Information Sharing & Analysis Centers (ISAC): Special category of ISAO consisting of a privately run, but government approved, industry-based cyber security.

InfraGard, run by the FBI and is a US govenrment program that assits in information sharing

### Dark Web
**Def: a subset of the worldwide content on the Internet that has its access restricted via specific obfuscation methods.**

Dark Web sites are sites that require Tor- a free, open source software that enables anonymous communication.

Dark web sites end with .onion, as opposed to .com, .net, and so on.

The **deep web** is part of the internet that isnot indexed by search engines. One example of the deep web is material that requires you to log in to an account before it is exposed. The deep web is readily accessible to a browser but only with specfic information

### Indicators of Compromise 
**Def: indications that a system has been compromised by unauthorized activity.**

When a threat actor makes changes to a system there are forensic artifacts that are left behind. 

IoCs act as breadcrumbs for investigators, providing litttle clues that can help identify the presence of an attack on a system.

Tools such as YARA can take a set of signatures (also called IoCs) and then scan a system for them, determining whether or not a specific threshold is met indicating a particular infection. 

Set of IoCs that firms should monitor include:
- Unusual outbound network traffic
- Anomalies in privileged user account activity
- Geographical irreqularities in entwork traffic
- Account login red flags
- Increases in database read volumes
- HTML response sizes
- Large numbers of requests for the same file
- Mismatched port-application traffic, including encrpyted traffic on plain ports 
- Suspicious registry or system file changes 
- Unusual DNS requests
- Unexpected patching of systems
- Mobile device profile changes
- Bundles of data in the wrong place
- Web traffic with nonhuman behavior
- Signs of DDoS activity, even if temporary

### Automated Indicator Sharing (AIS)
Created by the U.S. Department of Homeland Security

**Def: AIS is an automated, bidirectional cyber-threat indicator method that's used for reporting.**

Key element of AIS is that it operates at machine speed, permitting near-real-time reporting and reponse

The AIS system uses the Structured Threat Infromation Expression (STIX) and Trusted Automated Exchange of Intelligence Information (TAXII) specifications to enable machine-to-machine communication at machine speed.

### Structured Threat Information Expression (STIX)/ Trusted Automated Exchange of Intelligence Information (TAXII)
To communicate cyber-threat infromation at machine speed, the US DHS inititated the STIX/TAXII (Structured Threat Infromation Expression/ Trusted Automated Exchange of Intelligence Information) program in 2012. 

Now governed by the international consensus body OASIS, both STIX and TAXII provide a set of community-driven standards that enable the automated exchange of information associted with cyber threats, network defense, and threat analysis. 

**BIG TAKEAWAY: STIX represents the cyber-threat information (threat intelligence) while TAXII defines how the information is exchanged. You can think of TAXII as "how you get there."**


### Predictive Analysis
**Def: the use of threat intelligence information to anticipate the next move of a threat.**

This is done by curating large quantities of data from multiple sources and sifting through this sea of data to find the key pieces of information that are necessary to put together a hypothesis about what threats are potentially up to and determine how to find them in your enterpise. 


### Threat Maps
**Def: geographical representations of attacks showing where packets are coming from and going to.**

Attribution is difficult and just because an attack comes from an IP in a certain city does not mean the attack actually originated from there. 

### File/Code Repositories
**Def: act as locations where people can work together on projects and dvelop software.**

They offer a source of information to adversaries about how software is built, giving them a chance to to examine the source code for volunerabilities. 

You can also use the same sources to examine the capabilities of some of the tools your adversaries will use against you. 

## Research Sources
There is no one perfect source, each has goods and bads

### Vendor Websites
They have nice looking websites but its important to figure out their sources.

They will try to make you partner with them, their priority is marketing


### Vulnerability Feeds
It is important to vet your feeds for a variety of issues

Multiple feeds are almost mandatory for coverage

### Conferences
Researchers sometimes do not have time to wait for their papers to get turned into journal articles so they publish the paper themselves at conferences. This has two benefits

First: The timelines for conference submissions are much shorter than journals
Second: The presentation of the material at the conference is a good way to get multiple points of view in the ofrm of feedback in a quicker fashion.

Three major security conferences are held each year:
1. Black Hat USA 
2. RSA conference in San Fran
3. DEF CON in Las Vegas

### Academic Journals
Academic papers are reputable sources however they have two issues

1. Publishing a paper in an academic journal can take from a year to 18 months at the minimum
2. Academics are seldom experts in the application of the technologies they research. They look at things as theoretical problems and ignore many of the applied aspects.

### Requests for Comment (RFCs)
**Def: Sets of standards used to define how the Internet and the protocols involved in the World Wide Web are established and managed.**

They are free and openly available, and unlike some constantly evolving items, they are fixed in time when written.  Changes to these documents are formal and recored

### Local Industry Groups
They are a good source of practical information concerning threats, threat actors, and what can be done to defend networks.

They are a solid networking source of information that enables one to get answers to questions that have been vetted by others in similar positions. 

### Social Media
Like any other vet sources, its a good place to find like minded people and communicate

### Threat Feeds
Very similar to vulnerability feeds, make sure you have many of them and they are constantly changing

### Adversary Tactics, Techniques, and Procedures (TTPs)
The acronym TTP is used to describe how threat agents organize and orchestrate their efforts. 

**Def: TTPs are the patterns used by adversaries that are a key element of a threat intelligence program**

# Questions
1.D
2.C
3.B
4.D
5.A
6.B  (Review indicator of compromise)
7.D
8.B
9A
10.B (Vulnerability is different than a threat)
