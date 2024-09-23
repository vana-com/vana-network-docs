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

# L1 Validators

L1 Validators are essential for ensuring the composability and security of the Vana Proof-of-Stake (PoS) network.

## **Responsibilities**

* Consolidate and write data transactions onto the Connectome
* Verify the validity of network transactions.
* Maintain network state liveness through accurate and timely block creation.

L1 validators earn transaction fees and block rewards in the form of [VANA](broken-reference) for processing network transactions and finalizing blocks.

{% hint style="info" %}
L1 validators are only available on the Moksha testnet, which is the first to use Proof-of-Stake (PoS) consensus.
{% endhint %}

## Hardware requirements[​](https://docs.roninchain.com/validators/setup/overview#hardware-requirements) <a href="#hardware-requirements" id="hardware-requirements"></a>

To run a reliable, performant node, we suggest that the node’s hardware profile should match or exceed the following specifications:

### Vana Mainnet[​](https://docs.roninchain.com/validators/setup/overview#ronin-mainnet) <a href="#ronin-mainnet" id="ronin-mainnet"></a>

* 8-core CPU
* 32 GB RAM
* 1.2 TB high-speed SSD
* x86-64 architecture

### Testnet[​](https://docs.roninchain.com/validators/setup/overview#saigon-testnet) <a href="#saigon-testnet" id="saigon-testnet"></a>

* 2-core CPU
* 8 GB RAM
* 100 GB high-speed SSD
* x86-64 architecture

These hardware requirements are rough guidelines, and each node operator should monitor their node to ensure good performance for the intended task.

## Running a L1 validator

The guide for running L1 validators is available on our [GitHub](https://github.com/vana-com/vana) repository.

{% hint style="info" %}
Please note that this guide is under active development and may be updated in the future.
{% endhint %}
