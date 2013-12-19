---
filename: ref-lifecycle.md
layout: docs
title:  "RESTX Components Lifecycle"
---
# RESTX Components lifecycle

## Scopes

Components lifecycle and scopes in RESTX are pretty simple: _almost_ all components are singleton (and therefore have an Application scope).

### What? No Session scope?

RESTX is a REST framework, which favors a stateless architecture. Session scope in usual Java web frameworks breaks this principle, therefore RESTX simply doesn't support it. What you have is `RestxSession` which allows to store keys on the client, using signed Cookies. This is very limited but usually you don't need much there, the principal being most of the time the only thing to put there. Same applies to Conversation scope that you find in CDI.

### What? No Request scope?

When dealing only with a REST API implementation (which is the focus of RESTX), you don't frequently need to put objects in the request scope: you query your database, apply your business logic, and return data. Most of the time you don't need Request scope for that, and for sake of simplicity RESTX doesn't support Request scope. For the rare cases where you would need request scope, you can use a `ThreadLocal` (make sure you don't forget to clear it).

## DEV mode

The `dev` mode is the mode used during development: RESTX supports interesting features in dev mode such as autocompile, which makes developing with RESTX a pleasure in terms of development feedback loop.

### Stateless

To support thism and also to favor true statelessness, in `dev` mode RESTX uses a very specific component lifecycle: all components are created and thrown away on each request. Yes, that may be surprising especially when you've read the rule that all components are singleton. The idea is simple: to achieve statelessness you must ensure that each request can be performed independently, without relying on internale server state brought by other requests. To make sure you don't rely on components state between requests, RESTX drop them at each request. In production this is obvisouly not ideal for performance reasons, and therefore RESTX uses true singletons in production mode (and don't worry the test for dev or prod mode is made at startup, not on each request).

### Autocompile

Going even further, when using auto compile RESTX will automatically compile your sources when they change, and in such case drop the whole classloader with all your application classes in favor of a new one with your new classes. That's what allow you to change anything in your sources and still benefit from hot reload. Throwing away the whole classloader means that even static fields are reset on source changes.

### AutoClosable

Having components dropped away on each request implies that your components must be disposable without leaking resources. If you need to clean up something when disposed, your components must implement the `AutoClosable` interface, and the close method defined in that method will be called when closing the Factory which has built the component.

### AutoStartable

But sometimes you need a different behaviour even in `dev` mode. Some components may be too slow to start. or you may need some components which state have to stay between requests like a cache. For such cases RESTX provides a feature called `AutoStartable` components. Such components are started at application startup time even in DEV mode, and not dropped away at each request. This means that they are not auto compiled too, and are loaded with a different classloader. Being loaded by a different classloader implies some limitations: for instance you cannot access package private fields between `AutoStartable` components and regular ones. Moreover you have to be careful with such components: they make their dependencies part of the components which are not auto compiled.

## TEST and INFINIREST modes

There is also another specific case: the `test` and `infinirest` modes. They are used for testing (regular tests or continuous tests respectively), and therefore here you often need to override some components just for a single test. Therefore in these modes all components, including `AutoStartable` ones, are dropped at each request.

## Conclusion

So that's what we mean when we say that _almost_ all components are singleton. The real definition is that _all_ components are singleton in `prod` mode, in `dev` mode all components have request scope except components required to start all `AutoStartable` components, and in `test` and `infinirest` modes all components have request scope.

