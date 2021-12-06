# Push Files

### 1. To Storage

The function returns the file\_hash for the stored file or null if the file could not be stored.

Fileobject is required. Api\_server is optional and defaults to aleph api1.

```javascript

await storage_push_file(
  fileobject, 
  {
    api_server: 'https://api1.aleph.im'
  }
)
```

### 2. To IPFS

The function returns the file\_hash for the stored file or null if the file could not be stored.

Fileobject is required. Api\_server is optional and defaults to aleph api1.

```javascript

await ipfs_push_file(
  fileobject, 
  {
    api_server: 'https://api1.aleph.im'
  }
)
```
