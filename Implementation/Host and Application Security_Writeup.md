# Chapter 18 
# Host and Application Security

Computing involves the processing of data using machines and applications. Ensuring that both machines and the applications that run on them are as secure as possible is an important part of an enterprise security program.

## Endpoint Protection
**Def: The concept of extending the security perimeter to the devices that are connecting to the network.**

A variety of endpoint protection solutions can be employed, including antivirus/anti-malware solutions, endpoint detection and response solutions, data loss prevention solutions, and firewalls. 

Host-based intrusion detection and prevention solutions can also be deployed at endpoints. 

### Antivirus
**Def: Antivirus (AV) products attempt to identify, neutralize, or remove malicious programs, macros, and files.**

Use of an up-to-date antivirus package is essential in the current threat environment. 

Most antivirus products combine the following approaches when scanning for viruses: 
- **Signature-based scanning**: Much like an intrusion detection system (IDS), the antivirus products scan programs, files, macros, e-mails, and other data for known worms, viruses, and malware. The antivirus product contains a virus dictionary with thousands of known virus signatures that must be frequently updated, as new viruses are discovered daily. This approach will catch known viruses but is limited by the virus dictionary--what it does not know about, it cannot catch. 
- **Heuristic Scanning (or analysis)**: Heuristic scanning does not rely on a virus dictionary. Instead, it looks for suspicious behavior--anything that does not fit into a "normal" pattern of behavior for the operating system (OS) and applications running on the system being protected. 

Heuristic scanning typically looks for commands or instructions that are not normally found in application programs, such as attempts to access a reserved memory register. 

Most antivirus products use either a weight-based system or a rule-based system in their heuristic scanning (more effective products use a mix of both)

**Def: a weight based system rates every suspicious behavior based on the degree of threat associated with that behavior.**
- If the threat threshold is passed based on a single behavior or a combination of behaviors, the antivirus product will treat the process, application, macro, and so on that is performing the behavior(s) as a threat to the system. 

**Def: a rule-based system compares activity to a set of rules meant to detect and identify malicious software.**

Some heuristic products are very advanced and contain capabilities for examining executable code, a logic flow analyzer, and a disassembler/emulator so they can "guess" what the code is designed to do and whether or not it is malicious. 

**Exam Tip: Heuristic scanning is a method of detecting potentially malicious or "virus-like" behavior by examining what a program or section of code does. Anything that is "suspicious" or potentially "malicious" is closely examined to determine whether or not it is a threat to the system. Using heuristic scanning, an antivirus product attempts to identify new viruses or heavily modified versions of existing viruses before they can damage your system.**

IDS/IPS products will look for instructions to encrypt and decrypt since the malware must have these if it wants to run alone and unattended. 

Current antivirus products are highly configurable, and most offerings will have the following capabilities:
- **Automated updates**: Antivirus downloads the latest virus signatures to keep itself up to date. Requires system to stay connected to internet. 
- **Automated scanning**: Most antivirus products scan the local system for infected files. Scanning parameters can be configured. 
- **Media scanning**: Antivirus scans removable media (USBS, etc) as soon as they are connected to or accessed by the local system. 
- **Manual scanning**: Scanning on demand 
- **E-mail scanning**: Antivirus software gives users the ability to scan incoming and outgoing messages including their attachments.
- **Resolution**: When antivirus encounters an infected file it may, quarantine the file, making it inaccessible. It may try to repair the file by removing the infection or offending code, or it may delete the infected file. 

Antivirus solutions are typically installed on individual systems, but network-based antivirus capabilities are also available in many commercial gateway products. 

**Exam Tip: Antivirus is an essential security application on all platforms. There are numerous compliance schemes that mandate antivirus deployment, including Payment Card Industry Data Security Standard (PCI DSS) and North American Electric Reliability Council Critical Infrastructure Protections (NERC CIP). 

### Anti-Malware
**Def: The name of a product designed to protect your machine from malicious software or malware.**

Today most anti-malware solutions are combined with antivirus solutions to form a single product.

One of the most dangerous forms of malware is ransomware; it spreads quickly, encrypting a user's file and locking it until a ransom is paid. 

Malware is a different threat than a virus, but defenses are typically the same. 

### Endpoint Detection and Response (EDR)
**Def: Endpoint detection and response (EDR) solutions are integrated solutions that combine individual endpoint security functions into a complete package.**

This makes updating easier, and frequently these products are designed to integrate into an enterprise-level solution with a centralized management platform. 

Common EDR elements include: antivirus, anti-malware, software patching, firewall, and DLP solutions. 

**Def: Unified endpoint management (UEM) is a newer security model that focuses on the managing and securing devices in an enterprise such as desktops, laptops, smartphones, and other devices from a single location.**

### Data Loss Prevention
**Def: Data loss prevention (DLP) solutions serve to present sensitive data from leaving the network without notice.**

Endpoint DLP monitoring allows for file activity to be reported to centralized systems, and specializes DLP offerings such as the content DLP being rolled out by Microsoft across the Microsoft 365 environment. 

These endpoint solutions do not provide complete or comprehensive coverage but taken together can achieve many of the objectives with less cost and complexity. 

### Next-Generation Firewall (NGFW
**Def: Next-generation firewalls (NGFW) act by inspecting the actual traffic crossing the fire-wall--not just looking at the source and destination addresses and ports, but also at the actual content being sent.**

As with all of these rule-driven platforms, the challenge is in maintaining appropriate rulesets that catch the desired bad traffic. 

### Host-based Intrusion Detection System (HIDS)
**Def: Host-based intrusion detection systems (HIDS) act to detect undesired elements in network traffic to and from the host.**

Because the IDS is tied to the host, it can be very specific in regards to threats to the host OS and ignore those that would have no effect. 

The disadvantage of the HIDS is that it only detects the issues; it must rely on another component, typically through some logging or reporting mechanism, to act on the threat.

### Host-based Intrusion Prevention System (HIPS)
**Def: A host-based intrusion prevention system (HIPS) is a HIDS with additional components to permit it to respond automatically to a threat condition.**

**Exam Tip: Remember that HIDS can only detect malicious activity and send alerts. HIPS, on the other hand, can detect and prevent attacks.**

### Host-based Firewall 
**Def: host-based protective mechanisms that monitor and control traffic passing in to and out of a single system.**

Designed for the end user, they typically have a configurable security policy that allows the user to determine which traffic is "good" and is allowed to pass and which traffic is "bad" and is blocked.

The decision between good and bad is decided on addresses being passed, both IP address and port combination. 

Having the firewall on the host OS provides the ability to tune the firewall to the usage pattern of the specific endpoint. 

Linux-based firewalls have built-in software-based firewalls that include TCP wrapper, ipchains, and iptables. 

- TCP wrapper: a  program that limits inbound network connections based on port number, domain, or IP address and is managed with two text files called hosts.allow and hosts.deny.
- Ipchains: rule-based software firewall that allows for traffic filtering, Network Address Translation (NAT), and redirection. Three chains used for handling network traffic:
	1. Input chain contains rules for traffic that is coming into local system.
	2. Output chain contains rules for traffic leaving local system
	3. Forward chain contains rules for traffic that was received by the local system but is not destined for the local system. 
- Iptables: The latest evolution of ipchains. Iptables uses the same three chains for policy rules and traffic handling as ipchains, but with iptables each packet is processed only by the appropriate chain. 
	- Under ipchains, each packet passes through all three chains for processing. 
	- With iptables, incoming packets are processed only by the input chain, and packets leaving the system are processed only by the output chain.

 Windows Defender Firewall is fairly configurable, it can be set up to block all traffic, to make exceptions for traffic you want to allow, and to log rejected traffic for later analysis. 

**Exam Tip: When examining endpoint security solutions, you'll see that one of the key differentiators is in what the system detects. There are single-purpose systems, such as antivirus, anti-malware, and DLP. Multipurpose systems such as EDR, firewalls, and HIDS/HIPS can look for variety of types of items. The key to all of this is in the definition of the rules for each product.**

## Boot Integrity
**Def: The characteristic of the intended hardware/firmware/software to load for the system being in compliance with the expected state.**

Having a means to ensure boot integrity is a means of assuring that the hardware, firmware, and initial loading of software are free of any tampering.

The term **trusted platform boot** includes the hardware and any associated BIOS, firmware, and hypervisor software. 

### Boot Security/Unified Extensible Firmware Interface (UEFI)
UEFI offers a solution to the problem of boot integrity, called **Secure Boot**, which is a mode that, when enabled, only allows signed drivers and OS loaders to be invoked. 

Secure boot requires specific steps, but once enabled, it blocks malware that attempts to alter the boot process. 

Secure boot enables the attestation that the drivers and OS loaders being used have not changed since they were approved for use. Secure boot is supported by Microsoft Windows and all major versions of Linux. 

Unlike legacy BIOS, UEFI BIOS is designed to work with the hardware platform to ensure that the flash memory that holds the BIOS cannot be changed without the proper cryptographic credentials. 

This forms a Root of Trust in the contents of flash memory, specifically in the UEFI BIOS. The key used sign the BIOS is controlled by the equipment manufacturer, thus preventing unauthorized changes to the BIOS. 

Secure boot operates by verifying digital signatures on all the steps in the boot processes. 

The BIOS checks the loader, and the loader checks the kernel objects, each of these being digital signature checks with the keys controlled by the manufacturer. 

### Measured Boot
**Def: Measured boot is another method of depending on the Root of Trust in starting a system, but rather than using signatures to verify subsequent components, a measured boot process hashes the subsequent processes and compares the hash values to known good values.**

The known-good hash values must be stored in a secure location and the Trust Platform Module (TPM) platform configuration registers (PCRs) comprise the secure location that is used. 

### Boot Attestation
One of the challenges in securing an OS is the myriad of drivers and other add-ons that hook into the OS and provide specific added functionality. 

Because attacks can occur at boot time, at a level below security applications such as antivirus software, they can be very difficult to detect and defeat.

**Def: Boot attestation is the reporting of the state of a system with respect to components and their relationship to the Root of Trust.**

Part of the UEFI/Root of Trust specification is the means of reporting via digital signatures of the verified integrity of the system components.

This information can be used remotely by a server to determine if an OS is correct and has the correct patch level before allowing admission to a corporate VPN, as well as for other network admission activities. 

**Exam Tip: Attestation means verifying the authenticity of a platform or device based on a trust record of evidence. Secure boot, for example ensures the system boots into a trusted configuration by having evidence of each step's authenticity verified.**

## Database
Major database engines have built-in encryption capabilities. The advantage to these encryption schemes is their ability to be tailored to the data structure, protecting the essential columns while not impacting columns that are not sensitive. Properly employing database encryption requires that the data schema and its security requirements be designed into the database implementation. The advantage is in better protection against any database compromise, and the performance hit is typically negligible with respect to other alternatives. 

### Tokenization
**Def: The process of substituting a surrogate value, called a toke, for a sensitive data element.** 

This allows the data to be processed without disclosing the sensitive value. 

### Salting
**Def: The process of adding a random element to a value before performing a mathematical operation like hashing.**

This adds randomization and prevents identical original values from being hashed into an identical digest.

### Hashing
**Def: Hashing is a mathematical method of reducing a data element to a short form that is not reversible to the original form.**

Hashing sensitive data has the effect of creating a token, and hashes can be used as tokens in data structures.

**Exam Tip: Know the differences between tokenization, salting, and hashing. Tokenization is the process of substituting a surrogate value, called a token, for a sensitive data element. Salting is the process of adding a random element to a value before performing a mathematical element like hashing. Hashing is a mathematical method of reducing a data element to a short form that is not reversible to the original form.**

## Application Security
Applications are the reason for the computer equipment; it is the applications that do the work. 

Applications come in two classes: commercial software and software that is built in-house. In-house is much less likely to have a serious security review as part of their build and are more likely to have vulnerabilities. 

### Input Validations
The avenue for an attacker to access an application is via its inputs. Having a stringent and comprehensive validation of inputs prior to processing them is essential to filter out specific attacks. 

Check everything before use. 

**Exam Tip: Proper input validation prevents many different attack types by ensuring that input is properly formulated.**

### Secure Cookies
Cookies are text files sent with every request to a website. 

An attribute in the cookie called the **secure attribute**, when set, instructs the browser and server to only transport the cookie over HTTPS channels. 

If the cookie is not sent securely, it can be read in plaintext. 

### Hypertext Transfer Protocol (HTTP) Headers
Browsers are the window to many applications, acting as a means of providing user input and receiving system responses. The HTTP has a large number of options and features that can be manipulated via a browser, to improve the usability of a site, but in some manipulative cases, they can result in security risks. 

The website can exert some control over browser behaviors via response headers that convey directives to the browser. 

Using a security-related set of response headers can alleviate such risks as protocol downgrade attacks, clickjacking, cookie hijacking and other attacks. 

An example is the HTTP Strict Transport Security (HSTS) directive:
```
Strict-Transport-Security: max-age 3600; includeSubDomains
```

This directive declares that browsers should only interact via HTTPS, never HTTP, with a max time of 3600 seconds, and that all subdomains are included in this directive.

### Code Signing 
An important factor in ensuring that software is genuine and has not been altered is a method of testing software integrity. 

**Def: Code signing involves applying a digital signature to code, providing a mechanism where the end user can verify the code integrity.**

In addition to verification, digital signatures provide evidence as to the source of the software.

The digital signature contains the hash of the code, allowing its integrity to be verified at any time. 

**Exam Tip: Code signing ensures that code has not been changed since last signed.**

### Allow List
**Def: Lists of applications that are permitted to run on the OS.**

Allow listing is easier to employ from the aspect of the identification of applications that are allowed to run--hash values can be used to ensure the executables are not corrupted.

Issue is in determining the amount of potential applications that run on a typical machine. 

### Block List/Deny List
**Def: A list noting which applications should not be allowed to run on the machine.**

This is basically a permanent "ignore" or "call block" type of capability. Blocking in this fashion is difficult to use against dynamic threats, as the identification of a specific application can easily be avoided through minor changes.

**Exam Tip: An allow list is a list of approved applications. A block/deny list is a list of applications that should not be allowed to run.**

### Secure Coding Practices
Application security begins with code that is secure and free of vulnerabilities. Unfortunately, all code has weaknesses and vulnerabilities, so instantiating the code in a manner that has effective defenses to prevent the exploitation of vulnerabilities can maintain a desired level of security. 

There are numerous individual elements in a software development lifecycle methodology (SDLM) that can assist a team in developing secure code. 

The two main enumerations of common software errors are the Top 25 list, maintained by MITRE, and the OWASP Top Ten list for web applications. 

Because the causes of common errors do not change quickly, these lists are not updated every year. 

### Static Code Analysis
**Def: When code is examined without being executed.** This analysis can be performed on both source code and object code bases. 

The term source code is typically used to designate the high-level language code, although, technically, source code is the original code base in any form, from high-level language to machine code.

Static code analysis is frequently performed using automated tools. These tools are given a variety of names but are commonly called static code analyzers or source code analyzers. 

#### Manual Code Review
**Def: Manual Code review can be done in one of two fashions: either directed or undirected.**

In an undirected review, a programmer examines the code to see what is does and how it does it. Like proofreading a paper

A directed review is one where the code author walks through the code, explaining each line to the rest of the team. 

### Dynamic Code Analysis 
**Def: Dynamic code analysis is performed while the software is executed, either on a target system or an emulated system.** 

The system is fed specific test inputs designed to produce specific forms of behaviors. 

Dynamic analysis requires specialized automation to perform specific testing. Among the tools available are dynamic test suites designed to monitor operations for programs that have a high degree of parallel functions, thread-checking routines to ensure mutlicore processors and software are managing threads correctly, and programs designed to detect race conditions and memory-addressing errors.

**Exam Tip: Static code analysis is when the code is examined without being executed. Dynamic code analysis analyzes the code during execution.**

### Fuzzing
**Def: A brute force method of addressing input validation issues and vulnerabilities.** 

The basis for fuzzing a program is the application of large numbers of inputs to determine which inputs cause faults and which ones might be vulnerable to exploitation. 

The vast majority of browser errors are found via fuzzing. Fuzz testing works well in known environments, unknown environments, and partially known environments, as it can be performed without knowledge of the specifics of the application under test. 

## Hardening 
The key management issue behind running a secure system setup is to identify and the specific needs of a system for its proper operation and enable only the items necessary for those functions. 

Keeping all other services and users off the system improves system throughput and increases security. 

Reducing the attack surface area associated with a system reduces the vulnerabilities now and in the future as updates are required. 

### Open Ports and Services
Services on machines are accessed through neither TCP or UDP ports. For services that are being used, it is important that the port be open and not blocked by a firewall, which would stop the traffic to the service. 

But for security, any service that is not going to be used on a system should be disabled. 

Blocking unneeded open ports and disabling unused services are both easy and should be applied to virtually every machine. This is one of the cheapest defenses and should be one of the first applied because of the breadth of issues it heads off. 

Attackers use active reconnaissance and tools such as Nmap to scan and view open ports. As a security analyst, you can use the same tools, including netstat, to quickly ascertain listening ports and active connections. These should all be mapped to required services or else turned off and blocked. 

**Exam Tip: Any service that is not going to be used on a system should be disabled, and any unnecessary ports should be blocked by the firewall.**

### Registry
**Def: The registry in Microsoft Windows systems acts as a repository of all information related to configuration.**

The registry contains configuration information for the OS and applications on the system.

The Windows Registry is not a structure to be casually modified or changed. One security task you can do is periodically making a backup of the Registry to a secure location, as this will be important if something alters the current Registry. 

Registry-editing tools can also be limited by group policies under a domain-based system.

### Disk Encryption
Hardening a system also means protecting the information in the system. **Disk Encryption** can provide data protection even if the disk is removed from one system and placed in another. 

Having the data encrypted on the disk renders it unusable without hte proper keys. The best solutions for encryption today are built in to the operating system and use hardware encryption on the disk itself and store the keys in the TPM PCR. 

This makes the data easy for the OS to access when properly booted and logged in to, yet nearly impossible to bypass, even by removing the disk and putting it in another machine. 

### OS
Many different systems have the need for an operating system (OS). Hardware in networks requires an operating system to perform the networking function. 

Servers and workstations require an OS to act as the interface between applications and the hardware. 

Specialized systems such as kiosks and appliances, both of which are forms of automated single-purpose systems, require an OS between the application software and hardware. 

Servers require an OS to bridge the gap between the server hardware and the applications being run. Currently, server OSs include Microsoft Windows Server, many flavors of Linux, and more and more VM/hypervisor environments. 

The OS on a workstation exists to provide a functional working space for a user to interact with the system and its various applications. 

Appliances are standalone devices, wired into the network and designed to run an application to perform a specific function on traffic. 

Kiosks are standalone machines, typically operating a browser instance on top of a Windows OS. 

The OS on a kiosk needs to be able to be locked down to minimal functionality, have elements such as automatic login, and provide an easy way to construct applications. 

No matter what the OS, updates and patches should be applied where and when possible. Any nonessential services and software should be disabled and/or removed. Unnecessary open ports should be blocked or closed. All users should implement strong passwords and change them on a regular basis. Access policies and permissions should be implemented based on least privilege. 

### Patch Management 
**Def: The process used to maintain systems in an up-to-date fashion, including all required patches.**

Every OS, from Linux to Windows, requires software updates, and each OS has different methods of assisting users in keeping their systems up to date. 

In Windows 10, forward, Microsoft has adopted a new methodology treating the OS as a service and has dramatically updated its servicing model. 
	- Windows 10 now has a twice-per-year feature update release schedule, aiming for March and September, with an 18-month servicing timeline for each release.
How you patch a Linux system depends a great deal on the specific version in use and the patch being applied. 

Regardless of the method you use to update the OS, it is critically important to keep systems up to date. New security advisories come out every day, and while a buffer overflow may be a "potential" problem today, it will almost certainly become a "definite" problem in then near future. 

Vendors typically follow a hierarchy for software updates:
- **Hotfix**: This term refers to a small software update designed to address a specific problem, such as a buffer overflow in an application. Hotfixes are typically developed in reaction to a discovered problem and are produced and released rather quickly.
- **Patch**: This term refers to a more formal, larger software update that can address several or many software problems. Patches often contain enhancements or additional capabilities as well as fixes for known bugs. Patches are usually developed over a longer period of time.
- **Service Pack**: This refers to a large collection of patches and hotfixes rolled into a single, rather large package. Service packs are designed to bring a system up to the latest known-good level all at once, rather than requiring the user or system administrator to download dozens or hundreds  of updates separately. 

### Third-Party Updates
Maintaining up-to-date software is a problem that scales poorly. 

The key to solving this is to ensure that:
1. The solution chosen covers the apps you use
2. You properly enroll the apps with the program so it knows what to update

### Auto-Update
Updating software is a maintenance task that sits near the bottom of the everyone's list. 

Using an auto-update function to keep software up to date solves more problems than it creates. Many software vendors now equip their software with an auto-update function that calls home, gets the update, and installs it automatically. 

## Self-Encrypting Drive (SED)/Full Disk Encryption (FDE)
**Def: Self-encrypting drives (SEDs) and full disk encryption (FDE) are methods of implementing cryptographic protection on hard drives and other similar storage media with the express purpose of protecting the data, even if the drive is removed form the machine**

The use of modern cryptography, coupled with hardware protection of the keys, makes this vector of attack much more difficult. In essence, both of these methods offer a transparent, seamless manner of encrypting the entire hard drive using keys that are only available to someone who can properly log in to the machine. 

### Opal 
FDE and SED began as software-only proprietary solutions, but a hardware-based standard called Opal as been created.

Developed by the trust Computing Group (TCG Opal is used for applying hardware-based encryption to mass storage devices, hard drives, SSD, and optical drives. 

Having a standard has the advantage of interoperability between vendors and can be OS independent. 

The encryption/decryption keys are stored in the hard drive controller and are never loaded into system memory, keeping them safe from attack. 

**Exam Tip: SED, FDE, and Opal are methods of implementing encryption on hard drives.**

## Hardware Root of Trust
**Def: The concept that if one has trust in a source's specific security functions, this layer can be used to promote security to higher layers of a system.**

Because roots of trust are inherently trusted, they must be secure by design. This is usually accomplished by keeping them small and limiting their functionality to a few specific tasks. 

Examples of roots of trust include TPM chips in computers and Apple's Secure Enclave coprocessor in its iPhones and iPads. 

With respect to UEFI and Secure Boot, previously covered in this chapter, the term **Root of Trust** refers to a condition by which the hardware and BIOS work together to ensure the integrity of the BIOS and all subsequent software and firmware loads.

## Trust Platform Module (TPM)
**Def: Trust Platform Module (TPM) is a hardware solution on the motherboard, one that assists with key generation and storage as well as random number generation.**

When the encryption keys are stored in the TPM, they are not accessible via normal software channels and are physically separated from the hard drive or other encrypted data locations. 

The TPM platform also supports other security functions through a series of protected storage locations called platform configuration registers (PCRs). 

## Sandboxing 
**Def: The quarantine or isolation of a system from its surroundings.**

It has become standard practice for some programs with an increased risk surface to operate within a sandbox, limiting the interaction with the CPU and other processes, such as memory. 

This works as a means of quarantine, preventing problems from getting out of the sandbox and onto the OS and other applications of the system. 

Virtualization can be used as a form of sandboxing with respect to an entire system. You can build an virtual machine, test something inside the VM, and, based on the results, make a decision with regard to stability or whatever concern was present. 

# Chapter Questions
1. D
2. D
3. A, C 
4. B (Allow lists are ideally suited for single-purpose servers, as the applications that are allowed to execute are known in advance.)
5. C
6. A, B
7. B, D (Review fuzzing)
8. C
9. D
10. A (The windows registry is where configuration parameters for the OS and applications are stored. It is not associated with the Root of Trust, as it is not even accessible during the establishment of this trust chain.)















  