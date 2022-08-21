# Chapter 14
# Embedded and Specialized Systems

## Embedded Systems
**Def: The name given to computers that are included as an integral part of a larger system, typically hardwired in.**

Ex: Printers, smart TVs, thermostats..

Designed with a single control purpose in mind and have virtually no additional functionality, but this does not mean they are free of risk or security concerns. 

The designers of embedded systems typically are focused on minimzing costs, with security seldom seriously considered as part of either the design or the implementation.

### Raspberry Pi
**Def: A highly successful, low-cost, single-board computer.**

A Raspberry Pi running a science fair project with no connectivity to the Web has a completely different scope than one that is connected to the Internet and being used to log sensititive data necessary for production in an enterprise setting.

Determining the risk profiles and addressing them as appropriate is still a needed and important task.

### Field Programmable Gate Arrays (FPGAs)
**Def: Electronic circuits that are programmed to perform a specific function.**

These semiconductor devices are based around a matrix of configurable logic blocks (CLBs) that are connected via programmable interconnects, and in essence the logic is programmed before use.

FPGAs are designed to be reprogrammed to the desired functionality requirements after manufacturing, and they can be typically be reprogrammed as designs of the functionality evolve. 

FPGAs and ASICs (application-specific integrated circuits) are found in a lot of custom devices, where a full-blown computer with an operating system and all that it entails is not needed.

### Arduino
**Def: A single-board microcontroller, not a full-fledged computer like the Raspberry Pi.**

The Arduino is simpler, designed to provide computer control to hardware projects without the overhead of a full computer, OS, and so on.

While the Raspberry Pi is designed as a computer, the Arduino is designed as a controller, specifically for interfacing with sensors and devices. 

The Arduino can respond to sensor levels and actuate devices based on programming that is loaded onto the device. 

This coding works when power is applied; if power is lost, once it is restored, the device can begin functioning again --unlike a computer, which would have to reboot and start over.

Expansion of the Arduino platform is done via a series of boards called shields that can add specific functionality in networking, display, data collection, and so on.

**Exam Tip: Understand static environments-- systems in which the hardware, OS, applications, and networks are configured for a specific function or purpose. These systems are designed to remain unaltered through their lifecycle, rarely requiring updates.**

---
## Supervisory Control and Data Acquisition (SCADA)/ Industrial Control System (ICS)
**SCADA is an acronym for supervisory control and data acquisition,  a system designed to control automated systems in cyber-physical environments.**

SCADA systems have their own smart components, each of which is an example of an embedded system.

Together they form a SCADA system, which can control manufacturing plants, traffic control lights, refineries, energy networks, water plants, building automation and environmental controls, and a host of other systems. 

A SCADA system is also known as a distributed control system (DCS) or an industrial control system (ICS), depending on the industry and configuration.

Wherever computers control a physical process directly, a SCADA system is likely involved. 

Most SCADA systems involve multiple components networked together to achieve a set of functional objectives. These systems frequently include a human-machine interface (HMI), where an operator can exert a form of directive control over the operation of the system under control.

Modern SCADA systems are no longer air gapped and therefore more suseptible to attack.

SCADA systems have been drawn into the secuirty spotlight with the Stuxnet attack on Iranian nuclear facilities, initially reported in 2010.
- Stuxnet is a malware designed to attack a specific SCADA system and cause failures, resulting in planet equipment damage.
- This attack was complex and well designed, crippling nuclear fuel processing in Iran for a significant period of time. 
- This attack rasied awareness of the risks associated with SCADA systems, whether connected to the Internet or not (Stuxnet crossed an air gap to hit its target)

### Facilities
SCADA systems find many uses in facilities, ranging from the building automation systems of the HVAC systems, to pumps for water pressure, escalators and elevators, and fire alarms-- the lists just keep going.

Some systems are seperated and others are interconnected with other larger systems/networks.

As for all systems, understanding how to get access to a system and securing those access points is key for securing this type of SCADA employment.

### Industrial
Industrial facilities have some of the same needs as other facilities--the computer control of various processes, such as security, environmental monitoring, fire alarms, and more.

The key element is to understand that virtually any facility has a data collection --data response system, whether it is a simple HVAC or thermostat system or a more complex system such as a surveillance or fire alarm system.

### Manufacturing
Manufacturing systems add another laer of computer-controlled processes to the industrial/facility mix-those of the actual manufacturing process itself. 

Manufacturing equipment is commonly computer controlled, using devices such as programmable logic controllers (PLCs), to execute a process-specific set of instructions based on sensor readings and actuator settings. 

Because the SCADA systems that are running your manufacturing are typically very critical to your enterprise, these systems require protection from attackers. The standard practice for this is one of strict network segmentation.

### Energy
Energy systems range from electrical to chemcial, petroleum, pipelines, nuclear, solar, hydrothermal, and more.

Each of these systems has multiple systems under computer control, typically using the same types of SCADA components as other categories already discussed. 

In the case of energy distribution, such as pipelines and electricity, a further complication is the distributed nature of these elements, where they are geographically spread out (in many cases in our communities).

The distribution of components "outside the corportate walls" adds a unique physical security aspect to these systems.

### Logistics
Logistics systems are the systems that move material form point A to point B. 

These systems can involve sea, surface (roads and rail), and air transport. 

There are two basic elements that will be under control: the transport system itself and the material being moved.

**Exam Tip: When examining SCADA systems, you have three things to worry about: the value of the information being protected, physical access to the system, and logical (typically network) access to the data. When examining the question, parse the question for the specific detail that matters.**

---
## Internet of Things (IOT)
**Def: A term used to describe a wide range of devices that connect directly via the Internet to create a distributed sensor and processing system to achieve a specific function.**

As opposed to general-purpose devices, like comuters and network-ing equipment, IoT devices are purpose built; they are designed to do a specific task. 

All these devices havea  couple similarities
1. They all have a network interface 
2. On that network interface is some compute platform
3. These devices can also be massed produced and at a relatively low cost

Functionality is king, meaning that security or anything that might impact new expanded functionality has to take a backseat. 

### Sensors
**Def: Devices that measure some physical item and return data that can be used by a system.**

Sensors come in an endless array of sizes, shapes, and physical constraints.

Sensors can measure temperatures, pressures, voltages, positions, humidity levels, the list goes on.

Sensors can return the data as either a digital or analog signal. 

### Smart Devices
Smart devices and devices that comprise the IoT have taken the world's markets by storm. 

From key fobs that can track the location of items via GPS, to cameras that can provide surveillance, to connected household appliances, TVs, dishwashers, refrigerators, crock pots, washers, and dryers -- anything with a microcontroller now seems to be connected to the Web so that it can be controlled remotely. 

The only thing that can be said with confidence about this revolution is someone will figure out a how and a why to connect virtually anything to the network. 

### Wearables
**Def: Wearable technologies include everything from biometric sensors measuring heart rate, to step counters measuring how far one walks, to smart watches that combine all these functions and more.**

These wearable devices are built using using very small computers that run a real-time operating system, usually built from a stripped-down Linux kernal. 

Things you can do to start protecting personal data include checking the default settings, checking the privacy settings, turning off location tracking, reading the privacy policies, and, where possible, using a passcode to protect your personal information (PI).

### Facility Automation
Low-cost sensors in an IoT package offer several advantages, including but not limited to, network delivery of data, significant data collection capability, and cost advantages with scale. 

Automation can improve risk because it removes errors and improves speed of response.

### Weak Defaults
Whenever items are manufactured or produced in large quantities, specific specializations such as default credentials are a challenge.  

The typical process is to have default credentials on a device and then expect the user to change them. 

**Def: weak defaults are a condition where default conditions are generally known, including admin account and password, leaving the system completely vulnerable to an attacker.**

**Exam Tip: IoT is all about connectivity of low-cost items at scale. Deployments of hundres, thousands, and even millions of devices have been done, and the data can provide great insights that can only be seen with data at scale. However, with that scale comes the challenge of managing and securing the large number of devices.**

---
## Specialized Systems
**Def: Systems designed for special purposes.**

Four primary types of specialized systems targeted are medical devices, vehicles, aircraft, and smart meters.

### Medical Systems
Medical systems is a very diverse group-- from small implantable devices, such as pace-makers, to multi-ton MRI machines.

They all have a direct connection to human life. 

Medical devices such as lab equipment and infusion pumps have been running on computer controls for years. 

The standard of choice has been an embedded Linux kernal that has been stripped of excess functionality and pressed into service in the embedded device.

Medical devices are manufactured under strict regulatory guidelines that are designed for static systems that do not need patching, updating, or changes. Any change would force a requalification--a lengthy, time-consuming, and expensive process. 

### Vehicle Systems
A modern vechile has not a single computer in it, but actually hundreds of them, all interconnected on a bus. 

The controller area network (CAN) bus is designed to allow multiple micro controllers to communicate with each other without a central host computer. 

Since 2008, all new U.S. and European cars must use a CAN bus, per SAE regulations -- a mandate engineers have willingly embraced as they continue to add more and more subsystems. 

Recent auto hacking has discovered several interesting things:
1. First, in defending allegations that some of its vechicles could suddenly accelerate without driver action, Toyota claimed that the only way to make a vehicle accelerate quickly is to step on the gas pedal--that software alone won't do. This was proven to be false. Hackers have demonstrated almost complete control over all functions of the Toyota Prius using computers and CAN bus commands.
2. Second, every automobile manufacturer has interpreted/ignored the reference protocol specification to varying degrees. 
3. Finally, as demonstrated by hackers at DEFCON, it is possible to disable cars in motion, over the Internet, as well as fool around with the entertainment console settings and other systems.

The bottom line is that, to function properly, newer vehicles rely on multiple computer systems, all operating semi-autonomously and with very little security. 

The pace of vehicle security is very slow compared to other areas of technological growth. 

### Aircraft Systems
Aircraft also have a significant computer footprint inside, as most modern jets have what is called an "all-glass cockpit," meaning the old individual gauges and switches have been replaced with a computer display that includes a touchscreen.

Patching the OS for aircraft systems is a difficult process because the industry is heavily regulated, with strict testing requirements. 

This makes for systems that, over time, will become vulnerable as the base OS has been thoroughly explored and every vulnerability mapped and exploited in non-aviation systems, and these use cases can port easily to aircraft. 

Recent revelations have shown that the in-flight entertainment systems, on standard Linux distros, are seperated from flight controls not by seperate networks, but by a firewall. This has led hackers to sound the alarm over aviation computing safety. 

### Smart Meters
Smart meters is the common name for the advanced metering infrastructure, a program initiated by the DoE to bring the functionality of remote automation to meters in utilities. 

Real-time two-way communications, computing infrastructure to analyze the data, and a whole host of new policies and procedures to take advantage of the automation have provided a revolution in utility operations. 

Managing the large-scale deployment of infrastructure in a secure fashion requires an extensive cryptographic setup, with some meters having multiple passwords for different levels of operation. 


**Exam Tip:  Specialized systems are custom built to serve a purpose, and the required level of security goes along with the purpose. If the data needs protecting, then the same problems and solutions used to fix them apply. In most specialized systems, the risk are significant and cryptographic solutions are designed into the system to limit access to authorized users.**

---

## Voice over IP (VoIP)
**Def: The transmission of voice communication over IP networks --is now a commonplace method of providing telephone services.**

VoIP makes telephone managment as easy as an app in the enterprise, but it also brings security risks and vulnerabliitles.

VoIP require protections from standard traffic-based attacks such as denial of service, but also need protections from spoofing. 

Authentication and the protection of the communication channels have been the province of the telephone company, but in VoIP there is no overarching phone company to manage these risks. 

Just as we have to secure systems like e-mail from outside, unauthorized users, we need to do the same with VoIP services. 

---
## Heating, Ventilation, Air Conditioning (HVAC)
Building-automation systems, climate-control systems, and HVAC systems are all example of systems that are managed by embedded systems.

The rise of hyper-connectivity has shown value in integrating independent HVAC systems. Having a "smart building" that reduces the use of building resources in accordance with the number and distribution of people inside increases efficiency and reduces costs. 

Interconecting these systems and adding in Internet-based central control mechanisms does increase the risk profile from outside attacks. 

These outside attacks could result in HVAC malfunction or failure, rendering a major office building uninhabitable due to heat and safety. 

---
## Drones
**Def: Drones, or unmanned aerial vehicles (UAVs), represent the next frontier of flight.**

These machines range from the small drones taht hobbyists can play with for under $300 to full-size aircrafts that can fly across oceans. 

Unlike normal aircraft, these pilots are on the ground, flying the device via remote control. 

UAVs have cameras, sensors, and processors to manage the information, and even the simple hobbyist versions have sophisticated autopilot functions. 

Because of the remote connection, UAVs are networked and operated either under direct radio control (rare) or via a networked system (much more common). 

---
## Multifunction Printers (MFPs)
**Def: Multifunction printers (MFPs), which combine a printer, scanner, and fax, have embedded compute power to act as a print server, manage the actual printing or scanning process, and allow complete network connectivity.**

These devices communicate in a bidirectional fashion, accepting print jobs and sending back job status, printer status, and other information to the computer. 

This has decoupled printign from the computer, making the pritner a stand-alone entity. The system that runs all these functions was designed to provide maximum functionality for the device, and security is more of an afterthought than a design element. 

As such, these devices have been shown to be hackable and capable of passing malware from the printer to the computer. 

---
## Real-time Operating Systems (RTOSs)
**Def: Real-time operating systems are designed for devices where the processing must occur in real time and data cannot be queued or buffered for any significant length of time.**

RTOSs are not general-purpose machines but are programmed for a specific purpose. 

They still have to deal with contention, and they have scheduling algorithms to deal with timing collisions, but in general an RTOS proccess each input as it is received, or within a specific time slice defined as the response time. 

Examples of RTOSs range from something as common as an anti-lock braking computer system in a car to something as complex as a robotic system used on an assembly line. 

Most general-purpose computer operating systems are capable of multitasking by design. This includes Windows and Linux. 

Multitasking systems make poor real-time processors, primarily because of the overhead associated with seperating tasks and processes.

RTOS-based software is designed to emphasize the thread in processing rather than handling multiple threads. 

The security implications surrounding real-time operating system's lie in their timing. Should an event do something that interferes with the system's ability to respond within its time allotment, then the system itself can fail in its task. 

Real-time operating  systems also tend to be specific to the degree that updates and patches tend not to be common, as the manufacturer of the system does not provide that level of support. 

---
## Surveillance Systems
Digital surveillance systems have entered the computing world through a couple of different portals. First, there is the world of high-end digital cameras that have networking  stacks, image processors, and even 4K video feeds. 

These are used in enterprises such as news organizations, which rely on getting the data live without extra processing delays. 

What is important to note is that most of these devices, although they are networked into other networks, have built-in virtual private networks (VPNs) that are always on, because the content is considered valuable enough to protect as a feature. 

The next set of cameras reveres the quantity and quality of characteristics. Where the high-end devices are fairly small in number, there is a growing segement of video surveillance cameras, including cameras for household surveillance, baby monitoring, and the like. 

**Exam Tip: VoIP, HVAC, drones/UAVs, MFPs, and surveillance systems have one weakness in common: access via the Internet. The same vector can be used against any connected system, and without defenses, these are typically very insecure systems. they have to be connected for functionality, and hence they need basic protections like passwords.**

---
## System on a Chip (SoC)
**Def: Refers to a complete computer system miniaturized on a single integrated circuit, designed to provide the full functionality of a computing platform on a single chip.**

Some SoC solutions come with memory, while others have the memory separate. 

SoCs are very common in the mobile computing market (phones and tablets) because of their low power consumption and efficient design. 

Some SoC brands have become household names because mobile phone companies have advertised their inclusion in a system, such as the Snap-dragon processor in Android devices. 

The programming of SoC systems can occur at several different levels. Dedicated OSs and applications can be written for them, such as the Android fork of Linux, which is specific to the mobile device marketplace.

The security implications of SoC-based systems is associated not with the specifics of SoC, but in the fact that they are ubiquitous in our technology-driven lives. 

Security issues are handled by the device, not the specific SoC aspect itself. 

---
## Communication Considerations
Embedded and specialized systems are useful for a purpose, and many times those purposes require communications across a network for other resources. 

The communication considerations for embedded and specialized systems are dependent on the service, what task it is doing, and the resources needed. 

The methods of communication are wide and varied, and the choice is usually dependent on the range needed and with whom the communication is needed. 

For short-distance, local communications, certain technologies can excel. For worldwide communications, others would work better. 

Adopting technologies already employed by users has advantages as well; for instance, why use a specialty radio circuit in an environment that already has Wi-Fi?

### 5G
5G is the largest generation mobile radio-based network. It is designed to connect virtually everyone and everything together, including machines, objects, and devices with a focus on higher data speeds and bandwidths. 

5G networks are more than just bigger pipes; the standard has many functional elements to improve both performance and efficiencies.

5G is in the process of being rolled out worldwide, and connectivity is via a cellular circuit--- either a phone, modem, or a chipset designed in a product. 

Just as having a full-blown server is overkill for a simple sensor, 5G may be overkill for many communication needs. If worldwide range, large bandwidth, and low latency are important, then 5G may be warranted, but if not, there are lower-cost alternatives.

### Narrow-Band Radio
**Def: Narrow-band radio communications use narrow bands of frequencies for low-data-rate communications**

While a low data rate may seem to be a big problem, not all systems have high-data-rate needs, and narrow-band radio offers advantages in range and power utilization.

Lower-power transmitters are the norm, as are significantly longer ranges. 

Ex: If a company has a bunch of drilling rigs over a large geographic area and needs to move relative small quantities of data between them, then narrow-band radio can be the ideal solution. 

### Baseband Radio
**Def: Baseband refers to the original bandwidth produced by a signal.**

For typical audio signals, it is  20-20,000 Hz. For a signal to be transmitted over a radio circuit, it is usually encoded or modulated in a manner that can then be blended with the radio wave, carrying the information in the changes on a radio wave. 

Baseband radio refers to the signal that is being transmitted and represents a single channel of communication.

Broadband radio is when multiple signals are bundled together for transmission, and equipment is typically required to separate out the individual communications. 

Baseband radio, by design, is very simple, as it only carries a single channel to manage communications across. 

### Subscriber Identity Module (SIM) Cards
**Def: A sim card is a device used to hold key information needed to conduct communications across telecommunication networks.**

A SIM card provides a means of identifying users and other key items of infromation when using telecommunication networks. 

When accessing a telecommunication network, one has to identify themselves for billing purposes. The SIM card provides the information needed by the network to attribute the call. 

Elements such as provider, serial numbers, and keys are stored on a universal integrated circuit card that acts as a standard for storing and managing this information on devices. 

SIMs are important because they can contain user data and authentication information as well as provide identity services. 

### Zigbee
**Def: a low-power mesh radio service used to connect sensors and basic devices.**

**Exam Tip: Communication needs are common among a lot of devices, but the methods vary. Understanding the limitations of the different methods and the security options is important.**

---
## Constraints
Specialized and embedded systems have a different set of constraints that they are designed to operate under. 

As these devices are built for a specific purpose, these limitations are actually design elements and are part of the ability of the system to perform its task in the expected environment.

### Power
Electronic circuits take power to operate, and it comes from one of several sources: a power supply connected to the grid, a battery, solar, or another type of device. 

Power is a key driver in many embedded and specialized systems because it is a true limiter. When the power supply is interrupted and no backup power supply exists, the device stops functioning.

Power drives many design elements because extra functionality that is not needed, including speed, only uses power and does not add to the functionality of the unit.

### Compute
The computer capability of embedded and specialized systems is another key component that is matched to the task the device is designed to accomplish

Excess compute power results in more power drain and less useful life on a battery charge.

The key point to remember is that computer power, power capacity, and useful lifetime without external power are all locked in a battle, each taking from the other two.

### Network
Network limitations are due to constraints from power and connectivity. 

Without direct connectivity, networking requires a radio transceiver, and this increases power demands. 

Leaving single-unit considerations aside, networking is the key value component behind the Internet of Things revolution. 

Managing large data flows places a burden on the central site, which if not properly planned for and executed becomes a constraint on the overall system operation.

### Cryptographic Functions 
Cryptographic functions can be essential to secure data during transmission, but this functionality comes at a price.

Some crypto requires extensive computational resources

### Inability to Patch
The inability to patch an item represents a security risk and a constraint.

Simply put, the ecosystem for most embedded devices is missing the means, the culture, and in many cases, the sheer ability to manage the patch process.

### Authentication
Authentication is an important predicate to security functionality. 

### Range
In most cases, range is a function of power --one of the true limitations of many specialized and embedded systems. 

One of the challenges of IoT deployments is getting them to the Internet, because there range is unlimited. However this comes at the cost of security/risk. 

### Cost
The functionality return for the cost of the unit justifies the design and deployment, so cost is to a degree baked in.

So, rather than viewing cost as a constraint, it is the factor that drives the creation of these solutions.

### Implied Trust
**Def: Trust that has not been specifically set up but yet exists.**

This makes for easier connectivity, but also opens doors for an attacker.

**Exam Tip: When questioned about constraints and specialized systems (not general-purpose computers), remember the ecosystem that the device is intended to run in and consider that when formulating the answer. Many times it is different for specialized/embedded systems than for a general-purpose computer.**

---
# Questions
1. B
2. C
3. D
4. C
5. B
6. C
7. C
8. C
9. B
10. D
