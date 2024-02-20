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

![](/assets/images/envelope/request-seed.png)

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

### Seed Response

**UR:**
```
ur:envelope/lftpcstansfetansgshdcxkgeorojthnglfnrewsntcmkptlnsjorpwdkictidhlamdmgtbbssehbsdmhsjztaoycsihlrtpcsgdhkwzdtfthptokigtvwnnjsqzcxknsktdoyadcsspoycfadzttpcstantjyoeadisktjojeisdefzdydtaolytantjloxaxhdclaxvlcprfttldjobkredtlnhsidwybaeyjtswyandlgjnehtkdsidbkqzsrkphyfhsaaahdcxhnfgnepefxgdytryckticelyotsstoknfntavevaskiddmolsarntykbrybtjpksamtantjooeadlncsghykaeykaeykaocyhngrmuwzaycyzssajpsnoybdtpcskpfyhsjpjecxgdkpjpjojzihcxgdihiajecxhfinhsjzfzrdrsko
```

**Envelope:**
```
response(ARID(7b33b86e)) [
    'result': Bytes(16) [
        'isA': 'Seed'
        'hasName': "Dark Purple Peck Vial"
        'outputDescriptor': output-descriptor(Map)
    ]
]
```

**CBOR:**
```
[24(40005(40012(h'7b33b86e604e3cb5ef9d1675d59c70b6ea7d1f625d062e4d14c4310f2e616cd9'))),
 {101: [24(h'59f2293a5bce7d4de59e71b4207ac5d2'),
        {1: 200},
        {508: 24(40308({1: "wpkh(@0)",
                        2: [40303({3: h'03e322bcd189700ab529866162ee0e326ec6f89b8d6d31cf26620ab4c3755e3fc2',                            
                                   4: h'60469faf4350f9bd1ed01c81a3c4ce7a3cd9e4e6c5622ea6c2bed47ebd0d7278',
                                   6: 40304({1: [84, true, 0, true, 0, true],
                                             2: 1615565810}),
                                   8: 4207047373})]}))},
        {11: 24("Dark Purple Peck Vial")}]}]
```

## Key Request

### Key Derivation Request

## PSBT
