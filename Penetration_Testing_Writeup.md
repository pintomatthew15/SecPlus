# Chapter 8 
# Penetration Testing

Penetration testing is a structured form of testing defenses using the methodologies employed by attackers. These exercises can be performed in a variety of different ways, which will be explored in the sections that follow. 



## Penetration Testing
**Def: Penetration testing simulates an attack from a malicious outsider--probing your network and systems for a way in (often any way in).**

These are often the most aggressive forms of security testing and can take on many forms depending on what is considered "in" or "out" of scope. 

The goal of a pen test is always the same: to determine if an attacker can bypass your security and access your systems.

Unlike a vulnerability assessment, which typically just catalogs vulnerabilities, a pen test attempts to exploit vulnerabilities to see how much access they allow.

They are useful in the following ways:
- They can show relationships between a series of "low-risk" items that can be sequentially exploited to gain access (making them a "high-risk" item in the aggregate). 
- They can be used to test the training of employees, the effectiveness of your security measures, and the ability of your staff to detect and respond to potential attackers
- They can often identify and test vulnerabilities that are difficult or even impossible to detect with traditional scanning tools.

**Exam Tip: Penetration tests are focused efforts to determine the effectiveness of the security controls used to protect a system.**

An effective penetration test offers several critical elements. First, it focuses on the most commonly employed threat vectors seen in the current threat environment. Using zero-day threats that no one else has does not help a firm understand its security defenses against the existing threat environment. 

Second, an effective penetration test focuses on real-world attacker objectives, such as getting to and stealing intellectual property (IP). Just bypassing defenses, but not obtaining the attacker's objectives, again, does not provide a full exercise of security capabilities. 

There are numerous penetration test methodologies, the most recognized is the Open Source Open Web Application Security Testing Methodology Manual (OSSTMM) method. For web applications, the Open Web Application Security Project (OWASP) is the most recognized standard in the industry. 

The importantance of the process model is to have a plan that ll team members can use to understand where they are in the process and the relationships between major attacks.

### Known Environment
**Def: Known environment (white box) testing is almost the polar opposite of unknown enviroment (black box) testing. Sometimes called clear box testing, white box techniques test the internal structures and processing within an application for bugs, vulnerabilites, and so on.**

A white box tester will have detailed knowledge of the application they are examining

Known environment testing is often used to test paths within an application, data flows, decision trees, and so on. 

Basically there is knowledge about the system that the typical visitor or attacker is not initally privy to. 

### Unknown Environment
**Def: Unknown environment (black box) testing, is a software-testing technique that consists of finding implementation bugs using malformed/semi-malformed data injection in an automated fashion.**

It tests the functionality of the software, usually from an external or user perspective. Testers usually have no knowledge of the internal workings of the software they are testing. 

Unknown environment software testing techniques are especially useful for examining any web-based applications, which are typically subjected to a barrage of valid, invalid, malformed, and malicious input from the moment they are exposed to public traffic

Unkown environment testing can also be applied to networks or systems. Pen tests and vulnerability assessments are often performed from a purely external perspective, where the testers have no inside knowledge of the network or systems they are examining.

### Partially Known Environment
**Def: Also called grey box testing, it is mixing in segments of the known and unknown environment.**

Testers have some knowledge of the software, network, or systems they are testing.

**Exam Tip: The key difference between known, unknown, and partially known is the perspective and knowledge of the tester.**

### Rules of Engagement
ROEs Associated with a penetration test are critical for several reasons.

First, the activities associated with a penetration test are illegal if not authorized, and the ROEs specify the legal authority that the penetration testers associated with the test so that it is actually exercising the functions desired by the customer.

Typical rules of engagement will include a boundary of what is in scope and what is not. 

### Lateral Movement
**Def: Refers to to the process used by attackers to move deeper into a network to get to the target data.**

Inital entry into a system is via a user account that does not have access to the desired material, nor does the account have the appropriate levels of permission. 

Eventually the account escalates priviledge until it obtains proper credentials.

The process of moving across a network is refered to as laterl movement or network lateral movement

### Privilege Escalation
**Def: The process of gaining increased privileges fro an account.**

This can happen in a variety of ways either legitimately or through bugs/vulnerabilities

Gaining root or admin access is always a goal for an attacker, because this gives them additional powers on a system that makes their job easier and opens up pathways that are otherwise closed to them.

Some paths are easy to block, blocking local administrator accounts, limiting the number of users with native administrative ability are important. Monitor admin activites is another method

There are two types of priviledge escalation: horizontal and vertical. 
- Horizontal: the attacker expands their priviledges by taking over another account and misusing the legitimate privileges granted to the other user. Typically done with lateral movement

- Vertical: the attacker attempts to gain more permissions or access with an existing account they have already compromised. An attacker using a regular user-level account on a network can  attempt to gain admin permsissions via exploiting vulnerabilities in processes or services running with admin privilege.

**Vertical privilege escaltion requires more sophistication and is the main technique employed by advanced persistent threats (APTs).**

### Persistence
**Def: The ability to exist beyond a machine reboot or after disconnection.**

The term advanced persistent threat (APT) refers to a methodology that is focused first and foremost about maintaining persistence. 

**Exam tip: Lateral movement, privilege escalation, and persistence are common tools in the toolbox of attackers and penetration testers. They are frequently used together, but each has its unique characteristics.**

### Cleanup
Attacking systems can leave a large amount of evidence laying around. 

**Cleanup**, or covering one's tracks, is an essential step in a professional's toolkit. 

Clearing logs, blocking remote logging, messing with system history, and using reverse shells and Internet Control Message Protocol (ICMP) tunnels to avoid detection and logging are some of the methods employed. 

The use of rootkits or trojans to modify the OS so that specific account-based activities are not logged is one of the methods used by APT attacks.

### Bug Bounty
**Def: Bug bounty programs are mechanisms where companies pay hackers for revealing the details of vulnerabilites that they discover, providing companies an opportunity to correct the issues.**

Most bug bounties pay some form of cash reward, with several major companies like Microsoft, Apple, and Google paying up to six-digit rewards for very critical vulnerabilities.

One important element to understand, is that for bug hunting to be legal, the firm must have an established bug bounty program, and hunting activity must be in accordance with that program.

### Pivoting
**Def: A technique similar to lateral movement. In pivoting, one moves to a new location in a network and begins the attack process over again, performing scans to see machines that were not visible from the ouside.**

Lateral movement is moving across networks where pivoting is one of the key methods of learning where to move next. 

---
## Passive and Active Reconnaissance

Reconaissance can be one of two types: passive or active

**Def: Passive recon is performed using methods to gain information about targeted computers and networks without actively engaging with the target systems and thus avoiding detection.**

- Example: Using DNS and IP registration records are techniques the attacker can use to provide a lot of information without ever touching the targets, thus completely avoiding detection

**Def: In active recon, the attacker engages with the target system, typically conducting a port scan to find any open ports.**

Active recon involves using packets that can be traced; it involves engaging services that can be logged

In general: passive recon has limits on how much an attacker can learn, but its completely stealthy. Active recon is much more informative, but it tells the machines they are being "attacked"

### Drones
Drones are unmanned aerial platforms capable of carrying cameras, mobile devices, and other items across normal boundaries such as walls, fences, and checkpoints.

### War Flying
**Def: Using a drone to fly over a facility and capture wireless network traffic.**


### War Driving
Same as war flying except using a car


### Footprinting 
**Def: The first step in gaining active information on a network.**

Using footprinting, a pen tester can gather information about computer systems and the entities they belong to, and in some cases user information as well.

The primary method of gathering this information is via network sniffing and the use of scanning software 

This is the first step in gaining active information on a network during the recon process


### OSINT
Open Source Intelligence (OSINT) is the technique of using publicly available information sources to gather information on a system. 

OSINT is not a single method but rather an entire set of both qualitative and quantitative methods that can be used to collect useful information. 

OSINT describes using public information sources to gain information about a target and find methods that will improve the odds of a sucessful campaign

---
## Exercise Types
Security exercise types include those focused on offense, defense, or a mix of offense and defense

Different colors are used to denote the different teams that participate in an exercise. 

### Red Team
Red teams are composed of members who are focused on offense. Red team members use their skills to mimic a real-world threat environment and provide a test of a firm's defensive capabilities.

They are frequently third party contractors, as their skill set is specialized and the required skill level is high

### Blue Team
Blue teams are defense teams and, as such, typically an in-house operation, unless the defensive efforts are outsourced. 

Blue team members come from the IT and security operations departments, and they typically perform two functions: 

1. Establish defenses, configure defensive elements such as firewalls, and security applicances, managing permissions, and logging

2. Monitoring and incident response functions. They are on lookout for attacks and manage the system's responses to any unauthorized behaviors observed.

### White Team
The team of judges when an exercise involves scoring and/or a competition.

They exist to make sure exercise stays on track and employs the desired elements of a system

### Purple Team
Composed of both red and blue team members. These team members work together to establish and test defenses. 


# Questions
1. A
2. B
3. D (rescanning, always means pivoting)
4. B
5. C
6. D (OSINT makes unknown partially known)
7. A
8. A
9. D
10. B
