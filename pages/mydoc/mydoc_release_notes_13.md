---
title: Release Notes v1.3.0
sidebar: mydoc_sidebar
permalink: mydoc_release_notes_13.html
folder: mydoc
toc: false
---

## Version 1.3.0

### New Plugins:
- **Vaadin**
   - Register changes in @Route to the router when a class is modified (add new views on the fly)
   - Changes to a template model are live after a browser refresh
   - All internal metadata caches are cleared whenever a class is changed

### New features:
- [#242](https://github.com/HotswapProjects/HotswapAgent/issues/242)HotswapAgent plugins may be included as a standard maven dependency 

### Fixes:
Agent Core:
- [#223](https://github.com/HotswapProjects/HotswapAgent/issues/223)ERROR (org.hotswap.agent.watch.nio.EventDispatcher) - No match for watch event

Spring plugin:
- [#241](https://github.com/HotswapProjects/HotswapAgent/issues/241)Spring plugin registers a managed bean for a prototype bean
- [#221](https://github.com/HotswapProjects/HotswapAgent/issues/221)Spring Boot 2 projects throw NoSuchMethodException for __resetCache
- [#232](https://github.com/HotswapProjects/HotswapAgent/issues/232)Cannot create proxy for spring component without default constructor
- [#243](https://github.com/HotswapProjects/HotswapAgent/issues/243)HotswapSpringCallback not serializable

JBoss plugin:
- [#229](https://github.com/HotswapProjects/HotswapAgent/issues/229)JBoss - Plugin not found in the registry, error on random classloader jars.

Other:
- [#236](https://github.com/HotswapProjects/HotswapAgent/issues/236)Autodeploy snapshot from master to Sonatype
- [#224](https://github.com/HotswapProjects/HotswapAgent/issues/224)Release to Maven 
- [#234](https://github.com/HotswapProjects/HotswapAgent/issues/234)maven central repos not include version 1.2.0
