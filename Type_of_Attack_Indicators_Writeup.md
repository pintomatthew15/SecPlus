# Chapter 2:
# Type of Attack Indicators

**Def: The CIA triad of Security:**
		- Confidentiality
		- Integrity
		- Availability

Attacks on computer systems and netowrks can be grouped into two broad categories: 
1. Attacks on specific software (such as the OS)
2. Attacks on specific protocols or services (like HTTP, FTP,etc)
---
# Malware
**Def: software that has been designed for some nefarious purpose.**

---

## Types of Malware:

## Ransomware
**Def: form of malware that performs an action and extracts a ransom from the user**

Ransomware typically encrpyts files on a system and leaves them unusable either permenantly acting as a denial of service, or temporarily until a ransom is paid

Case Study: Crypto Locker
- First appeared in 2013
- A Trojan Horse that encrpyts files using RSA public key encrpytion
- Uses a 2048 bit RSA encrpytion making brute force out of the question

Case Study: NotPetya
- First appeared in 2017
- a ransomware worm with no decryption key
- Estimated $10 billion in damage

Case Study: WannaCry
- First appeared in 2017
- Exploited EternalBlue vulnerability in Microsoft Windows OS
- Vulnerability was exposed by group known as Shadow Brokers
- Stopped by Marcus Hutchins a hacker turned white-hat
---
## Trojans
**Def: A piece of software that appears to do one thing (and may in fact, actually do that thing) but hides some other functionality.**

Unlike a virus, a Trojan is a standalone program that must be copied and installed by the user. 

The challenge for the attacker is enticing the user to copy and run the program

Case Study: Back Orifice (BO)
- Created in 1999
- Once it is attached and the effected file is run, BO will create a way for unauthorized individuals to take over the system remotely, as if they were sitting at the console
- Designed to work with Windows based systems
- Many trojans open ports to communicate which aids in their detection
___
## Worms
**Def: Pieces of code that attempt to penetrate networks and computer systems**

Once penetration occurs, worm will create copy of itself on the system

Becauase reproduction does not rely on the attachment of the virus to another piece of code or to a file, a worm is not a virus

Worms can survive on their own

They are the tool of choice for ransomware attacks since they can spread from system to system without operator intervention

Examples:
- Sobig Worm of 2003
- SQL Slammer worm of 2003
- Code Red and Nimba 2003
- Zotob Worm 2005
---
## Potentially Unwanted Programs
**Def: designation used by security companies and antivirus vendors to identify programs that may have adverse effects on a computer's security or privacy**

They are still a form of malware and one of their common sources is from third-party distributers

Pups can exhibit undesirable characteristics such as:
- Slowing down your computer
- Displaying a ton of annoying ads
- Adding toolbars that steal space on the browser 
- Collecting private information
---
## Fileless Viruses
**Def: A virus that operates in memory never touching the filesystem. Also known as a memory based attack**

A fileless virus lives in memory and will continue to run until the device is powered down.

---
## Command & Control Servers
**Def: Servers used by hackers to control malware that has been launched against targets.**

Malware infections are seldom a single file on a single machine when an attack occurs on an enterprise
___
## Bot
**Def: a functioning piece of software that performs some task, under the control of another program**

Series of bots are controlled in groups along a netowork. This assembly is often called a botnet

Some botnets are legal while others are not 

Case Study: Zues
- Botnet that performs keystroke logging and is used primarily for the purpose of stealing banking information
- Linked to the delivery of CrptoLocker ransomware

Case Study: Conficker
- one of the most studied pieces of malware
- has a joint industry-government working group battling it
---
## Crypto-malware
**Def: malware that uses a system's resources to mine cryptocurrency** 

Theft-of-services attack where an attacker us using the CPU cycles of someone else's computer to do crypto mining
___
## Logic Bombs
**Def: A type of malicious software that is deliberately installed, generally by an authorized user.  It is a piece of code that sits dormant for a period of time until some event or date invokes its malicious payload**

Ex: malicious program that loads and runs automatically, and that periodically checks an organization's payroll or personnel database for a specific employee

If the event is a specific time or date it is called a time-bomb

They are difficult to detect because they are often installed by authorized users. 


Solution would be an active backup program

---
## Spyware
**Def: software that "spies" on users, recording and reporting on their activites**

It can record keystrokes (called keylogging) when the user logs on to specific websites 

---
## Keyloggers
**Def: a piece of software that logs all of the keystrokes that a user enters**

Keyloggers are not inherently malicious but these are the traits that make it malicious
- when it is unknown to the user
- not under the user's control
- hidden from
-  the task manager 
- against the user's interest
___
## Remote-Access Trojans (RATs)
**Def: A toolkit designed to provide the capability of covert surveillance and/or the capability to gain unauthorized access to a target system. **

They often mimic the behaviour of keyloggers and packet sniffers using automated collection of keystrokes, usernames, passwords, screenshots, browser history, emails, chat logs, and more

They also employ malware to infect systems with code that can be used to faciliate the exploitation of a target

It should be considered another form of malware, but rather than just being a program, it has an operator behind it.
___
## Rootkit
**Def: a form of malware that is specifically designed to modify the operation of the OS in some fashion to facilitate nonstandard functionality**

A rootkit can typically do whatever an OS does

Rookits modify the OS kernel and supporting functions, changing the nature of the system' s operation

They are designed to avoid detection

They can load before the OS loads acting as a virtualization layer 

There are five types of rootkits:
- FIrmware
- Virtual
- Kernel
- Libarary
- Application level

Most systems admins do not try to fix rootkit, they often restore the system to a version that was prior to the rootkit's detection
___
## Backdoors
**Def: Programs that attackers install after gaining unauthorized access to a system to ensure that they can continue to have unrestricted access to the system, even if the initial acccess method is discovered and blocked**

Common backdoors include:
- NetBus
- Back Orifice

Rootkit is a variation of a backdoor since it is established to ensure continued root access

---
# Types of Password Attacks

The most common form of authentication is the user ID and password combination

It is important that users understand what it means to have a strong password

---
## Spraying
**Def: an attack that uses a limited number of commonly used passwords and applies them to a large number of accounts**

Brute force tries to gain unauthorized access to a single account by guessing the password.

Spraying is the reverse of this, using a limited number of passwords and trying them against all the accounts.

---
## Dictionary
**Def: using a password-cracking program that uses a list of dictionary words to try to guess the password**

These programs often permit the attacker to create various rules that tell the program how to combine words to form new possible passwords

---
## Brute Force
**Def: the password-cracking program attempts all possible password combinations**

The length of the password and the size of the set of possible characters in the password will greatly affect the time a brute force attack will take

The attack on a password can take place at two levels:
- It can attack a system, where the attacker is ateempting to guess the password at a login prompt
- It can attack a list of password hashes contained in a password file
---
## Offline
**Def: offline brute force attacks can be employed to perform hash comparisons against a stolen password file**

---
## Online
**Def: When the brute force attack occurs in realtime against a system**

These tend to be noiser and are easy to see by network security monitoring 

---
## Rainbow Tables
**Def: precomputed tables or hash values associated with passwords. **

Using rainbow tables can change the search for a password from a computational problem to a lookup problem

Best defense against a table is salted hashes

A salt is merely a random set of characters designed to increase the length of the item being hashed, making the rainbow tables too big to compute

---
## Plaintext/Unencrpyted
**Def: Harvesting plaintext passwords from a system**

---
# Types of Physical Attacks
---
## Malicious Universal Serial Bus (USB) Cable
**Def: "Poisioned" cables in USB's that can deliver malware to machines**

---
## Malicious Flash Drives
**Def:  Malicous USB storage devices**

---
## Card Cloning:
**Def: If someone gets physical possession of your credit card, it is possible to copy the information on the magnetic strip, enabling one to make a clone of your card**

Smart cards made this better since chips cannot be cloned

---
## Skimming
**Def: physical devices built to intercept a credit card.**

Skim data from the card while passing it on to the legitimate reader

---
# Adversarial Artificial Intelligence (AI) and Types of AAI
**Def: the use of complex models to simulate functions of the brain**

Basically know that AI can be built to help avoid detection

When AI is developed to evade defenses it is called adversarial AI

---
## Tained Training Data for Machine Learning (ML)
**Def: tainting the trainig data is one of the attack vectors that attackers can use against ML systems**

---
## Security of Machine Learning Algorithmns
**Def: Ensure the ML algorithmn itself is crucial to the security of the system**

## Supply-Chain Attacks
**Def: attacking supply chains and let the normal build process instantiate the attack vector**

This leads to manufactures shipping PCs with pre-installed malware

---
## Cloud-Based vs. On-Premises Attacks
**Def: Ensure you define the security you desire whether you keep your secuirty in house or in the cloud**

---
# Types of Cryptographic Attacks
**Def: Attacks against the cryptographic system**

---
## Birthday Attack
**Def: a special kind of brute force attack that originates from the birthday paradox**

Most passwords are similar then we think

---
## Collision
**Def: where two different inputs yield the same output of a hash function.**

Subtle changes not visible to the user are made that result in an entirely different file

---
## Downgrade
**Def: Can downgrade the security of the TLS/SSL setup to a lower or nonexistant state**

This is possible due to TLS/SSL support of backwards compataibility

---
# Questions
1. D
2. B
3. C
4. C
5. A
6. A
7. B
8. D
9. D
10. B

