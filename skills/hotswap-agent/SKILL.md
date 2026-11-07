---
name: hotswap-agent
description: Reload changed Java classes in a running JVM with HotswapAgent instead of restarting the application. Use when developing or debugging a Java application (Spring, Spring Boot, Jakarta EE, Tomcat, WildFly, ...) whose restart is slow, to apply code changes without losing the running state.
---

# HotswapAgent for coding agents

HotswapAgent reloads changed classes and refreshes frameworks (Spring beans, request mappings, Hibernate, CDI, ...) in a
running JVM. You do not use an IDE debugger, so use `autoHotswap`: the agent watches the compiled class files and
reloads them when your build tool writes them.

## 1. Check the JVM
Use JetBrains Runtime (JBR) 17, 21 or 25 with the agent jar at `<JBR>/lib/hotswap/hotswap-agent.jar`.
- `java -XX:+AllowEnhancedClassRedefinition -version` must not fail. If it fails, the JVM supports only changes of method
  bodies. Download JBR from https://github.com/JetBrains/JetBrainsRuntime/releases.
- If `<JBR>/lib/hotswap/hotswap-agent.jar` is missing, download the latest `hotswap-agent-*.jar` from
  https://github.com/HotswapProjects/HotswapAgent/releases and copy it there as `hotswap-agent.jar` (no version in the name).
- You only need JBR to run the application. Compile with the JDK the project already uses.

## 2. Start the application with the agent
Add these JVM options to how the project starts the application (plain `java`, the Spring Boot plugin JVM arguments,
Gradle `jvmArgs`, the server's `JAVA_OPTS`, ...):

```
-XX:+AllowEnhancedClassRedefinition -XX:HotswapAgent=fatjar -DautoHotswap=true -DLOGFILE=hotswap-agent.log
```

- Run the application from the class directories the build writes (e.g. `target/classes`, `build/classes/java/main`),
  not from a packaged jar. Changes are only picked up from directories.
- Do not add `-javaagent:hotswap-agent.jar` as well, the agent would be loaded twice.
- `LOGFILE` is relative to the working directory of the JVM.

Check the console output at startup:
- `Loading Hotswap agent <version>` - the agent is loaded.
- `Plugin 'org.hotswap.agent.plugin.hotswapper.HotswapperPlugin' initialized` - autoHotswap is active.
- Framework plugins, e.g. `Spring plugin initialized`.

## 3. Change, compile, check
1. Edit the source.
2. Compile only, do not restart: `mvn compile` (or `mvn -o -q compile`), `./gradlew classes`.
3. Wait until `hotswap-agent.log` gets a new line `Reloading classes [...] (autoHotswap)` (usually a few seconds).
4. Check the behavior (call the endpoint, run the request, read the application log).

New methods, fields, classes, Spring beans and request mappings work without a restart.

## 4. When the reload fails, restart
A class change the JVM cannot apply is rejected and the application keeps running the old class. Check the console
(stderr) of the application, not only `hotswap-agent.log`:

```
Exception in thread "..." java.lang.IllegalStateException: Unable to redefine classes
Caused by: java.lang.UnsupportedOperationException: class redefinition failed: attempted to change superclass or interfaces
```

- Changing the superclass or the implemented interfaces is not supported. Restart the application for such a change.
- After a rejected change, revert it or restart. Until then, later reloads can fail as well.
- Restart also when there is an `ERROR` in the agent log, when no `Reloading classes` line appears after the compilation,
  or when the result looks inconsistent. A restart gives a reliable result, do not guess.

## Configuration
Options can also be put into `hotswap-agent.properties` in the resources of the application, e.g. `extraClasspath`
(class directories of other modules), `disabledPlugins`, `LOGGER=debug`. Reference:
https://hotswapagent.org/mydoc_configuration.html
