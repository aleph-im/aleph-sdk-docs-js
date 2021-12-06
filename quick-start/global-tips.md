# Global tips

### Account instantiated

The API Resources Reference usage and example calls assume you have an account already instantiated. See the [account reference](../api-resources-reference/chain-accounts/) on how to do so.



### Asynchronous functions

```python
import { aggregates } from 'aleph-js'

await aggregates.fetch(...)
```



### Functions

All functions throughout the API have required arguments (if any needed) followed by an optional object of additional parameters to be used in the function call.

```python
# Examples of creating an aggregate

aggregates.submit(address, key, content, {'account': account, 'channel': channel})
```



### api\_server

Any core channel node multi-address can be used as an api\_server. You can find a list of core nodes [here](https://account.aleph.im) and their multi-address in their "info".

Example of one of the nodes multi-address that can be found on [https://account.aleph.im/](https://account.aleph.im/#/): `/ip4/`<mark style="color:purple;">**`65.21.141.116`**</mark>`/tcp/4025/p2p/QmSuf7N2753dAeiwXmXVPdNW1JBvzhb43t6wXVaR75w64S)`.&#x20;

Api Server Url would look like this:

`https://<ip-address>` or `http://<ip-address>:4024`

{% hint style="info" %}
<mark style="color:blue;">\[Future Release]</mark> The Aleph will provide load-balancing in the future so the users don't have to pick an api\_server.&#x20;
{% endhint %}

Reasons for choosing a different api\_server:

* The latency decreases the closer the dApp is from the server
* Some offer HTTPS others don't (yet).&#x20;
