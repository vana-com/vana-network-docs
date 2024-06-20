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

Vana uses a Proof-of-Contribution (PoC) system to validate data submitted to the network. The PoC system functions to ensure the integrity and quality of data within Data Liquidity Pools (DLPs). Everyone's data is different, so to enable data liquidity, data must be mapped to some fungible asset.&#x20;

### DLP-specific implementations

Each DLP implements their own proof of contribution function based on their particular dataset. For example, r/datadao measured contributions based on amount of karma, and included an ownership check having users post a code in their reddit profile to confirm ownership. This proof-of-contribution check depends on the goals of the data liquidity pool and the best way to measure data contributions.&#x20;

The proof-of-contribution function defines success for your data liquidity pool. If you do not want a particular kind of data in your DLP, but it passes or is rewarded by your proof-of-contribution function, then your proof-of-contribution function is not compete.&#x20;

To validate data submissions, DLP Validators scan through the data transactions and assign a score using the DLP's contribution function. The function takes into account various data characteristics, such as completeness, accuracy, and relevance to the DLP’s purpose.

Each function depends on the constraints imposed by the DLP that receives the data contributions. As such, DLP Validators may impose their own unique functions to incentivize the type and quality of data they collect. This flexibility ensures efficient evaluation of data for each DLP while ensuring that data contributions are accurately evaluated.

### Model Influence Functions

One recommended implementation for DLP Proof-of-Contribution is to run a model influence function, which measures exactly how much new information a given data point teaches the AI model.&#x20;

### Data Privacy

To protect the privacy of data contributions, the PoC system supports zero-knowledge proofs. When a Data Contributor or Custodian submits data to the DLP, they generate a zero-knowledge proof that verifies the authenticity and integrity of the data, as well as its contribution to the DLP, without revealing its full contents. Read more about it in [zero-knowledge-proof-of-contribution.md](zero-knowledge-proof-of-contribution.md "mention").&#x20;

### Nagoya Consensus

> _Writer's note: We had to design a new consensus mechanism to handle the fuzziness of data contributions. For example, if I believe your data deserves a score of 100, and another validator believes your data deserves a score of 102, we could both be pretty much right. Neither of us as validators are acting maliciously or incorrectly. But generally crypto consensus mechanisms are designed for exact consensus only. Bittensor proposed an early version of this fuzzy consensus, which we have modified to work for private data and proof of contribution._&#x20;

To reach a state of agreement on data contributions and disincentivize malicious validators, the Proof-of-Contribution system employs Nagoya Consensus. In Nagoya Consensus, each DLP Validator expresses their perspective on the quality and value of data contributions as a rating. Validators then use their rating to score other validators through a set of ratings weighted by stake.

Nagoya Consensus rewards validators for producing data contribution scores that are in agreement with the evaluations of other validators. This disincentivizes divergence from the consensus majority while incentivizing validators to converge on honest assessments of data contribution.

By requiring validators to put stake behind their evaluations and rewarding convergence weighted by stake, Nagoya Consensus makes it economically unfavorable for even a significant minority of validators to collude and manipulate the state of the DLP. As long as an honest majority of stake-weighted validators participate, the system can come to consensus on data contribution scores that accurately reflect the quality and value of data in the DLP.
