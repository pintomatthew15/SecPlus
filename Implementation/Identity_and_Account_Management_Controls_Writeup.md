# Chapter 23 
# Identity and Account Management Controls

Identity forms part of the foundation of authentication in computer systems. The second part of this foundation is the use of accounts that are managed by a series of policies to enforce a level of rational risk associated with their use. 

## Identity
**Def: Identification is the process of ascribing a computer ID to a specific user, computer, network device, or computer process.**
- The ID process is typically performed only once, when a user ID is issued to a particular user.
- User ID enables authentication and authorization to form the basis of accountability. 
- A required characteristic of such IDs is that they must be **unique**

### Identity Provider (IdP)
**Def: The term identity provider (IdP) is used to denote a system or service that creates, maintains, and manages identity information.**
- IdPs can range in scale and scope--from operating for a single system to operating across an enterprise.
- Multiple standards have been employed to achieve these services, including those built on the Security Assertion Markup Language (SAML), OpenID, and OAuth. 

**EXAM TIP: The identity provider (IdP) creates, manages, and is responsible for authentication identity.**

### Attributes
**Def: Identity attributes are the specific characteristics of an identity--name, department, location, login ID, identification number, e-mail address, and so on--that are used to accurately describe a specific entity.**
- These elements are need to store identity information in some form of directory such as an LDAP directory.
- The details of schemas have already been taken care of via Active Directory, various IdPs, and so on, so this is not something that needs to be created; however, it does need to be understood.

### Certificates
**Def: Certificate-based authentication is a means of proving identity via the presentation of a certificate**.
- Certificates offer a method of establishing authenticity of specific objects such as an individual's public key or downloaded software.

**Def: A digital certificate is a digital file that is sent as an attachment to a message and is used to verify that the message did indeed come from the entity it claims to have come from.**
- When a certificate is held within a store that prevents tampering or extraction, this becomes a reliable means of identification, especially when combined with an additional factor such as something you know or a biometric.

### Tokens
**Def: An access token is a physical object that identifies specific access rights and, in authentication, falls into the "something you have" factor.**
- A house key is a basic example of a physical access token
- It is difficult to take access away from a single key or key holder, which usually requires a rekey of the whole system.

Contactless radio frequency cards and proximity readers have taken the place of physical access tokens since any card can be deleted from the system without affecting any other card or the rest of the system. 

The risk of theft of the token can be offset by the use of multifactor authentication described back in Chapter 12.

### SSH Keys
**Def: SSH keys are access credentials used by the Secure Shell (SSH) protocol.**
- They function like usernames and passwords, but SSH keys are primarily used for automated processes and services
- SSH keys are also used in implementing single sign-on (SSO) systems used by system administrators. 
- SSH keys are exchanged using public key cryptography, and the keys themselves are digital keys.

### Smart Cards 
**Def: Smart cards are devices that store cryptographic tokens associated with an identity.** 
- The form factor is commonly a physical card, credit card sized, that contains an embedded chip that has various electronic components to act as a physical carrier of information.

The US federal government has several smart card solutions for identification of personnel.
- The Personal Identity Verification (PIV) card is a US government smart card that contains the cardholder's credential data used to determine access to federal facilities and information systems.
- The Common Access Card (CAC) is a smart card used by the US DOD for active-duty military, Selected Reserve Members, and DoD civilians. 

**EXAM TIP: Remember the various uses for tokens, keys, and smart cards. An access token is a physical object that identifies specific access rights and in authentication, falls into the "something you have" factor. SSH keys are primarily used for automated processes and services. A PIV card is a smart card used for federal employees and contractors. You know what a CAC is.**

## Account Types 
To mange the privileges of many different people effectively on the same system, a mechanism for separating people into distinct entities (users) is required, so you can control access on an individual level. It's convenient and efficient to be able to lump users together when granting many different people (groups) access to a resource at the same time. At other times its better to grant or restrict based on a person's job or function within the organization (role). 

### User Account
**Def: The term user account refers to the account credentials used when accessing a computer system.**
- In privilege management, a user is a single individual.
- When accessing a computer system, each user is generally given a user ID--a unique alphanumeric identifier they will use to identify themselves when logging in or accessing the system.

**EXAM TIP: Having unique, nonshared user IDs for all users of a system is important when it comes time to investigate access control issues.**

The first step in privilege management is making sure a user does not make their own account but is instead given one by the system administrator.

Once the account is created the Administrator will assign permissions. While PC's have one or two user accounts, larger systems such as servers and mainframes can have hundreds of accounts on the same system.

Account policy enforcement is an important part of user credential systems. Managing credentials begins with policies that state the desired objective. 
- There should be a prohibition on sharing accounts and of generic accounts not being assigned to a user
- Users with multiple roles should possibly have multiple accounts but these need to be delineated by policy 
- When users are no longer authorized, their accounts should be disabled, not removed.

### Shared and Generic Accounts/Credentials
Shared accounts go against the specific premise that accounts exist so that user activity can be tracked.
- This said, there are times that shared accounts are used for groups like guests. Sometimes the shared accounts are called generic accounts and exist only to provide a specific set of functionalities such as in a PC running in kiosk mode, with a browser limited to accessing specific sites as an information display. 

A common form of a shared account is one created to run nightly batch operations.
- As every action must be associated to a user account, a shared account in the name of a batch user can be used to run batch jobs. 
- This is a generic set of credentials, not actually associated with a single person but with a particular type of process 

### Guest Accounts
Guest accounts are frequently used on corporate networks to provide visitors access to the Internet and to some common corporate resources, such as projectors, printers in conference rooms and so forth. 
- Like generic accounts, these accounts are restricted in their network capability to a defined set of machines, with a defined set of access.

**EXAM TIP: Guest accounts are granted limited permissions and access. They are used primarily for visitors. It is common practice to disable guest accounts as well as other default accounts when not in use.

### Service Accounts
**Def: Service accounts are accounts that are used to run processes that do not require human intervention to start, stop, or administer. 
- From a security perspective, administrators can configure service accounts to minimize risks associated with them.

**EXAM TIP: Service accounts run without human intervention and are granted only enough permission to run the services they support.**


## Account Policies 
The key method used to control access to most systems is still one based on passwords. 

An account policy can act to ensure that the necessary steps are taken to enact a secure password solution, both by users and by the password infrastructure system.


### Password Complexity
Every organization should have defined password complexity requirements that passwords must meet. 

Typical password requirements must:
- Meet the minimum length requirements 
- Have characters from at least three of the following four groups: English uppercase characters, English lowercase characters, numerals 0-9, and nonalphabetic characters.

**NOTE: Strong passwords aren't enough anymore. Computing power allows cybercriminals to run sophisticated programs to obtain or try massive numbers of credentials. That's why relaying on passwords alone is no longer sufficient. Specifically, companies should adopt tools like single sign-on (SSO) and multifactor authentication. (MFA), also known as two-factor authentication.**

### Password History
**Def: Password history refers to passwords previously used by an account.**
- It is good security to prohibit reuse of passwords, at least for a set number of passwords. In Windows under Local Security Policy (under Local Group policies), you can set three elements that work together to manage password history:
	1. Enforce Password history: Tells the system how many passwords to remember and does not allow a user to reuse an old password in that list. 
	2. Maximum Password age: Specifies the maximum number of days a password may be used before it must be changed
	3. Minimum Password age: Specifies the minimum number of days a password must be used before it is changed again.

The minimum password age is to prevent a user from changing their password 20 times in a row to recycle back to the previous or current password. 

### Password Reuse
Password reuse is a bad idea in that it reopens an exposure to an adversary who has previously obtained a password.
- Passwords should not be reused for at least a year. 
- We should never reuse passwords for a single account or between accounts

**EXAM TIP: Strong password policies and settings can help prevent password-cracking attempts such as brute force and dictionary attacks.**

### Time of Data
Creating time-of-day restrictions for access can solve many account management problems. 
- As with all policies, provisions need to be made for change and emergencies, whereby authorized users can obtain access when needed, even if outside normal working hours. 

You can set logon time limits for a user in Windows using an administrative command prompt with the following syntax:
```
net user <username> /time:<day>,<time>
```
Alternatively, in a domain environment, you can also set logon hour restrictions in Active Directory through Group Policy and Group Policy Objects (GPOs).

### Network Location
Having restrictions for accounts based on the network location can be a very powerful tool in limiting attack surfaces against privileged accounts.
- Might prevent legitimate users from performing actions, it is still a small price to pay

### Geofencing
**Def: The use of the Global Positioning System (GPS) and/or radio frequency identification (RFID) technology to create a virtual fence around a particular location and detect when mobile devices across the fence.**
- This enables devices to be recognized by others, based on location, and have actions taken.

### Geotagging
**Def: The process of applying geotags (location information) to a specific item.**
- The actual geotags can be in a variety of formats but are typically some form of an encoding of latitude and longitude. 
- Geotags have been used in many investigations , as many photos have geotag information embedded in the metadata at the time of creation.
- This data can only be read by special utilities that can read the exchangeable image file (EXIF) or extensive metadata platform (XMP) formats.

### Geolocation
Most mobile devices are now capable of using GPS for tracking device location. 
- Such technologies can be exploited to track movement and location of the mobile device, which is referred to geolocation. This tracking can be used to assist in the recovery of lost devices.

**EXAM TIP: Know the difference between geofencing and geolocation. These make great distractor answer choices for each other in exam questions.**

### Time-based Logins
**Def: Time-based logins are the implementation of time-based authentication, and the proper deployment of this method requires appropriate policies and procedures.** 
- Time-based exclusions also assist in security, blocking account usage outside of normal working hours. 

### Access Policies 
**Def: A set of policies to assist in the management of the access control system.**
- From simple policies covering password use, password length, expiration, and lockout, to more complex issues such as account expiration, recovery, and disablement, these directives provide the guidance for security personnel to manage access to the system.

**Password policies** are needed to cover the details of items such as password length, complexity, reuse, and history.
- Password length and complexity may seem to be forever increasing targets, but defining them is important to prevent people from using simple, easy-to-crack passwords.

**Account Expiration** should occur when a user is no longer authorized to use a system
- This requires coordination between those who manage the accounts and those who manage the need for access.

Managers should be the first ones to notify the security team as to any changes in permissions, and human resources (HR) should play a backup role. 

**NOTE: In Windows systems, user account expiration is a built-in feature that allows you to create a temporary user account that will expire automatically on a specified date. Upon reaching the expiration date, the user account is expired and the user is unable to log onto Windows after that date. This can be good for temporary and contract workers.**

**Account Recovery** seems like an esoteric topic until you lose the password on your laptop and have no way back in. This is even more serious if you lose your administrator account passwords to key elements of your infrastructure.

**EXAM TIP: Accounts have many facets that are governed by both action and policy. Remember, policy directs actions, and the specifics of the question give the context by which you can choose the best answer.**

### Account Permissions
Developing a policy for **account permissions** provides just that guidance to those who are implementing the access control schemes.
- An example of a policy would be that users who are acting as database admins are assigned to a group of database admins, to facilitate easier management. Once in the group, the group permissions solve the detail by user. Similarly, system administrators may be assigned to a group, to control their permissions. 

A good policy can enforce separation of duties as well as manage the detail associated with the granularity of permissions.

A common differentiation of types of users is:
- **Administrator**: An admin account has full control of the files, directories, services, and other resources on the local computer. The admin  creates other local users, assigns user rights, and assigns permissions. In Linux systems, the root account is used for admin purposes, while in Windows the account is called either Administrator or local administrator. 
- **Standard User**: Standard accounts are the basic accounts you use for normal everyday tasks. Standard users may be limited from installing new programs.
- **Guest**: The guest account should be disabled by default on installation. The guest account lets occasional or one-time users who do not have an account on the computer temporarily sign in to the local server or client computer with limited user rights. 

### Account Audits
**Def: Account audits like all other audits--they are an independent verification that the policies associated with the accounts are being followed.**
- An independent auditor can check all elements of policies. 

### Impossible Travel Time/Risky Login
Correct logins to an account can record many elements of information, including where the login came from. This "where" can be a machine in a network, or even a geographic location. Using this metadata, some interesting items can be calculated.

**Def: Risky logins or impossible time travel is when logins appear that fail to make logical sense due to certain geographic or timing differences between logins.**
- EX: Someone logs in from China and then the UK two hours apart.

Elements of the policy are not simple, because while a remote login from a continent may be easy to deny, what of the two logins in the same building overlapping? 

### Lockout
**Def: Account lockout is akin to disablement, although lockout typically refers to temporarily blocking the user's ability to log in to a system.**

**EXAM TIP: An account lockout policy is used to disable a user account when an incorrect password is used a specified number of times over a certain period of time. This is especially useful in slowing down brute force attempts at cracking passwords. 

### Disablement 
**Def: Account disablement is a step between the account having access and the account being removed from the system.**
- Disabling is preferable to removal, as removal may result in permission and ownership problems

**EXAM TIP: Accounts have many facets that are governed by both action and policy. Remember, policy directs actions, and the specifics of the question give the context by which you can choose the best answer. There is a lot of detail in this section, and it is all testable in this manner.**


# Questions
1. C
2. B
3. D
4. A
5. B
6. D
7. A
8. C
9. C
10. A

100! 