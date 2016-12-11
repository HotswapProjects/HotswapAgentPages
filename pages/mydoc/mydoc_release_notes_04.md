---
title: Release Notes v0.4
sidebar: mydoc_sidebar
permalink: mydoc_release_notes_04.html
folder: doc
toc: false
---

### New frameworks / JVM plugins:

* ClassInit - enhance DCEVM by static variables + enum values initialization
* Hibernate 3 + 4 + 5
* Deltaspike 1.7
* RestEasy 3.0
* Spring 4.2+
* Weld 2.3, 2.4 -  bean reloading in contexts + reloading strategy
* MyFaces 2.2
* log4j 2.7 

### Core changes:

* support to attach agent runtime to JVM process 
* Allow configuration to be loaded from an external file
* _jsp.class are excluded from .class processing
*  META-INF + Maven Versioning support

### Minor changes:

* LOGGER timestamp format can be setup in properties file
* [#154](https://github.com/HotswapProjects/HotswapAgent/pull/154) Modify the ClassPathScanner to support URIs prefixed with "zip:" 
* [#145](https://github.com/HotswapProjects/HotswapAgent/pull/145) Added support to attach agent runtime to JVM process
* [#108](https://github.com/HotswapProjects/HotswapAgent/pull/108) Allow configuration to be loaded from an external file
* [#104](https://github.com/HotswapProjects/HotswapAgent/pull/104) Adding LOGFILE.append configuration option

### Bugfixes

* [#155] (https://github.com/HotswapProjects/HotswapAgent/issues/155) Modifying jsp on tomcat8 threw ConcurrentModificationException
* [#157](https://github.com/HotswapProjects/HotswapAgent/pull/157) ZK label files not refreshing on change. 
* _jsp.class skipped from .class processing - fixes problems with JSPs
* [#141](https://github.com/HotswapProjects/HotswapAgent/pull/141) WebObjects plugin - clear validation cache on every reload
* [#124](https://github.com/HotswapProjects/HotswapAgent/issues/124) JBossModulesPlugin on JBoss Wildfly 10
* windows NIO2 watcher patched issues with massive class reload
* [#116](https://github.com/HotswapProjects/HotswapAgent/pull/116) Fixed UndeclaredThrowableException in Spring plugin. 
* [#103](https://github.com/HotswapProjects/HotswapAgent/issues/103) java.lang.RuntimeException: org.hotswap.agent.javassist.NotFoundException
* [#98](https://github.com/HotswapProjects/HotswapAgent/pull/98) Handle null ClassLoader
