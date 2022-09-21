# Chapter 26
# Tools/Assess Organizational Security

Competency in performing many security functions involves the use of tools.
- The number, scope, and details for the tools used in the security industry could fill an entire book, but a basic understanding of a core set of tools is important. 

**EXAM TIP: This chapter is filled with hands-on commands that need be used to be learned. The path to learning these commands is in using them. This is not a read-and-remember chapter, but rather a do-and-learn one. Linux commands can be a bit troublesome for some, so practice is advised.**

## Network Reconnaissance and Discovery
Networks are like most infrastructure, you never see or care about it until it isn't working. 
- A wide range of tools can be used to permit you to see the inner workings of a network, and they are covered in the sections that follow.

### tracert/traceroute
**Def: The tracert command is a Windows command for tracing the route that packets take over the network.**
- The tracert command provides a list of the hosts, switches, and routers in the order in which a packet passes through them, providing a trace of the network route from source to target.
- As tracert uses ICMP, if ICMP is blocked, tracert will fail to provide information.
- On Linux and macOS systems, the command with similar functionality is traceroute

**EXAM TIP: The tracert and traceroute commands display the route a packet takes to a destination, recording the number of hops along the way. These are excellent tools to use to see where a packet may get hung up during transmission.**

### nslookup/dig
**Def: The Domain Name System (DNS) is used to convert a human-readable domain name into an IP address.**
- This is not a single system, but rather a hierarchy of DNS servers, from roots servers on the backbone of the Internet, to copies at your Internet service provider (ISP), your home router, and your local machine, each in the form of a DNS cache.
- To examine a DNS query for a specific address, you can use the nslookup command.

At times, nslookup will return a nonauthoritative answer. This means the result is from a cache as opposed to a server that has an authoritative answer, such as from a DNS server. 

While nslookup works on Windows systems, the command **dig**, which stands for Domain Information Groper, works on Linux systems. 
- One difference is that dig is designed to return answers in a format that is easy to parse and include in scripts, which is a common trait of Linux command-line utilities.

### ipconfig/ifconfig
**Def: Both ipconfig (Windows) and ifconfig (Linux) are command-line tools to manipulate the network interfaces on a system.**

They have the ability to list the interfaces and connection parameters, alter parameters, and release/renew connections.
- One of the first tools to use if you feel like you're having network issues

The ip command in Linux is used to show and manipulate routing, devices, policy routing, and tunnels. 
- The ipconfig command is an important command for troubleshooting because it dispalys current TCP/IP configurations on a local system.

### nmap
**Def: Nmap is a free, open source port scanning tool developed by Gordon Lyon and has been the standard network mapping utility for Windows and Linux since 1999.**
- The **nmap** command is the command to launch and run the nmap utility. 
- Nmap is used to discover what systems are on a network and the open ports and services on those systems. 
- It also has a GUI interface called Zenmap.
- Works on MS, macOS, and Linux and is one of the top 10 tools used by system administrators on a regular basis.

### ping/pathping
**Def: The ping command sends echo request to a designated machine to determine if communication is possible.**
- The syntax is ```ping [options] targetname/address```
- The options include items such as name resolution, how many pings, data size, TTL counts, and more.

Pathping is a TCP/IP-based utility that provides additional data beyond that of a ping command. 
- Pathping will first display your path results as if you were using tracert or traceroute. 
- Pathping then calculates loss information

### hping
**Def: Hping is a TCP/IP packet creation tool that allows a user to craft raw IP, TCP, UDP, and ICMP packets from scratch.**
- This tool provides a means of performing a wide range of network operation; anything that you can do with those protocols can be crafted into a packet. 
- The current version is hping3, and it is available on most operating systems, including Windows and Linux. 

Like all Linux commands, hping can be programmed in Bash scripts to achieve greater functionality. 
- Outputs can be piped to other commands
- Hping also works with an embedded Tcl scripting functionality, which further extends its usefulness for system administrators. 

### netstat
**Def: The netstat command is used to monitor network connections to and from a system.** The following are examples of how you can use netstat:
- **nestat -a Lists all active connections and listening ports**
- **netstat -at Lists all active TCP connections**
- **netstat -an Lists all active UDP connections**

The netstat command is available on Windows and Linux, but availability of certain netstat command switches and other netstat command syntax may differ from operating system to operating system. 

**EXAM TIP: The netstat command is useful for viewing all listening ports on a computer and determining which connections are active.**

### netcat
**Def: Netcat is the network utility designed for Linux environments.**
- It has been ported to Windows but is not reguarly used in Windows environments.
- The actual command to invoke netcat is **nc -options -address**

The netcat utiltiy is the tool of choice in Linux for reading from and writing to network connections using TCP or UDP. 
- Like all Linux command-line utilities, it is designed for scripts and automation
- Netcat has a wide range of functions; it acts as a connection to the network can act as a transmitter or a receiver, and with redirection it can turn virtually any running process into a server.
- It can listen on a port and pipe the input it receives to the process identified

**EXAM TIP: You should know what each of these tools looks like when being used. If presented with output from one of the tools ,you should be able to identify the tools that was used and what action the tool is performing.**


## IP Scanners
**Def: IP scanners scan IP networks and report the status of an IP address.**

### arp
**Def: The arp command is designed to interface with the operating system's Address Resolution Protocol (ARP) caches on a system.**

When moving packets between machines, a device sometimes needs to know where to send a packet using the MAC or layer 2 address. ARP handles this problem with four basic message types:
1. **ARP request**: "Who has this IP address"
2. **ARP reply:** "I have that IP address, my MAC address is..."
3. **Reverse ARP (RARP) request:** "Who has this MAC address"
4. **RARP reply:** "I have that MAC address; my IP address is..."

These messages are used in conjunction with a device's ARP table, where a form of short-term memory associated with these data elements resides.
- Commands are used as a simple form of lookup

The ARP command allows a system administrator the ability to see and manipulate the ARP cache on a system. 
- This way, they can see if entries have been spoofed or if other problems, such as errors, occur.

### route
**Def: The route command works in Linux and Windows systems to provide information on current routing parameters and to manipulate these parameters.**
- It can both list and modify the current routing table

### curl
**Def: Curl is a tool designed to transfer data to or from a server, without user interaction.**
- It supports a long list of protocols and acts like a Swiss army knife for interacting with a server.
- Originally designed to interact with URLs, curl has expanded into a jack-of-all-trades supporting numerous protocols.
- Works on both Linux and Windows systems

An example of using curl to simulate a GET request for a website URL:
```
curl https://www.example.com
```

### theHarvester
**Def: theHarvester is a Python-based program designed to assist penetration testers in the gathering of information during the reconnaissance portion of a penetration test.
- This is a useful tool for exploring what is publicly available about your organization on the Web.
- Designed for Linux and included as part of Kali and other penetration testing. 

### sn1per
**Def: Sn1per is a Linux-based tool used by penetration testers.**
- Sn1per is an automated scanner designed to collect a large amount of information while scanning for vulnerabilities
- It runs a series of automated scripts to enumerate servers, open ports, and vulnerabilities, and it's designed to integrate with the penetration testing tool Metasploit.
- Sn1per goes further than just scanning; it can also brute force open ports, brute force subdomains and DNS systems, scan web application for common vulnerabilities, and run targeted nmap scripts against open ports as well as targeted Metasploit scans and exploit modules.
- This tool suite comes as a free community edition, with limited scope, as well as an unlimited professional version for corporations and penetration testers. 

### Scanless
**Def: Scanless is a command-line utility to interface with websites that can perform port scans as part of a penetration test.**
- When you use this tool, the source IP address for the scan is the website, not your testing machine
- Written in Python, with a simple interface, scanless anonymizes your port scans. 

### dnsenum
**Def: Dnesnum is a Perl script designed to enumerate DNS information.**
- Dnsenum will enumerate DNS entries, including subdomains, MX records, and IP addresses
- IT can interface with Whois, a public record that identifies domain owners, to gather additional information.
- Dnesum works on Linux distributions that support Perl.

**EXAM TIP: DNS enumeration can be used to collect information such as user names and IP addresses of targeted systems.**

### Nessus
**Def: Nessus is one of the leading vulnerability scanners in the marketplace.**
- It comes in a free version, with limited IP address capability, and fully functional commercial versions.
- Nessus is designed to perform a wide range of testing on a system, including the use of user credentials, patch level testing, common misconfigurations, password attacks, and more.
- Designed as a full suite of vulnerability and configuration testing tools, Nessus is commonly used to audit systems for compliance to various security standards such as PCI DSS, SOX, and other compliance schemes. 
- Nessus free version was the original source of the Open VAS fork, which is a popular free vulnerability scanner. 

### Cuckoo
**Def: Cuckoo is sandbox used for malware analysis.**
- Cuckoo is designed to allow a means of testing a suspicious file and determining what it does. 
- It is open source, free software that can run on Linux and Windows. 
- Cuckoo is a common security tool used to investigate suspicious files, as it can provide reports on system calls, API calls, network analysis, and memory analysis. 

**EXAM TIP: The Sec+ exam will test your knowledge of the network reconnaissance and discovery tools previously detailed. Practice with each of them and, given a scenario, be able to identify and the appropriate tool.**

## File Manipulation
In computer systems, most information can be represented as a file. Files are files, as are directories and even entire storage systems. The concept of a file is the basic interface to information. This next section looks at a bunch of tools used to manipulate files in Linux systems.

### head
**Def: Head is a utility designed to return the first lines of a file.**
- A common option is the number of lines one wishes to return. For example, **head -5** returns the first five liens of a file.

### tail
**Def: Tail is a utility designed to return the last lines of a file.
- **tail -5** returns the last five lines of a file

### cat
**Def: Cat is a Linux command, short for concatenate, that can be used to create and manipulate files.**
- It can display the contents of a file, handle multiple files, and can be used to input data from stdin, which is a stream of input, to a file if the file does not exist. Here is an example:
- ``` #cat textfile.txt```
- The cat command can be piped through **more** or **less** to limit the scrolling of long files:
- ```cat textfile.txt | more```

If you need line numbers in the output, you can add the **-n** option. The output can be piped through various other Linux commands, providing a significant manipulation capability. For instance, you can combine four files and sort the output into a fifth file, like so:
``` cat textfile1.txt textfile2.txt textfile3.txt textfile4.txt | sort > textfile5.txt ```

### grep 
**Def: Grep is a Linux utility that can perform patter-matching searches on file contents.**
- It can count number of matches and it can find lines with matching expressions, either case sensitive or case insensitive. 
- It can use anchors (matching based on beginning or ending of a word), wildcards, and negative searches. 

### chmod
**Def: Chmod is the Linux command used to change access permissions of a file. The general form of the command is:
``` chmod <options> <permissions> <filename> ```

Permissions can be entered either in symbols or octal numbers. An example:
``` 
chmod u=rwx,g=rx,o=r <filename>
chmod 754 <filename>
```

### Logger
**Def: The Linux command logger is how you can add log file information to /var/log/syslog.**
- The logger command works from the command line, from scripts, or from other files, thus providing a versatile means of making log entries.
- The syntax is simple:

``` logger <message to put in the log>```

This command will put the text in the option of the syslog file.

**EXAM TIP: Know the purpose of the Linux file manipulation commands. Given a scenario, be prepared to implement the appropriate command.**

## Shell and Script Environments
One of the most powerful aspects of the Linux environment is the ability to create shell scripts. By combining a series of functions, and through the use of redirecting inputs and outputs, one can do significant data manipulation. 

### SSH
**Def: Secure Shell (SSH) is a cryptography secured means of communicating and managing a network over an unsecured connection.**
- It was originally designed as a replacement for the plaintext protocols of telnet and other tools. 
- When remotely accessing a system, it is important not to use a plaintext communication channel.

**EXAM TIP: SSH is a cryptographically secured means of communicating and managing a network. SSH uses port 22 and is the secure replacement for Telnet.**

### PowerShell
**Def: PowerShell is a MS Windows-based task automation and configuration management framework, consisting of a command-line shell and scripting language.**
- PowerShell is built on top of the .NET Common Language Runtime (CLR) and accepts and returns .NET objects.
- The commands used in Powershell are called cmdlets, and they can be combined to process complex tasks.
- PowerShell can be run from a PowerShell Console prompt, or through the Windows Powershell Integrated Scripting Environment (ISE).

**EXAM TIP: PowerShell is a powerful command-line scripting interface. PowerShell files use the .ps1 file extension.**

### Python
**Def: Python is a computer language commonly used for scripting and data analysis tasks facing system administrators and security personnel.**
- Speed is not a strong attribute because it can be interpreted
- Must learn language for most security professsionals

**EXAM TIP: Python is a general-purpose computer programming language that uses the file extension .py**

### OpenSSL
**Def: OpenSSL is a general-purpose cryptography library that offers a wide range of cryptographic functions on Windows and Linux systems.**
- Designed to be a full-featured toolkit for TLS and SSL protocols, it provides so much more for real-world daily challenges

OpenSSL can perform the following tasks in either scripts or programs, offering access to cryptographic functions without having to develop the code:
- Work with RSA and ECDSA keys
- Create certificate signing requests (CSRs)
- Verify CSRs
- Create certificates
- Generate self-signed certificates
- Convert between encoding formats and container formats
- Check certificate revocation status
- And more

One can view OpenSSL as a Swiss army knife for all things involving cryptography functions.

## Packet Capture and Replay
Computers communicate and exchange data via network connections by way of packets. Software tools that enable the capturing, editing, and replaying of the packet streams can be very useful for a security professional. 
- The tools in this section provide this capability. They can operate either on live network traffic or recorded traffic in the form of packet capture (PCAP) files.

### Tcpreplay
**Def: Tcpreplay is the name for both a tool and a suite of tools.**
- They are a group of open-source tools for editing and replaying previously captured network traffic.
- As a tool, it replays a PCAP file on a network. 

### Tcpdump
**Def: The tcpdump utility is designed to analyze network packets either from a network connection or a recorded file.**
- You can use tcpdump to create files of packet captures, called PCAP files, and perform filtering between input and output, making it a valuable tool to lessen data loads on other tools. 

### Wireshark
**Def: Wireshark is the gold standard for graphical analysis of network protocols.**
- With dissectors that allow the analysis of virtually any network protocol, this tool can allow you to examine individual packets, monitor conversations, carve out files, and more. 

**EXAM TIP: When you're examining packets, the differentiator is what do you need to do. Wireshark allows easy exploration. Tcpdump captures packets into PCAP files, and tcpreplay has a suite of editing tools.**

## Forensics 
**Def: Digital forensics is the use of specific methods to determine who did what on a system at a specific time, or some variant of this question.**

### dd
**Data dump (dd) is a Linux command-line utility used to convert and copy files.**
- dd can be used for tasks such as backing up the boot sector of a hard drive, obtaining a fixed amount of random data, or copying (backing up) entire disks.
- Here's how to backup an entire hard disk:
```# dd if = /dev/sda of = /dev/sdb```

Here **if** represents the input file and **of** represents output file. Therefore, the exact copy of /dev/sda will be available in /dev/sdb.

Here's how to create an image of a hard disk:
```dd if = /dev/hda of = ~/hdadisk.img```

When doing a forensics data capture, rather than taking a backup of the hard disk, you should create an image file of the hard disk and save it on another storage device. There are many advantages to backing up your data to a disk image, one being the ease of use.
- Image files contain all the information on the associated source, including unused and previously used space.

### memdump
**Def: Linux has a utility program called memory dumper, or memdump, which dumps system memory to the standard output stream, skipping over any holes in memory maps.**
- By default, the program dumps the contents of physical memory (/dev/mem). 
- The output from memdump is in the form of a raw dump.
- Because running memdump uses memory, it is important to send the output to a location that is off the host machine being copied, using a tool such as netcat.

### WinHex
**Def: WinHex is a hexadecimal file editor.**
- It provides a plethora of tools for viewing, editing, and converting files
- As a native file read/hex editor, it can examine specific application files without invoking the application and changing the data.
- WinHex is a commercial program that is part of the X-ways forensic suite, which sis a comprehensive set of digital forensic tools.

### FTK Imager
**Def: FTK Imager is the company AccessData's answer to dd.** 
- Free to use and designed to capture an image of a hard drive in a forensic fashion.
- FTK Imager retains file system metadata and creates a log of the files copied. 

### Autopsy
**Def: Autopsy is the open source answer for digital forensic tool suites.** 
- It runs on Windows and offers a comprehensive set of tools that can enable network-based collaboration and automated, intuitive workflows.

It has case management tools to support the functions of case analysis and reporting, including managing timelines.

**EXAM TIP: Be able to identify the various digital forensics tools dicussed and know the purpose of each. For example, know that dd is a Linux command-line utility used to convert and copy files, whereas FTK Imager is a commercial program designed to capture an image of a hard drive (or other device) in a forensic fashion.**

## Exploitation Frameworks
**Def: Exploitation frameworks are toolsets designed to assist hackers in the tasks associated with exploiting vulnerabilities in a system.**
- These frameworks are important because the explication path typically involves multiple steps, all done in precise order on a system to gain meaningful effect.
- Metasploit is most commonly used

## Password Crackers
**Def: Software used by hackers to find weak passwords.**
- Work using dictionary lists and brute force. 

## Data Sanitization
**Def: Data Sanitization tools are tools used to destroy, purge, or otherwise identify for destruction specific types of data on systems.**
- Tools such as Identity finder excel at this aspect of data sanitization. As with all tools, it is not the tools that provides the true value but rather the processes and procedures that ensure the work is done, and done correctly when required.

# Questions 
1. B
2. D
3. C
4. A, C
5. D
6. A
7. A
8. A, B, C, D
9. D
10. A

100! 
