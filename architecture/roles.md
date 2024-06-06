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

# Roles

Each participant in the Vana network plays a vital role in maintaining Vana’s open data ecosystem. These participants include Data Pool Creators, Data Validators, Propagators, Data Contributors, Data Custodians, and Data Consumers.

### Data Liquidity Pool Creator

Liquidity Pool Creators are central to ensuring data liquidity and ecosystem integrity within the network.

#### **Responsibilities:**

* Deploy Data Liquidity Pools (DLPs) smart contracts on Vana.
* Define DLP validation methods and parameters to ensure data quality and value.
* Attract data contributors to upload their data and set conditions for data flow within the ecosystem.
* Design, implement, and manage systems to distribute DLP-token incentives to validators and Data Contributors.
* Influence users to contribute data for financial and ideological motives.

DLP Creators have full control over the tokenomics of their DLP-specific tokens, and can allocate their DLP-specific tokens however they like.&#x20;

### Validator

Validators are critical for maintaining the integrity, value, and trustworthiness of data within the network.

#### **Responsibilities:**

* Verify user data within DLPs according to standards set by DLP owners.
* Use Vana’s Proof-of-Contribution system to assess data legitimacy and value.
* Participate in the Nagoya Consensus to ensure consistent and accurate data scoring.
* Perform accurate and consistent data evaluations and disincentivize bad actors through slashing.
* Evaluate the performance of other validators to maintain network integrity.
* Back evaluations with personal stake to ensure accuracy and reliability.
* Respond to queries from data consumers, including decrypting data and validating results.

Data Validators earn DLP token rewards for accurate and consistent data evaluations.

### Propagator

Propagators are essential for ensuring the composability and security of the network.

#### **Responsibilities:**

* Consolidate and write data transactions onto the Connectome
* Verify the validity of network transactions.
* Maintain network state liveness through accurate and timely block creation.

Propagator’s earn transaction fees and block rewards for processing network transactions and finalizing blocks.

### Data Contributor

Data Contributors are the foundation of the system, supplying the valuable data on which the network is built.&#x20;

#### **Participation:**

* Submit data to network DLPs for token rewards and governance rights.
* Allow personal data to be written onto the Vana network for use across different DLPs and AI dApps.
* Pay transaction fees in DAT and additional fees to validators to maintain network stability.

Data Contributors provide their data to the network in return for DLP token rewards and ownership. Data contributors can also directly use their verified data in a dApp.&#x20;

### Data Consumers

Data Consumers pay for access to DLPs and dApps within the ecosystem. They create demand for data contribution and ecosystem growth.

#### **Participation:**

* Provide demand for DLP creation and data collection.
* Pay fees to access DLP data banks for external services.
* Propose ideas and data needs to DLP Creators.

We expect big tech companies will fill the role of Data Consumers and request access to niche data on the Vana network (if the users allow) to push the frontiers of their models. We also expect the Vana architecture to enable new model creators to finance and aggregate data for their projects.

### Data Custodian (optional)

Data Custodians increase the efficiency of data contributions within the Vana network by aggregating data from data contributors before it is submitted to a DLP. DLPs might opt to leverage Data Custodians to lower the barrier of entry for Data Contributors to share their data with DLPs.

#### **Responsibilities:**

* Act as intermediaries for Data Contributors to host their data.
* Simplify the process for Data Contributors to contribute data to DLPs.
* Ensure the safekeeping and accessibility of data and provide encryption to protect data from exploits.
* Comply with data protection regulations (GDPR, CCPA), ensuring data is hosted, stored, and accessed within authorized jurisdictions only.
* Generate zk-proofs for validators to verify the authenticity, integrity, and contribution of the data.

Data Custodians provide an optional service to simplify the data contribution process. Data Contributors share revenue with Custodians when they subscribe to their services.
