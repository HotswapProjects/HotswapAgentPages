---
title: Quick Start JDK 11
sidebar: mydoc_sidebar
permalink: mydoc_quickstart-jdk11.html
folder: mydoc
toc: false
---
### Install
Use *OpenJDK Hotswap* instead of standard JDK-11. Download
[windows jdk-11-hotswap](https://github.com/HotswapProjects/openjdk-jdk11/releases/download/dcevm-11.0.beta/jdk-11-hotswap.zip)
or [linux java-11-openjdk-hotswap.tgz](https://github.com/HotswapProjects/openjdk-jdk11/releases/download/dcevm-11.0.beta/java-11-openjdk-hotswap.tgz) 
, unpack it and set JAVA_HOME to it's location (or add it as JDK to your IDE). 

### Configure
1. Everything is configured for you, just run your application with downloaded JDK :-)
1. (optional) create a file named "hotswap-agent.properties" inside your resources directory, see available properties and
  default values: <https://github.com/HotswapProjects/HotswapAgent/blob/master/hotswap-agent-core/src/main/resources/hotswap-agent.properties>

### Run
1. start the application in debug mode, check that the agent and plugins are initialized correctly:

        HOTSWAP AGENT: 9:49:29.548 INFO (org.hotswap.agent.HotswapAgent) - Loading Hotswap agent - unlimited runtime class redefinition.
        HOTSWAP AGENT: 9:49:29.725 INFO (org.hotswap.agent.config.PluginRegistry) - Discovered plugins: [org.hotswap.agent.plugin.hotswapper.HotswapperPlugin, org.hotswap.agent.plugin.jvm.AnonymousClassPatchPlugin, org.hotswap.agent.plugin.hibernate.HibernatePlugin, org.hotswap.agent.plugin.spring.SpringPlugin, org.hotswap.agent.plugin.jetty.JettyPlugin, org.hotswap.agent.plugin.tomcat.TomcatPlugin, org.hotswap.agent.plugin.zk.ZkPlugin, org.hotswap.agent.plugin.logback.LogbackPlugin]
        ...
        HOTSWAP AGENT: 9:49:38.700 INFO (org.hotswap.agent.plugin.spring.SpringPlugin) - Spring plugin initialized - Spring core version '3.2.3.RELEASE'
1. save a changed resource and/or use the HotSwap feature of your IDE to reload changes

{% include links.html %}
