# Smart Contracts

The Vana network relies on several key smart contracts to facilitate data liquidity.

## Data Registry Contract

The data registry contract functions as a central repository for managing all data within the network, functioning as a comprehensive file catalog. It allows users to add new files to the system, with each file receiving a unique identifier for future reference.

The contract manages access control for these files, enabling file owners to grant specific addresses permission to access their files. It also handles the storage of file metadata, including any offchain proofs or attestations related to file validation, which can include various metrics such as authenticity, ownership, and quality scores. Users can retrieve detailed information about any file in the registry using its unique identifier, including its permissions and associated proofs.

{% hint style="info" %}
Moksha: [0xEA882bb75C54DE9A08bC46b46c396727B4BFe9a5](https://moksha.vanascan.io/address/0xEA882bb75C54DE9A08bC46b46c396727B4BFe9a5)
{% endhint %}

{% hint style="info" %}
Satori: [0xEA882bb75C54DE9A08bC46b46c396727B4BFe9a5](https://satori.vanascan.io/address/0xEA882bb75C54DE9A08bC46b46c396727B4BFe9a5)
{% endhint %}

## TEE Pool Contract

The TEE Pool contract manages and coordinates the [TEE Validators](../roles/satya-validators.md) and serves as an escrow for holding fees associated with validation tasks. Users pay a fee to submit data for validation, and the contract ensures that the validators process the data and provide proof of validation. The contract also allows the owner to add or remove validators, and it securely holds and disburses the fees related to these validation services.

{% hint style="info" %}
Moksha: [0xF084Ca24B4E29Aa843898e0B12c465fAFD089965](https://moksha.vanascan.io/address/0xF084Ca24B4E29Aa843898e0B12c465fAFD089965)
{% endhint %}

{% hint style="info" %}
Satori: [0xF084Ca24B4E29Aa843898e0B12c465fAFD089965](https://satori.vanascan.io/address/0xF084Ca24B4E29Aa843898e0B12c465fAFD089965)
{% endhint %}

## Root Network Contract

The DLP Root contract manages the registration and reward distribution for Data Liquidity Pools (DLPs) in the Vana ecosystem. It operates on an epoch-based system, where the top 16 most staked DLPs and their stakers receive rewards at the end of each epoch. The contract allows users to stake VANA tokens as guarantors for DLPs, with rewards distributed based on the staking position at the beginning of each epoch.

To prevent exploitation, the contract implements a minimum staking period and requires stakers to claim their rewards manually. DLP owners can set custom reward percentages to attract more stakers, potentially securing a position in the top 16. The system also allows for multi-DLP staking and requires an initial minimum stake from DLP owners for registration.

{% hint style="info" %}
Moksha:  [0xf408A064d640b620219F510963646Ed2bD5606BB](https://moksha.vanascan.io/address/0xf408A064d640b620219F510963646Ed2bD5606BB)
{% endhint %}

{% hint style="info" %}
Satori: [0xf408A064d640b620219F510963646Ed2bD5606BB](https://satori.vanascan.io/address/0xf408A064d640b620219F510963646Ed2bD5606BB)
{% endhint %}
