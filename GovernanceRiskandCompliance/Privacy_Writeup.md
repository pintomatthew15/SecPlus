# Chapter 35 (Last one!)
# Privacy

Data security and privacy practices are interrelated because of the basic premise that to have privacy, you must have security. Privacy is defined as the control you exert over your data, and security is a key element of that control.
- **Def: Data privacy in an organization is the prevention of unauthorized use of data held by the organization.**
- Elements that enable data privacy efforts include properly labeling and handling sensitive data, assigning responsibility for protecting data, and securely storing retained data, all of which are covered in this chapter. 

## Organizational Consequences of Privacy Breaches
When a company loses data that it has stored on its network, the term used is **data breach**. 
- Data breaches have become an almost daily news item, and the result is that people are becoming desensitized to their occurrence.
- Data breaches act as a means of notification that security efforts have failed.

Verizon publishes an annual data breach report that examines the types and causes of data breaches over the previous calendar year.
- These results are presented in multiple forms, by attribution to attack type, attacker type, industry, geographic region, company size, and more, providing a significant level of detailed analysis into the incidents.

### Reputation Damage
**Def: Reputation damage is a form of damage against a firm's brand.**
- Having to notify all customers of a breach/disclosure event is truly damaging to a firm's brands.

### Identity Theft
**Def: Identity theft occurs when a criminal, using stolen information, assumes the identity of another individual to obtain and use credit in the victim's name.**
- If the data disclosure results in loss of customer personal information, regulations may hold a firm responsible for sharing in the risk of identity theft for the victims.

### Fines
Regulatory agencies, such as the Federal Trade Commission (FTC), have the ability to levy fines when regulations are not followed. 
- Fines are not minor

### IP Theft
One of the primary targets of an attacker on a system is intellectual property.
- **Def: IP theft is a major organizational consequence when it occurs, because when it occurs, the damage may not become evident until the material is used by a competitor.**

**EXAM TIP: Be aware that organizational consequences of data privacy breaches can result in reputational damage, identity theft, fines, or IP theft.**

## Notifications of Breaches
In an ideal world, there would never be any data breaches, so there would never be a need for processes in the event of data breaches.
- Understanding and being prepared to issue **notifications of breaches** in accordance with these laws and directives is important, because once a breach occurs, the timelines to do the correct things are short and the penalties can be significant.

Breach notification laws and regulations typically have specific definitions of what comprises a breach, what entities are covered, what the specific notification requirements are, and key elements such as delays at the request of law enforcement agencies.

### Escalation
When a data breach occurs in the enterprise, it is important to have a process for **escalating** the incident up through your organization.
- Most data breaches are discovered as part of some incident up through your organization. 
- Failure to escalate a breach to the appropriate authorities can result in outside legal and financial risk, and thus management needs to be made aware of the incident and the progress towards the firm's responsibilities.

### Public Notifications and Disclosures
Many laws and regulations covering information breaches require public disclosure of computer security breaches in which unencrypted confidential information of any resident may have been compromised. 
- While there are no universal laws or regulations in this area, most have some form of public disclosure requirement. 

## Data Types
Data exists in many forms and is stored in systems that are used as part of business processes.
- Data management is a complex set of tasks that serve the purpose of protecting the data from a wide range of risks, including loss.
- Its easier to manage data when it is grouped into data types

### Classifications
Effective data **classification** programs include measures to ensure data sensitivity labeling and handling so that personnel know whether data is sensitive and understand the levels of protection required.

Training plays an important role in ensuring proper data handling and disposal. 
- Personnel are intimately involved in several specific tasks associated with data handling and data destruction/disposal.

A key component of IT security is the protection of the information processed and stored on the computer systems and network.
- Not all information is of equal importance or sensitivity.

The most widely known system of classification of information is implemented by the US government, which classifies information into categories such as: Confidential, Secret, and Top Secret.

#### Public 
**Def: Public data is data that can be easily seen by the public and has no needed protections with respect to confidentiality.**
- It is important to protect the integrity of public data, lest one communicate incorrect data as being true.

#### Private
**Def: Data is labeled as private if its disclosure to an unauthorized party would potentially cause harm or disruption to the organization.**
- The term private data is usually associated with personal data belonging to a person and less often with corporate entities.

#### Sensitive 
**Def: Sensitive data is a generalized term that typically represents data classified as restricted from general or public release.**
- This term is often used interchangeably with confidential data.

#### Confidential
**Def: Data is labeled confidential if its disclosure to an unauthorized party would potentially cause serious harm to the organization.**
- This data should be defined by policy, and that policy should include details regarding who has the authority to release the data.

**EXAM TIP: The difference between critical and confidential data lies in the level of potential damage should the information be released.**

#### Proprietary
**Def: Proprietary data is data that is restricted to a company because of potential competitive use.**
- If a company has data that could be used by a competitor for any particular reason, then it needs to be labeled and handled in a manner to protect it from release to competitors.

**EXAM TIP: Learn the differences between the data sensitivity labels so you can compare and contrast terms confidential, private, public, and proprietary. The differences are subtle but will be important to determine the correct answer.**

### Personally Identifiable Information (PII)
**Def: A set of elements that can lead to the specific identity of a person is referred to as personally identifiable information (PII).
- **CAUTION: AS little information as a ZIP code, gender, and date of birth can resolve to a single person.**

PII is an essential element of many online transactions, but it can also be misused if disclosed to unauthorized parties. 
- For this reason, it should be protected at all times, by all parties that possess it. 

**EXAM TIP: PII refers to information that can be used to distinguish or trace an individual's identity, either alone or when combined with other personal or identifying information that is linked or linkable to a specific individual.**

#### Health Information
The Health Insurance Portability and Accountability Act (HIPAA) regulations define **protected health information (PHI) as "any information, whether oral or recorded in any form of medium" that involves specific health details of an  individual.**

HIPAA's language is built upon the concepts of PHI and Notice of Privacy Practices (NPP).

**EXAM TIP: Know the difference between PII and PHI, and don't jump to the wrong one on the exam.**

#### Financial Information 
**Financial information** is a major source of PII. 
- One of the most sought-after types of PII because it is easiest type of information to monetize.

#### Government Data
Government data can include PII about people, and this information needs protection in accordance with current rules and regulations.

#### Customer Data
**Def: Customer data is the primary source of PII in an enterprise's systems.**
- This info was collected in response to a specific business need, and it requires appropriate levels of protection to prevent disclosure or release.

## Privacy-Enhancing Technologies
One principal connection between information security and privacy is that without information security, you cannot have privacy.
- If privacy is defined as the ability to control information about oneself, then the aspects of confidentiality, integrity, and availability from information security become critical elements of privacy 
- An application or tool that assists in such protection is called a privacy-enhancing technology (PET).

Encryption is at the top of the list of PETs for protecting privacy and anonymity.
- Tor routing to permit anonymous communications, coupled with high-assurance, low-cost cryptography, has made many web interactions securable and safe from eavesdropping.

Other PETs include small application programs called cookie cutters that are designed to prevent the transfer of cookies between browsers and web servers.
- Some cookie cutters block all cookies, while others can be configured to selectively block certain cookies. 
- Some cookie cutters also block sending of HTTP headers that might reveal personal information. 
- Other PETs are available to PC users, including encryption programs that allow users to encrypt and protect their own data, even on USB keys.

### Data Minimization 
**Def: Data minimization is one of the most powerful privacy-enhancing technologies.**
- In a nutshell, it involves not keeping what you don't need.
- One important outcome is that when a breach/disclosure occurs, the reach of the PII loss is limited.

While you may need to have a reasonable amount of PII to process and ship an order, once that process is concluded, do you need the data?

### Data Masking
**Def: Data masking involves the hiding of data by substituting altered values.**
- A mirror version of the database is created, and data modification techniques such as character shuffling, encryption, and word or character substitution are applied to change the data.
- Like the " ** " thing for passwords"

**EXAM TIP: Data masking hides personal or sensitive data but does not render it unusable.**

### Tokenization
**Def: Tokenization is the use of a random value to take the place of a data element that has traceable meaning.**
- Ex: in a credit card all you need to remember is the CVC
- If this was revealed to a third party, nothing changes

Tokens are used all the time in data transmission systems involving commerce because they protect the sensitive information from being reused or shared, yet they maintain the desired nonrepudiation characteristics of the event.
- Tokenization is not an encryption step because encrypted data can be decrypted

**EXAM TIP: Tokenization assigns a random value that can be reversed or traced back to the original data.**

### Anonymization
**Def: Data anonymization is the process of protecting private or sensitive information by removing identifiers that connect the stored data to an individual.**
- Separating the PII elements such as names, SSN, and addresses from the remaining data through a data anonymization process retains the usefulness of the data but keeps the connection to the source anonymous.

### Pseudo-Anonymization
**Def: Pseudo-anonymization is a de-identification method that replaces private identifiers with fake identifiers or pseudonyms.**
- Not all uniquely identifying fields are changed because some, such as DOB, may need to be preserved to maintain statistical accuracy.

**EXAM TIP: Be sure you can identify the various privacy-enhancing technologies. Know what they do and how they are implemented.**

## Roles and Responsibilities
Multiple personnel in an organization are associated with the control and administration of data.
- These **data roles** include data owners, data controllers, data processors, data custodian/stewards, and users.
- The leadership of this effort is under the auspices of the data privacy officer.

### Data Owners
All data elements in an organization should have defined requirements for security, privacy, retention, and other business functions.
- It is the responsibility of the designated  **data owner** to define these requirements.

### Data Controller
**Def: The data controller is the person responsible for managing how and why data is going to be used by the organization.**
- Under GDPR and other privacy laws, the data controller is the position responsible for protecting the privacy and rights of the data's subject, such as the user of a website. 
- There can be multiple data controllers in an organization, with responsibilities over different sets of data.

**EXAM TIP: In the European Union (EU), General Data Protection Regulation (GDPR) classifies the data controller as the data manager. In other words, the data controller manages the data.**

With respect to data with privacy implications, under most privacy regulations and GDPR, the data controller is responsible for deciding the following.
- What data is collected
- Where and how it is used
- With whom and how data is shared
- How long the data is kept and how it is disposed at the end of life (EOL)

### Data Processor
**Def: The data processor is the entity that processes data given to it by the data controller.**
- Data processors do not own the data, nor do they control it.
- Their role is the manipulation of data as part of business processes. 

With respect to data with privacy implications, under most privacy regulations and GDPR, data processors are responsible for the following:
- Developing and implementing IT processes and systems that manage personal data
- Implementing security measures that would safeguard personal data
- Using tools and strategies to properly handle personal data

### Data Custodian/Steward
**Def: A data custodian or data steward is the role responsible for the day-to-day caretaking of data.**
- The data owner sets the relevant policies, and the steward or custodian ensures they are followed.

### Data Privacy Officer (DPO)
**Def: The data privacy officer (DPO) is the C-level executive who is responsible for establishing and enforcing data privacy policy and addressing legal and compliance issues.**
- Data minimization initiatives are also the responsibility of the data privacy officer. 

The data privacy officer also plays an important role if information on European customers is involved because the EU has strict data protection (privacy) rules.
- The privacy officer who is accountable for the protection of consumer data from the EU must ensure compliance with EU regulations.

**EXAM TIP: The data privacy officer is responsible for ensuring legal compliance with data privacy regulations.**

## Information Lifecycle
Information has a lifecycle--a beginning, a middle, and, at some point, an end.
- Understanding the lifecycle of information assets--from the point of collection, use, and storage as well as how the assets are shared, protected, and ultimately destroyed is important if one is to properly handle the information.
- Not all information has the same time periods, or even steps, associated with it, so lifecycles are unique to different information sources and elements.

## Impact Assessment
**Def: A privacy impact assessment (PIA) is a structured approach to determining the gap between desired privacy performance and actual privacy performance.**
- A PIA is an analysis of how PII is handled through business processes and an assessment of risks to the PII during storage, use, and communication.
- A PIA provides a means to assess the effectiveness of a process relative to compliance requirements and to identify issues that need to be addressed.
- A PIA is structured with a series of defined steps to ensure a comprehensive review of privacy provisions.

**EXAM TIP: Organizations that collect, use, store, or process personal information are required to conduct a privacy impact assessment.**

The following steps comprise a high-level methodology and approach for conducting a PIA:
1. Establish PIA scope: Determine the departments involved and the appropriate representatives. Determine which applications and business processes need to be assessed. Determine applicable laws and regulations associated with the business and privacy concerns.
2. **Identify key stakeholders**: Identify all business units that use PII. Examine staff functions such as HR, Legal, IT, Purchasing, and Quality Control.
3. **Document all contact with PII**
4. **Review legal and regulatory requirements including any upstream contracts**: The sources are many, but some commonly overlooked issues are agreements with suppliers and customers over information-sharing rights.
5. **Document gaps and potential issues between requirements and practices**: All gaps and issues should be mapped against where the issue was discovered and the basis (requirement or regulation) that the gap maps to.
6. **Review findings with key stakeholders to determine accuracy and clarify any issues**: Before the final report is written, any issues or possible miscommunications should be clarified with the appropriate stakeholders to ensure a fair and accurate report.
7. **Create a final report for management.**

## Terms of Agreement
**Def: The legal description of terms of agreement is a set of items that both parties agree upon before some joint activity.** 
- This is used all the time with any external-facing interface, where you have the responding party agree to a published terms of agreement document before granting them access or processing their data elements. 
- This becomes a license that binds the parties to the terms the business wishes to enforce

## Privacy Notice
**Def: A privacy noticed is an exterior-facing statement that describes how the organization collects, uses, retains, and discloses personal information.**
- Privacy notices are also referred to as a privacy statement or a fair processing statement.
- The common elements of a privacy notice include the following:
	- When you collect personal information
	- Why you collect personal information
	- What information is collected
	- How the information will be protected
	- When the information can or will be shared
	- Who to contact and where questions should be directed concerning the notice
	- How to opt out or opt in
	- An effective dat of the document

**EXAM TIP: The key concept to note is that a privacy policy is internally focused, telling employees what they may do with personal information whereas a privacy notice is externally facing, telling customers, regulators, and other stakeholders what the organization does with personal information.**

# Questions
1. B
2. A
3. A
4. D
5. D (private data frequently refers to personal data)
6. B
7. B
8. C
9. C
10. A








