---
description: Overview of DLP tokens
---

# Incentives

{% hint style="warning" %}
Incentives are subject to change and might be updated to account for necessary adjustments in the ecosystem.
{% endhint %}

### Core economics in dataset-specific token

* Each DLP configures the address of the currency it would like to use
* It is recommended that each DLP create their own dataset-specific token
* DLPs have full control over the tokenomics of their pool. Suggested implementations:
  * Validators stake pool tokens, top validators are elected
  * Contributors stake pool tokens or directly pay pool tokens to get their data validated by validators
  * Data consumption requests are paid in pool tokens, which are burned
* DLP tokens are used to collectively govern the actions of the DLP

{% hint style="info" %}
See the [r/datadao docs](https://docs.rdatadao.org/usdrdat-tokenomics) for an example of dataset-specific tokenomics
{% endhint %}

### Relationship between the native token and dataset-specific tokens

The Vana network does not own or control any of the dataset-specific tokens created within the DLPs. These tokens are managed and governed by the respective DLPs.

The native gas token facilitates transactions and computations across the entire network. It is used to pay gas fees for data transactions across all DLPs, reward propagators and contributors, and secure the network. Dataset-specific tokens, on the other hand, are used specifically within their respective DLPs to access and consume the data they represent.

### Block rewards for top pools

* Top 16 DLPs split X% of block rewards for the first X months, halving over each period
* New pools must prove themselves by running w/o block rewards for some time
* Governable incentive to recognize the value of data onboarding and verification to network



