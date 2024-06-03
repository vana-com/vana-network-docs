---
description: Help bringing user data on-chain
---

# Create a Data Liquidity Pool (DLP)

## Creating a DLP

On mainnet, creating a DLP will be fully permissionless, with voting to elect the top 16 DLPs. As we roll out the network, we are partnering closely with DLP creators to help them get setup. Please fill out this [form](https://docs.google.com/forms/d/e/1FAIpQLSfB\_puqABBqCUZCFfjKihp7qc4V1wCv9APn86ijHNeBs93xyw/viewform) if you'd like to create a DLP and apply for token grants.&#x20;

_There are 16 slots on mainnet for data liquidity pools. This limit is intended to incentivize quality over quantity. Currently, there are teams building DLPs for: Reddit, Twitter, LinkedIn, ChatGPT, Github. Multiple DLPs can be created for the same data source, but we expect the community to prefer voting in one best performing DLP for each data source. Top performers on testnet will be voted into slots on mainnet._

{% hint style="info" %}
Please join our [Discord](https://discord.gg/xfGrYrjw) as well to present your DLP and engage with the community.
{% endhint %}

## How to start a DLP

1. Choose a valuable data source
   * Current community requests: stack overflow, telegram, youtube, email, google drive
2. Make sure users can access that data source
   * For example, through a GDPR or CCPA data export request, through scraping their own data, or through an API.&#x20;
   * Optionally, build an application that makes it easy for data contributions to add their data
3. Decide how the DLP will validate and value data
   * Data validation and value depends on the data source
   * Once decided, implement your incentives and validation checks
   * We recommend rolling this out iteratively in phases to test the incentives
4. Register as a DLP creator. This requires a minimum staking threshold.&#x20;
5. Deploy your DLP smart contract
6. Start up a DLP validator and recruit other existing validators to participate in the DLP as well
7. Congrats, you're up and running!
8. To quality for block rewards, get voted into the top 16 DLP slots based on data value and participation

## Components

A data liquidity pool consists of:

1. A peer-to-peer network of validators running proof-of-contribution
2. A DLP smart contract that communicates back to the connectome&#x20;
3. An optional UI for data contributors to add data to a liquidity pool

### DLP Nodes

A DLP node can handle data specific to a data liquidity pool. It can make use of the `opendata` framework that implements all the components of the Vana network. A starting point can be found here:&#x20;

{% hint style="info" %}
Vana framework with core components: [https://github.com/vana-com/vana-framework/](https://github.com/vana-com/vana-framework/)

ChatGPT data liquidity pool (as example): [https://github.com/vana-com/vana-dlp-chatgpt](https://github.com/vana-com/vana-dlp-chatgpt)
{% endhint %}

{% hint style="warning" %}
Still work-in-progress - not yet open sourced

* Data liquidity pool with simple zk proofs: [https://github.com/vana-com/dlp-zk](https://github.com/vana-com/dlp-zk)
{% endhint %}

### Proof of contribution

DLPs have the flexibility to validate data according to their unique requirements. Regardless of the specific verification methods employed, a DLP should strive to ensure that each data point passes the following criteria, which is implemented through a proof-of-contribution function:

* **Meaningfulness**: The data should contribute novel and valuable insights to the DLP's overall dataset. It should enhance the richness and diversity of the available information.
* **Validity**: The data must adhere to a schema that is consistent with the existing data within the DLP. Conforming to a standardized structure ensures compatibility and facilitates efficient data processing.
* **Authenticity and Contributor's rights**: The data must be genuine and, if required, originate from a legitimate account. This ensures the integrity and reliability of the information. The data contributor submitting the data must have the necessary rights and permissions to do so.&#x20;

This proof-of-contribution function checks data validity and maps the diverse data submissions to a score that can be used to reward fungible DLP-specific tokens.&#x20;

### DLP Smart Contract

A DLP smart contract is responsible for recording consensus values among network nodes and can help orchestrate how proof-of-contribution works in the DLP. A starting point can be found here:

{% hint style="info" %}
[https://github.com/vana-com/vana-dlp-smart-contracts](https://github.com/vana-com/vana-dlp-smart-contracts)
{% endhint %}

{% hint style="warning" %}
Integration of the DLP-specific ERC-20 token is still in progress.&#x20;

We highly recommend using the DLP Smart Contract with the integrated DLP token to avoid redeployment of the Smart Contract.
{% endhint %}

### DLP Upload UI

A UI may be useful to data contributors to upload their data to a DLP, but it is not necessary. Ultimately, it's up to the DLP to decide what is best for the DLP's contributors to be able to write data transactions on-chain. A starting point for a UI can be found here:&#x20;

{% hint style="warning" %}
Still work-in-progress, Link coming soon.\
Not yet open source - need to sanitize repos before open sourcing

ChatGPT: [https://github.com/vana-com/chatgpt-ui](https://github.com/vana-com/chatgpt-ui)\
r/datadao: [https://github.com/rdatadao/interface](https://github.com/rdatadao/interface)
{% endhint %}

## Deploy Your DLP

Once a DLP has been built, we are ready to deploy it. DLP nodes form a peer-to-peer network, and can be deployed to any infrastructure of your choice (ex, AWS, Google Cloud Platform, Azure, etc). Ideally, nodes have a static IP to more easily communicate with each other. Each node must have a wallet used to register the node to the DLP.

### Register a new DLP

Once a DLP Smart Contract is deployed to the Vana network, reach out to us and we will register this contract as a DLP. We will be manually approving DLP registration at the beginning of the testnet before moving to voting-based approval.&#x20;

### Deploy DLP Smart Contract

Clone the DLP smart contract from a template, modify it for the needs of your specific DLP, and deploy it to the network.&#x20;

1. Install [Hardhat](https://hardhat.org/hardhat-runner/docs/getting-started#installation), an Ethereum development environment.
2. Clone our DLP smart contract repository: \[Link coming soon]
3. Run: `yarn install`
4. Copy `.env.example` into `.env` file and fill it out&#x20;
5. Run the example: `npx hardhat test test/dlpExample.ts`  (this will create a temporary local node and run the example)
6. If you want to change the smart contract code, that can be found here : `contracts/dataLiquidityPool/DataLiquidityPool.sol`\
   If you want to change the example code (add more files, validators, etc): \
   `test/dlpExample.ts`
7. Repeat step 5 to run and test your changes
8. To redeploy the smart contract to the mycelium testnet:\
   `npx hardhat deploy --network vanaMycelium --tags DataLiquidityPool`\
   `npx hardhat verify --network vanaMycelium <deployed contract address>`

### Register a node to a DLP

A DLP Smart contract will be able to accept new nodes into the DLP. To register a new node, create a wallet for it and call the registration function in the DLP smart contract. More information can be found in [become-a-validator.md](become-a-validator.md "mention").&#x20;

### Deploy DLP Nodes

Once DLP nodes have been registered, they must be deployed to a location where they can be reached by other DLP nodes. This can mean deploying to your favorite cloud vendor of choice or even running a node on your own hardware and setting up appropriate networking rules. Once the node is running, they can begin serving proof-of-contribution requests within the DLP.
