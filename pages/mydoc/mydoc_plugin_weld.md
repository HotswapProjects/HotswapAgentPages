---
title: Weld/CDI Plugin
sidebar: mydoc_sidebar
permalink: mydoc_plugin_weld.html
folder: mydoc
toc: false
---

Support for [Weld/CDI](http://weld.cdi-spec.org/). Register a new bean class into BeanManager. Reinject injection points after 
bean class redefinition. Reload proxy factory after proxied class redefinition. Bean reloading strategy can be specified by
`weld.beanReloadingStrategy` in hotswap-agent.properties.

There are 4 possible values for this parameter:

    # Setup reloading strategy of bean INSTANCE(s) in Weld CONTEXT(s). While bean class is redefined by DCEVM, reloading of bean instances
    # can be customized by this parameter. Available values:
    #   - CLASS_CHANGE - reload bean instance on any class modification, plus reaload on changes specified in
    #     METHOD_FIELD_SIGNATURE_CHANGE and FIELD_SIGNATURE_CHANGE strategies
    #   - METHOD_FIELD_SIGNATURE_CHANGE - reload bean instance on any method/field change. Includes changes specified in
    #     strategy FIELD_SIGNATURE_CHANGE
    #   - FIELD_SIGNATURE_CHANGE - reload bean instance on any field signature change. Includes also field annotation changes
    #   - NEVER - never reload bean (default)
    # weld.beanReloadStrategy=NEVER

Reloading strategy is powerfull mechanism for control the bean reloading according personal preferences. Following strategies can be used:

* `CLASS_CHANGE`  is most general strategy. It reloads bean on any class modification. Strategy ensures bean state consistency for each type of code 
change. On other hand it leads to recreation of session beans and lost of sessions subsequently. 
* `METHOD_SIGNATURE` reload bean if any method or field is added (including constructors) or existing method or field signature is changed. 
It also includes changes of class signature. Any class, field or method annotation is included into signature evaluation as well.
* `FIELD_SIGNATURE_CHANGE` reload bean if any field is added or existing field signature is changed. Briefly speaking if a class data is changed.
* `NEVER` is default strategy and less invasive one. It lefts the responsibility of bean reloading to developer himself. It can lead to session 
or application bean inconsistence. Experienced developer knows the best when the bean modification leads to inconsistent state and should 
be capable to manage bean reloading himself. 

#### Implementation notes:
Plugin initialization is done in `org.jboss.as.weld.deployment.BeanDeploymentArchiveImpl` constructor in case if Weld is running under Wildfly or
in `org.jboss.weld.environment.deployment.WeldBeanDeploymentArchive` in another cases. An instance of BeanDeploymentArchiveAgent is created for each
bean archive found and then it is registered in BdaAgentRegistry. ProxyFactory is patched to call ProxyClassLoadingDelegate methods when proxy class is
created. Each instance of ProxyFactory is registered in WeldPlugin in registeredProxiedBeans map. When proxied bean class is redefined than appropriate
proxy factory instance is found and that is forced to recreate proxy class.

# TODO:
If a new proxy class is created than weld creates common beans instead proxied beans.
