# Chapter 16 
# Cryptographic Concepts

**Def: Cryptography is the science of encrypting, or hiding, information --something people have sought to do since they began using language.**

## General Cryptographic Concepts
As systems and technology became more complex, ciphers were frequently automated by some mechanical or electromechanical device. 

When setting up a cryptographic scheme, it is important to use proven technologies. 

Proven cryptographic libraries and cryptographically correct random number generators are the foundational elements associated with a solid program.

Developing your own cryptographic algorithmns is beyond the abilities of most groups

Algorithmns are complex and difficult to create. Any algorithm that has not had public review can have weakness. 

When material called **plaintext** needs to be protected from unauthorized interception or alteration, it is encrypted into **ciphertext**. This is done using an algorithm and a key. 

### Fundamental Methods
Modern cryptographic operations are performed using both an algorithmn and a key. The choice of algorithmn depends on the type of cryptographic operation that is desired.

While the mathematical specifics of these operations can be very complex and are beyond the scope of this level of material, the knowledge to properly employ them is not.

Encryption operations are characterized by the quantity and type of data, as well as the level and type assurance desired.

Data is characterized by its usage: data in transit, data at rest, or data in use. 

**Exam Tip: The terms data in transit, data at rest, and data in use are industry-standard terms.  For more, go back to 2.1**

---
## Digital Signatures
**Def: A cryptographic implementation designed to demonstrate authenticity and identity associated with a message.**

Using public key cryptography, a digital signature allows traceability to the person signing the message through the use of their private key.

The addition of hash codes allows for the assurance of integrity of the message as well.

A digital signature does not by itself protect the contents of the message from interception. The message is still sent in the clear, so if confidentiality of the message is a requirement, additional steps must be taken to secure the message from eavesdropping.

**Exam Tip: Know that a digital signature guarantees that the contents of a message have not been altered while in transit.**

---
## Key Length
The strength of a cryptographic function typically depends upon the strength of a key, where a larger key has more entropy and adds more strength to the encryption.

Some crytographic systems have fixed key lengths, such as Triple Digital Encryption Standard (3DES), while others, such as Advanced Encryption Standard (AES), have multiple lengths (for example AES-128, AES-192, AES-256)

Some algorithmns offer choices in key length: as a general rule, a longer key length is more secure, but also will take longer to compute.

Recommended minimum key lengths:
- Symmetric key lengths of at least 80 to 112 bits
- Elliptic curve key lengths of at least 160 to 224 bits
- RSA key lengths of at least 2048 bits. 
- DSA key lengths of at least 2048 bits

**Note: Cryptography is a discipline filled with acronyms; they are used for algorithmns, methods, and processes. This may seem intimidating, but after a couple passes through the chapter, they will become more familiar to you.**

---
## Key Stretching
**Def: A mechanism that takes what would be weak keys and "stretches" them to make the system more secure against brute-force attacks.**

In the case of a short key, the chance of randomly matching the hash function by use of computational guessing attacks has increased. 

To make matching the hash more difficult, one must increase the keyspace or slow down the computation.

Key stretching involves increasing the computational complexity by adding iterative rounds of computations--rounds that cannot be done in parallel.

---
## Salting
**Def: To provide sufficient entropy for low-entropy inputs to hash functions, a high-entropy piece of data can be concatenated with the material being hashed. The initial data piece is refered to as a salt.**

**Note: Entropy is an important term in cryptography; it refers to the level of randomness. **

Another term used in this regard is the **initialization vector**, or IV, and this is used in several ciphers, particularly in the wireless space, to achieve randomness, even with normally deterministic inputs. 

**Note: Initialization vectors is covered in more detail in Chapter 4, "Network Attack Indicators" A nonce is a number used only once, and is similar to a salt, or an IV. However, because it is only used once, if it is needed again, a different value is used. Nonces provide random nondeterministic entropy into cryptographic functions and are commonly used in stream ciphers to break stateful properties when the key is reused. 

---
## Hashing
**Def: Hashing functions are special mathematical functions that perform one-way encryption, which means that once the algorithm is processed, there is no feasible way to use the ciphertext to retrieve the plaintext that was used to generate it.**

Also, ideally, there is no feasible way to generate two different plaintexts that compute to the same hash value. 

Generic Hashing Process:
1. Original message plaintext
2. Padding
3. Hash Function
4. Message digest

Common uses of hashing algorithms are to store computer passwords and to ensure message integrity. 

The idea is that hashing can produce a unique value that corresponds to the data entered, but the hash value is also reproducible by anyone else running the same algorithm against the data

So you could hash a message to get a **message authentication code (MAC)**, and the computational number of the message would show that no intermediary has modified the message.

HMAC or **Hash-based Message Authentication Code**, is a special subset of hashing technology. 

- It is a hash algorithm applied to a message to make a MAC, but it is done with a previously shared secret.

- So the HMAC can provide integrity simultaneously with authentication. 

A hash algorithm can be compromised with what is called a **collision attack**, in which an attacker finds two different messages that hash to the same value. 

This type of attack is very difficult and requires generating a separate algorithm that will attempt to find a text that will hash to the same value as the known hash.

**A collision attack is a type of brute force attack that causes a lose of integrity for the hash**

**Exam Tip: The hash function is a special mathematical function that performs one-way encryption.**

By computing a digest of the message, less data needs to be signed by the more complex asymmetric encryption, and this still maintains assurances about the message integrity. This is the primary purpose for which the protocols were designed, and their success will allow greater trust in electronic protocols and digital signatures.

---
## Key Exchange 
Cryptographic mechanisms use both an algorithm and a key, with the key requiring communication between parties.

In symmetric encryption, the secrecy depends on the secrecy of the key, so insecure transport of the key can lead to failure to protect the information encrypted using the key.

**Def: Key exchange is the central foundational element of a secure symmetric encrpytion system.**

Maintaining the secrecy of the symmetric key is the basis of secret communications. 

**Exam Tip: With symmetric encryption the message to be protected is encrypted and decrypted using the same secret key. Asymmetric encryption uses two separate keys to encrypt and decrypt the message.**

Diffie-Hellman key exchange is an example of secure key exchange. It depends on two random numbers, each chosen by one of the parties and kept secret. The secret random numbers are never exposed to outside parties. 

---
## Elliptic Curve Cryptography

**Def: Elliptic curve cryptography (ECC) works on the basis of elliptic curves.** An **elliptic curve** is a simple function that is drawn as a gently looping curve on the X,Y plane. Elliptic curves are defined by this equation:

y^2 = x^3 + ax^2 + b

Elliptic curves work because they have a special property-- you can add two points on the curve together and get a third point on the curve.

For cryptography, the elliptic curve works as a public key algorithm. Users agree on an elliptic curve and a fixed curve point. 

The big benefit of ECC systems is that they require less computing power for a given bit of strength. THis makes ECC ideal for use in low-power mobile devices.

The surge in mobile connectivity has brought secure voice, e-mail, and text applications that use ECC and AES algorithms to protect a user's data.

**Exam Tip: Elliptic curve cryptography can be used in several ways, including in a key exchange and a digital signature. Sec+ has three acronyms need to know: ECC for elliptic curve cryptography, ECDHE for Elliptic Curve Diffie-Helman Ephemeral, and ECDSA for Elliptic Curve Digital Signatures Algorithm. 

---

## Perfect Forward Secrecy
**Def: Perfect forward secrecy (PFS) is a property of a public key system in which a key derived from another key is not compromised, even if the originating key is compromised in the future.**

This is especially important in session key generation, where future communication sessions may become compromised; if perfect forward secrecy were not in place, then past message that had been recorded could be decrypted. 

---
## Quantum Cryptography
**Def: The use of quantum computing hardware to perform encryption and decryption processes.**

Most of the issues associated with quantum cryptography are still theoretical, as machines with sufficient power and programmability have yet to be constructed. 

Quantum principles have already been deployed into communication-related key exchanges through quantum key distribution (QKD). QKD does not actually encrypt communication but rather provides a means for users to securely distribute keys that are used for encrypting the communication channel.

### Post-Quantum Era

As quantum computing presents a challenge for many of today's cryptographic algorithmns, signficiantly reducing their strength, there is a movement to develop algorithms that are not easily solved via quantum methods.

There are currently several cryptographic algorithms that have been developed in response to quantum methods and are believed to be resistant to quantum computing-based decryption methods to a reasonable level. 

---
### Ephemeral Keys
**Def: Cryptographic keys that are used only once after generation.**

When an ephemeral key is used as part of the Diffie-Hellman scheme, it forms an Ephemeral Diffie-Hellman (EDH) key exchange.

An EDH generates a temporary key for each connection, never using the same key twice. 

If this is constructed using an elliptic curve algorithmn, it would be ECDHE, for Elliptic Curve Diffie-Helman Ephemeral, as mentioned previously.

---
## Modes of Operation
In symmetric or block algorithmns, there needs to be a way to deal with multiple blocks of identical data to prevent multiple blocks of cyphertext that would identify the blocks of identical input data. 

**Def: The methods of dealing with this are called modes of operation**

The basic premise invovles some sort of entropy before encrypting subsequent blocks so that identical blocks of plaintext produce differing blocks of ciphertext. The three types of modes of operations are authenticated, unauthenticated, and counter. 

### Authenticated
**Def: Authenticated encryption with associated data (AEAD) is a form of encryption designed to provide both confidentiality and authenticity services.**

A wide range of authenticated modes is available for developers, including GCM, OCB, and EAX.

**NOTE: You may need authenticated encryption to protect against chosen ciphertext attacks such as POODLE. You need a second layer using a MAC implementation such as HMAC-SHA. You can do this with:
1. Compute the MAC on the ciphertext, not the plaintext
2. Use different keys: one for encryption and another for the MAC.

This specific, yet generic prescription adds steps and complications for developers. To resolve this, special modes for block ciphers called authenticated encryption (AE) and authenticated encryption with associated data (AEAD) were devised. 

These provide the same protection as the block cipher/MAC combination, but in a single function with a single key. 

**Note:  Offset Codebook Mode (OCB), a patented implementation that offers the highest performance, but because of patents, it's not included in any international standards.  EAX solves the patent problem, but has not been adopted by any international standards. This leaves GCM (Galois Counter Mode). 

#### Counter
**Def: Counter Mode (CTM) uses a "counter" function to generate a nonce that is used for each block encryption.**

Different blocks have different nonces, enabling parallelization of processing and substantial speed improvements. 

Sequence of Operations:
1.  Take the counter function value (nonce)
2. Encrypt it using a key
3. XOR it with plaintext 

Because each block can be done independently, multi-threading can be used

**Def: CCM is a mode of operation involving cipher block chaining (CBC) with a MAC, or CBC-MAC.**

This method was designed for block ciphers with a length of 128 bits, where the length of the message and any associated data must be known in advance. 

**Def: Galois Counter Mode (GCM) is an extension of CTM in that there's an addition of a Galois mode of authentication.** 

This adds an authentication function to the cipher mode, and the Galois field used in the process can be parallelized, providing efficient operations. GCM is employed in many international standards, including IEEE 802.1 ad and 802.1AE. 

### Unauthenticated
**Def: Unauthenticated modes use a non-identity-based source for the entropy element for subsequent blocks.**

In cipher block chaining (CBC), each block is XORed with the previous ciphertext block before being encrypted. 

To obfuscate the first block, an initialization vector (IV) is XORed with the first block before encryption. 

**Two major weaknesses in CBC**:
1. Because there is a dependence on previous blocks, the algorithm cannot be parallelized for speed and efficiency. 
2. Because of the nature of the chaining, a plaintext block can be recovered from two adjacent blocks of ciphertext. An example of this is the padding oracle on dwongraded legacy encryption (POODLE) attack on TLS. 
---
## Blockchain
**Def: A list of records, where each addition to the list is done by a cryptographic algorithm.**

Records in a blockchain are resistant to modification. This allows for a distributed ledger that can record transactions and have both verification of additions and protection with respect to integrity. 

The strength of the integrity comes from both the signing of records and the distributed nature of the blockchain. 

While a record could be altered, it would require all previous after it to also bbe altered, and thus would be detectable across the copies on the distributed storage of the chain. 

The concept of blockchains was invented to create the public transaction ledger of cryptocurrencies. 

**Def: A cryptocurrency is a currency system built on a finite set of "rare" numbers that are mined and then "created".**

There is no central authority for cryptocurrency so when numbers are mined they are entered into the distributed ledger, marking their creation. All transactions are also entered into the ledger to prevent double-spending of the tokens. 

**Note: The true winner in blockchain technology has been the implementation of distributed public ledgers.** 

**Exam Tip: Blockchain is the recordkeeping technology behind Bitcoin. It is a distributed and decentralized public record.**

---
## Cipher Suites 
**Def: A set of algorithms used together in cryptography, with the most famous being the TLS cipher suite.**

A cipher suite typically lists the key exchange mechanism, the authentication protocol, and the block/stream cipher, and message authentication.

### Block
Block ciphers operate on input data in a series of blocks. In the TLS cipher suite, in TLS 1.2, several block ciphers are available, inlcuding AES, 3DES, and IDEA. 

TLS 1.3 substantially trims this list to only ciphers that can support AEAD operations. This removes the CBC versions of AESS. 

### Stream
Stream ciphers operate on streams of data instead of blocks. Stream operations typically take place on a single bytre at a time, using an XOR function and a psuedorandom key. 

The challenge is to produce a long psuedorandom string of bytes that can be used to both encrypt and decrypt the stream. 

**Exam Tip: A block cipher encrypts plaintext one block at a time. A stream cipher encrypts one byte at a time.**

---
## Symmetric vs. Asymmetric
Symmetric encryption tends to be faster, less computationally involved, and is better for bulk transfers. 

Symmetric encryption suffers from key management problems in that keys must be protected from unauhtorized parites. 

Asymmetric methods resolve the key secrecy issues with public keys, but they add significant computational complexity, which mkaes them less suited for bulk encryption.

**Exam Tip: Know the differences between symmetric and asymmetric encryption. Symmetric uses one key, and it is faster but less secure. Asymmetric uses two keys, and it is slower but more secure.**

---
## Lightweight Cryptography
**Def: A specialized suite of cryptographic algorithms designed to operate in resource-constrained environments.**

Internet of Things (IoT) relies on this sort of cryptography.
___
## Steganography
**Def: Hiding data inside other data.**

Unlike cryptography, messages do not attract attetion, and this difficulty in detecting the hidden messages provides an additional barrier of analysis. 

Data hidden in steganogrpahy is often encrypted, so the message would most likely remain secure upon discovery. 

**Def: Least significant bit (LSB) is a method of encoding information onto an image while altering the last visual image as little as possible.**

---
## Homomorphic Encryption
**Def: A set of algorithms that allows operations to be conducted on encrypted data, without decrypting and re-encrypting. 

This concept is simple: create a system that allows operations on ciphertext that, when decrypted, will have the same result as if the operation was performed on plaintext. 

---
## Common Use Cases
Cryptographic services are being employed in more and more systems, and many common use cases are associated with them. Below are some examples. 

### Low-Power Devices
Low-power devices such as mobile phones and portable electronics, are commonplace, and these devices have needs for cryptographic functions. 

Crytopgrahic functions tend to take significant computaitonal power, and special cryptographic functions, such as elliptic curve cryptography, are well suited for low-power applications. 

### Low-Latency Operations
Some cryptographic operations require functions that have extreme time constraints. Stream ciphers are examples of low-latency operations.

### High-Resiliency Systems
High-resiliency systems are characterized by functions that have the ability to resume normal operational conditions after an external disruption. 

The use of cryptographic modules can support resiliency through a standardized implementation of cryptographic flexibility. 

### Support for Confidentiality
Cryptography is the primary means of protecting data confidentiality--at rest, in transit, and in use.

### Support for Integrity
Message authentication codes (MACs) supported by hash functions are an example of cryptographic services supporting integrity. 

### Support for Obfuscation
There are times when information needs to be obfuscated--that is, protected from casual observation. 

In case of a program, obfuscation can protect the code from observation by unauthorized parties. 

### Support for Authentication
Authentication is a property that deals with the identity of a party-- be it user, a program, or a piece of hardware. 

Cryptographic functions can be employed to demonstrate authentication, such as the validation that an entity has a specific private key associated with a presented public key, thus proving identity. 

### Support for Nonrepudiation
**Def: Nonrepudiation is a property that deals with the ability to verify that a message has been sent and received so that the sender (or receiver) cannot refute sending (or receiving) the information. 

Actions that are signed cannot be repudiated by the holder.

**Exam Tip: Remember that nonrepudiation is the ability to verify that a message has been sent and received so that the sender (or receiver) cannot refute sending (or receiving) the information.**

**Exam Tip: Understanding the different common use cases and being able to identify the applicable use case given a scenario is a testable element associated with this section's objective.**

---
## Limitations
Limitations exist when exploring options for implementing cryptographic solutions. 

### Speed
Encryption and decrpytion speed can be an issue with various forms of communication

The more complex the algorithmn, the more rounds that are performed and the stronger the encryption, but the slower the throughput. 

Computational efficiency is an important benchmark in modern cryptography and has led to algorithmns such as ChaCha20 gaining favor, as it has a significant speed advantage over AES. 

### Size
In cryptography, size does matter :( and that is related to key size. The bigger the key, the more data that can be throughput and the stronger the encryption. 

Size comes with the tradeoff of speed. Longer keys take longer to generate, and the more rounds a system operates, the longer the time to encrypt/decrypt. 

### Weak Keys
Cryptographic strength is a function of the algorithmn strength and the strength of the key. As mentioned earlier, key length can be an important element in the strength of cryptographic solutions. 

For some algorithms there are cases of key values that result in weaker encryption. A key value of all zeroes, or all ones, is just another key value in the set of all possible values, but numbers such as these or those with patterns may casue weakness. 

Weak keys are an issue 

### Time
Given enough time, encryption can be broken--one must simply try all the keys. 

This is refered to a brute force attack. 

### Longevity
The longevity of an encryption scheme must be measured not in today's computing ability, but in light of the increases in computing abilities over the expected protection time desired by the encryption. 

We can't 100% predict computing power in the next 25 years, things like Quantum computing have possible effects on that calcuation.

### Predictability
There needs to be some sort of randomness function that eliminates any form of predictability. 

The use of cryptographic random numbers is important, as it removes the predictablity problem of pseudorandom number generators. 

### Reuse
Never reuse cryptographic keys. 

### Entropy
**Def: The level or amount of randomness is referred to as entropy. **

Entropy is the measure of uncertainity associated with a series of values. 

**Exam Tip: A lack of good entropy may leave a cryptosystem vulnerable and unable to securely encrypt data.**


### Computational Overhead
Different algorithms have differing means of computing the complexity that makes cryptographic solutions secure. 

One of the limitations of a cryptographic system is the level of computational overhead needed the generate the system. 

### Resource vs. Security Constraints
When using cryptography for protection of data, several factors need to be included in the implementation plan. One of the first decisions is in algorithm selection.

There needs to be a balance when weighing the selection of cryptographic solutions, as resources are seldom unlimited and security considerations can greatly vary. 

### Weak/Deprecated Algorithms
Over time, cryptographic algorithms fall to different attacks or just the raw power of computation. The challenge with these algorithms is understanding which ones have fallen to attacks and may yet still be available for use in software libraries, resulting in their inapprorpiate application in use. 

MD5 is inappropriate
DES and 3DES have fallen from favor
SHA-1 and SHA-256 have issues because they are suspect to forced collisions. 

**Exam Tip: Understanding the different limitations of crytopgrahic solutions and being able to identify the implications given a use case scenario is a testable element associated with this chapter's objective.**

---
# Chapter Review
1. B
2. D Entropy is a measure of randomness, not a limitation of a cryptographic solution
3. A
4. C
5. C
6. D
7. A
8. C
9. B
10. C



