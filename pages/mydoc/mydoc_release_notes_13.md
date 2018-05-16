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
- HotswapAgent plugins may be included as a standard maven dependency #242 

### Fixes:
Agent Core:
- ERROR (org.hotswap.agent.watch.nio.EventDispatcher) - No match for watch event #223

Spring plugin:
- Spring plugin registers a managed bean for a prototype bean #241
- Spring Boot 2 projects throw NoSuchMethodException for __resetCache #221
- Cannot create proxy for spring component without default constructor #232 
- HotswapSpringCallback not serializable #243

JBoss plugin:
- JBoss - Plugin not found in the registry, error on random classloader jars. #229

Other:
- Autodeploy snapshot from master to Sonatype #236
- Release to Maven #224 
- maven central repos not include version 1.2.0 #234
