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

### At Launch

The initial 16 DLP slots at launch are allocated based on performance on Satori Testnet and the following criteria:

* **Total Transaction Volume:** The number of transactions created by the DLP.&#x20;
* **Unique Data Contributors:** The number of unique data contributions on Satori testnet. Note: users are discouraged from uploading real data to testnet DLPs.
* **Data Security Audit:** An independent assessment of the [Proof of Contribution](proof-of-contribution/) function deployed by the DLP.&#x20;

DLPs are encouraged to publicly launch earlier to ensure that they can start driving these metrics sooner.&#x20;

### Post-Launch

DLPs are selected and maintained by a [system of governance](dlp-governance.md) that aligns with Vana’s vision to prioritize community participation.&#x20;

To incentivize competition and ensure high-quality data within the DLPs, Data Liquidity Rewards are distributed based on performance across 4 key metrics, weighted as follows:

* Total Transactions Facilitated by the DLP (TTF) - 15%
* Total Transaction Fees (Gas Costs) created by the DLP (TFC) - 15%
* Total Number of Verified Data Uploads to the DLP (VDU) - 50%
* Unique Wallets that Interacted with the DLP (UW) - 20%

The score 𝑆𝑖 for each Data Liquidity Pool (DLP) 𝑖 is calculated by summing the weighted contributions of four metrics (W): TTF, TFC, VDU, and UW. Each metric is normalized by dividing it by the total of that metric across all DLPs, and then multiplied by its respective weight to reflect its importance as follows:&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2024-06-20 at 10.46.45.png" alt=""><figcaption></figcaption></figure>

## Propagators

Propagators rely on Proof of Stake (PoS) to validate data transactions and maintain network security.

To participate, Propagators must stake a minimum amount of VANA tokens, which are held as collateral to ensure honest behaviour. Propagators are randomly selected to propose and validate blocks, with the selection probability proportional to their staked amount.&#x20;

This process includes proposing new blocks, having them attested by other propagators, reaching consensus through a supermajority, and ensuring decentralization and fairness. Successful Propagators earn VANA rewards, while those who act maliciously may be penalized.
