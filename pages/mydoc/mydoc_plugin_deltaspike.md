---
title: Deltaspike Plugin
sidebar: mydoc_sidebar
permalink: mydoc_plugin_deltaspike.html
folder: mydoc
toc: false
---
Reload instances following on appropriate class redefinition:

* DeltaSpike proxy class
* Partial Bean
* Messages + JsfMessages
* Repository component in DeltaSpike data module.
* View Config

#### Implementation notes:
Plugin registers itselfs in following class instances initialization:

* `org.apache.deltaspike.partialbean.impl.PartialBeanBindingExtension`
* `org.apache.deltaspike.proxy.api.DeltaSpikeProxyFactory`
* `org.apache.deltaspike.proxy.impl.AsmProxyClassGenerator`
* `org.apache.deltaspike.data.impl.meta.RepositoryComponent`
* `org.apache.deltaspike.jsf.impl.config.view.ViewConfigExtension`

