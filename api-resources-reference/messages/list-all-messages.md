# List all messages

### Returns

Returns a list of Messages that have previously been created for the queried parameters.

**Only one msgType can be queried at a time**. All other **query parameters are arrays** of one or multiple values.



### Usage

```javascript
import { messages } from 'aleph-js'

await messages.get_messages()

// Or with optional parameters
await messages.get_messages({pagination: 200, tags: ["first_tag", "second_tag"]})
```

### Required parameters

No parameters are required.&#x20;

### Optional parameters

An object of options to further filter the list of posts returned.

*   <mark style="color:green;">**api\_server**</mark> - _string_

    _`Default: "https://api1.aleph.im"`_

    Target API server


*   <mark style="color:green;">**pagination**</mark> - _integer_

    _`Default: 200`_

    The number of messages returned per page


*   <mark style="color:green;">**page**</mark> - _integer_

    _`Default: 1`_

    The number of pages returned


*   <mark style="color:green;">**message\_type**</mark> - _string: "POST", "AGGREGATE" or "STORE"_

    _`Default: null`_

    A string representing the Message type. Value can be: `POST`, `AGGREGATE`, or `STORE`&#x20;


*   <mark style="color:green;">**content\_types**</mark> - _array_

    _`Default: null`_

    Array of Message content types (`item_content.type`)


*   <mark style="color:green;">**refs**</mark> - _array_

    _`Default: null`_

    Array of Refs listed in content refs (`item_content.ref`)


*   <mark style="color:green;">**addresses**</mark> _- array_

    _`Default: null`_

    Array of addresses listed in the content address (`item_content.address`) **or** sender (`sender`) attribute of the Message.&#x20;

    If multiple addresses are passed, any message with one of the queried addresses in the content address or sender attribute will be returned.


*   <mark style="color:green;">**tags**</mark> - _array_

    _`Default: null`_

    Array of Message content content tag. (`item_content.content.tags`).

    If multiple tags are passed, messages with at least one of the tags present in the content content tags will be returned.


*   <mark style="color:green;">**hashes**</mark> - _array_

    _`Default: null`_

    Array of hashes listed in the item hash (`item_hash`) or transaction hash (`tx_hash`)



### Historical changes for a post

