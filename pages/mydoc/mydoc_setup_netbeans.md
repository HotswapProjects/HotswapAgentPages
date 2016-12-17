---
title: Netbeans setup
sidebar: mydoc_sidebar
permalink: mydoc_setup_netbeans.html
folder: mydoc
toc: false
---

**Compile on save:**
{% include image.html file="NetbeansSetup-01.png" %}

**Enable automatic Hotswap after compile:**
{% include image.html file="NetbeansSetup-02.png" %}
If you don't enable this feature, you will need to hotswap changes manually by 

**Maven actions**
If you run your project with a maven action (usually a plugin like maven-jetty-plugin or maven-tomcat-plugin) setup MAVEN_OPTS for an appropriate target.

In the project properties dialog Actions -> Debug project -> Set Properties add Env.MAVEN_OPTS= .. your configuration ?
{% include image.html file="NetbeansSetup-03.png" %}

**Setup application server**
Or if you run your application on an application server (Tomcat, JBoss, Glassfish), use Platform VM options.
{% include image.html file="NetbeansSetup-04.png" %}

