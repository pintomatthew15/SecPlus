# Chapter 27
# Incident Response, Policies, Processes, and Procedures

Normal operations in an IT enterprise include preparing for when things go wrong. One aspect of this is when things are not operating correctly, for reasons unknown, and the incident response (IR) process is used to determine the what, why, and where of the problem.
- This chapter looks at the concepts and procedures behind these specialized operations.

## Incident Response Plans
**Def: Incident Response plans describe the steps an organization performs in response to nay situation determined to be abnormal in the operation of a computer system or network.**
- Results of incidents can be categorized into classes. 
- A low-impact incident may not result in any significant risk exposure, so no action other than repairing the system is necessary. 
- A moderate-risk incident will require greater scrutiny and response efforts
- A high-level risk incident will require greater scrutiny and response efforts.

Two major elements play a role in determining the level of response.
- Information criticality is the primary determinant, and this comes from the data classification and the quantity of data involved. 
- The second factor is how the incident potentially affects the organization's operations

## Incident Response Process
**Def: The Incident Response Process is the set of actions security personnel perform in response to a wide range of triggering events.**
- Incident response activities at times are closely related to other IT activities involving IT operations.
- Incident response activities are not performed in a vacuum, but rather are intimately connected to many operational procedures, and this connection is key to overall system efficiency.

The six phases of incident response process and their sequencing are:
1. Preparation
2. Identification
3. Containment
4. Eradication
5. Recovery
6. Lessons Learned

**EXAM TIP: Know the six phases of the incident response process and the order in which they are performed: preparation, identification, containment, eradication, recovery, and lessons learned.**

### Preparation
**Def: Preparation is the phase of incident response that occurs before a specific incident.**
- Preparation includes all the tasks needed to be organized and ready to respond to an incident. 
- Items done in preparation include ensuring that the correct data events are being logged, the reporting of potential incidents is happening, and people are trained with respect to the IR process and their personal responsibilities.

### Identification
**Def: Identification is the process where a team member suspects that a problem is bigger than an isolated incident and notifies the incident response team for further investigation.**
- An incident is defined as a situation that departs from normal, routine operations. 
- The act of identification involves coming to a decision that the information related to the incident is worthy of further investigation by the IR team.

Identification can be done by many on the IT team, such as the help desk, admins, database personnel--in essence, anyone who finds something out of the ordinary that may be a real problem.

A key first step is to process the information and determine whether or not to invoke incident response processes.
- Incident information can come from a wide range of source, including logs, employees, help desk calls, system monitoring, security devices, and more.

The IR team examines the information, gathering additional information if necessary, to determine the cause of the incident. 

### Containment 
Once the IR team has determined that an incident has occurred, their first step is to contain the incident and prevent its spread.
- **Def: Containment is the set of actions taken to constrain the incident to a minimal number of machines.**
- This can be complex because, in many cases, containing the problem requires fully understanding it as well as its root cause and the vulnerabilities involved.

### Eradication
Once the IR team has contained a problem to a set footprint, the next step is to eradicate the problem.
- **Def: Eradication involves removing the problem, and in today's complex system environment, this may mean rebuilding a clean machine.**
- A key part of eradication is preventing reinfection 
- One of the strongest value propositions for virtual machines is the ability to rebuild quickly, making the eradication step relatively easy

### Recovery
After the issue has been eradicated, the recovery process begins. At this point, the investigation is complete and documented. 
- **Def: Recovery is the process of returning the asset into the business function and restoring normal business operations.**

### Lessons Learned
A postmortem session should collect **lessons learned** and assign action items to correct weaknesses and to suggest ways to improve.
- The lessons learned phase serves two distinct purposes
- First, to document what went wrong and allowed the incident to occur in the first place
- Second, to examine the incident response process itself

**EXAM TIP: The two main elements covered thus far overlap: incident response planning and the actual incident response process are both multistep items that can easily appear in questions on the exam. Be sure to pay attention to which element is being discussed in the question as well as what aspect of that topic. In other words, first determine if the question concerns the planning process or the IR process and pick the correct phase.**

## Exercises
One really doesn't know how well a plan is crafted until it is tested. 
- **Def: Exercises come in many forms and functions, and doing a tabletop exercise where the planning and preparation steps are tested is an important final step in the planning process.**

**EXAM TIP: If you're given a scenario, the details of the scenario will point to the appropriate part of the planning process. Therefore, pay attention to the details for the best answer.**

### Tabletop
**Def: A tabletop exercise is one that is designed for the participants to walk through all the steps of a process, ensuring all elements are covered and that the plan does not forget a key dataset or person.**
- This is typically a fairly high-level review designed to uncover missing or poorly covered elements 

This exercise aspect is not a one-time thing; it should be repeated after major changes to systems that impact the continuity of the operations plan or other major changes such as personnel turnover. 

### Walkthroughs
**Def: Walkthroughs examine the actual steps that take place associated with a process, procedure, or event.**
- Walkthroughs are in essence a second set of eyes, where one part either explains or demonstrates  the steps to perform a task while a second person observes. 
- Much more in depth and provides a deeper analysis 

### Simulations
**Def: A simulation is an approximation of the operation of a process or system that is designed to represent the actual system operations over a period of time.**
- The simulation can be used in place of systems or elements that re not practical to replicate during an exercise, such as a complex element like a chemical plant or time-consuming activity like a backup operation.

**EXAM TIP: The different types of exercise elements, tabletop exercises, walkthroughs, and simulations can be used together as part of an exercise package.**

## Attack Frameworks
**Def: Attack Frameworks provide a roadmap of the types of actions and sequence of actions used when attacking a system.**
- Frameworks bring a sense of structure and order to the multidimensional problem associated with defending a variety of systems against multiple different types of attackers with various objectives.

### MITRE ATT&CK
**Def: The MITRE ATT&CK framework is a comprehensive matrix of attack elements, including the tactics and techniques used by attackers on a system.**
- This framework can be used by threat hunters, red teamers, and defenders to better classify attacks and understand the sequential steps an adversary will be taking when attacking a system. 
- This framework enables personnel to plan and defend, even during an attack, and further it acts as a useful tool in assessing an organization's risk.

The MITRE ATT&CK framework has a fairly simple design, with the top row of the matrix covering activities such as initial access, execution, persistence, privilege escalation, defense evasion, credential access, discovery, lateral movement, collection, command and control, exfiltration, and impact.

**EXAM TIP: The MITRE ATT&CK framework is a knowledgebase of various real-world observations and attack techniques. It is often used by organizations for threat modeling.**

### The Diamond Model of Intrusion Analysis
**Def: The Diamond Model of Intrusion Analysis is a cognitive model used by the treat intelligence community to describe a specific event.**
- IT is based on the notion that an event has four characteristics, each comprising a corner of the diamond.

The diamond takes the following form:
1. **Adversary: a description of the attacker and their data.**
2. **Infrastructure: A description of what is being used in the attack, such as IP addresses, e-mails etc.**
3. **Capability: A description of what is being used (malware, stolen creds, tools)**
4. **Victim: The target**

**EXAM TIP: The Diamond Model enables intrusion analysis by placing malicious activity at four points of the diamond: adversary, infrastructure, capability, and victim.**

### The Cyber Kill Chain
**Def: The cyber kill chain is a model developed by Lockheed Martin as a military form of engagement framework.**
- Model has a series of distinct steps during a cyberattack-from the early recon statges to the exfiltration of the data.

The implementation is the following:
1. **Reconnaissance: Research and Identify targets.**
2. **Weaponization: Exploit vulnerabilities to enter.**
3. **Delivery: Deliver the payload (evil content).**
4. **Exploitation: Begin the payload attack on the system and gain entry.**
5. **Installation: Implement backdoors, persistent access, bots, and so on.**
6. **Command and Control: Communicate to outside servers for control purposes**.
7. **Action on Objective: Obtain the objective of the attack (for example, steal intellectual property).**

**EXAM TIP: Developed by Lockheed Martin, the Cyber Kill Chain is a framework used to defend against the chain of events an attacker takes, from the beginning of an attack to the end of an attack.**

## Stakeholder Management
**Def: Stakeholders are the parties that have an interest in a process or the outcome of a process.**
- Having a structure to manage communication with the various stakeholders is important to keep them properly informed and to separate the communication tasks from the operational tasks associated with responding to the incident. 
- Having a **stake holder management** process, including defined personnel roles and responsibilities, is essential for the management of the stakeholders and their relationships during incidents. 

## Communication Plan
Planning the desired reporting requirements, including escalation steps, is an important part of the operational plan for an incident.

A **communication plan** as part of the incident response effort that answers the preceding questions and defines responsibilities for communication is a key element to be developed during the preparation phase.

## Disaster Recovery Plan
**Def: A disaster recovery plan (DRP) is critical for effective disaster recovery efforts.**
- A DRP defines the data and resources necessary and the steps required to restore critical organizational processes.

Consider what your organization needs to perform its mission. That is what you start with.
- Don't forget physical resources (hardware, software...) but also personal
- Ask yourselves for each function: who, what, when, where, why, how

A good DRP must include the processes and procedures needed in order for your organization to function properly and ensure continued operation.


**NOTE: It is often informative to determine what category your various business functions fall into. You may find that certain functions currently being conducted are not essential to your operations and could be eliminated. IN this way, preparing for a security event may actually help you streamline your operational processes.**

## Business Continuity Plan
As in most operational issues, planning is a foundational element to success. This is true in business continuity, and the **business continuity plan (BCP)**. 
- **Def: A Business Continuity Plan represents the planning and advanced policy decisions to ensure the business continuity objectives are achieved during a time of obvious turmoil.**

The focus of a BCP is the continued operation of the essential elements of the business or organization. 
- Business continuity is not about operations as normal but rather about trimmed-down, essential operations only.

The focus on a DRP is on recovering and rebuilding the organization after a disaster has occurred. 
- The DRP is part of the larger picture, while the BCP is a tactical necessity until operations can be restored.

**EXAM TIP: Although the terms DRP and BCP may be used synonymously in small firms, in larger firms, there is a difference in focus between the two plans. The focus of the BCP is on continued operation of a business, albeit at a reduced level or through different means during some period of time. The DRP is focused on specifically on recovering from a disaster. In many cases, both combined in small firms and in many discussions. The DRP is part of the larger BCP process.**

## Continuity of Operation Planning (COOP)
Ensuring continuity of operations is a business imperative, as it has been shown that businesses that cannot quickly recover from a disruption have a real chance of never recovering or going out of business. 
- The overall goal of **continuity of operation planning (COOP) is to determine which subset of normal operations needs to be continued during periods of disruption.**

**EXAM TIP: The COOP is focused on continuing business operation, whereas the BCP is focused on returning a business to functioning profitably, even if at a reduced level or capacity. Government agencies, where service is essential and costs can be dealt with later, focus on COOP, while many businesses have to focus on DRP and BCP.**

## Incident Response Team
**Def: The cyber incident response team (CIRT) is composed of the personnel who are designated to respond to an incident.**
- The incident response plan should identify the membership and backup members, prior to an incident occurring. 
- Once an incidence response begins, trying to find personnel to perform tasks only slows down the function, and in many ways would make it unmanageable. 

A critical step in incident response planning is to define the roles and responsibilities of the incident response team members.

There are several specific roles that are unique to all IR teams: the team leader, the tam communicator, and an appropriate bevy of SMEs.

## Retention Policies
**Def: Data retention is the storage of data records.**
- Maintaining data stores for longer than is required is a source of risk, as is not storing the information long enough.
- Failure to maintain the data in a secure state can also be a retention issue, as is not retaining it. 

**EXAM TIP: Data retention policies differ by organization. However, some information may be subject to regulations requiring specific data retention rules.**

# Questions
1. A
2. B
3. B
4. B
5. C
6. D
7. A
8. A,B,D
9. C
10. C

100! 