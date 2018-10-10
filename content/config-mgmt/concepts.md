---
title: "Concepts"
date: 2018-10-09T03:16:05Z
draft: false
---

Artifacts in Mothership are centered around two concepts: apps and environments. Each plays a role in how
configurations are loaded and applied to a running client. Throughout this documentation, a "client" refers
to any remote endpoint that would retrieve a configuration. This could be anything having access to an HTTP
client and the ability to parse an output format that Mothership supports. Clients may include: microservices,
serverless functions, mobile devices, internet of things devices, embedded systems, and so on. See the SDK
documentation for a list of officially supported platforms. If a client supporting your particular use case
doesn't exist, the REST API is always available.

### Apps
An **app** is intended to be a logical set of configuration key / value pairs that will be used by a client.
Values should typically relate to one another in some sort of logical unit (e.g. all used by a single microservice).
Apps are isolated from one another in they do not explicitly or implicitly share values with other apps. It's best
to create one app per consuming "thing" (e.g. a Docker container).

Every app automatically includes a "base" environment. More on this later.

### Environments
**Environments** represent differences in configurations across the same app. For example, in a microservice deployment
using containers, each place where a container is deployed would likely constitute an environment (e.g. dev, staging,
production, etc).

Apps and environments are intended to work together. The **base** environment should contain common values that apply
to every environment within the app. It could also include sane defaults that may not necessarily be overridden by
another environment.

When a client requests a config, it does so by specifying an environment. Mothership will load both the base environment
and the target environment. The target environment will be deeply merged over top of the base environment, overridding any
matching keys. Next, any template pointers will be will be resolved. Finally, the compiled configuration for the environment
will be returned to the client.

### Template pointers
Sometimes portions of a config value stay the same while other parts of the value change (e.g. a URL). For cases like these,
Mothership supports template pointers within any string value. Using dot notation, you can reference any other key in the
config. Template pointers are denoted by the enclosing string `${ }`.

For example, given the configuration block:
```
{
    "domains": {
        "main": "myurl.com"
    },
    "urls": {
        "main": "https://${domains.main}"
    }
}
```
`${domains.main}` would evaluate to `myurl.com`.

! Template pointers can reference any key within the config itself, whether in the environment config or the base. Template pointers
are always evaluated last and can reference other values that also contain template pointers. Template pointers will always be
evaluated in the proper order so that all values get resolved.