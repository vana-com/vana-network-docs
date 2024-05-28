---
description: >-
  The Vana network provides building blocks that can be used to create a data
  liquidity pool tailored for collecting any kind of meaningful data.
---

# Building Blocks

### Data Liquidity Pools

A Data Liquidity Pool (DLP) aims to aggregate similar data assets. Validators who uphold the integrity of this pool are responsible for evaluating the data for its usefulness and validity. Data comes in all shapes and sizes, so DLPs have a lot of freedom to operate in a way that makes sense for the data specific to that pool.

### Root Network

The root network is responsible for governing the DLPs in the network. DLP owners must register their DLP with the root network before it's considered active on the network. The root network also distributes rewards to the DLPs.

### DLP Smart Contract

Each DLP owner is responsible for deploying a smart contract specific to the DLP's needs. We provide contract templates that offer a starting point for registering DLP validators, recording and verifying data transactions written onchain, and validators reaching consensus through Nagoya consensus.

<figure><img src="../.gitbook/assets/Vana Docs Graphics.jpg" alt="" width="375"><figcaption><p>Nodes running within a DLP</p></figcaption></figure>

### Nodes

A node at the basic level is a network participant responsible for validating, querying, scoring, or performing any arbitrary task necessary for the DLP to perform proof-of-contribution. A node can be a _validator_ tasked with ensuring a data point belongs to the data contributor and is not fraudulent. A node can also be a _miner_ responsible for aggregating data points to respond to a data query. A DLP is responsible for defining who the DLP participants are, and how they're incentivized for good behavior and penalized for bad.&#x20;

#### Communication Between Nodes

Nodes can communicate with each other by encapsulating information in a Message object, and sending that object back and forth using a client-server relationship over HTTP.

#### NodeClient

A NodeClient is responsible for building the inputs of a Message object, and sending it to one or more NodeServers.&#x20;

#### NodeServer

The NodeServer runs a [FastAPI](https://fastapi.tiangolo.com/) server that is responsible for responding to API requests sent from a NodeClient. It will perform a task, then fill the outputs of the Message object and send it back to the NodeClient that requested it.

#### Messages

The Messages object is sent back and forth between nodes, providing a vehicle for communication between nodes. It wraps the inputs and outputs of a communication exchange sent between nodes.

### State

The state contains information about the current state of the DLP, including nodes in the network (and how they can be reached), scores of the nodes, when it was last synced, current block number, etc.&#x20;

### Chain Manager

This object encapsulates interactions with the blockchain.&#x20;
