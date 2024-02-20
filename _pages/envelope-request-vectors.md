---
cover: false
header:
  overlay_color: "#000"
  overlay_filter: "0.25"
  overlay_image: /assets/images/dev-data-background.jpg
  og_image: /assets/images/bc-card.jpg
title: "Envelope Request & Response Test Vectors"
hide_description: true
classes:
  - wide
permalink: /envelope/request/vectors/
sidebar:
  nav: envelope
---

## Base Seed

{% include seed-128.md %}

## Seed Request

**QR:**

**UR:**
```
ur:envelope/lstpcstansfytansgshdcxkgeorojthnglfnrewsntcmkptlnsjorpwdkictidhlamdmgtbbssehbsdmhsjztaoyaatpcsksmtfpjzinhsjkcxjskphsjncxkpjzjzhsjncxjskpincxjpihjojpihisihjtieihjpinjycxhsiecxjskpinidkpjkiehsjncxinjtcxisiniacxjliaiahsihiahsjyincxhskpjycxkpjycxkojljzkpjojyhsjkcxieiniajyhscxihjzinioihjtieincxjtjlidinjkdmcxgtjljzihjkjyinhsihcxjtihjskpihcxkojljzkpjojyhsjyinidkpjkcxihjycxiejljzjljpcxjskpincxjskphsjkfhoycsielftpcstansfgcsieoytpcstansflcssptpcstansfphdcxzmoycylumhmdgwspnyvadaktnsoycwmyaodihgftdllugltphlmtutytadosdwwdieferftd
```
**Envelope:**
```
request(ARID(7b33b86e)) [
    'body': «getSeed» [
        ❰seedDigest❱: Digest(ffa11a8b)
    ]
    'note': "Alias quam ullam qui reprehenderit ad quibusdam in hic occaecati aut ut voluptas dicta eligendi nobis. Molestiae neque voluptatibus et dolor qui quas?"
]
```
**CBOR:**
```
[24(40004(40012(h'7b33b86e604e3cb5ef9d1675d59c70b6ea7d1f625d062e4d14c4310f2e616cd9'))),
 {4: 24("Alias quam ullam qui reprehenderit ad quibusdam in hic occaecati aut ut voluptas dicta eligendi nobis. Molestiae neque voluptatibus et dolor qui quas?")},
 {100: [24(40006(100)),
        {24(40007(200)): 24(40001(h'ffa11a8b90954fc89ae625779ca11b8f0227573a2f8b4ed85d96ddf901a72cea'))}]}]
```

## Key Request

### Key Derivation Request

## PSBT
