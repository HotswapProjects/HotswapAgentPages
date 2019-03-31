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

#### extraClaspath, watchResources
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

This property is currently supported only for Jetty and Tomcat servlet containers.

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

{% include links.html %}
