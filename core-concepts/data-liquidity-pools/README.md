---
description: >-
  The Vana network provides building blocks that can be used to create a Data
  Liquidity Pool (DLP) tailored for collecting any kind of meaningful data.
---

# Data Liquidity Pools

## Root Network

The root network is responsible for governing the DLPs in the network. A DLP owner must register their DLP with the root network before it is considered active on the network. The root network distributes rewards to active DLPs.

## Data Liquidity Pools

Formally, a DLP is a smart contract registered with and approved by the root network.

DLPs must meet the root network's standard to be activated. To do so, each DLP onboards a class of data assets, creating liquidity, and guarantees that data is secure, ensuring privacy.

Typically, validators uphold the integrity of a DLP by evaluating the data for its usefulness and validity. Data comes in all shapes and sizes, so DLPs have a lot of freedom to operate in a way that best fits the data specific to that pool.

## DLP Templates

Each DLP owner is responsible for deploying a smart contract specific to the DLP's needs. We provide contract templates that offer a starting point for registering DLP validators, recording and verifying data transactions written on-chain, and validators reaching consensus through [Nagoya consensus](https://colab.research.google.com/drive/19MUtnOTk1kXp18pCRGNBgMTOJhW-4TGK). We also provide a template implementation for the corresponding validators.

<figure><img src="../../.gitbook/assets/Vana Docs Graphics.jpg" alt="" width="375"><figcaption><p>Nodes running within a DLP</p></figcaption></figure>

The provided templates include:

* A smart contract: [https://github.com/vana-com/vana-dlp-smart-contracts](https://github.com/vana-com/vana-dlp-smart-contracts)
* A validator network (transacts with contract): [https://github.com/vana-com/vana-dlp-template](https://github.com/vana-com/vana-dlp-template)
* The Vana framework (used by validators): [https://github.com/vana-com/vana-framework](https://github.com/vana-com/vana-framework)

## Vana Framework

The Vana Framework is a library designed to streamline the process of building a DLP.

### Chain Manager

This object encapsulates interactions with the blockchain.

### State

The state contains information about the current state of the DLP, including nodes in the network (and how they can be reached), scores of the nodes, when it was last synced, current block number, etc.&#x20;

### Nodes

The Vana framework provides a node abstraction that simplifies the creation and management of a peer-to-peer network that operates the DLP.

A node is a network participant responsible for validating, querying, scoring, or performing any arbitrary task necessary for the DLP to perform proof-of-contribution. A node can be a _validator_ tasked with ensuring a data point belongs to the data contributor and is not fraudulent. A node can also be a _miner_ responsible for aggregating data points to respond to a data query. A DLP is responsible for defining who the DLP participants are, and how they're incentivized for good behavior and penalized for bad.&#x20;

#### Communication Between Nodes

Nodes can communicate with each other by encapsulating information in a Message object, and sending that object back and forth using a client-server relationship over HTTP.

#### NodeClient

A NodeClient is responsible for building the inputs of a Message object, and sending it to one or more NodeServers.&#x20;

#### NodeServer

The NodeServer runs a [FastAPI](https://fastapi.tiangolo.com/) server that is responsible for responding to API requests sent from a NodeClient. It will perform a task, then fill the outputs of the Message object and send it back to the NodeClient that requested it.

#### Messages

The Messages object is sent back and forth between nodes, providing a vehicle for communication between nodes. It wraps the inputs and outputs of a communication exchange sent between nodes.

