# Chapter 13
# Cybersecurity Resilience

## Redundancy
**Def: Redundancy is the use of multiple, independent elements to perform a critical function, so that if one element fails, there is another that can take over the work.**

Some common applications of redundancy include the use of redundant servers, redundant connections, and redundant ISPs. 

**Exam Tip: Redundancy is an important factor in both security and reliability. Make sure you understand the many different areas that can benefit from redundant components.**

### Geographic Dispersal
An important element to factor into the cost of the backup strategy is the expense of storing the backups. 

The solution is to keep copies of backups in separate locations. The most recent copy can be stored locally, as it is the most likely to be needed, while other copies can be kept at other locations. 

A more recent advance is online backup services. 

### Disk
Disks are the primary storage mechanism in a system, whether composed of physical hard drives with spinning platters or solid-state memory devices. 

The therm disk refers to the spinning platter historically, but more and more storage is being handled by solidstate memory. 

Also the logical construct of a disk can be mapped across multiple physical storage elements.

### Redundant Array of inexpensive Disks (RAID) Levels
A common approach to increasing reliability in disk storage is employing a redundant array of inexpensive disks (RAID). 

RAID takes data that is normally stored on a single disk and spreads it out among several others. If any single disk is lost, the data can be recovered from the other disks where the data also resides. 

RAID can also increase the speed of data recovery as multiple drives can be busy retrieving requested data at the same time instead of relying on just one disk to do the work.

Several different RAID approaches can be considered:

- RAID 0 (stripped disks) simply spreads the data that would be kept on the one disk across several disks. This decreases the time it takes to retrieve data because the data is read from multiple drives at the same time, but it does not improve reliability because the loss of any single drive will result in the loss of all the data. Data is split across all the drives with no redundancy offered. 

- RAID 1 (mirrored disks) is the opposite of RAID 0. RAID 1 copies the data from one disk onto two or more disks. If any one disk is lost, the data is not lost since it is also copied onto the other disk(s). This method can be used to improve reliability and retrieval speed, but it is relatively expensive when compared to other RAID techniques. 

- RAID 2 (bit-level error-correcting code) is not typically used, as it stripes data across the drives at the bit level as opposed to the block level. It is designed to be able to recover the loss of any single disk through the use of error-correcting techniques. 

- RAID 3 (byte-striped with error check) spreads the data across multiple disks at the byte level with one disk dedicated to parity bits. This technique is not commonly implemented because input/output operations can't be overlapped due to the need for all to access the same disk

- RAID 4 (dedicated parity drive) stripes data across several disks but in larger stripes than in RAID 3, and it uses a single drive for parity-based error checking. RAID 4 has the disadvantage of not improving data retrieval speeds since all retrievals still need to access the single parity drive.

- RAID 5 (block-striped with error check) is a commonly used method that stripes the data at the block level and spreads the parity data across the drives. This provides both reliability and increased speed performance. This form requires a minimum of three drives. 

RAID 0 through 5 are the original techniques, with RAID 5 being the most common method used, as it provides both the reliability and speed improvements. 


**Exam Tip: Knowledge of the basic RAID structures by number designation is a testable element and should be memorized for the exam. RAID 0 and RAID 1 require a two-drive minimum. Both RAID 3 and RAID 5 have a three-drive minimum. RAID 10 (also called 1+0) requires four drives at a minimum.**


### Multipath Solutions
Between the storage systems and the server/computer is an I/O interface. 

The I/O interface converts the information from the computer to a form that works for the specific storage system. 

When a storage element is connected by multiple adapters, this provides rudnancy in the event of a problem with one of the adapters. This is referred to as a **multipath** connection and is commonly employed in high-reliability servers and critical systems. 

Figure 13-1 shows a server with two host bus adapters (HBAs), along with two storage area network (SAN) switches and two RAID controllers. This provides two independent paths from server to data. 

![[multipath-server3.png]]

### Network
A network is the infrastructure element that connects all the IT components in the enterprise. 

A network can serve as a point of failure, or it can be a system of redundant connections that can be resilient under various traffic loads and connectivity conditions. 

Having a properly architected network that has multiple independent pathways and infrastrucutre  elements designed to increase redundancy is important.

Two major elements to consider are load balancers and network interface card (NIC) teaming to remove some of the common modes of network-related traffic failures. 

### Load Balancers
**Def: a load balancer moves loads across a set of resources in an effort not to overload indiviudal servers.**

It is used to help improve resource utiliization and throughput but also has the added advantage of increasing the fault tolerance of the overall system since critical process may be split across several systems. 

Load balancing is best for stateless systems, as subsequent requests can be handled by any server, not just the one that processed the previous request.

### Network Interface Card (NIC) Teaming
If a server has multiple network interface cards (NICs) connecting it to a switch or router, it will have multiple addresses, one for each NIC. 

**Def: NIC teaming is an alternative means of connecting used by servers that have multiple network interface cards and wish to enjoy the benefits of load balancing, fault tolerance, and failover without requiring added infrastructure to do it.**

**Exam Tip: NIC teaming groups multiple NICs together to form a logical network device called a bond. This provides for load balancing and fault tolerance.**


---

## Power
Power is required for all machines to operate, and having a reliable and resilient source of electrical power is critical for continued operations of enterprise computing. 

Servers and networking equipment are always on, and even occasional outages due to equipment failures need to be planned for and managed to provide an appropriate level of service. 

In a modern enterprise, equipment such as uninterruptible power supplies, generators, dual supplies, and managed power distribution all support having the proper levels of electricity available to the networking equipment all the time. 

### Uninterruptible Power Supply (UPS)
**Def: Power supply systems that can function using a temporary battery backup in the event of a power failure.**

In most enterprise systems UPSs are designed and rated typically for 20 mins of runtime.

### Generator
Backup generators are used to provide power when normal sources of electricity are lost.

Generators come with a host of requirements, including maintenance and testing, and they require significant electrical architecture work to isolate the desired circuits. 

Sizing of the backup generator is done with respect to the load, and because of the phyiscal infrastructure, it is not easy or cost efficient to continuously resize the backup power. 

### Dual Supply
Individual pieces of equipment have power supplies in them to convert the line power in the facility to the voltages and currents used by the devices. 

A dual supply is a system where two independent power supply units, either capable of handling the load, are used. 

In the event that either supply is lost, the other one is used.

### Managed Power Distribution Units (PDUs)
**Def: a device designed to handle the electrical power for server racks.**

Server rooms need special HVAC to handle the heat distribution, and they used managed power distribution units to efficiently handle the electrical side.

The objective of a PDU is to efficiently convert the power, and manage the heat from the conversion, while producing a power flow that is conditioned from spikes and over/under voltage conditions. 

**Exam Tip: Given a scenario, you should understand how each device is used to manage power and provide cybersecurity resilience.**

---
## Replication
**Def: Having another copy of something should something happen to the original.**

Dual power supplies replicate the power. Having a redundant array of disks to store data is another form of replication, as are backups and having offsite alternate operations for business and continuity purposes. 

Common ways of seeing replication in everyday enterprises include the use of storage area networks and virtual machine technologies. 

### Storage Area Network (SAN)
**Def: A dedicated network that connects compute elements to storage elements.**

This network can be optimized for the types of data sotrage needed, in terms of size and data rates, in terms of format, and in terms of accesss criteria. 

Data storage is independent of any individual computer and can even interface to mulltiple redundant storage systems to allow redundancy on the side of data storage as well.

### VM

Virtual Machine (VM) technologies can enable replication of processing units that can be manipulated between different computers.

VM technology allows multiple copies of a specific instance to be used on different hardware and with centralized monitoring and management.

Proper maintenance and deployment of VM technologies can provide hardware independence for specific operating images, enabling efficient use of server resources. 

---
## On-premises vs. Cloud
When you're examining redundancy, one factor to consider is location. Make sure you factor in the risks of On-premises or cloud when making a redundancy decision.

---
## Backup Types
A key element in business continuity/disaster recovery (BC/DR) plans is the availability of backups. 

Data backup is thus a critical element in these plans, as well as in nromal operation. There are several factors to consider in an organization's data backup strategy: 
- How frequently should backups be conducted? 
- How extensive do the backups need to be?
- What is the process for conducting backups?
- Who is responsible for ensuring backups are created?
- Where will the backups be stored?
- How long will backups be kept?
- How many copies will be maintained?

The purpose of a backup is to provide valid, uncorrupted data in the event of corruption or loss of the original file or the media where the data was stored. 

There are four main forms of backup: full, incremental, differential, and snapshot.

Understanding the purpose of the archive bit is important when you read about the backup types. The archive bit is used to indicate whether a file has (1) or has not (0) changed since the last backup. 

The bit is set (changed to a 1) if the file is modified or, in some cases, if the file is copied, the new copy of the file has its archive bit set. 

The bit is reset (changed to a 0) when the file is backed up. The archive bit can be used to determine which files need to be backed up when using methods such as the differential backup method. 

**Exam Tip: Pay attention to details concerning how many backups are needed for a restore. Note that this is not a simple case of memorization because you need the details from the scenario to answer the question. Also, you need to know the "order of restoration" of the backups.**

### Full 
The easiest type of backup to understand is the full backup. 

In a full backup, all files and software are copied onto the storage media. Restoration from a full backup is copying all the files back into the system, which takes a considerable amount of time.

In a full backup, the archive bit is cleared.

**Exam Tip: A full backup copies all the data and clears/resets the archive bit. This process takes a considerable amount of time to complete but allows for a complete restore with one tape.**

## Incremental
The incremental backup is a variation on a differential backup, with the difference being that instead of copying all files that have changed since the last full backup, the incremental backup backs up only files that have changed since the last full or incremental backup occured, thus requiring fewer files to be backed up. 

With incremental backups, even less information will be stored every backup. 

The incremental backup relies on the occasional full backup being accomplished.

To restore a system using this type of backup requires quite a bit more work. First you need to go back to the last full backup and reload the system with this data. Then you have to update the system with ever yincremental backup that has occurred since the fullbackup. 

Advantage: requires less storage and time to accomplish
Disadvantage: the restoration process is more involved. 

An incremental backup will clear the archive bit.

**Exam Tip: To perform a restore from incremental backup, you need the last full backup and every incremental tape since the last full backup.**

### Snapshot
**Def: A copy of a virtual machine at a specific point in time.**

A snapshot is created by copying the files that store the virtual machine.

### Differential
In a differential backup, only the files that have changed since the last full backup was completed are backed up. 

This also implies that periodically a full backup needs to be accomplished. 

Restoration from a differential backup requires two steps:
1. the last full backup first needs to be loaded 
2. Then the last differential backup performed can be applied to update the files that have been changed since the full backup was conducted.

The archive bit in a differential backup is not cleared in a differential backup since the key for a differential is to back up all the files that have changed since the last full backup.

**Exam Tip: To perform a restore from differential backup, you need the last full backup and the most recent differential backup tape.**


Full
Amount of Space: Large
Restoration: Simple

Differential
Amount of Space: Medium
Restoration: Simple

Incremental
Amount of Space: Medium
Restoration: Involved

---
## Backup Technologies

### Tape
Tape drivers are an older form of data storage mechanism, and they are characterized by their sequential read/write access. 

A disk allows you to directly access specific elements randomly, whereas a tape system stores everything in one long structure, requiring you to physically move the tape if you wish to access an element halfway through the storage.

For bulk storage of backups, tape is still a viable alternative in terms of cost and performance.

### Disk
**Def: refers to either a physical hard drive with spinning platters or a solid-state memory device.**

Backing up a disk is a common operation for a single computer because most computers have very few disks, and this is a logical structure to maintain and restore.

For client-based PCs, a disk backup can make sense, and many systems can perform a full, incremental, snapshot, or differential backup of a disk.

### Copy
**Def: The simplest form of backup for a file or set of files.**

This method breaks down when the scope expands to larger and larger sets of data, and for large-scale backups, one of the previous methods is more efficient both for backing up and restoring. 

One of the advantages of having users make copies of critical documents is the abililty to do a quick restore in the event of an overwrite error.

### Network Attached Storage (NAS)
**Def: The use of a network connection to attach external storage to a machine.**

A simple method of extending storage

NAS is a simple extension of data storage to an external system, and typically these devices do not transfer data fast enough for regular operations. 

However, they work well as an external site for data-backup-and-recover solutions on a smaller, single-machine scale.

### Storage Area Network (SAN)
**Def: a dedicated network that connects compute elements to storage elements.**

Using a SAN as part of a backup solution is a good example of using technology to solve complex problems. 

**Exam Tip: NAS is a single storage device that serves files over the network to a machine. It's a simple form of external storage. A SAN, on the other hand, is a network of multiple devices designed to manage large and complex sets of data in real time at processor speed.**

### Cloud
Just as NAS and SANs can be used as locations to store data backups, so can the cloud.

Numerous cloud-based backup security vendors and products place the data storage of a backup in the cloud. 

It is important to realize that cloud storage has invaded the desktop of many users. 

Understanding the risk associated with data in these situations matters in a corporate environment because what might be convenient or seem like a good idea from a user perspective might put data at risk of disclosure. 

### Image 
An image-based backup is a specific structure of a backup file to match that of the system being backed up.

This may take more time, but it is guarenteed to backup everything including the deleted data and free space.

For critical systems, this provides a complete capture of the system as it was at the time of backup, including all nonpersistent data associate dwith the OS. 

---
## Online vs. Offline

**Def: Online backups are those that are stored in a location that is accessible via the Internet. 

This provides flexibilty in recovery by making the backup data available anywhere there is a network connection. 

**Def: Offline backups are those stored on an offline system that is not accessible via the Internet.**

Online backups have the advantage of providing geographic separation of the backups from the original system.

### Offline Storage
**Def: Backups stored in a location separate from the system being backed up.**

This can be important in regard to problems that affect an area larger than a single room. 

Events like fires, natural disasters, are common and having on-site backups  makes that a major risk.


### Distane Considerations
The distance associated with an offsite backup is a logistics problem. If you need to restore a system and the backup is stored hours away by car, that increases the recovery time.

The delay resulting from physical movement of backup tapes has been alleviated in many systems through networks that move the data at the sepeed of the network. 

---
## Nonpersistence
**Def: refers to system items that are not permanent and can change.**

An example of something that is nonpersistent is the registry in Microsoft Windows, which is a dynamic list of configuration criteria.

Nonpersistence needs to be appropriately managed, and systems that have this characteristic typically have mechanisms built in to manage this diversity.

For VMs, where the current state of the system is continually changing, and thus the image is changing, we have snapshots. 

**Exam Tip: In the event of a failure in a nonpersistent system, all data is lost. The resilience and recovery of those conditions must occur from external sources. Think memory when you turn off your computer; it must be reloaded when you restart.**

### Revert to Known State
**Def: Having the ability to recover to a known state is referred to as reverting to a known state**

Modern OSs are a great example of nonpersistance; they are regularly changing with new data, new software, new configurations, new drivers, and so on.

Reverting to a known state for OS means restoring the system to a previous point in time while leaving the files intact-- back to a condition where the OS previously worked properly.

### Last Known-Good Configuration
When you have a system without persistance, you need a means to recover to a known-good state. 

On a boot failure, Microsoft Windows can give you an option to revert to the **last known good configuration**, which is a means of reverting to a known state.

If Windows fails on three subsequent boots in sequence, it will present you with recovery options rather than trying to boot again

### Live Boot Media
One means of beginning with a known configruation and a known state is to boot to **live boot media**, which is a bootable flash drive or DVD source that contains a complete bootable image of the OS.

Using this as a means of starting in a known state is common in digital forensics investigations.

---

## High Availability
One of the objectives of security is the availability of data and processing power when an authorized user desires it.

**Def: High availability refers to the ability to maintain the availability of data and operational processing (services) despite a disrupting event.**

High availability is more than data redundancy; it requires that both data and services be available.

**Exam Tip: Fault tolerance and high availability are similar in their goals, yet they are separate in applicaiton. High availabilty refers to maintaining both data and services in an operational state, even when a disrupting event occurs. Fault tolerance is a design objective to achieve high availability should a fault occur.**


### Scalability 
**Def: A design element that enables a system to accommodate larger workloads by adding resource either making hardware stronger (scaling up) or adding additional nodes (scaling out).**

This term is commonly used in server farms and database clusters, as these both can have scalre issues with respect to workload.

**Exam Tip: Elasticity and scalability seem to be the same thing, but they are different. Elasticity is related to dynmically scaling a system with workload (scaling out), whereas scalability is a design element that enables a system both to scale up to more capable hardware and to scale out to more instances.**

### Restoration Order
Data restoration operations are designed to take an alternative copy of the data and put it back into a working system. 

Developing a restoration plan, along with an order of what needs to be restored first, second, and so on, is important because this will drive certain operations when backing up the data in the first place. 

---
## Diversity
Having a monoculture of equipment and OS can be useful for quickly replacing parts and spares but it also makes you vulnerable to common failure across the entire enterprise.

Building diversity into systems to allow parallel operations using different technologies, vendors, processes, and controls can provide a means to continue operation even during times of systems failures.

### Technologies
Employing the practice of defense in depth, it is best practice not to use a single technology, but to use several different technologies in an overlapping fashion, forcing an attacker to bypass them all to achieve their objective.

Having firewalls, ACLs, bastion hosts in a screened subnet (DMZ), and network monitoring is an example of multiple technologies designed to detect unauthorized network activity. 

### Vendors
Different vendors approach security problems with different methodologies, different toolsets, different policies and procedures. 

Having diversity in the vendors used for security prevents vendor-specific forms of single points of failure and creates a more robust set of defensive capabilities. 

### Crypto
For cryptographic solutions to work, both sides need to agree on algorithms, keys, and other parameters, but diversity can still exist in this environment.

A prime example is in the TLS cipher suite, a set of different crypto protocols, preassigned to facilitate flexibility in establishing a connection. 

### Controls
Defense in depth is a security principle where multiple layers of different security mechanisms are used to ensure catching a risk.

This is the use of diversity in controls. Modern networks employ not just firewalls but also a screened subnet (DMZ), bastion hosts, and ACLs, all working together to make bypassing the entire suite of controls nearly impossible.

**Exam Tip: Diversity is about having multiple different sets of controls to provide for risk mitigation. Diversity should be practiced in all aspects and used to enhance security. A performance-based question that considers diversity should be examined in ligh of which element is most efficient to manipulate-- technologies, vendors, crypto, or controls -- and the answer is found in the specifics of the question.**

# Questions
1. D (Difference between incremental and differential: differential requires a full backup, incremental can be full or another incremental)
2. C
3. C & D
4. A, C, D
5. C
6. C (Cloud backup solutions can be ideal for small offices)
7. D
8. B
9. A
10. B












