# Chapter 10
# Virtualization and Cloud Security
Virtualization and cloud services are becoming common enterprise tools to manage cost, capacity, complexity, and risk. It is important to understand how these services contribute to a security solution in today's enterprise.

## Cloud Models
There are many different cloud development models. Clouds can be created by many entities, both internal and external to an organization. 

The promise of cloud computing while improving the utility of and is marketed under the concepts of Platform as a Service (PAAS), Software as a Service (SaaS), and Infrastructure as a Service (IPaaS)

There are pros and cons to cloud-based computing. And for each use, the economic factors may differ (issues of cost, contracts, and so on). However, for someone standing up a test project for which they might not want to incur hardware costs associated with buying servers that may live beyond the test project, then "renting" space in the cloud makes sense. 

For each case, a business analysis must be performed to determine the correct choice between cloud options and on-premises computing.

### Infrastructure as a Service (IaaS)
**Def: a marketing term used to describe cloud-based systems that are delivered as a virtual solution for computing.**

Rather than firms building data centers, IaaS allows them to contract for utility computing as needed. 

IaaS is specifically marketed on a pay-per-use basis, scalable directly with need.

### Platform as a Service (PaaS)
**Def: A marketing term used to describe the offering of a computing platform in the cloud.**

Multiple sets of software working together to provide services, such as database services, can be delivered via the cloud as a platform. 

PaaS offerings generally focus on security and scalability, both of which are characteristics that fit with cloud and platform needs.

### Software as a Service (SaaS)
**Def: The offering of software to end users from within the cloud.**

Rather than installing software on client machines, SaaS acts as software on demand, where the software runs from the cloud. 

This has a couple advantages: updates can be seamless to end users, and integration between components can be enhanced. 

Common examples of SaaS are products offered via the Web as subscription services, such as Microsoft Office 365 and Adobe Creative Suite. 

### Anything as a Service (XaaS)
With the growth of cloud services, applications, storage, and processing, the scale provided by cloud vendors has opened up new offerings that are collectively called **Anything as a Service (XaaS)**

The wrapping of the previously mentioned SaaS and IaaS components into a particular service creates a new marketable item.

### Level of Control in the Hosting Models

One method of seperating cloud models and on-premises computing is to look at who controls what aspect of the model. 

![[Pasted image 20220321175129.png]]

- #### Public: refers to a cloud service that is rendered over a system open for public use. Less security 
- #### Community: one where several organizations with a common interest share a cloud environment for the specific purposes of the shared endeavor. 
- #### Private: Reserved resources used only by your organization--your own little cloud within a cloud.  More expensive but pretty secure
- #### Hybrid: elements from private, public, and community cloud structures are combined.
	- Operationally these differing environments are not actually joined together but rather used together. 

## Cloud Service Providers
Cloud Service Providers (CSP) come in many sizes and shapes, with a myriad of different offerings, price points, and service levels. 

There are the mega-cloud providers, Amazon, Google, Microsoft, and Oracle, which have virtually no limit to the size they can scale to when needed. 

One important thing to remember: if something isn't in the contract, it won't be done. Take security items for example, if it is not included in a contract, it won't be done.

## Managed Service Provider (MSP)/ Managed Security Service Provider (MSSP)
**Def: A managed service provider (MSP) is a company that remotely manages a customer's IT infrastructure.**

**Def: A managed security service provider (MSSP) does the same thing as a third party that manages security services.**

Devil is in the details.


## On-Premises vs. Off-Premises
Systems can exist in a wide array of places-- from on-premises, to hosted, to in the cloud.

**Def: On-premises means the system resides locally in the building of the organization.**
- Ex: Virtual Machine (VM), storage, or even a service, if the solution is locally hosted and maintained, it is referred to as "on-premises"

The advantage is the organization is in complete control of the system

**Def: Off-premises or hosted services refer to having the services refer to having the services hosted somewhere else, commonly in a shared environment.**

Using a third party for hosted services provides you a set cost based on the amount of those services you use. 

**Exam Tip: The phrase "in the cloud" refers to having the system distributed across a remotely accessible infrastructure via a netowrk, with specific cloud characteristics, such as scalability and so on. This is true for both on- and off- premises.**

## Fog Computing
Fog computing is a distributed form of cloud computing, in which the workload is performed on a distributed, decentralizied architecture. 

Fog computing is an architecture where devices mediate processing between local hardware and remote servers. 

One can view fog computing as using intelligent gateways that handle immediate needs while managing the cloud's more efficient data storage and processing. 

This makes fog computing an adjunct to cloud, not a replacement. 

## Edge Computing
**Def: Edge computing refers to computing performed at the edge of a network.**

Edge computing is similar to fog computing in that it is an adjunct to existing computing architectures-- one that is designed for speed. 

The true growth in edge computing has occured with the Internet of Things (IoT) revolution. 

**EXAM TIP: Remember that edge computing brings processing closer to the edge of the network, which optimizes web applications and IoT devices.**


## Thin Client
**Def: a lightweight computer, with limited resources, whose primary purpose is to communicate with another machine.**

Rather than having 32 GB of memory, a top-level porcessor, a high-end graphics card, etc, the thin client allows access to a server where the appropriate resources are available and can be shared.

## Containers

Virtualization enables multiple OS instances to coexist on a single hardware platform. 

Containers are similar, but rather than having multiple independent OSs, a container holds the portions of an OS that it needs seperate from the kernal. 

Therefore multiple containers can share an OS, yet have seperate memory, CPU, and storage threasd, guaranteeing that they will not interact with other containers. 

- This allows multiple instances of an application or different applications to share a host OS with virtually no overhead.

Think of containers as the evolution of the VM concept to the application space. A container consists of an entire runtime environment bundled into one package: an application, including all its dependencies, libraries, and other binaries, and the configuration files needed to run it. 

**EXAM TIP: Containers are a form of operating system virtualization. They are a packaged-up combination of code and dependencies that help applications run quickly in different computing environments.**

## Microservices/API
**Def: An application programming interface (API) is a means for specifying how one interacts with a piece of software. **

Lets use a web service as an example: if it uses the representational state transfer (REST) API, then the defined interface is a set of four actions expressed in HTTP:
- GET: Get a single item or a collection
- POST: Add an item to a collection
- PUT: Edit an item that already exists in a collection
- DELETE: Delete an item in a collection

**Def:  Unlike defining inputs and outputs, a microservices divide a system into a series of small modules that can be coupled together to produce a complete system.**

## Managing Cloud Resources

### Infrastructure as Code
**Def: The use of machine-readable defintion files as well as code to manage and provision computer systems.**

Rather than having to manage physical hardware configurations using interactive configuration tools, infrastructure as code allows for this to be done programmatically. 

### Software-Defined Networking (SDN)
**Def: A network architecture where the control plane and data plane are seperated.**


This allows for for networking harrdware to be under programmatic control even while processing data. 

Traditional network architectures have the data plane and the control plane coexisting, and one of the results is the reduced flexibility of changing the network. 

With SDN a complete network programming stack exists, separate from data flows and programmable across the entire network. This provides significant flexibility and programmability in SDN networks, although at the cost of complexity. 

**A key element of SDN is network function virtualization (NFV). NFV is an architecture that virtualizes network services such as routers, firewalls, and load balancers, as opposed to running them on dedicated, specific hardware.**

Together, SDN and NFV create a fully functional network under the infrastructure as code architectural model 

### Software-Defined Visibility (SDV)
For a network to operate on data, it must see the data flow. Firewalls can't manage data they don't see, so firewalls are physically positioned throughout the network in line with the system's physical architecture. 

Software-defined Visibility (SDV) is an extension of network infrastructure as code idea for the network visibility problem.

Rather than the next-generation firewall (NGFW) being positioned strategically in line with data flows physically, it is done via code through the SDN fabric 

Allowing for flexibility in design and the ability to reconfigure networks on the fly, including the security components.

### Serverless Architecture
The cloud is like the ultimate shared resource, and with many large providers, you don't specify servers or disks, you specify capacity.

By specifying the resources needed in terms of processing power, the cloud provider can spin up the necessary resources. 

**Exam Tip: Know that serverless architecture is a way to develop and run applications and services without owning and managing an infrastrucuture. Servers are still used but they are owned and managed "off-premises"


### Services Integration
**Def: The connection of infrastructure and software elements to provide specific services to a business entity.**


Through predesigned scripts, the cloud provider can manage services integration in a much more scalable fashion than individual businesses. 

For a business, each integration is a one-off creation, whereas the cloud services provider can capitalize on the reproducibility of doing the same integrations for many customers. 

### Resource Policies
Management of resources is done through resource policies.

Through resource policies you can define what, where, or how resources are provisioned. This allows your organization to set restrictions, manage the resources, and manage cloud costs.

### Transit Gateway
**Def: A network connection that is ued to interconnect virtual private clouds (VPCs) and on-premises networks.**

Using transit gateways, organizations can define and control communication between resources on the cloud provider's network and their own infrastructure. 

Transit gateways are unique to each provider and are commonly implemented to support the administration of the provider's cloud environment.

---

## Virtualization/Hypervisors

### Virtualization

**Def: Technology that is used to enable a computer to have more than one OS present and, in many cases, operating at the same time.**

Virtualization is an abstraction of the OS layer, creating the ability to host multiple OSs on a single piece of hardware. 

To enable virtualization, a hypervisor is employed. A hypervisor is a low-level program that allows multiple operating systems to run concurrently on a single host computer.
- They use a thin layer of code to allocate resources in real time.
- They act as traffic cops that control I/O and memory management. 

One of the major advantages of virtualization is the separation of the software and the hardware, creating a barrier that can improve many system functions, including security. 

The underlying hardware is refered to as the host machine, and on it is a host OS. Either the host OS has a built-in hypervisor capability or an application is needed to provide the hypervisor function to manage the virtual machines (VMs)

**Def: A hypervisor is an interface between a virtual machine and the host machine hardware. Hypervisors comprise the layer that enables virtualizaiton**.


### Hypervisors

#### Type I:
- Run directly on the system hardware. They are referred to as a native, bare-metal, or embedded hypervisors in typical vendor literature.
- They are designed for speed and efficiency, as they do not have to operate through another OS layer.
- They are designed for high-end server market in enterprises and are designed to allow multiple Vms on a single set of server hardware.
- Example: KVM, Xen, Microsoft Windows Server Hyper-V, VMware's vSphere/ESXi platforms. 

#### Type II: 
- Run on top of a host operating system. In the beginning of the virtualization movement, Type II hypervisors were the most popular. 
- They are designed for limited numbers of VM's, typically running in a desktop or smaller server environment

### Virtual Machine (VM) Sprawl Avoidance
Spawl is the uncontrolled spreading and disorganization caused by lack of an organizational structure when many similar elements require management.

Just as you can lose track of a file in a large file directroy and have to hunt for it, you can lose track of a VM among many others that have been created.

VMs are basically files that contain a copy of a working machine's disk and memory structures.

You can avoid sprawl through naming conventions and proper storage architectures so that the files are in the correct directory/folder, making finding the correct VM easy and efficient.

### VM Escape Protection
When multiple VMs are operating on a single hardware platform, one concern is VM escape, where software either malware or an attacker, escapes from one VM to the underlying OS.

Once the VM escape occurs, the attacker can attack the underlying OS or resurface in a different VM

While the VM system is designed to provide protection, as with all things of larger scale, the devil is in the details. 

Large scale VM environments have specific modules designed to detect escape and provide VM escape protection to the other modules.

**Exam Tip: Virtual environments have several specific concepts that the exam may address. Understand the differences bewtween VM sprawl and VM escape and the issues each poses. Expect questions for which you are given several of these terms as options and have to choose the correct one.**

---
# Questions
1. B ( The hypervisor abstracts away the hardware from the guest operating system to support virtaulization)
2. B 
3. C (Containerization runs small applications on a host OS with virtually no overhead)
4. D
5. B
6. C
7. A
8. B
9. B
10. B (A private cloud model is considerably more expensive, as it is a dedicated resource)


# Notes:
- This was a harder chapter, will definetly have to come back and review

















