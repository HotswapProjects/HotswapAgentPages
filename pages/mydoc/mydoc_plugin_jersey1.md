---
title: Jersey1 Plugin
sidebar: mydoc_sidebar
permalink: mydoc_plugin_jersey1.html
folder: doc
toc: false
---

Jersey1 reloading support for all root resource classes (classes annotated by `javax.ws.rs.Path`) and provider classes.

#### Implementation notes:
##### Jersey1:
Hook into `com.sun.jersey.spi.container.servlet.ServletContainer` call. Register all *scanClasses* and *registeredClasses*
from `com.sun.jersey.api.core.ResourceConfig` and trigger reloading of jersey container on any root resource class change.
