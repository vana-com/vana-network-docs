# Data Storage

In the Vana network, data is stored encrypted and off-chain in a storage solution of the DLP's choice, providing flexibility and control over their data. This approach allows data contributors to utilize familiar platforms such as Dropbox, Google Drive, or decentralized options like IPFS.&#x20;

The DLP can choose to provide a central storage location (ex: a Dropbox account controlled by the DLP), or ask the data contributor to store it in their own storage (ex: a Dropbox account controlled by the data contributor).&#x20;

Vana's system only requires two key pieces of information: a URL pointing to the data's location and an optional identifier that changes when the data is modified (e.g., an [ETAG](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/ETag) or last modified date). This ensures data at a particular location has not changed since it was uploaded there.&#x20;

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt="" width="375"><figcaption><p>Contributors upload files to their personal Dropbox or Google Drive accounts in the <a href="https://www.gptdatadao.org/claim/upload">GPT Data DAO</a>.</p></figcaption></figure>

By keeping data off-chain but accessible through these identifiers, Vana maintains a balance between data privacy, user control, and cost efficiency.

## Adding Data

To make data discoverable in the Vana network, it must be written onchain using the [Data Registry contract](../smart-contracts.md#data-registry-contract). The data contributor first uploads an [encrypted file](data-privacy.md) to a storage provider of their choice, then writes a pointer to that file (the URL) and an optional content integrity hash to the registry.

<figure><img src="../../.gitbook/assets/image (1).png" alt="" width="375"><figcaption><p>Adding data to the <a href="../smart-contracts.md#data-registry-contract">data registry</a></p></figcaption></figure>

To add data to the Vana Network:

1. Generate a signature, the `encryption_key`, by asking the data contributor to sign a message, the `encryption_seed`
2. Symmetrically encrypt the data using the `encryption_key`. Code samples available in [data-privacy.md](data-privacy.md "mention").
3. Upload the encrypted data to a location of your choice. This can be a Web2 storage solution like Google Cloud, Dropbox, etc, or a Web3 solution like IPFS
4. Get the storage URL of the uploaded file
5. Add file to the [data registry contract](../smart-contracts.md#data-registry-contract): `addFile(encrypted_data_url)`
6. The data registry returns a `file_id`, which can be used later to look up the file
