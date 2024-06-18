---
description: >-
  Creating a DLP is the best way for highly motivated builders to get involved
  and rewarded. It takes a few hours to deploy a template, and 1-2 days to
  modify the template for your chosen data source.
---

# Create a Data Liquidity Pool (DLP)

## Getting Started

The Data Liquidity Layer is where data is contributed, validated, and recorded to the network into data liquidity pools (DLPs). Here, DLP creators deploy DLP smart contracts with specific data contribution objectives, including the DLP’s purpose, validation method, and data contribution parameters.

The top DLPs earn data liquidity pool rewards, so DLP slots are competitive. There 16 slots available on mainnet. This limit is intended to incentivize quality over quantity.

* To register your DLP or provide updates on progress, go [here](https://usevana.typeform.com/to/lYvFKKYY).
* To see other DLPs, view the [DLP Leaderboard](../../welcome-to-vana/dlp-leaderboard.md)

{% hint style="info" %}
Join our [Discord](https://discord.com/invite/Wv2vtBazMR) server to present your DLP and chat with other devs creating DLPs
{% endhint %}

## Understanding DLPs

A typical data liquidity pool consists of the following components:

1. A peer-to-peer network of validators running proof-of-contribution
2. A DLP smart contract that communicates back to the connectome&#x20;
3. An optional UI for data contributors to add data to a liquidity pool

### DLP Validators

A DLP validator can handle data specific to a data liquidity pool. It can make use of the `vana` framework that implements all the components of the Vana network. A starting point can be found here:&#x20;

{% hint style="info" %}
Vana framework with core components: [https://github.com/vana-com/vana-framework](https://github.com/vana-com/vana-framework/)

Template for creating DLP validators [https://github.com/vana-com/vana-dlp-template](https://github.com/vana-com/vana-dlp-template)

Data liquidity pool with simple zk proofs: [https://github.com/vana-com/zk-proof-poc](https://github.com/vana-com/zk-proof-poc)
{% endhint %}

### Proof of contribution

DLPs have the flexibility to validate data according to their unique requirements. Regardless of the specific verification methods employed, a DLP should strive to ensure that each data point passes the following criteria, which is implemented through a proof-of-contribution function:

* **Meaningfulness**: The data should contribute novel and valuable insights to the DLP's overall dataset. It should enhance the richness and diversity of the available information.
* **Validity**: The data must adhere to a schema that is consistent with the existing data within the DLP. Conforming to a standardized structure ensures compatibility and facilitates efficient data processing.
* **Authenticity and Contributor's rights**: The data must be genuine and, if required, originate from a legitimate account. This ensures the integrity and reliability of the information. The data contributor submitting the data must have the necessary rights and permissions to do so.&#x20;

This proof-of-contribution function checks data validity and maps the diverse data submissions to a score that can be used to reward fungible DLP-specific tokens.&#x20;

{% hint style="info" %}
See the ChatGPT DLP for a [detailed example of proof-of-contribution](https://github.com/vana-com/vana-dlp-chatgpt/blob/main/docs/proof\_of\_contribution.md)
{% endhint %}

### DLP Smart Contract

A DLP smart contract is responsible for recording consensus values among network nodes and can help orchestrate how proof-of-contribution works in the DLP. A starting point can be found here:

{% hint style="info" %}
[https://github.com/vana-com/vana-dlp-smart-contracts](https://github.com/vana-com/vana-dlp-smart-contracts)
{% endhint %}

#### DLP Tokens

The Smart Contract repo contains a [DLPT (DLP Token) contract](https://github.com/vana-com/vana-dlp-smart-contracts?tab=readme-ov-file#dlpt-contract), that is an ERC20 token with additional features such as minting permissions, an admin role, and a blocklist for addresses. It leverages OpenZeppelin's ERC20, ERC20Permit, ERC20Votes, and Ownable modules for extended functionality.

#### Validator registration

The [Data Liquidity Pool smart contract](https://github.com/vana-com/vana-dlp-smart-contracts?tab=readme-ov-file#data-liquidity-pool-smart-contract) is designed to manage the registration of validators. This contract ensures that validators can participate in maintaining the network's integrity and security while earning rewards for their contributions.

### DLP Upload UI

Some DLPs use a UI for data contributors to upload their data to a DLP. It's up to the DLP to decide what is best for the DLP's contributors to be able to write data transactions onchain. A starting point for a UI, which implements client-side encryption, is here:&#x20;

{% hint style="info" %}
Generic UI for uploading data to DLPs: [https://github.com/vana-com/vana-dlp-ui](https://github.com/vana-com/vana-dlp-ui)\
gpt data dao:  [https://www.gptdatadao.org/](https://www.gptdatadao.org/)\
reddit data dao: [https://rdatadao.org/](https://rdatadao.org/)
{% endhint %}

Other DLPs are using chrome extensions or scrapers for users to contribute data.

## How to start a DLP

Now that you're familiar with the components of a DLP, here's a conceptual step-by-step guide to launch a DLP of your own.

{% hint style="info" %}
Follow the [ChatGPT DLP tutorial](https://github.com/vana-com/vana-dlp-chatgpt/blob/main/docs/running\_on\_testnet.md) for a step-by-step guide on creating a DLP
{% endhint %}

1. Choose a valuable data source.
   * Current community requests: stack overflow, telegram, youtube, email, google drive
   * To see what others are building, visit the [DLP Leaderboard](../../welcome-to-vana/dlp-leaderboard.md)
2. Tell users how to access that data source.
   * For example, through a GDPR or CCPA data export request, through scraping their own data, or through an API.&#x20;
   * Optionally, build an UI that makes it easy for data contributors to add their data via your smart contract.
3. Implement a DLP validator template and smart contract that will validate and value data.
   * Data validation and value depends on the data source.
   * Once decided, implement your incentives and validation checks.
   * We recommend rolling this out iteratively in phases to test the incentives.
4. Register as a DLP creator. This requires meeting a minimum staking threshold.&#x20;
5. Deploy your DLP smart contract.
6. Start up a DLP validator and recruit other existing validators to participate in the DLP as well.
7. Congrats, you're up and running!
8. To qualify for block rewards, get voted into the top 16 DLP slots based on data value and participation.

{% hint style="warning" %}
**Satori Testnet is for Testing Purposes Only**

Ensure you create a different configuration for data validation on testnet versus mainnet.
{% endhint %}

### Deploy Validators

Once a DLP has been built, we are ready to deploy it. DLP nodes form a peer-to-peer network, and can be deployed to any infrastructure of your choice (ex, AWS, Google Cloud Platform, Azure, etc). Ideally, nodes have a static IP to more easily communicate with each other. Each node must have a wallet used to register the node to the DLP.

### Register Your DLP

Once a DLP Smart Contract is deployed to the Vana network, reach out to us and we will register this contract as a DLP. We will be manually approving DLP registration at the beginning of the testnet before moving to voting-based approval.&#x20;

### Deploy the Smart Contract

Clone the DLP smart contract from a [template](https://github.com/vana-com/vana-dlp-smart-contracts), modify it for the needs of your specific DLP, and deploy it to the network following the readme.

### Register a node to a DLP

A DLP Smart contract will be able to accept new nodes into the DLP. To register a new node, create a wallet for it and call the registration function in the DLP smart contract. More information can be found in [become-a-dlp-validator.md](become-a-dlp-validator.md "mention").&#x20;

### Deploy DLP Nodes

Once DLP nodes are registered, they must be deployed to a location where they can be reached by other DLP nodes. This can mean deploying to your favorite cloud vendor of choice or running a node on your own hardware and setting up appropriate networking rules. Once the node is running, they can begin serving proof-of-contribution requests within the DLP.
