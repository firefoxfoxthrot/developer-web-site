---
cover: false
header:
  overlay_color: "#000"
  overlay_filter: "0.25"
  overlay_image: /assets/images/dev-seed-background.jpg
  og_image: /assets/images/bc-card.jpg
title: "CKM: Collaborative Key Management"
hide_description: true
classes:
  - wide
permalink: /ckm/
sidebar:
  nav: ckm
---

## Overview

_Collaborative Key Management (CKM) is a Blockchain Commons architecture for generating, storing, and using keys in a collaborative way, where several different devices or entities come together and use their individual secrets to generate and regenerate keys solely for the brief instant that they're needed. Our roadmap target for deployment of solutions leveraging this CKM architecture is 2024+._

_CKM expands upon [Collaborative Seed Recovery (CSR)](/csr/), our existing architecture (begun in 2019 with [SSKR](/sskr/)), which supports the resilience and recovery of seeds (not keys) using well-reviewed cryptographic code. It's still a future project, but these current pages are intended to create a touchstone for the current CSR work, so that it's appropriately future-proofed against prospective CKM development._

## Why Is CKM Important?

Digital assets are an emerging asset class in the 21st century economy. Unlike physical assets, they require a secure digital custody solution. However, in order to protect digital assets, we need someone in the physical world who will protect the keys underlying the digital assets — acting as an interface to the digital landscape.

CKM resolves the current problems of centralization and of self-custody solutions by providing a new solution that is not endangered by the lossage possibilities of self-custody or the censorship and compromise dangers of third-party custody. It also improves on CSR by creating a system much less prone to compromise and incrementally less vulnerable to censorship.

_See [CKM Architectural Overview](/ckm/architecture) for more information on both general and specific problems solved by CKM._

## How Does CSR Work?

CKM depends on SMPC (Secure Multi Party Computation). Its ultimate goal is to use secrets held by Secret Server on the internet to generate keys to be used for a variety of services. No Secret Server individually has enough key material to access digital assets; instead those keys are only generated just as they're needed by the Secret Servers working together.

_See [CKM Architectural Overview](/ckm/architecture) for more on the new technologies making this possible._

## Links

**Intro:**

* [Architectural Overview](/csr/architecture/)

**Use Cases:**

* [CSR-Focused Progressive Use Cases](/csr/use-cases/) (CSR Docs)
