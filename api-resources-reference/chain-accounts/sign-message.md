# Sign Message

Signing a message from a chain module **returns a signed message**.

The `account` and `message` are the **two required parameters** to be passed to the chain module to sign a message, except for the NULS chains where the private\_key from the account should be provided instead of the account.&#x20;

{% tabs %}
{% tab title="Avalanche" %}
```javascript
import { avalanche } from 'aleph-js'

signed_message = await avalanche.sign(account, message)
```
{% endtab %}

{% tab title="Cosmos" %}
```javascript
import { cosmos } from 'aleph-js'

signed_message = await cosmos.sign(account, message)
```
{% endtab %}

{% tab title="Ethereum" %}
```javascript
import { ethereum } from 'aleph-js'

signed_message = await ethereum.sign(account, message)
```
{% endtab %}

{% tab title="NULS / NULS 2.0" %}
```javascript
import { nuls } from 'aleph-js'

signed_message = await nuls.sign(private_key, message)


import { nuls2 } from 'aleph-js'

signed_message = await nuls2.sign(private_key, message)
```
{% endtab %}

{% tab title="Solana" %}
```javascript
import { solana } from 'aleph-js'

signed_message = await solana.sign(account, message)
```
{% endtab %}

{% tab title="Substrate" %}
```javascript
import { substrate } from 'aleph-js'

signed_message = await substrate.sign(account, message)
```
{% endtab %}
{% endtabs %}



Accounts connected with an Ethereum web3 provider have the ability to sign messages with the provider.

{% tabs %}
{% tab title="Ethereum" %}
```javascript
import { ethereum } from 'aleph-js'

signed_message = await ethereum.w3_sign(w3, address, message)
```
{% endtab %}
{% endtabs %}

