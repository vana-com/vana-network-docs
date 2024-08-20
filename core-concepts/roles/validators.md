---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Validators

Validators are critical for maintaining the integrity, value, and trustworthiness of data within the network. Depending on the DLP's architecture, different validators may be required.

* [TEE Validators](../../developers/create-a-data-liquidity-pool-dlp/tee-validators.md) - the recommended approach, a group of confidential validators that can perform validation for any DLP
* [DLP Validators](../../developers/create-a-data-liquidity-pool-dlp/dlp-validators/) - a group of validators specific to a DLP, useful when TEE validators cannot be used
* No Validators - some DLPs may not require validators at all

## Choosing the right Validator for your DLP

For most DLPs, TEE Validators are the way to go. They offer a simpler DLP architecture, one where DLPs focus on building out their proof-of-contribution. TEE Validators are DLP agnostic and can run PoC from any DLP.&#x20;

In specific instances, when running PoC is not possible within the limits of the TEE Validators, a DLP can opt to deploy its own network of DLP validators.&#x20;

Some DLPs may not require validators; for example, a DLP that generates the proof-of-contribution entirely on the client side using [ZK Proofs](../key-elements/proof-of-contribution/zero-knowledge-proof-of-contribution.md).
