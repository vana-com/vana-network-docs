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
This is a draft and should not be relied upon as a legal promise or guarantee for future implementations.
{% endhint %}

## Data Liquidity Pool Rewards

Data Liquidity Pools (DLPs) are critical to Vana, as they incentivize and verify data coming into the network. Our core strategy is to gather the highest quality data, build the best AI models, and monetize them, providing a programmable way to work with user-owned data and build the frontiers of decentralized AI.&#x20;

## Reward Structure

For two years following the Token Generation Event (TGE), DLP rewards are 17.5% of the Fully Diluted Valuation (FDV), distributed over twenty-four months:

| DLP Rewards | % of FDV | Tokens       |
| ----------- | -------- | ------------ |
| Year 1      | 8.75%    | 10.5 million |
| Year 2      | 8.75%    | 10.5 million |

On average, the top 16 DLPs will earn 0.547% of FDV, with top DLPs earning upwards of 1% of FDV. Vana has a slightly deflationary supply of 120 million tokens, similar to Ethereum.&#x20;

{% hint style="success" %}
**Top DLPs can earn upwards of 1% of FDV**
{% endhint %}

These rewards are designed to incentivize Data Liquidity Contributions similar to early Ethereum miners. We believe that to scale crypto adoption, it's important to invite new participants. Proof of stake networks have the downfall of only making the rich richer. Proof of work and proof of contribution networks are incredibly powerful, as they allow anyone to contribute to the network.&#x20;

Participating in a data liquidity pool on Vana is like being an early Ethereum miner, and we've structured the rewards similarly.

## DLP Reward Distribution

DLPs control how they distribute rewards to the DLP creator, data token holders, and DLP stakers. This allows new DLPs to break into the top 16 by incentivizing stakers and issuing rewards to their token holders before directly monetizing the data.

Here's an example breakdown for a top DLP earning 1% of FDV in the first year:

<table><thead><tr><th width="186"></th><th width="136">% of rewards</th><th width="104">% of FDV</th><th width="98">Tokens</th><th>Role in DLP</th></tr></thead><tbody><tr><td>DLP Creator</td><td>40%</td><td>0.4%</td><td>480,000</td><td>Implements proof of contribution and a method for data contributors</td></tr><tr><td>DLP Stakers</td><td>20%</td><td>0.2%</td><td>240,000</td><td>Puts stake behind the DLP based on its data value to Vana</td></tr><tr><td>DLP Token Holders, including Data Contributors and Validators</td><td>40%</td><td>0.4%</td><td>480,000</td><td>Includes data contributors, validators, and token purchasers</td></tr></tbody></table>

{% hint style="info" %}
The DLP creator chooses the initial rewards split. After launch, the split is decided by DLP token holders, forming a data DAO.
{% endhint %}

## DLP Selection Process

The DLP Rewards apply to the top 16 DLP slots, prioritizing quality over quantity. These DLPs are selected through a staking mechanism where VANA token holders stake their tokens with DLPs they believe will perform well. The top 16 DLPs, ranked by total staked tokens, qualify for rewards, which they [share with their stakers](incentives.md#dlp-reward-distribution).

A detailed breakdown of the DLP Selection process can be found in the [DLP Governance](dlp-governance.md) section.

## Propagators

Propagators rely on Proof of Stake (PoS) to validate data transactions and maintain network security.

To participate, Propagators must stake a minimum amount of VANA tokens, which are held as collateral to ensure honest behaviour. Propagators are randomly selected to propose and validate blocks, with the selection probability proportional to their staked amount.&#x20;

This process includes proposing new blocks, having them attested by other propagators, reaching consensus through a supermajority, and ensuring decentralization and fairness. Successful Propagators earn VANA rewards, while those who act maliciously may be penalized.
