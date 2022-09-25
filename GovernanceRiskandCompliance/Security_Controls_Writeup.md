# Chapter 31
# Security Controls
**Def: Security controls are the tools used to reduce risk in the enterprise.**
- There are many different types of security controls, and this chapter looks at different categories and types to provide a means of understanding and classifying controls.

## Security Controls
**Def: Security controls are the mechanisms employed to minimize exposure to risk and mitigate the effects of loss.**
- Using the security attributes of confidentiality, integrity, and availability (CIA) associated with data, it is incumbent upon the security team to determine the appropriate set of controls to achieve the security objectives.

Controls can be of a variety of types, as described in this chapter.

**NOTE: The National Institute of Standards and Technology (NIST) provides a catalog of controls in its NIST SP 800-53 series. The current revision 5, lists over 600 controls grouped into 18 functional categories. The 18 functional categories are grouped under three major categories: management, technical, and operational. Although the vast majority of these controls are associated with the electronic security of information, many of them extend also into the physical world.**

**EXAM TIP: The types of security controls are commonly tested on the exam--memorization is recommended.**

## Categories
Three categories of security controls are specified in a variety of defining documents, and these categories have become the de facto standard for the cybersecurity industry.
- The use of categories separates the controls into separate groups based on what the control users as its lever: managerial activity, operational activity, or technical control.

### Managerial
**Def: Managerial controls are those that are based on overall risk management.**
- These security controls focus on the management of risk or the management of the cybersecurity system.
- The use of cybersecurity audits is an example of a managerial control

**NOTE: The NIST SP 800 series refers to managerial controls as management controls.**

### Operational 
**Def: An operational control is a policy or procedure used to limit security risk.**
- These security controls are primarily implemented and executed by people, as opposed to systems.
- Instructions to guards are an example of an operational control

### Technical
**Def: A technical control uses some form of technology to address a physical security issue.**
- These security controls are primarily implemented and executed by the information system through mechanisms contained in its hardware, software, or firmware components.
- Biometrics is an example of a technical control

**EXAM TIP: The main difference between operational and technical controls is that operational controls are those that people initiate and follow, whereas technical controls are typically automated and involve a machine to execute.**

## Control Types
Controls can also be categorized by **control type**. The cybersecurity industry recognizes several different control types, and while these categories can be descriptive, they are not a taxonomy because they are not necessarily exclusive.
- Controls can fit into multiple types, depending on deployment and use. 
- A door lock is an example of both a physical control and preventative control

### Preventative
**Def: A preventative control is one that prevents specific actions from occurring, such as a mantrap prevents tailgating.**
- Preventative controls act before an event, preventing it from advancing.
- A firewall is an example of a preventative control, as it can block access to a specific resource

**EXAM TIP: The key element in passing Exam Objective 5.1 is the ability to compare and contrast various types of controls. How are they alike (compare) and how are they different (contrast)? Understanding the differences can be subtle. For instance, do laws with punishment, if enforced, prevent attacks? Laws may deter attackers, but they do not prevent them from attacking if the deterrent doesn't dissuade them from deciding to attack.**

### Detective
**Def: A detective control is one that facilitates the detection of a physical security breach.**
- Detective controls act during an event, alerting operators to specific conditions.
- Alarms are common examples of detective controls. 
- An IDS is an example of an IT security alarm that detects intrusions.

### Corrective
**Def: A corrective control is sued after an event, in an effort to minimize the extent of damage.**
- Load balancers and redundant systems act to reduce the risk from system overloading and are thus corrective controls.
- Backups area prime example of corrective control, as they can facilitate rapid resumption of operations.

### Deterrent
**Def: A deterrent control acts to discourage the attacker by reducing the likelihood of success from the perspective of the attacker.**
- Any control that increases the cost to an attacker is a deterrent control.
- An example would be laws and regulations that increase punishment, increasing risk and costs for the attacker. 
- Another example would be the use of salts for password hashes to increase the cost of building rainbow tables.

### Compensating
**Def: A compensating control is one that is used to meet a requirement when there is no control available to directly address the threat.**
- Fire suppression systems do not prevent fire damage, but if properly employed, they can mitigate or limit the level of damage from fire.

**EXAM TIP: The previous five types of controls tend to be exclusive of each other--they describe the point of interaction of the control with the attacker's tools, techniques, and processes.**

## Physical
**Def: A physical control is one that prevents specific physical actions from occurring, such as a mantrap prevents tailgating.**
- Physical controls prevent specific human interaction with a system and are primarily designed to prevent accidental operation of something.
- Physical controls act before an event, preventing it from actually occurring.
- The use of covers over critical buttons is one example, as is a big red "STOP" button, positioned so it is easily reachable.

**EXAM TIP: Physical controls are separate from the previous descriptors and can be used independently of them. It is possible to have a control that is technical, physical,  and preventative control (for example, a door lock).** 

# Questions
1. B
2. D
3. C (A penetration test is a form of risk assessment and this is a managerial action, as it advises management of the current risk posture associated with the system.)
4. C
5. A, D
6. A
7. B
8. D 
9. A (know the difference between type and category)
10. B

