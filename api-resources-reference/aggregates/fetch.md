# List all keys & values

### Returns

A list of aggregate keys and corresponding values found for the address.

{% hint style="info" %}
Up to 1,000 results will be returned.
{% endhint %}



### Usage

```javascript
import { aggregates } from 'aleph-js'

await aggregates.fetch(address)

// Or with an optional object of additional parameters
await aggregates.fetch(address, {keys: ["my_key"]})
```



### Required parameters

| Parameter                                                | Description                                          |
| -------------------------------------------------------- | ---------------------------------------------------- |
| <mark style="color:green;">**address**</mark> - _string_ | Address for which the aggregates should be returned. |



### Optional parameters

In addition to the required parameters above, an object of optional  parameters can be passed following the address parameter like so:

`aggregates.fetch(address,`<mark style="color:purple;">`{api_server: "https://api2.aleph.im"}`</mark>`)`

*   <mark style="color:green;">**api\_server**</mark> - _string_

    _`Default: "https://api1.aleph.im"`_

    Target API server


*   <mark style="color:green;">**keys**</mark> - _array_

    _`Default: null`_

    If none are passed, all keys and their content found for the address will be returned.

    If some are passed, only the key value pairs with those keys will be returned for the address_`.`_



### Example

{% code title="RETRIEVE AGGREGATE" %}
```javascript
import { aggregates } from 'aleph-js'

await aggregates.fetch(account.address)
```
{% endcode %}

In this example, all key-value pairs for the address are returned.

{% code title="RESPONSE" %}
```javascript
// If an aggregates are found for the address
// The key-value pairs are returned
{ mykey: { a: 3, b: 2, c: 5 }, 
  mysecondkey: { a: 1, d:6 } 
}

// If none are found - null is returned
null
```
{% endcode %}

