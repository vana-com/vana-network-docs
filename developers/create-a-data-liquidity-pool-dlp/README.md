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

# Create a Data Liquidity Pool (DLP)

Creating a DLP is the best way for highly motivated builders to get involved and rewarded. It takes a few hours to deploy a template, and 1-2 days to modify the template for your chosen data source.

## Getting Started

The Data Liquidity Layer is where data is contributed, validated, and recorded to the network into data liquidity pools (DLPs). Here, DLP creators deploy DLP smart contracts with specific data contribution objectives, including the DLP’s purpose, validation method, and data contribution parameters.&#x20;

The top DLPs earn data liquidity pool rewards, so DLP slots are competitive. There are 16 slots available on mainnet. This limit is intended to incentivize quality over quantity.

* To register your DLP or provide updates to be added to the leaderboard, submit [here](https://usevana.typeform.com/to/lYvFKKYY).
* To see other DLPs, view the [dlp-leaderboard.md](../../welcome-to-vana/dlp-leaderboard.md "mention")

{% hint style="info" %}
Join our [Discord](https://discord.com/invite/Wv2vtBazMR) server to present your DLP and chat with other devs creating DLPs
{% endhint %}

## Understanding DLPs

A data liquidity pool consists of the following components:

1. A DLP smart contract that issues rewards and communicates back to the [connectome](../../core-concepts/network-overview/connectome.md).&#x20;
2. A proof-of-contribution function to measure data quality. This can be run by the [Satya validators](satya-validators.md).
3. An optional UI for data contributors to add data to a liquidity pool.

### Validators

A validator runs a proof-of-contribution function that measures data quality. There are two kinds of Validators that DLPs can use: [Satya Validators](satya-validators.md) (recommended) and [DLP Validators](dlp-validators/).&#x20;

Validators use of the `vana` framework to interact with all the components of the Vana network. A starting point can be found here:

{% hint style="info" %}
Vana framework with core components: [https://github.com/vana-com/vana-framework](https://github.com/vana-com/vana-framework/)
{% endhint %}

### Proof of contribution

Data value and validation depends on the data source. DLPs have the flexibility to validate data according to their unique requirements. Regardless of the specific verification methods employed, a DLP should strive to ensure that each data point passes the following criteria, which is implemented through a proof-of-contribution function:

* **Meaningfulness**: The data should contribute novel and valuable insights to the DLP's overall dataset. It should enhance the richness and diversity of the available information.
* **Validity**: The data must adhere to a schema that is consistent with the existing data within the DLP. Conforming to a standardized structure ensures compatibility and facilitates efficient data processing.
* **Authenticity and Contributor's rights**: The data must be genuine and, if required, originate from a legitimate account. This ensures the integrity and reliability of the information. The data contributor submitting the data must have the necessary rights and permissions to do so.

This proof-of-contribution function checks data validity and maps the diverse data submissions to a score that can be used to reward fungible DLP-specific tokens.&#x20;

{% hint style="info" %}
See the ChatGPT DLP for a [detailed example of proof-of-contribution](https://github.com/vana-com/vana-dlp-chatgpt/blob/main/docs/proof\_of\_contribution.md)
{% endhint %}

{% hint style="info" %}
If using Satya validators, use this [proof-of-contribution template](https://github.com/vana-com/vana-satya-proof-template/) as a starting point.
{% endhint %}

### DLP Smart Contract

A DLP smart contract is responsible for rewarding data contributors DLP-specific tokens for their data. After proof-of-contribution is run, a score from 0-1 is given to the file, which can be used to determine how valuable the data is, and convert that to DLP-specific tokens (example: $TDAT for Twitter data).&#x20;

The template below can be used, swapping out the DLP token to something specific to your DLP (example: $TDAT for Twitter data).&#x20;

{% hint style="info" %}
[https://github.com/vana-com/vana-dlp-smart-contracts](https://github.com/vana-com/vana-dlp-smart-contracts)
{% endhint %}

#### DLP Tokens

The Smart Contract repo contains a [DLPT (DLP Token) contract](https://github.com/vana-com/vana-dlp-smart-contracts?tab=readme-ov-file#dlpt-contract), that is an ERC20 token with additional features such as minting permissions, an admin role, and a blocklist for addresses. It leverages OpenZeppelin's ERC20, ERC20Permit, ERC20Votes, and Ownable modules for extended functionality.

### DLP Upload UI

Some DLPs use a UI for data contributors to upload their data to a DLP. It's up to the DLP to decide what is best for the DLP's contributors to be able to write data transactions onchain. A starting point for a UI, which implements client-side encryption, is here:

{% hint style="info" %}
Generic UI for uploading data to DLPs: [https://github.com/vana-com/vana-dlp-ui](https://github.com/vana-com/vana-dlp-ui)\
gpt data dao: [https://www.gptdatadao.org/](https://www.gptdatadao.org/)\
reddit data dao: [https://rdatadao.org/](https://rdatadao.org/)
{% endhint %}

Other DLPs are using Chrome extensions or scrapers for users to contribute data.

## How to start a DLP

Now that you're familiar with the components of a DLP, here's a conceptual step-by-step guide to launch a DLP of your own.

{% hint style="info" %}
Follow the [ChatGPT DLP tutorial](https://github.com/vana-com/vana-dlp-chatgpt/blob/main/docs/running\_on\_testnet.md) for a step-by-step guide on creating a DLP
{% endhint %}

1. Choose a valuable data source.
   * Current community requests: stack overflow, telegram, youtube, email, google drive
   * To see what others are building, visit the [dlp-leaderboard.md](../../welcome-to-vana/dlp-leaderboard.md "mention")
2. Tell users how to access that data source.
   * For example, through a GDPR or CCPA data export request, through scraping their own data, or through an API.&#x20;
   * Optionally, build an UI that makes it easy for data contributors to add their data via your smart contract.
3. Build a UI, CLI tool, browser extension, mobile app, etc to allow data contributors to upload data to the network.&#x20;
4. Implement a [Proof-of-Contribution function](https://github.com/vana-com/vana-satya-proof-template/) to validate and value data.
   * Data validation and value depends on the data source.
   * Once decided, implement your incentives and validation checks.
   * We recommend rolling this out iteratively in phases to test the incentives.
5. Register your DLP with the [Root Network](../smart-contracts.md#root-network-contract). This requires meeting a minimum staking threshold.&#x20;
6. Deploy your DLP smart contract and DLP Token contract.
7. Congrats, you're up and running!
8. To qualify for block rewards, get voted into the top 16 DLP slots based on data value and participation.

{% hint style="warning" %}
**Vana Testnet is for Testing Purposes Only**

Ensure you create a different configuration for data validation on testnet versus mainnet. Data privacy cannot be guaranteed in testnet.&#x20;
{% endhint %}

### Register Your DLP

Once a DLP Smart Contract is deployed to the Vana network, reach out to us and we will register this contract as a DLP. We will be manually approving DLP registration at the beginning of the testnet before moving to voting-based approval.

A DLP Smart contract will be able to accept new nodes into the DLP. To register a new node, create a wallet for it and call the registration function in the DLP smart contract. More information can be found in [become-a-dlp-validator.md](dlp-validators/become-a-dlp-validator.md "mention").&#x20;
