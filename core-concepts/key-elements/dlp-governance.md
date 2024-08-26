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

# DLP Governance

{% hint style="warning" %}
This is a draft and should not be relied upon as a legal promise or guarantee for future implementations.
{% endhint %}

Data Liquidity Pools (DLPs) transform raw data into valuable onchain assets, playing a crucial role in Vana's architecture. Given their central importance, it is logical for DLPs to be at the heart of community governance, allowing [VANA](../../undefined/key-terms.md#vana-token-usdvana) holders to directly influence key decisions.&#x20;

Combined with the [DLP Rewards](incentives.md), DLP Governance ensures the sustainability of the ecosystem by aligning governance with contributions that support the network's growth.

## DLP Selection Process

The DLP Rewards apply to the top 16 DLP slots, prioritizing quality over quantity. These DLPs are selected through a staking mechanism where VANA token holders stake their tokens with DLPs they believe will perform well. The top 16 DLPs, ranked by total staked tokens, qualify for rewards, which they [share with their stakers](incentives.md#dlp-reward-distribution).

This competitive system ensures only the highest quality data feeds into Vana. Each DLP must demonstrate a robust "[proof of contribution](proof-of-contribution/)" system, validating the value of their collected data. This focus on data quality is crucial for Vana's long-term goal of building a user-owned AI model capable of outperforming advanced systems like GPT-6. Leading DLPs are set out in the [DLP Leaderboard](https://docs.vana.org/vana/welcome-to-vana/dlp-leaderboard).&#x20;

## DLP Staking and Periodic Snapshots

DLP Staking in the Vana network allows users to stake their VANA tokens in support of their preferred DLPs, directly influencing which DLPs are eligible for block rewards.

Regular periodic snapshots are taken to ensure that the top 16 DLPs, determined by the amount of VANA staked, continue to reflect the community's choice.&#x20;

This system ensures that DLPs that add value to those who are most invested in network growth (and therefore largest VANA holders) avail of DLP rewards. It also provides clear incentives for DLPs to continuously create value.  At the same time, it fosters competition to drive high quality data by allowing new entrants, with community support, to overtake incumbents.

## Creating new DLP Slots

The parameter of the top 16 slots earning rewards is governable, and if the community votes to increase slots, it can be expanded to allow more DLPs to earn rewards for onboarding data onto the network. Vana is a permissionless network, so any new DLP can join the network, but only the top 16 DLPs by stake earn rewards.

## Initial DLP Selection

### At launch - overview

The initial DLP slots at launch are allocated based on performance on Satori Testnet and the following criteria:

* **Total Transaction Fees (Gas Costs)** created by the DLP
* **Total Number of Unique wallets** with Verified Data Uploads
* **Amount Staked** in the DLP

DLPs are encouraged to publicly launch earlier to ensure that they can start driving these metrics sooner.&#x20;

### At launch - details

DLPs are selected and maintained by a [system of governance](dlp-governance.md) that aligns with Vana’s vision to prioritize community participation.&#x20;

To incentivize competition and ensure high-quality data within the DLPs, Data Liquidity Rewards are distributed based on weighted, normalized performance across the below metrics. _Note that DLP Revenue and Trading Volume are currently set to 0% but will be adjusted as the Network continues to grow._

* Total Transaction Fees (Gas Costs) created by the DLP (TFC) - 20%
* Total Number of Unique wallets with Verified Data Uploads (VDU) - 20%
* Amount Staked (AST) - 60%
* DLP Revenue in $VANA (REV) - 0%
* 2 week avg DLP Trading Volume (DTV) - 0%

The score 𝑆𝑖 for each Data Liquidity Pool (DLP) 𝑖 is calculated by summing the weighted contributions of three metrics: TFC, VDU, and AST. Each metric is normalized by dividing it by the total of that metric across all DLPs, and then multiplied by its respective weight to reflect its importance as follows:&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2024-08-15 at 12.48.10 PM.png" alt=""><figcaption></figcaption></figure>
