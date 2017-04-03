---
title: Intellij IDEA setup
sidebar: mydoc_sidebar
permalink: mydoc_setup_intellij_idea.html
folder: mydoc
toc: false
---
## Start with `Hot`SwapAgent plugin for IntelliJ IDEA.
| steps: |  
| ----- | 
|1. Install HotSwapAgent [plugin](https://plugins.jetbrains.com/plugin/9552-hotswapagent) for IntelliJ IDEA.
![plugin](https://cloud.githubusercontent.com/assets/1389501/24604200/29589bfa-1864-11e7-9dd3-266e08401f24.png)|
|2. Enable HotSwapAgent plugin for all configurations (or one by one).
![enable](https://cloud.githubusercontent.com/assets/1389501/24604139/ed4eba0e-1863-11e7-8dd4-a6b81eb86fb9.png)|
|3. You will see HOTSWAP AGENT notification in your console in case if setup was correctly done.
![notnotification](https://cloud.githubusercontent.com/assets/1389501/24604444/150f084a-1865-11e7-876b-5615c73bc989.png)|
|4. Be sure that you have `"Reload classes after compilation: Always"` ON in IntelliJ IDEA in HotSwap section in your IDEA preferences.
![image](https://cloud.githubusercontent.com/assets/1389501/23870558/12ddd752-0827-11e7-9689-2015c38ebaea.png)|
|5. To re-deploying changed classes in IDEA press keys combination (: `Command+Shift+F9`/ ⊞: `Ctrl+Shift+F9`)|

### Happy:heart: `Hot` Swapping!
||  
| ----- |
|1. `change` method name & then press (: `Command+Shift+F9`/ ⊞: `Ctrl+Shift+F9`)
![change_01](https://cloud.githubusercontent.com/assets/1389501/24606429/56005bc6-186d-11e7-8793-a5ccc7e1b486.gif)|   
|2. `add new` method & then press (: `Command+Shift+F9`/ ⊞: `Ctrl+Shift+F9`)
![change_02](https://cloud.githubusercontent.com/assets/1389501/24606440/5d8d64ec-186d-11e7-970c-f32a1088886b.gif)|



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
