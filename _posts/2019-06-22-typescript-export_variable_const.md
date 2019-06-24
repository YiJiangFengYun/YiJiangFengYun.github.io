---
layout: post
title: Typescript -- Exported variable should be constant.
---


# Exported variable should be constant.  

Because if it is not constant and try to change its value in its module file. The change will be invalid when typescript is converted to commonjs.

Builded js script will store value of exported variable to map with the variable name. and then Changing its value don't effect on value in the map. so if the origin value of the variable is null when exporting and change value, but its value is still null to user of the varible of the module.

It is not like es6 module export. Es6 module use a shared memory to store a value, module and module users use a reference to get the value.


