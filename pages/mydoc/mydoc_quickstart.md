---
title: Quick Start JDK 8
sidebar: mydoc_sidebar
permalink: mydoc_quickstart.html
folder: mydoc
toc: false
---
### Install
1. download [latest release of DCEVM Java patch](https://github.com/dcevm/dcevm/releases) and launch the installer
(e.g. `java -jar installer-light.jar`). Currently you need to select correct installer for Java major version (7/8).
1. select java installation directory on your disc and press "Install DCEVM as altjvm" button. Java 1.7+ versions are supported.
 Be sure to have write access to the java installation directory (on Windows: Start > cmd > right click > run as administrator).
1. download [latest release of Hotswap agent jar](https://github.com/HotswapProjects/HotswapAgent/releases),
unpack `hotswap-agent.jar` and put it anywhere on your disc. For example: `C:\java\hotswap-agent.jar`

### Run your application
1. add following command line java attributes: `-XXaltjvm=dcevm -javaagent:PATH_TO_AGENT\hotswap-agent.jar` (you
need to replace PATH_TO_AGENT with an actual) directory. For example `java -XXaltjvm=dcevm -javaagent:c:\java\hotswap-agent.jar YourApp`.
  See dedicated pages for [Eclipse][mydoc_setup_eclipse], [IntelliJ IDEA][mydoc_setup_intellij_idea]
  and [Netbeans][mydoc_setup_netbeans] for IDE specific setup guides. If your application is already running, you still can attach agent jar using the example [code snippet](https://gist.github.com/xnike/a268fc209df52bf1bf09a268e97cef53).
1. (optional) create a file named "hotswap-agent.properties" inside your resources directory, see available properties and
  default values: <https://github.com/HotswapProjects/HotswapAgent/blob/master/hotswap-agent-core/src/main/resources/hotswap-agent.properties>
1. start the application in debug mode, check that the agent and plugins are initialized correctly:

        HOTSWAP AGENT: 9:49:29.548 INFO (org.hotswap.agent.HotswapAgent) - Loading Hotswap agent - unlimited runtime class redefinition.
        HOTSWAP AGENT: 9:49:29.725 INFO (org.hotswap.agent.config.PluginRegistry) - Discovered plugins: [org.hotswap.agent.plugin.hotswapper.HotswapperPlugin, org.hotswap.agent.plugin.jvm.AnonymousClassPatchPlugin, org.hotswap.agent.plugin.hibernate.HibernatePlugin, org.hotswap.agent.plugin.spring.SpringPlugin, org.hotswap.agent.plugin.jetty.JettyPlugin, org.hotswap.agent.plugin.tomcat.TomcatPlugin, org.hotswap.agent.plugin.zk.ZkPlugin, org.hotswap.agent.plugin.logback.LogbackPlugin]
        ...
        HOTSWAP AGENT: 9:49:38.700 INFO (org.hotswap.agent.plugin.spring.SpringPlugin) - Spring plugin initialized - Spring core version '3.2.3.RELEASE'
1. save a changed resource and/or use the HotSwap feature of your IDE to reload changes

{% include links.html %}
