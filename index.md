---
title:
keywords: sample homepage
tags: [getting_started]
sidebar: mydoc_sidebar
permalink: index.html
summary:
toc: false
---
[![Gitter](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/HotswapProjects/user) [![Build Status](https://travis-ci.org/HotswapProjects/HotswapAgent.svg?branch=master)](https://travis-ci.org/HotswapProjects/HotswapAgent)

Java unlimited runtime class and resource redefinition.

The main purpose of this project is to avoid infamous change->restart + *wait*->check development lifecycle.
Save&Reload during development should be standard and many other languages (including C#) contain this feature.

### Features
In contrast to standard Java, where the hotswap is limited to in-body code changes, the DCEVM + HotswapAgent 
allow following code changes:

* Add/remove/modify class fields.
* Add/remove/modify methods. Add/remove/modify method annotations
* Add/remove/modify classes including inner classes. HotswapAgent handless correct inner class redefinitions.
* Add/remove static member of classes. HotswapAgent handles static member initialization.
* Add/remove enum values
* Refresh framework and application server settings

The only unsupported operation is hierarchy change (change the superclass or remove an interface). 

DCEVM realizes hotswap on JVM level. HotwapAgent does the same on level of Java frameworks and 
servlet containers. Both projects used together forms excellent combination for daily development not only
in Java but also in another JVM languages.

### Easy to start
Download and install latest [DCEVM Java patch](https://github.com/dcevm/dcevm/releases) +
[agent jar](https://github.com/HotswapProjects/HotswapAgent/releases) and launch your application server
with options `-XXaltjvm=dcevm -javaagent:hotswap-agent.jar` to get basic setup. You can attach [agent jar](https://github.com/HotswapProjects/HotswapAgent/releases) to the running JVM using the following example [code snippet](https://gist.github.com/xnike/a268fc209df52bf1bf09a268e97cef53). Optionally add hotswap-agent.properties to your application to configure plugins and agent behaviour.

### Plugins
Each application framework (Spring, Hibernate, Logback, ...) needs special reloading mechanism to keep
up-to-date after class redefinition (e.g. Hibernate configuration reload after new entity class is introduced).
Hotswap agent works as a plugin system and ships preconfigured with all major framework plugins. It is easy
to write your custom plugin even as part of your application.

### Contribute
This project is very complex due to lot of supported frameworks and various versions. Community contribution
is mandatory to keep it alive. You can start by creating a plugin inside your application or by writing an
example/integration test. There is always need for documentation improvement :-). Thank you for any help!

