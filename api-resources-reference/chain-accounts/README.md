# 🌐 Accounts

`Accounts` are objects containing attributes referencing a blockchain account.&#x20;

They can be imported from an existing blockchain account or newly created but **they are needed** in order to write to the Aleph network, in particular, **to sign messages** when creating or updating a resource.

The API allows you to create or connect an account, sign messages and get message signatures.

| ENDPOINTS                                                |                                                                                                                                                                                                                                                                 |
| -------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Generate & Connect a new chain account](new-account.md) | [.new\_account()](new-account.md)                                                                                                                                                                                                                               |
| [Connect an existing chain account](import-account.md)   | <p><a href="import-account.md#1-from-private-key-or-secret-phrase">.import_account()</a></p><p><a href="import-account.md#2-from-wallet-provider">.from_provider()</a></p><p><a href="import-account.md#3-from-external-signer">.from_external_signer()</a></p> |
| [Sign messages](sign-message.md)                         | <p><a href="sign-message.md#1-signing-message-for-all-chain-account">.sign() </a><br><a href="sign-message.md#2-signing-with-web3">.w3_sign()</a></p>                                                                                                           |
| [Get message signature](pkey-sign.md)                    | <p><a href="pkey-sign.md#1-from-the-private-key">.pkey_sign()</a></p><p><a href="sign-message.md#2-signing-with-web3">.provider_sign()</a></p>                                                                                                                  |

