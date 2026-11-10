---
title: Release Notes v2.0.5
sidebar: mydoc_sidebar
permalink: mydoc_release_notes_205.html
folder: mydoc
toc: false
---

## Version 2.0.5 (2026-11-10)
### Main changes
* File watching recovers from event queue overflows and directory recreation. On macOS, JetBrains Runtime can watch an entire directory tree with one registration, reducing file descriptor usage ([#318](https://github.com/HotswapProjects/HotswapAgent/issues/318), [#479](https://github.com/HotswapProjects/HotswapAgent/issues/479), [#596](https://github.com/HotswapProjects/HotswapAgent/issues/596), [#673](https://github.com/HotswapProjects/HotswapAgent/issues/673)).
* Spring reload handles enhanced configuration beans, scoped proxies, `@Lookup` and `@EventListener` methods, and bean classes written after the file creation event ([#623](https://github.com/HotswapProjects/HotswapAgent/issues/623), [#624](https://github.com/HotswapProjects/HotswapAgent/issues/624), [#458](https://github.com/HotswapProjects/HotswapAgent/issues/458), [#245](https://github.com/HotswapProjects/HotswapAgent/issues/245)). Bean metadata caching stays enabled, so annotations on `@Bean` methods such as `@Qualifier` and `@Order` are seen again ([#461](https://github.com/HotswapProjects/HotswapAgent/issues/461), [#639](https://github.com/HotswapProjects/HotswapAgent/issues/639)).
* Agent initialization and transformer registration are safer when the agent is loaded twice or deployments start concurrently. Class loaders that cannot see the agent no longer receive transforms that depend on it ([#560](https://github.com/HotswapProjects/HotswapAgent/issues/560), [#635](https://github.com/HotswapProjects/HotswapAgent/issues/635)).
* Added support for Logback 1.3 and newer ([#713](https://github.com/HotswapProjects/HotswapAgent/issues/713)). Jersey containers now reload in the request thread ([#185](https://github.com/HotswapProjects/HotswapAgent/issues/185), [#333](https://github.com/HotswapProjects/HotswapAgent/issues/333), [#423](https://github.com/HotswapProjects/HotswapAgent/issues/423)), and the Hibernate session factory proxy works with Spring transactions in a native Hibernate setup ([#187](https://github.com/HotswapProjects/HotswapAgent/issues/187), [#288](https://github.com/HotswapProjects/HotswapAgent/issues/288), [#301](https://github.com/HotswapProjects/HotswapAgent/issues/301)).
* Fixed Mojarra Facelet includes from `webappDir` ([#684](https://github.com/HotswapProjects/HotswapAgent/issues/684)) and Jakarta EL cache invalidation on WildFly ([#722](https://github.com/HotswapProjects/HotswapAgent/issues/722)). Weld beans are reloaded once per class instead of once per deployment.
* Fixed Kotlin anonymous class patching ([#263](https://github.com/HotswapProjects/HotswapAgent/issues/263), [#552](https://github.com/HotswapProjects/HotswapAgent/issues/552), [#637](https://github.com/HotswapProjects/HotswapAgent/issues/637)) and plugin discovery in JARs without directory entries ([#400](https://github.com/HotswapProjects/HotswapAgent/issues/400)).

### Fixes:
* [#688](https://github.com/HotswapProjects/HotswapAgent/issues/688) - autoHotswap keeps a rejected class in the reload map, so every later reload fails
* [#358](https://github.com/HotswapProjects/HotswapAgent/issues/358) - `PropertyNotFoundException` for a getter added at runtime on Java 9 - 16
* [#359](https://github.com/HotswapProjects/HotswapAgent/issues/359) - class file stream is not closed (Gradle, IntelliJ, Windows)
* [#612](https://github.com/HotswapProjects/HotswapAgent/issues/612) - warnings about bean definitions described only by text
* [#674](https://github.com/HotswapProjects/HotswapAgent/issues/674) - property reload of a bean factory without environment
* [#477](https://github.com/HotswapProjects/HotswapAgent/issues/477) - Mojarra `BeanManager` is patched without javax managed beans
* [#388](https://github.com/HotswapProjects/HotswapAgent/issues/388) - InvocationTargetException in the Tomcat plugin transformation
* [#426](https://github.com/HotswapProjects/HotswapAgent/issues/426) - ZK plugin without `DHtmlLayoutServlet`
* [#676](https://github.com/HotswapProjects/HotswapAgent/issues/676) (partly) - WildFly: a deployment fails when it disables a plugin that server classes call
* Plugins disabled by the agent option are not loaded during the plugin scan

{% include links.html %}
