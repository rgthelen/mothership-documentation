---
title: "SDK basics"
date: 2018-12-02T23:08:15-05:00
weight: 1
---

## Considerations
SDKs are provided for various platforms and/or programming languages in order to
simplify the adoption of Mothership for configuration. Each SDK generally provides
similar programmatic APIs for access to config values.

In general, it's best practice to load the appropriate Mothership SDK during the
boot phase of the application. That way, configuration values can be used as part
of initialization in addition to value retrieval during general operation.

In runtimes that may not generally support threading (e.g. Node.js), the
Mothership SDK will execute synchronously, blocking execution of the rest of the
system until the configuration has been retrieved.

## Supported languages / runtimes
- [Node.js](/sdks/node)
- [Python](/sdks/python)

Don't see an SDK for your use case? Try our fully public [REST API](/sdks/api)!