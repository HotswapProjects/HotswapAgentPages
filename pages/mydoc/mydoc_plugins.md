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

* [CXF]({{ site.data.mydoc_plugin_cxf.link }}) (3.x) - redefine JAXRS resource after resource class redefinition, reinject instance if integrated with Spring and CDI (Weld/OWB).
* [Deltaspike]({{ site.data.mydoc_plugin_deltaspike.link }}) (1.x) - messages, ViewConfig, repository, proxy reloading.
* [ELResolver]({{ site.data.mydoc_plugin_el_resolver.link }}) 2.2 (JuelEL, Appache Commons EL, Oracle EL 3.0)- clear ELResolver cache on class change. Support hotswap for #{...} expressions.
* [FreeMarker]({{ site.data.mydoc_plugin_freemarker.link }}) - clear the Apache Freemarker beans class-introspection cache on class definition change.
* [Hibernate v3]({{ site.data.mydoc_plugin_hibernate3.link }}) (3x,4x,5x) - Reload Hibernate configuration after entity create/change.
* [Hibernate v4,v5]({{ site.data.mydoc_plugin_hibernate45.link }}) (3x,4x,5x) - Reload Hibernate configuration after entity create/change.
* [Jersey 1]({{ site.data.mydoc_plugin_jersey1.link }}) - reload Jersey1 container after root resource or provider class definition or redefinition.
* [Jersey 2]({{ site.data.mydoc_plugin_jersey2.link }}) - reload Jersey2 container after root resource or provider class definition or redefinition.
* [JSF]({{ site.data.mydoc_plugin_jsf }}/README.md) (mojarra 2.1, 2.2, MyFaces 2.2) - support for application resource bundle changes (properties files).
* [Logback]({{ site.data.mydoc_plugin_logback.link }}) - Logback configuration reload.
* [Log4j2]({{ site.data.mydoc_plugin_log4j2.link }}) - Log4j2 configuration reload.
* [MyBatis]({{ site.data.mydoc_plugin_mybatis.link }}) (5.3) - reload configuration after mapper file changes
* [OpenWebBeans]({{ site.data.mydoc_plugin_owb.link }}) (CDI) (1.x, 2.x) - reload bean class definition after class definition/change. Beans can be reloaded according strategy defined in property file.
* [OsgiEquinox]({{ site.data.mydoc_plugin_osgiequinox.link }}) - Hotswap support for Eclipse plugin or Eclipse platform development.
* [RestEasy]({{ site.data.mydoc_plugin_resteasy_registry.link }}) (2.x, 3.x) - Cleanups and registers class redefinitions.
* [Spring]({{ site.data.mydoc_plugin_spring.link }}) (3x, 4.x) - Reload Spring configuration after class definition/change.
* [Vaadin]({{ site.data.mydoc_plugin_vaadin.link }}) (10.x) - Update routes, template models and in practice anything on the fly.
* [WebObjects]({{ site.data.mydoc_plugin_webobjects.link }}) - Clear key value coding, component, action and validation caches after class change.
* [Weld]({{ site.data.mydoc_plugin_weld.link }}) (CDI) (2.2,2.3,3.x) - reload bean class definition after class definition/change. Beans can be reloaded according strategy defined in property file.
* [Wicket]({{ site.data.mydoc_plugin_wicket.link }}) - clear wicket caches if property files are changed
* [WildFlyELResolver]({{ site.data.mydoc_plugin_wildfly_el.link }}) - Clear BeanELResolver after any class redefinition.
* [Vaadin]({{ site.data.mydoc_plugin_vaadin.link }}) Vaadin Framework (https://vaadin.com) 
* [ZK]({{ site.data.mydoc_plugin_zk.link }}) (5x-7x) - ZK Framework (http://www.zkoss.org/). Change library properties default values to disable caches, maintains Label cache and bean resolver cache.

#### Servlet containers and application servers plugins:

* [JBossModules]({{ site.data.mydoc_plugin_jbossmodules.link }}) - add extra class path to JBoss's module class loader. (Wildfly)
* [Jetty]({{ site.data.mydoc_plugin_jetty.link }}) - add extra classpath to the app classloader. All versions supporting WebAppContext.getExtraClasspath should be supported.
* [Tomcat]({{ site.data.mydoc_plugin_tomcat.link }}) (7.x, 8.x) configure Apache Tomcat with extraClasspath property.
* [Undertow]({{ site.data.mydoc_plugin_undertow.link }}) - add extra classpath, watchResources and webappDir to the undertow's resource manager.

#### JVM plugins - hotswapping enhancements:

* [AnonymousClassPatch]({{ site.data.mydoc_plugin_anonymous_class_patch.link }}) - Swap anonymous inner class names to avoid not compatible changes.
* [ClassInit]({{ site.data.mydoc_plugin_class_init.link }}) - initializes new static members/enum values after class/enum redefinition and keeps surviving static values. (Fix of known DCEVM)
* [Hotswapper]({{ site.data.mydoc_plugin_hotswapper.link }}) - Watch for any class file change and reload (hotswap) it on the fly via Java Platform Debugger Architecture (JPDA)
* [Proxy]({{ site.data.mydoc_plugin_proxy.link }}) (supported com.sun.proxy, CGlib) - redefines proxy classes that implement or extend changed interfaces or classes.
