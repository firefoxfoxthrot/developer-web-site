---
cover: false
header:
  overlay_color: "#000"
  overlay_filter: "0.25"
  overlay_image: /assets/images/dev-data-background.jpg
  og_image: /assets/images/bc-card.jpg
title: Envelope Executive Summary
hide_description: true
classes:
  - wide
permalink: /envelope/summary/
sidebar:
  nav: envelope
---

{% capture abstract %}
## Abstract

The Gordian Envelope, developed by Blockchain Commons, is a sophisticated smart document architecture that secures private data and enhances its management using hashed data elision. This privacy-centric feature enables provable data redaction without compromising the data's integrity or authenticity. This allows users to manage data exposure incrementally as trust develops over time. Its privacy-first features align closely with global data protection laws that advocate for data minimization and the protection of individual privacy.

The recursive structure of Gordian Envelope supports the inclusion of envelopes within envelopes, thereby enabling complex data hierarchies. By design, this creates support for a variety of structured data formats. Deterministic CBOR (dCBOR) then ensures consistent data encoding across multiple languages and platforms, maintaining data uniformity in distributed systems and constrained computing environments. This consistency is essential to ensure reliable data verification and authentication and to support decentralized applications, addressing common challenges in data interchange and storage.

Gordian Envelope is built to support industries where data security and privacy are critical. In the healthcare & wellness industries, it is used to share sensitive patient data in compliance with HIPAA and to collect public health data while simultaneously protecting participants through herd privacy. At financial institutions, it enables secure transactions while supporting regulatory requirements such as dual control. In educational institutions, it maintains the integrity and verifiability of digital credentials even when a holder elides some of the data for privacy purposes. Additionally, digital wallet developers deploy Gordian Envelope to enhance the security and privacy of their apps, ensuring the robust protection of users' digital identities and assets.

Blockchain Commons supports Gordian Envelope with all the specifications, reference libraries, documentation, and other tools necessary for developers to effectively integrate and deploy Gordian Envelope solutions. It also promotes a robust and collaborative developer community, built around monthly meetings, live Signal chats, and GitHub Discussions that enhances the architecture's adoption and demonstrates its practical deployment and relevance in today's digital landscape.
{% endcapture%}

<div class="notice--info">{{ abstract | markdownify }}</div>

## Executive Summary

Gordian Envelope, a Blockchain Commons initiative, is an advanced smart document architecture designed to enhance secure and privacy-preserving data storage and transmission. This is achieved through structured data and hashing that provides any holder the flexibility to redact data as needed.

Hashed data elision is the foundation that enables provable data redaction without compromising integrity or authenticity. The core specification employs the well-established quantum-resistant SHA-256 algorithm to build structured Merkle trees, ensuring robust and cryptographically secure data. Gordian Envelope enables several approaches for holder-initiated elision, to provide fine-grained control over data exposure. Signatures maintain their consistency and verifiability even after redaction, as they are computed across the structured trees of hashes, rather than the original data.

The elision capability of Gordian Envelope is essential for complying with global data protection regulations for data minimization, while supporting individual privacy and human rights. The design promotes a progressive trust architecture, which not only facilitates phased information sharing but also adapts to evolving trust levels, enabling data holders to dynamically control the visibility of their information based on interaction and perceived risk. Leveraging this architecture supports minimal initial data disclosure with structured options to expand transparency as trust or the relationship matures over time. By enabling holders to manage their data revelation progressively, this architecture not only enhances privacy and security but also bolsters user autonomy, thereby cultivating more organic and adaptable trust across interactions.

The Gordian Envelope architecture supports a wide range of data structures, from various relational hierarchical structures, simple linked lists, or node or edge-labeled graphs, to accommodate complex data relationships. Its nested recursive structure can reference and encapsulate other Envelopes, enabling more complex data structures and scenarios. Gordian Envelope offers schema flexibility—no schema is required, allowing for enhanced adaptability and ease of use, yet supports formal schemas when necessary for specific data integrity needs or regulatory compliance.

Consistent data encoding is guaranteed across diverse platforms using dCBOR (Deterministic CBOR), available in multi-platform code libraries written in security-conscious Rust, mobile-optimized Swift, server-centric Ruby, and web-optimized Typescript, each ensuring uniformity even on constrained or low-powered hardware. This reliability is crucial in heterogeneous environments such as distributed systems and blockchain applications, where consistent integrity and authentication are required to verify and authenticate data across different languages and platforms.

Gordian Envelope is engineered to be cryptographically agnostic, adept at integrating both current and emerging encryption standards, and thus adaptable to varying trust levels and security requirements. This includes using multiple permits such as symmetric keys, public-private key pairs, and advanced cryptographic techniques such as secret sharing, bolstered by support of proof of inclusion for herd privacy, as well as support for emerging quantum-resistant algorithms, each allowing diverse security configuration tailored to specific scenarios.

Employing multiple decorrelation approaches, including salting and emerging zero-knowledge proofs, Gordian Envelope prevents unintended data correlation, thereby enhancing data confidentiality and privacy within the Envelope. This flexibility is ensured by architecture's structured and layered design for data security and verifiability, engineered to seamlessly adopt new cryptographic standards as they emerge.

Gordian Envelope is a key component of Blockchain Commons' broader Gordian Architecture and is advanced through collaborations with the IETF and W3C, aiming to establish it as a foundation for standardized secure digital architectures that can adapt to evolving cryptographic landscapes. This larger architecture introduces a range of optional enhancements to Gordian Envelope.

Envelope data can be stored in a variety of ways. Data compression optimizes storage and transmission without compromising integrity and verifiability, while selective encryption secures partial or entire contents of an Envelope. Additionally, the Gordian Architecture is designed to support advanced cryptographic solutions, including secret sharing, quorum threshold schemes, and multisig cryptography, to expand beyond basic signing and encryption. Gordian Envelope is further engineered to accommodate zero-knowledge proofs for enhanced cryptographic privacy.

Data can also be dynamic in both what it does and how it changes over time. Proof-of-inclusion, differencing, and merging tools for Gordian Envelope facilitate the auditing and integration of data changes over time, optimizing storage and streamlining data integration.

There is support for an expression language with application-specific logic within Envelopes. A sealed transaction protocol employs Envelope expressions to support encrypted and authenticated communications across potentially insecure channels such as QR codes and NFC, ensuring secure data exchanges even in vulnerable environments.

The Gordian Architecture additionally supports a wide variety of forward-looking technologies. A sealed transaction protocol employs Envelope expressions to support encrypted and authenticated communications across potentially insecure channels such as QR codes and NFC (Near-Field Communication) cards. The architecture is also designed to operate efficiently in resource-constrained environments, including low-power devices, embedded systems, and IoT.

Gordian Envelope significantly enhances data security and privacy across numerous industry sectors. In the healthcare industry, it ensures the secure handling and sharing of patient information, compliant with privacy regulations like HIPAA. Financial institutions can leverage its robust capabilities for secure transactions and compliance reporting. The technology excels in managing digital credentials by offering secure issuance and privacy-preserving verification processes that adapt based on the holder's and verifier's trust levels. More specifically, Gordian Envelope was also designed to support self-sovereign identity management by allowing individuals and organizations to control their digital identities without reliance on a central authority. Gordian Envelope also supports use cases in supply chain transparency, data provenance in scientific research and AI models, and the integrity of software releases. In the realm of digital media, Gordian Envelope safeguards journalistic integrity by verifying the source and authenticity of news content, thus combating misinformation and bolstering public trust in media outlets.

Blockchain Commons' Gordian Envelope is actively deployed today by developers to create the next generation of secure, privacy-centric digital wallets. Its application in real-world scenarios, where security and privacy are paramount, demonstrates its effectiveness. By integrating Gordian Envelope, developers are able to significantly enhance the resilience and privacy of digital wallets, crucial for protecting users' digital identities and assets. This practical deployment positions Gordian Envelope as a leading choice in the competitive field of cryptographic security solutions, underlining its role in safeguarding privacy and bolstering human rights.

Blockchain Commons actively supports the Gordian Envelope by positioning it as a leading cryptographic security tool, essential for enhancing privacy and protecting human rights. The organization drives continuous improvement and open development of the Gordian Envelope specification, libraries, and reference applications through robust collaboration with the developer community and key standards organizations like the IETF and W3C. By hosting monthly meetings and specialized roundtable events, Blockchain Commons facilitates a proactive planning process for enhancements, ensuring the Gordian Envelope remains responsive to the evolving challenges within the industry. These collaborative efforts help to foster an ecosystem where security innovations can thrive, aligning with the latest in cryptographic practices and industry needs.

Gordian Envelope is a future-proof technology that readily adapts to evolving technological needs and supports a broad spectrum of applications, from securing data at rest to digital asset management and secure communications, making it an indispensable tool for developers seeking robust, flexible, and secure data architecture solutions.
