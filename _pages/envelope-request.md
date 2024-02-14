---
cover: false
header:
  overlay_color: "#000"
  overlay_filter: "0.25"
  overlay_image: /assets/images/dev-data-background.jpg
  og_image: /assets/images/bc-card.jpg
title: Envelope Request and Response
hide_description: true
classes:
  - wide
permalink: /envelope/request-response/
sidebar:
  nav: envelope
---

Gordian Envelope includes request and response functionality: one user can issue an Envelope requesting certain information or certain actions and then another user can respond to that request with the data.

## The Purpose of Request & Response

Request and response are crucial for enabling interoperability and thus interactions between different members of the digital asset ecosystem. Our two largest use cases are seed vaults talking to transaction coordinators (for example if Gordian Seed Tool wants to talk to Sparrow) and seed vaults talking to share servers (for example if Gordian Seed Tool wants to talk to Gordian Depo).

**Example Seed Vault (SV) ⇔ Network Coordinator (NC) Interactions**

* **NC Request:** Specific Seed
   * **SV Response:** Specific Seed
* **NC Request:** Specific Key
   * **SV Reponse:** Specific Key
* **NC Request:** Key-Derivation Path
   * **SV Response:** Specific Key
* **NC Request:** Unsigned PSBT
   * **SV Response:** Signed PSBT

**Example Seed Vault (SV) ⇔ Share Server (SS) Interactions**

* **SV Request:** Share with Receipt
  * **SS Response:** Specific Share
* **SV Request:** Shares
  * **SS Response:** All Shares
 
A request/response system is crucial because of the complexity of many of these digital task. A user may not be able to find a specific seed or even moreso to generate a key along an appropriate derivation path without guidance. A request/response system minimizes both errors and user frustration.

It becomes even more important as tasks are combined together for more complex projects. The [multisig self-sovereign scenario](https://github.com/BlockchainCommons/SmartCustody/blob/master/Docs/Scenario-Multisig.md) is one such example. It demonstrates how to safely secure digital assets using keys on two closely held devices. However, it ultimately proved too complex for more users. A system built on requests and responses that told users what to do as part of an interactive process would be more likely to be successful.

## Example Seed

{% include seed-128.md %}

## The Foundation of Request & Response: Expressions

Requests and responses are built atop an Envelope functionality called [Expressions](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2023-012-envelope-expression.md). Expressions are assentially functions. They take the following form:

```
«function» [
    ❰parameter❱: argument
    ❰parameter❱: argument
    ...
]
```
The function is the subject and then assertions each define a parameter and argument for that function.

A function to retrieve a seed looks as follows:
```
100 [
        200: Digest(ffa11a8b)
]
```


```
«getSeed» [
        ❰seedDigest❱: Digest(ffa11a8b)
]
```

## Wrapping Up Request & Response: GSTP

## 

- user involvement
- OIB
