# Working with Keys

## Coldkeys and Hotkeys

The Vana wallet holds the core ownership of assets on the Vana network, acting as the identity for all operations. This guide explains how to work with Vana wallet keys. For instructions on creating a Vana wallet, see [creating-a-wallet.md](creating-a-wallet.md "mention").

A Vana wallet consists of a coldkey and a hotkey, used for different operations in the Vana ecosystem.&#x20;

## **Key Pairings**

Each key is a pair of separate cryptographic keys. A coldkey has a private key and a public key, as does a hotkey. This is similar to an account on a blockchain.

## Coldkey

The coldkey is synonymous with the wallet name. For example, the `--wallet.name` option in a `vanacli` command accepts the coldkey as its value, while `--wallet.hotkey` accepts the hotkey. One coldkey can have multiple hotkeys.

### **Coldkey Uses**

* **Storage**: Holds DAT tokens.
* **Delegation**: For delegating and undelegating DAT tokens.
* **DLP Creation**: Used for creating a DLP.
* **Security**: Provides the highest level of security; always encrypted.

## Hotkey

You can create multiple hotkeys paired with a single coldkey. In a DLP, you are identified by your hotkey, keeping your coldkey secure. The same hotkey cannot be used for two nodes in the same DLP but can be used in different DLPs.

### **Hotkey Uses**

* **Transactions**: Signing transactions.
* **Operations**: Registering and running DLP nodes.
* **Delegation**: DAT holders can delegate their DAT to a validator’s hotkey.

## Security

* **Coldkey**: Highly secure and always encrypted, used for storing and managing DAT securely.
* **Hotkey**: Less secure, generally unencrypted, used for regular operational tasks.
