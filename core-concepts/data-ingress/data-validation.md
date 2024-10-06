# Data Validation

Vana uses a [proof-of-contribution](../key-elements/proof-of-contribution/ "mention") system to validate data submitted to the network. "Valid" means something different in each DLP, because different DLPs value data differently.

## Running Proof-of-Contribution in the Satya Network

The recommended way of validating data securely in the Vana Network is by using the Satya Network, a group of highly confidential nodes that run on special hardware. At a high level, the data contributor adds unverified data, and requests a proof-of-contribution job from the [satya-validators.md](../roles/satya-validators.md "mention") (and pay a small fee to have their data validated). Once validated, the Satya validator will write the proof on chain.

## Proof-of-Contribution Template

To run PoC in the Satya Network, a DLP builder must implement a simple proof-of-contribution function using this template.

{% hint style="info" %}
PoC Template: [https://github.com/vana-com/vana-satya-proof-template](https://github.com/vana-com/vana-satya-proof-template)
{% endhint %}

The diagram below explains how this PoC template works.&#x20;

<figure><img src="../../.gitbook/assets/image (23).png" alt=""><figcaption><p>Proof-of-contribution running in a Satya node</p></figcaption></figure>

1. The data contributor adds their encrypted data onchain, via the [Data Registry](../key-elements/smart-contracts.md#data-registry-contract).
2. They request a validation job, paying a small fee. Once a Satya node is available to run the job, they connect directly to the node, and send them the encryption key and the proof-of-contribution docker image that needs to run on the data to validate it.
3. The Satya node receives the key, and downloads the encrypted file, and decrypts it
4. The Satya node places the decrypted file in a temporary, shielded\* location. The node operator cannot see the contents of this location.
5. The Satya node downloads and initializes a docker container to run the specified proof-of-contribution, and mounts the input and output volumes. The PoC container will have access to the decrypted file.
6. The PoC container runs its validations on the decrypted data, and outputs the attestation. More information on data attestation can be found here: [data-attestation.md](data-attestation.md "mention").
7. The Satya node reads the output, and generates the proof.
8. The Satya node writes the proof onchain, and claims the fee as a reward for completing that work.

{% hint style="info" %}
\* A [Gramine shielded container](https://gramine.readthedocs.io/projects/gsc/en/latest/) is a specialized type of container that leverages the Gramine library OS to run applications in a secure, isolated environment, typically utilizing hardware-based trusted execution environments (TEEs) like Intel SGX.
{% endhint %}

## Satya Network Integration

Once a data contributor has uploaded their encrypted file to the [Data Registry](../key-elements/smart-contracts.md#data-registry-contract), it's time to run a proof of contribution job to validate it. The steps below show how to use the Satya Network to validate it.&#x20;

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption><p>Using a Satya node to run proof-of-contribution</p></figcaption></figure>

1. Each validation job requires a small fee (which changes based on load). The data contributor can get the current fee by calling `teeFee()` on the [#tee-pool-contract](../key-elements/smart-contracts.md#tee-pool-contract "mention").&#x20;
2. The current job fee is returned: ex: `job_fee = 3 VANA`.
3. The DLP UI now attaches a listener to listen for `JobSubmitted` events from the TEE Pool contract, which emits when the job is successfully submitted.
4. The DLP UI submits the job request to the TEE Pool to get the data contributor's file validated: `requestContributionProof(file_id, { value: job_fee })`.
5. The TEE Pool assigns a Satya node to handle the job, and the `JobSubmitted` event is fired.
6. The DLP UI receives the `JobSubmitted` event, and gets the corresponding `job_id`.
7. The DLP UI gets the details of the Satya node assigned to the job by calling the TEE Pool's `jobTee(job_id)`.
8. The TEE Pool returns the address of a Satya node, so the UI can connect to it directly: ex: `https://satya-1.com`.
9. The DLP UI sends a `/RunProof` request to the Satya node to begin the validation. It includes the encryption key used by the Satya node to decrypt the file, along with the URL of the proof-of-contribution docker image that will be run to generate the attestation. More information about the request below.
10. The Satya node downloads the encrypted data, decrypts it, and spins up the proof-of-contribution container, which validates the data and generates a result. It then builds the attestation according to the [data-attestation.md](data-attestation.md "mention") schema, and the proof is uploaded to IPFS.
11. The Satya node sends the proof to the TEE Pool.
12. The TEE Pool contract verifies the proof.
13. The TEE Pool adds the proof to the data registry.
14. The Satya node claims the `job_fee` for completing the job.
15. The TEE Pool releases the `job_fee`.

{% hint style="warning" %}
The Satya Network is a work in progress. It is subject to change, and may be unstable at this time. Do not send sensitive information to the Satya nodes while in testnet.
{% endhint %}

### Running Proofs on a Satya Node

<mark style="color:green;">`POST`</mark> `/RunProof`

Once a Satya node has been selected to run the proof-of-contribution for a data point, the data contributor can talk to that node directly.

**Headers**

| Name         | Value              |
| ------------ | ------------------ |
| Content-Type | `application/json` |

**Body**

<table><thead><tr><th width="207">Name</th><th width="117">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>file_id</code></td><td>number</td><td>File ID from the Data Registry</td></tr><tr><td><code>job_id</code></td><td>number</td><td>Job ID sent by the JobSubmitted event</td></tr><tr><td><code>encryption_key</code></td><td>string</td><td>The symmetric key used to decrypt the file (a wallet signature like <code>0x1234...</code>)</td></tr><tr><td><code>encryption_seed</code></td><td>string</td><td>The message that was signed to generate the <code>encryption_key</code></td></tr><tr><td><code>proof_url</code></td><td>string</td><td>The proof-of-contribution docker image URL, ex: <code>https://github.com/vana-com/vana-satya-proof-template/releases/download/v22/gsc-my-proof-22.tar.gz</code></td></tr><tr><td><code>env_vars</code></td><td>object</td><td>Any environment variables that get passed into the proof-of-contribution container as key/value pairs</td></tr><tr><td><code>secrets</code></td><td>object</td><td>Any sensitive environment variables that are get passed into the proof-of-contribution container as key/value pairs, encrypted using the process below. Only decryptable by a registered Satya node.</td></tr><tr><td><code>nonce</code></td><td>number</td><td>A random number that will be signed and returned in the response, useful for checking the Satya node's wallet address.</td></tr></tbody></table>

**Sample Request**

```json
{ 
    file_id: 123,
    job_id: 456, 
    encryption_key: "0x1234..", 
    encryption_seed: "Please sign to retrieve your encryption key",
    proof_url: "https://github.com/vana-com/vana-satya-proof-template/releases/download/v22/gsc-my-proof-22.tar.gz", 
    env_vars: {
        username: "john_doe"
    },
    secrets: {
        password: "008b24d...142e8"
    },
    nonce: 546883
}
```

**Response**

{% tabs %}
{% tab title="200" %}
```json
{
  "success": true
}
```
{% endtab %}

{% tab title="400" %}
```json
{
  "error": "Invalid request"
}
```
{% endtab %}
{% endtabs %}

#### Sending Secrets to PoC Container

When your Proof-of-contribution container runs, you may need to access secrets such as API keys, passwords, etc. The Satya nodes accept an `env_vars` object to send environment variables in plain text, however, this is not suitable for secret values.

To send secrets, encrypt them with the public key below, and send them as a part of the `secrets` object in the `/RunProof` request. They will be decrypted and injected into the Proof-of-contribution container as environment variables along with the `env_vars`. These secrets can only be decrypted by a TEE that's currently registered in the TEE Pool. &#x20;

```bash
# Create the public key
echo "-----BEGIN PUBLIC KEY-----
MIIBojANBgkqhkiG9w0BAQEFAAOCAY8AMIIBigKCAYEA4129oK+dUEalpqP5aT/M
A6yhFbAjNppOidQuVgeSgEPquXLlJrdLoomHGhzugbBYeKS6lceEDM3oygFdCGhT
sly26Ws8qyUIGlk0/JGf4mRHd9RMs0uOF50/mB4abNM/mA/k8cO46+UmXOK2rwEL
U2rPb5tWVzxjPqs8Aw9eT1n7UlvOXxFc4ChyIHX/plfbkKK1R1+PYhtBHeQT8aW1
o7wLsbbnkCGh2iahJaNacMWmUZ9YygdPg2DICQLK2KbZfZHhhylBjDzuBgjUzNai
ikVHzrR6f9eTihYjmpx8Br5Ubhj3lVt45nAXFidxMBe1e7IILNVl9C57sqV+nPFM
2s5ad/r3TDjOZ23e0FGBVsyG+lJwn9q/kx4kjSFsO8fNzJ7wUczVnfW+akox2rMX
rnvdxUhpAAEtJZme5+pnS6Fr4Zi8mUBPt9kC/mHTtbPQoLsX+FeBs/u+rpXe4xBr
+QhqShKWQ+4HzwQHCc5h9d4pqZEKK8UnpdeJ0c/QTqcVAgMBAAE=
-----END PUBLIC KEY-----" > public_key.pem

# Encrypt a sensitive value, ex: "my_password"
echo -n "my_password" | openssl pkeyutl -encrypt -pubin -inkey public_key.pem -pkeyopt rsa_padding_mode:oaep -pkeyopt rsa_oaep_md:sha256 | xxd -p -c 256 | tr -d '\n'
> 008b24d9c6e4ffc47e3ffa967c09804c7d536d5cf9d4b8a128699917823c9ec4987e82cc71e0bddefc02f273f3b5c48b9ac5238623c3496a865d986542dda00af0f328593243f9369fe1d83cfdadde9da8da319e7b3bb153a5d3d5f41b780def4454e3d4de622d2a60dde568a153d6ad4b7861937a381916786827ada875dc469c2838433d50a6076b1da6af720b696ad452972cc48bec6093738e75e9a49bef3d6f96769c6f1bf14ad2f2115de41133f3043976f2ce257f4cd3f4bafcd597f92bfaa8bf393b038fcdd70fa652bccf45669ac2007689af45c7da91abcb31b326d4d632560cf4857bc1e806c17b33aa6ee6af1f70641f63e487321ddfd6eea9accfac3a72915807a5ff553fc782d823e64f547fff8fb53b9b0022e54e8d78ba6c9973943c2bc491ac0b2020c94f7ae7198451ed295997a8c1e0c7dbe524a0faedd1cadc4149e06d14ecd533262b412def7108cd0dff76e2c00fe7598bb52cdb546afb38962405d5d25a50ff3c377eddf06f056363c41ae870dcb25819b98142e8

# Include the encrypted secret in the POST /RunProof request
...
secrets: {
    password: "008b24d...142e8"
},
...
```
