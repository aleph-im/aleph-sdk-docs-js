# The aggregate Object

The aggregate object inherits from the [`Message`](../messages/) object structure as follows:

```javascript
{
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
    key:
    address:
    content:
    time:
  item_hash:
  item_type:
}
```

| <mark style="color:green;">**channel**</mark> _- text_                 | Channel of the message. Ideally, an application would decide and use one channel.                                                                                              |
| ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <mark style="color:green;">**time**</mark> _- float_                   | Time the aggregate was created in seconds.                                                                                                                                     |
| <mark style="color:green;">**type**</mark> _- text_                    | <p>Text representing the message object type.</p><p>Value is <code>AGGREGATE</code>.</p>                                                                                       |
|                                                                        |                                                                                                                                                                                |
| <mark style="color:green;">**chain**</mark> _- text_                   | <p>The chain used by the sender's account. <br>Value can be <code>NULS2</code>, <code>ETH</code>, <code>DOT</code>, <code>CSDK</code>, <code>SOL</code>, <code>AVAX</code></p> |
| <mark style="color:green;">**sender**</mark> _- text_                  | Chain address who sent and is signing the Aggregate Message.                                                                                                                   |
|                                                                        | -                                                                                                                                                                              |
| <mark style="color:green;">**hash\_type**</mark> _- optional text_     | Defaults to sha256. This is the only supported value for now.                                                                                                                  |
| <mark style="color:green;">**item\_content**</mark> _- JSON string_    | <p>JSON string representing the content of the aggregate. </p><p>See below for the content of the string.</p>                                                                  |
|                                                                        |                                                                                                                                                                                |
| item\_content.<mark style="color:green;">**key**</mark> _- text_       | The indexed key to reference the value (`item_content.content`) is stored under.                                                                                               |
| item\_content.<mark style="color:green;">**address**</mark> _- text_   | Chain address to associate the `Aggregate` with.                                                                                                                               |
| item\_content.<mark style="color:green;">**content**</mark> _- object_ | Value object stored for the key.                                                                                                                                               |
| item\_content.<mark style="color:green;">**time**</mark> _- float_     | Time the object was created.                                                                                                                                                   |
|                                                                        |                                                                                                                                                                                |
| <mark style="color:green;">**item\_hash**</mark> _- hash_              | The hash of the item\_content encrypted with SHA256.                                                                                                                           |
| <mark style="color:green;">**item\_type**</mark> - _optional text_     | `ipfs`, `inline` or `storage`                                                                                                                                                  |

