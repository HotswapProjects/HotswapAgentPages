---
title: Configuration
sidebar: mydoc_sidebar
permalink: mydoc_configuration.html
folder: mydoc
toc: false
---
### hotswap-agent.properties
Main Hotswap Agent (HA) configuration file. You can create an empty file or start with [commented content](https://github.com/HotswapProjects/HotswapAgent/blob/master/hotswap-agent-core/src/main/resources/hotswap-agent.properties).

You need to put hotswap-agent.properties file into application runtime classpath. This means:
 
1. maven: src/main/resources
1. webapp: WEB-INF/classes
1. ant, plain java: check your classpath

The hotswap-agent.properties file is loaded per classloader, e.g. each webapp may have seperate configuration.

#### extraClasspath, watchResources
The most important configuration property is 'extraClasspath'. Set semicolon or comma separated list of directories with additional java .class files.
  These directories will be used prior standard classpath.
 
Example: `extraClasspath=target/classes;../my-other-project/classes;C:/libs/gui/classes`

Multiline form example:
`extraClasspath=/my-other-project1/classes; \`<br>
`/my-other-project2/classes; \`<br>
`/my-other-project3/classes; \`<br>
`/my-other-project4/classes;`


Watch resources is similar to extraClasspath, however it will use a resource from this path only after it is modified after application
startup. Sometimes it is not possible to point extraClasspath to your i.e. src/main/resources, because there are multiple replacements 
of resources in a building step (maven filtering resource option). This setting will leave i.e. src/target/classes as default source for resources, 
but after the resource is modified in src/main/resources, the new changed resource is served instead.
Example: `watchResources=src/main/resources`

#### webappDir
Add a directory prior to webapp path (load webapp resources). Load web application resources (such as HTML, JSP, CSS, ...) from this directory 
prior to default processing.

Example: `webappDir=src/main/webapp`

This property is supported for Jetty, Tomcat and Undertow (WildFly). It accepts more directories separated by `;` or `,`.

#### Paths and system properties
A relative path in extraClasspath, watchResources or webappDir is resolved against the working directory of the JVM
(e.g. the server directory), not against the project. If the relative examples above do not work for your server, use absolute paths.

`${name}` in a property value is replaced with the JVM system property `name`. Maven properties such as `${basedir}` are not
available at runtime. To set the project location only once, start the JVM with e.g. `-Dproject.dir=/home/devel/myApp` and use

`webappDir=${project.dir}/web/src/main/webapp;${project.dir}/module-a/src/main/resources/META-INF/resources`

#### disabledPlugins
Comma separated list of plugin names to disable, e.g. `disabledPlugins=Hibernate,Spring`. The names are the ones listed in
`Discovered plugins` at startup.

In the `hotswap-agent.properties` of an application this disables the plugin for that application only: it is not initialized
there and its transformers skip the application classes. The plugin is still listed in `Discovered plugins`, and classes of the
server itself (e.g. JBoss Modules in WildFly) are still patched. To disable a plugin for the whole JVM, use the agent option
`-javaagent:hotswap-agent.jar=disablePlugin=Hibernate` or the system property `-Dhotswapagent.disablePlugin=Hibernate,Spring`.

#### Logging
* `LOGGER=info` - level of the agent log. Levels: `error`, `reload`, `warning`, `info`, `debug`, `trace`.
* `LOGGER.my.package=debug` - level for a package or class of the agent, e.g. `LOGGER.org.hotswap.agent.plugin.spring=debug`.
* `LOGGER_DATETIME_FORMAT=HH:mm:ss.SSS` - time format of the log lines (`SimpleDateFormat`).
* `LOGFILE=agent.log` - write the log into a file, `LOGFILE.append=true` to append to it (default `false`).
* `LOG_TO_CONSOLE=false` - do not print the log to the console (default `true`).

The log level can also be set as a system property, e.g. `-DLOGGER=debug`.

#### Class loaders
By default the agent initializes plugins in every class loader. To limit it, set one of these properties
(a comma separated list of regular expressions matched against the class name of the class loader, you cannot set both):
* `includedClassLoaderPatterns` - initialize only class loaders whose class name matches.
* `excludedClassLoaderPatterns` - skip class loaders whose class name matches, e.g. `excludedClassLoaderPatterns=jdk.nashorn.*`.

#### Custom plugins
`pluginPackages=com.example.hotswap` - comma separated list of packages with your own plugins (classes annotated with `@Plugin`)
on the class path of the application. See [Custom plugins](mydoc_custom_plugins.html).

#### Spring
`spring.basePackagePrefix=com.example` - comma separated list of package prefixes of your Spring beans. It is needed when
component scan is not used, and it can limit the beans handled by the agent. When it is set, the agent does not register
the packages of `<context:component-scan>` / `@ComponentScan`, so new bean classes added at runtime are not registered.
Do not set it if you use component scan and want to add new beans.

#### Plugin specific properties
Some plugins have their own properties, e.g. `weld.beanReloadStrategy` (see [Weld](mydoc_plugin_weld.html)) or
`osgiEquinox.debugMode` (see [OsgiEquinox](mydoc_plugin_osgiequinox.html)). All properties with their default values are
in the [default hotswap-agent.properties](https://github.com/HotswapProjects/HotswapAgent/blob/master/hotswap-agent-core/src/main/resources/hotswap-agent.properties).

### Standard setup

#### Multi-module maven project
Parts of your project are built into .jar files, which are finally assembled usually into WEB-INF/lib directory of the webapp. 
Without HA you have to rebuild the module *and* restart the application.

Example: `extraClasspath=../my-other-module1/classes;../my-other-module2/classes`

#### Tomcat, Jetty
You may start the server at any location from .war file and point web resources, class files and resource files to your development directory.   

Example: 
`extraClasspath=/home/devel/myApp/classes;/home/devel/myApp/resources;/home/devel/myLib/classes` 
`webappDir=/home/devel/myApp/web` 

#### Auto hotswap
Usually you will launch debugging session from your IDE and use standard hotswap feature. If you do not want to use debugging session 
for some reason or if you want to enable hotswap at runtime environment, set `autoHotswap=true`. 

This feature may be used even on production environment to apply a hot patch. 

With `autoHotswap=true` the classes are reloaded with the Java Instrumentation API. To reload them with JPDA (the debugger
API) instead, start the JVM with a debug port, e.g. `-agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=8000`,
and set `autoHotswap.port=8000`.

### Agent options
Options of the agent are set after the jar path, separated by `,`, e.g.
`-javaagent:hotswap-agent.jar=disablePlugin=Hibernate,disablePlugin=Spring,autoHotswap=true`.
With JetBrains Runtime and `-XX:HotswapAgent=fatjar` the JVM loads the agent without options. There use the system properties
below, or the `external` mode with `-javaagent` (see [Quick Start JDK 17+](mydoc_quickstart-jdk17.html)).

* `disablePlugin=Name` - disable a plugin for the whole JVM. Repeat it for more plugins.
* `autoHotswap=true` - enable `autoHotswap` for all applications.
* `propertiesFilePath=/path/to/hotswap-agent.properties` - use this file instead of the `hotswap-agent.properties` files
  found on the class path.
* `LOGGER=debug` - level of the agent log.

System properties (they work also with `-XX:HotswapAgent=fatjar`):
* `-Dhotswapagent.disablePlugin=Hibernate,Spring` - disable plugins for the whole JVM.
* `-DLOGGER=debug` - level of the agent log. Other properties of the main `hotswap-agent.properties` can be set this way too.

{% include links.html %}
