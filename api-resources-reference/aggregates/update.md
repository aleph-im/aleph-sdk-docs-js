# Update one key

Use the [create endpoint](create-an-aggregate.md) to update a specific key content from an existing `Aggregate`.

Since creating an `Aggregate` message mutates the value of the specific key, if the key exists, the value object will be updated (mutated) with the object you are saving.

### Example

To illustrate the update process, below we are creating an aggregate, updating it, and showing you what the aggregate looks like through the calls.

```javascript
import { aggregates } from 'aleph-js'

// CREATE NEW AGGREGATE WITH KEY "MY KEY" --------------------------
await aggregates.submit(
  account.address, 
  'mykey', 
  {'a': 1, 'b': 2}, 
  {'account': account, 'channel': 'TEST'}
)
// >> Returns the Aggregate object with the item_content key and
// content that were passed in



// RETRIEVE THE KEY "MYKEY" ----------------------------------------
await aggregates.fetch_one(account.address, 'mykey')

// >> { 'a': 1, 'b': 2 }

---------------------------------------------------------------------

// UPDATE THE KEY "MYKEY" -------------------------------------------
await aggregates.submit(
  account.address, 
  'mykey', 
  {'a': 3, 'c': 5}, 
  {'account': account, 'channel': 'TEST'}
)

// >> Returns the Aggregate object with the item_content key and
// content that were passed in
// {
//   chain: 'ETH',
//   channel: 'TEST',
//   sender: '<ADDRESS WOULD DISPLAY HERE>',
//   type: 'AGGREGATE',
//   time: 1629242218.859,
//   item_type: 'inline',
//   item_content: '{"address":"<ADDRESS WOULD DISPLAY HERE>",
//                    "key":"mykey",
//                    "content":{'a': 3, 'c': 5},
//                    "time":1629242218.859}',
//   item_hash: 'd1a71b97cff51d9a1623a85c847675e85b36b5eb30239a715249b17698d6b7dc',
//   signature: '0xdc7f26dd94f58b50cba058c6c47dc57f750b83149b94e5007a83f7feed11252774b620593c17daa7cf39ec9206d150a53b4bbbac8a7f1629894d30d583b742c61c'
// }

---------------------------------------------------------------------

// RETRIEVE THE KEY------- -------------------------------------------
await aggregates.fetch_one(account.address, 'mykey')

// >> { 'a': 3, 'b': 2, 'c': 5 }
```

