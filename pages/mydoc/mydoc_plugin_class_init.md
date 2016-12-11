---
title: Class Init Plugin
sidebar: mydoc_sidebar
permalink: mydoc_plugin_class_init.html
folder: doc
toc: false
---

Initialize new static members. When a class is redefined, DCEVM copies values from all surviving static members
to the new class, but it leaves all new static members uninitialized. That applies to enumerations as well. ClassInit
plugin fixes this issue. After redefinition all surviving static values are kept and initialization is done
only for new static members. After redefinition of an enumeration all surviving enumeration values are kept,
so it is guaranteed that surviving enumeration value Enum.X' is identical to value before redefinition Enum.X.

Known issues
---------------
Ordinal values of a redefined enumeration value X'.ordinal() values can be different than original one

    X.ordinal() != X'.ordinal()

#### Implementation notes:
Content of '<clinit>' method is copied to '__ha_clinit'. Assignment to surviving members are removed using javassist.
'__ha_clinit' method is called after class is redefined in JVM after timeout (100ms).
