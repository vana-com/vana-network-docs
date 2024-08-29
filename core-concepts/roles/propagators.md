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

# Propagators

Propagators are essential for ensuring the composability and security of the network.

## **Responsibilities**

* Consolidate and write data transactions onto the Connectome
* Verify the validity of network transactions.
* Maintain network state liveness through accurate and timely block creation.

Propagators earn transaction fees and block rewards in the form of [VANA](../../undefined/key-terms.md#vana-token-usdvana) for processing network transactions and finalizing blocks.

{% hint style="warning" %}
Satori testnet is currently run as Proof-of-Authority (PoA) chain for now. More information will be shared, as the testnet progresses. Please join our [Discord](https://discord.com/invite/Wv2vtBazMR) for more information.

The testnet will be upgraded to proof-of-stake for propagators to ensure Satori testnet remains stable for data liquidity pools.
{% endhint %}

## Hardware requirements[​](https://docs.roninchain.com/validators/setup/overview#hardware-requirements) <a href="#hardware-requirements" id="hardware-requirements"></a>

To run a reliable, performant node, we suggest that the node’s hardware profile should match or exceed the following specifications:

### Vana Mainnet[​](https://docs.roninchain.com/validators/setup/overview#ronin-mainnet) <a href="#ronin-mainnet" id="ronin-mainnet"></a>

* 8-core CPU
* 32 GB RAM
* 1.2 TB high-speed SSD
* x86-64 architecture

### Satori testnet[​](https://docs.roninchain.com/validators/setup/overview#saigon-testnet) <a href="#saigon-testnet" id="saigon-testnet"></a>

* 2-core CPU
* 8 GB RAM
* 100 GB high-speed SSD
* x86-64 architecture

These hardware requirements are rough guidelines, and each node operator should monitor their node to ensure good performance for the intended task.

## Running a Propagator

{% hint style="info" %}
We will release more information on how to run a propagator node soon.
{% endhint %}
