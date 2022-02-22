---
title: Kivy Layout Types
weight: 2
---

Layouts are containers used to arrange widgets in a particular manner.
### [Anchor Layout:](https://kivy.org/doc/stable/api-kivy.uix.anchorlayout.html#module-kivy.uix.anchorlayout)
 Widgets can be anchored to the ‘top’, ‘bottom’, ‘left’, ‘right’ or ‘center’.

### [Box Layout:](https://kivy.org/doc/stable/api-kivy.uix.boxlayout.html#module-kivy.uix.boxlayout) 
Widgets are arranged sequentially, in either a ‘vertical’ or a ‘horizontal’ orientation.

### [Float Layout:](https://kivy.org/doc/stable/api-kivy.uix.floatlayout.html#module-kivy.uix.floatlayout) 
Widgets are essentially unrestricted.

### [Relative Layout:](https://kivy.org/doc/stable/api-kivy.uix.floatlayout.html#module-kivy.uix.floatlayout) 
Child widgets are positioned relative to the layout.

### [Grid Layout:](https://kivy.org/doc/stable/api-kivy.uix.floatlayout.html#module-kivy.uix.floatlayout) 
Widgets are arranged in a grid defined by the rows and cols properties.

### [Page Layout:](https://kivy.org/doc/stable/api-kivy.uix.pagelayout.html#module-kivy.uix.pagelayout) 
Used to create simple multi-page layouts, in a way that allows easy flipping from one page to another using borders.

### [Scatter Layout:](https://kivy.org/doc/stable/api-kivy.uix.scatterlayout.html#module-kivy.uix.scatterlayout) 
Widgets are positioned similarly to a RelativeLayout, but they can be translated, rotated and scaled.

### [Stack Layout:](https://kivy.org/doc/stable/api-kivy.uix.scatterlayout.html#module-kivy.uix.scatterlayout) 
Widgets are stacked in a lr-tb (left to right then top to bottom) or tb-lr order.


When you add a widget to a layout, the following properties are used to determine the widget’s size and position, depending on the type of layout:

size_hint: defines the size of a widget as a fraction of the parents size. Values are restricted to the range 0.0 - 1.0 i.e. 0.01 = 1/100th of the parent size (1%) and 1. = same size (100%).

pos_hint: is used to place the widget relative to the parent.

The size_hint and pos_hint are used to calculate a widget’s size and position only if the value(s) are not set to None. If you set these values to None, the layout will not position/size the widget and you can specify the values (x, y, width, height) directly in screen coordinates.