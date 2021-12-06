# Broadcast Message

### 1. Message

The message object should be one of aggregate, post or store. Api\_server is optional and defautls to aleph api1.

```javascript
await broadcast(
  message, 
  {
    api_server: 'https://api1.aleph.im'
  }
)
```

### 2. Sign Message & Broadcast

Message, account and api\_server are required.

```javascript
await sign_and_broadcast(
  message, 
  account,
  api_server
)
```

