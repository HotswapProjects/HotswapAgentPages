---
title: Equinox (OSGI)/ Eclipse Plugin
sidebar: mydoc_sidebar
permalink: mydoc_plugin_osgiequinox.html
folder: mydoc
toc: false
---

OsgiEquinox plugin provides hotswap support for Eclipse platform development or development of Eclipse plugins.
(Do not confuse it with common development in Eclipse!).

Configuration
-------------
Following options must be setup in eclipse.ini for debugee Eclipse instance:

     # use application classloader for the framework
    -Dosgi.frameworkParentClassloader=app
     # development classpath that is added to each plugin classpath
    -Dosgi.dev=[extra_classpath]
     # use dcevm as JVM
    -XXaltjvm=dcevm
     # enable hotswapagent
    -javaagent:PATH_TO_AGENT/hotswap-agent.jar
     # enable remote debugging on port 8000
    -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=8000

`extra_classpath` is directory where compiled classes are deployed to either by IDE or some script. Classes from this path take 
precedence over classes from package's jar. When debugger send a modified class file to JVM, HotswapAgent stores this file into 
extra_classpath directory.

It is also necessary to setup following hotswap-agent.properties:

    extraClasspath=[extra_classpath]
    osgiEquinox.debugMode=true

then connect the IDE debugger (eclipse, netbeans or idea) to port 8000 and happy hotswapping!
