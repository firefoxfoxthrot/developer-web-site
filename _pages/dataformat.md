---
cover: false
header:
  overlay_color: "#000"
  overlay_filter: "0.25"
  overlay_image: /assets/images/dev-data-background.jpg
  og_image: /assets/images/bc-card.jpg
title: Data Formats
hide_description: true
classes:
  - wide
permalink: /dataformat/
sidebar:
  nav: dataformat
---

## Overview

_Data formats are the hidden heroes of technology. They're what allow
for the accurate usage of data. Blockchain Commons technologies are
built on a stack of four data formats. Together they allow for
deterministic, self-identifying storage of data in a
privacy-preserving way._

_From the top down, these formats are:_

* [**Envelope**](/envelope/) is a Uniform Resource format that can be
used to preserve both digital assets and metadata and which can be
selectively elided to allow for the maintenance of privacy.
* [**Animated QRs**](/animated-qrs/) offer a way to sequence QRs using
Uniform Resources, allowing for the transmission of larger amounts of data.
* [**Uniform Resources**](/ur/) is a self-identifying data format that
ensures that data is interoperable and will not suffer from bitrot if
it's rediscovered far in the future.
* [**ByteWords**](/bytewords/) is a methodology for representing data as
standard words that's utilized in the creation of UR's URIs.
* [**dCBOR**](/dcbor/) is a deterministic variant of the CBOR standard
that allows for the hash-based elision used in Envelope.
