# Connect Existing Chain Account

Existing blockchain accounts can be imported through the library in an Account object to allow for the use of the private key to sign messages.&#x20;

Different options are available to make the connection:&#x20;

* the chain account private key&#x20;
* the chain account secret phrase
* the use of a third-party browser web3 provider like metamask
* the chain account details to stub an account object

Not all options are available on each chain module. Please refer below to see the connecting methods available for the needed chain.

### 1. From Private key or Secret Phrase

You can connect with **any existing blockchain account** by using the `import_account` function and passing in either the private key or the mnemonics of the account depending on the chain used.

Besides the `private_key` or `mnemonics`, other parameters like `name`, `path`, `prefix` or `format` can be passed in depending on the chain but are optional.&#x20;

In the eventuality that both `mnemonics` and `private_key` are passed in, private\_key will be ignored and **mnemonics will be used to import the account**.

{% tabs %}
{% tab title="Avalanche" %}
```javascript
// FUNCTION SIGNATURE
await avalanche.import_account({
  private_key: null,
  name: null
})

------------------------------------------------------------------------

// EXAMPLE
import { avalanche } from 'aleph-js'

// Import account from private key
account = await avalanche.import_account({
  private_key: '<YOUR PRIVATE KEY>'
})

// RETURNS THE ACCOUNT OBJECT

{
  'private_key': '<PRIVATE KEY>',
  'public_key': '<PUBLIC KEY>',
  'address': '<ADDRESS>',
  'type': 'AVAX',
  'source': 'integrated',
  'signer': '<KEYPAIR>',
  'name': '<PASSED IN NAME OR ACCOUNT ADDRESS>'
}
```
{% endtab %}

{% tab title="Cosmos" %}
```javascript
// FUNCTION SIGNATURE
await cosmos.import_account({
  mnemonics: null,
  path: "m/44'/118'/0'/0/0",
  prefix: "cosmos",
  name: null
})

------------------------------------------------------------------------

// EXAMPLE
import { cosmos } from 'aleph-js'

// Import account from mnemonics
account = await cosmos.import_account({mnemonics: '<ACCOUNT MNEMONICS>'})

// RETURNS THE ACCOUNT OBJECT
{
  'private_key': '<PRIVATE KEY>',
  'public_key': '<PUBLIC KEY>',
  'mnemonics': '<MNEMONICS>',
  'address': '<ADDRESS>',
  'prefix': '<PREFIX>',
  'path': '<PATH>',
  'type': 'CSDK',
  'source': 'integrated'
}
```
{% endtab %}

{% tab title="Ethereum" %}
```javascript
// FUNCTION SIGNATURE
await ethereum.import_account({
  private_key: null,
  mnemonics: null,
  path: "m/44'/60'/0'/0/0",
  name: null
})

-------------------------------------------------------------------------

// EXAMPLE
import { ethereum } from 'aleph-js'

// Import account from mnemonics
account = await ethereum.import_account({
  mnemonics: '<YOUR PASSPHRASE HERE>'
})

// OR Import account from private key
account = await ethereum.import_account({
  private_key: '<YOUR PRIVATE KEY HERE>'
})

// RETURNS THE ACCOUNT OBJECT

{
  'private_key': '<PRIVATE KEY>',
  'public_key': '<PUBLIC KEY>',
  'mnemonics': '<MNEMONICS>',
  'address': '<ADDRESS>',
  'type': 'ETH',
  'source': 'integrated',
  'signer': <WALLET OBJECT>,
  'name': '<PASSED NAME OR ACCOUNT ADDRESS>'
}
```
{% endtab %}

{% tab title="NULS 2.0" %}
```javascript
// FUNCTION SIGNATURE
await nuls2.import_account({
  private_key: null,
  mnemonics: null,
  chain_id: 1,
  prefix: 'NULS',
  name: null
})

-------------------------------------------------------------------------

// EXAMPLE
import { nuls2 } from 'aleph-js'

// From mnemonics:
account = await nuls2.import_account({
  mnemonics: '<YOUR MNEMONICS PASSPHRASE HERE>'
})

// OR From private key:
account = await nuls2.import_account({
  private_key: '<YOUR PRIVATE KEY HERE>'
})

// RETURNS THE ACCOUNT OBJECT

{
  'private_key': '<PRIVATE KEY>',
  'public_key': '<PUBLIC KEY>',
  'mnemonics': '<MNEMONICS>',
  'address': '<ADDRESS>',
  'type': 'NULS2',
  'name': '<PASSED NAME OR ACCOUNT ADDRESS>'
}


```
{% endtab %}

{% tab title="Solana" %}
```javascript
// FUNCTION SIGNATURE
await solana.import_account({
  private_key: null,
  name: null
})

-------------------------------------------------------------------------

// EXAMPLE
import { solana } from 'aleph-js'

// Import account from private key
account = await solana.import_account({
  private_key: '<YOUR PRIVATE KEY>'
})

// RETURNS THE ACCOUNT OBJECT

{
  'private_key': '<PRIVATE KEY>',
  'public_key': '<PUBLIC KEY>',
  'address': '<ADDRESS>',
  'type': 'SOL',
  'source': 'integrated',
  'signer': <WALLET OBJECT>,
  'name': '<PASSED IN NAME OR ACCOUNT ADDRESS>'
}
```
{% endtab %}

{% tab title="Substrate" %}
```javascript
// FUNCTION SIGNATURE
await substrate.import_account({
  private_key: null,
  mnemonics: null,
  format: 42,
  name: null
})

--------------------------------------------------------------------

// EXAMPLE
import { substrate } from 'aleph-js'

// Import account from mnemonics
account = await substrate.import_account({
  mnemonics: 'YOUR PASSPHRASE HERE'
})

// OR Import account from private key
account = await substrate.import_account({
  private_key: '<YOUR PRIVATE KEY>'
})

// RETURNS THE ACCOUNT OBJECT

{
  'keyring': <KEYRING OBJECT>,
  'private_key': '<PRIVATE KEY>',
  'public_key': '<PUBLIC KEY>',
  'mnemonics': '<MNEMONICS>',
  'address': '<ADDRESS>',
  'address_format': <FORMAT>,
  'type': 'DOT',
  'source': 'integrated',
  'signer': pair,
  'name': '<NAME PASSED IN OR ACCOUNT ADDRESS>'
}
```
{% endtab %}
{% endtabs %}

### 2. From Wallet Provider

Gets account from wallet provider and returns an account object containing the details of the account that was found in the wallet.

Note how `private_keys` are not returned with this connection type. Messages will be signed with the provider instead.&#x20;

{% tabs %}
{% tab title="Ethereum" %}
```javascript
// FUNCTION SIGNATURE
// Most likely provider is web3.currentProvider
// provider = web3.currentProvider

ethereum.from_provider(provider)

----------------------------------------------------------------------

// EXAMPLE
import { ethereum } from 'aleph-js'

let account = null

if (window.ethereum) {
  try {
    // Request account access if needed
    await window.ethereum.enable()
    account = await ethereum.from_provider(
      window['ethereum'] || window.web3.currentProvider
    )
  } catch (error) {
      // User denied account access...
  }
}

// RETURNS ACCOUNT OBJECT
{
  'private_key': null,
  'mnemonics': null,
  'address': '<ACCOUNT ADDRESS>',
  'name': '<ACCOUNT ADDRESS>',
  'type': 'ETH',
  'source': 'provider',
  'provider': <WEB3 PROVIDER>,
  'signer': signer
}
```
{% endtab %}

{% tab title="Solana" %}
```javascript
// FUNCTION SIGNATURE

solana.from_provider(provider)

--------------------------------------------------------------------------

// EXAMPLE

// You are most likely using the wallet adapter @project-serum/sol-wallet-adapter
// Provider would be the Wallet initliazed
// provider = wallet 

import { solana } from 'aleph-js'
await solana.from_provider(provider)

// RETURNS AN ACCOUNT OBJECT
{
    'private_key': null,
    'public_key': '<PUBLIC KEY>',
    'address': '<PUBLIC KEY>',
    'name': '<PUBLIC KEY>',
    'type': 'SOL',
    'source': 'provider',
    'provider': provider
  }
```
{% endtab %}
{% endtabs %}

### 3. From External Signer

Will return a stub account object with the passed in attributes. In this case, a message signature will be done by the signer.

{% tabs %}
{% tab title="Cosmos" %}
```javascript
await cosmos.from_external_signer({
    address: null, 
    name: null, 
    signe: null, 
    public_key: null
})

---------------------------------------------------------------------
// EXAMPLE

import { cosmos } from 'aleph-js'
await cosmos.from_external_signer({public_key: '<PUBLIC KEY HERE>'})

// RETURNS AN ACCOUNT OBJECT
{
    'public_key': '<PUBLIC KEY PASSED IN>',
    'address': '<ADDRESS PASSED IN>',
    'type': 'CSDK',
    'source': 'function',
    'signer': '<SIGNER PASSED IN>',
    'name': '<NAME PASSED IN>'
  }
```
{% endtab %}
{% endtabs %}
