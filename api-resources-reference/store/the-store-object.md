# The store object

The store object inherits from the `Message` object's structure as follows:

```javascript
// Message info
channel:
time:
type:

// Sender info
chain:
sender:

// Content
hash_type:
item_content:
  address:
  item_type:
  item_hash:
  time:
item_hash:
item_type:
```

| Attributes                                                                                                   | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <mark style="color:blue;">**channel**</mark> _- text_                                                        | Channel of the message. Ideally, an application would decide and use one channel.                                                                                              |
| <mark style="color:blue;">**time**</mark>** ** _- float_                                                     | Time the post was created.                                                                                                                                                     |
| <mark style="color:blue;">**type**</mark> _- text_                                                           | <p>Text representing the message object type.</p><p>Value is <code>STORE</code></p>                                                                                            |
|                                                                                                              |                                                                                                                                                                                |
| <mark style="color:blue;">**chain**</mark>** ** _- text_                                                     | <p>The chain used by the sender's account. <br>Value can be <code>NULS2</code>, <code>ETH</code>, <code>DOT</code>, <code>CSDK</code>, <code>SOL</code>, <code>AVAX</code></p> |
| <mark style="color:blue;">**sender**</mark> _- text_                                                         | Chain address who sent and is signing the Store Message.                                                                                                                       |
|                                                                                                              | -                                                                                                                                                                              |
| <mark style="color:blue;">**hash\_type**</mark> _- optional text_                                            | Defaults to sha256. This is the only supported value for now.                                                                                                                  |
| <mark style="color:blue;">**item\_content**</mark> _- JSON text_                                             | <p>JSON string representing the content of the store. </p><p>See below for the content of the string.</p>                                                                      |
|                                                                                                              |                                                                                                                                                                                |
| item\_content.<mark style="color:blue;">**address**</mark>** ** _- text_                                     | Chain address to associate the `Store` with.                                                                                                                                   |
| item\_content.<mark style="color:blue;">**item\_type**</mark>** ** _- text_                                  | `storage` or `ipfs`                                                                                                                                                            |
| item\_content<mark style="color:blue;">.</mark><mark style="color:blue;">**item\_hash**</mark>** ** _- text_ | <p>Text representing the file stored. </p><p>It can be used to retrieve the object stored through the retrieve endpoint.</p>                                                   |
| item\_content.<mark style="color:blue;">**time**</mark>** ** _- float_                                       | Time the object was created.                                                                                                                                                   |
|                                                                                                              |                                                                                                                                                                                |
| <mark style="color:blue;">**item\_hash**</mark> _- hash_                                                     | The hash of the item\_content encrypted with SHA256.                                                                                                                           |
| <mark style="color:blue;">**item\_type**</mark> - _optional text_                                            | `ipfs`, `inline` or `storage`                                                                                                                                                  |

