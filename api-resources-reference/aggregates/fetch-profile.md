# Retrieve the profile key

### Returns

Retrieves the aggregate for the address with the key "profile" and returns the content value if an aggregate is found. Otherwise, returns null.



### Usage

```javascript
import { aggregates } from 'aleph-js'
await aggregates.fetch_profile(address)
```



### Required parameters

| <mark style="color:green;">**address**</mark> - _string_ | Chain `address` the `Aggregate` was created for. |
| -------------------------------------------------------- | ------------------------------------------------ |



### Optional parameters

In addition to the required parameters above, an object of optional  parameters can be passed following the address like so:

`aggregates.fetch_profile(key,`<mark style="color:purple;">`{api_server: "https://api2.aleph.im"}`</mark>`)`

*   <mark style="color:green;">**api\_server**</mark> - _string_

    _`Default: "https://api1.aleph.im"`_

    Target API server



### Example

If you have previously created an aggregate with the key "profile", you would query it as followed:

{% code title="RETRIEVE AGGREGATE WITH KEY PROFILE" %}
```javascript
import { aggregates } from 'aleph-js'

await aleph.aggregates.fetch_profile(account.address)
```
{% endcode %}

Aleph returns the content for the "profile" key and the address queried if one is found.

{% code title="RESPONSE" %}
```javascript
// Example response

{ username: 'tallboy' }
```
{% endcode %}
