---
title: Release Notes v1.2.0
sidebar: mydoc_sidebar
permalink: mydoc_release_notes_12.html
folder: mydoc
toc: false
---

## Version 1.2.0

### New Plugins

* OpenWebBeans (Tomcat/Tommee supported)
* Mojarra 
* MyFaces
* OmniFaces 

### New features

* Support for Java9.
* WeldPlugin - SesionScoped bean reinjection, EJB session beans support
* Deltaspike contexts reinjections
* excludedClassLoaderPatterns: comma separated list of class loaders to exclude from initialization, in the form of RegEx patterns.
* [#171](https://github.com/HotswapProjects/HotswapAgent/issues/171) - hotswap-agent.properties properties values can reference System variables defined by JVM argument -D...
* improved GlassFish support. Felix OSGi patches, GlassFish/Weld support
* [#197](https://github.com/HotswapProjects/HotswapAgent/issues/197) - multiple webappDir entries allowed. Entrypoints are separated by ',' character

### Bugfixes

* Jersey HK2 service reload on any change
* Weld plugin field access [#161](https://github.com/HotswapProjects/HotswapAgent/issues/161)
* DeltaSpike v1.7 fixes
* JavaBeans - synthetic classes are flushed from Itrospector cache
* multi resource methods from extraClassPath, [#176](https://github.com/HotswapProjects/HotswapAgent/issues/176)
* fixed problem with not started WebappClassLoader, [#185](https://github.com/HotswapProjects/HotswapAgent/issues/185)
* SpringPlugin in JBossAS/Wildfly [#140](https://github.com/HotswapProjects/HotswapAgent/issues/140),  [#184](https://github.com/HotswapProjects/HotswapAgent/issues/184)
* Support symbolic links in extraClassPath [203](https://github.com/HotswapProjects/HotswapAgent/issues/203)
