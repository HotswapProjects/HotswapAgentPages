---
title: Using HotswapAgent with AI coding agents
sidebar: mydoc_sidebar
permalink: mydoc_ai_agents.html
folder: mydoc
toc: false
---
A coding agent (Claude Code, Codex, Cursor, ...) changes code and checks the result many times in a row. With HotswapAgent
it can apply a change to the running application in a few seconds instead of restarting it. The agent does not use the
hotswap action of an IDE debugger, so it needs `autoHotswap`: HotswapAgent watches the compiled class files and reloads
them when the build tool writes them.

### Agent skill
The [hotswap-agent skill](https://raw.githubusercontent.com/HotswapProjects/HotswapAgentPages/gh-pages/skills/hotswap-agent/SKILL.md) contains the instructions below in the
[Agent Skills](https://agentskills.io) format (`SKILL.md`). To use it in Claude Code, save it as
`.claude/skills/hotswap-agent/SKILL.md` in your project (or in `~/.claude/skills/` for all projects):

```
mkdir -p .claude/skills/hotswap-agent
curl -o .claude/skills/hotswap-agent/SKILL.md https://raw.githubusercontent.com/HotswapProjects/HotswapAgentPages/gh-pages/skills/hotswap-agent/SKILL.md
```

For other agents, add the short version below to the instructions file of the project (`AGENTS.md`, `CLAUDE.md`, ...).

### Short version for AGENTS.md

```
## Reloading Java changes
The application runs with HotswapAgent on JetBrains Runtime. Do not restart it after a code change:
- start it with -XX:+AllowEnhancedClassRedefinition -XX:HotswapAgent=fatjar -DautoHotswap=true -DLOGFILE=hotswap-agent.log,
  from the class directories of the build (e.g. target/classes), not from a jar
- after a change run only the compilation (mvn compile / ./gradlew classes)
- wait for "Reloading classes [...] (autoHotswap)" in hotswap-agent.log, then check the behavior
- if the console shows "Unable to redefine classes" (e.g. a changed superclass or interface), revert the change or restart
- restart when unsure, a restart gives a reliable result
```

### How it works
1. Run the application on JetBrains Runtime with `<JBR>/lib/hotswap/hotswap-agent.jar`, see
   [Quick Start JDK 17+](mydoc_quickstart-jdk17.html), with the options
   `-XX:+AllowEnhancedClassRedefinition -XX:HotswapAgent=fatjar -DautoHotswap=true -DLOGFILE=hotswap-agent.log`.
   No `hotswap-agent.properties` is needed for this. The application must run from the class directories of the build
   (e.g. `target/classes`), changes in a packaged jar are not picked up.
2. At startup the console shows `Loading Hotswap agent <version>` and
   `Plugin 'org.hotswap.agent.plugin.hotswapper.HotswapperPlugin' initialized` (autoHotswap is active).
3. After a change the agent runs only the compilation (`mvn compile`, `./gradlew classes`). A few seconds later
   `hotswap-agent.log` contains `Reloading classes [...] (autoHotswap)` and the change is active, including new methods,
   fields, classes, Spring beans and request mappings.
4. A change the JVM cannot apply, e.g. a changed superclass or interface, is rejected and the application keeps the old
   class. The console (stderr) shows `Unable to redefine classes` with the cause, e.g.
   `attempted to change superclass or interfaces`. Revert such a change or restart the application.

The agent should prefer a restart over guessing when the result looks inconsistent: a reload changes the running state,
and a restart gives a reliable result.

Tested with JetBrains Runtime 21, HotswapAgent 2.0.4 and a Spring Boot 2.7 application built with Maven.

{% include links.html %}
