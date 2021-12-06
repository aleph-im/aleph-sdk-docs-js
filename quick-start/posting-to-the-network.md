---
description: >-
  Writing to the network requires a blockchain account which will serve as the
  referenced account on the resource generated.
---

# Posting to the Network

{% hint style="success" %}
Posting to the network is done in two steps:

1. Connect a blockchain account
2. Create a resource
{% endhint %}

### 1. Connect a blockchain account

The aleph-js library currently supports the following chains:

* NULS 1.0 and NULS 2.0
* Ethereum
* Polkadot - Substrate
* Cosmos & Cosmos SDK
* Solana
* Avalanche

Whether you connect to an existing blockchain account or create a new one, the account returned by the library is an object having:

* a `type`: which type of account it is ETH, NULS, ...
* an `address`
* a `public_key`
* a few other fields like a private\_key, source, signer, name. The`private_key` is needed by the signing and encryption modules.&#x20;
* `mnemonics` that can be used to reconstruct the `private_key`.

```javascript
// Example of a NULS account imported or created through aleph-js
{
  private_key:  '<PRIVATE KEY DISPLAYED HERE>',
  mnemonics: '<this would be a mnemonics phrase>',
  type: 'NULS2',
  public_key: '<PUBLIC KEY DISPLAYED HERE>',
  address: '<ACCOUNT ADDRESS>',
  name: '<ACCOUNT NAME OR ADDRESS>'
}
```

#### ➡️  With an existing blockchain account

You can connect **any existing blockchain account** by using the `import_account` function and passing in either the **private key** or the **mnemonics** of the account depending on the chain used.

{% tabs %}
{% tab title="Avalanche" %}
```javascript
import { avalanche } from 'aleph-js'

// Import account from private key
account = await avalanche.import_account({private_key: '<YOUR PRIVATE KEY>'})
```
{% endtab %}

{% tab title="Cosmos" %}
```javascript
import { cosmos } from 'aleph-js'

// Import account from mnemonics
account = await cosmos.import_account({mnemonics: '<YOUR PRIVATE KEY>'})
```
{% endtab %}

{% tab title="Ethereum" %}
```javascript
import { ethereum } from 'aleph-js'

// Import account from mnemonics
account = await ethereum.import_account({mnemonics: '<YOUR PASSPHRASE HERE>'})

// Import account from private key
account = await ethereum.import_account({private_key: '<YOUR PRIVATE KEY HERE>'})
```
{% endtab %}

{% tab title="NULS" %}
```javascript
import { nuls2 } from 'aleph-js'

// From mnemonics:
account = await nuls2.import_account({mnemonics: '<YOUR MNEMONICS PASSPHRASE HERE>'})

// From private key:
account = await nuls2.import_account({private_key: '<YOUR PRIVATE KEY HERE>'})
```
{% endtab %}

{% tab title="Polkadot" %}
```javascript
import { substrate } from 'aleph-js'

// Import account from mnemonics
account = await substrate.import_account({mnemonics: 'YOUR PASSPHRASE HERE'})

// Import account from private key
account = await substrate.import_account({private_key: '<YOUR PRIVATE KEY>'})
```
{% endtab %}

{% tab title="Solana" %}
```javascript
import { solana } from 'aleph-js'

// Import account from private key
account = await solana.import_account({private_key: '<YOUR PRIVATE KEY>'})
```
{% endtab %}
{% endtabs %}

#### ➡️  With a web3 wallet provider

{% tabs %}
{% tab title="Ethereum" %}
```javascript
import { ethereum } from 'aleph-js'

let account = null

if (window.ethereum) {
  try {
    // Request account access if needed
    await window.ethereum.enable()
    account = await ethereum.from_provider(window['ethereum'] || window.web3.currentProvider)
  } catch (error) {
      // User denied account access...
  }
}
```
{% endtab %}

{% tab title="Solana" %}
```javascript
import { solana } from 'aleph-js'

await solana.from_provider(wallet)
```
{% endtab %}
{% endtabs %}

#### ➡️  With a newly created account

If your application user does not have a chain account yet, an account can be created for them with the `new_account` function.

Make sure the user has access and save the details of the account created for them.

{% tabs %}
{% tab title="Avalanche" %}
```javascript
import { avalanche } from 'aleph-js'

// Import account from private key
account = await avalanche.new_account()
```
{% endtab %}

{% tab title="Cosmos" %}
```javascript
import { cosmos } from 'aleph-js'

account = await cosmos.new_account()
```
{% endtab %}

{% tab title="Ethereum" %}
```javascript
import { ethereum } from 'aleph-js'

account = await ethereum.new_account()
```
{% endtab %}

{% tab title="Nuls" %}
```javascript
import { nuls2 } from 'aleph-js'

await nuls2.new_account()
```
{% endtab %}

{% tab title="Polkadot" %}
```javascript
import { substrate } from 'aleph-js'

account = await await substrate.new_account()
```
{% endtab %}

{% tab title="Solana" %}
```javascript
import { solana } from 'aleph-js'

account = await solana.new_account()
```
{% endtab %}
{% endtabs %}

{% hint style="success" %}
More details on importing and creating an account are available [here](../api-resources-reference/chain-accounts/).&#x20;
{% endhint %}

### 2. Create a resource

```javascript
import { posts, ethereum } from 'aleph-js'

// Import account from the correct chain to post to Aleph
account = await ethereum.import_account({mnemonics: '<YOUR PASSPHRASE HERE>'})

await posts.submit(
  account.address,
  'mytype',
  {'body': 'test post written on Aug 17th'},
  {
    'account': account,
    'channel': 'TEST',
    'api_server': 'https://api2.aleph.im'
  }
 )
```

🎉 A `Message` object, with a POST type, has been created and is returned.

```javascript
{
  chain: 'ETH',
  channel: 'TEST',
  sender: '<YOUR ACCOUNT ADDRESS WILL DISPLAY HERE>',
  type: 'POST',
  time: 1629224958.629,
  item_type: 'inline',
  item_content: '{"type":"mytype","address":"<YOUR ACCOUNT ADDRESS WILL DISPLAY HERE>","content":{"body":"test post written on Aug 17th"},"time":1629224958.629}',
  item_hash: '7f146b0ecac264c8c2d48ffc3143b0be9329cad5f24861c8172a5f7a17d99385',
  signature: '0x3dab99351b5773a7d174ce71136c0f9ff23e26e8a347b1b3a90592f75ea4553300dbf7277243b7760f0ab4eede8ded26ae3d1228d7fc540379401d36639abcc71c'
}
```

{% hint style="info" %}
All `post`, `aggregate` and `store` resources created in Aleph are inherently `Message` Objects. Depending on the type of resource created, the `item_content` object keys will differ.
{% endhint %}

### 3. Going further

Learn more about how you can create, update and query [Post](../api-resources-reference/posts/), [Aggregate](../api-resources-reference/aggregates/) and [Store](../api-resources-reference/store/) objects.&#x20;
