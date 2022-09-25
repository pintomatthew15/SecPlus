# Chapter 30
# Digital Forensics 

Computer forensics is certainly a popular buzzword in computer security. The term forensics relates to the application of scientific knowledge to legal problems. 

**Def: Digital forensics is the technical side of developing proof as to what happened or didn't happen as part of an incident response effort.**

## Documentation/Evidence
All evidence is not created equal. Some evidence is stronger and better than other, weaker evidence. Several types of evidence can be germane:
- **Direct evidence**: Oral testimony that proves a specific fact (such as an eyewitness statement). The knowledge of the facts is obtained through the five senses of the witness, with no inferences or presumptions.
- **Real evidence**: Also known as associative or physical evidence, this includes tangible objects that prove or disprove a fact. Physical evidence links the suspect to the scene of a crime.
- **Documentary evidence**: Evidence in the form of business records, printouts, manuals, and the like. Much of the evidence relating to computer crimes is documentary evidence.
- **Demonstrative evidence**: Used to aid the jury and can be in the form of a model, experiment, chart, and so on, offered to prove that an event occurred. 

A wide range of items can be considered documentation and evidence is an investigation. This chapter examines some of the common types one would run across in a forensics examination and the issues associated with each.

### Legal Hold
In the U.S legal system, legal precedent requires that potentially relevant information is preserved at the instant a party "reasonably anticipates" litigation or another type of form dispute.
- Once an organization is aware that it needs to preserve evidence for a court case, it must do so.
- **Def: A legal hold or litigation hold is the process by which you properly preserve any and all digital evidence related to a potential case.**

Where does the information subject to a legal hold reside? 
- Everywhere effectively
- Finding and managing all of this information falls under a branch of digital forensics called e-discovery, which deals with the identification, management, and preservation of digital information that is subject to legal hold.

**EXAM TIP: Understanding the consequences of legal hold on record retention is testable, and legal holds supersede any standard corporate policy or procedure.**

### Video
A convenient method of capturing significant information at the time of collection is video capture.
- Videos allow high-bandwidth data collection that can show what was connected to what, how things were laid out, desktops, and so forth.

Another source of video data is in the closed-circuit television (CCTV) cameras that are used for security both in industry and, in growing numbers, homes. 

**EXAM TIP: A digital camera is great for recording a scene and information. Screenshots of active monitor images may be obtained as well. Pictures can detail elements such as serial number plates, machines, drives, cables connections, and more. A photograph is truly worth a thousand words.**

### Admissibility
For evidence to be credible, especially if it will be used in court proceedings or in corporate disciplinary actions that could be challenged legally, it must meet three standards:
- **Sufficient Evidence: The evidence must be convincing or measure up without question.**
- **Competent Evidence: The evidence must be legally qualified and reliable.**
- **Relevant Evidence: The evidence must be material to the case or have a bearing on the matter at hand.**

For materials to meet these standards for **admissibility**, it is incumbent that proper procedures are followed at all stages during collection, processing, and analysis. 

Three rules guide a judge's determination of whether to admit an item into evidence:
1. **Best evidence rule**: Courts prefer original evidence rather than a copy, to ensure that no alteration of the evidence has occurred.
2. **Exclusionary rule:** Any evidence collected in violation of the fourth amendment (improper search/seizure) is not admissible as evidence.
3. **Hearsay rule**: Hearsay is secondhand evidence -- evidence offered by the witness that is not based on the personal knowledge of the witness but is being offered to prove the truth of the matter asserted. 

**NOTE: The laws mentioned here are U.S laws. Other countries and jurisdictions may have similar laws that would need to be considered in a similar manner.**

### Chain of Custody
After evidence is collected, it must be properly controlled to prevent tampering. 
- **Def: The chain of custody accounts for all persons who handled or had access to the evidence.**
- It also shows who obtained the evidence, when and where it was obtained, where it was stored, and who had control or possession of the evidence for the entire time since the evidence was obtained. 
- The following are the critical steps in a chain of custody:
	1. Record each item collected as evidence
	2. Record who collected the evidence along with the data and time it was collected or recorded
	3. Write a description of the evidence in the documentation
	4. Put the evidence in containers and tag the containers with the case number, the name of the person who collected it, and the date and time it was collected or put in the container.
	5. Record all message digest (hash) values in the documentation
	6. Securely transport the evidence to a protected facility
	7. Obtain a signature from the person who accepts the evidence at this storage facility
	8. Provide controls to prevent access to and compromise of the evidence while it is being stored.
	9. Securely transport the evidence to court for proceedings

**EXAM TIP: Never analyze the seized device directly. The original evidence must be secured and protected with a chain of custody. It should never be subjected to a forensic examination because of the fragile nature of digital evidence. A forensic copy, can be examined and, if something goes wrong, discarded, and the copy process can be repeated. A good forensic analysis shows that the forensic copy and the original copy are the same from beginning to end**

### Timelines of Sequence Events
Digital forensic investigations begin with a scope a charge of what is of interest to be investigated.
- In a modern computer environment, asking for everything that happened is a scope that is impossible to fulfill, for just booting up a machine can result in hundreds of events in literally seconds. 
- The timeline of events will have the specifics, including the metadata to document it, demonstrating the sequence of events as recorded by the computer. 
- The sequence can be very important because it provides key clues as to what actually happened, even when there is not a direct artifact. 

#### Timestamps
**Def: Timestamps are metadata entries associated with artifacts in a computer system.**
- While a log entry may have a timestamp, some items can have multiple timestamps, stored in multiple locations. 
- In NTFS, there are three common file times (Creation, Modification, Accessed) and one metadata time (MFT Change). 
- These four timestamps are stored in two places: one with the $File_Name attribute and one with $Standard_Info. 

Time is measured differently in Linux and Windows. 
- Linux uses the concept of Epoch time--the number of seconds that have elapsed since January 1, 1970. It is stored as a signed 32-bit number, enabling times before January 1, 1970 as well as after.
- Windows uses 64-bit value that represents the elapsed time since 12:00 AM January 1, 1601 Coordinated Universal Time (UTC), with a resolution of 100-nanosecond intervals.

#### Time Offset
**Def: Record time offset is the difference in time between the system clock and the actual time.**
- Computers keep their own time, but to minimize record time offset, most computer sync their time over the Internet with an official time source.
- File and events logged on a computer will have timestamp markings that are based on the clock time on the machine itself.

Another form of time offset is the difference between local time zones and UTC. 
- As discussed earlier, with most time records being in UTC, conversion to local time zones may be necessary to make sense of some records.

**NOTE: Whenever one is using time, whether timestamps, log times, or comparison to actual calendars, it is important to synchronize all records to the same offset. Many logs use local time. Comparing local time and UTC time will result in errors, except for the GMT time zone, where the local time is UTC. Know what your times are with respect to the zones before use.**

**EXAM TIP: Understanding time elements for forensics is important. Pay attention to time zones and the specific details in the question.**

### Tags
As previously discussed, a chain-of-custody document records all accesses to evidence from time of collection until destruction. 
- Physical serialized tags are attached to each item, and the tag number is used to identify a specific item.
- Frequently the items are then stored in anti-static bags to protect them from damage. 

### Reports 
**Def: Reports are the official descriptions of the forensic data.**
- Reports can have a variety of elements--from pure descriptive information, such as machine/device identifiers (make, model, and serial number), to information on the data, including size and hash values. 
- Reports can also have specific elements that are derived from this information, such as a timeline, an analysis of keywords, specific artifacts, and present or missing items.
- As such, reports tend to be very sanitized, and the lawyers add the color of the case later. 

### Event Logs
Ideally, you should minimize the scope of logging so that when you have to search logs, the event you are interested in stands out without being hidden in a sea of irrelevant log items. 
- Active logging is determined during preparation, and when it comes time for recovery, the advance planning pays off in the production of evidence.

### Interviews
Remember that witness credibility is extremely important. 

As human memory is not as long lasting as computer files, it is important to get witness testimony and collect that data as early as possible. 
- Having them write down what they remember immediately is very helpful in preserving memory.

**EXAM TIP: The different elements under documentation/evidence work together, not as separate entities. Be sure to understand what the question is specifically asking for when you choose the answer, as several answers may be connected to the correct one, but one will be the principal component.**

## Acquisition
**Def: Acquisition refers to the collection of information that may be evidence in an investigation.**
- Evidence consists of the documents, verbal statements, and material objects admissible in a court of law.
- It is vitally important to document all the steps taken in the collection of evidence, as these may be challenged in court and the processes followed as evidenced by the documentation will be all that can be used to demonstrate the veracity of the processes

### Order of Volatility 
There are many sources of data in a computer system, and if the machine is running, some of these sources are volatile.
- Items such as the state of the CPU and its registers, RAM, and even storage are always changing, which can make the collection of electronic data a difficult and delicate task. 
- **Def: The order of volatility is that lifetime of the data.**

The following is the order of volatility of digital information in a system:
1. CPU, cache, and register contents (collect first)
2. Routing tables, ARP cache, process tables, kernel statistics
3. Live network connections and data flows
4. Memory (RAM)
5. Temporary file system/swap space
6. Data on hard disk
7. Remotely logged data
8. Data stored on archival media/backups (collect last)

**EXAM TIP: Understanding the order of volatility of digital information in a system is a testable item--commit this to memory.**

Failure to pay attention to the order of volatility during data collection will result in data loss, and once lost, the data is gone forever in many of the categories.

**EXAM TIP: A common data element needed later in the forensics process is an accurate system time with respect to an accurate external time source. A record time offset is calculated by measuring system time with an external clock such as a Network Time Protocol (NTP) server. The offset between system time and true time can be lost if the system is powered down, so it is best to collect it while the system is still running.**

### Disk
When collecting digital evidence, it is important to use proper techniques and tools. Some of the key elements are the use of write blockers when making forensic copies, hashing and verifying hash matches, documenting handling and storage, and protecting media from environmental change factors. 

A physical hard disk drive (HDD) will persist data longer than a solid state drive (SSD). 
- Raw disk blocks can be recovered in some file systems long after data has been rewritten or erased, due to the nature of how the file system manages the data. 

### Random-Access Memory (RAM)
**Def: Random-access memory (RAM) is the working memory of the computer that handles the current data and programs being processed by the CPU.**
- This memory, once limited to a single megabyte, now commonly consists  of 4GB or more.
- This memory holds the current state of the system as it is processing and is continuously changing.
- There are cases of malware that exists only in RAM, and without memory analysis and forensics, you would never see it.

### Swap/Pagefile
**Def: The swap or pagefile is a structure on a system's disk to provide temporary storage for memory needs that exceed a system's RAM capacity.**
- The OS has provisions that manage the RAM and pagefile, keeping in RAM what is immediately needed and moving excess to the pagefile when RAM is full.
- Capturing the pagefile (pagefile.sys stored by default in C:\ pagefile.sys) in a forensics investigation is important any time the RAM is captured, as it is an extension of the RAM. 

### Operating System (OS)
**Def: The OS, or operating system, is a base computer program that acts as the manager of all activity on a system.**
- The OS is the source of many forensic artifacts, most of which are created to enhance system responsiveness to user requests.
- The two major OSs, Windows and Linux, perform basically the same tasks: they enable applications to perform on a system.

### Device
One of the most common device acquisitions is USB storage devices. These devices are used to transport files between machines and are common in any case where the removal of information is suspected. 

### Firmware
**Def: Firmware is a set of software that is associated with a physical device.**
- Firmware exists for almost every electronic device, not just computers; for example, firmware exists for USB devices.
- Firmware can be of interest in a forensics investigation when the malfunctioning of a device is an issue, as malware has targeted the firmware. 

### Snapshot
**Def: A snapshot, as you can easily guess, is a picture of a particular moment in time.**
- Snapshots are common in virtual machines, providing a point in time to which the machine can be recovered.
- Operating systems also have adopted this technology for some of their information, using point-in-time recovery to assist in fixing problems from updates or changes to the system.
- The scope of what is covered by a snapshot can vary between different systems, and this may limit usefulness.

### Cache
**Def: Caches are temporary storage locations for commonly used items and are designed to speed up processing.**
- Cashes exist all over in computer systems and are performance-enhancing items.
- Caches exist for files, for memory, for artifacts; they exist for fast retrieval of items that the OS expects
- An example of this would be an artifact such as a prefetch record of a file, indicating that the user that is logged in has previously opened that file.

### Network
An important source of information in an investigation can be the network activity associated with a device.
- There can be a lot of useful information in the network logs associated with network infrastructure.
- The level of breadth of this information is determined by the scope of the investigation. 
- There are many other sources of network forensic data, including firewall and IDS logs, network flow data and event logs on key servers and services.

### Artifacts
**Def: Artifacts are the key element in modern digital forensics.**
- Most of the items used to demonstrate a specific action as occurring fall into one of two categories:
	1. metadata: registry entries, timestamps, and sizes 
	2. OS artifacts: prefetch files, jump list artifacts

**EXAM TIP: Artifacts are the principal data element used in forensics. They are connected to how the computer manages data to perform a task. Be sure to choose the correct artifact that's specifically and directly related to the question, not peripherally.**

## On-premises vs. Cloud
The cloud has become a resource for enterprise IT systems, and as such it is intimately involved in both e-discovery and forensics.
- Having data that may or may not be directly accessed by the tools of e-discovery and forensics can complicate the needed processes. 

The issues associated with **on-premises versus cloud** with respect to forensics is one dominated by access. 
- When storage or computing is happening on another party's computing platform, as in the cloud, whether physically at another site or on premises, access is governed by the contracts and agreements covering the relationship.

### Right to Audit Clauses 
Audits are the mechanism used to verify that systems are performing to their designed levels of purpose, security, and efficiency.
- The ability to audit involves access to a system and the data.
- When the information is stored or processed in the cloud, users need the ability to audit the cloud provider.
- The only rights the customer has are detailed in the service level agreements/contracts with the **cloud provider**. 
- This makes the **Right to Audit clause** a critical requirement of any service level agreement, and its specificity needs to match the operational and regulatory scope of the cloud engagement. 

### Regulatory/Jurisdiction
Whether on premises or in the cloud, there will be cases where regulatory or law enforcement actions raise jurisdictional issues. 
- It is important to consult with the company's legal counsel to understand the ramifications of data location with respect to forensics and subsequent data use. 

### Data Breach Notification Laws
The discovery of a data breach can occur during a forensic examination. 
- Many forensic investigations are related to the theft of intellectual property, and many times that is also a breach of data protected under privacy laws. 

## Integrity
**Def: Integrity is a very important concept in security because it refers to the veracity of a data element.**
- Has there been an unauthorized change to an element, or can on trust its current value?

### Hashing
If files, logs, and other information are going to be captured and used for evidence, you need to ensure that the data isn't modified.
- In most cases, a tool that implements a hashing algorithm to create message digests is used. 

A **hashing algorithm** performs a function similar to the familiar parity bits, checksum, or cyclic redundancy check (CRC).
- IT applies mathematical operations to a data stream (or file) to calculate some number that is unique based on the information contained in the data stream (or file).
- If a subsequent hash created on the same data stream results in a different hash value, it usually means that the data stream was changed.
- The hash tool is applied to each file or log and the message digest value is noted in the investigation documentation.

**NOTE: The number of files stored on today's hard drives can be very large--literally hundreds of thousands of files. Obviously, this is far too many for the investigator to analyze. However, by matching the message digests for files installed by the most popular software products to the message digests of the files on the drive being analyzed, the investigator can avoid analyzing approximately 90% of the files because he can assume they are unmodified.**

**EXAM TIP: Hashing is used throughout digital forensics to measure integrity between copies of data. Checksums do not have the specificity of hashes, so hashes are the primary tool.**

### Checksums
**Def: Checksums are mathematical algorithms that produce a check digit based on an incoming stream.**
- Designed for error testing across small data sets, they have advantages and disadvantages. 
- One advantage is that for error checking, they are fast and can detect a single-bit error.
- A disadvantage is that they miss larger numbers of errors as a second error can cancel the effect of the first on a checksum.
- If two checksums are different, the incoming data streams are different, IF they are the same, you still may have different data streams.

### Provenance
**Def: Provenance is a reference to the origin of the data.**
- Provenance is specific, as in where on a file structure and where on a device; in most cases, there will be multiple representations, as in the file structure with respect to where a file resides and with respect to the OS (logical) and its location on a physical drive in sectors.

## Preservation
One of the key elements in preservation is to ensure that nothing changes as a  result of data collection.
- If a machine is off, do not turn it on--the disk drives can be imaged with the machine off.

Digital evidence has one huge, glaring issue: it can change and not leave a record of the change. 
- The fact that the outcome of a case can hinge on information that can be argued as not being static makes the act of preservation a crucial element in determining the veracity of evidence. 

**EXAM TIP: Understanding not only the importance of data preservation but the process of ensuring it uses hash values is a very testable concept.**

## E-Discovery
Electronic discovery, or e-discovery, is the term used for the document and data production requirements as part of legal discovery in civil litigation.
- When a civil lawsuit is filed, under court approval, a firm can be compelled to turn over specific data from systems pursuant to the legal notice at hand.

One of the pressing challenges in today's enterprise record store is the maintenance of the volumes of electronic information.

## Data Recovery 
**Def: Recovery in a digital forensics sense is associated with determining the relevant information for the issue at hand--simply stated, recover the evidence associated with an act.**

Handing a forensic investigator a 1TB drive and sayin, "Tell me everything that happened on this machine," is a tantamount to giving the investigator a never-ending task.

## Nonrepudiation
**Def: Nonrepudiation is a characteristic that refers to the inability to deny an action has taken place.**
- Using cryptographic elements to establish identity and credentials, along with hash values to establish integrity, the appropriate combinations can yield results that can only happen if the parties are actually involved and the event took place.

**EXAM TIP: Nonrepudiation is an important security concept. In fact, it is listed in two separate exam objectives. Remember it refers to the inability to deny an action has taken place. Digital signatures, the use of multiple authentication factors, and even audit trails by IP address are examples of nonrepudiation and prove or disprove that something has happened.**

## Strategic Intelligence/Counterintelligence
**Def: Strategic intelligence gathering is the use of all resources to make determinations.**
- This can make a large difference in whether or not a firm is prepared for threats. 
- Strategic intelligence can provide information that limits the scope of an investigation to a manageable level.

**Def: Counterintelligence gathering is the gathering of information specifically targeting the strategic intelligence effort of another entity.**
- Making and using a tool so that it does not leave specific traces of where, when, or on what it was used is a form of counterintelligence gathering in action.

# Questions
1. C,A,B,D
2. A
3. B
4. D
5. C
6. B (Real evidence is also known as associative or physical evidence and includes tangible objects that prove disprove a fact.)
7. A
8. C
9. D
10. A



