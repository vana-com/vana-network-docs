# Data Ingress

{% embed url="https://www.loom.com/share/e4508aae3dfb4af7997204f5f327107d?sid=d17cddcc-8579-4d47-a51c-f0b2c366d6a8" %}

Anyone can add data to the Vana network. However, for a data point to be considered "valid", it must run through [proof-of-contribution](../key-elements/proof-of-contribution/ "mention")to ensure its validity. This process outputs a public attestation that can be attached to an encrypted data point, allowing anyone to judge how valuable a data point is without needing to decrypt it.

At a high level, these are the steps:

1. A [Data Liquidity Pool](broken-reference) will provide a UI for its [data contributors](broken-reference) to add data (a webapp, browser extension, CLI tool, etc).
2. The data contributor will [encrypt](data-privacy.md) and upload the data to a storage location of the DLP's choosing.
3. The DLP will specify a Proof-of-Contribution function to run on the data. If using the [Satya network](data-validation.md) to run PoC, it will coordinate with a Satya node to generate this attestation.
4. The attestation is recorded onchain, and the data contributor is rewarded for their contributions.

Read through this section's subpages to learn more about how each step works.
