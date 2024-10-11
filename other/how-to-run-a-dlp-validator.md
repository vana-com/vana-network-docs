---
description: Validate user data for specific Data Liquidity Pools
hidden: true
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

# How to run a DLP Validator?

Start to validate user data for specific Data Liquidity Pools.

{% hint style="info" %}
Please join our [Discord](https://discord.gg/withvana) to get an overview of all existing DLPs and how to access them.

If you need to meet specific minimum staking requirements for a DLP, please reach out to the community in our [#testnet-help](https://discord.com/channels/1239717483536187504/1243719189223571456) channel for support as well.
{% endhint %}

You can run a validator on your own hardware or on a cloud provider like GCP and AWS, ensuring the quality of data in the pool and earning rewards accordingly.&#x20;

{% hint style="info" %}
**Minimum hardware requirements:** 1 CPU, 8GB RAM, 10GB free disk space
{% endhint %}

## How to run a validator

{% hint style="info" %}
See example integration of a Validator [here](https://github.com/vana-com/vana-dlp-chatgpt/blob/main/docs/running\_on\_testnet.md#running-a-validator-on-an-existing-dlp).
{% endhint %}

The following outlines the high level steps to run a DLP validator.&#x20;

1. Choose the DLP you'd like to run a validator for.
   * You can run validators in multiple DLPs
2. Register as a validator through the DLP via its smart contract.
   * You must meet the minimum staking requirements for the DLP
3. Wait for your registration request to be approved by the DLP.
4.  Run the validator node specific to the DLP. Confirm that your validator is running correctly. Your logs should look something like this, which will vary by DLP:

    <figure><img src="../.gitbook/assets/Screenshot 2024-05-27 at 1.27.48 PM.png" alt=""><figcaption><p>Logs for a ChatGPT DLP validator node</p></figcaption></figure>

    * See DLP-specific instructions for running a validator node
5. Congratulations, your validator is up and running! You can keep track of your stats and trust score by looking onchain.&#x20;

### Deploy Validators

Once a DLP validator has been built, we are ready to deploy it. DLP nodes form a peer-to-peer network, and can be deployed to any infrastructure of your choice (ex, AWS, Google Cloud Platform, Azure, etc). Ideally, nodes have a static IP to more easily communicate with each other. Each node must have a wallet used to register the node to the DLP. Once the node is running and registered, they can begin serving proof-of-contribution requests within the DLP.

### Deploy the Smart Contract

Clone the DLP smart contract from a [template](https://github.com/vana-com/vana-dlp-smart-contracts), modify it for the needs of your specific DLP, and deploy it to the network following the readme.

### Validator registration

The [Data Liquidity Pool smart contract](https://github.com/vana-com/vana-dlp-smart-contracts?tab=readme-ov-file#data-liquidity-pool-smart-contract) is designed to manage the registration of validators. This contract ensures that validators can participate in maintaining the network's integrity and security while earning rewards for their contributions. To register a new node, create a wallet for it and call the registration function in the DLP smart contract.

## Scoring process

Validators earn rewards for validating uploaded files. For a given data validation request, each validator scores data based on metrics that are relevant to the data type. The scores are aggregated and written onchain, but how does the DLP decide how to reward its validators?

Every 1800 blocks (\~3 hours), a DLP epoch concludes and the DLP contract sends a chunk of rewards to its validators. The precise amount of rewards a given validator receives depends is determined by the Nagoya consensus process.

In Nagoya consensus, each validator submits a score for every other validator to the DLP smart contract. Validators score each other based on the quality of their assessments and their operational performance. For instance, if a validator is perceived as wrongly giving an uploaded file that appears fraudulent or low quality a high score, it may receive low scores from other validators.

{% hint style="info" %}
Somewhat more formally: a validator peer's emissions amount is based on calculations for their **rank** and **consensus**. It is calculated by multiplying these two scores, integrating both the peer's individual valuation by the network (rank) and the collective agreement on that valuation (consensus). This multiplication ensures that emissions are allocated in a manner that considers both the quality of contributions and the degree of communal support for those contributions.
{% endhint %}

When an epoch concludes, the consensus process converts the most recent validator scores into a distribution for that epoch's emissions, and the rewards are distributed to the validators accordingly. Low-ranking validators quickly realize fewer rewards for their contributions, ensuring that an honest majority of validators is able to out-earn dishonest actors and therefore uphold the integrity of the DLP over time.
