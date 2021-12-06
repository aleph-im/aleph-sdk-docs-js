# Push Value

### 1. To Storage

Function stores a content object to storage and returns a hash for the content or null if it couldn't be saved.\
The hash returned corresponds to the `message.item_hash` found in the `Message` object

```javascript
await storage_push(
  value, 
  {
    api_server: 'https://api1.aleph.im'
  }
)
```

### 2. To IPFS

Function stores a content object to ipfs and returns a hash for the content or null if it couldn't be saved.

The hash returned corresponds to the `message.item_hash` found in the `Message` object

```javascript
await ipfs_push(
  value, 
  {
    api_server: 'https://api1.aleph.im'
  }
)
```
