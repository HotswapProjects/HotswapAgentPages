---
title: Release Notes v2.0.0
sidebar: mydoc_sidebar
permalink: mydoc_release_notes_20.html
folder: mydoc
toc: false
---

## Version 2.0.0

### Fixes:
### Key features
* Java17/Java21 support
* Jakarta support

### New Plugins:

* **Idea** pluging for developing IntelliJ IDEA in Idea
* **iBatis** plugin (thanks to @muwaiwai)
* **MyBatis** plugin
* **jackson** plugin (thanks to @liuzhengyang)
* **Spring Boot** plugin (thanks to @cvictory )
* **Sponge plugin** (thanks to @aromaa )
* **OwbJakarta** plugin
* **WeldJakarta** plugin
* **DeltaspikeJakarta** plugin
* **HibernateJakarta** plugin
* **MyBatisPlus** plugin



### Fixes:
## Fixes
* [#404](https://github.com/HotswapProjects/HotswapAgent/issues/404) - fix missing declaredMethodCache in java17
* [#391](https://github.com/HotswapProjects/HotswapAgent/issues/391) - Proxy redefinition support in Weld3
* [#355](https://github.com/HotswapProjects/HotswapAgent/issues/355) - VaadinPlugin does not work in hotswapagent 1.4.1 on Wildfly 19 on Windows 10
* [#357](https://github.com/HotswapProjects/HotswapAgent/issues/357) - Doesn't work with hibernate 5.4.15.final
* [#369](https://github.com/HotswapProjects/HotswapAgent/issues/369)
* [#383](https://github.com/HotswapProjects/HotswapAgent/issues/383) - java.lang.NoSuchMethodException: org.hibernate.validator.internal.metadata.BeanMetaDataManager.__resetCache()
* [#445](https://github.com/HotswapProjects/HotswapAgent/issues/445) - fix enum field add/remove  
* [#463](https://github.com/HotswapProjects/HotswapAgent/issues/463) - MyBatis support mybatis-spring 
* [#557](https://github.com/HotswapProjects/HotswapAgent/issues/557) - fix MyBatis-Spring integration where MyBatis reloading is not functioning properly and results in a NullPointerException
* [#447](https://github.com/HotswapProjects/HotswapAgent/issues/447) - full jakarta support
* [#568](https://github.com/HotswapProjects/HotswapAgent/issues/568) - java.lang.NoSuchMethodException for org.zkoss.zel.BeanELResolver.__resetCache() in ZKPlugin
