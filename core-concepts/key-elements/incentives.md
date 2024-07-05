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
This is a draft and subject to change based on testnet findings and community feedback. It should not be relied upon as a legal promise or guarantee for future implementations
{% endhint %}

## Block Rewards

The Block Rewards program ensures that those who have invested in building the core pieces of the Vana ecosystem continue to play a governance role through their holdings of [VANA](../../undefined/key-terms.md#vana-token-usdvana) as the network grows.&#x20;

By rewarding Data Liquidity Pool (DLP) creators and Propagators, the program incentivizes the essential components needed to harness the network effects of pooled data: data liquidity and security. This structure generates strong initial value, enabling robust data network effects to drive ecosystem value creation over time.

## Structure

At launch, a portion of supply is designated for community development and block rewards.  Of the amount designated for Block Rewards, 70% is allocated to Data Liquidity Pools and 30% is allocated to Propagators.&#x20;

The structure of Block Rewards heavily incentivizes early contributions and declines over time. This ensures that the network effects of pooled data can be realized quickly, allowing the system to achieve broad adoption and sustainable growth.&#x20;

## DLP Block Rewards

The top 16 DLPs are eligible to participate in the Block Rewards Program.  DLPs are selected and maintained by a [system of governance](dlp-governance.md) that aligns with Vana’s vision to prioritize user-owned infrastructure and encourage community participation.&#x20;

To incentivize competition and ensure high-quality data within the DLPs Block Rewards are distributed based on performance across 4 key metrics, weighted as follows:

* Total Transactions Facilitated by the DLP (TTF) - 15%
* Total Transaction Fees (Gas Costs) created by the DLP (TFC) - 15%
* Total Number of Verified Data Uploads to the DLP (VDU) - 50%
* Unique Wallets that Interacted with the DLP (UW) - 20%

Blocks are created every 6 seconds (10 blocks per minute).&#x20;

The score 𝑆𝑖 for each Data Liquidity Pool (DLP) 𝑖 is calculated by summing the weighted contributions of four metrics (W): TTF, TFC, VDU, and UW. Each metric is normalized by dividing it by the total of that metric across all DLPs, and then multiplied by its respective weight to reflect its importance as follows:&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2024-06-20 at 10.46.45.png" alt=""><figcaption></figcaption></figure>

## Division of Block Rewards

Block rewards in the Vana network are divided between DLP Creators and VANA stakers within each eligible DLP. This dual reward system ensures that both the creators driving network value and the stakeholders supporting them are fairly compensated.

## Propagator Block Rewards

Propagators rely on Proof of Stake (PoS) to validate data transactions and maintain network security.

To participate, Propagators must stake a minimum amount of VANA tokens, which are held as collateral to ensure honest behavior. Propagators are randomly selected to propose and validate blocks, with the selection probability proportional to their staked amount.&#x20;

This process includes proposing new blocks, having them attested by other Propagators, and reaching consensus through a supermajority, ensuring decentralization and fairness. Successful Propagators earn VANA rewards, while those who act maliciously may be penalized.
