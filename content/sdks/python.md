---
title: "Python"
date: 2018-12-02T22:52:40-05:00
weight: 20
---

## Installation
```
pip3 install mothership-client
```

## Requirements
- Python 3

## Usage
Since most configuration values are needed during intial bootstrap of an app, this
module should probably be one of the first things your code imports.

Import the module, then initialize it using your environment key.

```
import mothership.client
config = mothership.client.init({
  'key': '<config-key>'
});
```

Then simply reference your config like: `config['someKey']`;

When you need config in another module, simply import the `mothership` module and 
call `mothership.get()` to grab the entire config:

```
import mothership
config = mothership.get();
```

