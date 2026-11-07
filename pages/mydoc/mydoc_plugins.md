---
title: Plugins
tags: []
keywords: plugins, framework
sidebar: mydoc_sidebar
permalink: mydoc_plugins.html
folder: mydoc
toc: false
---
Plugins administered by Hotswap agent are usually targeted towards a specific framework. For example Spring plugin
uses agent services to:

* Modify root Spring classes to get Spring contexts and registered scan path
* Watch for any resource change on a scan path
* Watch for a hotswap of a class file within a scan path package
* Reload bean definition after a change
* ... and many other

#### Java frameworks plugins:

* [CXF](mydoc_plugin_cxf.html) (3.x) - redefine JAXRS resource after resource class redefinition, reinject instance if integrated with Spring and CDI (Weld/OWB).
* [Deltaspike](mydoc_plugin_deltaspike.html) (1.x, Jakarta: 2.x) - messages, ViewConfig, repository, proxy reloading.
* [ELResolver](mydoc_plugin_el_resolver.html) 2.2 (JuelEL, Appache Commons EL, Oracle EL 3.0)- clear ELResolver cache on class change. Support hotswap for #{...} expressions.
* [FreeMarker](mydoc_plugin_freemarker.html) - clear the Apache Freemarker beans class-introspection cache on class definition change.
* [Hibernate v3](mydoc_plugin_hibernate3.html) (3.x) - Reload Hibernate configuration after entity create/change.
* [Hibernate v4,v5](mydoc_plugin_hibernate45.html) (4.x, 5.x, Jakarta: 5.5 - 6.x) - Reload Hibernate configuration after entity create/change.
* [iBatis](mydoc_plugin_ibatis.html) - iBatis configuration reload.
* [IDEA](mydoc_plugin_idea.html) - support for IntelliJ IDEA development in IDEA
* [Jackson](mydoc_plugin_jackson.html) - clears Jackson internal caches when a class is redefined.
* [Jersey 1](mydoc_plugin_jersey1.html) - reload Jersey1 container after root resource or provider class definition or redefinition.
* [Jersey 2](mydoc_plugin_jersey2.html) - reload Jersey2 container after root resource or provider class definition or redefinition.
* [JSF](mydoc_plugin_jsf.html) (Mojarra, MyFaces) - support for application resource bundle changes (properties files).
* [Logback](mydoc_plugin_logback.html) - Logback configuration reload.
* [Log4j2](mydoc_plugin_log4j2.html) - Log4j2 configuration reload.
* [MyBatis](mydoc_plugin_mybatis.html) (3.5) - reload configuration after mapper file changes
* MyBatis-Plus (3.2 - 3.5) - reload MyBatis-Plus configuration after mapper file changes.
* [OmniFaces](mydoc_plugin_omnifaces.html) - support for ViewScoped beans reinjection/reloading.
* [OpenWebBeans](mydoc_plugin_owb.html) (CDI) (1.x, 2.x) - reload bean class definition after class definition/change. Beans can be reloaded according strategy defined in property file. Jakarta: 4.x.
* [OsgiEquinox](mydoc_plugin_osgiequinox.html) - Hotswap support for Eclipse plugin or Eclipse platform development.
* [RestEasy](mydoc_plugin_resteasy_registry.html) (2.x, 3.x) - Cleanups and registers class redefinitions.
* [Spring](mydoc_plugin_spring.html) (3.x - 7.0) - Reload Spring configuration after class definition/change.
* Spring Boot - reload Spring Boot after a change of `application.properties` / `application.yaml`.
* Sponge (11) - register newly added listeners of a changed listener class.
* Thymeleaf (3.0) - clear the template cache when a template is modified.
* [Vaadin](mydoc_plugin_vaadin.html) (up to 25.x) - Update routes, template models and in practice anything on the fly.
* [WebObjects](mydoc_plugin_webobjects.html) - Clear key value coding, component, action and validation caches after class change.
* [Weld](mydoc_plugin_weld.html) (CDI) (2.2, 2.3, 3.x, Jakarta: 5.x) - reload bean class definition after class definition/change. Beans can be reloaded according strategy defined in property file.
* Velocity - enhance Spring's `VelocityEngineFactory`.
* [Wicket](mydoc_plugin_wicket.html) - clear wicket caches if property files are changed
* [WildFlyELResolver](mydoc_plugin_wildfly_el.html) - Clear BeanELResolver after any class redefinition.
* [ZK](mydoc_plugin_zk.html) (5x-7x) - ZK Framework (http://www.zkoss.org/). Change library properties default values to disable caches, maintains Label cache and bean resolver cache.

#### Servlet containers and application servers plugins:

* GlassFish - support for the GlassFish server (GlassFish 7).
* [JBossModules](mydoc_plugin_jbossmodules.html) - add extra class path to JBoss's module class loader. (Wildfly)
* [Jetty](mydoc_plugin_jetty.html) - add extra classpath to the app classloader. All versions supporting WebAppContext.getExtraClasspath should be supported.
* [Tomcat](mydoc_plugin_tomcat.html) (7.x - 9.x) configure Apache Tomcat with extraClasspath property.
* [Undertow](mydoc_plugin_undertow.html) - add extra classpath, watchResources and webappDir to the undertow's resource manager.
* [Weblogic](mydoc_plugin_weblogic.html) - add extra classpath to the app classloader.

#### JVM plugins - hotswapping enhancements:

* [AnonymousClassPatch](mydoc_plugin_anonymous_class_patch.html) - Swap anonymous inner class names to avoid not compatible changes.
* [ClassInit](mydoc_plugin_class_init.html) - initializes new static members/enum values after class/enum redefinition and keeps surviving static values. (Fix of known DCEVM)
* [Hotswapper](mydoc_plugin_hotswapper.html) - with `autoHotswap=true`, watch for any class file change and reload (hotswap) it on the fly (Instrumentation API, or JPDA with `autoHotswap.port`).
* [JDK](mydoc_plugin_jdk.html) - clears `java.beans.Introspector` and serialization caches of the JDK after class redefinition.
* [Proxy](mydoc_plugin_proxy.html) (supported com.sun.proxy, CGlib) - redefines proxy classes that implement or extend changed interfaces or classes.
* WatchResources - support for the `watchResources` configuration property.
