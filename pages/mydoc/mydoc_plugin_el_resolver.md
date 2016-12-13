---
title: EL-Resolver Plugin
sidebar: mydoc_sidebar
permalink: mydoc_plugin_el_resolver.html
folder: mydoc
toc: false
---

Clear `javax.el.BeanELResolver` cache after any class redefinition.
Following implementations are supported :

* JuelEL
* ApacheEL (tomcat-el-api)
* JBossEL

#### Implementation notes:
Plugin resolves appropriate implementaition of BeanELResolver according specific methods that differs
in each supported implementation. Plugin initialization is triggered at the end of `javax.el.BeanELResolver`
constructor. Method `__resetCache` is inserted into `javax.el.BeanELResolver` class. This method is called
by `org.hotswap.agent.plugin.elresolver.PurgeBeanELResolverCacheCommand` on any class redefinition.

## TODO:
* Support for another EL implementations
