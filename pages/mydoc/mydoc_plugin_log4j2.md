---
title: Log4j2 Plugin
sidebar: mydoc_sidebar
permalink: mydoc_plugin_log4j2.html
folder: doc
toc: false
---

[Log4j2](http://logging.apache.org/log4j/2.x/) configuration reload.

#### Implementation notes:
Plugin hooks into `org.apache.logging.log4j.core.LoggerContext.setConfiguration(Configuration)` call. All configuration URL's are
registered and watched for change. After the file change, full reconfiguration via setConfigLocation(URI) method is executed.


