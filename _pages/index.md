---
cover: true
header:
  overlay_color: "#000"
  overlay_filter: "0.25"
  overlay_image: /assets/images/qr-background.jpg
  og_image: /assets/images/bc-card.jpg
title: Blockchain Commons Developer Pages
hide_description: false
classes:
  - wide
permalink: /
sidebar:
  nav: mainside
---

_**Latest News:** Added [Achitectural Design Patterns & Auth Patterns](/architecture/patterns/auth) pages (5/8/24). Added [Envelope Executive Summary](/envelope/summary/) and [Feature List](/envelope/features/) pages (4/24/24)._
{: .notice--info}

The Gordian Stack is a layered set of specifications founded on the CBOR data format and built up from that, step by step, to support digital-asset management in a way that fulfills [the Gordian Principles](/principles/). These developer pages contain developer resources that
explain the elements in the Stack, and their importance, and make it easy
for you to adopt them.

![bc-stack](https://hackmd.io/_uploads/ByXO-7kFC.png)

The heart of the Gordian Stack is the [<font color="#ffac1c">Gordian Envelope</font>](/envelope/), a simple data-storage mechanism that organizes content into semantic triples. You don't need to know about the underlying elements to use Envelopes, so as a developer you can jump straight in and be confident that everything under Envelope is correctly abstracted to maintain layer divisions.

The [<font color="#17c3ff">Animated QR specification</font>](/animated-qrs), built on Multipart Uniform Resources (MURs), is the other major entry point to the Gordian Stack, since it allows for the transmission of large data sets, such as Bitcoin's PSBTs, across Airgaps.

Following is a description of the major layers of the Gordian Stack, in descending order.

If you have any questions or want more resources for any specific
element in the Stack, please [let us know via
email](mailto:team@blockchaincommons.com) or [file an
Issue](https://github.com/BlockchainCommons/developer-web-site/issues)
at the repo for this website.

## The <font color="#221dff">Storage</font> Layer

_The Storage Layer allows for the secure & resilient remote storage of sharded digital assets._

* **Collaborative Seed Recovery (CSR).** CSR supports the sharding of seeds using SSKR and their storage in independent storage servers such as the [Gordian Depository](https://github.com/BlockchainCommons/bc-depo-rust). Communication with Depositories occur via GSTP, an Envelope functionality.
   * See our [CSR page](/csr/).

## The <font color="#ffac1c">Envelope</font> Layer

_Digital-asset storage uses Gordian Envelope, Blockchain Commons' smart document system, which allows for hashed data elision, encryption, and much more._

* **Envelope.** Gordian Envelopes are built on URs, Blockchain Commons' foundational plain-text encoding system, and can be output as `ur:envelope`. However, Envelopes have much more functionality than simple UR text strings due to their recursive storage capabilities. They also support the new capability of hashed elision, which allows for provable redaction of data in support of [data minimization](https://www.blockchaincommons.com/musings/musings-data-minimization/). Extensions support even more functionality.
   * See our [Envelope page](/envelope/)

* **Seeds & SSKR.** Seeds and SSKR shares can be stored in Envelopes. This goes beyond simpler storage techniques such as `ur:seed` and `ur:sskr` because it can include metadata to help identify a seed and also allows the use of Envelope functionality such as elision and encryption.

* **Other Envelope Extensions.** Other Envelope extensions include existence proofs, encryption, signatures, compression, salting, known values, attachments, diffing & merging, and expressions. Envelope's features can be used or not as a developer prefers: _you only pay for what you use_. 

### <font color="#ffac1c">Envelope's</font> Expressions & Communication

_Envelope's Expressions are an extension that enables secure communication._

**Expressions.** Expressions are Envelope functions. They are a specified way to request that a specific action be undertaken when an Evelope is accessed.  
   * See [Expressions Research Paper](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2023-012-envelope-expression.md)
   
**Request/Response.** Request/Response packages up Expressions so that they can be sent to a remote recipient as a Request, who can then send a Response tied to the original request. This allows for interoperable communication using Envelopes when further security is not required.
   * See our [Envelope Request & Response page](https://developer.blockchaincommons.com/envelope/request/).

**Gordian Sealed Transaction Protocol (GSTP).** GSTP builds on top of Request/Response for those times when security <i>is</i> required. It not only supports encryption and signatures but also uniquely supports Encryption State Continuations (ESC) to securely encapsulate state information. It's used by the Gordian Depository as part of CSR.
   * See our [GSTP Research Paper](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2023-014-gstp.md).

## The <font color="#2df775">Descriptive</font> Layer

_It's important to be able to identify a seed, no matter how it's stored or transmitted._

* **Object Identity Block (OIB).** The OIB suggests best practices for organizing and displaying data that can help users  toidentify seeds. An OIB includes an icon, a name, abbreviated digest, and Lifehashes.
   * See our [OIB page](/oib/)

* **LifeHash.** The LifeHash is a graphical element in an OIB. It creates a visual hash of a seed that should be distinct and relatively unique.
   * See our [LifeHash page](/lifehash/)
   
## The <font color="#c96055">UR</font> Layer

_The UR layer encodes structured CBOR binary data into plain text strings. It's a method for sending plain-text strings or for efficiently encoding data into QRs. It's used by Envelopes, Animated QRs, and other higher level capabilities._ 

* **Bytewords.** The foundation of URs are ByteWords, which are a set of 256 carefully chosen words which each translate a byte (from `0x00` to `0xff`) into a four-letter English word. A four-word checksum for data then improves resilience.
  * See our [Bytewords page](/bytewords/)

* **Uniform Resources (URs).** Bytewords can be reduced in size by using the "minimal" form, which uses only the first and last letter of each word, which are always unique. URs therefore convert CBOR binary data into well-formed URIs by converting the data into minimal Bytewords and then preceding it with a `ur:` string followed by an appropriate tag for the data type. The result is self-identifying and transport-independent.
   * See our [UR page](/ur/)

* **Multipart UR (MURs).** URs include support for multipart URs, which divide and sequence UR data and which can be used with fountain codes to transmit the data even if a channel is unreliable.
   * See our [MUR  Implementation Guide](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2024-001-multipart-ur.md)


### UR's <font color="#17c3ff">Animated QRs</font>

_URs are formatted as a plain-text URIs, but they're optimized to allow efficient encoding as QR codes._

* **Animated QRs.** MURs are the foundation of Animated QRs, a method for transmitting data across an [airgap](/airgap/) when that data would be too large for a standard QR code. MURs' fountain codes allow for individual frames to be missed without requiring all the frames to be resent. Due to Animated QR's application for signing PSBTs over airgaps, they've become one of Blockchain Commons' most successful releases.
   * See our [Animated QRs page](/animated-qrs/)

### UR's <font color="#038e3e">Seeds & SSKR</font>

_URs can store [a variety of typed data](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2020-006-urtypes.md). That includes two data types of particular interest to wallet developers: seeds and SSKR shares._

* **Seeds.** Seeds are the foundation of digital-asset security, as they're used to generate signing keys and auth keys, often in a hierarchical manner. URs allow the encoding of seeds as `ur:seed` (though Envelopes are now preferred). Blockchain Commons' [seedtool-cli-rust](https://github.com/BlockchainCommons/seedtool-cli-rust) and [Seedtool for iOS](https://github.com/BlockchainCommons/GordianSeedTool-iOS) offer best practices for the management of seeds.

* **SSKR.** Sharded Secret Key Reconstruction (SSKR) allows a seed to be sharded into individual shares. The seed can then be reconstructed from `m` of `n` of those shares where `m ≤ n`. Currently, this is done using a variant of Shamir's Secret Sharing with expansions for two-level shares. URs allow the encoding of SSKR shares as `ur:sskr` (though Envelopes are now preferred).
   * See our [SSKR page](/sskr/).

## The <font color="#8f1402">CBOR</font> Layer

_The CBOR layer defines the deterministic binary data serialization format for the Gordian Stack._

* **CBOR.** The heart of Gordian's data format is CBOR, a data format defined by [IETF RFC 8949](https://cbor.io/spec.html). It supports the _organized_ and _tagged_ formatting of data.
   * See [Why CBOR?](https://www.blockchaincommons.com/introduction/Why-CBOR/)

* **CDE.** Determinism is a requirement for the Gordian Stack. It was loosely described in RFC 8949, but needed further detailing. Blockchain Commons' work with CBOR led to one of CBOR's original authors further describing how CBOR could be used deterministically in the [CBOR Common Deterministic Encoding (CDE) Internet-Draft](https://datatracker.ietf.org/doc/draft-ietf-cbor-cde/).

* **dCBOR.** CDE allows for the creation of application profiles, which lay out specific rules for deterministic encoding. [dCBOR](https://datatracker.ietf.org/doc/draft-mcnally-deterministic-cbor/) is Blockchain Common's CDE application profile used by Gordian Envelope. To support Envelope, it includes specific rules for things such as numeric encoding.
   * See our [dCBOR page](/dcbor/).

## Architectural Overview

_The Gordian Stack is built atop a carefully considered architecture that works to uphold human dignity and choice on the internet._

* **Architecture.** The Gordian architecture is built on specific [principles](/principles/), using specific [design patterns](/architecture/patterns/auth/), and with a general philosophy of functional partition.
   * See [our architecture page](/architecture/)
   * See [Musings of a Trust Architect](https://www.blockchaincommons.com/musings/)


## Other <font color="#888888">Future</font> Development

_A few other technologies are currently in early stages of development or integration._

* **FROST.** FROST is a Schnorr-based signature system that offers more robust multisigs. It also has the advantage of optionally integrating Distributed Key Generation (DKG), where portions of a key are held by different devices.
   * See our [FROST page](/frost/)
 
* **Collaborative Key Management (CKM).** A next-generation key-management solution, CKM uses Secure Multi Party Computation (SMPC) to keep a key separated, rather than having it all in one place. This offers an alternative to a system such as CSR that is potentially more secure. Currently, ZF FROST is the only production-ready implemention of CKM, so it's likely CKM and FROST will go hand in hand.
   * See our [CKM page](/ckm/) 

* **The Discovery Layer.** A discovery layer is planned that will allow end-users to find and identify Gordian Depositories or other online services.
  
## For More Info

Our Gordian Developer community is actively working with this resources! Join us in Discussions or at our monthly meetings!

* [Gordian Developer Community](https://github.com/BlockchainCommons/Gordian-Developer-Community/discussions)
   * [Meetings Records](https://github.com/BlockchainCommons/Gordian-Developer-Community/blob/master/meetings/README.md)
   * [Join Us!](https://www.blockchaincommons.com/subscribe/)
