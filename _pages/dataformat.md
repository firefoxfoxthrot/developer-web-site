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
built on a stack of data formats. Together they allow for
deterministic, self-identifying transmission of data in a
privacy-preserving way._

_From the top down, these formats are:_

* [**Envelope**](/envelope/) is a CBOR format that can be
used to transmit both digital assets and metadata and which can be
selectively elided to allow for the maintenance of privacy.
* [**Animated QRs**](/animated-qrs/) let you exceed the normal
capacity limits of QR codes. These sequenced QR codes are formatted
using the Uniform Resource format.
* [**Uniform Resources**](/ur/) (URs) are a URI packaging for CBOR that is
self-identifying to ensure that data is interoperable and can be understood
in the future, even if current applications are no longer available.
* [**Bytewords**](/bytewords/) can represent any data as a sequence of
simple words (or in the more compact "minimal" form as a sequence of letters).
Uniform Resources are built from compact sequences of Bytewords.
* [**dCBOR**](/dcbor/) is a deterministic variant of the CBOR standard.
It's used for CBOR contained in URs and generally is required for
multi-party protocols where distributed consensus is important.
