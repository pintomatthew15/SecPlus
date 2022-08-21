# Chapter 11
# Secure Application Development, Deployment, and Automation Concepts

## Environment
Most organizations have multiple, separate computing environments designed to provide isolation between the functions of development, test, staging, and production. 

The point of these seperate environments is to prevent security incidents from arising.

The hardware of these environments is segregated, and access control lists are used to prevent users from accessing more than one environment at a time.

### Development
The develpoment environment is sized, configured, and set up for developing applications and systems. 

Unlike production hardware, the development hardware does not have to be scalable, and it probably does not need to be as responsive for given transactions. 

The development platform does need to use the same OS type and version as used in the production environment, for developing on Windows and deploying to Linux is fraught with difficulties

### Test
The test environment fairly closely mimics the production environment --same versions of software, down to patch levels, same sets of permissions, same file structures, and so forth.

The purpose of the test environment is to test a system fully prior to deploying it into production to ensure that it is bug-free and will not disrupt the production environment. 

It is important that a product is tested in an environment identical to that in which it will be run.

### Staging
The staging environment is an optional environment, but it is commonly used when an organization has multiple production environments.

The primary purpose of staging is to serve as a sandbox after testing, so the test system can test the next set while the current set is deployed across the enterprise. 

### Production
The production environment is when the systems work with real data, doing the business that the system is intended to perform. 

This is an environment where, by design, very few changes occur, and those that do must first be approved and tested via the system's change management process. 

**Exam Tip: Understand the structure and purpose of the different environments so that when given a scenario and asked to identify which environment is appropriate, you can pick the best answer: development, test, staging, or production.**


### Quality Assurance (QA)
Quality Assurance (QA) is a common step in any manufacturing process, and software is no exception.

Ensuring thaat qualilty is in a product is a process issue, not an inspection issue. 

Security needs to be considered as the project is being developed not after. 

---

## Provision and Deprovisioning
**Def: Provisioning is the process of assigning permissions or authorities to objects.**

Users can be provisioned into groups, and computer processes or threads can be provisioned to higher levels of authority when executing.

**Def: Deprovisioning is the removal of permissions or authorities.**

In secure coding, the practice is to provision a thread to an elevated execution permission level (for example root) only during the time that the administrative permissions are needed. Once that step has passed, the thread can be deprovisioned back to a lower access level.

## Integrity Measurement
**Def: Integrity is defined in the security field as a determiniation that data has no unauthorized changes.**

In a software development and deployment environment, this is a very important issue because even little changes can cause huge issues and can be difficult to detect. 

First, you have control over the copies in such a way that people are only working on a legitimate codebase.

Second, you maintain a log of the changes and a method of identifying the versions. The version control system you use should keep track of the versions, but to clearly identify a set of code requires a different tool. 


---

## Secure Coding Techniques
Software security begins with code that is secure and free of vulnerabilities. Unfortunately, all code has weaknesses and vulnerabilities, so instantiating the code in a manner that has effective defenses to prevent the exploitation of vulnerabilities can help maintain a desired level of security. 


### Normalization
**Def: The initial setup of the input validation process. Specifically, it is the process of creating the canonical form, or simplest form, of a string before processing.**

Strings can be encoded using Unicode and other encoding methods. This makes byte-by-byte comparisons meaningless when trying to screen user input of strings. 

Checking to see whether the string is "rose" can be difficult when "A Rose is a rose is a r%6fse" The process of normailzation converts all of these to "rose," where they can be screened as valid input.

Different libraries exist to assist developers in performing this part of input validation. Developers should always normalize their inputs prior to validation steps to remove Unicode and other encoding issues.

### Stored Procedures
**Def: Methods of interfacing with database engines.** 

Stored procedures are precompiled scripted methods of data access that offer many advantages. 

First is speed. Because they are precompiled, they can run much more efficiently in the production environment, but because they are scripted in advance they lack flexibility. 

**Exam Tip: A stored procedure is a group of one or more statements stored within a database. Stored procedures are used in programming languages such as SQL, Java, C++, and C.**

### Obfuscation/Camouflage
**Def: The hiding of obvious meaning from observation.**

Not good while writing the code, bad code is like a ticking time bomb. 

### Code Reuse and Dead Code
Modern software development includes the extensive reuse of components. From component libraries to common functions across multiple components, there is significant opportunity to reduce development costs through reuse. 

The downside of reuse is a monoculture environment, which is where a failure has a larger footprint because of all the places it is involved with. 

**Exam: The use of legacy code in current projects does not exempt that code from security reviews.**

**Def: Dead code is code that, while it may be executed, obtains results that are never used elsewhere in the program.**

There are compiler options that can remove dead code, called dead code elimination, but these must be used with care.

### Server-Side vs. Client-Side Execution and Validation
In a modern client/server environment, data can be checked for compliance with input/output requirements either on the server or on the client side.  

The client is not a suitable place to perform any critical value checks or security checks. The reasons for this are twofold. 

1. The client can change anything after the check
2. The data can be altered while in transit or at an intermediary proxy.

For all checks that are essential, either for business reasons or for security, the verification steps should be performed on the server side, where the data is free from unauthorized alterations. 

Input validation checks can be safely performed only on the serverside.

### Memory Management
Memory management encompasses the actions used to control and coordinate computer memory, assigning memory to variables, and reclaiming it when it is no longer being used. 

Errors in memory management can result in a program that has a memory leak, and it can grow overtime, consuming more and more resources. 

The routine to cleanup memory that has been allocated but no longer needed is called garbage collection. 

Low level programming languages (C and C++) do not provide automatic garbage collection. 

### Use of Third-Party Libaries and Software Development Kits (SDKs)
Once code has been debugged and proven to work, rewriting it is generally not a valuable use of time. 

Also, some fairly complex routines, such as encrpytion, have vetted, proven library sets that remove a lot of risk from programming these functions.

**Exam Tip: Software developers use packaged sets of software programs and tools called SDKs to create apps for specific vender platforms.**

### Data Exposure
**Def: The loss of control over data from a system during operations.**

Data must be protected during storage, communication, and even at times during use

Data can be lost to unauthorized parties (a failure of confidentiality) and, equally dangerous, can be changed by an unauthorized party (a failure of integrity).

---
## Open Web Application Security Project (OWASP)
**Def: The Open Web Application Security Project (OWASP) is a nonprofit foundation dedicated to improving web-based applicaiton software security.**

Best known for its top ten list of software vulnerabilities associated with website applications, OWASP also has a multitude of useful guidelines on its website, www.owasp.org. 

OWASP is a resource that should be actively used by web application programmers to prevent vulnerabilities that are common in web appplications. 

---
## Software Diversity
Software is not a single product. Software can be categorized by elements such as platform (PC, server, mobile, IoT device, cloud), programming language, interfaces (web, API, messaging, direct connections), purpose, and a whole host of other factors.

Having a proper security process as part of the development process is important to reduce vulnerabilities and manage security issues as they are uncovered.

Another key aspect of software diversity is monoculture avoidance. As many systems of an enterprise have common elements, there exists the possibility for common vulnerabilities to affect many components.

### Compilers
**Compilers** take computer programs written in one lnaguage and convert them to a set of codes that can run on a specific set of hardware. 

Modern compilers take high-level platform-agnostic code and convert it to machine language code that actually can run on a given platform. 

### Binaries
Having two machines, or more, with completely identical memory layouts again provides attackers a reproducible target. 

This has led to defenses that include randomizing memory layouts, where the pattern is specific to each boot of the machine and is only known to the machine.

**Binary Diversity** is the creation of identically functioning binary images, but with different specific instantiations. Different locations for memory variables, different pointer offsets, and different layouts in computer memory can all be done today and yet completely preserve functionality. 

**Exam Tip: Taking binary diversity to the extreme, one can run a set of variants simultaneously in a multivariant execution environment (MVEE). The system then unifies inputs/outputs and monitors the operation, enabling detection of when variants diverge in behavior. This indicates abnormal behavior and enables the system to react and recover from bad result stream.**


---
## Automation/Scripting
Automation through scripting and other programmable means has great utility in software development. 

The use of these technology-backed methods has led to a field of development known as DevOps. DevOps is a combination of ***development*** and ***operations*** in other words, a blending of tasks performed by a company's application development and systems operations teams.

DevOps emphasizes communication and collaboration between product management, software development, and operations professionals to facilitate continuous development, continuous integration, continuous delivery and continuous monitoring processes. 

### Automated Courses of Action
One of the key elements of DevOps is automation. DevOps relies on automation for much of its efficiencies.

Security automation can do the same for security that automation has in DevOps. Automating routines and extensive processes allows fewer resources to cover more of the environment in a more effective and efficient manner. 

### Continuous Monitoring
**Def: the term used to describe the technologies and processes employed to enable rapid detection of compliance issues and security risks.**

Automation and scripts are commonly used as part of a continuous monitoring framework, as they can provide 24/7/365 monitoring of processes and condtions, feeding alterts into the organization's monitoring system for review and action by security personnel. 

### Continuous Validation
**Def: The extension of testing to support the continuous process of software development that occurs in DevOps.**

As code is changed in the DevOps process, the new code must be tested with the existing codebase to ensure functionality and stability.

**THINK TESTING**

### Continuous Integration
**Def: The DevOps manner of continually updating and improving the production codebase.**

This means that rather than several large updates, with many integrated and many potentially cross-purpose update elements, all squeezed into a single big package, a whole series of smaller single-purpose integrations is run.

This reduces interaction errors and other types of errors that are time-consuming to chase down

### Continuous Delivery
**Def: The natural extension of continuous integration so that you can quickly release new changes to production in a sustainable way.**

Continuous delivery relies on automated testing and is an automated release process that enables the delivery of updates when they are complete, at any point of time, as opposed to a fixed release schedule. 

### Continuous Deployment
**Def: Continous delivery on autopilot.**

It goes one step further than continuous delivery in that the release is automatic. 

With this practice, every change that passes all stages of your production pipeline is released to production.

**Exam Tip: Continuous deployment goes one step further than continuous delivery--every change that passes all stages of your production pipeline is automatically released to customers.**

----
## Elasticity
**Def: The characteristic that something is capable of change without breaking.**

For software to be elastic, it needs to be able to run under a variety of different conditions. 

For scalability to be stable and sustainable, the software needs to be elastic. 

---
## Scalability
**Def: the characteristic of a software system to process higher workloads on its current resources (scale up) or on additional resources (scale out) without interruption.**

Scalability is important in web systems, databases, application engines, and cloud systems. 

Scaling out to multiple machines brings in issues of synchronization and coordination. All of these issues can be solved, but this has to happen during design and development, not after delivery.

---
## Version Control
**Def: The simple tracking of which version of a program is being worked on, whether in dev, test, or production.**

Versioning tends to use the first whole number to indicate major releases and uses numbers after a decimal point to indicate minor changes. 

Having the availability of multiple versions brings into focus the issue of change managment. 


# Questions
1. D (software diversity in the form of diverse binaries will prevent direct memory attacks)
2. C
3. A
4. B
5. D
6. B (Obfuscation is the technique of hiding properties to prevent examination)
7. C
8. D (The stagining environment can be used to manage software releases against different target
9. A
10. B






