---
description: Encrypt content for an address public key using the .encrypt() function.
---

# Encrypt

### Returns

This will return the encrypted content.



### Usage

```javascript
import { encryption } from 'aleph-js'

await encryption.encrypt(public_key, content)
  
// Or with an additional parameters
await encryption.encrypt(public_key, content, {as_hex: true, as_string: true})
```



### Required parameters

| Parameter                                                         | Description                                |
| ----------------------------------------------------------------- | ------------------------------------------ |
| <mark style="color:green;">**public\_key**</mark>** ** _- string_ | Public key used for encrypting the content |
| <mark style="color:green;">**content**</mark>** **                | Content to encrypt                         |



### Optional parameters

In addition to the required parameters above, an object of optional  parameters can be passed following the content like so:

`encryption.encrypt(public_key, content,`<mark style="color:purple;">`{as_hex: false}`</mark>`)`

*   <mark style="color:green;">**as\_hex**</mark> - _boolean_

    _`Default: true`_

    If true, the function will return the encrypted result as a hexadecimal string representation.


*   <mark style="color:green;">**as\_string**</mark> - _boolean_

    _`Default: true`_

    Should be set to true if the content to encrypt is a string.


*   <mark style="color:green;">**curve**</mark> - _string_: `secp256k1` or `secp256r1` or `ed25519`

    _`Default "secp256k1"`_

    The curve of encryption, as it can't be deducted from the public key. `` Value can be either `secp256k1` or `secp256r1` or `ed25519`

{% hint style="info" %}
Using the `as_hex` and `as_string` options are useful if you want to serialize yourself, or avoid serialization, and if you are working with files (or binary blobs).

Typically, if you want to store an encrypted file, you will handle Buffer objects, and won't serialize in any way (both options will be set to false).
{% endhint %}



### Example

```javascript
import { encryption } from 'aleph-js'

await aleph.encryption.encrypt(account.public_key, "content to encrypt")
```

{% code title="RESPONSE" %}
```javascript
'04465d5bbda5a12 ... df3ea58ef66041b89e2ac7fa'
```
{% endcode %}

