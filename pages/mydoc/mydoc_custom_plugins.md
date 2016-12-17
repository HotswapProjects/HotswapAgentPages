---
title: Custom Plugin
sidebar: mydoc_sidebar
permalink: mydoc_custom_plugins.html
folder: mydoc
toc: false
---

You can write plugin directly as a part of your application. Set `pluginPackages=your.plugin.package` inside
your `hotswap-agent.properties` configuration to discover `@Plugin` annotated classes. You will also need
agent JAR dependency to compile, but be careful NOT to add the JAR to your application, it must be loaded only
as a javaagent. Maven dependency:

        <dependency>
            <groupId>org.hotswap.agent</groupId>
            <artifactId>HotswapAgent</artifactId>
            <version>${project.version}</version>
            <scope>provided</scope>
        </dependency>
(Note that the JAR is not yet in central maven repository - you need to build it from source first).

Example:

        @Plugin(name = "MyPlugin")
        public class MyPlugin {
        
            @OnClassLoadEvent(classNameRegexp = ".*", events = LoadEvent.REDEFINE)
            public static void onAnyReload() {
                MyCache.clear();
            }
        
            @OnResourceFileEvent(path = "/", filter = ".*.resource")
            public void onResourceChanged() {
                MyResourceCache.clear();
            }
        }
        
        
See [ExamplePlugin](https://github.com/HotswapProjects/HotswapAgentExamples/blob/master/custom-plugin/src/main/java/org/hotswap/agent/example/plugin/ExamplePlugin.java)
(part of TestApplication) to go through a commented simple plugin. Read [agent readme](https://github.com/HotswapProjects/HotswapAgent/blob/master/README.md)
 to understand agent concepts. Check existing plugins source code for more examples.
