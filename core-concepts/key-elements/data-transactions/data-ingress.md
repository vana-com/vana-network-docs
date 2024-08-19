# Data Ingress

## Data Storage

In the Vana network, data is stored off-chain in a storage solution of the user's choice, providing flexibility and control over their data. This approach allows data contributors to utilize familiar platforms such as Dropbox, Google Drive, or decentralized options like IPFS.&#x20;

Vana's system only requires two key pieces of information: a URL pointing to the data's location and an optional identifier that changes when the data is modified (e.g., an [ETAG](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/ETag) or last modified date). This ensures data at a particular location has not changed since it was uploaded there.&#x20;

<figure><img src="../../../.gitbook/assets/image (1).png" alt="" width="375"><figcaption><p>Contributors upload files to their personal Dropbox or Google Drive accounts in the <a href="https://www.gptdatadao.org/claim/upload">GPT Data DAO</a>.</p></figcaption></figure>

By keeping data off-chain but accessible through these identifiers, Vana maintains a balance between data privacy, user control, and cost efficiency.

## Adding Data

To make data discoverable in the Vana network, it must be written onchain using the [Data Registry contract](../smart-contracts.md#data-registry-contract). The data contributor first uploads an [encrypted file](data-privacy.md) to a storage provider of their choice, then writes a pointer to that file (URL) and an optional content integrity hash to the registry.
