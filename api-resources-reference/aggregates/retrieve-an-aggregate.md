# Retrieve one key

### Returns

Retrieves the content value for the queried key for an address. If no aggregate for this address and the key is found, null will be returned.



### Usage

```javascript
import { aggregates } from 'aleph-js'

await aggregates.fetch_one(address, key)
```



### Required parameters

| Parameter                                                     | Description                                          |
| ------------------------------------------------------------- | ---------------------------------------------------- |
| <mark style="color:green;">**address**</mark>** ** - _string_ | The chain `address` the `Aggregate` was created for. |
| <mark style="color:green;">**key**</mark>** ** - _string_     | The `key` the `Aggregate` was created for.           |

###

### Optional parameters

In addition to the required parameters above, an object of optional  parameters can be passed following the key like so:

`aggregates.fetch_one(address, key,`<mark style="color:purple;">`{api_server: "https://api2.aleph.im"}`</mark>`)`

*   <mark style="color:green;">**api\_server**</mark> - _string_

    _`Default: "https://api1.aleph.im"`_

    Target API server

###

### Example

{% code title="RETRIEVE AGGREGATE" %}
```javascript
import { aggregates } from 'aleph-js'

await aggregates.fetch_one(account.address, 'mykey')
```
{% endcode %}

Aleph returns the content for the key and the address queried if one is found.

{% code title="RESPONSE" %}
```javascript
// If an aggregate is found for the key and the address
// The content for the key is returned
{ 'a': 1, 'b': 2 }

// If none are found - null is returned
null
```
{% endcode %}

