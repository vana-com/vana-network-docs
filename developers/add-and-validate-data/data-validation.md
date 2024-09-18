# Data Validation

Vana uses a [proof-of-contribution](../../core-concepts/key-elements/proof-of-contribution/ "mention")system to validate data submitted to the network. "Valid" means something different in each DLP, because different DLPs value data differently.

## Running Proof-of-Contribution in the Satya Network

The recommended way of validating data securely in the Vana Network is by using the Satya Network, a group of highly confidential nodes that run on special hardware. At a high level, the data contributor adds unverified data, and requests a proof-of-contribution job from the [satya-validators.md](../create-a-data-liquidity-pool-dlp/satya-validators.md "mention") (and pay a small fee to have their data validated). Once validated, the Satya validator will write the proof on chain.

## Proof-of-Contribution Template

To run PoC in the Satya Network, a DLP builder must implement a simple proof-of-contribution function using this template.

{% hint style="info" %}
PoC Template: [https://github.com/vana-com/vana-satya-proof-template](https://github.com/vana-com/vana-satya-proof-template)
{% endhint %}

The diagram below explains how this PoC template works.&#x20;

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption><p>Proof-of-contribution running in a Satya node</p></figcaption></figure>

1. The data contributor adds their encrypted data onchain, via the [Data Registry](../smart-contracts.md#data-registry-contract).
2. They request a validation job, paying a small fee. Once a Satya node is available to run the job, they connect directly to the node, and send them the encryption key and the proof-of-contribution docker image that needs to run on the data to validate it.
3. The Satya node receives the key, and downloads the encrypted file, and decrypts it
4. The Satya node places the decrypted file in a temporary, shielded\* location. The node operator cannot see the contents of this location.
5. The Satya node downloads and initializes a docker container to run the specified proof-of-contribution, and mounts the input and output volumes. The PoC container will have access to the decrypted file.
6. The PoC container runs its validations on the decrypted data, and outputs the attestation. More information on data attestation can be found here: [data-attestation.md](data-attestation.md "mention").
7. The Satya node reads the output, and generates the proof.
8. The Satya node writes the proof onchain, and claims the fee as a reward for completing that work.

{% hint style="info" %}
\* A [Gramine shielded container](https://gramine.readthedocs.io/projects/gsc/en/latest/) is a specialized type of container that leverages the Gramine library OS to run applications in a secure, isolated environment, typically utilizing hardware-based trusted execution environments (TEEs) like Intel SGX.
{% endhint %}

## Satya Network Integration

{% hint style="warning" %}
More information on integrating with the Satya network for data validation is coming soon.
{% endhint %}

