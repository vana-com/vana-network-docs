---
hidden: true
---

# DLP Validators

DLPs may choose to rely on a network of DLP Validators to run their DLP's proof-of-contribution (PoC). After running PoC, these validators form a [consensus](../core-concepts/key-elements/proof-of-contribution/#nagoya-consensus) with each other and write the proof-of-contribution assessment back on-chain. In this model, DLPs are responsible for deploying and maintaining their validators. DLP Validators earn DLP token rewards for accurate and consistent data evaluations.

<figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption><p>A DLP that relies on DLP validators</p></figcaption></figure>

## **Responsibilities**

* Verify user data within DLPs according to standards set by DLP owners.
* Use Vana’s Proof-of-Contribution system to assess data legitimacy and value.
* Attest to the validity of the data and write the attestation back on-chain
* Participate in the Nagoya Consensus to ensure consistent and accurate data scoring.
* Perform accurate and consistent data evaluations and disincentivize bad actors through slashing.
* Evaluate the performance of other validators to maintain network integrity.
* Back evaluations with personal stake to ensure accuracy and reliability.
* Respond to queries from data consumers, including decrypting data and validating results.

## DLP Validator Components

Each DLP owner is responsible for deploying a smart contract specific to the DLP's needs. We provide contract templates that offer a starting point for registering DLP validators, recording and verifying data transactions written on-chain, and validators reaching consensus through [Nagoya consensus](https://colab.research.google.com/drive/19MUtnOTk1kXp18pCRGNBgMTOJhW-4TGK). We also provide a template implementation for the corresponding validators.

The provided templates include:

* A smart contract: [https://github.com/vana-com/vana-dlp-smart-contracts](https://github.com/vana-com/vana-dlp-smart-contracts)
* A sample validator node (transacts with contract): [https://github.com/vana-com/vana-dlp-hotdog](https://github.com/vana-com/vana-dlp-hotdog)
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

<figure><img src="../.gitbook/assets/Vana Docs Graphics.jpg" alt="" width="375"><figcaption><p>Nodes running within a DLP</p></figcaption></figure>

Nodes can communicate with each other by encapsulating information in a Message object, and sending that object back and forth using a client-server relationship over HTTP.

#### NodeClient

A NodeClient is responsible for building the inputs of a Message object, and sending it to one or more NodeServers.&#x20;

#### NodeServer

The NodeServer runs a [FastAPI](https://fastapi.tiangolo.com/) server that is responsible for responding to API requests sent from a NodeClient. It will perform a task, then fill the outputs of the Message object and send it back to the NodeClient that requested it.

#### Messages

The Messages object is sent back and forth between nodes, providing a vehicle for communication between nodes. It wraps the inputs and outputs of a communication exchange sent between nodes.

## Nagoya Consensus

> _Writer's note: We had to design a new consensus mechanism to handle the fuzziness of data contributions. For example, if I believe your data deserves a score of 100, and another validator believes your data deserves a score of 102, we could both be pretty much right. Neither of us as validators are acting maliciously or incorrectly. But generally crypto consensus mechanisms are designed for exact consensus only. Bittensor proposed an early version of this fuzzy consensus, which we have modified to work for private data and proof of contribution._&#x20;

To reach a state of agreement on data contributions and disincentivize malicious validators, the Proof-of-Contribution system employs Nagoya Consensus. In Nagoya Consensus, each DLP Validator expresses their perspective on the quality and value of data contributions as a rating. Validators then use their rating to score other validators through a set of ratings weighted by stake.

Nagoya Consensus rewards validators for producing data contribution scores that are in agreement with the evaluations of other validators. This disincentivizes divergence from the consensus majority while incentivizing validators to converge on honest assessments of data contribution.

By requiring validators to put stake behind their evaluations and rewarding convergence weighted by stake, Nagoya Consensus makes it economically unfavorable for even a significant minority of validators to collude and manipulate the state of the DLP. As long as an honest majority of stake-weighted validators participate, the system can come to consensus on data contribution scores that accurately reflect the quality and value of data in the DLP.
