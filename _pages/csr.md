---
cover: false
header:
  overlay_color: "#000"
  overlay_filter: "0.25"
  overlay_image: /assets/images/dev-seed-background.jpg
  og_image: /assets/images/bc-card.jpg
title: "CSR: Collaborative Seed Recovery"
hide_description: true
classes:
  - wide
permalink: /csr/
sidebar:
  nav: csr
---

## Overview

_CSR allows for the recovery of seeds and other secrets by dividing
responsibility for recovery up between multiple devices, some (but not
all) of which will be necessary for recovery. Its baseline recovery
mechanism uses self-sovereign recovery, while more advanced scenarios
allow for social key recovery. Backup is meant to be largely
automated, especially in the baseline scenario, while recovery may
require some user intervention._

_One of the advantages of CSR over traditional social key recovery is
that you don't have to choose friends or family that you trust. Though
you can do so, you can also entrust fragments of keys to companies
running share servers. You don't have to worry about them stealing
keys, because you're only giving them fragments (shards), but you can
trust that they'll likely still be around when you need to reconstruct
your key._

_CSR is built using [SSKR](/sskr/) to lock [Envelopes](/envelope/) of
data and to allow recovery using a variety of Authentication
methods._

## Why is CSR Important?

CSR focuses on
[Resilience](https://github.com/BlockchainCommons/Gordian#gordian-principles),
but it takes the next step beyond [SSKR](/sskr/). Whereas SSKR
provides a robust way to protect a seed _if_ the user is careful and
knows what to do, CSR goes beyond that by making it easy for users to
store their seeds in an automated way.

CSR is also built using [Gordian Envelope](/envelope/), which allows
for the storage of larger amounts of data, such as SSKR shares with
metadata.

## How Does CSR Work?

CSR is integrated into Wallet and Seed Storage apps. When a user
chooses to backup a seed, it will automatically shard the seed and
send it off to designated Share Servers. If a user wishes to assert
more agency, they can choose where those shares are stored, or even
take them offline.

Seed reconstruction requires the user to authentication using
different, predetermined methods with each Share Server. They can
include everything from passwords and email responses to personal
identification. Each authentication retrieves a share, and when
sufficient shares have been restored, the seed is reconstructed.

The following example depicts the recovery of a seed complete with
note and name, something not possible with bare SSKR.

![](/assets/images/csr/example.jpg)

_See the [CSR Architectural Overview](csr-architecture.md) for more
information._

## Videos

<table width="100%">
  <tr>
    <td width="640px">
      <b>CSR Kickoff Meeting:</b>

{% include video id="FVzTRsqcyMU" provider="youtube" %}

    </td>
    <td width="640px">
      <b>CSR Example API:</b>

{% include video id="mpCEGUiCwFg" provider="youtube" %}

    </td>
    <td width="640px">
      <b>CSR Demo:</b>
{% include video id="9fyICk0lwL0&t=3255s" provider="youtube" %}
    </td>

  </tr>
</table>

_See the [Gordian Developer Meetings: CSR &
Envelope](https://www.youtube.com/playlist?list=PLCkrqxOY1Fbp-P1Yv-7gmu75i2QS2Z6vk)
playlist for even more videos on the development of CSR and Gordian
Envelope._

## Libraries

{% include lib-envelope.md %}

## Links

**Intro:**

* [Architectural Overview](/csr/architecture/)

**Developer Resources:**

* [Sequence Diagram](/csr/sequence-diagram/)

**Developer Reference Apps:**

* [Gordian SeedTool](https://github.com/BlockchainCommons/GordianSeedTool-iOS) (app implementation)

**Use Cases:**

* [Progressive Use Cases](/csr/use-cases/)
