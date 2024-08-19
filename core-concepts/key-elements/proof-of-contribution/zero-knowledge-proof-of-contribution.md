# Zero-Knowledge Proof of Contribution

## What is a Zero Knowledge Proof?

A zero-knowledge proof (ZKP) is a cryptographic method by which one party (the prover) can prove to another party (the verifier) that they know a value without conveying any information apart from the fact that they know the value. This means the verifier learns nothing about the value itself, only that the prover knows it.

To protect the privacy of data contributions, a DLP can implement a Proof of Contribution using ZKP. When a Data Contributor or Custodian submits data to the DLP, they generate a zero-knowledge proof that verifies the authenticity and integrity of the data and its contribution to the DLP without revealing its full contents.

<figure><img src="../../../.gitbook/assets/image (3) (1).png" alt=""><figcaption><p>ZK Proofs as a Proof of Contribution</p></figcaption></figure>

## Example

To illustrate this example, imagine a DLP for ChatGPT data exports. The DLP considers a data point "valid" if the number of conversations inside the zip file exceeds 50. We can generate cryptographic proof that a file meets this requirement without revealing its contents (or even the exact number of conversations in the file).

To protect against tampering with the proof generation while maintaining privacy and ensuring the data doesn't leave the user's browser unencrypted, the proof is generated in a WebAssembly environment, which is much harder to tamper with than generating proofs in the browser in plain JavaScript.&#x20;

We provide an example here: [https://zk-proof-poc.vercel.vana.com/](https://zk-proof-poc.vercel.vana.com/)

The source code is available here: [https://github.com/vana-com/zk-proof-poc](https://github.com/vana-com/zk-proof-poc)
