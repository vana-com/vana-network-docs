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

# Incentives

{% hint style="warning" %}
This is a draft and should not be relied upon as a legal promise or guarantee for future implementations
{% endhint %}

## Data Liquidity Rewards

Data Liquidity Rewards ensure that early participants who contribute to building data liquidity on the network play a significant governance role through their holdings of [VANA](../../undefined/key-terms.md#vana-token-usdvana) as the network grows.&#x20;

By rewarding Data Liquidity Pool (DLP) creators and Propagators, these emissions incentivize the essential components needed to harness the network effects of pooled data: data liquidity and security. This structure incentivizes significant data onboarding early on, enabling robust data network effects to drive ecosystem value creation over time through user-owned AI models and user-owned data applications. The key network effect in an AI-first world is data.&#x20;

## Structure

The demand for data is extremely high and rapidly advancing towards AGI (Artificial General Intelligence). There is a wealth of Web2 data that needs to be onboarded to a user-owned system quickly to support better primitives for new economies and markets to emerge. The next few years are critical for building user-owned AI as we are witnessing advancements at an unprecedented pace.

To address this urgency, Data Liquidity Rewards are emitted at a significant rate for the first two years, with the option for the community to reconsider continuing emissions thereafter.&#x20;

|             | Year 1                | Year 2                | After year 2                       |
| ----------- | --------------------- | --------------------- | ---------------------------------- |
| DLPs        | 8% of Total Supply    | 6% of Total Supply    | Subject to Community Consideraiton |
| Propagators | 0.44% of Total Supply | 0.44% of Total Supply | 0.44% of Total Supply              |

_Top performing DLPs can earn approximately 1% of the total supply of the governance token based on initial estimates._&#x20;

## DLPs

The top 16 DLPs automatically earn Data Liquidity Rewards. &#x20;

### Post-Launch

DLPs are selected and maintained by a [system of governance](dlp-governance.md) that aligns with Vana’s vision to prioritize community participation.&#x20;

To incentivize competition and ensure high-quality data within the DLPs, Data Liquidity Rewards are distributed based on performance across 4 key metrics, weighted as follows:

* Total Transactions Facilitated by the DLP (TTF) - 15%
* Total Transaction Fees (Gas Costs) created by the DLP (TFC) - 15%
* Total Number of Verified Data Uploads to the DLP (VDU) - 50%
* Unique Wallets that Interacted with the DLP (UW) - 20%

The score 𝑆𝑖 for each Data Liquidity Pool (DLP) 𝑖 is calculated by summing the weighted contributions of four metrics (W): TTF, TFC, VDU, and UW. Each metric is normalized by dividing it by the total of that metric across all DLPs, and then multiplied by its respective weight to reflect its importance as follows:&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2024-06-20 at 10.46.45.png" alt=""><figcaption></figcaption></figure>

### At Launch

The initial 16 DLP slots at launch are allocated based on performance on Satori Testnet and the following criteria:

* **Total Transaction Volume:** The number of transactions created by the DLP.&#x20;
* **Unique Data Contributors:** The number of unique data contributions on Satori testnet. Note: users are discouraged from uploading real data to testnet DLPs.
* **Data Security Audit:** An independent assessment of the [Proof of Contribution](proof-of-contribution/) function deployed by the DLP.&#x20;

DLPs are encouraged to publicly launch earlier to ensure that they can start driving these metrics sooner.&#x20;

### Division of Data Liquidity Rewards

Data Liquidity Rewards rewards are divided between DLP Creators and VANA stakers within each eligible DLP at the discretion of the DLP Creator. The need for VANA holders to delegate stake to DLPs ensures a balancing mechanism wherein DLP Creators are incentivized to offer attractive sub-emissions to stakers while ensuring high-quality contributions.&#x20;

## Propagators

Propagators rely on Proof of Stake (PoS) to validate data transactions and maintain network security.

To participate, Propagators must stake a minimum amount of VANA tokens, which are held as collateral to ensure honest behaviour. Propagators are randomly selected to propose and validate blocks, with the selection probability proportional to their staked amount.&#x20;

This process includes proposing new blocks, having them attested by other propagators, reaching consensus through a supermajority, and ensuring decentralization and fairness. Successful Propagators earn VANA rewards, while those who act maliciously may be penalized.
