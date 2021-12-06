---
description: >-
  Call the .submit function to create an aggregate of a key-value pair for an
  address.
---

# Create an aggregate key

### Returns

The function will return the aggregate message object created.&#x20;

If no account is passed in the optional object parameter, the aggregate won't actually be written to the network (aka you would be running a test).



### Usage

```javascript
import { aggregates } from 'aleph-js'

await aggregates.submit(address, key, content)

// OR with additional optional parameters:
await aggregates.submit(address, key, content, { account: account })
```



### Required parameters

| Parameter                                                 | Description                                                                                          |
| --------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| <mark style="color:green;">**address**</mark> - _string_  | <p>Address the Aggregate should be associated with <br>or the address that posted the Aggregate.</p> |
| <mark style="color:green;">**key**</mark> - _string_      | Key to mutate                                                                                        |
| <mark style="color:green;">**content**</mark>  - _object_ | The value content object to save for the key.                                                        |

###

### Optional parameters

In addition to the required parameters above, <mark style="color:purple;">an object of optional parameters</mark> can be passed following the content object like so:

`aggregates.submit(address, key, content,`<mark style="color:purple;">`{channel: "my_channel", account: account}`</mark>`)`

*   <mark style="color:green;">**api\_server**</mark> _- string_

    _`Default: "https://api1.aleph.im"`_

    Target API server


*   <mark style="color:green;">**chain**</mark> - _string_

    `Default: null`

    The chain used by the sender's account. Value can be `NULS2`, `ETH`, `DOT`, `CSDK`, `SOL`, `AVAX`.


*   <mark style="color:green;">**channel**</mark> - _string_

    `Default: null`

    Channel of the message. Ideally, an application would decide and use one channel.


*   <mark style="color:green;">**inline**</mark> - _boolean_

    `Default: true`

    Should the message be stored as a separate file or inserted inline? :information\_source: Set it to false for data that could fall under GDPR.


*   <mark style="color:green;">**storage\_engine**</mark> - _string_

    `Default: "storage"`

    Storage engine to use. Possible values: `storage`, `ipfs`


*   <mark style="color:green;">**account**</mark> - _Account_ | <mark style="background-color:red;">required for writing to the network</mark>&#x20;

    `Default: null`

    Sender's account to use for signing.

    :information\_source: Needed if you want to send and save the message on the network. Without it, it is a dry run.



### Example: Create an aggregate

{% code title="CREATE AN AGGREGATE OF KEY-VALUE PAIR FOR ADDRESS" %}
```javascript
import { aggregates } from 'aleph-js'

await aggregates.submit(
  account.address, 
  'first_key', 
  {'a': 1, 'b': 2}, 
  {
    'account': account, 
    'channel': 'TEST'
  }
)
```
{% endcode %}

{% code title="RESPONSE" %}
```javascript
{
  chain: 'ETH',
  channel: 'TEST',
  sender: '<SENDER ADDRESS WILL DISPLAY HERE>',
  type: 'AGGREGATE',
  time: 1629228489.081,
  item_type: 'inline',
  item_content: '{"address":"<YOUR SENDER ADDRESS WILL DISPLAY HERE>",
  "key":"first_key",
  "content":{"a":1,"b":2},
  "time":1629228489.081}',
  item_hash: '251f6bc2d4e61713a91c255d91011c6d50fbd786eadb6640ec8d3c86e311c9be',
  signature: '0xe078056f7a8192a9f44d1b57dd78e35e2aae1b5ce17824180be943d717d6969a09d654139326a3d7c945ddc91f8699eaff65f4b6c67ebc40fe09fd319101a9171c'
}
```
{% endcode %}

