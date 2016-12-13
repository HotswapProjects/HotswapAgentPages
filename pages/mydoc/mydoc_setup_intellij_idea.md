---
title: Intellij IDEA setup
sidebar: mydoc_sidebar
permalink: mydoc_setup_intellij_idea.html
folder: mydoc
toc: false
---

**Compile on save:**
You need to compile the source file first. Although IDEA does not contain this feature, you can simulate it with keymap settings and  map CTRL+S to the Compile action (it gets saved anyway):

{% include image.html file="IdeaSetup-04.png" %}
You can always run Compile file (CTRL+SHIFT+F9) or Build project (CTRL+F9) manually.

**Enable automatic Hotswap after compile**
{% include image.html file="IdeaSetup-05.png" %}
If you don?t enable this feature, you will need to hotswap changes manually by Run -> Reload changed files.

**Maven Run/Debug configuration**
If you run your project with a maven action (usually a plugin like maven-jetty-plugin or maven-tomcat-plugin), use standard setup:

{% include image.html file="IdeaSetup-01.png" %}

And add VM Options for dcevm and javaagent.  If your project JDK does not contain DCEVM patch, select alternative JRE with DCEVM.

{% include image.html file="IdeaSetup-02.png" %}

**Setup application server**
Or if you run your application on an application server (Tomcat, JBoss, Glassfish), just set VM options for DCEVM and javaagent. If your project JDK does not contain DCEVM patch, select alternative JRE with DCEVM.

{% include image.html file="IdeaSetup-03.png" %}
