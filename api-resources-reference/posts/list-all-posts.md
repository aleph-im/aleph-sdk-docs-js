---
description: >-
  Use the .get_post() function to get the latest version of each post sorted by
  most recent
---

# List all posts

### Returns

The function **returns an object** containing a **posts array** as well as **details on the number** of posts and pages returned:

{% code title="Returned object structure" %}
```javascript
{ 
  posts: [ { ... }, { ... }, { ... }], 
  pagination_page: 1,
  pagination_total: 3,
  pagination_per_page: 200,
  pagination_item: 'posts'
 }
```
{% endcode %}

The "post objects" within the array returned are made of a combination of:

* the post message object
* additional details to help reference the original post (original\_...)
* the `post.item_content` object attributes (`type, content, address, time`) are merged in at the top level of the post result

{% code title="Post object in returned array" %}
```javascript
// Regular Post Message
channel:
time:
chain:
sender:
hash_type:
item_content:
  type:
  address:
  content:
  time:
  ref:
item_hash:
item_type:

// Details from original
original_item_hash
original_signature
original_tx_hash
original_type
original_ref
hash

// item_content object merged in
type:
content:
address:
time:
ref:

// Additional info from server
size:
confirmations:
confirmed:

```
{% endcode %}



### Usage

```javascript
import { posts } from "aleph-js"
await posts.get_posts(post_types)

// or with optional parameters
await posts.get_posts(post_types, {pagination: 200, page: 1})
```

###

### Required parameters

| Parameter                                                                    | Description                                                                                                                                                                                                                                                                                                                                                                            |
| ---------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <mark style="color:green;">**post\_types**</mark> - _comma separated string_ | <p>Posts with the "post_types" in the<code>item_content.type</code> as well as any last amended post where the original post type was "post_types"</p><p><br><mark style="background-color:yellow;">The value is a <strong>string</strong> of one type or <strong>multiple types separated with commas without extra space</strong>.</mark> </p><p>ex: <code>"blog,comment"</code></p> |

###

### Optional parameters

In addition to the required parameters above, an object of optional  parameters can be passed following the post\_types to further filter the list returned:

`posts.get_posts(post_type,`<mark style="color:purple;">`{pagination: 200}`</mark>`)`

*   <mark style="color:green;">**api\_server**</mark> - _string_

    _`Default: "https://api1.aleph.im"`_

    Target API server


*   <mark style="color:green;">**pagination**</mark> - _integer_

    _`Default: 200`_

    The number of posts returned per page


*   <mark style="color:green;">**page**</mark> - _integer_

    _`Default: 1`_

    The page to be returned.&#x20;

    ex: page 1 or page 2


*   <mark style="color:green;">**refs**</mark> - _array_

    _`Default: null`_

    Array of Refs listed in the post `item_content.ref`


*   <mark style="color:green;">**addresses**</mark> _- array_

    _`Default: null`_

    Array of addresses listed in the content address (`item_content.address`)

    If multiple addresses are passed, any message with one of the queried addresses in the content address or sender attribute will be returned.


*   <mark style="color:green;">**tags**</mark> - _array_

    _`Default: null`_

    Array of Message content content tag. (`item_content.content.tags`).

    If multiple tags are passed, messages with at least one of the tags present in the content content tags will be returned.


*   <mark style="color:green;">**hashes**</mark> - _array_

    _`Default: null`_

    Array of hashes listed in the item hash (`item_hash`) or transaction hash (`tx_hash`)

###

### Example: Get\_posts

{% code title="GET_POSTS" %}
```javascript
import { posts } from 'aleph-js'
let result = await posts.get_posts('mytype')
```
{% endcode %}

{% hint style="info" %}
In the response, the `item_content` object attributes (`type, content, address, time`) are merged in the post message object to be easily reachable. `Item_content` is still available in the message object as well.
{% endhint %}

{% hint style="info" %}
The `original_` fields are here in case you amended the post.&#x20;
{% endhint %}

{% hint style="info" %}
This function retrieves the latest version of all posts. If a post was updated twice after the original version was created, only the last updated post will show.&#x20;

To see all the changes made to a post, check [the next header item](list-all-posts.md#history-for-a-post) (To retrieve all changes made to a post)
{% endhint %}

{% code title="RESPONSE" %}
```javascript
{ posts:
 [
  {
    _id: { '$oid': '5e53e1deeecd5271f209dbd7' },
    chain: 'NULS2',
    item_hash:
     'b546f70573a1a91a35a39dbacea0bbfe50847337dcbd995323994535847a6519',
    sender: 'NULSd6HgcLR5Yjc7yyMiteQZxTpuB6NYRiqWf',
    type: 'mytype', // MERGED IN FROM ITEM CONTENT
    channel: 'TEST',
    confirmed: true,
    content: { body: 'test' }, // MERGED IN FROM ITEM CONTENT
    item_content:
     '{"type":"mytype",
     "address":"NULSd6HgcLR5Yjc7yyMiteQZxTpuB6NYRiqWf",
     "content":{"body":"test"},
     "time":1582555614.466}',
    item_type: 'inline',
    signature:
     'HGnCVb6Rnck5l/BfP93zR3/dvgVToK1yRiPTQrCZjKA/eMiUZwMkaSQFb/FMLvENTtZX804KRERGZxoxU1lEip0=',
    size: 115,
    time: 1582555614.466, // MERGED IN FROM ITEM CONTENT
    confirmations: [ { chain: 'ETH', height: 6027674, hash: [Object] } ],
    original_item_hash:
     'b546f70573a1a91a35a39dbacea0bbfe50847337dcbd995323994535847a6519',
    original_signature:
     'HGnCVb6Rnck5l/BfP93zR3/dvgVToK1yRiPTQrCZjKA/eMiUZwMkaSQFb/FMLvENTtZX804KRERGZxoxU1lEip0=',
    original_type: 'mytype',
    hash:
     'b546f70573a1a91a35a39dbacea0bbfe50847337dcbd995323994535847a6519',
    address: 'NULSd6HgcLR5Yjc7yyMiteQZxTpuB6NYRiqWf'  // MERGED IN FROM ITEM CONTENT
  },
  {...},
  {
      _id: [Object],
      chain: 'ETH',
      item_hash: '12e789a0a6bdcf56c12c626b1865e00eca9c43ae67bd75260396e4b6e2cb96d3',
      sender: '0xaAFd6626ff5697BDaCCa9A1106097FC5C7C05602',
      type: 'amend',
      channel: null,
      confirmed: false,
      content: [Object],
      item_content: '{"type":"amend","address":"0xaAFd6626ff5697BDaCCa9A1106097FC5C7C05602","content":{"body":"test post written on Aug 17th UPDATED"},"time":1629246696.847,"ref":"f7c01795b42dd7fb3eb300ed5ee726b359705a7afe18d891b6cc2942496d5593"}',
      item_type: 'inline',
      signature: '0x391b59c6508e31b26c360123ffdff9fd50537fe7e04898643b54c5c7d4f39e6e623637abdc449007c20740eb33016881849fded0374655e4ed9425bedb3d2ac71c',
      size: 225,
      time: 1629246696.847,
      confirmations: [Array],
      original_item_hash: 'f7c01795b42dd7fb3eb300ed5ee726b359705a7afe18d891b6cc2942496d5593',
      original_signature: '0x2427296faa119c7744b8cefb76e3dde04d6efc1d2eeeebc2e880022faf6d68ac3afe551c4acb804ae17c2c0c8edde05607e031dc7d60cb62c6561df7518894091b',
      original_type: 'mytype',
      hash: 'f7c01795b42dd7fb3eb300ed5ee726b359705a7afe18d891b6cc2942496d5593',
      address: '0xaAFd6626ff5697BDaCCa9A1106097FC5C7C05602',
      ref: 'f7c01795b42dd7fb3eb300ed5ee726b359705a7afe18d891b6cc2942496d5593'
    }
 ],
 pagination_page: 1,
 pagination_total: 3,
 pagination_per_page: 200,
 pagination_item: 'posts'
}
```
{% endcode %}

### History for a post

{% hint style="danger" %}
**To retrieve all updates made to a specific post** and the original post, **use** [**list all messages**](../messages/list-all-messages.md) **endpoint** rather than list all posts referencing the original item hash.\
\
When using list all posts with the item\_hash reference, any updated posts, including amends of amends will get displayed whether or not they were performed by the account address. \
In addition, the original post cannot be retrieved by this endpoint.&#x20;
{% endhint %}

