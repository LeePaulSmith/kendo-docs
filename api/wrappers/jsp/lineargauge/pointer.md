---
title: linearGauge-pointer
slug: jsp-linearGauge-pointer
tags: api, java
publish: true
---

# \<kendo:linearGauge-pointer\>
A JSP tag representing Kendo Pointer.

#### Example
    <kendo:linearGauge>
        <kendo:linearGauge-pointer></kendo:linearGauge-pointer>
    </kendo:linearGauge>


## Configuration Attributes


### color `String`

The color of the pointer.

#### Example
    <kendo:linearGauge-pointer color="color">
    </kendo:linearGauge-pointer>



### margin `float`

The margin of the pointer.

#### Example
    <kendo:linearGauge-pointer margin="margin">
    </kendo:linearGauge-pointer>



### opacity `float`

The opacity of the pointer.
Any valid CSS color string will work here, including hex and rgb.

#### Example
    <kendo:linearGauge-pointer opacity="opacity">
    </kendo:linearGauge-pointer>



### shape `String`

The shape of the pointer.

#### Example
    <kendo:linearGauge-pointer shape="shape">
    </kendo:linearGauge-pointer>



### size `float`

The size of the pointer.

#### Example
    <kendo:linearGauge-pointer size="size">
    </kendo:linearGauge-pointer>



### value `float`

The value of the gauge.

#### Example
    <kendo:linearGauge-pointer value="value">
    </kendo:linearGauge-pointer>



## Child JSP Tags

### kendo:linearGauge-pointer-border

The border of the pointer.

More documentation is available at [kendo:linearGauge-pointer-border](/api/wrappers/jsp/lineargauge/pointer-border).

#### Example

    <kendo:linearGauge-pointer>
        <kendo:linearGauge-pointer-border></kendo:linearGauge-pointer-border>
    </kendo:linearGauge-pointer>
 
### kendo:linearGauge-pointer-track

The element arround/under the pointer.
(available only for 'barIndicator' shape)

More documentation is available at [kendo:linearGauge-pointer-track](/api/wrappers/jsp/lineargauge/pointer-track).

#### Example

    <kendo:linearGauge-pointer>
        <kendo:linearGauge-pointer-track></kendo:linearGauge-pointer-track>
    </kendo:linearGauge-pointer>
 
