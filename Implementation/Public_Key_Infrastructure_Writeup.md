# Chapter 25
# Public Key Infrastructure

**Def:** **public key infrastructure (PKI) provides all the components necessary for different types of users and entities to be able to communicate securely and in a predictable manner.**
- A PKI is made up of hardware, applications, policies, services, programming interfaces, cryptographic algorithms, protocols, users, and utilities. 
- These components work together to allow communication to manage asymmetric keys facilitating the use of public key cryptography for digital signatures, data encryption, and integrity.

**THIS CHAPTER IS A GOOD CANDIDATE FOR PERFORMANCE BASED QUESTIONS**

## Public Key Infrastructure (PKI)
A PKI is composed of several components, all working together to handle the distribution and management of keys in a public key cryptosystem.
- Keys are carried via a digital structure known as a **certificate**.
- Other components, such as certificate authorities and registration authorities, exist to manage certificates.

Man-in-the-middle-attack: 
1. John and Diane want to communicate and all public keys are posted in a public directory
2. Katie replaces John's public key with her key in the publicly accessible directory.
3. Diane extracts what she thinks is John's key but is in fact Katie's key.
4. Katie can now read messages Diane encrypts and sends to John.
5. After Katie decrypts and reads Diane's message, she encrypts it with John's public key and sends it on to him so he will not be the wiser. 

There needs to be a way to verify an individual's identity, to ensure that a person's public key is bound to their identity and thus ensure that the previous scenario cannot take place. 

In PKI environments, entities called registration authorities (RAs) and certificate authorities (CAs) provide services similar to those of the DMV. 
- If John wants a license he needs to show his passport, birth certificate, etc
- If DMV satisfied, they will create a driver's license which proves ID.
- While people may not trust John, they do trust the DMV

In PKI context, while some variations exist in specific products, the RA will require proof of identification from the individual requesting a certificate and will validate this information. 
- The RA will then advise the CA to generate a certificate
- The CA will digitally sign the certificate using its private key.
- The use of the private key assures the recipient that the certificate came from the CA. 

**EXAM TIP: A registration authority (RA) verifies digital certificate requests and forwards them to a certificate authority (CA). The CA is a trusted organization that validate and issues digital certificates.**

This is commonly referred to as a **third-party trust model.** Public keys are components of digital certificates, so when Diane verifies the CA's digital signature, this verifies the certificate is truly John's and that the public key the certificate contains is also John's. 

**EXAM TIP: Make sure you understand the role of PKI in managing certificates and trust associated with public keys.**

### Key Management
The whole purpose of PKI is to provide the structure and components necessary for an organization to manage cryptographic keys that need to be shared between entities.
- Without a certificate, key is just a series of numbers. 
- The certificate stores the metadata of the key.
- Organizations must undertake key management to ensure keys enable proper cryptography and do not cause security issues.

### Certificate Authority (CA)
**Def: The trust authority that certifies individuals' identities and creates electronic documents indicating that individuals are who they say they are.**
- That document is the digital certificate and it establishes an association between the subject's identity and a public key.
- Private key of the recipient is stored separately

CA is multi-component and must ensure that each component remains uncompromised.

Every CA should have a certification practices statement (CPS) that outlines how identities are verified; the steps the CA follows to generate, maintain, and transmit certificates; and why the CA can be trusted to fulfill its responsibilities.
- It describes how keys are secured, what data is placed in the certificate, and how revocations will be handled.

The certificate server is the actual service that issues certificates based on the data provided during the initial registration process
- The server constructs and populates the digital certificate with the necessary information and combines the user's public key with the resulting certificate.
- The certificate is then signed with the CA's private key

### Intermediate CA
**Def: Intermediate CAs function to transfer trust between different CAs.**
- The path of trust is walked up from the subordinate CA to the higher-level CA; in essence, the subordinate CA is using the higher-level CA as a reference.

### Registration Authority (RA)
**Def: A registration authority (RA) is the PKI component that accepts a request for a digital certificate and performs the necessary steps of registering and authenticating the person requesting the certificate.**
- Most CAs offer a series of classes of certificates with increasing trust by class.

Each higher class of certificate can carry out more powerful and critical tasks than the one below it. 
- For different classes you may be asked to provide more personally identifying information. 

### Certificate Revocation List (CRL)
The CA provides protection against bad certificates by maintaining a **certificate revocation list (CRL), a list of serial numbers of certificates that have been revoked.**
- The CRL also contains a statement indication why the individual certificates were revoked and a data when the revocation took place.
- Expired certificates are not the same of revocation

The CA is the entity responsible for the status of the certificates it generates; it needs to be told of a revocation, and it must provide this information to others. 
- The CA is responsible for maintaining the CRL and posting it in a publicly available directory.

**EXAM TIP: The certificate revocation list is an essential item to ensure a certificate is still valid. CA post CRLs in publicly available directories to permit automated checking of certificates against the list before certificate use by a client. A user should never trust a certificate that has not been checked against the appropriate CRL. 

The mechanism used to protect the integrity of a CRL is a **digital signature**. 
- The CA's revocation service creates a digital signature for the CRL.
- To validate a certificate, the user accesses the directory where the CRL is posted, downloads the list, and verifies the CA's digital signature to ensure that the proper authority signed the list and to ensure that the list was not modified in an unauthorized manner.
- The user then looks through the list to determine whether the serial number of the certificate that he is trying to validate is listed. 

One last option for checking distributed CRLs in an online service. 
- When a client user needs to validate a certificate and ensure that it has not been revoke, he can communicate with an online service that will query the necessary CRLs available within the environment.

### Certificate Attributes
A digital certificate binds an individual's identity to a public key, and it contains all the information a receiver needs to be assured of the identity of the public key owner. 
- The certificates are created and formatted based on the X.509 standard, which outlines the necessary fields of a certificate and the possible values that can be inserted into the fields.

The latest version of X.509 is v3, and the fields it contains are described below:
- **Certificate Version:** v1 = 0, v2= 1, v3 = 2
- **Serial Number:** a nonnegative integer assigned by the certificate issuer that must be unique to the certificate
- **Signature Algorithm Parameters (optional**): The algorithm identifier for the algorithm used by the CA to sign the certificate. The optional parameters field is used to provide the cryptographic algorithm parameters used in generating the signature.
- **Issuer**: Identification for the entity that signed and issued the certificate. This must be a Distinguished Name within the hierarchy of CAs.
- **Validity Not valid before time, Not valid after time:** Specifies a period of time during which the certificate is valid.
- **Subject**: The Distinguished Name for the certificate owner. 
- **Subject Public Key Info**: An encryption algorithm identifier followed by a bit-string identifier for the subject of the certificate.
- **Issuer Unique ID**: Optional for v2 and v3. This is a unique bit-string identifier for the CA that issued the certificate.
- **Subject Unique ID:** Optional for v2 and v3. This is a unique bit-string identifier for the subject of the certificate.
- **Extensions Extension ID, Critical Extension, Value**: Optional for v3. The extensions area consists of a sequence of extension fields containing an extension identifier, a Boolean field indicating whether 
- **Thumbprint Algorithm**: Identifies the algorithm used by the CA to sign this certificate. This field must match the algorithm identified in the Signature Algorithm field.
- **Thumbprint**: The signature is the bit-string hash value obtained when the CA signed the certificate. The signature certifies the contents of the certificate, binding the public key to the subject.

### Online Certificate Status Protocol (OCSP)
One of the protocols used for online revocation services is the **Online Certificate Status Protocol (OCSP)**, a request and response protocol that obtains the serial number of the certificate that is being validated and reviews the CRLs for the client. 

**EXAM TIP: Certificate revocation checks are done either by examining the CRL or using OCSP to see if a certificate has been revoked.**

### Certificate Signing Request (CSR)
**Def: A certificate signing request (CSR) is the actual request to a CA containing a public key and the requisite information needed to generate a certificate.**
- The CSR contains all identifying information that is to be bound to the key by the certificate-generation process.
### Common Name (CN)
**Def: The common name field (CN) is represented in the Subject field of the certificate and is the fully qualified domain name (FQDN) for which the certificate is valid.** 
- A common representation in the subject line of a certificate may contain the Common Name and other elements, such as Organization, Location, State, and Country

Example:
- CN: google.com
- O = Google LLC
- L = Mountain View
- S = Claifornia
- C = US

**Def: Distinguished Name (DN) is a term that describes the identifying information in a certificate and is part of the certificate itself.**
- A certificate contains DN information for both the owner or requestor of the certificate.

### Subject Alternative Name (SAN)
**Def: Subject Alternative Name (SAN) is a field (extension) in a certificate that has several uses.**
- In certificates for machines, it can represent the FQDN of the machine. 
- For users, it can be the user principal name (UPN
- In the case of an SSL certificate, it can indicate multiple domains across which the certificate is valid.

**NOTE: SAN certificates allow you to secure a primary domain and then add additional domains to the Subject Alternative Name field of the certificate. For example, you an secure all these domains with a single SAN certificate:
- www.example.com
- email.example.com
- intranet.example.com
- www.example.net

### Expiration
A certificate itself has a lifetime that can be different from the key pair's lifetime.
- The certificate's lifetime is specified by the validity dates inserted into the digital certificate.
- These are beginning and ending dates indicating the time period during which the certificate is valid.

## Types of Certificates 
Four main types of certificates are used:
- End-entity certificates
- CA certificates
- Cross-certification certificates
- Policy certificates

**End-entity certificates** are issued by a CA to a specific subject, such as Joyce, the Accounting department, or a firewall.
- An end-entity certificate is the identity document provided by PKI implementations.

**A CA certificate** can be self-signed, in the case of a stand-alone or root CA, or it can be issued by a superior CA within a hierarchical model.
- The superior CA gives the authority and allows the subordinate CA to accept certificate requests and generate the individual certificate itself.

**Cross-certification certificates, or cross-certificates**, are used when independent CAs establish peer-to-peer trust relationships.
- Simply put, they are a mechanism through which one CA can issue a certificate allowing its users to trust another CA.

**Policy certificates** provide centrally controlled policy information to PKI clients.

### Wildcard Certificates
**Def: Wildcard certificates work exactly as one would expect, a certificate issued for .example.com would be valid for one.example.com as well as two.example.com.**

**EXAM TIP: Wildcard certificates include an asterisk and period before the domain name. SSL certificates commonly extend encryption to subdomains through the use of wildcards.**

### Subject Alternative NameSAN
See previous section

### Code-Signing Certificates
Certificates can be designated for specific purposes, such as code signing. 
- This is to enable the flexibility of managing certificates for specific functions and to reduce the risk in the event of compromise.
- **Code-signing certificates** are designed as such in the certificate itself, and the application that uses the certificate adheres to this policy restriction to ensure proper certificate usage.

### Self-Signed Certificates
Certificates are signed by a higher-level CA, providing a root of trust. As with all chains, there is a final node of trust: the root node.
- Not all certificates have the same root node.
- Companies can create their own certificate chain for use inside the company, and thus it creates its own root node.
- A company created root-certificate is an example of a CA certificate.

### Machine/Computer
Certificates bind identities to keys and provide a means of authentication, which at times is needed for computers. 
- Active Directory Domain Services (AD DS) can keep track of machines in  asystem via machines identifying themselves using machine certificates, also known as computer certificates.
- When a user logs in, the system can use either the machine certificate, identifying the machine, or the user certificate, identifying the user--whichever is appropriate for the desired operation.
- This is an example of an end-entity certificate

### E-mail
Digital certificates can be used with e-mail systems for items such as digital signatures associated with e-mails. 
- Just as other specialized functions such as code signing have their own certificates, it is common for a separate e-mail certificate to be used for identity associated with e-mail. 
- This is an example of an end-entity certificate

### User
User certificates identify a user. 
- They are an example of an end-entity certificate

**NOTE: User certificates are employed by users for encrypted file systems (EFS), e-mail, and client authentications, whereas computer certificates help computers to authenticate to the network.**

### Root
**Def: A root certificate is a certificate that forms the initial basis of trust in a trust chain.**
- All certificates are signed by the CA that issues them, and CAs can be chained together in a trust structure.
- When you climb the chain, you eventually find a self-signed certificate...this is the root certificate
- Root certificates because they form anchors of trust for other certificates, are examples of CA certificates, as explained earlier.

### Domain Validation
**Def: Domain Validation is a low-trust means of validation based on an application demonstrating control over a DNS domain.**
- Typically used for TLS and has the advantage that is can be automated via checks against a DNS record.
- A domain validation-based certificate, which is typically free, offers very little in assurance that the identity has not been spoofed because the applicant doesn't need to directly interact with the issuer. 

### Extended Validation
**Def: Extended Validation (EV) certificates are used for HTTPS websites and software to provide a high level of assurance as to the originator's identity.** 
- EV certificates use the same methods of encryption to protect certificate integrity as do domain and organization-validated certificates.
- The difference in assurance comes from the processes used by a CA to validate an entity's legal identity before issuance. 
- EV certificates display the legal identity and other legal information as part of the certificate. 

To assist in identifying EV certificates and the enhanced trust, several additional visual clues are provided to users when EVs are employed.
- When implemented in a browser, the legal entity name is displayed, in addition to the URL and lock symbol, and in most instances, the entire URL bar is green.
- All browser vendors provide this support, and because the information is included in the certificate itself, this function is web server agnostic.

**EXAM TIP: Know the various types of certificates discuss in this section and what they are used for.**


## Certificate Formats
Digital certificates are defined in *RFC 5280: Internet X.509 Public Key Infrastructure Certificate and Certificate Revocation List (CRL) Profile*. 
- This RFC describes the X.509 v3 digital certificate format in detail.
- There are numerous ways to encode the information in in a certificate before the instantiation as a file, and the different methods result in different file extensions. 
- Common extensions include .der, .pem, .crt, .cer, .pfx, .p12, and .p7b.

### KEY 
A KEY file, denoted by the file extension .key, can be used both for public and private PKCS#8 keys. 
- The keys may be encoded as binary DER or as ASCII PEM

### Distinguished Encoding Rules (DER)
**Def: Distinguished Encoding Rules (DER) is one of the Abstract Syntax notation One (ASN.1) encoding rules that can be used to encode any data object into a binary file.**
- With respect to certificates, name-value pairs should be converted to consistent format for digital signing.
- DER offers a consistent mechanism for this task. A DER file (.der extension) contains binary data and can be used for a single certificate.

### Privacy-Enhanced Mail (PEM)
**Def: Privacy-Enhanced Mail (PEM) is the most common format used by certificate authorities when issuing certificates.**
- PEM comes form RFC 1422 and is a Base64-encoded ASCII file that begins with "---BEGIN CERTIFICATE---" followed by the Base64 data, and ends with "---END CERTIFICATE---". 
- A PEM file supports multiple digital certificates, including a certificate chain. 
- A PEM file can contain multiple entries, one after another, and can include both public and private keys

The PEM format for certificate data is used in multiple file types, including .pem, .cer, .crt, and .key files.

**EXAM TIP: If you need to transmit multiple certificates, or a certificate chain, use PEM for encoding. PEM encoding can carry multiple certificates, whereas DER can only carry a single certificate.**

### Personal Information Exchange (PFX)
**Def: A PKCS#12 file is a portable file format with a .pfx extension.**
- It is binary format for storing the server certificate, intermediate certificates, and the private key in one file
- **Def: Personal Information Exchange (PFX) files are typically used on Windows machines to import and export certificates and private keys.**

### CER
**Def: The .cer file extension is used to denote an alternative form, from Microsoft, of CRT files.**
- The .cer/,crt extension is used for certificates and may be encoded as binary DER or as ASCII PEM. 
- The .cer and .crt extensions are nearly synonymous.
- The .cer extension is most commonly used with Microsoft Windows, whereas .crt is with UNIX systems.

**NOTE: The only time .crt and .cer can safely be interchanged is when the encoding type can be identical (for example, PEM-encoded CRT is the same as PEM-encoded CER).**

**EXAM TIP: The file extension .cer is an SSL certificate file format used by web servers to help verify the identity and security of the site in question.**

### P12
**Def: P12 is an alternative file extension for PKCS#12 file format, a binary format for storing the server certificate, intermediate certificates, and the private key in one encrypted file.**
- These files usually have an extensions such as .pfx or .p12.
- They are typically used on Windows machines to import and export certificates and private keys.

### P7B
**Def: The PKCS#7or P7B format is stored in Base64 ASCII format and has a file extension of .p7b or .p7c.**
- A P7B file begins with "---BEGIN PKCS7---" and only contains certificates and chain certificates (intermediate CAs), not the private key.
- The most common supported platforms are MS Windows and Java Tomcat

## Concepts
PKI systems are composed of the items discussed in the first section, as well as methods of using and employing those items to achieve the desired functionality.
- This section describes several important operational elements, such as pricing, stapling, and certificate chaining, and it examines the various trust models.

### Online vs. Offline CA
Certification servers must be online to provide certification services, so why would anyone have an offline server?
- The primary reason is security; if a given certificate authority is used only for periodic functions--for example, signing of specific certificates that are rarely reissued or signed--then keeping the server offline except when needed provides a significant level of security to the signing process.
- Other CA requests, such as CRL and validation requests, can be moved to a validation authority approved by the CA.

### Stapling
**Def: Stapling is the process of combining related items to reduce communication steps.**
- An example is when someone requests a certificate, stapling sends both the certificate and OCSP responder information in the same request to avoid the additional fetches the client would have to perform during path validation. 

**EXAM TIP: Certificate stapling is considered a more efficient way to handle certificate verification. It minimizes the burden of the CA.**

### Pinning
**Def: When a certificate is presented for a host, either identifying the host or providing a public key, this information can be saved in an act called pinning, which is the process of associating a host with a previously provided X.509 certificate or public key.**
- Pinning assists in security through the avoidance of the use of DNS and its inherent risks when on less-than-secure networks.

**Def: Key continuity is the process of reusing a certificate or public key.**
- This provides protection from an attacker, assuming that the attacker was not in position to attack on the initial pinning. 

**EXAM TIP: Certificate pinning is the process of associating a host with its expected public key or X.509 certificate.**


### Trust Model
**Def: A trust model is a construct of systems, personnel, applications, protocols, technologies, and policies that work together to provide a certain level of protection.**
- Different trust domains are usually managed by different groups of administrators, have different security policies, and restrict outsiders from privileged access.

**Def: A trust anchor is the agreed-upon trust third party, an example is the DMV**

When two companies need to communicate using their individual PKIs, or if two departments within the same company use different CAs, two separate trust domains are involved.

A trust relationship must be established between two issuing authorities (CA).
- This happens when one or both of the CAs issue a certificate for the other CA's public key. 

The trust models describe and outline the trust relationships between the different CAs and different environments, which will indicate where the trust paths reside.


- #### 1. Hierarchical Trust Model
It is a basic hierarchical structure that contains a root CA, an intermediate CA, leaf CAs, and end-entities. The configuration is that of an inverted tree. The root CA is the ultimate trust anchor for all other entities in this infrastructure.

No bidirectional trust exists--they are all unidirectional trusts. This root CA certificate and public key are distributed to all entities within this trust model.

- #### 2. Walking the Certificate Path
When a user in one trust domain needs to communicate with another user in another trust domain, one user will need to validate the other's certificate.

- #### 3. Peer-to-Peer Trust Model
**Def: In a peer-to-peer trust model, one CA is not subordinate to another CA, and no established trust anchor between the CAs is involved.**

The end-entities will look to their issuing CA as their trusted anchor, but the different CAs will not have a common anchor. 

The two different CAs will certify the public key for each other, which creates a bidirectional trust. This is referred to as **cross-certification** since the CAs are not receiving their certificates and public keys from a superior CA, but instead are creating them for each other.

One of the main drawbacks to this model is scalability. Each CA must certify every other CA that is participating, and a bidirectional trust path must be implemented crazily.

- #### 4. Hybrid Trust Model
A company can be complex within itself, and when the need arises to communicate properly with outside partners, suppliers, and customers in an authorized and secured manner, this complexity can make sticking to either the hierarchical or peer-to-peer trust model difficult, if not impossible.

**Def: In a hybrid trust model, the two companies have their own internal hierarchical models and are connected through a peer-to-peer model using cross-certification.**

**EXAM TIP: Three trust models exist: hierarchical, peer-to-peer, and hybrid. Hierarchical trust is like an upside-down tree. Peer-to-peer is a lateral series of references, and hybrid is a combination.**

### Key Escrow
**Def: Key escrow is a system by which your private key is kept both by you and by a third party.**
- EX: Key escrow in this circumstance is a system by which your private key is kept both by you and the by the government

**EXAM TIP: Key escrow can solve many problems resulting from inaccessible key, and the nature of cryptography makes the access of the data impossible without the key.**

### Certificate Chaining
The signatures of all certificates in the chain must be verified up to the root CA certificate.

# Questions
1. C (Third-party trust model)
2. D
3. B
4. C (The certificate has likely been revoked)
5. D
6. A
7. B
8. C
9. C 
10. D





