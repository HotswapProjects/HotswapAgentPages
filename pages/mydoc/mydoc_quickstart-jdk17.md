---
title: Quick Start JDK 17+
sidebar: mydoc_sidebar
permalink: mydoc_quickstart-jdk17.html
folder: mydoc
toc: false
---
### Install
1. Download the latest release of [JetBrains Runtime](https://github.com/JetBrains/JetBrainsRuntime/releases) 17, 21 or 25
for your platform, unpack it and set JAVA_HOME to its location (or add it as JDK to your IDE). JetBrains Runtime supports
enhanced class redefinition. To check it, run `java -XX:+AllowEnhancedClassRedefinition -version`, it fails if the JVM does not support it.
1. Download the [latest release of the Hotswap agent jar](https://github.com/HotswapProjects/HotswapAgent/releases)
and copy it as `<JBR-install-directory>/lib/hotswap/hotswap-agent.jar` (create the `lib/hotswap` folder if it does not exist).
The file name must be `hotswap-agent.jar`, without the version.

### Configure
1. Run your application with JBR using additional options: `-XX:+AllowEnhancedClassRedefinition -XX:HotswapAgent=fatjar`
1. (optional) create a file named "hotswap-agent.properties" inside your resources directory, see available properties and
  default values: <https://github.com/HotswapProjects/HotswapAgent/blob/master/hotswap-agent-core/src/main/resources/hotswap-agent.properties>
1. (optional) in case you are not using `autoHotswap=true` and therefore not using the hotswapping mechanism provided by HotswapAgent, you may want to add `-Xlog:redefine+class*=info` as an additional JVM argument in order to get feedback about reloaded classes.

#### -XX:HotswapAgent modes
* `fatjar` - the JVM loads `<JBR>/lib/hotswap/hotswap-agent.jar` with all plugins.
* `core` - the JVM loads `<JBR>/lib/hotswap/hotswap-agent-core.jar`, the agent with core plugins only (e.g. Hotswapper, JDK, anonymous classes), without framework plugins.
* `external` - the JVM only prepares the module access for the agent, the agent is added with `-javaagent:/path/to/hotswap-agent.jar`.
  Use this mode to use an agent jar from another location.
* `disabled` - no agent (default).

Use only one way to load the agent. With `-XX:HotswapAgent=fatjar` (or `core`) do not add `-javaagent:hotswap-agent.jar`, otherwise the agent is loaded twice.

### Run
1. start the application in debug mode, check that the agent and plugins are initialized correctly:

        HOTSWAP AGENT: 9:49:29.548 INFO (org.hotswap.agent.HotswapAgent) - Loading Hotswap agent - unlimited runtime class redefinition.
        HOTSWAP AGENT: 9:49:29.725 INFO (org.hotswap.agent.config.PluginRegistry) - Discovered plugins: [org.hotswap.agent.plugin.hotswapper.HotswapperPlugin, org.hotswap.agent.plugin.jvm.AnonymousClassPatchPlugin, org.hotswap.agent.plugin.hibernate.HibernatePlugin, org.hotswap.agent.plugin.spring.SpringPlugin, org.hotswap.agent.plugin.jetty.JettyPlugin, org.hotswap.agent.plugin.tomcat.TomcatPlugin, org.hotswap.agent.plugin.zk.ZkPlugin, org.hotswap.agent.plugin.logback.LogbackPlugin]
        ...
        HOTSWAP AGENT: 9:49:38.700 INFO (org.hotswap.agent.plugin.spring.SpringPlugin) - Spring plugin initialized - Spring core version '3.2.3.RELEASE'
1. save a changed resource and/or use the HotSwap feature of your IDE to reload changes

{% include links.html %}
