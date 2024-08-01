_The CBOR layer defines the deterministic binary data serialization format for the Gordian Stack._

* **CBOR.** The heart of Gordian's data format is CBOR, a data format defined by [IETF RFC 8949](https://cbor.io/spec.html). It supports the _organized_ and _tagged_ formatting of data.
   * See [Why CBOR?](https://www.blockchaincommons.com/introduction/Why-CBOR/)

* **CDE.** Determinism is a requirement for the Gordian Stack. It was loosely described in RFC 8949, but needed further detailing. Blockchain Commons' work with CBOR led to one of CBOR's original authors further describing how CBOR could be used deterministically in the [CBOR Common Deterministic Encoding (CDE) Internet-Draft](https://datatracker.ietf.org/doc/draft-ietf-cbor-cde/).

* **dCBOR.** CDE allows for the creation of application profiles, which lay out specific rules for deterministic encoding. [dCBOR](https://datatracker.ietf.org/doc/draft-mcnally-deterministic-cbor/) is Blockchain Common's CDE application profile used by Gordian Envelope. To support Envelope, it includes specific rules for things such as numeric encoding.
   * See our [dCBOR page](/dcbor/).
