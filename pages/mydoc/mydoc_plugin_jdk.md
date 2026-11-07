---
title: JDK Plugin
sidebar: mydoc_sidebar
permalink: mydoc_plugin_jdk.html
folder: mydoc
toc: false
---
Clears caches of the JDK after a class is redefined:

* `java.beans.Introspector` caches (bean info of the class) in all thread groups. Frameworks use them for property access.
* `java.io.ObjectStreamClass` caches (serialization descriptors), so a redefined `Serializable` class is serialized with its
  new fields.

This plugin replaces the former JavaBeans plugin.

#### Implementation notes:
The caches are cleared on any class redefinition.

On JetBrains Runtime or DCEVM with `-XX:HotswapAgent=...` the JVM opens the needed modules. On another JDK 17+ with
`-javaagent`, add `--add-opens java.base/java.io=ALL-UNNAMED --add-opens java.desktop/java.beans=ALL-UNNAMED
--add-opens java.desktop/com.sun.beans=ALL-UNNAMED`, otherwise the plugin cannot access the caches and logs an error on every
redefinition.

{% include links.html %}
