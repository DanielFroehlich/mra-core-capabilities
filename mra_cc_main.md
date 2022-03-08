

# Security \[Maintainer: Daniel\]

IT and OT integration brings its own set of security challenges in the
Industrial context as these were earlier considered to be separate and
isolated networks. The Security capability ensures that complete
connected system is secured end to end.

To enable a robust security mechanism, it is advisable to also take best
practices suggested by international standard agencies (ISO 27001, ISO
27002, ISO 27017, IEC 62443) and then apply additional measures and
approaches on top of it to align it to industrial context. It might also
be necessary to deviate from standards, e.g. the strict communication
hierarchy defined by IEC62433 is diluted by Industrial IoT solutions.
Modern concepts like Zero Trust Networks will become more and more
important.

An Open Manufacturing Platform needs Security Controls that:

-   Are Form factor independent

-   Offer End to End Visibility (Edge \<-\> DC \<-\> Cloud)

-   Are Programmable, Intent driven

-   Are good to handle, Reduce the complexity

-   Offer atomic visibility to Reduce the attack surface in the endpoint

-   Decoupling Security Policy from cabling (Control/data Plane)

-   Use industry standard protocols

As we are getting new formfactors like containers and VMs steering the
shop floor, running on Container Hosts and Hypervisors, and securing
these in an omniscient and efficient way. Security controls need to move
closer to the workloads to the edge, and ideally must be moved into the
platform and offer the possibility to be interconnected and automated
via API.

Security is a vast and critical topic. We grouped the capabilities into
the main section:

-   Control identity and access

-   Protect resources

-   Detect & Respond - to threads

## Control Identify and Access \[Ashish\]

Identity and access need to be controlled for user, system, machine,
devices etc. User Federation and Identity Brokering are needed to
integrate existing repositories. Modern authentication mechanisms like
Multi Factor Authentication, Step-Up-Authentication, FIDO2 security keys
can help to resolve conflicts with operational needs of fast and easy
access.

Certificates are used to establish trust, to identify users and devices
(in general: end point). They are part of a Public Private Key
Infrastructure – PKI) and the Certificate Authority. They take care of
provisioning, inventory management, monitoring, renewal, and revocation
of certificates.

Once identity is verified, access and privileges to the resources is
granted and enforced. Least privilege access principles should be
followed. Access control governs all the available resources and
workloads, and can be either pure policy based, or time bound, or based
on certain conditions (e.g., role based, source location, time of day
etc.), or a combination of them.

### Manage Identity

> This capability assists in associating a user, system, machine, or
> process with a unique identity which is global to the whole system.
> This enables the system to know with whom it is interacting so that
> necessary access can be provided. Identities should be maintained in a
> secured system (e.g., Active Directory for user identities).
> Additionally, in IoT context, each physical device needs to have a
> specific identity assigned to it, if it has to connect and interact
> with the system. Along with this, it is advisable to enable a
> “hardware root of trust” for physical devices to secure this identify
> at source.
>
> Non-Personalized Identities (“User: NightShift”) or no identities at
> all should be avoided to allow for zero trust concepts. This often
> conflicts with operational needs of fast and easy access, e.g. to an
> HMI interface of a machine.

### Authenticate Identities

> This helps in “proving” that the identity is valid. This is where the
> system starts to trust the end point. For example, this could be via
> password comparison between what is provided versus what is available
> in the system. Depending upon the context, authentication can cover
> various mechanisms like Password based or Multi Factor Authentication
> (MFA) based. In today’s security posture, it is advisable to have MFA
> for added security which brings an additional second layer. This
> second layer can be enabled via an authenticator App, SMS, Voice,
> OAUTH software, hardware tokens, and FIDO2 security keys etc. The
> authentication does not stop at user level but covers all entities
> which need to connect. For devices it is advisable to have a password
> less authentication mechanisms, enabled by certificates (e.g., X.509)
> which are secured by a TPM module. It is also important for the system
> to have capability to enable renewal of credentials. Similarly, for
> the external systems who need to interact (system to system
> interaction) can utilize token-based authentication (e.g., OAUTH, SAML
> etc.)

### Control Access & Authorization

> This enables the access rights and privileges to the resources once
> its identity has been verified. This capability enables mechanism for
> a “Least privilege access”. The access control governs all the
> available resources and workloads, and can be either pure policy
> based, or time bound, or based on certain conditions (e.g., role
> based, source location, time of day etc.), or a combination of them.

### Manage Certificates

> Certificates are used to establish trust, to identify users and
> devices (in general: end point). They are part of a Public Private Key
> Infrastructure – PKI) and the Certificate Authority. They take care of
> Provisioning, Inventory Management, Monitoring, Renewal, and
> Revocation of certificates.

## Protect resources \[Bernd/Alexandra/Ashish\]

> In spite of various security control measures, we still seen
> industrial environments being subjected to sophisticated
> cyber-attacks. Active protection is required to mitigate the risks.
> Network segmentation becomes important as a countermeasure to control
> the blast radius and containing it from spreading to larger network.
> This segmentation covers separating out the layers in Purdue model,
> and also within the layers as well creating smaller segments.

### Protect Networks

> Segmented network zones are key to control blast radius. Transition
> points between networks with firefalls provide control authority and
> enable detection of malicious activities using anomaly patterns. It is
> important to ensure that specialized firewalls are enabled for the
> industrial scenarios. These firewalls should also understand OT
> protocols like DNP, CIP, Modbus etc. which are being used by
> automation vendors. This is important to enable the firewall to secure
> the OT environment. Esp. Shop floor networks are frequently “secure by
> definition”. In a highly access controlled manufacturing site this
> “the network is secure” approach is comprehensible. However, it should
> be avoided and translated into a “zero trust, always verify” approach.

### Protect Data

> Data Confidentiality capability ensures that through various controls
> placed, the access to data is controlled to only those which are
> specifically authorized for that. In order to protect critical data,
> manufacturers should ensure that end-to-end encryption with strong
> encryption keys is implemented along the entire value chain spanning
> from the edge to cloud. This holds true for data at rest and data in
> motion. Above mentioned PKI capabilities are helpful for key
> management.

### Protect Endpoints

> All endpoints need protection and management. Mobile Devices,
> Industrial PCs, HMI systems. All are vulnerable to attacks, thus all
> need protection. Imagine the HMI system of a critical machine being
> hijacked by a ransomware attack.

### Protect the Operating System (OS)

> No good security concept can leave out security countermeasures in or
> around the OS System. The role of the classical guest operating system
> is changing since two decades massively. A classical OS is something
> like Linux or Windows or Macintosh. But the verge of Virtualization
> and Containerization, that serve as the orchestration, abstraction and
> platform layer for other classical OSes and their Applications
> (Hypervisor & Central Management / Container Hosts & Caas) degraded
> these classical OSes as VMs guests. If you carve out even more
> binaries of a classical OS, to a minimal viable OS (Container Host) to
> launch tailored massively distributed applications (containers), also
> these need special security considerations. In contrast to VMs on a
> hypervisor (x86 guest OS virtualization), containers are a form of
> kernel level virtualization and provide less isolation guarantees on
> the same container host.
>
> No matter whether it is a hypervisor or a container steering a machine
> on the shopfloor, they are additional layers, which are a high value
> attack target and therefore need to be hardened and operated with
> care. They are so to say the privileged OS for others OS form factors
> (VM/Container). So it is imperative to develop good operating and
> hardening strategies with special due diligence at this layer.
>
> Is even more important than on Guests. Still nowadays you often find
> in the shopfloors very outdated Operating Systems that are not
> maintained be the software supplier, and no new patches are developed
> to patch vulnerabilities leaving them vulnerable. Behavioral
> Whitelisting Solutions are a good technology area to ensure that only
> intended and known good software is used in the correct manner inside
> the outdated OS. They allow to run what is good and everything else is
> being execution blocked per default. Device control is also mandatory
> at operator machines on the shop floor.

## Detect & Respond to Threads \[Bernd/Alexandra/Ashish\]

### Intrusion Detection

> This capability helps in detecting proactively the vulnerability
> caused by looking at the network traffic. This acts as a line of
> defense to identify early signs of malicious activities and gives
> ability to effectively report and respond. Usually, the threats are
> identified by a standard signature-based mechanism. In this the
> traffic patterns are analyzed based on already known specific
> patterns. However, this approach has a limitation of missing new
> attacks for which no signature exists. Looking at today's threat
> landscape it is better to also look at capabilities which enable an AI
> based approach which uses machine learning to create a model which
> helps to identify still unknown attacks.

### Vulnerability Scanning

> Ability to identify vulnerabilities within the network is a critical
> line of defense to proactively identify scenarios of security weakness
> which can lead to threats. This is enabled by some of the tools which
> help in scanning and identifying threats. Usually, it does it by
> scanning the whole network to create an inventory of the systems which
> are connected and then builds up a knowledge base, e.g., operating
> system, software running on each node, open ports, accounts etc. It is
> also important to have a constantly enriched knowledge base against
> which this inventory and its data needs to be compared to identify
> vulnerabilities. This becomes much more critical in industrial setup,
> as in majority of the scenarios unlike the IT ecosystem, the inventory
> of assets is either not created or is not updated due to lack of
> focused solutions for this area. This could mean like for example a
> PLC may be running a very outdated and unpatched OS, some of the ports
> on a PLC may be open although not required, a laptop may be connected
> on the same network as manufacturing line with higher user privileges,
> a new program may be loaded to a PLC. All these scenarios open up a
> huge attack vector. While such a capability is a standard in IT
> networks, but manufacturers should look into enabling this capability
> in OT network as well. For this to work this capability should be
> capable of understand the OT system and network, its specific
> protocols, its processes, and capabilities of various automation OEM
> systems.

### Threat Intelligence & Monitoring

> Threat Intelligence & Monitoring is a capability which draws its
> features from multiple other security capabilities like logging,
> monitoring, vulnerability scanning, IDS, IPS etc. This is focused on
> collecting and analyzing information about the current and potential
> attack vectors and is helpful towards improving the security posture.
> It helps to play a major role in helping detect a potential attack
> early enough to either prevent or limit its impact. It is important
> that this capability is able to collect and process data from multiple
> existing sources and solutions, is able to process data in multiple
> formats, is able to add context between the data, and is able to
> identify thread indicators. It is important for the organization to
> have capability to constantly research new threats emerging outside
> and augment this information. In case organization lacks this in house
> skills of research and analysis, it can also tap into solution vendors
> specializing in this area.

### Risk & Vulnerability Management

> In this context where the networks handling IT and OT assets have
> started to connect, it is important to have the capability to look at
> the entire attach surface. In an approach of looking at only
> vulnerabilities in isolation may have an impact of missing out the
> vulnerabilities which pose more risk or threat and which needs to be
> prioritized. Hence looking at vulnerabilities with the Lense of the
> risk helps to put a context and helps to prioritize and group them
> into areas of focus. Also, this process needs to be automatic and
> dynamic so that it can change the risk score based on the shifting
> threat landscape. Overall, this capability encompasses other aspects
> to enable the complete cycle of Discovering, Classification,
> Prioritization, and Remediation.

### Monitoring

> Monitoring is a foundational capability which helps analyze and
> process billions of events and alerts being generated by various
> systems which can be running in the centralized/cloud system, or in
> the plant eco system (including production support systems, equipment,
> devices, gateways etc.). This allows to analyze this diverse set of
> data to optimize performance, remediate problems, and also to monitor
> for security incidents and events. Monitoring can go from simple
> reporting, to a complex one which also includes aspects of machine
> learning to filter out noise from information.

### Logging

> Logging is one of the most fundamental capabilities which essentially
> drives a lot of upper-level security capabilities. As most of the
> capabilities would depend on the underlying systems to provide it with
> enough data to identify patters. For example, event logs can be used
> for forensic works to look at audit trails when doing the root cause
> analysis. Hence it is important that all systems provide a consistent
> and controllable access to logs. Also, a centralized logging framework
> helps to connect various systems and identify patterns and
> correlations helping in proactively identifying threats

## Manage Policies

Security policy are set of rules that define the security objectives in
terms of what should be protected from whom under which the conditions.
A platform must provide effective monitoring of these policies and sure
their enforcement. Security policies inherently help to standardize
their enforcements across organization in a consistent way. Industry
specific governmental and regulatory requirements (e.g., NIST, HIPPA)
might apply additionally. Security policy have broad impact on elements
like system resources, authentication & authorization, system Integrity
and many others.

Regular and sometimes continuous auditing is needed to ensure compliance
with security policies, to avoid security posture degrade over time.

### Security Policies

> Security policy are set of rules that define the security objectives
> in terms of what do we want to protect, from whom, and the conditions.
> Effective monitoring of policies in terms of effectiveness and
> enforcement is important. Security policies help standardize the
> enforcements across organization in a consistent way. Depending upon
> industries, there may be a need to align the policies with
> governmental and regulatory requirements (e.g. NIST, HIPPA). Security
> policy would broadly control: System resources, Authentication,
> Authorization, Data Integrity, System Integrity, Auditing,
> Confidentiality.

### Network Policies

> Network policy is a specific kind of Security Policy, which define the
> rules that govern the behaviors of network and connected devices.
> Having the ability to define policy for network also helps to automate
> and respond more quickly at the network level on the changing security
> requirement and posture. Broadly various policies under this cover:
> Access to network, resources access, allowed applications, define and
> allocate Quality of Service, traffic routing and control

### Auditing

> Auditing is needed to make sure that the security posture doesn't
> degrade over time. Ideally auditing needs to be aligned to some of the
> industry standard benchmarks (e.g., Center for Internet Security
> (CIS), OWASP, ISA/IEC 62443 etc.). This industry alignment helps to
> improve the security program as it allows the learnings across the
> wider industry space and also helps compare the security state with
> other peers. So even if the current security program is not tied to
> any of these standard benchmarks, it still will give a good guidance
> to define own program and compare with what others are doing. However,
> another aspect which is also important is that after the definition of
> these, there has to be a capability available to continuously assess,
> review, and monitor the compliance status across the space under
> scope.

### Secure the Software Supply Chain

> Secure Software Supply Chain is in theory good imperative policy
> target, but reality shows it is often not doable or an illusion. There
> may be contractual and due diligence things that can be done in the
> supply chain, but reality shows that you cannot trust software that
> you bought, that your 3rd party ISV is always guaranteed error free.
> Also an in-house development team is vulnerable to Typosquatting type
> of attacks and can introduce inadvertently malicious code.
>
> A secure software supply chain (SSSC) defines and enforces standards
> for the whole chain – from sourcing of base images, libraries,
> frameworks, 3d party software via static code analysis and security
> scanning to deployment and operations. As new vulnerability are
> identified after deployment, continuous scanning is required to be
> alerted and necessary controls can be activated.

# Interoperability \[Maintainer: Daniel\]

A key characteristic of manufacturing is its distributed execution.
Therefore, connecting and integration the different parts of the overall
system are key challenges. The huge amount of legacy production assets
in combination with their specific communication protocols are
increasing the challenges even further.

The following diagram groups the different communication parts into four
areas:

<img src="./assets/images/4b34552223a745d45dae62a91130b1b357078ba3.png"
style="width:3.85417in;height:4.25in" />

According to the OMP IoT Connectivity Whitepaper [\[OMP IOTCON-01
2020\]](https://github.com/OpenManufacturingPlatform/iotcon-connectivity-handbook/tree/publication/White_Paper/01_Insights_Into_Connecting_Industrial_IoT_Assets),
there are three different communication categories: telemetry, control,
and management. Each communication category can occur between all the
areas.

Each area has special aspects to consider, which are described in the
following sub-capabiltities:

-   Connect Assests

-   Integrate Business Systems and Applications

-   Connect Third Parties

Sometimes, cardinal points are used to describe the direction of the
connection. That refers to the Purdue / ISA-95 hierarchy (enterprise at
the top, production at the bottom). The following diagram depicts this
from the plant perspective as an example.

<img src="./assets/images/618e0a8ce9c1ea6724cac96db74abab2fd6845ab.png"
style="width:5in;height:4.45833in" />

As all areas have certain aspects in common, these are grouped into the
following sub-capabiltites.

-   Manage Protocols

-   Manage APIS and Interfaces

-   Manage Communication

Connectivity / integration capabilities have a lot of similarities with
Enterprise Service Bus (ESB) or Enterprise Application Integration (EAI)
architectures. In the OMP context, we expect this to be highly
de-centralized and distributed. E.g. the necessary protocol adapters /
transformation capabilities are deployed to where they are needed /
suited best.

## Connect Assests

Production assets like machines, automated guided vehicles (AGVs) and
equipment are the vital part of each manufacturing plant. To gain
insights about their current state and behavior the platform must
integrate and connect them to IT systems. This requires the platform to
Manage communication protocols. The required information flow direction
is an important system characteristic: Pushing control and management
information down to the assets (sometimes referred as north-south
communication) is much more challenging than just sending sensor data to
upper IT systems like cloud data storages. Best practices can be derived
by IEC 62443.

However, we also expect modern security architecture and concepts like
zero trust networks to be introduced to production level asset
communication.

Needs to support traditional / specialized / propriety protocols
(Profinet, Powerlink, Modbus, EtherCAT,… ), but also standard / modern
protocols (OPC-UA, MQTT).

Scalability is a key requirement for the platform right from the start.
The approach to connect a 20-year-old brownfield machine will differ
very much from the one to connect 1,000 conveyor belt motors. The
general advice is to analyze, react, filter and aggregate information
flows as early as possible and as late as needed. The scaling stages
must be chosen consciously and align with the overall production network
strategy. The platform must be able to reflect the hierarchical
production structures which are organizing the production assets.

As production assets are typically being operated in dedicated and
segmented network environments, setting up bi-directional communication
is still a complex task. Production assets are protected by application
of the Protect resources capability. At scale, this needs to automated
Integrate Business Systems and Applications

## Integrate Business Systems and Applications

Business applications like MES or ERP systems are an indispensable part
of today’s manufacturing processes. They are providing context to
actions executed by production assets and are responsible for action
execution. For the former an example is shift information being provided
by dedicated shift management tools or corresponding ERP modules. The
latter could be a transport order being triggered by a machine. The
platform should provide ready to use connectors to bidirectional
communication with business applications. Implementing real life
integration scenarios early in the evaluation process is a good
practice. Ease of use and implementation speed are important selection
criteria. Commercial software offerings provide many pre-defined
connectors. Unfortunately, they only provide the technical mapping. The
semantic mapping remains a complex task to be executed and knowing the
historical “customization backpack” of the business applications is key.

On the one hand, integrating business applications is similar to
connecting production assets in that it involves the technical
connection to external systems. On the other hand, there are huge
differences on the level of integration: While production assets
integration is a low-level task with a lot of raw data handling,
business applications integration is usually a high-level integration
which is consuming business-oriented API calls. For many use cases the
data will remain in the business applications. An example is requesting
order data from an MES. This might be triggered by an RFID reader to
gain information for a specific product. The data of this corresponding
production order is then received and processed while the data of all
other orders stays untouched in the MES.

Business applications are more and more operated in (public or private)
cloud environments to reduce their operation cost. Today, core
applications like ERP typically already have been moved to the cloud.
This integration down to the production assets and the remaining systems
in between is called north-south-integration. For the integration of
typically decentral deployed business applications like MES the terms
east-west or horizontal integration are used.

Sustainable IT initiatives have an increasing effect on business
application management. In most cases the environmental impact of
business applications can be significantly reduced by shifting them to
central locations. This process should not be underestimated as even
identical software products are configured and operated quite
differently from plant to plant. The platform must therefore support a
stepwise movement of single applications from local installations to
cloud environments.

The consumption of business applications by a software-as-a-service
(SaaS) offering is getting traction in manufacturing as well. SaaS is
shifting the application management into the hands of the service
vendors. While this reduces the initial investment cost and operation
effort, some new problems like data protection can emerge. The platform
needs the capability to consume SaaS offerings seamlessly using
different integration levels. Some SaaS offerings might be integrated to
consume (raw) data and provide the results using their own user
interfaces, while others might just be integrated as computational
services. It is an important and often strategic decision which path to
follow.

Provides connectivity towards the core systems. On the one hand side,
this needs to handle (large amount of) telemetry data, e.g., for
Industrial IoT use cases. But also command/control/management data, e.g.
to connect to business systems like MES, MOM, SCM, PPS, ERP. Suitable
protocol adapters are provided by this capability (e.g. SAP sRFC,
Salesforce DTO@REST, etc.). There is a high likelihood that the
communication target is located in a public/private cloud.

## Connect Third Parties

Several Thrird Paries might need access to different parts of the
platform. Examples are

-   Suppliers to update on status of order / deliveries

-   ISV to support a SaaS deployment model on premises

-   OEM of control system helping with diagnostic/maitenance/optimising
    tasks

-   SIs providing manages services

Depending on the level of integration, different other capabilities are
needed to implement this. Examples are:

-   API Management and Identity and Access Management to provide secure
    access to an API to provide updates on shipment status for an
    suplier

-   Manage Communication to provide VPN access to the OT network for an
    Control System OEM to help with trouble shooting

## Manage Protocols

Communication protocols define how different system interact within a
network. IT communication protocols like HTTP and MQTT are established.
But to connecting production assets still is a huge endeavor due to
their variety of (legacy) protocol generations like IO-Link, Profinet,
Modbus and OPC-UA. As many older machines cannot be upgraded
economically the protocol selection is a delicate task.

The platform should manage the minimum number of protocols needed. Third
party solutions or custom-built adapters can handle the complexity
outside the platform and therefore are keeping the complexity out of the
core platform itself.

In most cases protocol conversions will be executed on the lowest level
close to the complexity source (e.g., machines from different vendors).
The platform needs to support this southbound protocol mapping close to
the production assets. There might be reasons good reasons to leave the
conversion to upper level (e.g., bandwidth optimizations requiring
payload transformation to a dedicated cloud service). Therefore the
platform must enable a selection of protocol northbound as well.

### Integrate Services

Integration capabilities are all the capabilities which are commonly
referred to as Enterprise Service Bus (ESB) or Enterprise Application
Integration. It includes adapters, protocol conversion, payload
transformation etc. We expect these capabilities not to be implemented
as a central ESB, which could become a bottleneck. Rather, we expect
de-centralized deployment of integration capabilities to where they are
needed.

### Implement Protocols

Provide / adapters for all necessary protocols, esp. The ones listed by
the connectivity capabilities.

### Convert Protocols

Provides the capability to convert between different protocols. This
includes both transport and application layer conversion. For example,
to convert from REST@HTTP to XML@JMS, or from OPC-UA@UDP to Kafka@TCP

### Transform Payload

When integrating different services, frequently data structures need to
be transformed, e.g. from REST to XML, or a single field from the source
system needs to be split and mapped to several fields in the target
system

## Manage APIS and Interfaces

API management is a key platform capability and involves the
distribution, control, and analysis of APIs that connect applications
and data across the enterprise and from cloud to cloud.

Changing configurations on shopfloor level is a complex process due to
the vast amount of legacy systems. Therefore, the platform must provide
a sophisticated versioning of APIs. If things go wrong the platform must
provide an intuitive way to evaluate the change history.

Communication patterns are rarely documented at shopfloor level today.
API management solutions can eliminate this issue by analyzing
communication patterns and optionally enforcing communication policies.

### Provide API Gateways

Decentralized gateway components keep track of communication
relationships, API usage and are the point of policy enforcement

### Provide API Administration

A centralized component where API providers and consumer administrate
the APIs and their usage. Define Endpoint, Register Client, Monitor
Usage, monitoring and chargeback. Versioning etc. Is managed here.

## Manage Communication

The decentral structure of manufacturing combined with its mission
critical processes is demanding an asynchronous communication
architecture. This communication is sometimes called store and forward
technique which has its origin in telecommunication. The desired system
behavior can be established by two different architectures: message
exchange and event streaming. As these architectures are complementary
technologies for different use cases the platform must support both.

Message exchanged is used for a communication when a system requests
another system to complete an action. In most cases the response message
will be processed by the requester. Many existing shopfloor applications
are dependent on this communication pattern.

Event streaming is applied for if a system wants to communicate a status
to other enterprise systems. The publish-and-subscribe pattern (Pub/Sub)
is the core mechanism and is reducing the complexity of point-to-point
communication. For some use cases, such as asset tracking, Pub/Sub is
even a prerequisite for economic scaling.

### Provide Messaging

To integrate different applications, message-oriented middleware is a
well-known pattern and solution. It provides capabilities for
communication patterns:

-   point to point

-   pub sub

-   event streaming

-   Persistent / non-persistent,

-   high frequency, low frequency

-   Synchronous / asynchronous

Must support communication types for

-   Telemetry data

-   Command & control

-   Management

This also includes data buffering capabilities, to support offline /
disconnected scenarios. For example, if the wide area connection to the
cloud / core datacenter is lost, telemetry data is buffered in the
streaming component until connection is restored.

### Manage Networks

Ability to manage the many different networks that are required due to
performance and security requirements. Needs to be highly automated,
e.g. use of IT automation tools for firewall configurations etc.

# Device Management \[Maintainer: Daniel, Content: Lukas\]

In contrast to production assets which are providing direct value to the
manufacturing process, devices are defined as being IT infrastructure
components. The main goals of the devices are data collection and
sending information back to the production assets. Thus, devices are
equipment like sensors, gateways, industrial PCs. PLCs are part of both
worlds: They are part of the production asset and a device as well as
they are communicating directly with the infrastructure. A platform must
be able to support this hybrid existence and enable new trends like
software defined automation and PLCs.

## Manage Device Lifecycle

\[OMP IOTCON-02 2021\] defines device lifecycle phases and management
capabilities:

<img src="./assets/images/8a2e90e0f4203c5c6408273f24474ff3eb0e2003.png"
style="width:5in;height:1.20833in" />

### Provision devices

For most companies the differences between the use case to be supported
will lead to a selection of different device types rather than a single
device. The challenge is to balance a cost-efficient solution with a
hardware standardization approach. As selected use cases will be
executed on the same single devices a secure and conflict-free operation
is mandatory and containerization is a proven solution. The platform
must enable to provision all these different devices with the correct
software installation. This is usually done by providing a common
endpoint to all devices. Then, a basic setup of the devices is
performed. Example actions are installing the operating system,
provisioning of applications, and providing security credentials.

Zero Touch provisioning concepts are required to support device rollout
by non-it trained personell.

Proposed Standards like [FIDO](https://fidoalliance.org/specifications/)
Device Onboard Specification (FDO) need to be considered for security
(esp. In areas where the physical security of the device can be easily
compromised).

### Configure devices

The onboarded and provisioned devices need to be configured to fulfil
their dedicated roles. Therefore, a use case specific configuration must
be managed by the platform and rollout to the devices on predefined
trigger conditions. For some use cases defining the correct
configuration is an iterative process which needs a corresponding
fine-tuning phase. The platform must enable this iterative process while
always keeping and updating the master configuration without device
specific deviations.

Continually compares current state with desired state. If deviations
occur, a state update is sent down to the device. State updates can be
security or policy updates, changed configurations, firmware / operating
system / application versions (containers).

### Retire devices

Before devices can be decommissioned their retirement has to be planned.
If devices are just being replaced the changeover must be scheduled.
Elimination of devices needs even more planning as the downstream
consequences must be evaluated beforehand. Sometimes unrelated business
processes are dependent on the data the very device is recording and
transmitting. This could be a temperature value of a device equipped to
any machine. It could be used to monitor the environment temperature
while handling the conditioning process of injection molding granulate.
Just shutting down the device would have a negative impact on this
process that is unrelated to the machine itself.

As all technical equipment devices usually contain sensitive data like
keys. This information must be removed before the devices are leaving
corporate property. The platform must keep track of these changes and
document them even after the devices have been removed.

## Manage Device Fleets

Devices are usually being rolled out at large scale. Thus, the platform
must be able to operate and handle the resulting complexity. A key
driver for the device architecture is the desired availability of the
devices. For high availability, backup resources must usually be
available to cover hardware defects. This is typically easier to
accomplish in datacenters than close to the production assets. The
platform therefore must support different deployment scenarios and
efficient transitions between them.

# Data Foundation \[Maintainer: Paul\]

The Data Foundation capabilities ensure that all data across the
manufacturing platform can be reliably stored, integrated, operated on
and managed. Implementing this capability serves as a baseline for being
able to then turn the raw data into insights and actions, which is
another top-level capability.

## Integrate Data

> The Integrate set of capabilities ensure that systems and their data
> can be combined to ensure that all relevant contextual manufacturing
> process, asset and event data can be captured and utilized with the
> manufacturing platform.

Data integration, also known as data ingestions, is the first step for
making data available. It is the process of loading data from external
systems in a reliable, secure, and extensible manner. This may involve
generic ingest mechanisms as well as pre-build connectors, standards,
and operating models.

As flexibility is key mechanism like schema on read data APIs such as
OData and GraphQL are gaining popularity. As much information in
manufacturing is stored in relational databases de facto APIs like xDBC
and Gremlin are still the most adopted integration mechanisms today.

### Data Ingest

> The capability of being able to bring data into the platform from
> external systems in a reliable, secure, and extensible manner. This
> capability may include generic ingest mechanisms as well as pre-build
> connectors, standards and operating models for ingesting data from
> known systems and 3<sup>rd</sup> parties.

### Data Integration & APIs

> The capability to provide and interoperate with industry standard
> integration APIs, schema on read data APIs (such as OData and GraphQL)
> and data technology de facto APIs (such as xDBC and Gremlin) within
> the data platform.

## Persist Data

The Persist capability allows for data to be collected, retained and
managed within the manufacturing platform.

Storing data is a fundament capability of every platform. The platform
must support these basic data structure types: structured, unstructured,
semi-structured and timeseries data. The latter is gaining much
importance as they are an efficient means to enable insights from
historical data. Emerging paradigms like Lakehouse are combining some
aspects of the different approaches.

Cloud solutions have significantly reduced the cost of data storage.
Nevertheless, a conscious selection of the data to be stored is still
important as the cost of stored data can not only be measured by the
direct storage service cost: Many data lake projects failed as it was
impossible to obtain meaningful information after some time.

Additionally, the speed to gain access to data is an important cost
aspect. Direct access to data is usually 10 times more expensive than to
archived data. Data archiving therefore is key feature to keep cost
under control.

### Structured

> Enables the storage, consumption and query of data that has a strictly
> defined content model (schema on write) - e.g. relational and graph
> databases.

### Unstructured

> Enables the storage, consumption and query of data that has no defined
> content model (schema on read) - e.g. object stores and filesystems.

### Semi-structured

> Enables the storage, consumption and query of data that may have
> unstructured or (potentially multiple) structured content models –
> e.g. document databases.

### Time Series

> Enables the storage, consumption and query of data that is ordered
> chronologically (such as events emitted from plant equipment).

## Compute Data

> The Compute capability encompasses all capabilities relating to the
> manipulation and mutation of data within the manufacturing platform.
> Some of these capabilities might be layered on top of into the
> connectivity capabilities of the platform, e.g. data transformation,
> enrichment and filtering.

Data processing is encompassing all actions of data manipulation and
mutation. It is executed at different locations. High-frequency data at
the edge level is typically filtered, aggregated and sometimes
compressed before being sent to the cloud. Specialized hardware can be
used in central locations to parallelize computing and thus drastically
required execution times. Data processing or computation therefore is a
key feature of the platform.

An important design decision is the application of batch and stream
processing. Batch processing is concerned with allowing bounded datasets
to be incorporated into the platform (e.g., large, periodic diagnostic
or log file transfer). Stream processing (sometimes called event
processing) is concerned with allowing data in motion to be ingested
(e.g., unbounded streams of data such as status events being emitted
from plant equipment). A typical example is the processing of data from
its data source (e.g., plant equipment) to a sink (e.g., a time series
store), maybe with intermediate processing (aggregation, filtering).
Stateful processing should be avoided but can be needed.

So-called data pipelines are composable and reusable building blocks.
They structure the data transformation process according to the
underlying business rules. Examples of data pipelines are those that may
transform, enrich, conform, or project data into different data
products.

Data processing is often executed on messages in the context of event
driven architectures. Thus, there is most often a tight relationship to
the *Manage messages* capability.

### Stream & Event Processing

> Stream and Event Processing is concerned with allowing data in motion
> to be ingested (e.g. unbounded streams of data such as status events
> being emitted from plant equipment). Typically, connection from a data
> source (e.g. plant equipment) to a sink (e.g. a time series store),
> maybe with intermediate processing (aggregation, filtering). Stateful
> processing should be avoided, but can be needed. Might rely on
> Messaging capabilities from Integration Services. These capabilities
> might be used by applications that rely on event driven architectures.

### Batch Processing

> Batch processing is concerned with allowing bounded dataset(s) to be
> incorporated into the platform (e.g. large, periodic diagnostic or log
> file transfer).

### Data Pipeline

> The data pipeline capability enables the construction of composable
> and reusable building blocks of data transformation business rules,
> logic and analytics to enable the efficient and consistent delivery of
> data products within the platform. Examples of data pipelines are
> those that may transform, enrich, conform or project data into
> different data products. These pipelines become especially important
> when understanding how data can be used from the manufacturing
> processes within facilities.

### Edge Data Pre-Processing

> Filtering and aggregations of high-frequency data, keep that local to
> the edge and sent only relevant data to the cloud. Data can be
> pre-filtered or compressed on the edge to avoid massive data upload
> from unnecessary data.

### Parallel Compute

> Hardware based compute capabilities that are effective for the timely
> processing and analysis of data in parallel (e.g. to support Deep and
> Machine Learning Capabilities across the manufacturing platform).

## Manage Data

> Manage includes all areas that relate to ensuring that data is thought
> of as an asset within a manufacturing company and its data platform.
> These capabilities may follow guidance and be operationalized within
> existing standards and data frameworks (such as ISO 8000/25012/27701,
> DANA-DMBoK and EDM Council Maturity Framework).

To derive meaning from information it must be structured beforehand.
Data models give data structure and include all technical
characteristics (the structural format and content of the data, access
protocols etc.) as well as operational characteristics (metadata, data
ownership etc.).

The structuring process is executed by transforming, conforming
(applying consistent data semantics and business rules) and mapping data
from multiple sources into a common semantic data model. This model
captures common metadata, attributes, and entity definitions (and their
navigable relationships) to allow applications and data users to be able
use it across multiple systems, processes plants and devices in a
consistent, meaningful way.

Data product is a term gaining popularity recently. It is emphasizing
the value of the data and the target of achieving (virtual) revenues
with the consumption of this data. It is therefore considered as an
extension of the expression data asset.

The importance of this capability is underscored by the existence of a
dedicated OMP semantic data structuring working group.

### Semantic Data Modelling

> Data models are the definition of curated data products that may be
> used and consumed by the applications. This includes all technical
> characteristics (the structural format and content of the data, access
> protocols etc.) as well as operational characteristics (metadata, data
> ownership etc.). Models and data products may be aligned by their
> usage characteristics (events, documents, relational etc.). OMP
> provides data model standards and recommendations via its [semantic
> data structure working
> group](https://openmanufacturingplatform.github.io/sds-documentation/sds-documentation/index.html).

### Data Governance

> Data governance capabilities ensures that data can used across the
> manufacturing platform in an operationally valid and appropriate
> manner. This capability includes the technical, process and human
> mechanisms to achieve this (such as data custodianship and data
> stewardship).

### Reference and Master Data

> The ability to define, catalogue and organize authoritative sets of
> non-transactional, consistent data and their core attributes within
> the manufacturing platform. This is important for defining and
> understanding data taxonomies in the manufacturing platform (such as
> asset, organization and geographic hierarchies).

### Metadata

> This capability ensures that the metadata of data is captured and used
> appropriately within the platform. This includes metadata derived from
> source (e.g. plant equipment) and derived metadata (such as the OMP
> Data Definition Aspect Model).

### Data Quality

> The capability that ensures that the veracity of data can be
> understood, quantified, and so, if necessary, improved within the
> system. This capability includes both technical data quality
> capabilities and support (such as outlier detection) as well as
> process capabilities (such as manual human in the loop inspection of
> data).

### Data Security

> The capability to ensure that data is controlled, retained and
> accessible to permitted systems and users at an appropriate level of
> granularity within defined legal and operational policies.

A compliant usage of data requires that data is controlled, retained and
accessible to permitted systems and users at an appropriate level of
granularity within defined legal and operational policies. The challenge
is to define the right level of appropriateness. Quite often data
security initiatives do not factor in the cost of policy maintenance and
enforcement. This is leading to complex policies that are trimmed down
later in the execution phase and create a lot of frustration with the
users that must cope with it. A detailed data usage logging can be much
more efficient as it is not restricting data access but making data
consumption transparent.

# Data Insights and Actions

The Data Insights & Analytics capability ensures that data can be used
effectively by humans and systems within the architecture to achieve key
use cases. The goal is to turn raw data (that is managed and handled by
the Data Foundation capabilities) into actionable insight.

Companies are following different platform strategies here: While some
companies are having dedicated analytics platform being used for a wide
range of domains (like manufacturing, R&D and sales), other companies
are favouring domain specific platforms that are integrating the
analytics capabilities. The capabilities documented here are valid for
both approaches.

Manufacturing is all about closed-loop operations. A great visualization
not triggering appropriate actions is worthless. Therefore, insights
must be efficiently derived from visualizations and lead to actions. The
platform therefore must integrate actions into the control loop.
Typically, this requires (semi-) automatic control flows into the legacy
applications using the Integrate business application capability. In
most cases a human expert will receive the proposal for a specific
action execution and will then act on his own decision. The platform is
handling this by close integration with the Manage process execution
capability.

Triggering actions at the shopfloor level has security implications as
this often requires a north-south communication. As many production
security policies are only supporting the reverse direction the platform
must enable a reliable yet secure communication.

## Analyze Data

> The ability to derive answers and deliver insight from the
> foundational data captured within the platform. The platform needs to
> support the four main classifications of analytics: ‘what happened’
> (Descriptive), 'why did it happen' (Diagnostic) 'what will happen'
> (Predictive) and ‘what to do’ (Prescriptive) and the toolchains that
> support these techniques.

### Business Intelligence

Descriptive analytics that deliver actionable business insight from the
manufacturing platform. Business Intelligence involved the definition
process of the typical reports and dashboards that are commonly provided
by the *Visualize data* capability. The analytic process is typically
iterative and thus relies on interactive data manipulation like
drill-down. There is a growing trend for so-called self-service BI. This
pull approach is shifting many tasks to the users have a business
question. It is shortening the insights process as educated users are
enabled to prepare the data to answer their questions.

### Reporting and Dashboarding

> The descriptive capability of visualizing, formatting, drill-down and
> historic interrogation of data within the manufacturing platform.

### Data Mining

The diagnostic capability required to extract and discover information
across the large amounts of data delivered by the manufacturing
platform, such as the correlation, filtering, and statistical analysis
of data. The data volume in manufacturing in constantly increasing:
While some years ago vehicle control was executed on pre-defined vehicle
characteristics like aggregate and components, today many plants are
controlling on single part level. This approach alone increases the
typical data volume by factor 10. To cope with this data mining and time
series analysis are key diagnostic approaches.

### Time Series Analysis

> The diagnostic capability of being able to analyze data within the
> context of time intervals (e.g. for analyzing event data emitted from
> facility equipment)

### Regression & Forecasting

> The predictive analytics capability of being able to understand and
> trends in the data collected from across the manufacturing platform.

### Human in the Loop Analytics

The capability of augmenting algorithms and models used in predictive
and prescriptive analytics with human experience and knowledge.

While simulation today is predominately used in the planning phase of
manufacturing (e.g., optimizing production line throughput during
reconstruction phases), this technique is being applied for
what-if-scenarios as well. As a prescriptive approach this is assisting
the human expert on how to cope with interruptions and plan deviations.

### Pattern Matching

> The predictive capability to recognize patterns and irregularities in
> data (both computer formatted and binary data such as image and audio
> data)

### Machine and Deep Learning

The capability to learn, infer and automatically build predictive models
from data within the manufacturing platform.

The application of machine learning is an increasing domain. The
platform must provide optimized environment for training and analytics
processes executed by data engineers and scientist. MLOps must be part
of the platform to make the manual tasks more efficient and reliable.
The platform should reduce the huge gap between the data science and
manufacturing (mental) models.

### Complex Event Processing

The prescriptive ability to processes real-time event and streamed data
(particularly on-device) in order to also gain insight across these
streams in real-time.

### Simulation

The prescriptive technique of developing a modelled representation of an
asset, environment or process to understand possible outcomes,
probabilities and scenarios.

While simulation today is predominately used in the planning phase of
manufacturing (e.g., optimizing production line throughput during
reconstruction phases), this technique is being applied for
what-if-scenarios as well. As a prescriptive approach this is assisting
the human expert on how to cope with interruptions and plan deviations.

## Develop Data

> The capability to use data efficiently and effectively within the
> manufacturing platform.

### Distributed Query

> Distributed data queries provide a common mechanism that allows data
> to be queried and processed across multiple instances of storage
> technologies and/or partitions of data. This capability ensures that
> data can be used across the range of technologies in the manufacturing
> platform independent of its underlying storage technology.

### Data Labs

> The ability for data engineers and scientists to have data sets and
> environment for them to perform valid and appropriate analytics within
> the manufacturing platform.

### Feature Store

> The capability and process to construct, manage and execute known,
> operationally valid models within the data platform.

## Visualize Data

This capability allows data to be represented graphically. Data may be
exposed directly from the platform in a manner suitable for direct
visualization and to visualize state (e.g. for real time monitoring), or
visualizations that are suitable for exploration of data (paired with
analytics capabilities). In addition, visualization may be volumetric or
represent a model of a physical environment (for instance, for use with
a Digital Twin).

Reports and dashboards are created by application of the Analyze data
capability. Typically, this is executed by vendor specific BI tools. The
platform must provide the integration of these tools. This integration
has many dependencies with the Store data capability and a tool
independent storage is important. Many companies are using multiple BI
tools even within the same business domain. While many of these insights
are consumed in office environments, andon boards are an example for
visualizing data directly at the shopfloor. For the later the platform
must provide the integration of customized visualizations.

There are huge differences on the acceptable data age to be displayed.
While visualizations directly at the shopfloor sometimes need updates
within a second (e.g., vehicle specific information for worker
guidance), visualizations like weekly product targets are more in the
range of minutes and hours. The platform must be able to handle these
different requirements with a selection of different visualization
approaches.

As a replacement for the still all too common printed reports
visualization processes need a high availability and maturity: Having no
information during the regular morning rounds is an unacceptable risk.
On the other hand, live data instead of legacy data on paper is moving
production to a new level of responsiveness.

Some manufacturing visualizations have been carefully crafted and
refined over years (like specific start-up curves). Therefore, the
integration of custom-built charts is characteristic for the platform.

### 2D Visualization

### 3D Visualization

## Data Discovery

> Data discover allow for consumers of data of the platform to be able
> to understand which data products are available within the platform,
> how to use them (APIs etc.) and any constraints on usage (legal,
> operational etc.). This capability can be realized from a system
> perspective (through data discovery APIs) or a human consumption
> perspective (e.g. data cataloguing, search and publishing). This
> capability is important within the manufacturing platform to
> understand what data is available across processes, its provenance,
> operational constraints and access patterns.

Additional information like provenance, operational constraint,
ownership, and access restrictions are being made available by the
platform to further refine the discovery process.

To improve data discovery cataloguing solutions are usually covering the
entire enterprise. The platform therefore must enable the integration of
corporatewide solutions. An example scenario is the evaluation of part
range which is requiring the combination of logistics and production
domain data.

### Knowledge graph

### Data Marketplace

# Application Enablement \[Maintainer: Daniel\]

Applications are the only means by which users can experience a
production platform. Applications are turning platform capabilities into
business value based on the use cases implemented. A wide range of
application architectures needs to be supported: from traditional N-tier
architectures to modern micro-services, event driven and low code
architectures.

Most applications are relying on the underlying platform capabilities,
e.g., interoperability for async messaging, data storage or event
processing.

In the complex manufacturing IT landscape professional dependency and
lifecycles management are key elements of the platform.

## Develop Applications

While many manufacturing applications are COTS (like SCADA, MES or WMS)
every plant is additionally more or less depending on custom-built
solutions. These solutions are developed both in-house and from external
partners. In any case the platform must provide a professional
continuous integration (CI) approach to enable this distributed
development approach. This is even more important in regulated
environments.

### Developer Tooling

Tools for developing applications are needed. From traditional tooling
running on the PC of the developer, to cloud based or low code tooling.

### Support Low Code Application Development

Low code application development provides a fast and easy approach for
simple applications like custom inventory management. Experienced
business users can create these (data entry) applications without IT
support. The challenge of this “grass root” approach is keeping these
solutions in a manageable state. If these applications become too
complex, they are much harder to maintain than classical development
approaches. The platform must therefore enable an optional integration
of low code application and provide mechanism to support an low-code to
non-low-code evolution.

### Manage Application Lifecycle

For a more complex application environment, lifecycle tooling to keep
track of requirements, software assest, their dependencies could be
required.

## Deploy Applications

Getting from development to production requires deployment and
configuration management.

###

### Continuus Integration and Deployment (CI/CD)

All IT systems need to be maintained and updated on a regular basis.
Security updates are typically applied once a month, minor updates at
least once a year. IT systems in general and applications specifically
should be updatable without significant downtime e.g., by applying
rolling update techniques. While continuous deployment (CD) is common in
many IT domains by using sophisticated deployment pipelines, within
manufacturing this is yet a challenge for the same reasons listed in the
*Configure application* capability.

As manufacturing systems are cyber-physical, integration testing is a
challenging task. The physical systems must be simulated to verify that
the overall system will behave as intended after the deployment.
Rollback scenarios are important but are only fixing the IT parts. All
physical effects (e.g., products being assembled, parts being produced)
must be ejected from the manufacturing process and being reworked or
scrapped.

Despite these challenges, deployments become highly automated and are
executed with a pushbutton approach executed by human experts. This is
reducing the deployment process from hours to minutes and making sure
that every step is executed as intended without “manual magic”.
Application deployments are quite often being combined with an update of
the underlying IT systems (like network, operating system, or database).
This ensures a consistent IT stack.

### Manage configurations

Configuration management in general and application configuration in
particular is an underestimated task. It is requiring both business
process and technical knowledge. Applications must be adapted to
(changing) business process without negative effects on operations. This
is especially IT maintenance windows are becoming smaller and smaller.
Opposed to other IT domain, where configurations can be verified e.g.
with AB testing approaches, production is demanding a deterministic
approach where the configuration is pre-defined for every product being
produced. The platform should provide a central and generic application
configuration support.

The central configuration repositories can be used to ensure
consistency, but also detect issues like configuration drift. Yet the
decentral structure of manufacturing demands decentral configurations as
well. Only varying configurations enable global manufacturing of
different product using identical IT systems.

IT automation is used to ensure compliance with policies.

## Serve Applications

Applications play an important role, as they implement use cases, thus
providing the actual business value. We see three different types of
applications:

### Serve Front-End

Applications which required human interaction. A lot of different
interaction technologies, from traditional PC, via Industrial HMI Touch
Display (usable with gloves), Voice Command, Tablets, Mobile Phone to
Augmented Reality is imaginable. The majority will be more traditional
web-based or rich client like solutions. Front-End Applications have
special requirements regarding usability, authentication & authorization
which need to be considered. A wide range of different personas with
different IT backgrounds and skill levels need to be supported.

### Serve Backend

Backend-Application provide the heavy lifting. Here is where the actual
business logic and algorithms take place. They will probably rely on
capabilities from the data platform. Front-End applications consume
backend applications via APIs.

### Serve Control Loop

Control Loop Applications are really close to operational level. They
control critical parts of the manufacturing process using open or closed
feedback loops from sensors to actuators. Think PLC and SCADA type of
functionality, but software defined. Control Loop Applications can have
demanding requirements regarding availability and latency. Example a
software defined PLC with sub-millisecond latency requirements. Brings
also special security requirements required for command execution to
devices. Depending on the type of devices, safety criticality and
corresponding certifications can be required.

## Manage business process execution

There are many approaches to execute business process: workflow
management, rule processing and complex event processing. It is
important that the process implementations are flexible to changes.
Quite too often they are “locked-in” into multiple legacy systems (for
example PLCs) and therefore resistant to change.

The topic can be split into the follwing aspects

-   Business Rules

-   Business Process Management or Workflow Management

Busines Rules and Process have two aspects - a Modeling / Tooling part,
and a runtime/processing part. The first is about

Workflow management is still not widely adopted yet in manufacturing
compared to established domains like HR or finance. The business process
should be modelled using standards like BPMN to enable different runtime
execution environments. Like with rules, it externalized business
processes from the applications and makes them more flexible. Things
like approval steps, parallel sequencing of tasks etc. Like business
rules, this breaks down into runtime and modelling aspect. Business
Process can be long running and have a state which needs to be managed
carefully. Business Process heavily rely on Business Rules (“Scrapping
of parts of value \>1000€ need approval by shift manager”), to
externalize the branching conditions of the process flow.

Deviations from planned status are triggering alerts. Some alerts are
handled by system, while others are presented to humans. This human
interaction is typically established by task lists. Experts are in the
lead to take (business) decisions based on the tasked being assigned to
them. A challenge here is the appropriate presentation of these tasks
into the existing working environment.

### Rule Modeling Tools

Externalization of business rules does need modelling tools. The tooling
needs to support a wide range of personas with different IT background
(“business users”). It can range from simple MIN/MAX value input fields,
via Excel based decision tables and front-end applications to domain
specific languages, and programming languages. There does not need to be
a single central modeling tooling, for different scopes, different
tools, or multiple deployments of the same tools, can be needed.

### Rule Processing

Rule processing is about the externalization of rules, out of
programming code. Instead of hard coding rules in a programming
language, the rules are stored out of the code. The code uses the rule
processing service (can be local or remote) to determine next steps /
actions. It enables easy changing of the rules, without changing the
source code. If needed, rules can even be changed at runtime.

### Complex Event Processing

Complex Event Processing (CEP) is based on rules processing, but able to
process more complex information. This can be due to the need of
aggregating different data source or event streams. As changes in data
sources can be seen as particular event streams, CEP is also known as
stream processing. The power of event streaming lies in the real-time
processing of a multitude unrelated events to derive actions. An example
is the handling of machine alerts which are processed differently in the
context of additional conditions like shift breaks or production
capacity levels. Including historical data (e.g., to detect data drifts)
makes CEP even more powerful.

### Model Business Process

Contains the development / modeling aspect. Tooling (e.g. via web
frontend) to allow easy, fast change of the process to implement
required changes. Tooling is used by a wide range of personas with
different IT backgrounds.

### Execute Business Process

Contains the runtime aspect and is responsible of the actual execution
of the process. Waits for events (“Approved by shift operator”) to then
execute the next step of the process (“Scrap part”).

### Manage Task lists

Execution of business processes needs some kind of task list management,
so that a human worker can see a list of tasks / work orders to execute.
“Approve scraping of this batch yes / no - escalate to supervisor”

### Handle Alerts and Notification

Not only during the execution of business processes, but in a lot of
different contexts, alerts and notification can occur that need to be
handled, e.g. with acknowledgment by a human operator, escalation to a
shift supervisor etc.

## Operate Systems and Applications

Manufacturing is demanding a wide range of systems being deployed from
edge to cloud. This is resulting in complex IT operations procedures. IT
operations is only successful if it is in sync with the non-IT systems
and not focussing on the applications only. Therefore, at least part of
the IT operations is quite often part of the manufacturing organization.
The platform therefore must provide constant SLAs for both the OT and IT
domain. Otherwise, parts of the system will be optimized at the expense
of the other (e.g., reliability vs. modifiability).

The combination of IT and business process monitoring is a key success
factory for reliable platform operations. It is helping to understand
the bi-directional influences and dependencies. If problems are
gradually increasing (e.g., throughput of messages) business processes
can adapt accordingly.

While the practice of DevOps is gaining a lot of momentum in other IT
domains, this is still an exception for manufacturing IT. But moving
workloads to the cloud in combination with a decomposition of the
existing rather monolithic applications will change the current
operation procedures as well. Therefore, support for DevOps is a key
platform capability that must be implemented yet and extent to more and
more services.

### Provide Flexible Compute, Network Storage

Place workload (containerized or virtualized) to where it is needed and
where enough resources are available, manage the available
compute/network/storage resource at the specific location. The different
non-functional requirements of workloads (e.g. high availability,
disaster recovery, failover, scalability, low latency) must be
supported.

Cloud like, next to self-service IaaS and PaaS services for

-   compute (virtualized and containerized)

-   network (software defined)

-   storage (file, block and object storage)

Workload should run as close to the core as possible to simplify
management and operations, and as decentral as needed to support
non-function requirements (data governance, data transmission cost,
latency).

### Manage Updates

All systems need to be maintained and updated on a regular basis. Best
practices are for security updates / patch updates to be applied once a
month, minor updates at least once a year. Platforms and applications
should be updatable without significant downtime e.g., by applying
rolling update techniques.

### Manage Configuration

Configuration management in general and application configuration in
particular is an underestimated task. It is requiring both business
process and technical knowledge. Applications must be adapted to
(changing) business process without negative effects on operations. This
is especially IT maintenance windows are becoming smaller and smaller.
Opposed to other IT domain, where configurations can be verified e.g.
with AB testing approaches, production is demanding a deterministic
approach where the configuration is pre-defined for every product being
produced. The platform should provide a central and generic application
configuration support.

The central configuration repositories can be used to ensure
consistency, but also detect issues like configuration drift. Yet the
decentral structure of manufacturing demands decentral configurations as
well. Only varying configurations enable global manufacturing of
different product using identical IT systems.

### IT Automation

One piece of the puzzle to manage complexity is automation. Provisioning
of systems, configuration (esp. Compliance with security policies),
networks / firewall config can be very time consuming. IT automation
concepts and tools help to reduce the effort, while ensuring consistent
management. E.g. all systems are configured automatically on a daily
basis according to security hardening guidelines.

### Monitoring

Monitoring of all involved systems and components is crucial to be able
to react to problems, but also to plan proactively, e.g. regarding
capacity. SLA monitoring is needed, esp. Operation tasks are outsourced.

### Monitor Consumption / Charge Back

In larger organization, charge back of consumed service to cost centers
is required. Esp. If cloud like models are used. Charge back relies on
monitoring data and is integrated with ER

Holistic monitoring of IT service consumption is still in a nascent
state. In larger organizations consumption is typically measured with
hardware usage and being charged to the respective cost centers. To
enable a data-driven enterprise data and service consumption the
platform must monitor and document this. This information is the basis
for (virtual) revenue streams that will be credited to the providers of
the data and services. Some companies are already integrating (external)
monetarization services into their platforms to incentivize the intended
transformation to a data-driven enterprise.

In addition, consumption monitoring is a key capability for sustainable
IT. The knowledge of consumption is the essential foundation for
important decisions like application retirement or cloud migration.

<img src="./assets/images/image4.png" style="width:7.97986in;height:3.15in" />