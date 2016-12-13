---
title: JavaBeans Plugin
sidebar: mydoc_sidebar
permalink: mydoc_plugin_javabeans.html
folder: mydoc
toc: false
---
Clear Introspector cache in appropriate thread groups. Introspector cache is used for reflection data caching.

#### Implementation notes:
Cache cleanup is triggered on any class redefinition.

