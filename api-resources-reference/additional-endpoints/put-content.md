# Put Content

The .push\_content() function:&#x20;

* serializes or saves the content object of the message to either ipfs or storage server&#x20;
* adds the item\_hash from the content to the message object.

All parameters are required.&#x20;

`Inline_requested` can be either true or false. If true, the content will be serialized otherwise the content is saved to:&#x20;

* ipfs if "ipfs" is passed as `storage_engine`&#x20;
* storage otherwise.

```javascript
await put_content(
  message,
  content,
  inline_requested,
  storage_engine,
  api_server
)
```
