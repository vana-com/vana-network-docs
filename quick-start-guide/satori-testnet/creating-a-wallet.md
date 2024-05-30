# Creating a Wallet

This is an overview of how to create a Vana wallet, and associated keys. Read the [working-with-keys.md](working-with-keys.md "mention") section on how keys work in the Vana ecosystem.&#x20;

## Ways to Create a Wallet

### For Basic Use

The Vana L1 is an EVM-compatible blockchain; therefore, any wallet that supports EVM chains can be used to create a wallet that can send and receive $DAT. Some good ones are [MetaMask](https://metamask.io/), [Rabby](https://rabby.io/), and [Trust Wallet](https://trustwallet.com/).

### For DLP Participation

Create a local wallet using the `vanacli` command line tool on your computer, so it can be used to create or participate in a DLP.

{% hint style="danger" %}
**Keep your mnemonic safe**

When a wallet is created, a mnemonic is created that can be used to recover your wallet. Anyone who knows the mnemonic for your wallet account can access your DAT tokens. Hence you must always keep this mnemonic in a safe and secure place, known only to you. More important, if you lose your wallet address, you can use its mnemonic (that you stored away in safekeeping) to restore the wallet.
{% endhint %}

## Creating a local wallet with CLI <a href="#creating-a-local-wallet-with-cli" id="creating-a-local-wallet-with-cli"></a>

To create a wallet using the CLI:

Install the Vana package.

Run the following command

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
