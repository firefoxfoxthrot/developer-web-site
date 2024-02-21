---
cover: false
header:
  overlay_color: "#000"
  overlay_filter: "0.25"
  overlay_image: /assets/images/dev-data-background.jpg
  og_image: /assets/images/bc-card.jpg
title: Gordian Envelope
hide_description: true
classes:
  - wide
permalink: /envelope/
sidebar:
  nav: envelope
---

## Overview

<a href="https://www.youtube.com/watch?v=OcnpYqHn8NQ"><img src="https://img.youtube.com/vi/OcnpYqHn8NQ/mqdefault.jpg" style="float: right; border: 2px solid blue"></a>

Gordian Envelope is a specification for the achitecture of a “smart
document". It uses CBOR to support the secure, reliable, and
deterministic storage and transmission of data such as seeds, keys,
decentralized identifiers, and verifiable credentials in a way that
enables privacy while preserving structure. The format is very simple
and compact, with minimal overhead, but documents can ultimately be as
complex as needed. Gordian Envelope's privacy features are built on a
hashed Merkle Tree that supports cryptography and privacy-related
methodologies such as [progressive
trust](https://www.blockchaincommons.com/musings/musings-progressive-trust/)
and Merkle-based selective disclosure.

Blockchain Commons is currently working with multiple companies on the
development and deployment of Gordian Envelopes via regular biweekly
meetings; [contact us](mailto:team@blockchaincommons.com) if you'd
like to be involved. Envelope is also on the experimental track as an
[Informational Draft for the
IETF](https://blockchaincommons.github.io/WIPs-IETF-draft-envelope/draft-mcnally-envelope.html).
Further, ongoing discussions are occurring with the W3C Credentials
Community Group.

### The Envelope as Metaphor

The name "envelope" was chosen for this smart-document architecture
because that provides an excellent metaphor for its capabilities.

<figure class="half">
  <a href="/assets/images/envelope/envelope-canhold.jpg"><img src="/assets/images/envelope/envelope-canhold.jpg"></a>
  <a href="/assets/images/envelope/envelope-cando.jpg"><img src="/assets/images/envelope/envelope-cando.jpg"></a>
</figure>

These capabilities include:

* **Envelopes can have things written on them.** Plaintext parts of a
    Gordian Envelope can be read by anyone.
* **Envelopes can have routing instructions.** That plaintext
    information can include data on how to use the Gordian Envelope,
    such as how to open or close it.
* **Envelopes can contain things.** Things can be placed within the
    structure of a Gordian Envelope.
* **Envelopes can contain envelopes.** The Gordian Envelope structure
    is fully recursive: any part of an envelope can actually be
    another envelope.
* **Envelopes can have a seal.** A signature can be made for the
    contents of a Gordian Envelope, verifying their authenticity and
    that they haven't been changed.
* **Envelopes can be certified.** Beyond just guarding against
    changes, a Gordian Envelope signature can also act as a
    certification of the envelope's contents by some authority.
* **Envelopes can be closed.** Encryption allows any part of a Gordian
    Envelope to be protected from prying eyes.
* **Envelopes can have windows.** Selective disclosure allows for some
    parts of a Gordian Envelope to be readable while others have been
    redacted. Merkle proofs can proof that those parts were present in
    the original envelope.
* **Different recipients can open envelopes in different ways.** Just
    as people might use letter openers, their fingers, or a machine to
    open a normal envelope, special permits can grant people different
    ways to open a Gordian Envelope.

## Why Are Envelopes Important?

The Gordian Envelope is intended as a more privacy-focused encoding
architecture than existing data formats such as JWT and JSON-LD. We
believe it has a better security architecture than JWT and that it
doesn't fall victim to the barriers of canonicalization complexity
found in JSON-LD — which should together permit better security
reviews of the Gordian Envelope design.

However, new features of Gordian Envelope not available in JWT or
JSON-LD offer some of the best arguments for using the Smart Document
structure.

### Fundamental Design

Gordian Envelope was designed with two key goals in mind: to be
_Structure-Ready_, allowing for the reliable and interopable storage
and transmission of information; and to be _Privacy-Ready_, ensuring
that transmission of that data can occur in a privacy-protecting
manner.

* **Structure-Ready.** Gordian Envelope is designed as a Smart
    Document, meant to store information about a subject. More than
    that, it's a meta-document that can contain or refer to other
    documents. It can support multiple data formats, from simple
    hierarchical structures to labeled property graphs, semantic
    triples, and other forms of structured graphs. Though its
    fundamental structure is a tree, it can even be used to create
    DAGs through references between Envelopes. Besides protecting at-rest data, Envelope can also enable communication with its [Request & Response](/envelope/request/) system.
    Envelope is built upon
    [dCBOR](/dcbor/) which ensures that its content is always
    deterministic, which is vital to maintain the consistency of its
    hashes.
* **Privacy-Ready.** Gordian Envelope protects the privacy of its data
    through progressive trust, allowing for holders to minimally
    disclose information by using elision or encryption, and then to
    optionally increase that disclosure over time. The fact that a
    holder can control data revelation, not just an issuer, creates a
    new level of privacy for all stakeholders. The progressive trust
    in Gordian Envelopes is accomplished through hashing of all
    elements, which creates foundational support for cryptographic
    functions such as signing and encryption, without actually
    defining which cryptographic functions must be used.

## How Do Envelopes Work?

The following structural decisions support the goals of the Gordian
Envelope design:

* **Structured Merkle Tree.** A variant of the Merkle Tree structure
    is created by forming the hashing of the elements in the Envelope
    into a tree of digests. (In this "structured Merkle Tree", all
    nodes contain both semantic content _and_ digests, rather than
    semantic content being limited to leaves.)
* **Deterministic Representation.** There is only one way to encode
    any semantic representation within a Gordian Envelope. This is
    accomplished through the use of [Deterministic CBOR](/dcbor/) and
    the sorting of the Envelope by hashes to create a lexicographic
    order. Any Envelope that doesn't follow these strict rules can be
    rejected; as a result, there's no need to worry about different
    people adding the assertions in a different order or at different
    times: if two Envelopes contain the same data, they will be
    encoded the same way.

_Please see the [Technical Overview](/envelope/tech/) for more
specifics on how Envelopes work._

### Elision Support

* **Elision of All Elements.** Gordian Envelopes innately support
    elision for any part of its data, including subjects, predicates,
    and objects.
* **Redaction, Compression, and Encryption.** Elision can be used for
    a variety of purposes including redaction (removing information),
    compression (removing duplicate information), and encryption
    (enciphering information).
* **Holder-initiated Redaction.** Elision can be performed by the
    holder of a Gordian Envelope, not just the issuer.
* **Granular Holder Control.** Elision can not only be performed by
    any Holder, but also for any data, allowing each entity to elide
    data as is appropriate for the management of their personal (or
    business) risk.
* **Progressive Trust.** The elision mechanics in Gordian Envelopes
    allow for [progressive
    trust](https://www.blockchaincommons.com/musings/musings-progressive-trust/),
    where increasing amounts of data are revealed over time. It can
    even be combined with encryption to escrow data to later be
    revealed.
* **Consistent Hashing.** Even when elided or encrypted, hashes for
    those parts of the Gordian Envelope remain the same.

### Privacy Support

* **Proof of Inclusion.** As an alternative to presenting redactive
    structures, proofs of inclusion can be included in top-level
    hashes.
* **Herd Privacy.** Proofs of inclusion allow for herd privacy where
    all members of a class can share data such as a VC or DID without
    revealing individual information.
* **Non-Correlation.** Encrypted Gordian Envelope data can optionally
    be made less correlatable with the addition of salt.

### Communication Support

* **Expressions.** Envelope elements can be recognized as functions and parameters, allowing for the encoding and evaluation of expressions.
* **Requests/Responses.** Expressions can be wrapped up in [Requests](/envelope/request/), allowing for the communication between two entities. Responses can be sent in reply to Requests.

### Authentication Support

* **Symmetric Key Permits.** Gordian Envelopes can be locked
    ("closed") using a symmetric key.
* **SSKR Permits.** Gordian Envelopes can alternatively be locked
    ("closed") using a symmetric key sharded with Shamir's Secret
    Sharing, with the shares stored with copies of the Envelope, and
    the whole enveloped thus openable if copies of the Envelope with a
    quorum of different shares are gathered.
* **Public Key Permits.** Gordian Envelopes can alternatively be
    locked ("closed") with a public key and then be opened with the
    associated private key, or vice versa.
* **Multiple Permits.** Gordian Envelopes can simultaneously be locked
    ("closed") via a variety of means and then openable by any
    appropriate individual method, with different methods likely held
    by different people.
 
### Future Looking

* **Data Storage.** The initial inspiration for Gordian Envelopes was
    secure data storage.
* **Credentials & Presentations** The usage of Gordian Envelope
    signing techniques allows for the creation of credentials and the
    ability to present them to different verifiers in different ways.
* **Distributed or Decentralized Identifiers.** Self-Certifying
    Identifiers (SCIDs) can be created and shared with peers,
    certified with a trust authority, or registered on blockchain.
* **Future Techniques.** Beyonds its technical specifics, Gordian
    Envelopes still allows for cl-sigs, bbs+, and other
    privacy-preserving techniques such as zk-proofs, differential
    privacy, etc.
* **Cryptography Agnostic.** Generally, the Gordian Envelope
    architecture is cryptography agnostic, allowing it to work with
    everything from older algorithms with silicon support through more
    modern algorithms suited to blockchains and to future zk-proof or
    quantum-attack resistent cryptographic choices.

## Envelope Videos

<table width="100%">
  <tr>
    <td width="640px">
      <b>Intro to Envelopes:</b>

{% include video id="OcnpYqHn8NQ" provider="youtube" %}

    </td>
    <td width="640px">
      <b>MVA & Ciphers:</b>

{% include video id="S0deyIHXukk" provider="youtube" %}

    </td>    
  </tr>
</table>  

_See the [Gordian Envelope playlist](https://www.youtube.com/playlist?list=PLCkrqxOY1FbooYwJ7ZhpJ_QQk8Az1aCnG) for more._

## Envelope Links

**Intro:**

* [**A Technical Overview of Envelopes**](/envelope/tech/)
* [**The Dangers of Digital Credentials in Education**](https://www.blockchaincommons.com/articles/Dangerous-Educational-Credentials/) (blog article)
* [**Protecting Your Wellness Data with Hashed Elision**](https://www.blockchaincommons.com/articles/Dangerous-Wellness-Data/) (blog article)

**Developer Resources:**

* [**Envelope Technical Documents**](https://github.com/BlockchainCommons/Gordian/tree/master/Envelope#articles) (GitHub repo)
* [**IETF Draft: The Envelope Structured Data Format**](https://blockchaincommons.github.io/WIPs-IETF-draft-envelope/draft-mcnally-envelope.html) (Editor's Draft)
* [**dCBOR: Deterministic CBOR**](/dcbor/)

**Developer Extension Resources:**

* [**Attachment**](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2023-006-envelope-attachment.md)
* [**Compression**](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2023-005-envelope-compression.md)
* [**Cryptographic Seeds**](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2023-009-envelope-seed.md)
* [**Cryptography**](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2023-013-envelope-crypto.md)
* [**Expressions**](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2023-012-envelope-expression.md)
* [**Known Values**](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2023-003-envelope-known-value.md) (GitHub repo)
* [**Request & Response**](https://developer.blockchaincommons.com/envelope/request/)
   * [**Request & Response Test Vectors**](https://developer.blockchaincommons.com/envelope/request/vectors/)
* [**Symmetric Encryption**](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2023-004-envelope-symmetric-encryption.md) (GitHub repo)

**Developer Reference Apps:**

* [**Envelope-CLI**](https://github.com/BlockchainCommons/envelope-cli-swift) (CLI implementation)
  * [**Envelope-CLI Docs**](https://github.com/BlockchainCommons/envelope-cli-swift/tree/master/Docs)
* [**CLI Usage Overview Transcript**](https://github.com/BlockchainCommons/envelope-cli-swift/blob/master/Transcripts/1-OVERVIEW-TRANSCRIPT.md) (GitHub repo)

  
### Use Cases:

* [**Overview of Envelope Use Cases**](/envelope/use-cases/)
* [**Summary of Use Cases**](/envelope/use-cases/summary/)
* [**Educational Use Cases**](https://github.com/BlockchainCommons/developer-web-site/blob/master/_pages/envelope-usecases-educational.md) (GitHub repo)
* [**Wellness Use Cases**](https://github.com/BlockchainCommons/developer-web-site/blob/master/_pages/envelope-usecases-wellness.md) (GitHub repo)
* [**Data Distribution Use Cases**](https://github.com/BlockchainCommons/developer-web-site/blob/master/_pages/envelope-usecases-data.md) (GitHub repo)
* [**Asset Control Use Cases**](https://github.com/BlockchainCommons/developer-web-site/blob/master/_pages/envelope-usecases-assets.md) (GitHub repo)
* [**Software Release Use Cases**](https://github.com/BlockchainCommons/developer-web-site/blob/master/_pages/envelope-usecases-software.md) (GitHub repo)

