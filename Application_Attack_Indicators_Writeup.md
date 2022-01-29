# Chapter 3:
# Application Attack Indicators
---

# Types of Attack Indicators

## Privilege Escalation
**Def: when the attacker exploits vulnerabilities that enable them to achieve root- or admin-level access.**

This is a major step in the attack chain

One way to achieve priviledge escalation is to use existing priviledges to perform an action that steals a better set of credentials.
- You can obtain better credentials using a sniffer to grab credentials or getting the Windows Security Account Manager (SAM)
- You can also grab the Linux/Unix etc/passwd file

Another method is by exploiting vulnerabilities or weaknessess in processes that are running with escalated privileges. 
- This is typically accomplished by enjecting malicious code into them

---
## Cross-Site Scripting (XSS)
**Def: An attack that exploits weak user input validation allowing users to include entire scripts as part of their input. This is also one of the most common web attack methodologies. **

Three Different Types of XSS:
1. **Non-persistent XSS attack:** The injected script is not persisted or stored but rather is immediately executed and passed back via the the webserver.

2. **Persistent XSS attack:** The script is permanently stored on the web server or some back-end storage. This allows the script to be used against others who log into the system.

3. **DOM-based XSS attack**: The script is executed in the browser via the Document Object Model (DOM) process as opposed to the web server.

Results in a wide range of consequences such as: theft of authentication information, session hijacking, deploying hostile content, impersonation, phishing or stealing sensitive information

Best defense is the use of anti-XSS libaries to strip scripts from the input sequences. Input validation is extremely helpful.

---
## Types of Injection Attacks
**Def: The manipulation of input, resulting in a SQL statement that is different from the statement the designer intended.**

Extensible Markup Language (XML) injection attacks and Light-weight Directory Access Protocol (LDAP) are used to store data, this can give an attacker access to data against business rules

---
### Structured Query Language (SQL)
**Def: a form of code injection aimed at any SQL-based database, regardless of vendor**

Example: Function takes the user-provided inputs for username and password and substitutes them in a **where** clause of an SQL statement with the express purpose of changing the **where** clause into one that gives a false answer to the query

Consider the desired SQL statement as follows:

`select count (*) from users_table where username = ' JDoe' and password = 'newpass' `

The values JDoe and newpass are provided by the user and are simply inserted into the stringsequence. Though seemingly safe functionally, this can be easily corrupted by using the sequence

` ' or 1=1 -`

which changes the where clause to one that returns all records as shown here:

` select count (*) from users_table where username = ' JDoe' and password = ' ' or 1=1 -'   `

The addition of the **or** clause, with an always true statement and the beginning of a comment line to block the trailing single qupte, alters the SQL statement to one in which the **where** clause is rendered inoperable
- This results in a data breach since the where clause returns all records

The primary defense against SQL injection attacks are stored procedures. 
- They are precompiled methods implemented within a database engine
- They isolate user input from the actual SQL statement being executed

Two main steps for testing SQL injection vulnerability
1. Confirm the system is vulnerable, this can be done by using various inputs to test whether an input variable can be used to manipulate the SQL command
2. Use the error message information to attempt to perform an actual exploit against the database
---
### Dynamic-Link Library (DLL)
**Def: A piece of code that can add functionality to a program through the inclusion of library routines linked at runtime**

DLL Injection is the process of adding to a program, at runtime, a DLL that has a specific function vulnerability that can be capitalized on by the attacker. 

Microsoft Office uses many DLLs

---
### Lightweight Directory Access protocol (LDAP)
**Def: When an application constructs an LDAP request based on user input, a failure to validate the input can lead to a bad LDAP request**

Its on the application layer of the internet protocol suite (like HTML, FTP)

---
### Extensible Markup Language (XML)
**Def: XML injection can be used to infect an XML-based system.**

XML that is maliciously altered can affect changes in configurations, changes in data streams, changes in outputs-- all form the injection

---
Recap: The four kinds of injection attacks:
	1. SQL
	2. DLL
	3. LDAP
	4. XML

---
## Pointer/Object Dereference
**Def: a pointer is a construct that refers to the memory location that holds the variable, as opposed to a variable, where the value is stored directly in the memory location.**

The act of dereferencing a pointer now changes the meaning of the object to the contents of the memory location, not the memory location as identified by the pointer. 

It is called pointer/object dereference becuase dereferencing the pointer will also dereference the object 

---
## Directory Traversal
**Def: When an attacker uses special inputs to circumvent the directory tree structure of the filesystem.**

Can be masked using the enocding of input streams

___
## Buffer Overflow
**Def: "Nearly half of all exploits of computer programs stem histrorically from some form of these buffer overflows"**

The input buffer that holds the program input is overridden with data that is larger than the buffer

This is almost allways due to poor code and issues with different languages

They are input validation attacks, designed to take advantage of input routines that do not validate the length of inputs

---
## Race Condition
**Def: An error condition that occurs when the output of a function is dependent on the sequence or timing of the inputs. It becomes a bug when the inputs do not happen in the order the programmer intended**

The term relates to the idea of multiple inputs racing each other to influence the output first.

Occurs when timing or sequence of processes is important for the program to operate properly

Race conditions are defined by race windows, a period of opportunity when concurrent threads can compete in attempting to alter the same object.
- Identifying the race windows is the first step to avoid race conditions

Once these windows are identified its important to make sure that threads are not called concurrently, this is known as the property of mutual exclusion

Race conditions can be combined with reference counters, kernel locks, and thread synchronization
- reference counters: structures in the kernel that detail whether or not a resource is actively being used at the current moment.
- kernel locking: earlier method but caueses performance issues
- thread synchronization prevents threads from accessing the shared data at the same time.
---
## Time of Check/Time of Use
**Def: an attack that takes advantage of a separation between the time a program checks a value and when it uses the value, allowing an unauthroized manipulation that can affect the outcome of a process**

This develops a race condition

---
## Improper Error Handling
**Def: Not properly establishing error messages that may give attackers more data than prefered**

Some errors give attackers information about the machine they are trying to exploit

---
## Improper Input Handling
**Def:  when users manipulate input on software or other mediums that returns results that are unexpected or not normal**

It is the number 1 cause of software vulnerabilities

Input handling or input validation is the root cause behind most overflows, injection attacks, and canonical structure errors. 

Buffer overflows are an example of input handling 

Input validation is a way to fix this and can be used well against the following attacks:
- buffer overflows
- reliance on untrusted inputs in a security decision
- cross site scripting (XSS)

Input validation may seem suitable for various injection attacks but improperinput streams makes this message fall short

recognition and whitelisting approach could work

---
## Replay Attacks
**Def: an attack that attempts to re-create the conditions that existed the first time the sequence of events occured**

If an attacker can record a series of packets and then replay them, what was valid before may well be valid again

---
## Session Replay
**Def: When computer connects to the internet a session is created. This attacks replays that section**

---
## Integer Overflow
**Def: error condition that occurs when a program attempts to store a numeric value, which is an integer, in a variable that is too small to hold it. 

Easy to test for, static code analyzers can point out where they are likely to occur

---
## Request Forgery
**Def: an attack where the user performs a state-changing action on behalf of another user, typically without their knowledge. 

Attacks utilize the behavioral characteristcs of web-based protocols and browsers. 

## Server-Side Request Forgery
**Def: an attack that sends requests to the server-side application to make HTTP requests to an arbitrary domain of the attack's choosing.**

Exploit trust relationship between server and target

--- 

## Cross-Site Request Forgery (XSRF)
**Def:  An attack that utilizes unintended behavior that are proper in defined use but  performed outside the authorized use**

This is an example of a confused deputy problem, where one entity mistakenly performs an anction on behalf of another. 

---
## Application Programming Interface (API) Attacks

**Def: The attacker specifically attacks the API and the service behind it by manipulating inputs**

APIs are used to feed data to an application, so some of the processing is done in the application

This means that the interface is more of a raw feed into the server, with less work, and less checking , done on the server.

---
## Resource Exhaustion
**Def: the state where a system does not have all of the resources it needs to continue to function**

Two common resources are capacity and memory, which are interdependent in some scenarios but completely seperate in others.

- capacity: a system having the necessary amount of communication, bandwidt, processing bandwidth, and memory to manage intermediate states

---
## Memory Leak
**Def: The result of errors in memory management**

There is not automatic garbadge collector in C or C++, programmer must allocate free memory explicitly

---
## Secure sockets Layer (SSL) Stripping
**Def: A man in the middle attack against all SSL and early versions of TLS connections**

Starts by intercepting inital connection request for HTTPs, redirecting it to an HTTP site, and then mediating the site

---
## Driver Manipulation
**Def: an attack on the system but chaning drivers, thus changing the behavior of the system**

---
## Shimming
**Def: putting a layer of code between the driver and the OS**

allows flexibility and portability by enabling changes between different versions of an OS without modifying the original driver code

---
## Refactoring
**Def: the process of restructuring existing computer code without changing its external behaviour**

done to improve nonfunctional attributes of the software
___

## Pass the Hash
**Def: the attacker captures the hash used to authenticate a process. They can then use this hash by injecting it into a process in place of the password**

---
# Questions
1 B
2 C
3 B
4 A 
5 C
6 D 
7 B
8 B
9 A
10 D 











