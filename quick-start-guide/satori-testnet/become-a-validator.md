# Become a Validator

{% hint style="info" %}
Please join our [Discord](https://discord.gg/xfGrYrjw) to get an overview of all existing DLPs and how to access them.
{% endhint %}

You can run a validator on your own hardware or on a cloud provider like GCP and AWS, ensuring the quality of data in the pool and earning rewards accordingly.&#x20;

## How to run a validator

1. Choose the DLP you'd like to run a validator for
   * You can run validators in multiple DLPs
2. Register as a validator through the DLP via its smart contract
   * You must meet the minimum staking requirements for the DLP
3. Run the validator node specific to the DLP. Confirm that your validator is running correctly. Your logs should look something like this, which will vary by DLP:&#x20;
   * See DLP-specific instructions for running a validator node

<figure><img src="../../.gitbook/assets/Screenshot 2024-05-27 at 1.27.48 PM.png" alt=""><figcaption></figcaption></figure>

4. Congratulations, your validator is up and running! You can keep track of your stats and trust score by looking onchain.&#x20;

## Scoring process

A data validation request is received by a validator and sent to other validators in the network to perform the actual validation. Each validator scores the data points based on certain metrics and reports them to the initiator. The scores are then aggregated and written onchain.&#x20;

Along with the data scores, whenever a task is performed by a validator, the validators are scored as well, depending on their performance. The scores are sent to the DLP smart contract, where consensus is reached via Nagoya consensus, and the validator scores are updated. Low-ranking validators quickly realize fewer rewards for their contributions, incentivizing validators who stay in consensus with other validators.&#x20;

