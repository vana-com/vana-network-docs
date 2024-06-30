---
description: Store private data off-chain while permissioning it onchain
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

# Collective Servers

## Off-Chain Storage and OnChain Permissioning

How can we ensure private data is stored off-chain while managing permissions onchain?

Depending on a DLPs tokenomics, they may want to hold user data in escrow. Other DLPs may use liveness checks and rewards to ensure that user data remains connected, even without holding an encrypted copy of it.&#x20;

## Secure Data Contribution and Encryption

For DLPs and other user-owned data apps that require access to a collective dataset or model weights, Vana users a secured compute node with asymmetric encryption. Users contribute their data by encrypting it client-side with the node's public key. It is decrypted with the corresponding private key held securely on the node.

## Code Approval and Community Governance

The trusted compute node can only run code that is approved by the collective. With a community-owned dataset, for example, for a company to pay for access to train on the data, the company (or someone on their behalf) puts up a pull request with the code that they need to run on the secure node. This could include code to transmit the data to them, or code to train the model. Note the trusted compute node does not have access to a GPU, so to train larger models, the data requester must setup a secure compute node that that its own private key, then request that an encrypted copy is sent to that heavy compute node. Then, the data requester submits a proposal to the DAO describing what they would like to do.

If the DAO approves the proposal (and code), the pull request is merged and deployed to the node. [Here](https://github.com/vana-com/rdatadao-executor) is the code running on the node. However, this still requires trusting that the node operator(s) will adhere to the approved code and not introduce any vulnerabilities.

## Ongoing developments <a href="#ongoing-developments" id="ongoing-developments"></a>

Our current approach is a step towards decentralization, but still relies on trust in the compute node and code approval process. If the node operator, which at this point is only Vana, were to deploy malicious code to the server, or otherwise compromise the private key that can decrypt the data, then the node operator would be able to access the underlying data.

We are eager to add more secure and decentralized options as fully homomorphic encryption, distributed training, and other privacy-preserving technologies mature. We looked at implementing ways to reduce the trust required by splitting model weights or splitting the dataset across many machines in a way that preserves privacy, but have not found a satisfactory solution, so rely on a trusted compute node today. For example, [petals.dev](https://petals.dev/) is doing great work letting many users load a small part of the model for distributed inference.

[\
](https://docs.vana.com/network/personal-servers/run-your-personal-server/hosted-app)
