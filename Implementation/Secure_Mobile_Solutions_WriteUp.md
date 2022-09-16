# Chapter 21 
# Secure Mobile Solutions 
The ubiquitous presence of mobile devices and the need for continuous data across multiple platforms have led to significant changes in the way mobile devices are being used for personal and business purposes. With continuously emerging devices and constantly changing technologies, many companies are allowing employees to bring their own devices for both personal and business usage. 

## Connection Methods and Receivers
Mobile devices require a non-wired means of connection to a network. Typically, this connection on the enterprise side is via the Internet, but on the mobile device side, a wide range of options exist for connectivity. 

This section covers the common methods of connecting, including cellular, Wi-Fi, Bluetooth, NFC, infrared, and USB. 


## Cellular
**Def: Cellular connections use mobile telephony circuits, today typically fourth-generation (4G) or LTE in nature, although some 3G services still exist.**
- One strength of cellular is that robust nationwide networks have been deployed, making strong signals available virtually anywhere with a reasonable population density. 
- One weakness is that gaps still exist in many rural areas

World is moving to 5G which is more than just a newer faster network. It is also a redesign to improve network communications through greater throughput, lower latency, better quality-of-service controls, and service differentiations. 


### Wi-Fi
**Def: Wi-Fi refers to the radio communication methods developed under the Wi-Fi Alliance.**
- These systems exist on 2.4 and 5.0 GHz frequency spectrums, and networks are constructed by both the enterprise you are associated with and third parties.
- Chapter 20 (previous chapter) discussed securing Wi-Fi networks

### Bluetooth
**Def: Bluetooth is a short-to-medium range, low-power wireless protocol that transmits in the 2.4-GHz band, which is the same band used for 802.11.**
- Original concept was to transmit data in personal area networks (PANs)

Bluetooth has gone through several releases:
- Version 1.1 was the first and we are now near 5.X

### NFC
**Def: Near field communication (NFC) is a set of wireless technologies that enables smartphones and other devices to establish radio communication when they are within close proximity to each other --typically a distance of 10 cm (3.9 in) or less.**

NFC is likely to become a high-use technology  in the years to come as multiple uses exist for the technology, and the next generation of smartphones is sure to include this as a standard function. 
- Currently, NFC relies to a great degree on its very short range for security, although apps that use it have their own security mechanisms as well 

### Infrared
**Def: Infrared (IR) is a band of electromagnetic energy just beyond the red end of the visible color spectrum.**
- IR can be used to connect devices in a network configuration, but it is slow compared to other wireless technologies. 
- IR cannot penetrate walls but instead bounces off them. 
- Because IR can be seen by all in range, any desired security must be on top of the base transmission mechanism.

### USB
**Def: Universal Serial Bus (USB) has become the ubiquitous standard for connecting devices with cables.**
- Laptops, desktops, even servers have USB ports for a variety of data connection needs. Many devices, such as phones, tablets, and IoT devices, also use USB ports, although many are moving to the newer and smaller USB type C (USB-C) connector. 

The most interesting of these devices, for security purposes, are the USB flash memory-based storage devices.
- USB drive keys provide a way to move files easily from computer to computer.

- They can easily be used by an individual with malicious intent to conceal the removal of files or data from the building or to bring malicious files into the building and onto the company network.

USB connectors come in a wide range of sizes and shapes. For mobile use, there is USB mini, USB micro, and now USB-C, which is faster and reversible.
- There are also type A and B connectors, with different form factors. 

### Point-to-Point
**Def: Point-to-Point communications are defined as communications with one endpoint on each end --a single transmitter talking to a single receiver.**
- Bluetooth is a good example and is mandated by a protocol
- USB is another example and is mandated by physical connection

### Point-to-Multipoint
**Def: Point-to-multipoint communications have multiple receivers for a transmitted signal.**
- When a message is sent in broadcast mode, it has multiple receivers and is called a point-to-multipoint communication.
- Most radio-based and networked systems are potentially point-to-multipoint, from a single transmitter to multiple receivers.

**EXAM TIP: Remember that a point-to-point connection is between two devices (one to one) while point-to-multipoint connections are one (device) to many (devices).**

### Global Positioning System (GPS)
**Def: GPS is a series of satellites that provide nearly global coverage of highly precise time signals that, when multiple signals are combined, can produce precise positional data in all three dimensions.**

- GPS receivers, operating in the 6-GHz band, are small, cheap, and have been added to numerous mobile devices, becoming nearly ubiquitous. 

- GPS enables geolocation, geofencing, and a whole host of other capabilities

### RFID
**Def: Radio Frequency Identification (RFID) tags are used in a wide range of use cases.**
- RFID tags are either active or passive. Active tags have a power source, where passive tags utilize the RF energy transmitted to them for power.

- RFID tags are used as a means of identification and have the advantage over bar codes that they do not have to be visible, just within radio wave range--typically centimeters to 200 meters, depending on tag type.

- RFID are used in a range of security situations, including contactless identification systems such as smart cards 

RFID tags have multiple security concerns:
- Because they are connected via RF energy, physical security is a challenge.

Several different attack types can be performed against RFID systems.
- The first is against the RFID devices themselves--the chips and the readers.
- A second form of attack goes against the communication channel between the device and the reader.
- The third category of attack is against the read and the back-end system.

The two main attacks are replay and eavesdropping. In a replay attack, the RFID information is recorded and then replayed later. 

**EXAM TIP: The various mobile device connection methods are conductive to performance-based questions, which means you need to pay attention to the scenario presented and choose the best connection methodology. Consider data rate, purpose, distances, and so forth in picking the best choice.**

## Mobile Device Management (MDM)
MDM began as a marketing term for a collective set of commonly employed protection elements associated with mobile devices. When its's viewed as a comprehensive set of security options for mobile devices, every corporation should have and enforce an MDM policy. The policy should require the following:

- Device locking with a strong password
- Encryption of data on the device
- Device locking automatically after a certain period of inactivity
- The capability to remotely lock the device if it is lost or stolen
- The capability to wipe the device automatically after a certain number of failed login attempts
- The capability to remotely wipe the device if it is lost or stolen

**EXAM TIP: Mobile device management (MDM) is a marketing term for a collective set of commonly employed protection elements associated with mobile devices. In enterprise environments, MDM allows device enrollment, provisioning, updating, tracking, policy enforcement, and app management capabilities.**

### Application Management
**Def: Application management is the method of installing, updating, and managing applications.**
- The two major vendor platforms are Google Store for Android and the Apple App Store for iOS devices.

### Content Management
**Def: The set of actions used to control content issues, including what content is available and to what apps, on mobile devices.**

MDM solutions exist to assist in this security issue with respect to mobile devices.

### Remote Wipe
Lost or stolen devices raise a security concern if data exists on them. 

**Def: Remote wiping in a mobile device typically removes data stored on the device and rests the device to factory settings.**

For most devices, remote wipes can only be managed via apps on the device, such as Outlook for e-mail, calendar and contacts and MDM solutions for all data. Apple and Android devices have a remote locking and factory reset, which effectively wipes the device.

### Geofencing
**Def: The use of the Global Positioning System (GPS) and/or radio frequency identification (RFID technology to create a virtual fence around a particular location and detect when mobile devices cross the fence.**
- Geofencing is used in marketing to send messages to devices that are in a specific area, such as near a point of sale, or just to count potential customers.

- Although you can turn off location services on Apple, you must also enable Airplane mode to turn off the radio.

### Geolocation
Most mobile devices are now capable of using GPS for tracking device location.

**EXAM TIP: Know the difference between geofencing and geolocation. These make great distractors.**

### Screen Locks
Most corporate policies regarding mobile devices require the use of the mobile device's **screen locking** capability. 

**EXAM TIP: Mobile devices require basic security mechanisms of screen locks, lockouts, device wiping, and encryption to protect sensitive information contained on them.**

### Push Notification Services
**Def: Services that deliver information to mobile devices without a specific request from the device.**
- Apple Push Notification services for Apple devices and Android Cloud to Device Messaging as Android device example

- It is possible to push devices to emit a sound even if the sound is muted on the device.

### Passwords and Pins
Passwords and Pins are common security measures used to protect mobile devices from unauthorized use. 

### Biometrics
**Def: Biometrics are used across a wide range of mobile devices as a means of access control.**
- Because biometric sensors have been shown to be bypassable, they should be considered convenience features, not security features. 
- Management policies should reflect this fact and should dictate that these methods not be relied on for securing important data.

### Context Aware Authentication
**Def: The use of contextual information--who the user is, what resource they are requesting, what machine they are using, how they are connected, and so on- to make the authentication decision as to whether to permit the user access to the requested resource.**

### Containerization
**Def: Containerization on mobile devices refers to dividing the device into a series of containers--one container holding work-related materials, the other personal.**
- Some MDM solutions support remote control over the work computer. This enables a much stronger use case for mixing business and personal matters on a single device.

- Most MDM solutions offer the ability to encrypt the containers, especially the work-related container, thus providing another layer of protection for the data.


### Storage Segmentation
On mobile devices it can be very difficult to keep personal data separate from corporate data.

**Def: Storage Segmentation is similar to containerization in that it represents a logical separation of the storage of the unit.**


**EXAM TIP: Remember that containerization and storage segmentation are technologies to keep personal data separate from corporate data on devices.**

### Full Device Encryption
Just how laptops and computers can have a full disk encryption, we may need to consider full device encryption (FDE) for mobile devices used by the organization's employees.

**EXAM TIP: Protection of data on a mobile device is accomplished via multiple tools and methods. For the exam, pay careful attention to the details of the question to determine which protection method is applicable, as each defends against a different issue. Full device encryption offers completely different protection from screen locks, and the details of the question will steer you to the correct answer. Don't jump on the choice that appears to be obvious; take a moment to understand the details. 

## Mobile Devices 
Mobile Devices can bring much to the enterprise in terms of business functionality, but with this increased utility comes additional risks. There are several methodologies to manage mobile devices, and these are covered in the following sections.

### MircoSD Hardware Security Module (HSM)
**Def: A MicroSD HSM is a hardware security module in a MicroSD form factor.**
- This device allows you a portable means of secure storage for a wide range of cryptographic keys.

- These devices come with an application that manages the typical HSM functions associated with keys, including backup, restore, and many PKI functions.

### MDM/Unified Endpoint Management (UEM)
**Def: MDM software is an application that runs on mobile devices and, when activated, manages aspects of the device including connectivity and functions.**
- The purpose of an MDM application is to turn the device into one where the functionality is limited in accordance with the enterprise policy. 

**Def: Unified Endpoint Management (UEM) is an enterprise-level endpoint management solution that can cover all endpoints, from PCs to laptops, from phones to other mobile devices, tablets, and even some wearables.**
- The idea behind UEM is to extend the function set from MDM to encompass all endpoint devices, including bringing more functionality under enterprise control. 

### Mobile Application Management (MAM)
Mobile devices bring a plethora of applications along with them into an enterprise. While MDM solutions can protect the enterprise from applications installed on a device, there is also a need to manage corporate applications on the device. The deployment, updating, and configuration of applications on devices requires an enterprise solution that is scalable and provides for the installation, updating, and management of in-house applications across a set of mobile devices.

**EXAM TIP: Distinguishing between MDM, UEM, and MAM applications is done by functionality. MAM controls in-house applications on devices. MDM controls the data on the device, segregating it from the general data on the device. UEM is a complete endpoint control solution that works across virtually every form of endpoint, mobile or not.**


### SEAndroid
**Def: Security Enhanced Android (SEAndroid) is a mobile version of the Security Enhanced Linux (SELinux) distribution that enforces mandatory access control (MAC) over all processes, even processes running with root/superuser privileges.
- SELinux has one overarching principle: default denial, anything not explicitly allowed is denied
 
## Enforcement and Monitoring
Your organization's policies regarding mobile devices should be consistent with your exiting computer security policies. Your training programs should include instruction on mobile device security. Disciplinary actions should be consistent. Your monitoring programs should be enhanced to include monitoring and control of mobile devices.

### Third-Party Application Stores
Many mobile devices have manufacturer-associated app stores from which apps can be downloaded to their respective devices. These app stores are considered by an enterprise to be third-party application stores, as the contents they offer come from neither the user nor the enterprise. 
- Apple App Store more secure than Google Play Store

### Rooting/Jailbreaking
**Def: The process by which the user escalates their privilege level, bypassing the operating system's controls and limitations.**
- User bypasses the OS-imported user restrictions.

**Def: Rooting a device is a process by which OS controls are bypassed, and this is the term frequently used for Android devices.**
- Whether the device is rooted or jailbroken, the effect is still the same: the OS controls designed to constrain operations are no longer in play and the device can do things it was never intended to do, either good or bad. 

**EXAM TIP: Rooting is used to bypass OS controls on Android, and jailbreaking is used to to escalate privileges and do the same on iOS devices. Both processes stop OS controls from inhibiting user behaviors.**

### Sideloading
**Def: The process of adding apps to a mobile device without using the authorized store associated with the device.**
- Currently only works on Android devices, as Apple has not enabled execution of any apps except those coming through the App Store. 
- Greater risk of malicious software due to lack of vendor screening

### Custom Firmware
**Def: firmware for a device that has been altered from the original factory settings.**
- May add functionality or new security holes
- Custom firmware should be used only on devices that do not have access to critical information

### Carrier Unlocking
Most mobile devices in the US are locked to a carrier, while in other parts of the world they are unlocked, relying upon a subscriber identity module (SIM) for connection and billing information.
- **Def: Carrier unlocking is the process of programming the device to sever itself from the carrier.** 
- This is usually done through the inputting of a special key sequence that unlocks the device.

### Firmware OTA Updates
Firmware essentially is software, it may be stored in a chip, but like all software, it sometimes requires updating.
- With mobile devices literally everywhere, the scale does not support brining the devices to a central location or connection for updating.

**Def: Firmware OTA (over-the-air) updates are a solution to this problem.**
- Its just like downloading something from the app store

### Camera Use
Cameras take photos of a lot of information that may be valuable
- Despite all the potential legal concerns, possibly the greatest concern of mobile device users is that their personal photos will be lost during a device wipe originated by the company

### SMS/Multimedia Message Service (MMS)/Rich Communication Services (RCS)
**Def: Short Message Service (SMS) and Multimedia Messaging Service (MMS) are standard protocols used to send messages, including multimedia content in the case of MMS, to and from mobile devices over a cellular network.**
- SMS is limited to text-only messages of fewer than 160 characters 
- MMS is more recent and designed to support multimedia content to and from mobile devices 

**Def: Rich Communication Services (RCS) is a protocol that is currently used alongside SMS and MMS.**
- RCS operates between the mobile device and the carrier and requires RCS-capable apps on both ends of the communication.
- RCS is intended to eventually replace both SMS and MMS

### External Media
**Def: External Media refers to any item or device that can store data.**
- External media can also deliver malware into the enterprise.

### USB On-The-Go (USB OTG)
**Def: An extension of USB technology that facilitates direct connection between USB OTG- enabled mobile devices.**
- USB OTG allows those devices to switch back and forth between the roles of host and device, including deciding which provides power (host) and which consumes power across the interface.
- USB OTG allows the connection of USB-based peripherals, such as keyboards, mice, and external storage, to mobile devices. 
- Most devices since 2015 are USB OTG compatible

### Recording Microphone
**Def: Recording Microphones can be used to record conversations, collecting sensitive data without the parties under observation even being aware of the activity.**

### GPS Tagging
**Def: GPS tagging or Geo-tagging is when photos taken with a camera enabled with GPS capabilities have location information embedded in the digital photo.**
- It is recommended to be disabled unless you had a specific reason

### Wi-Fi Direct/Ad Hoc
Wi-Fi typically connects a Wi-Fi device to a network via a wireless access point. Other methods exist, namely Wi-Fi direct and Wi-Fi ad hoc. 
- In Wi-Fi direct, two Wi-Fi devices connect to each other via a single-hop connection. In essence, one of the two devices acts as an access point for the other device. It only connects two devices but those two devices have all the bells and whistles of modern wireless networking including WPA2.

The primary difference between Wi-Fi ad hoc and direct is that in the ad hoc network, multiple devices can communicate with each other, with each device capable of communication with all other devices.

### Tethering
**Def: Tethering involves connecting a device to a mobile device that has a means of accessing a network for the purpose of sharing the network access.**
- Connecting a mobile phone to a laptop to charge the phone's battery is not tethering.
- Connecting a mobile phone to a laptop so that the laptop can use the phone to connect to the Internet is tethering.
- When you tether a device, you create additional external network connections.

### Hotspot
**Def: The term hotspot can refer to a specific piece of network equipment, an endpoint for a wireless solution, or in other respects the physical area in which it provides connectivity.**
- Typically a Wi-Fi endpoint, a hotspot provides a set of users a method of connecting to a network. 
- A network engineer will refer to a hotspot as the physical equipment that provides services over a specified geographic area, while a user will refer to it as a place they can connect to the network.

**EXAM TIP: Tethering involves the connection of a device to a mobile device to gain network connectivity. A hotspot can be tethered if the actual device is mobile, but if the device is fixed, it is not tethering.**

### Payment Methods
Payment methods involving NFC and biometrics/PIN are evolving. 

**Exam TIp: This section contains topics that can be tested with performance-based questions. It is not enough to simply learn the terms associated with the material. You should be familiar with how to determine the correct enforcement and monitoring solution based on a given scenario. The scenario will provide the necessary information to determine the best answer to the question. You should understand the differences between the item--from app stores, to OS protections, to connectivity options--sufficiently to be able to select the correct item based on the stated scenario.**

## Deployment Models
When determining how to incorporate mobile devices securely in your organization, you need to consider a wide range of issues, including how security will be enforced, how all the policies will be enforced, and, ultimately, what devices will be supported. 

**EXAM TIPS: BE prepared for performance-based questions that ask you to determine the correct mobile deployment model based on a given scenario.**

### Bring Your Own Device (BYOD)
**Def: BYOD deployment model has many advantages in business, and not just from the perspective of minimizing device cost for the organization.** 
- Users tend to prefer to have a single device rather than carry multiple devices
- Model is popular in small firms and in organizations that employ a lot of temporary workers

### Corporate-Owned, Personally Enabled (COPE)
**Def: In the corporate-owned, personally enabled (COPE) deployment model, employees are supplied a mobile device that is chosen and paid for by the organization, but they give permission to use it for personal activities.**

This allows the organization to control security functionality while dealing with the employee dissatisfaction associated with the traditional method of device supply, corporate-owned, business only (COBO).

### Choose Your Own Device (CYOD)
**Def: CYOD deployment is similar to BYOD in concept in that it gives users a choice in the type of device.**
- Organization constraints this choice to a list of devices that can be supported in the organization.

### Corporate-Owned
**Def: In the corporate-owned deployment model, also known as corporate-owned, business only (COBO), the company supplies employees with a mobile device that is restricted to company-only use.**
- The disadvantage to this model is that employees have to carry two devices--one personal and one for work.

**EXAM TIP: Expect performance-based questions for the different deployment models: BYOD, CYOD , COPE, and corporate owned. The correct answer is always in the details.**


### Virtual Desktop Infrastructure (VDI)
While it seems the deployment models are only associated with phones, this is really not the case, because personal computers can also be external mobile devices requiring connections at times. 

**Def: A virtual desktop infrastructure (VDI) solution can bring control to the mobile environment associated with non-corporate-owned equipment.**


# Questions
1. B
2. B
3. D
4. C (Three modes supported by Bluetooth 4.0 is classic, high speed, and low energy)
5. A
6. D
7. B
8. C
9. D
10. C



