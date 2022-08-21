# Chapter 7
# Security Assessments

Assessment is the examination of something against a standard, to see how it stacks up. In security, the primary standard should be your set of security policies-- and they should align with any external requirements. 

---
## Threat Hunting 
**Def: The practice of proactively searching for cyber threats that are inside a network, yet remain undetected.**

Cyber threat hunting use tools, techniques, and procedures (TTPs) to uncover unauthorized actors in your network that have not been detected by your defenses. 

Threat hunting uses tools and techniques to specifically detect users who permeate through inital network defenses. These tools can be indicators of attack (IOAs) and indicators of compromise (IOCs). 

IOAs: comprise a series of actions an attacker must accomplish to perform an attack
- This could include creating an account and connecting to a command-and-control server 

### Intelligence Fusion
Intelligence Fusion enables a defender to identify and contextualize the threats they face in the environment, using the information from threat intelligence in the Diamond Model of Intrusion Analysis

**Def: a process involving collecting and analyzing threat feeds from both internal and external sources on a large scale.**

### Threat Feeds
**Def: Sources of information concerning adversaries**

They can come from internal or external sources. 

By leveraging threat data from your own network based on incident response data, it is possible to find other locations of the same threat in your environment. 

### Advisories and Bulletins
**Def: Published sets of information from partners, such as security vendors, industry groups, the government, information-sharing groups, and other sources of "trusted" information.**

These are external sources of threat feeds and need to be processed by security personnel to determine to determine their applicability and how ot use them to improve defenses for the enterprise. 

### Maneuver 
**Def: The ability to move within a network, a tactic commonly used by advanced adversaries as they move toward their objectives.**

Threat hunting can counter an attacker maneuvering via a couple mechanisms. 
1. The threat hunter can watch for traffic at chokepoints
2. The threat hunter can analyze the company's own network infrastructure, through the eyes of an attacker, and provide insight into how the network can be connected to provide better defenses against lateral movement, both in terms of connections and logging.

Maneuvering is also a defensive tactic used by security professionals to disrupt or prevent an attacker from mvoing laterally as part of the attack chain

---

## Vulnerability Scans
**Def: the process of examining services on computer systems for known vulnerabilities in software.**

The Common Vulnerabilities and Exposures database can be used as a repository; it has recorded over 145,000 specific vulnerabilities. 


### False Positives & False  Negatives
Any system that uses a measurement of some attribute to detect some other condition can be subject to errors.

When a measurement is used as part of a decision process, external factors can introduce errors. In turn, these errors can influence a measurement to a condition that creates an error in the final number. When a measurment is used in a decision process, the possibility of errors and their influence must be part of the decision process. 

Example: Cooking a steak, we can't just cut into it since the customer does that. We can however, use tools

**Know the difference**
False positive: occurs when expected or normal behavior is wrongly identified as malicious. 

False negative: occurs when you test something and it comes back negative when it was in fact positive.

When an intrusion detection system (IDS) does not generate an alert from a malware attack, this is a false negative

### Log Reviews
A properly configured log system can provide tremendous insight into what has happened on a computer system. The key is in proper configuration so that youcapture the events you want without adding extraneous data

**Log reviews can provide information as to security incidents, policy violations, and other abnormal conditions that require further analysis**

### Credentialed vs. Non-Credentialed
Credential scans are more involved, requiring credentials and extra steps to log in to a system, whereas non-credentialed scans be done more quickly across multiple machines using automation. Credentialed scans can reveal additional information over non-credentialed scans. 

### Intrusive vs. Non-Intrusive
A non-intrusive scan is typically a simple scan of open ports and services, where an intrusive scan attempts to leverage potential vulnerabilities through an exploit to demonstrate the vulnerabilities. 

This intrusioncan result in system crashes and is therefore referred to as intrusive. 

### Application
**Def: Applications are the software programs that perform data processing on the information in a system.**

Applications are the middle element between data and users so they are a primary target for attackers

### Web Application
**Def: Web applications are just applications that are accessible across the web.**

This brings convenience and greater potential exposure to unauthorized activity.

From a vulnerability scan perspective, a web application is like an invitation to explore how well it is secured.

### Network
**Def: The network is the element that connects all the computing systems together, carrying data between the systems and users.**

### Common Vulnerabilities and Exposures (CVE)/ Common Vulnerability Scoring System (CVS)

**The Common Vulnerabilites and Exposures (CVE)** enumeration is a list of known vulnerabilities in software systems. 

- Each vulnerability in the list has an identification number, description, and reference

- This list is the basis for most vulnerability scanner systems, as the scanners determine the software version and look up known or reported vulnerabilities. 

**The Common Vulnerability Scoring System (CVSS)** is a scoring system to determine how risky a vulnerability can be to a system

- The CVSS score ranges from 0 to 10. The higher the score, the more severe the vulnerablility 

| Risk Rating     | CVSS Score | 
| :---        |    :----:   |         
| Low     | 0.1-3.9     | 
| Medium   | 4.0-6.9       | 
| High   | 7.0-8.9    | 
| Critical  | 9.0-10     | 


### Configuration Review
System configurations play a significant role in system security. Misconfiguration leaves a system in a more vulnerable state, sometimes even causing security controls to be bypassed completely

**Configuration reviews** are important enough that they should be automated and performed on a regular basis 

There are protocols and standards for measuring and validating configurations. 
- The Common Enumeration (CCE)
- Common Platform Enumeration (CPE)

Both are part of the National Vulnerability Database (NVD) and maintained by NIST

---
## Syslog/Security Information and Event Management (SIEM)

Syslog stands for System Logging Protocol and is a standard protocol used in Linux systems to send system log or event messages to a specific server, called a syslog server. 

The value of in syslog is the separation of a system from error reports, allowing both for the security functions of logging to be separate from the system being monitored and for the aggregation of multiple log streams on a common server. 

A syslog server listens on either UDP port 514 or TCP port 6514. 

Syslog is for more than just errors; it is the standard for remote logging on Linux systems. Ubuntu stores global activity and startup messages in /var/log/syslog. Applications can use it as well

The information in syslog server is just tables of raw data. To make this information easier to use, a system called **security information and event management (SIEM)** is employed to collect, aggregate, and apply pattern matching to the volumes of data. 

**EXAM TIP: Remember that syslog can be used for log aggregation on network devices and Linux operating systems. A syslog server listens for and logs messages from syslog clients. SIEM systems collect, aggregate, and apply pattern matching to the volumes of data to produce human-readbale infromation.**

### Review Reports
The primary means of providing output from a SIEM is either an alert or a report

These reports can then be reviewed to determine whether an incident exists or is a false alarm

### Packet Capture
Packet captures have been a staple of network engineers for as long as networks have existed. 

Diagnosing and understanding network communication problems is easier when one can observe how packets flow through a network

It is important to ensure you have continous packet capturing so that security people are able to go back and review previous network traffic 

Using a SIEM, coupled with smart appliances like next-generation firewalls, when a rule is fied, the network capture appliance can automatically collect and ship off a predetermined amount of traffic for later analysis. 

### Data Inputs
**The data inputs to a SIEM are as varied as the systems they are used to protect**

As a SIEM matures, more data sources are identified and included, and ones that are not used are removed. 

A SIEM is tuned by the security personnel to answer the questions relative to their environment and their risks.

### User Behavior Analysis
SIEMS are systems built to apply rules to sets of data with respect to specific patterns. 

Traditionally this meant network- and server-type events, failures, and other condtions that alerted an operator that the system was not responding in a normal manner. 

Advances in **user behavioral analysis** has provided another interesting use of the SIEM: monitoring what people do with their systems and how they do it. 

Many modern SIEMs have modules that analyze end-user behaviors, looking for anomalous behavior patterns that indicate a need for analysis. 

### Sentiment Analysis
The same systems that are used to pattern-match security issues can be adapted to match patterns of data indicating specific sentiments. 

Sentiment analysis is used to identify and track patterns in human emotions, opinions, or attitudes that may be present in data.

### Security Monitoring 
**Def: security monitoring process of collecting and analyzing information to detect suspicious behavior or unauthorized changes on your network and connected systems.**

Today, security orchestration, automation, and response (SOAR) systems complete the move to full cycle automation of security processes.

### Log Aggregation
**Def: log aggregation is the process of combining logs together.**

This allows different formats from different systems to work together.

The objective of log aggregation is to take multiple different data sources and condition the data into a form that is searchable and usable for specific purposes. 

### Log Collectors 
**Def: Log collectors are pieces of software that function to gather data from multiple independent sources and feed it into a unified source such as a SIEM.**

Different sources may have differing formats, and log collectors can harmonize these different field elements into a comprehensive data stream. 



# Questions
1. B
2. A
3. C (This type of scan is less scalable with automation)
4. D
5. C
6. A (Applications are not part of the SIEM process)
7. D
8. A,B,D
9. A
10. A

