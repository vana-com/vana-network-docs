---
description: Once you’ve scoped out your DLP, it’s time to start building.
---

# Stage 2: Building

{% hint style="warning" %}
**Vana Testnet is for Testing Purposes Only**

Ensure you create a different configuration for data validation on testnet versus mainnet. Data privacy cannot be guaranteed in testnet.&#x20;
{% endhint %}

{% hint style="info" %}
You can follow the [ChatGPT DLP tutorial](https://github.com/vana-com/vana-dlp-chatgpt/blob/main/docs/running\_on\_testnet.md) for a step-by-step guide on creating a DLP. Skip 'Validator Setup' section as we sunsetted DLP Validators.
{% endhint %}

### **Step 1: Build a UI for Data Contributors \[Optional]**

Your DLP needs a user-friendly interface where contributors can upload, encrypt, and validate their data. You can choose from a range of options for building this UI — anything from a web app to a browser extension or mobile app. You can also use the open-source DLP UI template [here](https://github.com/vana-com/vana-dlp-ui) or understand how it works [here](../../core-concepts/data-ingress/data-storage.md).

* **Key Feature:** Ensure the UI has client-side encryption to maintain privacy and control for data contributors.
* **Tip:** Ensure your users understand how to access that data source. For example, through a GDPR or CCPA data export request, through scraping their own data, or through an API.&#x20;
* **Tip:** You can skip this step. Some DLPs are using Chrome extensions or scrapers to contribute data without a separate UI.

{% hint style="info" %}
Check out [gptDataDAO](https://www.gptdatadao.org/) and [redditDataDAO](https://rdatadao.org/) as references.
{% endhint %}

### **Step 2: Deploy the DLP Smart Contract**

The core of every DLP is the fully customizable **DLP Smart Contract**. Register your DLP with the [Root Network](../../core-concepts/key-elements/smart-contracts.md#root-network-contract). This requires meeting a minimum staking threshold.&#x20;

A DLP smart contract is responsible for rewarding data contributors DLP-specific tokens for their data. After proof-of-contribution is run, a score from 0-1 is given to the file, which can be used to determine how valuable the data is, and convert that to DLP-specific tokens.

* **Repo:** You can use the audited smart contract templates from the Vana GitHub repo [here](https://github.com/vana-com/vana-dlp-smart-contracts). Follow first 12 steps to complete the deployment.

### **Step 3: Contact Vana team**

Once a DLP Smart Contract is deployed to the Vana network, reach out to us and we will register this contract as a DLP. We will be manually approving DLP registration at the beginning of the testnet before moving to voting-based approval.&#x20;

{% hint style="info" %}
On the Mainnet this process will become permissionless.
{% endhint %}

### **Step 4: Deploy the DLPT (DLP Token) Contract**

Your DLP needs a token (e.g., $TDAT for Twitter data) to reward contributors and facilitate governance. Deploy [DLPT (DLP Token) contract](https://github.com/vana-com/vana-dlp-smart-contracts?tab=readme-ov-file#dlpt-contract) for your DLP using OpenZeppelin’s modules for minting permissions and voting rights. It leverages OpenZeppelin's ERC20, ERC20Permit, ERC20Votes, and Ownable modules for extended functionality.

### **Step 5: Implement Proof-of-Contribution**

A critical piece of your DLP is the **proof-of-contribution** function, which validates the quality of the submitted data and can be used to reward fungible DLP-specific tokens. You can customize this function to meet the needs of your specific DLP. Use the proof-of-contribution template provided [here](https://github.com/vana-com/vana-satya-proof-template) as a starting point.

* Data validation and value depends on the data source.
* Once decided, implement your incentives and validation checks.
* We recommend rolling this out iteratively in phases to test the incentives.

DLPs have the flexibility to validate data according to their unique requirements.&#x20;

* **Meaningfulness**: The data should contribute novel and valuable insights to the DLP's overall dataset. It should enhance the richness and diversity of the available information.
* **Validity**: The data must adhere to a schema that is consistent with the existing data within the DLP. Conforming to a standardized structure ensures compatibility and facilitates efficient data processing.
* **Authenticity and Contributor's rights**: The data must be genuine and, if required, originate from a legitimate account. This ensures the integrity and reliability of the information. The data contributor submitting the data must have the necessary rights and permissions to do so.

{% hint style="info" %}
See the ChatGPT DLP for a [detailed example of proof-of-contribution](https://github.com/vana-com/vana-dlp-chatgpt/blob/main/docs/proof\_of\_contribution.md)\
\
If using Satya validators, use this [proof-of-contribution template](https://github.com/vana-com/vana-satya-proof-template/) as a starting point. Attestation schema is [here](../../core-concepts/data-ingress/data-attestation.md).
{% endhint %}

### **Step 6: Connect to Satya for Proof Validation \[Optional]**

Connect your DLP’s UI and backend to the [Satya network](../../core-concepts/roles/satya-validators.md), which will handle data validation through decentralized validators. This ensures your proof-of-contribution mechanism runs efficiently and securely. You can read the whole integration guide in the [Data Validation](../../core-concepts/data-ingress/data-validation.md) section. You can also use your own TEE infrastructure for proof validation.
