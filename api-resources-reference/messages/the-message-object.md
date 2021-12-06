# The message object

```
// Message info
type:
channel:
time:

// Sender info
sender:
chain:

// Content
item_hash:
item_content:
item_type:
hash_type:
```

| Attributes                                                               | Description                                                                                                                                                                                                                                                                                                                             |
| ------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <mark style="color:blue;">**channel**</mark>** ** _- text_               | Channel of the message. Ideally, an application would decide and use one channel.                                                                                                                                                                                                                                                       |
| <mark style="color:blue;">**time**</mark> _- float_                      | Time the message was created.                                                                                                                                                                                                                                                                                                           |
| <mark style="color:blue;">**type**</mark> _- text_                       | <p>Text representing the message object type.</p><p>Value is one of <code>POST</code>, <code>AGGREGATE</code> or <code>STORE</code></p>                                                                                                                                                                                                 |
|                                                                          |                                                                                                                                                                                                                                                                                                                                         |
| <mark style="color:blue;">**chain**</mark> _- text_                      | <p>The chain used by the sender's account. <br>Value can be <code>NULS2</code>, <code>ETH</code>, <code>DOT</code>, <code>CSDK</code>, <code>SOL</code>, <code>AVAX</code></p>                                                                                                                                                          |
| <mark style="color:blue;">**sender**</mark>** ** _- text_                | Chain address who sent and is signing the Aggregate Message.                                                                                                                                                                                                                                                                            |
|                                                                          | -                                                                                                                                                                                                                                                                                                                                       |
| <mark style="color:blue;">**hash\_type**</mark> _- optional text_        | Defaults to sha256. This is the only supported value for now.                                                                                                                                                                                                                                                                           |
| <mark style="color:blue;">**item\_content**</mark>** ** _- JSON string_  | <p>JSON string representing the content of the message. </p><p>The structure of the item_content depends on the type of message created. See <a href="../posts/the-post-object.md"><code>POST</code></a>, <a href="../aggregates/the-aggregate-object.md"><code>AGGREGATE</code></a> or <a href="../store/"><code>STORE</code></a>.</p> |
| <mark style="color:blue;">**item\_hash**</mark> _- hash_                 | The hash of the item\_content encrypted with SHA256.                                                                                                                                                                                                                                                                                    |
| <mark style="color:blue;">**item\_type**</mark> _- optional string_      | `ipfs`, `inline` or `storage`                                                                                                                                                                                                                                                                                                           |
