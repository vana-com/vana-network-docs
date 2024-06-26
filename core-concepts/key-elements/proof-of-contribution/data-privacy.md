---
description: >-
  The Vana network strives to ensure personal data remains private, and is only
  shared with trusted parties.
---

# Data Privacy

## Encrypting personal data

Vana uses a patented non-custodial encryption technique to encrypt personal data. Data does not leave the user's browser unencrypted. A user's file is encrypted with their own encryption key, and when the encryption key is shared with a validator, that encryption key is encrypted with a validator's encryption key.&#x20;

The steps are as follows:

1. The user uploads a decrypted file (F)
2. They are prompted to sign a message with their wallets, creating a unique signature that can only be recreated by signing that same message using that same wallet
3. The generated signature is used as the encryption key (EK) to encrypt the file F using a symmetric encryption technique
4. The encryption key EK is then encrypted with the validator's public key, making an encrypted encryption key (EEK)
5. The validator receives this EEK, and uses their private key to decrypt it and get back the EK
6. The EK is used to decrypt the file F

This way, only a trusted validator can see the user's encrypted file.&#x20;

This is just one privacy implementation of a DLP. A DLP can implement other privacy features as well, for example, using a [zero-knowledge-proof-of-contribution.md](zero-knowledge-proof-of-contribution.md "mention") that doesn't require a validator to decrypt the user's file to be able to verify it.&#x20;
