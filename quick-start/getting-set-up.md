---
description: >-
  Get up and running with our Aleph-js client library and start developing your
  Aleph integration.
---

# Getting Setup

{% hint style="success" %}
Integrating with Aleph requires two steps:

1. Install the client library in your application so that you can interact with the Aleph API
2. Make an API request
{% endhint %}

### 1. Import Aleph-js in your dApp

We provide an official javascript library. Open your terminal window and navigate into your project's root folder and install the library:

```
$ yarn add aleph-js
```

### 2. Make an API request

To check the integration is working, make a basic API request within your project.&#x20;

Here we are retrieving all Posts that were made with a post type of "chat" and with a reference of "hall". We'll go into more details about post types and references in the [Post Resource Reference](../api-resources-reference/posts/).

{% code title="index.js" %}
```javascript
import { posts } from 'aleph-js'

var api_server = 'https://api2.aleph.im'

await posts.get_posts(
  'chat', 
  {
    'refs': ['hall'], 
    'api_server': api_server
  }
)
```
{% endcode %}

Aleph returns an object with a `posts` key containing an array of all the posts that were made with the query params we requested.

The response should look like this:&#x20;

```javascript
{
  posts: [
    {
      _id: { '$oid': '60f1da898499cc7baac3f484' },
      chain: 'ETH',
      item_hash: 'd1316434dba36f0754a067bf9a1b1c1bef55d754fe58567091b1726e892f9cfd',
      sender: '0xfE11ef2890Ac034e2320df5b62B8F3366D3B42D5',
      type: 'chat',
      channel: 'TEST',
      confirmed: true,
      content: { body: 'jhgjhgjghhj\n' },
      item_content: '{"type":"chat","address":"0xfE11ef2890Ac034e2320df5b62B8F3366D3B42D5","content":{"body":"jhgjhgjghhj\\n"},"time":1626462857.641,"ref":"hall"}',
      item_type: 'inline',
      signature: '0x219c9ef32f268be4d5a81b5dcf748942796c336d555553f633e1804f8764778b4bf51da36696fddf2ebfa946a34eb3e9b15a2c1a2e2ed5c800382d8a650d97d11c',
      size: 140,
      time: 1626462857.641,
      confirmations: [
        {
          chain: 'ETH',
          height: 12839885,
          hash: '0x3cd841f4303542ea2664a7f30254e5cdf83334f318b108c7ec228af163e22abf'
        }
      ],
      original_item_hash: 'd1316434dba36f0754a067bf9a1b1c1bef55d754fe58567091b1726e892f9cfd',
      original_signature: '0x219c9ef32f268be4d5a81b5dcf748942796c336d555553f633e1804f8764778b4bf51da36696fddf2ebfa946a34eb3e9b15a2c1a2e2ed5c800382d8a650d97d11c',
      original_type: 'chat',
      hash: 'd1316434dba36f0754a067bf9a1b1c1bef55d754fe58567091b1726e892f9cfd',
      original_ref: 'hall',
      address: '0xfE11ef2890Ac034e2320df5b62B8F3366D3B42D5',
      ref: 'hall'
    },
    { ... },
    ... 100 more items
    ]
  }
```

### 3. Next Steps

Once you have successfully made an API _GET_ request, **connect a blockchain account and write to the aleph.im network (**[Posting to the Network](posting-to-the-network.md)).
