<i>The UR layer encodes structured CBOR binary data into plain text strings. It's a method for sending plain-text strings or for efficiently encoding data into QRs. It's used by Envelopes, Animated QRs, and other higher level capabilities.</I><img src="https://developer.blockchaincommons.com/assets/images/bc-stack-ux-2.png" style="margin-left: 20px; float: right" width="25%">

* **Bytewords.** The foundation of URs are ByteWords, which are a set of 256 carefully chosen words which each translate a byte (from `0x00` to `0xff`) into a four-letter English word. A four-word checksum for data then improves resilience.
  * See our [Bytewords page](/bytewords/)

* **Uniform Resources (URs).** Bytewords can be reduced in size by using the "minimal" form, which uses only the first and last letter of each word, which are always unique. URs therefore convert CBOR binary data into well-formed URIs by converting the data into minimal Bytewords and then preceding it with a `ur:` string followed by an appropriate tag for the data type. The result is self-identifying and transport-independent.
   * See our [UR page](/ur/)

* **Multipart UR (MURs).** URs include support for multipart URs, which divide and sequence UR data and which can be used with fountain codes to transmit the data even if a channel is unreliable.
   * See our [MUR  Implementation Guide](https://github.com/BlockchainCommons/Research/blob/master/papers/bcr-2024-001-multipart-ur.md)

### UR's <font color="#17c3ff">Animated QRs</font>

<i>URs are formatted as a plain-text URIs, but they're optimized to allow efficient encoding as QR codes.</I><img src="https://developer.blockchaincommons.com/assets/images/bc-stack-ux-3.png" style="margin-left: 20px; float: right" width="25%">

* **Animated QRs.** MURs are the foundation of Animated QRs, a method for transmitting data across an [airgap](/airgap/) when that data would be too large for a standard QR code. MURs' fountain codes allow for individual frames to be missed without requiring all the frames to be resent. Due to Animated QR's application for signing PSBTs over airgaps, they've become one of Blockchain Commons' most successful releases.
   * See our [Animated QRs page](/animated-qrs/)
