---
title: Java Hotswap-API proposal
sidebar: mydoc_sidebar
permalink: mydoc_ha_api.html
folder: mydoc
toc: false
---

Public Hotswap API proposal. It is intended to be used by framework authors. 

This is **first draft** and it is meant only as a material for discussion.

@Plugin
------------------
- name - A name of the plugin. This name is used to reference the plugin in code and configuration.
- description - Any meaningful plugin description.

@OnClassLoadEvent
------------------
Define plugin callback method on class load by classloader (application class is loaded or reloaded by hotswap).

- classNameRegexp - Regexp of class name.
- events - Specify list of events to watch for (class is loaded by the ClassLoader / redefined by hotswap mechanism). By default are both DEFINE and REDEFINE events enabled.
- skipAnonymous (default true) - Anonymous classes (e.g. MyClass$1, MyClass$2, ...) are usually reloaded with main class MyClass, but the transformation should be done only on the main class. 
- skipSynthetic (default true) - Classes created at runtime are usually skipped

@OnClassFileEvent
------------------
- classNameRegexp - Regexp of class name.
- events - Filter watch event types. Default is all events (CREATE, MODIFY, DELETE). 
      Be careful about assumptions on events. Some IDEs create on file compilation sequence of multiple delete/create/modify events.
- timeout - Merge multiple same watch events up to this timeout into a single watch event (useful to merge multiple MODIFY events).      

@OnResourceFileEvent
------------------
- path - Prefix of resource path to watch.
- filter - Regexp expression to filter resources.
- events - Filter watch event types. Default is all events (CREATE, MODIFY, DELETE).
- onlyRegularFiles (default true) - Watch only for regular files. By default all other types (including directories) are filtered out.
- timeout - Merge multiple same watch events up to this timeout into a single watch event (useful to merge multiple MODIFY events).


