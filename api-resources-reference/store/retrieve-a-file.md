# Retrieve a file



Files can be retrieved **using the item\_hash** returned after creating the file in the api server **or** with a **request to the following endpoint**:



### Usage

```javascript
import { store } from 'aleph-js'

await store.retrieve(item_hash)
```



### Required parameters

| Parameter                                                   | Description                                                             |
| ----------------------------------------------------------- | ----------------------------------------------------------------------- |
| <mark style="color:green;">**item\_hash**</mark> - _string_ | `content.item_hash` generated from  creating the file on the api server |

###

### Optional parameters

In addition to the required parameters above, an object of optional  parameters can be passed following the item\_hash like so:

`store.submit(item_hash,`<mark style="color:purple;">`{api_server: "https://api2.aleph.im"}`</mark>`)`

*   <mark style="color:green;">**api\_server**</mark> - _string_

    _`Default: "https://api1.aleph.im"`_

    API server accepting files. Examples: "https://api1.aleph.im", "https://api2.aleph.im"

###

### Example: Retrieve from endpoint

{% code title="REQUEST" %}
```javascript
import { store } from 'aleph-js'

var my_buffer = await store.retrieve(
  'QmQkv43jguT5HLC8TPbYJi2iEmr4MgLgu4nmBoR4zjYb3L',
  {
    api_server: 'https://api2.aleph.im'
  }
)
```
{% endcode %}

{% code title="RESPONSE" %}
```javascript
<Buffer 54 68 69 73 20 69 73 20 6a 75 73 74 20 61 20 74 65 73 74 2e>

// Buffer can be converted back to a string like so:
my_buffer.toString('utf8')
// => 'This is just a test.'
```
{% endcode %}

###

### Example: Retrieve from an API server

If stored on aleph storage:

```javascript
// https://<FILE API_SERVER>/api/v0/storage/raw/<FILE ITEM HASH HERE>

https://api2.aleph.im/api/v0/storage/raw/QmQkv43jguT5HLC8TPbYJi2iEmr4MgLgu4nmBoR4zjYb3L
```

If stored on ipfs compatible server, the file is also available on:&#x20;

```javascript
// https://ipfs.io/ipfs/<FILE ITEM HASH HERE>

https://ipfs.io/ipfs/QmQkv43jguT5HLC8TPbYJi2iEmr4MgLgu4nmBoR4zjYb3L
```

