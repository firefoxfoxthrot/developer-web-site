---
cover: false
header:
  overlay_color: "#000"
  overlay_filter: "0.25"
  overlay_image: /assets/images/dev-arch-background.jpg
  og_image: /assets/images/bc-card.jpg
title: Gordian Architecture
hide_description: true
classes:
  - wide
permalink: /architecture/
sidebar:
  nav: architecture
---

Blockchain Commons' specifications are built to support an
architectural design for independent and resilient ownership of
digital assets, following the [Gordian Principles](/principles/). This
architecture is called The Gordian Architecture, an overall plan for
interoperable specifications and design patterns. The ultimate goal
is to prevent vendor lock-in and to remove the threats of single
points of compromise, failure, and denial so that users can personally
protect their self-sovereign digital assets without the fear of loss.

_As Above, So Below:_ the Gordian Architecture comes in two parts. At
the high level, the _Macro-Architecture_ envisions the overall shape
of digital-asset services, but it depends on a numbers of
specifications and designs, including [Data Formats](/dataformat/),
[Seed Recovery systems](/seedrecovery/), and [UX Design](/ux/).

## Macro-Architecture

The Gordian Macro-architecture is built on a design pattern of
functional partition.

Rather than following the design pattern of classic services, which
group multiple services into singular applications, the Gordian
Architecture instead separates both services and confidential data
from each other. Doing so improves privacy and security by reducing
the value of honeypots and also improves functional design by ensuring
that each application is precisely and concisely able to perform a
specific function. Many of the Gordian reference apps are actually
microservices, intended to perform small and simple but necessary
activities as part of the blockchain ecosystem.

Using functionally partitioned services, the Gordian architecture
creates a powerful and safe new methodology for financial, data, and
information operations on the internet. It also creates an ecosystem
that allows for the inclusion of multiple developers, each producing
their own applications that are all interoperable thanks to usage of
Gordian Data Format & Encoding Specifications. This improves the
overall architecture through these competitive designs and ensures
survivability of the model as a whole.

* **Service.** A service that fulfills some large-scale need for
digital-asset management, most commonly the ability to store private
information, create transactions, sign transactions, or send
transactions. *Examples:* [Gordian Seed
Tool](https://github.com/BlockchainCommons/GordianSeedTool-iOS)
(signing device), Gordian Coordinator (transaction coordinator).

* **Microservice.** A service that fulfills a small need in the
overall Gordian ecosystem such as price lookups. *Examples:*
[SpotBit](https://github.com/BlockchainCommons/spotbit).

_Please see [Gordian Architecture Roles](/architecture/roles/) for
examples of what functions can be partitioned as part of the Gordian
Macro-architecture and [Gordian Arhitecture Apps](/architecture/apps/)
for reference examples of these roles._

### Macro-Architectural Transport

With a properly partitioned ecosystem, the transport & communication
methodology among services becomes less important. Nonetheless, some
transport methods may improve privacy and security.

* **Networked.** The standard methodology for transport: direct
network communications, presumably encryped with TLS for security.

* **AirGap.** A physical gap between services or microservices, where
either side might not even be networked. This improves the security of
the non-networked side of the communication, as it will not be
vulnerable to network attacks. A service protected by an AirGap
communicates through the reading of QR Codes or through transmission
of data on MicroSD cards, NFC tags, or other removable media.

* **TorGap.** A link between services or microservices that connect
via [Tor](https://www.torproject.org/). Though both services likely
remain fully networked, they are anonymous to each other. This
improves privacy and also deters network attacks due to the
anonymity. See our [Torgap
Overview](https://github.com/BlockchainCommons/torgap/blob/master/README.md).

## Supporting Specifications

The Gordian Architecture is supported by a variety of specifications:

* [**Data Format**](/dataformat/) — Uniform Resources, Envelope,
Bytewords, and other data formats are focused primarily on
interoperability and independence.
* [**Seed Recovery**](/seedrecovery/) — Helping users to preserve
their seeds through methodologies like Collaborative Seed Recovery is
all about improving the resilience of digital assets.
* [**UX**](/ux/) — Improvements to UX such as Lifehash improves the
resilience and independence of digital assets by empowering users.

## Reference Apps

Reference apps are exemplar programs meant to show how the Gordian
architecture and its specifications are meant to work, as
demonstrations for developers. Our most up-to-date and supported reference
apps include:

* [**Gordian Seed Tool**](https://github.com/BlockchainCommons/GordianSeedTool-iOS) — An example of a seed vault and signing device, demonstrating how airgaps work.
* [**Gordian Coordinator**]() — An example of an on-network transaction coordinator, connected to airgapped devices such as Gordian Seed Tool. (Pending.)
* [**SpotBit**](https://github.com/BlockchainCommons/spotbit) — An example of a TorGapped microservice, providing pricing services.

Please see [Gordian Architecture Apps](/architecture/apps/) for a more
complete list of apps past and present.  Please see [Gordian Architure
Roles](/architecture/roles/) for examples of what functions can be
partitioned as part of the Gordian Macro-architecture.

## How the Gordian Architecture Supports Gordian Principles

The Gordian architecture supports the four [Gordian
Principles](/principles/) as follows:

* **Independence.** Users can choose which applications to use within an open ecosystem.
* **Privacy.** The partioning of services reduces data collation. Even stronger protections can be created by Airgaps and Torgaps.
* **Resilience.** The paritioned design minimizes Single Points of Compromise.
* **Openness.** Standard specifications such as UR allow anyone to connect to the ecosystem.

## Links

**Why We Do This:**

* [**Gordian Principles**](/principles/)
* [**Musings of a Trust Architect**](https://www.blockchaincommons.com/musings/) (Blockchain Commons blog)
* [**Gordian Architecture FAQ**](/architecture/faq/)

**Architectural Nodes:**

* [**Gordian Lexicon**](/architecture/lexicon/)
* [**Gordian Architecture Roles**](/architecture/roles/)
* [**Gordian Architecture Apps**](/architecture/apps/)

**Architectural Edges:**

* [**Airgap**](/airgap/)
* [**Torgap**](/torgap/)

**Self-Sovereign Identity:**

* [**The Path to Self-Sovereign Identity**](http://www.lifewithalacrity.com/2016/04/the-path-to-self-soverereign-identity.html) (Life with Alacrity blog)
* [**Self-Sovereign Identity: 5 Years On**](https://www.blockchaincommons.com/musings/SSI-5-Years-On/) (Blockchain Commons blog)
* [**The Origins of Self-Sovereign Identity**](https://www.blockchaincommons.com/musings/origins-SSI/) (Blockchain Commons blog)
