---
cover: false
header:
  overlay_color: "#000"
  overlay_filter: "0.25"
  overlay_image: /assets/images/dev-data-background.jpg
  og_image: /assets/images/bc-card.jpg
title: Deterministic CBOR (dCBOR)
hide_description: true
classes:
  - wide
permalink: /dcbor//
sidebar:
  nav: dataformat
---

## Overview

dCBOR is deterministic CBOR, a optional variant of CBOR described in
[RFC 8949](https://www.rfc-editor.org/rfc/rfc8949.html#name-deterministically-encoded-c).

## What is dCBOR Important?

A deterministic version of CBOR is critical when an application
requires the same data to always be encoded in the same way. This is
true for [Gordian Envelope](/Envelope/), which uses CBOR to arrange
data that is identified by hashes. The hashes only remain the same if
the same data is always encoded in the exact same way, hence the need
for determinism.

Determinism of data storage can also be critical for other use cases.

## How Does dCBOR Work?

Though RFC 8949 includes some requirements for dCBOR, it leaves other
options up to encoder developers. This results in dCBOR usage that is
not necessarily consistent across multiple encoders. As a result,
Blockchain Commons has produced an
[Internet-Draft](https://datatracker.ietf.org/doc/draft-mcnally-deterministic-cbor/)
to fully codify dCBOR practices.

We have also released libraries for dCBOR in Rust and Swift as well as
a command line application for testing encoding and decoding that all
follow the specifications laid out in this Draft.

## dCBOR Videos


<table width="100%">
  <tr>
    <td width="640px">
      <b>Why CBOR?</b>

{% include video id="uoD5_Vr6qzw" provider="youtube" %}

    </td>
    <td width="640px">
      <b>dCBOR Library from Blockchain Commons</b>

{% include video id="NlJE8oF1B5M" provider="youtube" %}

    </td>
  </tr>
</table>

## Libraries

{% include lib-dcbor.md %}

## Links

**Developer Resources:**

* **dCBOR IETF I-D** — https://datatracker.ietf.org/doc/draft-mcnally-deterministic-cbor/
* **Editor's Draft (Repo)** — https://github.com/BlockchainCommons/WIPs-IETF-draft-deterministic-cbor


**Developer Resource Apps:**

* **dcbor-cli Parser/Validator** - https://github.com/BlockchainCommons/dcbor-cli

## dCBOR Discussions

* [6/30/23: cbor - Requested session has been scheduled for IETF 117](https://mailarchive.ietf.org/arch/browse/cbor/?gbt=1&index=X4K-UjBZP6wxxZdWgBYEfCp2vH4)
* [5/31/23: draft-mcnally-deterministic-cbor: rationale for not going with pre-encoded data](https://mailarchive.ietf.org/arch/msg/cbor/X4K-UjBZP6wxxZdWgBYEfCp2vH4/)
* [5/8/23: Updated Drafts for dCBOR I-D and Gordian Envelope Structured Data Format I-D & IANA Tag Registration](https://mailarchive.ietf.org/arch/msg/cbor/DOUxXB-IMTPtvDeGh13ob-IjJsE/)
* [5/8/23:  Proposal for Deterministic CBOR (dCBOR) discussion at May 17th meeting](https://mailarchive.ietf.org/arch/msg/cbor/G1oXN5DlSpAt7TI5re-fb1lL69I/)
* [3/12/23: dCBOR moving from numerically-typeless systems](https://mailarchive.ietf.org/arch/msg/cbor/aiGvqw1-sQWJ4pXY3zzQuWwNVzE/)
* [3/10/23: Decoding numbers and compliance verification in dCBOR](https://mailarchive.ietf.org/arch/msg/cbor/LUQ0lMaAA1ADGuRtb1VLahnlQUg/)
* [3/10/23: New IETF Internet-Draft draft-mcnally-deterministic-cbor-00](https://mailarchive.ietf.org/arch/msg/cbor/fnz_F5lQNiDiTJFAaJGB3YJdPik/)
* [3/5/23: Deterministic CBOR as a possible DISPATCH item](https://mailarchive.ietf.org/arch/msg/cbor/qMAOUa8-wIZn5Ts2_53VunGu7Co/)
* [2/16/23: Fwd: New deterministic CBOR Libraries (Rust & Swift) from Blockchain Commons](https://mailarchive.ietf.org/arch/msg/cbor/l7nzQHFjfpK9nfBOHiQ1L-Rr558/)
