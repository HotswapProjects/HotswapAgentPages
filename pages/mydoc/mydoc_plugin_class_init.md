---
title: Class Init Plugin
sidebar: mydoc_sidebar
permalink: mydoc_plugin_class_init.html
folder: doc
toc: false
---

Initializes new static members after class redefinition. DCEVM copies values of all surviving static members 
from old class to the new class, but new static members are left uninitialized. That applies to enumerations 
as well. ClassInit plugin fixes this issue. Values of all surviving static members are kept after redefinition and 
initialization is done only for new static members. If an enumeration is redefined, all surviving enumeration 
values are kept, so it is guaranteed that enumeration value Enum.X' after redefinition is identical to value 
Enum.X before redefiniton.

Known issues
---------------
Ordinal values of a redefined enumeration value X'.ordinal() values can be different than original one

    X.ordinal() != X'.ordinal()

#### Implementation notes:
Content of `<clinit>` method is copied to `__ha_clinit`. Assignment to surviving members are removed using javassist.
`__ha_clinit` method is called after class is redefined in JVM after timeout (100ms).
