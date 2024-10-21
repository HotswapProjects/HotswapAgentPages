---
title: Intellij IDEA setup
sidebar: mydoc_sidebar
permalink: mydoc_setup_intellij_idea.html
folder: mydoc
toc: false
---
## Start with HotSwapHelper plugin for IntelliJ IDEA.

### The plugin will automatically add vm option for hotSwapAgent part for you.
### Plugin source code: [github](https://github.com/gejun123456/HotSwapHelper)

### steps:
1. Install HotSwapHelper [plugin](https://plugins.jetbrains.com/plugin/25171-hotswaphelper) for IntelliJ IDEA.  {% include image.html file="HotSwapHelper-01.png" %}
2. After install, there will have a debug with hotSwap action after debug action.  {% include image.html file="HotSwapHelper-02.png" %}
3. After click the action,You will see HOTSWAP AGENT notification in your console in case if setup was correctly done.  {% include image.html file="IdeaPlugin-03.png" %}
4. Be sure that you have `"Reload classes after compilation: Always"` ON in IntelliJ IDEA in HotSwap section in your IDEA preferences.  {% include image.html file="IdeaPlugin-04.png" %}
5. To re-deploying changed classes in IDEA press keys combination (: `Command+Shift+F9`/ ⊞: `Ctrl+Shift+F9`)

### Happy:heart: HotSwapping!
1. `change` method name & then press (: `Command+Shift+F9`/ ⊞: `Ctrl+Shift+F9`) {% include image.html file="IdeaPlugin-05.gif" %}
2. `add new` method & then press (: `Command+Shift+F9`/ ⊞: `Ctrl+Shift+F9`) {% include image.html file="IdeaPlugin-06.gif" %}
3. change multiple class or xml, press (⌘: `Command+F9`/ ⊞: `Ctrl+F9`) or use build module.

### Provide external agent file, the plugin has bundled one agent file, if you want to use your own agent file.

1. In Setting -> HotSwapHelper set use external agent file path.  {% include image.html file="HotSwapHelper-03.png" %}


## Other way: it's explicit agent configuration without plugin.

**Compile on save:**
You need to compile the source file first. Although IDEA does not contain this feature, you can simulate it with keymap settings and  map CTRL+S to the Compile action (it gets saved anyway):

{% include image.html file="IdeaSetup-04.png" %}
You can always run Compile file (CTRL+SHIFT+F9) or Build project (CTRL+F9) manually.

**Enable automatic Hotswap after compile**
{% include image.html file="IdeaSetup-05.png" %}
If you don't enable this feature, you will need to hotswap changes manually by Run -> Reload changed files.

**Maven Run/Debug configuration**
If you run your project with a maven action (usually a plugin like maven-jetty-plugin or maven-tomcat-plugin), use standard setup:

{% include image.html file="IdeaSetup-01.png" %}

And add VM Options for dcevm and javaagent.  If your project JDK does not contain DCEVM patch, select alternative JRE with DCEVM.

{% include image.html file="IdeaSetup-02.png" %}

**Setup application server**
Or if you run your application on an application server (Tomcat, JBoss, Glassfish), just set VM options for DCEVM and javaagent. If your project JDK does not contain DCEVM patch, select alternative JRE with DCEVM.

{% include image.html file="IdeaSetup-03.png" %}
