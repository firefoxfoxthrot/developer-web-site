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

_**Latest News:** Added [Executive Summary](/envelope/summary/) and [Feature List](/envelope/features/) pages (4/24/24).  Released [IETF Envelope I-D v7](https://datatracker.ietf.org/doc/draft-mcnally-envelope/) (3/31/24). Added [Multisig Custody use case for Request & Response](https://github.com/BlockchainCommons/SmartCustody/blob/master/Docs/Scenario-Multisig-RR.md) (2/28/24). Published [Envelope Request & Response Implementation Guide](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2024-004-request.md) (2/20/24)._
{: .notice--success}

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

* For a more extensive overview of Gordian Envelopes, see [Executive Summary](/envelope/summary).
* For a list of Gordian Envelope features, see [Features List](/envelope/features).
* For a technical look at Gordian Envelope, see [Technical Overview](/envelope/tech).

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

* [**Executive Summary**](/envelope/summary/)
* [**Technical Overview**](/envelope/tech/)
* [**Feature List**](/envelope/features/)

**Industry Intros:**

* [**The Dangers of Digital Credentials in Education**](https://www.blockchaincommons.com/articles/Dangerous-Educational-Credentials/) (blog article)
* [**Protecting Your Wellness Data with Hashed Elision**](https://www.blockchaincommons.com/articles/Dangerous-Wellness-Data/) (blog article)

**Developer Resources:**

* [**Envelope Technical Documents**](https://github.com/BlockchainCommons/Gordian/tree/master/Envelope#articles) (GitHub repo)
* [**IETF Draft: The Envelope Structured Data Format**](https://blockchaincommons.github.io/WIPs-IETF-draft-envelope/draft-mcnally-envelope.html) (Editor's Draft)
* [**dCBOR: Deterministic CBOR**](/dcbor/)

**Developer Extension Resources:**

* [**BCR-2023-006: Attachment**](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2023-006-envelope-attachment.md) (GitHub repo)
* [**BCR-2023-005: Compression**](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2023-005-envelope-compression.md) (GitHub repo)
* [**BCR-2023-009: Cryptographic Seeds**](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2023-009-envelope-seed.md) (GitHub repo)
* [**BCR-2023-013: Cryptography**](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2023-013-envelope-crypto.md) (GitHub repo)
* [**BCR-2023-012: Expressions**](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2023-012-envelope-expression.md) (GitHub repo)
* [**BCR-2024-006: Graphs**](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2024-006-envelope-graph.md) (GitHub repo)
* [**BCR-2023-003: Known Values**](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2023-003-envelope-known-value.md) (GitHub repo)
* [**BCR-2023-003: Known Values**](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2023-003-envelope-known-value.md) (GitHub repo)
* [**BCR-2024-004: Transport Protocol**](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2024-004-request.md) (GitHub repo)
   * [**Request & Response**](https://developer.blockchaincommons.com/envelope/request/)
   * [**Request & Response Test Vectors**](https://developer.blockchaincommons.com/envelope/request/vectors/)
* [**BCR-2023-014: Sealed Transport Protocol**](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2023-014-gstp.md) (GitHub repo)
* [**BCR-2023-004: Symmetric Encryption**](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2023-004-envelope-symmetric-encryption.md) (GitHub repo)

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

