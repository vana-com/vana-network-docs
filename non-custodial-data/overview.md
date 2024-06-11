---
description: Vana makes data non-custodial by running operations in a personal server
---

# Overview

Vana uses a personal server architecture to allow users and data collectives to store private information off-chain. You may be familiar with this architecture through [Solid Project](https://solidproject.org/). The basic idea is that you have some off-chain compute environment where you can execute code that works with private data. You can think of this as a safe little home to execute code that requires your private data, and follows the data permissions rules you have laid out.

There is no expectation that every user runs their own personal server - it is simply a secure environment where you can work with private data. It can be secure because it's on your macbook, or secure because you trust the third party provider, similar to Infura for ethereum. You can also just use someone's browser as a lightweight personal server, [generating proofs](https://zk-proof-poc.vercel.vana.com/) or encrypting data client-side so it is fully secured as soon as it leaves their device.&#x20;

Personal servers exist for users and for collectives. For example, I have a personal server that runs on my Macbook. It has all of my private platform data - my messages, my journal entries, my emails, my writing - and allows me to run personalized inference on the macbook and return the output to a third party application without the data leaving my machine.

Personal servers follow a set of rules set out in a data permissions smart contract. As a simple example, [here](https://github.com/vana-com/vana-protocol-contracts/blob/main/contracts/Whitelist.sol) is a data permissions contract with a whitelist.



[\
](https://docs.vana.com/network/introduction/motivating-use-cases)
