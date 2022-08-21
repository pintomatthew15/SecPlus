# Chapter 12
# Authentication and Authorization

## Authentication Methods
**Authentication** is the process of verifying an identity previously established in a computer system. There are are a variety of methods of performing this function, each with its advantages and disadvantages, as detailed in the following sections.

### Directory Services 
**Def: a directory is a data storage mechanism similar to a database, but it has several distinct differences designed to provide efficient data-retrieval services compared to standard database mechanisms.**

Directories are designed and optimized to read data offering very fast serach and retrieval operations. 

Common uses of directories include e-mail address lists, domain server data, and resource maps of netowrk resources.

The Lightweight Directory Access Protocol (LDAP) is commonly used to handle user authentication and authorization and to control access to Active Directory (AD) objects.

To enable interoperability, X.500 was created as a standard for directory services. The primary method for accessing an X.500 directory is through the Directory Access Protocol (DAP), a heavyweight protocol that is difficult to implement completely, especially on PCs and more constrained platforms. 

This led to LDAP, which contains the most commonly used functionality. LDAP can interface with X.500 services and, most importantly , can be used over TCP with significantly less computing resources than a full X.500 implementation. 

LDAP has become the Internet standard for directory services. LDAP standards are governed by two separate entities, depending on use: the International Telecommunication Union (ITU) governs the X.500 standard, and LDAP is governed for Internet use by the Internet Engineering Task Force (IETF). 

**Exam Tip: A client starts an LDAP session by connecting to an LDAP server, called a Directory System Agent (DSA), which is by default on TCP and UDP port 389 or on port 636 for LDAPS (LDAP over SSL).**

### Federation
**Def: defines policies, protocols, and practices to manage identities across systems and organizations.**

Federation's ultimate goal is to allow users to seamlessly access data or systems across domains.

Federation is enabled through the use of industry standards such as Security Assertion Markup Language (SAML)

**Exam Tip: Federated identity access management systems allow users to authenticate and access resources across multiple enterprises using a single credential. But don't confuse this with single sign-on (SSO), which allows users access to multiple resources within a single organization or enterprise.**

### Attestation
**Def: the supplying of proof or evidence of some fact.**

In the case of authentication, attestation can be done by a service that checks the credentials supplied, and if they are correct and match the required values, the service can attest that the entry is valid or correct. 

Attestation is used throughout cyber security whenever a third party or entity verifies an object as valid or an item as correct in value. 

### Technologies
There are multiple ways to perform authentication, and multiple technologies can be employed to assist in the effort. 

- #### Time-based One-Time Password (TOTP):
	The Time-based One-Time Password (TOTP) algorithmn is a specific implementation of an HOTP that uses a secret key with a current timestamp to generate a one-time password (OTP). It is described in RFC 6238.

- #### HMAC-based One-Time Password (HOTP):
	HMAC-based One-Time Password (HOTP) is an algorithm that can be used to authenticate a user in a system by using an authentication server. It is defined in RFC 4226.

**Exam Tip: HOTP passwords can remain valid and active for an unknown time period. TOTP passwords are considered more secure because they are valid for short amounts of time and change often.**

- #### Short Message Service (SMS):
	The use of Short Message Service (SMS), or text messagining, in a cell phone provides a second authentication factor that is sent to a preidentified number, the message that is sent provides a code that the user enters into the system.
- #### Token Key:
	Token keys are physical devices that carry a digital token used to identify the user. This is a "something you have" element in a multifactor authentication scheme. Tokens are a proof of possession type of event, and to prevent their use if lost, they are backstopeed with a PIN code. 
- #### Static Codes:
	Static codes are just that -- codes that do not change, or are static in nature. There are many use cases where these are essential, such as devices without user intervention.

	Weakness: if compromised, the keys are no longer valid 
- #### Authentication Applications:
	Functions by accepting user input, and if the user input is correct, it can pass the appropriate credentials to the system requesting authentication. 

	The use of the application on the device is a second factor of authentication and is part of a multifactor authentication scheme.
- #### Push Notifications:
	Push notification authentication supports user authentication by pushing a notification dirctly to an application on the user's device. 

	This is an out-of-band communication and demonstrates a second communication channel, thus making account hacking significantly more challenging.

- #### Phone Call:
	The Authentication phone call is delivered from the authentication system to a specified phone number, which then can verify that the user is in possession of the actual mobile device.

**Exam Tip: Tokens represent something you have with respect to authentication as well as devices that can store more information than a user can memorize, which makes them very valuable for access control. The details in the scenario preceding a question will provide the necessary criteria to pick the best token method for the question.**


- #### Smart Card Authentication
	A smart card is a credit card-sized card with embedded integrated circuits that is used to provide identification security authentication. 

---
## Biometrics
**Def: Biometric factors are measurements of certain biological factors to identify one specific person from others.**

These factors are based on parts of the human body that are unique. The most well known being the fingerprint.

### Fingerprint
A finger print scanner measures the unique pattern of a person's fingerprint and translates that pattern into a numerical valule, or template, as discussed in the previous section. 

One of the challenges of fingerprint scanners is that they don't function if the user is wearing gloves (for example, medical gloves) or has worn of their fingerprints through manual labor

### Retina
A retinal scanner examines blood vessel patterns in the back of the eye. Believed to be unique and unchanging, the retina is a readily detectable biometric.

It is expensive because of the precision of the detector and the involvement of lasers and users' vision. 

### Iris
An iris scanner works in a manner similar to a retinal scanner in that is ues an image of a unique biological measurment (in this case, the pigmentation associated with the ris of the eye). 

Works at any distance

### Facial
Facial recognition nough said. 

One downside is that someone could move the sensor in front of the other's face triggering it.

### Voice
Voice recognition is the use of unique tonal qualities and speech patterns to identify a person. 

Hard to develop because of the abundance of false acceptance and rejection rates

### Vein
A different biometric is the use of blood vein patterns to identify a user. Humans have a common vascular system, but the individual elements can vary in size and microstructure, and these fine-grained patterns are believed to be unique. 

These are noninvasive measurements, but they do require close proximity to the user's item under measurement. 

### Gait Analysis
Gait analysis is the measurement of the pattern expressed by a person as they walk. An analysis of the gait, its length, the speed, and the rate of movement of specific points provides a unique signature that can be recorded and compared to previous samples.

From an access control perspective,  in high-security situations, a camera can record the gait of incoming personnel and compare it to known values, providing a remote and early additional factor in determining identity. 

---
## Efficacy Rates
Biometric measurements have a level of uncertainty, and thus the efficacy of biometric solutions has been an issue since they were first developed. 

For biometrics to be effective, they must have both low false positive and low false negative rates.

FAR: False acceptance rate, the chance the user that an incorrect user will be falsely accepted 

FRR: False Rejection Rate the chance a correct user will be falsely rejected. 

A low false acceptance rate is more important from a security perspective. 


## False Acceptance
**Def: False Acceptance Rate (FAR) determines what level of false positives is allowed in the system.**

False acceptance is demonstrated by the grayed-out area in the system. 

Thus, if you are not a match, but your measured value falls on the upper end of the nonmatch curve (in the gray area), you will be considered a match, hence a false positive. 

The false acceptance rate is expressed as the probability that they system incorrectly identified a match between the biometric input and the stored template value.

When selecting the threshold value, the designer must be cognizant of two factors:
1. The rejection of a legitimate biometric the area on the match curve below the threshold value.
2. The acceptance of false positives. The more the curves overlap, the larger the problem, because once a threshold is chosne, that number defines the FAR

## False Rejection
**Def: The false rejection rate (FRR) determines what level of false negatives, or rejections, are going to be allowed in the system.**

A false rejection is demonstrated by the grayed-out area in the chart. 

When comparing the FAR and the FRR, one realizes that, in most cases, whenever the curves overlap, they are related. This brings up the issue of the crossover error rate.

Both the FAR and the FRR are set by choosing the threshold value. This is done when the system is set up and reflects the choice of which error rate is more important. 

If you want to make sure all legitimate users do not experience trouble during scans, then some unauthorized users will get accepted (false positives) because they will be interpreted by the system as being on the wrong curve based on where the threshold is.

![[Pasted image 20220330165734.png]]

![[Pasted image 20220330165755.png]]

## Crossover Error Rate
**Def: The cross over error rate (CER) is where both accept and reject error rates are equal.**

This is the desired state for the most efficient operation, and it can be managed by manipulating the threshold value used for matching. 

In practice, values will not actually be the same, but they should be close.

**Exam Tip: Remember that the crossover error rate (CER) is the percentage at which the false acceptance rate (FAR) and the false rejection rate (FRR) are equal.**

---
## Multifactor Authentication (MFA) Factors and Attributes

**Def: Multifactor authentication (or multiple-factor authentication) is simply the combination of two or more types of authentication.**

Five broad categories of authentication can be used: what you are (for example biometrics) what you have (tokens), what you know (passwords), somewhere you are (location), and something you do (physical performance). 

Two factor authentication combines any of these two before granting access.

**Exam Tip: Two-factor authentication combines any two methods, matching items such as a token with a biometric. Three-factor authentication combines any three, such as a passcode, biometric, and a token.**

Using multiple factors is one of the best ways to ensure proper authentication and access control.

### Factors
**Def: Factors are the specific elements that comprise an item of proof.**

These items can be grouped into three classes: something you know, something you have, and something you are.

- #### Something You Know
The most common example is a password. 

One of the challenges with something you know is that it can be shared without you knowing it

Another example of something you know: identity-driven authentication, here you contact someone to get access, and they respond with a series of challenge questions. 

- #### Something You Have
Something you have specifically refers to security tokens and other items that a user can possess physically. 

One of the challenges of with using something you have as an authentication factor is that you have to have it with you whenever you wish to be authenticated, and this can cause issues.

One of the challenges of something you have is the cocnept of "something you lost," such as something you left in a briefcase, at home, and so on. 

- #### Something You Are
Something you are refers to biometrics. One of the challenges with using something you are artifiacts as authentication factors is that typically they are hard to change; once assigned, they inevitably become immutable, as you can change fingers, but only limited number of times. 

### Attributes
**Def: Collections of artifacts, like the factors previously presented, but rather than focus on the authentication item, they focus on elements associated with the user.**

Common attributes include the user's location, their ability to perform a task, or something about the user themselves.

- #### Somewhere You Are
When a mobile device is used, GPS can identify where the device is currently located. When you are logged on to a local, wired desktop connection, it shows you are in the building. 

Both of these can be compared to records to see if you are really there or should be there. 

With geofencing, location becomes a big thing for marketing services pushing content to devices when in specific locations.

- #### Something You Can Do
Something you can do specifically refers to a physical action that you perform uniquely. 

An example of this is a signature; the movement of the pen and the two-dimensional output are difficult for others to reproduce.

Hard to capture without specialized software. 

- #### Something You Exhibit
Something you exhibit is a special case of a biometric. An example would be a brainwave response to seeing a picture. 

Another example would be the results of a lie detector test. 

The concept is to present a trigger and measure a response that cannot be faked. 

- #### Someone You Know
Just as passwords relate to possession of knowledge, someone you know relates to a specific memory, but in this case an individual. 

"Having someone vouch for you" attribute

**Exam Tip: Be able to differentiate between the three factors for authentication (something you know, have, and are) as well as the four attributes (somewhere you are, something you can do and exhibit, and someone you know). These are easily tested on the exam.

---
## Authentication, Authorization, and Accounting (AAA)
**Def: Authentication is the process of verifying an identity previously established in a computer system.**

**Def: Authorization is the process of permitting or denying access to a specific resource. **

- Once identity is confirmed via authentication, specific actions can be authroized or denied.
- This functionality is frequently part of the OS and is transparent to users.

**Def: Accounting is the process of ascribing resource usage by account for the purpose of tracking resource utilization.**

The separation of tasks, from identification to authentication to authorization, has several advantages. 

**Exam Tip: Authentication is the process of validating an identity. Authorization is the process of permitting or denying access to resources. Accouting is the process of keeping track of the resources a user accesses. Together, they make up the AAA framework for identity access security.**

---
## Cloud vs. On-premises Requirements
Authentication to cloud versus on-premises requirements is basically a revisting of the identity and authentication problem all over again. 

Solutions such as federated authentication and single sign-on exist, and the proper determination of authentication processes should rest on data criticality and who needs access. 

---
# Questions
1. B
2. A (Review false acceptance/rejection)
3. C
4. B
5. D
6. C
7. B
8. A
9. C
10. D



