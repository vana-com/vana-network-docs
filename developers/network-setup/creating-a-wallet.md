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

# Creating a Wallet

This is an overview of how to create a Vana wallet, and associated keys. A Vana wallet holds the core ownership of assets on the Vana network, acting as the identity for all operations.

## For Basic Use

The Vana network is EVM-compatible and supports Ethereum-compatible addresses. Any wallet that supports EVM chains can be used to create a wallet that can send and receive [VANA](../../undefined/key-terms.md#vana-token-usdvana), including hardware wallets. Some recommended wallet applications are [MetaMask](https://metamask.io/), [Rabby](https://rabby.io/), and [Trust Wallet](https://trustwallet.com/).

## For Network Operators

Network operators like DLP validators can use the CLI tool that comes with the [Vana framework](https://github.com/vana-com/vana-framework) to manage their wallets.

The Vana framework supports wallets that each contain:

* **A coldkey**: an address representing the owner of a service running in the network.
* **A hotkey**: an address representing the service running in the network.

Coldkeys are secure keys stored encrypted offline, used for critical or infrequent transactions. A hotkey allows a validator to call a DLP smart contract and must be loaded into the live service environment.

Each of these is a pair of separate cryptographic keys. A coldkey has a private key and a public key, as does a hotkey.

### Coldkey

The coldkey is synonymous with the wallet name. For example, the `--wallet.name` option in a `vanacli` command accepts the coldkey as its value, while `--wallet.hotkey` accepts the hotkey. One coldkey can have multiple hotkeys.

### **Coldkey Uses**

* **Storage**: Holds VANA.
* **Delegation**: For delegating and undelegating VANA.
* **DLP Creation**: Used for creating a DLP.
* **Security**: Provides the highest level of security; encrypted at rest.

### Hotkey

You can create multiple hotkeys paired with a single coldkey. In a DLP, you are identified by your hotkey, keeping your coldkey secure. The same hotkey cannot be used for two nodes in the same DLP but can be used in different DLPs.

#### **Hotkey Uses**

* **Transactions**: Signing transactions.
* **Operations**: Registering and running DLP nodes.
* **Delegation**: VANA holders can delegate their VANA to a validator’s hotkey.
* **Security**: Less secure, generally unencrypted, used for regular operational tasks.

### For DLP Participation

Create a local wallet using the `vanacli` command line tool on your computer, so it can be used to create or participate in a DLP.

{% hint style="danger" %}
**Keep your mnemonic safe**

When a wallet is created, a mnemonic is created that can be used to recover your wallet. Anyone who knows the mnemonic for your wallet account can access your VANA tokens. Hence you must always keep this mnemonic in a safe and secure place, known only to you. More important, if you lose your wallet address, you can use its mnemonic (that you stored away in safekeeping) to restore the wallet.
{% endhint %}

## Creating a local wallet with CLI <a href="#creating-a-local-wallet-with-cli" id="creating-a-local-wallet-with-cli"></a>

To create a wallet using the CLI:

Clone the [vana-framework](https://github.com/vana-com/vana-framework) repository and follow the steps in Getting Started to install the CLI tool. Use the `wallet create` command to start the process of creating a wallet.

```bash
vanacli wallet create
```

You will be prompted to enter the wallet name (aka coldkey name), hotkey name, and a password to encrypt your wallet with.

```bash
vanacli wallet create
Enter wallet name (default): my-wallet
Enter hotkey name (default): my-hotkey

IMPORTANT: Store this mnemonic in a secure (preferable offline place), as anyone who has possession of this mnemonic can use it to regenerate the key and access your tokens. 

The mnemonic to the new coldkey is:

<super secret coldkey mnemonic>

You can use the mnemonic to recreate the key in case it gets lost. The command to use to regenerate the key using this mnemonic is:
vanacli w regen_coldkey --mnemonic <super secret coldkey mnemonic>

Specify password for key encryption: <super secret password>
Retype your password: <super secret password>

IMPORTANT: Store this mnemonic in a secure (preferable offline place), as anyone who has possession of this mnemonic can use it to regenerate the key and access your tokens. 

The mnemonic to the new hotkey is:

<super secret hotkey mnemonic>

You can use the mnemonic to recreate the key in case it gets lost. The command to use to regenerate the key using this mnemonic is:
vanacli w regen_hotkey --mnemonic <super secret hotkey mnemonic>
```

## Location of local wallets

Local wallets are stored on your machine under `~/.vana/wallets`.&#x20;
