---
description: Only available for Accounts connected with Solana chain accounts
---

# Get Message Signature

Message signatures can be obtained by using either `pkey_sign` or `provider_sign` depending on the connection of the chain account (from private key vs from wallet provider)

### 1. From the private key

{% tabs %}
{% tab title="Solana" %}
```javascript
import { solana } from 'aleph-js'

signature = await solana.pkey_sign(private_key, address, message)
```
{% endtab %}
{% endtabs %}

### 2. From the provider

{% tabs %}
{% tab title="Solana" %}
```javascript
import { solana } from 'aleph-js'

signature = await solana.provider_sign(provider, message)
```
{% endtab %}
{% endtabs %}
