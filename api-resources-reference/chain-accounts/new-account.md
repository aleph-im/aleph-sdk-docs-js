# Generate & Connect New Chain Account

To create a new account, use the new\_account function. Aleph will create a blockchain account on the chain of your choice and import it as an `Account` object.&#x20;

Call the new\_account function on the corresponding chain module of your choice:

{% tabs %}
{% tab title="Avalanche" %}
```javascript
//EXAMPLE

import { avalanche } from 'aleph-js'

account = await avalanche.new_account()

// RETURNS THE ACCOUNT OBJECT

{
  'private_key': '<PRIVATE KEY>',
  'public_key': '<PUBLIC KEY>',
  'address': '<ADDRESS>',
  'type': 'AVAX',
  'source': 'integrated',
  'signer': '<KEYPAIR>',
  'name': '<ACCOUNT NAME OR ADDRESS>'
}
```
{% endtab %}

{% tab title="Cosmos" %}
```javascript
// New account function signature for Cosmos
await cosmos.new_account(
  {
    path: "m/44'/118'/0'/0/0",
    prefix: "cosmos"
  }
)

-------------------------------------------------

// EXAMPLE 

import { cosmos } from 'aleph-js'

account = await cosmos.new_account()

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
await ethereum.new_account(
  {
    path: "m/44'/60'/0'/0/0"
  }
)

-----------------------------------------------

//EXAMPLE
  
import { ethereum } from 'aleph-js'

account = await ethereum.new_account()

// RETURNS THE ACCOUNT OBJECT

{
  'private_key': '<PRIVATE KEY>',
  'public_key': '<PUBLIC KEY>',
  'mnemonics': '<MNEMONICS>',
  'address': '<ADDRESS>',
  'type': 'ETH',
  'source': 'integrated',
  'signer': <WALLET OBJECT>,
  'name': '<ACCOUNT NAME OR ADDRESS>'
}
```
{% endtab %}

{% tab title="NULS 2.0" %}
```javascript
// FUNCTION SIGNATURE
await nuls2.new_account(
  {
    chain_id: 1,
    prefix: 'NULS'
  }
)

-----------------------------------------------

// EXAMPLE
  
import { nuls2 } from 'aleph-js'

account = await nuls2.new_account()

// RETURNS THE ACCOUNT OBJECT

{
  'private_key': '<PRIVATE KEY>',
  'public_key': '<PUBLIC KEY>',
  'mnemonics': '<MNEMONICS>',
  'address': '<ADDRESS>',
  'type': 'NULS2',
  'name': '<ACCOUNT NAME OR ADDRESS>'
}
```
{% endtab %}

{% tab title="Solana" %}
```javascript
// EXAMPLE
import { solana } from 'aleph-js'

account = await solana.new_account()

// RETURNS THE ACCOUNT OBJECT

{
  'private_key': '<PRIVATE KEY>',
  'public_key': '<PUBLIC KEY>',
  'address': '<ADDRESS>',
  'type': 'SOL',
  'source': 'integrated',
  'signer': <WALLET OBJECT>,
  'name': '<ACCOUNT NAME OR ADDRESS>'
}

------------------------------------------------

// FUNCTION SIGNATURE
await solana.new_account(
  {
    path: "m/44'/60'/0'/0/0",
  }
)

```
{% endtab %}

{% tab title="Substrate" %}
```javascript
// FUNCTION SIGNATURE

await substrate.new_account(
  {
    format: 42
  }
)

-----------------------------------------------

// EXAMPLE 

import { substrate } from 'aleph-js'

account = await await substrate.new_account()

// RETURNS THE ACCOUNT OBJECT
{
  'keyring': keyring,
  'private_key': '<PRIVATE KEY>',
  'public_key': '<PUBLIC KEY>',
  'mnemonics': '<MNEMONICS>',
  'address': '<ADDRESS>',
  'address_format': format,
  'type': 'DOT',
  'source': 'integrated',
  'signer': pair,
  'name':
}
```
{% endtab %}
{% endtabs %}

Some of the chains allow for passing extra parameters to create the blockchain account. Below you will find a table of the optional parameters, sorted by chain.

| Chain         | Parameters                                 | Default value         |
| ------------- | ------------------------------------------ | --------------------- |
| **Cosmos**    | <mark style="color:blue;">path</mark>      | `"m/44'/118'/0'/0/0"` |
|               | <mark style="color:blue;">prefix</mark>    | `"cosmos"`            |
|               |                                            |                       |
| **Ethereum**  | <mark style="color:blue;">path</mark>      | `"m/44'/60'/0'/0/0"`  |
|               |                                            |                       |
| **NULS2**     | <mark style="color:blue;">chain\_id</mark> | `1`                   |
|               | <mark style="color:blue;">prefix</mark>    | `"NULS"`              |
|               |                                            |                       |
| **Solana**    | <mark style="color:blue;">path</mark>      | `"m/44'/60'/0'/0/0"`  |
|               |                                            |                       |
| **Substrate** | <mark style="color:blue;">format</mark>    | `42`                  |
