---
title: Release Notes v2.0.5
sidebar: mydoc_sidebar
permalink: mydoc_release_notes_205.html
folder: mydoc
toc: false
---

## Version 2.0.5 (2026-11-10)
### Main changes
* File watching recovers from event queue overflows and directory recreation. On macOS, JetBrains Runtime can watch an entire directory tree with one registration, reducing file descriptor usage.
* Spring reload handles enhanced configuration beans, scoped proxies, `@Lookup` and `@EventListener` methods, and bean classes written after the file creation event.
* Agent initialization and transformer registration are safer when the agent is loaded twice or deployments start concurrently. Class loaders that cannot see the agent no longer receive transforms that depend on it.
* Added support for Logback 1.3 and newer. Jersey containers now reload in the request thread, and the Hibernate session factory proxy works with native Spring transactions.
* Fixed Mojarra Facelet includes from `webappDir`, Weld reloads across deployments, and Jakarta EL cache invalidation on WildFly.
* Fixed Kotlin anonymous class patching and plugin discovery in JARs without directory entries.

### Fixes:
* [#722](https://github.com/HotswapProjects/HotswapAgent/issues/722) - WildFly 27+ (Jakarta EL): a bean property added by hotswap is not resolved
* [#358](https://github.com/HotswapProjects/HotswapAgent/issues/358) - `PropertyNotFoundException` for a getter added at runtime on Java 9 - 16
* [#635](https://github.com/HotswapProjects/HotswapAgent/issues/635) - InvocationTargetException in class loaders that cannot see the agent (Gradle Gretty)
* [#684](https://github.com/HotswapProjects/HotswapAgent/issues/684) - Undertow `webappDir` breaks relative `<ui:include>` with Mojarra 4.0.27+ / 4.1.13+
* [#187](https://github.com/HotswapProjects/HotswapAgent/issues/187), [#288](https://github.com/HotswapProjects/HotswapAgent/issues/288), [#301](https://github.com/HotswapProjects/HotswapAgent/issues/301) - Hibernate `SessionFactory` proxy breaks Spring transactions
* [#612](https://github.com/HotswapProjects/HotswapAgent/issues/612) - warnings about bean definitions described only by text
* [#674](https://github.com/HotswapProjects/HotswapAgent/issues/674) - property reload of a bean factory without environment
* [#560](https://github.com/HotswapProjects/HotswapAgent/issues/560) - the agent is initialized twice when it is loaded twice
* [#477](https://github.com/HotswapProjects/HotswapAgent/issues/477) - Mojarra `BeanManager` is patched without javax managed beans
* [#388](https://github.com/HotswapProjects/HotswapAgent/issues/388) - InvocationTargetException in the Tomcat plugin transformation
* [#359](https://github.com/HotswapProjects/HotswapAgent/issues/359) - class file stream is not closed (Gradle, IntelliJ, Windows)
* [#688](https://github.com/HotswapProjects/HotswapAgent/issues/688) - autoHotswap keeps a rejected class in the reload map, so every later reload fails
* [#400](https://github.com/HotswapProjects/HotswapAgent/issues/400) - `pluginPackages` in JAR files without directory entries
* [#263](https://github.com/HotswapProjects/HotswapAgent/issues/263), [#552](https://github.com/HotswapProjects/HotswapAgent/issues/552), [#637](https://github.com/HotswapProjects/HotswapAgent/issues/637) - anonymous class patch when the main class file is missing (Kotlin)
* [#426](https://github.com/HotswapProjects/HotswapAgent/issues/426) - ZK plugin without `DHtmlLayoutServlet`
* Weld beans are reloaded once per class, not once per deployment
* Plugins disabled by the agent option are not loaded during the plugin scan
* Transformer registration is thread safe

{% include links.html %}
