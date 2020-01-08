---
title: Release Notes v1.4.0
sidebar: mydoc_sidebar
permalink: mydoc_release_notes_13.html
folder: mydoc
toc: false
---

## Version 1.4.0

### Fixes:
### Key features
* Java11 support
* Kotlin support - HotswapAgent + dcevm is succesfuly used on many Kotlin projects now

### New Plugins:
* **CXF-JAXRS** plugin, with Spring + CDI integration & JAXB realoding
* **FreeMarker** plugin (thanks to AJ Banck)
* **MyBatis** plugin
* **Undertow** plugin
* **Wicket** plugin (thanks to T. Heigl)

### New features:
* Add watchResources support to JBossModules plugin (JbossAS+Wildfly)
* Weld3 support (CDI-2.0)
* OWB2 support (CDI-2.0)
* Deltaspike 1.8, 1.9 support
* Reloading of CDI beans is skipped for simple method body modifications (using full class signature comparision)
* Support for watchResources+extraClassPath  in SpringBoot  applications (TomcatPlugin supports `TomcatEmbeddedWebappClassLoader`)
* Improve performance by skipping useless `DelegatingClassLoader` registration.

### Fixes:
* [#201](https://github.com/HotswapProjects/HotswapAgent/issues/201) - Fix npe in Log4J2 plugin
* [#218](https://github.com/HotswapProjects/HotswapAgent/issues/218) - Exclude jdk.internal.reflect.DelegatingClassLoader
* [#255](https://github.com/HotswapProjects/HotswapAgent/pull/255) - Added check to `ProxyReplacer` for null beans 
* [#264](https://github.com/HotswapProjects/HotswapAgent/issues/264) - Fix extraClassPath in UrlClassLoader
* [#269](https://github.com/HotswapProjects/HotswapAgent/issues/269) - Fix spring plugin on wildfly 12
* [#286](https://github.com/HotswapProjects/HotswapAgent/issues/286) - change log level on reloading of Spring XML config
* [#291](https://github.com/HotswapProjects/HotswapAgent/issues/291) - Fix NPE on private enum redefinition
* [#192](https://github.com/HotswapProjects/HotswapAgent/issues/192) -  Fix HA doesn't work on war deployed on Wildfly10.1
