# Data Validation

Vana uses a [proof-of-contribution](../proof-of-contribution/ "mention")system to validate data submitted to the network. "Valid" means something different in each DLP, because different DLPs value data differently.&#x20;

## Data Attestation

Anyone can submit data to the Vana network. However, for data to be considered valid, it must be attested for by a trusted party, i.e. [validators](../../roles/validators/ "mention") in a DLP. These trusted parties issue a "certificate" to prove that this data is, in fact, authentic, high-quality, unique, and has whatever other properties DLPs value in its data contributions.&#x20;

Data attestations live offchain, and a URL to a data's attestation is written onchain alongside the data itself.&#x20;

<figure><img src="../../../.gitbook/assets/image (7).png" alt=""><figcaption><p>A DLP that uses TEE validators gets its data contributions attested for (in blue)</p></figcaption></figure>

## Attestation Schema

The attestation of a data point must follow a spec. Each attestation has fields that are shared across all attestations and also allow DLPs to insert unique fields.&#x20;

An example of when this would be useful: consider a ChatGPT DLP that accepts GDPR exports from chatgpt.com. Say the DLP considers the export to be high quality when the number of conversations in the export exceeds 10. This DLP can insert `numberOfConversations: xxx` right in the attestation when Proof of Contribution is run.&#x20;

{% hint style="warning" %}
The attestation schema is a work in progress and will be shared soon.
{% endhint %}
