---
cover: false
header:
  overlay_color: "#000"
  overlay_filter: "0.25"
  overlay_image: /assets/images/dev-seed-background.jpg
  og_image: /assets/images/bc-card.jpg
title: "SSKR: Sharded Secret Key Reconstruction"
hide_description: true
classes:
  - wide
permalink: /sskr/
sidebar:
  nav: sskr
---

## Overview

_SSKR is Sharded Secret Key Reconstruction. It's a way that you can
divide ("shard") the master seed underlying a Bitcoin HD wallet into
"shares", which a user can then distribute to friends, family, or
fiduciaries. If the user ever loses their seed, they can then
"reconstruct" it by collecting sufficient of the shares (the
"threshold")._

## Why SSKR is Important

One of the biggest challenges in the control of digital assets
(particularly the self-sovereign control of digital assets) is
[Resilience](https://github.com/BlockchainCommons/Gordian#gordian-principles).
It's too easy for a user to lose the seed or key that control their
assets, and thus the assets.

SSKR resolves the Single Point of Failure (SPOF) represented by a seed
by allowing a backup of the seed to be in a way that doesn't introduce
a Single Point of Compromise (SPOC) to the system. It does by using
Shamir's Secret Sharing to shard a secret, with the intent being that
the shares are then placed in discrete, remote locations. The seed can
only be recovered.

## How Does SSKR Work?

The basic level of SSKR allows you to create a single group of shares,
with a threshold for how many of those must be collected to
reconstruct the seed. The following shows an example from [Gordian
SeedTool](https://github.com/BlockchainCommons/GordianSeedTool-iOS) of
creating three shares, of which two must be recovered.

<figure class="third">
  <a href="/assets/images/sskr/export-1.jpg"><img src="/assets/images/sskr/export-1.jpeg"></a>
  <a href="/assets/images/sskr/export-2.jpg"><img src="/assets/images/sskr/export-2.jpeg"></a>
  <a href="/assets/images/sskr/export-3.jpg"><img src="/assets/images/sskr/export-3.jpeg"></a>  
</figure>

The user would take these shares and give one each to three different
trusted people (or places, such as a safe or bank vault). (Or, this
could be automated using [CSR](/csr/).)

Note [the overlap in words in different
shares](https://github.com/BlockchainCommons/crypto-commons/blob/master/Docs/ur-3-sskrs.md#the-difference-between-sskr-bytewords-and-sskr-urs):
this is expected. The first four words will always be the same as they
describe the share as SSKR ("tuna acid epic") of a specific length
("gyro"). The next two ("flap pose") are a fingerprint that match all
the shares in a split, and the next two ("able acid") describe the
group threshold, count, and index, plus the member threshold, so
they're the same for all the shares in a group. There's then a
checksum at the end ("toys flap solo film"), which is also how
SeedTool identifies individual shares.

SSKR | length | ID | group & member info | secret share | checksum
---|---|---|---|---|---
tuna acid epic | gyro | flap pose | able acid able | even iris... taco wolf | toys flap solo film

Note also that these words will change each time you regenerate SSKR
shares from a secret. This is also expected: there is a random factor
in SSKR generation.

### How Does Advanced SSKR Work?

SSKR supports a more advanced methodology where you can define
multiple groups, and then require a certain number of shares to come
back from each group for a certain number of groups.

The following shows an example from [Gordian
SeedTool](https://github.com/BlockchainCommons/GordianSeedTool-iOS)
where 2 of 3 shares must come back from 2 of 3 groups.


  <a href="/assets/images/sskr/export-4.jpg"><img src="/assets/images/sskr/export-4.jpeg"></a>
  <a href="/assets/images/sskr/export-5.jpg"><img src="/assets/images/sskr/export-5.jpeg"></a>
  <a href="/assets/images/sskr/export-6.jpg"><img src="/assets/images/sskr/export-6.jpeg"></a>  
</figure>

This can allow for more complex scenarios, such as a business that
hands off one set of shares to Chief Officers, and then backs that up
with a set of shares held by their accountants or some other
fiduciary.

(Though this example is symmetrical, it's not required. You could
require 2 of 3 from group #1 and 3 of 5 from group #2, and then only
require 1 of 2 gorups, which means either threshold would fulfill the
requirement.)

Once you generate advanced SSKR shares, the user would distribute them
just like basic SSKR shares, but here being very careful to understand
the roles of everyone they'ree giving shares to, since they're
creating a more complex procedure.

## Videos

<table width="100%">
  <tr>
    <td width="640px">
      <b>SSKR in Technology Overview:</b>

{% include video id="RYgOFSdUqWY?start=1612" provider="youtube" %}

    </td>
    <td width="640px">
      <b>Early Demo Video:</b>

{% include video id="PIND7J096U8" provider="youtube" %}

    </td>
  </tr>
</table>
  
## Links

* [Shamir's Secret Sharing: An Overview](https://docs.google.com/document/d/1rZJlFZcftrCM_KaxFnHUIskJKlSQzF0zFn4WIRQGDLU/edit#heading=h.imy5xgr88lxa) (Google Doc)
