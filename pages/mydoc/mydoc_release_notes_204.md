---
title: Release Notes v2.0.4
sidebar: mydoc_sidebar
permalink: mydoc_release_notes_204.html
folder: mydoc
toc: false
---

## Version 2.0.4 (2026-10-31)
### Main changes
* Optimized hotswap using jbr-api 1.10.0 (JBR hotswap callback), supported in new JBR 21/25
* Spring: support for Spring Framework 5.3 through 7.0

### Fixes:
* [#671](https://github.com/HotswapProjects/HotswapAgent/issues/671) - IllegalAccessError when using HotswapAgent with Mockito/ByteBuddy, ByteBuddy class loaders are excluded from plugin class patching
* [#646](https://github.com/HotswapProjects/HotswapAgent/issues/646) - add LOG_TO_CONSOLE property to enable/disable console logging
* [#668](https://github.com/HotswapProjects/HotswapAgent/issues/668) - support for new Weld + JBoss ELResolver
* [#392](https://github.com/HotswapProjects/HotswapAgent/issues/392) - Vaadin 20.0.0.alpha6: NoSuchMethodError: 'VaadinServletService VaadinServlet.getService()'
* [#394](https://github.com/HotswapProjects/HotswapAgent/issues/394) - NullPointerException in WatchResourcesPlugin.init
* [#652](https://github.com/HotswapProjects/HotswapAgent/issues/652) - fix jar files handling, custom plugins in a directory with spaces in its name
* [#665](https://github.com/HotswapProjects/HotswapAgent/issues/665) - autoHotswap and disabledPlugins do not work when using an external hotswap-agent.properties
* WildFly: hotswap failing after undeploy and redeploy of a WAR, ClassNotFoundException for classes in a new package
* AnonymousClassPatch: skip Spring CGLIB proxies
* Plugin transform types are not resolved through the context class loader
* Watcher: improved event deduplication in the event dispatcher

{% include links.html %}
