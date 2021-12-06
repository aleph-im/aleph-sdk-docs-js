# Encrypt for self

### Returns

Encrypt content for an account. The public key of the address account wil be used for encryption. This will return the encrypted content.



### Usage

```javascript
import { encryption } from 'aleph-js'

await encryption.encrypt_for_self(account, content)

// Or with optional parameters
await encryption.encrypt_for_self(account, content, {as_hex: true, as_string: true})
```



### Required parameters

| Parameter                                                      | Description                                                                                |
| -------------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| <mark style="color:green;">**account**</mark>** ** - _Account_ | Account to encrypt the content for. Public key of the account will be used for encrypting. |
| <mark style="color:green;">**content**</mark>                  | Content to encrypt.                                                                        |



### Optional parameters

In addition to the required parameters above, an object of optional  parameters can be passed following the content like so:

`encryption.encrypt_for_self(public_key, content,`<mark style="color:purple;">`{as_hex: false}`</mark>`)`

*   <mark style="color:green;">**as\_hex**</mark> - _boolean_

    _`Default: true`_

    If true, the function will return the encrypted result as a hexadecimal string representation.


*   <mark style="color:green;">**as\_string**</mark> - _boolean_

    _`Default: true`_

    Should be set to true if the content to encrypt is a string.

{% hint style="info" %}
The encryption curve in this function is either `ed25519` for Solana accounts or `secp256k1` for all other accounts.
{% endhint %}



### Example

```javascript
import { encryption } from 'aleph-js'

await aleph.encryption.encrypt_for_self(account, "content to encrypt")
```

{% code title="RESPONSE" %}
```javascript
'04465d5bbda5a ... 9e2ac7fa'
```
{% endcode %}

