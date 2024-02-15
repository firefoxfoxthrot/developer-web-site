---
cover: false
header:
  overlay_color: "#000"
  overlay_filter: "0.25"
  overlay_image: /assets/images/dev-data-background.jpg
  og_image: /assets/images/bc-card.jpg
title: "Envelope Request & Response"
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

* **NC Request:** Seed Digest
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
«100» [
        ❰200❱: Digest(ffa11a8b)
]
```

The numbers refer to specific functions and specific parameters. They are defined in [Format.swift](https://github.com/BlockchainCommons/BCSwiftEnvelope/blob/master/Sources/Envelope/Base/Format.swift) in the [Envelope base code](https://github.com/BlockchainCommons/BCSwiftEnvelope/tree/master/Sources/Envelope/Base). The function call is tagged with CBOR tag #40006, which defines it as a `ur:function` and the parameter is defined with CBOR tag #40007, which defines it as a `ur:function`. That's what the "«»" and "❰❱" represent.

The functions are as follows:

| # | Function |
|---|----------|
| 100 | getSeed |
| 101 | getKey |
| 102 | signPSBT |
| 103 | getOutputDescriptor |

The parameters are as follows:

| # | Parameter |
|----|----------|
| 200 | seedDigest |
| 201 | derivationPath |
| 202 | isPrivate |
| 203 | useInfo |
| 204 | isDerivable |
| 205 | psbt |
| 206 | name |
| 207 | challenge |

These are essentially "known values" for functions and their parameters, meaning that we maintain the values internally at Blockchain Commons. 

The above function to retrieve a seed thus parses as follows:

```
«getSeed» [
        ❰seedDigest❱: Digest(ffa11a8b)
]
```

In other words, please send me a seed that matches the digest `ffa11a8b...`

### Responses to Function Requests

Though functions are used to generate requests, the response is just a standard Envelope. Here's an example of a response to the `«getSeed»` function for `ffa11a8b`.

```
Bytes(16) [
        'isA': 'Seed'
        'hasName': "Dark Purple Peck Vial"
        'outputDescriptor': output-descriptor(Map)
]
```

The subject is the seed, while the three assertions describe the seed. If you look at the CBOR, you'd seed that the subjects of those assertions are actually [known values](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2023-002-known-value.md). The actual CBOR looks more like this:
```
Bytes(16) [
        1: 200
        11: "Dark Purple Peck Vial"
        507: output-descriptor(Map)
]
```
The output descriptor also has a map structure as described in [BCR-2023-010](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2023-010-output-descriptor.md).

## Wrapping Up Request & Response: GSTP

In order to identify a request function as a request requires wrapping it with a `ur:request` subject. This is done using the methodology of [Gordian Secure Transport Protocol (GSTP)](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2023-014-gstp.md). 

(Note that the overall GSTP protocol includes encryption & signature steps, which are certainly best practices for requests and responses, but not required. The following describes only the request and reponses envelopes, which are enclosed in GSTP communications and which can be standalone in other uses of `request` and `response`.)

1. Generate an ["Apparently Random Identifier"](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2022-002-arid.md).
2. Tag it as `ur:arid` (CBOR tag #40012).
3. Tag that as `request` (CBOR tag #40004).

`envelope-cli` will display a Request subject as follows:
```
request(ARID(7b33b86e))
```
The actual CBOR looks like this:
```
40004(40012(
     h'7b33b86e604e3cb5ef9d1675d59c70b6ea7d1f625d062e4d14c4310f2e616cd9'
))
```
It then contains the functional request in an assertion called `body` (known value #100). This is what identifies its subenvelope as a function call. Other assertions may contain a `note` about the request (known value #4) or other info.

Putting that all together, here's a complete `request` containing the `«getSeed»` function call shown above:

```
request(ARID(7b33b86e)) [
    100: «100» [
        ❰200❱: Digest(ffa11a8b)
    ]
    4: "Alias quam ullam qui reprehenderit ad quibusdam in hic occaecati aut ut voluptas dicta eligendi nobis. Molestiae neque voluptatibus et dolor qui quas?"
]
```

Here it is with all the known values and function values filled in:

```
request(ARID(7b33b86e)) [
    'body': «getSeed» [
        ❰seedDigest❱: Digest(ffa11a8b)
    ]
    'note': "Alias quam ullam qui reprehenderit ad quibusdam in hic occaecati aut ut voluptas dicta eligendi nobis. Molestiae neque voluptatibus et dolor qui quas?"
]
```

Going in the other direction, here's what the CBOR looks like (with explanations):
```
/* Array of 3 */

[
 
 /* #1: request(ARID(7b33b86e)) */

     /* CBOR tag #24 = byte string */
     /* CBOR tag #40004 = request */
     /* CBOR tag #40012 = ur:arid */
 
 24(40004(40012(
     h'7b33b86e604e3cb5ef9d1675d59c70b6ea7d1f625d062e4d14c4310f2e616cd9'
   ))), 

 
  /* #2: note */
  
     /* map */
     /* Known Value #4 = note */
     /* CBOR tag #24 = byte string */
  
 {4: 24("Alias quam ullam qui reprehenderit ad quibusdam in hic occaecati aut ut voluptas dicta eligendi nobis. Molestiae neque voluptatibus et dolor qui quas?")}, 
 
 /* #3: 'body': «getSeed» */
 
     /* map */
     /* Known Value #100 = body */
     
     /* array of 2 */
       
       /* CBOR tag #24 = bytestring */
       /* CBOR tag #40006 = ur:function */
       /* Function #100 = getSeed */
       
       /* CBOR tag #24 = bytestring */
       /* CBOR tag #40007 = ur:parameter */
       /* Parameter #200 = seedDigest */
       
       /* CBOR tag #24 = bytestring */
       /* CBOR tag #40001 = ur:digest */
       
 {100: [
        24(40006(100)), 
        {24(40007(200)): 24(40001(
          h'ffa11a8b90954fc89ae625779ca11b8f0227573a2f8b4ed85d96ddf901a72cea'
        ))}
       ]
     }

]
```
### Responses to GSTP Requests

To respond to a GSTP request:

1. Use the _same_ ARID as the subject.
2. Tag it as `ur:arid` (CBOR tag #40012).
3. Tag that as `request` (CBOR tag #40004).
4. Create an object that's an assertion with a 'result' subject (Known Value #101) and then insert the envelope that's the response the functional request as the object.

The response to the above request thus look as follows:

```
response(ARID(7b33b86e)) [
    101: Bytes(16) [
        1: 200
        11: "Dark Purple Peck Vial"
        507: output-descriptor(Map)
    ]
]
```

Or:
```
response(ARID(7b33b86e)) [
    'result': Bytes(16) [
        'isA': 'Seed'
        'hasName': "Dark Purple Peck Vial"
        'outputDescriptor': output-descriptor(Map)
    ]
]
```

### Putting It Together

Here's the complete `request` and `response`

```
request(ARID(7b33b86e)) [
    'body': «getSeed» [
        ❰seedDigest❱: Digest(ffa11a8b)
    ]
    'note': "Alias quam ullam qui reprehenderit ad quibusdam in hic occaecati aut ut voluptas dicta eligendi nobis. Molestiae neque voluptatibus et dolor qui quas?"
]
```

```
response(ARID(7b33b86e)) [
    'result': Bytes(16) [
        'isA': 'Seed'
        'hasName': "Dark Purple Peck Vial"
        'outputDescriptor': output-descriptor(Map)
    ]
]
```

Complete test vectors can be found at [Envelope Request & Response Test Vectors]

## Best Practices for Request & Response

- user involvement
- OIB

- UX should support helping users should confirm separate things, separately. For instance, Confirm lifehash and check digits correct is one decision, continue to return request is a second. Especially important when the “choices” are divergent.

Mental model of “is this what you expected” is different than “is this what you want to take the risk of doing”

Thus don’t conflate the decision.

Each switch of mental model needs to be care. It it for some reason requires five separate mental models to make a decision (god forbid) than you really need 5 choices.


