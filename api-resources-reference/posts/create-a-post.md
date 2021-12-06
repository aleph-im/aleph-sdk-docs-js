---
description: Call the .submit() function to create a Post
---

# Create a post

### Returns

The post object that was just created.

{% hint style="success" %}
**Tips** \
Pass a **ref** in the optional object parameter and/or **tags** in your content to take full advantage of the filtering abilities later on.
{% endhint %}

###

### Usage

```javascript
import { posts } from 'aleph-js'

await posts.submit(address, post_type, content)

// Or with optional parameters
await posts.submit(address, post_type, content, { channel: channel, account: account})
```

###

### Required parameters

| Parameter                                                   | Description                                                                                                                                                                                                                               |
| ----------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <mark style="color:green;">**address**</mark> - _string_    | <p>Address the Post should be associated with <br>or the address that submitted the Post.</p>                                                                                                                                             |
| <mark style="color:green;">**post\_type**</mark> - _string_ | <p>A lowercase string of your choice for the <code>item_content.type</code> of the post message.<br> ex: <code>amend</code>,<code>blog</code>, <code>chat</code>, <code>comment</code></p>                                                |
| <mark style="color:green;">**content**</mark> - _object_    | <p>The content object to save to the <code>item_content.content</code> of the post message.</p><p><mark style="background-color:yellow;">If <code>tags</code> are passed within the object, they can be searched for later on.</mark></p> |

###

### Optional parameters

In addition to the required parameters above, an object of optional  parameters can be passed following the content like so:

`posts.submit(address, post_type, content,`<mark style="color:purple;">`{api_server: "https://api2.aleph.im"}`</mark>`)`

*   <mark style="color:green;">**api\_server**</mark> - _string_

    _`Default: "https://api1.aleph.im"`_

    Target API server


*   <mark style="color:green;">**ref**</mark> - _string_

    _`Default: null`_

    A searchable reference string of your choice to save to the `item_content.ref`.\
    Can be the reference to another post, an address, transaction hash, etc.


*   <mark style="color:green;">**chain**</mark> - _string_

    _`Default: null`_

    The chain used by the sender's account. \
    Value can be `NULS2`, `ETH`, `DOT`, `CSDK`, `SOL`, `AVAX`


*   <mark style="color:green;">**channel**</mark> - _string_

    _`Default: null`_

    Channel of the message. Ideally, an application would decide and use one channel.


*   <mark style="color:green;">**inline**</mark> - _boolean_

    _`Default: true`_

    Should the message be stored as a separate file or inserted inline?&#x20;

    :information\_source: Set it to false for data that could fall under GDPR.&#x20;


*   <mark style="color:green;">**storage\_engine**</mark> - _string_ either `"ipfs"` or `"storage"`

    _`Default: "storage"`_

    Storage engine to use. \
    Possible values: `storage`, `ipfs`


*   <mark style="color:green;">**account**</mark> - _Account_

    _`Default: null`_

    Account to use for signing.

    :information\_source: Needed if you want to send the message. Without it, it is a dry run.

###

### Example: Create post

{% code title="CREATE POST" %}
```javascript
import { posts } from 'aleph-js'

await posts.submit(
  account.address,
  'mytype',
  {'body': 'test'},
  {
    'account': account,
    'channel': 'TEST',
    'api_server': 'https://api2.aleph.im'
  }
 )
```
{% endcode %}

{% code title="RESPONSE" %}
```javascript

{ 
  chain: 'NULS2',
  channel: 'TEST',
  sender: 'NULSd6HgcLR5Yjc7yyMiteQZxTpuB6NYRiqWf',
  type: 'POST',
  time: 1582555614.466,
  item_type: 'inline',
  item_content: '{
    "type":"mytype",
    "address":"NULSd6HgcLR5Yjc7yyMiteQZxTpuB6NYRiqWf",
    "content":{"body":"test"},
    "time":1582555614.466
  }',
  item_hash:'b546f70573a1a91a35a39dbacea0bbfe50847337dcbd995323994535847a6519',
  signature: 'HGnCVb6Rnck5l/BfP93zR3/dvgVToK1yRiPTQrCZjKA/eMiUZwMkaSQFb/FMLvENTtZX804KRERGZxoxU1lEip0=' 
}
```
{% endcode %}
