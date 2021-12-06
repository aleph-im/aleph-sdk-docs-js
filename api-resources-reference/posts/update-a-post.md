---
description: Uses the create post endpoint to update the original post.
---

# Update a post

Update the specific post by [creating a new post](create-a-post.md) with the `post_type` `amend` and the original post __ `item_hash` as the `ref` along with the new `content.`

```javascript
await posts.submit(
  account.address, 
  'amend',
  {<UPDATED CONTENT OBJECT >},
  {
    'ref': <ORIGINAL POST ITEM_HASH HERE>,
    'account': account,
    'channel': 'TEST',
    'api_server: 'https://api2.aleph.im'
  }
 )
```

```javascript
await aleph.posts.submit(
    account.address, 
    'amend', 
    {"body":"test post written on Aug 17th UPDATED"}, 
    {
        'ref': 'f7c01795b42dd7fb3eb300ed5ee726b359705a7afe18d891b6cc2942496d5593', 
        'account': account
    }
)
```

```javascript
{
  chain: 'ETH',
  channel: null,
  sender: '0xaAFd6626ff5697BDaCCa9A1106097FC5C7C05602',
  type: 'POST',
  time: 1629246696.847,
  item_type: 'inline',
  item_content: '{"type":"amend","address":"0xaAFd6626ff5697BDaCCa9A1106097FC5C7C05602","content":{"body":"test post written on Aug 17th UPDATED"},"time":1629246696.847,"ref":"f7c01795b42dd7fb3eb300ed5ee726b359705a7afe18d891b6cc2942496d5593"}',
  item_hash: '12e789a0a6bdcf56c12c626b1865e00eca9c43ae67bd75260396e4b6e2cb96d3',
  signature: '0x391b59c6508e31b26c360123ffdff9fd50537fe7e04898643b54c5c7d4f39e6e623637abdc449007c20740eb33016881849fded0374655e4ed9425bedb3d2ac71c'
}
```
