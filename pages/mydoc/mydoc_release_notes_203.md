---
title: Release Notes v2.0.3
sidebar: mydoc_sidebar
permalink: mydoc_release_notes_203.html
folder: mydoc
toc: false
---

## Version 2.0.3 (2026-01-22)
### Compatibility / core
* Declared JDK compatibility expanded to 21+.
* `ClassInitPlugin`: handle enum reordering correctly.

### Plugins / frameworks
* **Vaadin**: support for Vaadin 25.1 (hotswap classes moved to a different module and package, still backward compatible).
* **GlassFish**: adjustments for GlassFish 7.
* **Spring**:
  * Updates for Spring 6 deprecations and API changes.
  * New system property `-DSpringReloadDelayMillis` to improve the redefine timing.
  * Fixes around caches and bean instantiation (e.g. `createBean`, no initialization of abstract beans).
* **Hibernate**: plugin version updates, cleanup of a fallback parameter.
* **MyBatis / MyBatis-Plus**: extended supported versions, transformation fixes, dependency scope `provided`.

### Watcher / file change detection
* Watcher and scheduler are initialized before the plugin configuration.
* Files inside a newly created directory get a create event ([#596](https://github.com/HotswapProjects/HotswapAgent/issues/596)).
* Other watcher fixes.

### Configuration
* Plugins can be disabled with the system property `-Dhotswapagent.disablePlugin=Plugin1,Plugin2`.

### Fixes and maintenance
* Javassist upgrade and follow-up fixes ([#661](https://github.com/HotswapProjects/HotswapAgent/issues/661)).

### Build and publishing
* Publishing to Maven Central with `central-publishing-maven-plugin` (OSSRH was retired).

{% include links.html %}
