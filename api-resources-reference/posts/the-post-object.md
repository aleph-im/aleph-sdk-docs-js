# The post object

The post object inherits from the `Message` object's structure as follows:

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
  type:
  address:
  content:
  time:
  ref:
item_hash:
item_type:
```

| Attributes                                                                                                                                                                             | Description                                                                                                                                                                     |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <mark style="color:blue;">**channel**</mark> - _text_                                                                                                                                  | Channel of the message. Ideally, an application would decide and use one channel.                                                                                               |
| <mark style="color:blue;">**time**</mark> _- float_                                                                                                                                    | Time the post was created in seconds.                                                                                                                                           |
| <mark style="color:blue;">**type**</mark> _- text_                                                                                                                                     | <p>Text representing the message object type.</p><p>Value is<code>POST</code></p>                                                                                               |
|                                                                                                                                                                                        |                                                                                                                                                                                 |
| <mark style="color:blue;">**chain**</mark>** ** _- text_                                                                                                                               | <p>The chain used by the sender's account. <br>Value can be <code>NULS2</code>, <code>ETH</code>, <code>DOT</code>, <code>CSDK</code>, <code>SOL</code>, <code>AVAX</code></p>  |
| <mark style="color:blue;">**sender**</mark> _- text_                                                                                                                                   | Chain address who sent and is signing the Post Message.                                                                                                                         |
|                                                                                                                                                                                        | -                                                                                                                                                                               |
| <mark style="color:blue;">**hash\_type**</mark> _- optional text_                                                                                                                      | Defaults to sha256. This is the only supported value for now.                                                                                                                   |
| <mark style="color:blue;">**item\_content**</mark>** ** _- JSON text_                                                                                                                  | <p>JSON string representing the content of the aggregate. </p><p>See below for the content of the string.</p>                                                                   |
|                                                                                                                                                                                        |                                                                                                                                                                                 |
| item\_content.<mark style="color:blue;">**type**</mark>** ** _- text_                                                                                                                  | <p>A string of your choice representing what the post is. Should be simple and lowercase.</p><p>For instance, for a blog post you could have:</p><p>a "blog" or a "comment"</p> |
| item\_content.<mark style="color:blue;">**address**</mark>** ** _- text_                                                                                                               | Chain address to associate the `Post` with.                                                                                                                                     |
| item\_content.<mark style="color:blue;">**content**</mark>** -** _object_                                                                                                              | <p>An object containing the content you want to save. <br>For instance, for a blog post you could have:<br>{ body: "This is my content" }</p>                                   |
| item\_content<mark style="color:blue;">.</mark><mark style="color:blue;">**content.tags**</mark> <mark style="color:blue;"></mark>_<mark style="color:blue;"></mark> - optional array_ | If tags were passed in on post create or update you could have: { tags: \["my\_first_\__tag"] }                                                                                 |
| item\_content.<mark style="color:blue;">**time**</mark>** ** _- float_                                                                                                                 | Time the object was created.                                                                                                                                                    |
| item\_content<mark style="color:blue;">.</mark><mark style="color:blue;">**ref**</mark>** ** _- text_                                                                                  | <p>A text representing a reference.</p><p>Present if a ref was passed during creation.</p>                                                                                      |
|                                                                                                                                                                                        |                                                                                                                                                                                 |
| <mark style="color:blue;">**item\_hash**</mark> _- hash_                                                                                                                               | The hash of the item\_content encrypted with SHA256.                                                                                                                            |
| <mark style="color:blue;">**item\_type**</mark> - _optional text_                                                                                                                      | `ipfs`, `inline` or `storage`                                                                                                                                                   |

