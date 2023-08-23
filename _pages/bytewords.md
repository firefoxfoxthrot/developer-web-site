---
cover: false
header:
  overlay_color: "#000"
  overlay_filter: "0.25"
  overlay_image: /assets/images/dev-data-background.jpg
  og_image: /assets/images/bc-card.jpg
title: Bytewords
hide_description: true
classes:
  - wide
permalink: /bytewords/
sidebar:
  nav: dataformat
---

## Overview

Bytewords is a method for encoding binary objects as a sequence of
four-letter English words.

## Why is Bytewords Important?

Encoding binary strings as human-readable words allows for better
human interaction. Blockchain Commons adopted this approach not only
for improved human interactivity, but also so that CBOR data
structures could be encoded in a self-describing way, increasing their
resilience.

[BIP39](https://github.com/bitcoin/bips/blob/master/bip-0039.mediawiki)
and
[SLIP39](https://github.com/satoshilabs/slips/blob/master/slip-0039.md)
offered two existing methods for textual encoding of binary data, but
were ultimately found insufficient. Bytewords offers advantages over
existing schemes, including: use of words with a uniform length of
four letters; ability to minimally encode words with two letters;
addition of a checksum;and specific selection of "interesting" words
for improved memory.

Bytewords is used by the [Uniform Resources](/ur/) specification.

## How Does Bytewords Work?

[CBOR](/dcbor/) data is converted to a hex string and a CRC32 checksum
is appended to it. Each byte of the hex string is then converted to
one of the 256 words on Bytewords word list. For "minimal" encoding,
each byte is instead encoded as the first and last character of the
appropriate entry on the Bytewords list, which have been designed to
be unique.

["BCR-2020-012:
Bytewords"](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2020-012-bytewords.md)
lists the complete set of words and provides examples.

## Bytewords Videos


<table width="100%">
  <tr>
    <td width="640px">
      <b>Bytewords in Technical Overview</b>

{% include video id="RYgOFSdUqWY?start=973" provider="youtube" %}

    </td>
  </tr>
</table>

## Libraries

{% include lib-bytewords.md %}

## Links

**Developer Resources:**

* [**BCR-2020-012:
Bytewords**](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2020-012-bytewords.md) (Blockchain Commons Research)

