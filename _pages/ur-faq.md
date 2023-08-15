---
cover: false
header:
  overlay_color: "#000"
  overlay_filter: "0.25"
  overlay_image: /assets/images/dev-data-background.jpg
  og_image: /assets/images/bc-card.jpg
title: UR FAQ
hide_description: true
classes:
  - wide
permalink: /ur/faq/
sidebar:
  nav: ur
---

## What is an Airgap?

You can't ever be certain that a network or serial interface between
two devices won't lead to one of those devices corrupting the
other. Nor can you be certain that a networked connection is proof
from man-in-the-middle attacks. That leads to the need for airgaps,
where devices don't physically connect except "through a gap of
air". In recent years, QR codes have been a prime method of bridging
airgaps: they leverage the cameras and displays in the devices to
communicate. Airgaps can also be bridged by NFCs, MicroSDs, and other
methods that remove the real-time interactivity of a networked
connection.

URs are generally important for any type of interoperability between
devices, because their self-identifications makes it easy for a
receiving device to know what they're getting. However, they're
particularly important when QRs are being used to communicate through
an airgap, because of UR's support for QRs and particularly for
Animated QRs.

Blockchain Commons' development of airgap specifications is not just
the product of our work, but also cooperation with other Bitcoin
wallet companies to create digital formats, specifications, and
reference apps that support new ways to protect your digital
assets. This discussion happens primarily in the [Gordian Developer
Community](https://github.com/BlockchainCommons/Gordian-Developer-Community/discussions).

## What Tools Can I Use to Understand CBOR?

Obviously, the most important tool is the [CBOR
reference](https://tools.ietf.org/html/rfc7049), with our [dCBOR
specification](https://datatracker.ietf.org/doc/draft-mcnally-deterministic-cbor/)
trailing close behind.

CBOR has a more human-readable text [diagnostic
notation](https://datatracker.ietf.org/doc/html/rfc7049#page-33) you
should become familiar with. When you are testing your understanding
of how CBOR encoding works or debugging, you can use the [CBOR
Playground](http://cbor.me/) to transform CBOR between hex and
diagnostic notation, or if you prefer a command-line implementation,
the [CBOR-cli](https://www.npmjs.com/package/cbor-cli), which can be
installed with `npm` if you have Node.js installed.

Specifications for CBOR structures are written in the [Concise Data
Defintion Language
(CDDL)](https://datatracker.ietf.org/doc/html/rfc8610).

The [bytewords
CLI](https://github.com/BlockchainCommons/bytewords-cli) can also be
of use, since CBOR is converted to bytewords for text encoding when
constructing URs.

## What Can Be Encoded in URs?

*Any* data can be encoded as URs as long as it has a CBOR encoding and a user-defined UR type. The [Registry of Uniform Resource types](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2020-006-urtypes.md) lists data types that Blockchain Commons specifies, maintains, and promotes. You can also define proprietary [user-defined types](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2020-006-urtypes.md#user-defined-types-x-).

To date, the major uses have fallen into three categories:

* **PSBT Signing.** URs can transfer PSBTs as they are being signed (`ur:crypto-psbt`).
* **Key Transfer.** URs can be encode seeds (`ur:crypto-seed`), HD keys, (`ur:crypto-hdkey`), and SSKR shards (`ur:crypto-sskr`).
* **SSKR Shares.** URs can encode shards of a key or seed sharded by SSKR.
 
When data is being transferred between airgapped apps, it often is done as part of a request (`ur:crypto-request`) / response (`ur:crypto-response`) interaction, as defined in [BCR-2021-001](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2021-001-request.md).
