---
description: Call the .submit() function to create a store object and save a file.
---

# Create a file

### Returns

The function returns the store object that was just created with a couple of extra attributes.

### Usage

```javascript
import { store } from 'aleph-js'

await store.submit(address, {file_hash: null, storage_engine: 'storage', account: null})
```

### Required parameters

| Parameter                                                | Description              |
| -------------------------------------------------------- | ------------------------ |
| <mark style="color:green;">**address**</mark> - _string_ | Most likely your address |



### Other parameters

In addition to the required parameters above, an object of optional parameters can be passed following the address like so:

`store.submit(address,`<mark style="color:purple;">`{api_server: "https://api2.aleph.im"}`</mark>`)`

*   <mark style="color:green;">**file\_hash**</mark> _- string -_ <mark style="color:red;">**REQUIRED if no**</mark><mark style="color:red;">** **</mark><mark style="color:red;">**`fileobject`**</mark>\
    _`Default: None`_\
    file\_hash is ignored if a fileobject is passed in.\
    Use this if you already have uploaded the file to storage or ipfs yourself.


*   <mark style="color:green;">**fileobject**</mark> _- bytes -_ <mark style="color:red;">**REQUIRED if no**</mark><mark style="color:red;">** **</mark><mark style="color:red;">**`file_hash`**</mark>\
    _`Default: None`_

    The file you want to store.

    This takes precedence over the `file_hash`\

*   <mark style="color:green;">**api\_server**</mark> _- string_\
    _`Default: "https://api1.aleph.im`_\
    Select an API server accepting files.

    ex: [https://api1.aleph.im](https://api2.aleph.im) and "[https://api2.aleph.im](https://api2.aleph.im)" are two available API servers accepting files.\

* <mark style="color:green;">**chain**</mark> _- string_\
  _`Default: null`_\
  The chain used by the sender's account.\
  Value can be `NULS2`, `ETH`, `DOT`, `CSDK`, `SOL`, `AVAX`.\

* <mark style="color:green;">**channel**</mark> _- string_\
  _`Default: null`_\
  Channel of the message. Ideally, an application would decide and use one channel.\

* <mark style="color:green;">**storage\_engine**</mark> _- string_\
  _`Default: "storage"`_\
  Storage engine to use.\
  Use "storage" for aleph.im built-in storage or "ipfs" for an ipfs compatible storage. Possible values: `storage`, `ipfs`\

*   <mark style="color:green;">**account**</mark> - _Account_

    `Default: null`

    Account to use for signing.

    :information\_source: <mark style="background-color:yellow;">Needed if you want to send the message. Without it, it is a dry run.</mark>\

*   <mark style="color:green;">**extra\_fields**</mark> _- object_\
    _`Default: {}`_

    <mark style="background-color:yellow;">Any custom fields to save alongside the file in the message item\_content.</mark>\ <mark style="background-color:yellow;"></mark>

{% hint style="info" %}
If you've already stored a file in an IPFS storage, you can still create a file using the .submit() to "pin" it, by passing the:\
{ ..., storage\_engine: "**ipfs**" , file\_hash: \_ **<**\_**ipfs item hash>** , ... }

See how to [push a file in IPFS file storage](../additional-endpoints/storage\_push\_file.md#2-to-ipfs).
{% endhint %}

### Aleph file storage example

{% code title="REQUEST" %}
```javascript
// Creating a file we need to store

// Tthis file object can also be obtained 
// from an upload form input (if you don't want to create it 
// programmatically).

var myfile = new File(
  ["This is just a test."],
  "test.txt",
  {type: "text/plain"})
        
await store.submit(
  account.address,
  {
    'fileobject': myfile,
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
  "chain": "NULS2",
  "channel": "TEST",
  "sender": "NULSd6HgcLR5Yjc7yyMiteQZxTpuB6NYRiqWf",
  "type": "STORE",
  "time": 1582562109.316,
  "item_type": "inline",
  "item_content": "{\"address\":\"NULSd6HgcLR5Yjc7yyMiteQZxTpuB6NYRiqWf\",\"item_type\":\"storage\",\"item_hash\":\"11dfc1e6953dac4bd02d8faa06878f51eea3421fa58d7148e808d425cff2a921\",\"time\":1582562109.316}",
  "item_hash": "fde8effa834d12ce127e7f82ac317639505af36b34b3b40a2d108b9e1bfb3b2b",
  "signature": "HLzL+XlkNkCOo8UReVo7Qh3mMzVn5/imD9J5xbzBejS4b9BjKDTiGfcnhJQPGd47lcmPg3jtBcVOTPNSPVwb3Ws=",
  "content": {
    "address": "NULSd6HgcLR5Yjc7yyMiteQZxTpuB6NYRiqWf",
    "item_type": "storage",
    "item_hash": "11dfc1e6953dac4bd02d8faa06878f51eea3421fa58d7148e808d425cff2a921",
    "time": 1582562109.316
  }
}
```
{% endcode %}

{% hint style="info" %}
In the response, **content.item\_hash** can be used to **retrieve** the stored file **via** a **direct URL** as follow:

**https://\<API SERVER URL>/api/v0/storage/raw/\<FILE ITEM HASH HERE>**

Api server can be any api server accepting files.
{% endhint %}

### IPFS file storage example

```javascript
var msg = await store.submit(
  account.address,
  {
    'fileobject': myfile,
    'account': account,
    'channel': 'TEST',
    'storage_engine': 'ipfs',
    'api_server': 'https://api2.aleph.im'
  }
)
msg.content.item_hash
// => QmQkv43jguT5HLC8TPbYJi2iEmr4MgLgu4nmBoR4zjYb3L

To retrieve file via direct url:

https://ipfs.io/ipfs/QmQkv43jguT5HLC8TPbYJi2iEmr4MgLgu4nmBoR4zjYb3L

https://api2.aleph.im/api/v0/storage/raw/QmQkv43jguT5HLC8TPbYJi2iEmr4MgLgu4nmBoR4zjYb3L
```

{% hint style="info" %}
Files are available at two URLs in this case:

* The IPFS URL: **https://ipfs.io/ipfs/\<FILE ITEM HASH HERE>**
* The API server URL: **https://\<FILE API\_SERVER>/api/v0/storage/raw/\<FILE ITEM HASH HERE>**
{% endhint %}
