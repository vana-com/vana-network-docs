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

# Proof of Contribution

Vana uses a Proof-of-Contribution (PoC) system to validate data submitted to the network. The PoC system functions to ensure the integrity and quality of data within Data Liquidity Pools (DLPs). Everyone's data is different, so to enable data liquidity, data must be mapped to some fungible asset.

## DLP-specific implementations

Each DLP implements their own proof of contribution function based on their particular dataset. For example, r/datadao measured contributions based on amount of karma, and included an ownership check having users post a code in their reddit profile to confirm ownership. This proof-of-contribution check depends on the goals of the data liquidity pool and the best way to measure data contributions.

The proof-of-contribution function defines success for your data liquidity pool. If you do not want a particular kind of data in your DLP, but it passes or is rewarded by your proof-of-contribution function, then your proof-of-contribution function is not complete.

To validate data submissions, DLP Validators scan through the data transactions and assign a score using the DLP's contribution function. The function takes into account various data characteristics, such as completeness, accuracy, and relevance to the DLP’s purpose.

Each function depends on the constraints imposed by the DLP that receives the data contributions. As such, DLP Validators may impose their own unique functions to incentivize the type and quality of data they collect. This flexibility ensures efficient evaluation of data for each DLP while ensuring that data contributions are accurately evaluated.

## Model Influence Functions

One recommended implementation for DLP Proof-of-Contribution is to run a [model influence function](https://www.vana.org/posts/model-influence-functions-measuring-data-quality), which measures exactly how much new information a given data point teaches the AI model.

## Data Privacy

To protect the privacy of data contributions, great care has gone in to protecting the user's data. Validators can act as a trusted party and securely run PoC on user data. Read more about how Validators protect data in [data-privacy.md](../../../developers/data-ingress/data-privacy.md "mention").

The PoC system supports zero-knowledge proofs. When a Data Contributor or Custodian submits data to the DLP, they generate a zero-knowledge proof that verifies the authenticity and integrity of the data, as well as its contribution to the DLP, without revealing its full contents. Read more about it in [zero-knowledge-proof-of-contribution.md](zero-knowledge-proof-of-contribution.md "mention").
