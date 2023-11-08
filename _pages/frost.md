---
cover: false
header:
  overlay_color: "#000"
  overlay_filter: "0.25"
  overlay_image: /assets/images/dev-seed-background.jpg
  og_image: /assets/images/bc-card.jpg
title: "FROST: Flexible Round-Optimized Schnorr Threshold Signatures"
hide_description: true
classes:
  - wide
permalink: /frost/
sidebar:
  nav: frost
---

## Overview

_FROST (Flexible Round-Optimized Schnorr Threshold Signatures) is a threshold signature scheme built on Schnorr signatures that allows for
"T of N" signers, each of whom hold a share of a private key, to produce a valid signature for the private key (where T is the threshold). Because of its
[foundation in Schnorr](https://www.blockchaincommons.com/musings/Schnorr-Intro/), it has several interesting characteristics, such as signature aggregation,
where a set of signatures look exactly the same as a single signature. Beyond that, FROST improves on the fundamentals
of Schnorr through improved network efficiency and protection against forgery attacks._

## Why is FROST Important?

Using a Schnorr-enabled signature scheme allows for [many advantages](https://www.blockchaincommons.com/musings/Schnorr-Intro/) including compactness
and faster verification as well as the use of signature aggregation, adapter signatures, blind signatures, and threshold signatures. Each of
these adds vital tools to the toolkit of a signature designer.

Some of the biggest benefits come from the threshold signatures at the heart of FROST, which improve
the [resilience](/principles/) of digital assets. Traditionally, multisigs or Shamir's Secret Sharing were the ways to create this type of
resilience, but they each had limitations. Multisigs could become quite large as more signatures were added, while Shamir's Secret
Sharing creating vulnerabilities on reconstruction (and also had a history of problematic implementations). FROST resolves size issues
with its aggregate signatures (which are always the same size), while the Distributed Key Generation (DKG) methodology creates keys that are _never_ in
one place!

## How Does FROST Work?

FROST is fully described in [a paper](https://eprint.iacr.org/2020/852.pdf) by Chelsea Komlo and Ian Goldberg. Some of the fundamental elements
of FROST are:

**Schnorr Signatures.** A signature scheme based on finite fields rather than prime numbers. Besides being very elegant, Schnorr signatures have numerous other advantages, as discussed in ["Musings of a Trust
Architect: A Layperson's Intro to Schnorr"](https://www.blockchaincommons.com/musings/Schnorr-Intro/).

**Signature Aggregation.** One of the advantages of Schnorr signatures it that they can easily be added to or subtracted
from each other as part of its finite field operations, creating signature aggregation, where all signatures are the same size, no matter how
many signatures they contain. 

**Distributed Key Generation (DKG).** One of the core features of FROST is Distributed Key Generation: rather than a key being created,
then broken apart to allow for threshold signing with the shares, the shares are instead each created individually. This means that they key never exists in a single place.

**Trusted Dealer Generation.** This is the traditional methodology for generating shares, where a key is created then broken apart by
a "trusted dealer". Some FROST implementations such as [ZF FROST](https://frost.zfnd.org/index.html) also support this methodology, creating
a bridge between traditional use of Shamir's Secret Sharing and use of DKG in FROST.

**Verifiable Secret Sharing (VSS).** A methodology for verifying the existence of shares without reconstruting a secret. FROST uses a
VSS protocol invented by Paul Feldmann. 

## Videos

<table width="100%">
  <tr>
    <td width="640px">
      <b>FROST Round Table I:</b>

{% include video id="mpCEGUiCwFg" provider="youtube" %}

    </td>
  </tr>
</table>

## Links

**Intro:**

* [Understanding FROST](https://frost.zfnd.org/frost.html) (ZF FROST Book)
* [A Layperson's Intro to Schnorr](https://www.blockchaincommons.com/musings/Schnorr-Intro/) (Blockchain Commons Blog)

**Developer Resources:**

* [FROST Implementer's Round Table I](/frost/meeting1/)

**Developer Reference Libraries:**

* [ZF FROST](https://frost.zfnd.org/index.html) (ZF FROST Book)

