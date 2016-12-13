---
title: Eclipse setup
sidebar: mydoc_sidebar
permalink: mydoc_setup_eclipse.html
folder: mydoc
toc: false
---

**Step-1:** Install ?jvm.dll? DCEVM patch in JDK

Follow the same steps which are mentioned on [HotswapAgent quick start page - Install section](http://hotswapagent.org/quick-start) to patch Java Hotspot(r) file in JDK 1.7_xy and download HotswapAgent.jar file.

**Step-2:** In Eclipse - Tomcat Server - Runtime Environment - JRE must be mapped to the same JRE of JDK in which DECVM is patched in step-1

{% include image.html file="EclipseSetup-01.png" %}

**Step-3:** Tomcat - Add "-XXaltjvm=dcevm -javaagent:<PATH>\HotswapAgent.jar" in VM Arguments.

{% include image.html file="EclipseSetup-02.png" %}

**Step-4:** Disable ?Auto Reload? in Tomcat web modules
This is most important step, otherwise you will not see power of Hotswap Agent in step-5.

{% include image.html file="EclipseSetup-03.png" %}

**Step-5:** Run Tomcat in Debug mode and Enjoy java coding.
When you start your server in debug mode, you should see messages like below in Eclipse Console.

{% include image.html file="EclipseSetup-04.png" %}

Now if you do code changes in java as well as configuration files of supported plugins (i.e. logback.xml), those would be ready for unit testing immediately without server restart.

{% include image.html file="EclipseSetup-05.png" %}
