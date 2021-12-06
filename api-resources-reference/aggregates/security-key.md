---
description: Allows accounts to post on behalf of other addresses
---

# Security key

Inside most Messages there is an “address” field. This is the address for which the message applies (for which address to apply this aggregate, who posted that item…).

The pyaleph client validates that the message sender (the one signing the message) has the right to publish on this address's behalf.

1. obvious case: if the sender == the content address, it is authorized.
2. the “security” key in the address aggregate has an entry for this address

### <mark style="color:blue;">Security</mark>  key with <mark style="color:blue;">authorizations</mark> subkey in value object <a href="#security-key-with-authorizations-subkey-in-value-object" id="security-key-with-authorizations-subkey-in-value-object"></a>

This key is a special case in the Aggregate system. It can only be changed by sending an AGGREGATE message on the “security” channel.

For now, only the address itself (sender == content.address) has the right to send an AGGREGATE message on this channel (“security”) with this key (“security”). This behavior might change in the future.&#x20;

The value to be created for the security key:

* is an object
* has the authorizations subkey
* the authorizations subkey value is an array of objects structured as follows

```
{'authorizations': [
  {
    'address': '<ADDRESS_TO_AUTHORIZE>',
    'types': ['AGGREGATE'],
    'post_types': ['chat'],
    'aggregate_keys': ['testkey', 'preferences'],
    'chain': ['ETH'],
    'channels': ['MYCHANNEL']
  }
]}
```

> If some filter is set only messages that match the filter set (all options selected) will be accepted except for:
>
> * post\_types only apply to POST Messages,
> * aggregate\_keys only apply to AGGREGATE Messages

*   <mark style="color:green;">**address**</mark> _- <mark style="color:red;">required</mark>_

    account address to authorize to write on behalf of the aggregate's address
*   <mark style="color:green;">**types**</mark> _- optional_

    Can be Post, Aggregate, or Store; Only these types will be accepted from this address
*   <mark style="color:green;">**post\_types**</mark> _- optional_

    Only those post types will be writeable by the address
*   <mark style="color:green;">**aggregate\_keys**</mark> _- optional_

    Only those keys will be writeable by the address
*   <mark style="color:green;">**chain**</mark> _- optional_

    Only accept the passed address on a specific chain
*   <mark style="color:green;">**channels**</mark> _- optional_

    Only the messages of these types on these channels will be accepted
