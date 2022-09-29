# Chapter 28
# Investigations

Investigations are used to determine what happened, who did what, and what elements of an information system have been affected by some specific event or series of events.

This chapter looks at how to utilize these sources of data to support an investigation and shed light on what actually happened to both the system and the data it processed.

## Vulnerability Scan Output
**Def: Vulnerability scan output provides information as to the systems that are running, any additional services that are listening on the network, and what the known vulnerabilities are against each of these.**

This information is important in a couple of ways:
1. It allows verification that the authorized systems are adequately patched.
2. Even more important, is the identification of additional services.

Bottom line: A vulnerability report provides you information on what is visible on your network, authorized or not.

## SIEM Dashboards
**Def: Security Information and Event Management (SIEM) dashboards are the windows into the SIEM datastore, a collection of information that can tell you where attacks are occurring and provide a trail of breadcrumbs to show how the attacker got into the network and moved to where they are now.**
- SIEM systems act as the information repository for information surrounding potential and actual intrusions. 
- The fundamental purpose of SIEM systems is to provide alerts and relevant information to incident response teams that are investigating incidents. 

**EXAM TIP: SIEMs allow you to identify, visualize, and monitor trends via alerts and a dashboard.**

### Sensor
**Def: Sensors are the devices that provide security data into the security datastore.**
- Sensors must be placed in the correct location to collect information 

Sensor placement begins with defining collection objectives
- **Def: Collection objectives are a study of where the data flows, where the information of value is in a network, and where adversaries can gain access, coupled with what information you wish to collect.**

### Sensitivity
**Def: Sensitivity is the quality of being quick to detect or respond to slight changes, signals, or influences.**
- Biggest issue with SIEMS and sensitivity is tradeoff between false positives and false negatives. 
- Must adjust sensitivity to the right balance 

### Trends
**Def: Trends are a series of data points that indicate a change over time.**
- Trends can be increasing, decreasing, cyclical, or related to variability.
- What is important is that trends indicate some form of change.

### Alerts 
**Def: Alerts are the primary method of communication between the SIEM system and operators.**
- Make sure alerts have information that steers engineers in right direction

### Correlation
**Def: Correlation is the process of establishing a relationship between two variables.**
- Correlation is a means for a SIEM system to apply rules to combine data sources to fine-tune event detection.

**EXAM TIP: SIEM event correlation logs are extremely useful because they can be used to identify malicious activity activity across a plethora of network devices and programs. This is data that otherwise may go unnoticed.**

## Log Files
**Def: Log files are a primary source of information during an investigation.**
- Software can record in log files a wide range of information as it is operating. 
- Logs act as a historical record of what happened on a system.
- Log files require configuration because if you don't log an event when it happens, you can't go back in time to capture it. 

### Network
Networks are filled with equipment that can provide valuable log information. Firewalls, routers, load balancers, and switches can provide a wealth of information.
- **Network Logs** tend to have a duplication issue as packets can traverse several devices, giving multiple, nearly identical records.

### System
Virtually every operating system creates **system logs**. 
- These logs provide a very detailed history of what actions were performed on a system.
- Big question is which logs produce meaningful information and what is just noise?
- Remember, the decision to log must happen before the event occurs.

### Application
**Def: Application logs are generated by applications themselves as they run.**
- Logging volume and capability vary per application

### Security
**Def: Security logs are logs kept by the OS for metadata associated with security operations.**
- In Windows, group policy objects help tune logs to collect information that is needed.

The driving force for what needs to be recorded is the system's audit policy, a statement about what records need to be kept.

**EXAM TIP: The Windows Event Viewer is used to look at Windows logs. The System log displays information related to the operating system. The Application log provides data related to applications that re run on the system. The Security log provides information regarding the success and failure of attempted logins as well as security-related audit events.**

### Web
Web servers respond to specific, formatted requests for resources with responses, whether in the form of a web page or an error.
- All this activity can be logged.
- Web log files can help identify when these activities are occurring.

### DNS 
**Def: DNS logs, when enabled, can contain a record for every query and response.**
- This can be a treasure trove of information for an investigator because it can reveal malware calling out to its command-and-control server, or data transfers to non-company locations.
- Analysis of DNS logs can show IP addresses and domain names that your systems should be communicating with as well as ones they shouldn't be.
- DNS logs are some of the most valuable logs to import into a SIEM system

### Authentication
**Def: Authentication logs contain information about successful and failed authentication attempts.**
- The most common source of authentication log information comes from the system's security logs, but additional sources exist as well. 

### Dump Files
**Def: Dump files are copies of what was in memory at a point in time--typically a point when some failure occurred.**
- Dump files can be created by the operating system (OS) when the OS crashes, and these files can be analyzed to determine the cause of the crash.
- Dump files can also be created by several utilities and then shipped off for analysis by a 3rd party
- Dump files can contain sensitive information.

### VoIP and Call Managers
**Def: Voice over IP (VoIP) solutions and call manger applications enable a wide range of audio and video communication services over the internet.**
- These systems can log a variety of data, including call information such as the number called (to and from), time of the call, and duration of the call.
- These records are called call detail records (CDRs).

### Session Initiation Protocol (SIP) Traffic
**Def: The Session Initiation Protocol (SIP) is a text-based protocol used for signaling voice, video, and messaging applications over IP.**
- SIP provides information for initiating, maintaining, and terminating rea-time sessions.
- SIP traffic logs are typically in the SIP Common Log Format (CLF), which mimics web server logs and captures the details associated with a communication 

## Syslog/Rsyslog/Syslog-ng
**Def: Syslog stands for System Logging Protocol and is a standard protocol used in Linux systems to send system log or event messages to a specific server.**
- **Def: Rsyslog is an open source variant of syslog that follows the syslog specifications but also provides additional features such as content-based filtering.**
- **Def: Syslog-ng is another open source implementation of the syslog standard.** It can tag, classify, and correlate in real time, which can improve SIEM performance. 
- For Linux-based systems, these implementations are the de facto standard for managing log files.

**EXAM TIP: Syslog, rsyslog, and syslog-ng all move data into log files on a log server. Ryslog and syslog-ng both extend the original syslog standard by adding capabilities such as content filtering, log enrichment, and correlation of data elements into higher-level events. **

## Journalctl
**Def: On a Linux system, the initial daemon that launches the system is called systemd.**
- When systemd creates log files, it does so through the systemd-journald service.
- **Def: Journalctl is the command that is used to view these logs.**

Here is an example of journalctl comand to view logs for a given systems service.
``` journalctl -u ssh ```

**EXAM TIP: Understand the differences between journalctl and syslog. Journalctl is the command to examine logs on a server. Syslog is used to move logs to a log server and sometimes to manipulate the log file entries in transit.**

## NXLog 
**Def: NXLog is a multiplatform log management tool designed to assist in the use of log data during an investigation.**
- This tool is capable of handling syslog-type data as well as other log formats, including MS Windows.
- As logs are one of the most used data sources in investigations, tools such as NXLog can enable investigators to identify security issues, policy violations, and operational problems in systems.

## Bandwidth Monitors
**Def: Bandwidth monitors are utilities designed to measure network bandwidth utilization over time.**
- Bandwidth monitors can provide information as to how much bandwidth is being utilized, by service type, and how much remains.
- Bandwidth monitors can log this information over time and provide a historical record of network congestion problems, including by type of traffic in quality of service-enforced networks. 

## Metadata
**Def: Metadata is data about data.**
- A file entry on a storage system has the file contents plus metadata, including the filename, creation, access, and update timestamps, size, and more.
- Collecting, analyzing, and correlating metadata are all part of almost every investigation.

**EXAM TIP: Remember that everything digital contains metadata, and correlating metadata is a part of almost every investigation.**

### E-mail
E-mail is half metadata, half message. 
- E-mail metadata is in the header of the email and includes routing information, the sender, receiver, timestamps, subject, and other information associated with the delivery of the message.

The header of an e-mail includes information for the handling of the e-mail between mail user agents (MUAs), mail transfer agents (MTAs), and mail delivery agents (MDAs), as well as a host of other details.
- The entire message is sent via plain ASCII text, with attachments included using the Base64 encoding. 

E-mail header data can be important in investigations because it can show details such as the following:
- **From**: Contains information on where the message comes from (can easily be forged.)
- **To**: The receiving end of the e-mail (not necessarily the recipient's e-mail address)
- **Subject**: Think of this as the "title" or the topic.
- **Date**: This is the data and time when an e-mail is written. 
- **Return-Path**: Also known as Reply-To, this field contains the address where the reply to the e-mail will be sent.
- **Delivery Date**: This is the timestamp when an e-mail client receives the e-mail.
- **Received**: This line shows the servers an e-mail has gone through in order to arrive at the recipient's mailbox. 
- **DKIM Signature and Domain Key Signature**: DKIM stands for Domain Keys Identified Mail. Along with the domain key signature, it is part of an e-mail signature identification system.
- **Message-ID**: This is a combination of unique letters and numbers created when the e-mail was first written.
- **MIME-version**: MIME is an Internet standard that extends the format and the functionality of an e-mail. You can attach videos, images, and other files using MIME. Attachments are in Base64.
- **Content-type**: Tells you whether e-mail is written as plaintext or HTML.
- **X-Spam status**: Tells you the score of an e-mail. IF it reaches more than the threshold, the e-mail will be considered spam.
- **X-Spam level**: This level depends on the score of the e-mail's X-Spam status, for every point it gains, the X-Spam level will show one asterisk.
- **Message Body**: The actual message that was sent 

As you can see, an e-mail can be mostly metadata.

### Mobile
Mobile devices generate, store, and transmit metadata.
- Other sources of metadata include things like Wi-Fi access points connected to, GPS data in application logs, whether the device has a camera, and EXIF data.

### Web
The Web provides a means of moving information between browsers and servers.
- There are a variety of protocols involved and a variety of sources of metadata.
- There can be a wealth of user behavior information with respect to web browsing.

### File
File metadata comes in two flavors: system and application.
- The file system uses metadata to keep track of the filename as well as the timestamps associated with last access, creation, and last write.
- The system metadata will include items needed by the OS, such as ownership information, parent object, permissions, and security descriptors.

Application metadata in a file is part of the file data field and is used by the application. 
- A JPEG file, has metadata that's typically expressed in the form of EXIF data.
- The Exchangeable image file (EXIF) format is a standard that defines the formats of image, audio, and metadata tags used by cameras, phones, and other digital recording devices. 
- EXIF data exists to assist applications that use these files and can be modified independently of the file contents.

**EXAM TIP: Metadata is a very valuable source of information during an investigation. Understanding what type of information and detail are present in each major category is important.**

## NetFlow/sFlow
**Def: NetFlow and sFLow are protocls designed to capture information about packet flows as they traverse a network.**
- NetFlow is a proprietary standard from Cisco/
- Flow data is generated by the network devices themselves, including routers and switches. 
- The data that is collected and shipped off to data collectors is a simple set of metadata--source and destination IP addresses, source and destination ports, if any, and the protocol.
- NetFlow does this with all packets, but sFlow does a statistical sampling. 

**EXAM TIP: Both NetFlow and sFlow collect packets from routers and switches. NetFlow data can be useful in intrusion investigations. sFlow is used primarily for traffic management, although it will help with DDoS attacks.**

### IPFIX
**Def: Internet Protocol Flow Information Export (IPFIX) is an IETF protocol that's the answer to the proprietary Cisco NetFlow standard.**
-  The primary purpose of IPFIX is to provide a central monitoring station with information about the state of the network.
- IPFIX is a push-based protocol, where the sender sends the reports and  receives no response from the receiver. 

## Protocol Analyzer Output
**Def: A protocol analyzer (also known as a packet sniffer, network analyzer, or network sniffer) is a piece of software or an integrated software/hardware system that can capture and decode network traffic.**
- Protocol analyzers have been popular with system administrators and security professionals for decades because they are such versatile and useful tools for a network environment.

Protocol analyzers can be used for a number of activities, such as:
- Detecting intrusions or undesirable traffic. (An IDS/IPS must have some type of capture and decode capabilities to be able to look for suspicious/malicious traffic.)
- Capturing traffic during incident response or incident handling
- Looking for evidence of botnets, Trojans, and infected systems.
- Looking for unusual traffic or traffic exceeding certain thresholds.
- Testing encryption between systems or applications.

From a network administration perspective, protocol analyzers can be used for activities such as:
- Analyzing network problems
- Detecting misconfigured applications or misbehaving applications
- Gathering and reporting network usage and traffic statistics
- Debugging client/server communications

Regardless of intended use, a protocol analyzer must be able to see network traffic in order to capture and decode it. The output of the analyzer is a human-readable format of the information being passed on the system.

# Questions
1. C
2. B (NetFlow data describes which machines are talking to which machines)
3. C (Syslog is the protocol used to move log files to remote servers)
4. A (IPFIX captures which machines are in communication with each other)
5. A 
6. D 
7. C 
8. D (Removing the duplicates in a distributed system can be a challenge)
9. B
10. A,B,C,D




 




 