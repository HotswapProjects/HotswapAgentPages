---
title: Eclipse setup
sidebar: mydoc_sidebar
permalink: mydoc_setup_eclipse.html
folder: mydoc
toc: false
---

**Step-1:** In Eclipse setup `Runtime Environment` (Tomcat Server in this example) - JRE must be mapped to the same JRE of JDK in which DCEVM is patched (look at [quick start][mydoc_quickstart] how to setup DCEVM).

{% include image.html file="EclipseSetup-01.png" %}

**Step-2:** Add "-XXaltjvm=dcevm -javaagent:<PATH>\HotswapAgent.jar" in VM Arguments. 

{% include image.html file="EclipseSetup-02.png" %}

**Step-3:** If you use servlet container like Tomcat, JBoss, Glassfish etc., disable option **Auto Reload** (in web modules).
This is most important step, otherwise you will not see power of Hotswap Agent in step-4.

{% include image.html file="EclipseSetup-03.png" %}

**Step-4:** Run your application or servlet container (Tomcat, JBoss, Glassfish ...) in Debug mode and enjoy java coding.
When you start your server in debug mode, you should see messages like below in Eclipse Console.

{% include image.html file="EclipseSetup-04.png" %}

Now if you do code changes in Java as well as configuration files of supported plugins (i.e. logback.xml), those would be updated without server restart.

{% include image.html file="EclipseSetup-05.png" %}

{% include links.html %}
