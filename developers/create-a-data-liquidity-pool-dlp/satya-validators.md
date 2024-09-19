# Satya Validators

The Vana network utilizes independent Trusted Execution Environment (TEE) validators to perform data validation requests for DLPs, simplifying their architecture by eliminating the need for DLPs to operate their own validator nodes. We refer to these highly confidential compute nodes as the Satya Validators.

Each Satya validator node is a sealed, encrypted virtual machine running on an independently operated server with a bare metal install of [Intel SGX](https://www.intel.com/content/www/us/en/products/docs/accelerator-engines/software-guard-extensions.html), an advanced hardware-level isolation technology.&#x20;

This setup ensures that neither the node operators nor any other parties can access the interior of the processor or the data being processed. The TEE environment guarantees that deployed programs within it are immutable and private, maintaining operational integrity and preventing unauthorized changes while processing user data.

<figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption><p>A DLP that relies on TEE validators</p></figcaption></figure>

## **Responsibilities**

* Verify user data by running Proof-of-Contribution docker images to assess data legitimacy and value.
* Attest to the validity of the data and write the attestation back on-chain.
* Claim rewards for completing a validation job.

{% hint style="warning" %}
Satya Validators are a work in progress. Code samples and technical documentation will be added soon.
{% endhint %}

Read more about how the Satya network operates in [data-validation.md](../data-ingress/data-validation.md "mention").
