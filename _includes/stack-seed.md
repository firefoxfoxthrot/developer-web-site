_Seeds have long been a focus of Blockchain Commons. They can be stored in one of two ways: as simple text-based URs, or as more descriptive Envelopes._

* **Seeds.** Seeds are the foundation of digital-asset security, as they're used to generate signing keys and auth keys, often in a hierarchical manner. URs allow the encoding of seeds as `ur:seed`, but Envelopes are now preferred because they can store metadata and also allow for encryption or elision. Blockchain Commons' [seedtool-cli-rust](https://github.com/BlockchainCommons/seedtool-cli-rust) and [Seedtool for iOS](https://github.com/BlockchainCommons/GordianSeedTool-iOS) offer best practices for the management of seeds.

* **SSKR.** Sharded Secret Key Reconstruction (SSKR) allows a seed to be sharded into individual shares. The seed can then be reconstructed from `m` of `n` of those shares where `m ≤ n`. Currently, this is done using a variant of Shamir's Secret Sharing with expansions for two-level shares. URs allow the encoding of SSKR shares as `ur:sskr` (though Envelopes are now preferred).
   * See our [SSKR page](/sskr/).

### Seeds' <font color="#2df775">OIB</font> Layer

_It's important to be able to identify a seed, no matter how it's stored or transmitted._

* **Object Identity Block (OIB).** The OIB suggests best practices for organizing and displaying data that can help users  toidentify seeds. An OIB includes an icon, a name, abbreviated digest, and Lifehashes.
   * See our [OIB page](/oib/)

* **LifeHash.** The LifeHash is a graphical element in an OIB. It creates a visual hash of a seed that should be distinct and relatively unique.
   * See our [LifeHash page](/lifehash/)
