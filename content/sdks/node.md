---
title: "Node.js client"
date: 2018-12-01T00:02:50-05:00
weight: 10
---

## Installation
```
npm i mothership-client
```

## Requirements
- Node.js >= 8.x

## Usage
Since most configuration values are needed during intial bootstrap of an app, this
module should probably be one of the first things your code requires.

Require the module, then initialize it using your environment key.

```
const mothership = require('mothership-client');
const config = mothership.init({
    key: '<config-key>'
});
```

Then simply reference your config like: `config.someKey`;

When you need config in another module, simply require the module and call `get()`:

```
const config = require('mothership-client').get();
```

That's it!

## Future improvements
The module requires an outbound network connection in order to function properly.
This could be problematic in situations where network access to Mothership is 
disrupted for some reason. Eventually, this module will support caching the config
to protect against such problems.

## Contributing
All of our clients are open source! We welcome contributions from the community
whether they be bug fixes, enhancements, suggestions, etc. Feel free to open an
issue or pull request.

This client's source code can be found in its official [Github repository](https://github.com/spicket/mothership-client-nodejs).