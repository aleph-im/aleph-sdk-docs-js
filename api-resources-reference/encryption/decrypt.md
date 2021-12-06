# Decrypt

### Returns

Decrypt content with the account the content was encrypted for. This will return the decrypted content.



### Usage

```javascript
import { encryption } from 'aleph-js'

await encryption.decrypt(account, content)

// Or with optional parameters
await encryption.decrypt(account, content, {as_hex: true, as_string: true})
```

###

### Required parameters

| Parameter                                                      | Description                                               |
| -------------------------------------------------------------- | --------------------------------------------------------- |
| <mark style="color:green;">**account**</mark>** ** - _Account_ | Account where the public key was used to encrypt content. |
| <mark style="color:green;">**content**</mark>** **             | Content to decrypt                                        |

###

### Optional parameters

In addition to the required parameters above, an object of optional  parameters can be passed following the content like so:

`encryption.decrypt(account, content,`<mark style="color:purple;">`{as_hex: false}`</mark>`)`

*   <mark style="color:green;">**as\_hex**</mark> - _boolean_

    _`Default: true`_

    Should be set to true to decrypt content that was a hexadecimal representation of the object.


*   <mark style="color:green;">**as\_string**</mark> - _boolean_

    _`Default: true`_

    Should be set to true if the content to decrypt is a string. <mark style="background-color:yellow;">If as\_hex</mark> <mark style="background-color:yellow;"></mark>_<mark style="background-color:yellow;"></mark>_ <mark style="background-color:yellow;"></mark><mark style="background-color:yellow;">is set to true, as\_string will be ignored.</mark>

###

### Example

{% code title="DECRYPT REQUEST" %}
```javascript
await aleph.encryption.decrypt(account, '04465d5bbda5a1255fc19d494bfa8035b8a210ac96a0cdc8787d684048e1c879a06f107885ccec8b12350499fcad124a4adf3bbe4de125e55aac6359402e8db8b210241fbe86a785208995a26e913bcd3d23970a0a04872893a575be11dc87dde2a811d0183e86df3ea58ef66041b89e2ac7fa')
```
{% endcode %}

{% code title="RESPONSE" %}
```javascript
'content to encrypt'
```
{% endcode %}
