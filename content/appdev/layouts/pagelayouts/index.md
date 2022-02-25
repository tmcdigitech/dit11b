---
title: Page Layouts
weight: 2
---

The PageLayout works in a different manner from other layouts. It is a dynamic layout, in the sense that it allows flipping through pages using its borders. The idea is that its components are stacked in front of each other, and we can just see the one that is on top. 
PageLayout is similar to pages of a copy like that we can move/change the pages right or left.

The PageLayout class is used to create a simple multi-page layout, in a way that allows easy flipping from one page to another using border.

To use PageLayout you have to import it by the below command: 
{{< highlight python >}}
from kivy.uix.pagelayout import PageLayout
    {{< /highlight >}}
{{< hint info >}}
Note: 
PageLayout does not currently honor the size_hint, size_hint_min, size_hint_max, or pos_hint properties. That means we can not use all these in a page layout. 
{{< /hint >}}
Example:  
{{< highlight python >}}
PageLayout:
    Button:
        text: 'page1'
    Button:
        text: 'page2'
    Button:
        text: 'page3'

{{< /highlight >}}

Transitions from one page to the next are made by swiping in from the border areas on the right or left-hand side. If you want to use multiple widgets on a page, use layouts to do that. Ideally, each page should consist of a single layout widget that contains the remaining widgets on that page.

Page Layout contains many things which can be used to make it more effective easily in .kv file. 

1. **border:** The width of the border around the current page used to display the previous/next page swipe areas when needed. border is a NumericProperty and defaults to 50dp.
2. **page:** The currently displayed page. Page is a NumericProperty and defaults to 0.
3. **swipe_threshold:** The threshold used to trigger swipes as percentage of the widget size. swipe_threshold is a NumericProperty and defaults to .5.

**Basic Approach to create page layout using .kv file**
1) import kivy
2) import kivyApp
3) import Pagelayout
4) Set minimum version(optional)
5) create Layout class
6) create App class
      - create build() function
7) Set up .kv file(name same as the App class)
8) return Layout/widget/Class(according to requirement)
9) Run an instance of the class

Below is the Implementation for .kv files in this code :

1). kv file is just Simply how to create pages in .kv file 
2). kv file is how can yo add features like : color, text, image, canvas, swipe_threshold, button in the pages.



### Implementation of the Approach –
main.py file 

{{< highlight python  >}}
## Sample Python application demonstrating the
## working of PageLayout in Kivy using .kv file
 
##################################################
# import kivy module  
import kivy
   
# base Class of your App inherits from the App class.  
# app:always refers to the instance of your application 
from kivy.app import App
 
# this restrict the kivy version i.e
# below this kivy version you cannot
# use the app or software
kivy.require('1.9.0')
  
# The PageLayout class is used to create
# a simple multi-page layout,
# in a way that allows easy flipping from
# one page to another using borders.
from kivy.uix.pagelayout import PageLayout
  
# creating the root widget used in .kv file
class PageLayout(PageLayout):
    pass
 
# creating the App class in which name
#.kv file is to be named PageLayout.kv
class PageLayoutApp(App):
    # defining build()
    def build(self):
        # returning the instance of root class
        return PageLayout()
 
# creating object of PageLayoutApp() class
plApp = PageLayoutApp()
 
# run the class
plApp.run()
{{< /highlight >}}


### .kv file of Simple pages
{{< highlight python  >}}
# creating simple Pagelayout using.kv
 
<PageLayout>:
     
    # creating Page 1
    Button:
        text: "Page 1"
 
    # creating Page 2
    Button:
        text: "Page 2"
 
    # creating Page 3
    Button:
        text: "Page 3"
 
    # creating Page 3
    Button:
        text: "Page 4"
 
    # create Page as may as you want
{{< /highlight >}}
Output:
{{< figure src="page-12-300x165.png" title="" >}}

## Lets modify the .kv file to include more widgets on each page
{{< highlight python  >}}
# creating simple Pagelayout using.kv
 
# creating page Layout
<PageLayout>:
 
    # creating simple Pagelayout using.kv
 
# creating page Layout
<PageLayout>:
 
    # Creating Page 1
     
    # Using BoxLayout inside PageLayout
    BoxLayout:
 
        # creating Canvas
        canvas:
            Color:
                rgb: 0, .5, .95, 1
            Rectangle:
                pos: self.pos
                size: self.size
 
        # Providing orientation to the BoxLayout
        orientation: "vertical"
 
        # creating Button
        Button:
            text: "Page 1"
            size_hint_y: .4
 
        # Adding Label to Page 1
             
        Label:
            markup: True
            text: "[b]This is a label[/b]"
            color: 0, 0, 0, 1
            outline_color: 0, 0.5, 0.5, 1
            font_size: 30
 
 
    # Creating Page 2
    BoxLayout:
        orientation: "vertical"
         
        canvas:
            Color:
                rgba: 109 / 255., 8 / 255., 57 / 255., 1
            Rectangle:
                pos: self.pos
                size: self.size
        Label:
            markup: True
            text: " Kivy[b]PageLayout[/b]!!!!! "
            color: 0, 0, 0, 1
            outline_color: 0, 0.5, 0.5, 1
            font_size: 30
 
             
        Button:
            text: "Page 2"
            size_hint_y: .2
 
 
    # Creating Page 3
    BoxLayout:
         
        orientation: 'vertical'
 
        canvas:
            Color:
                rgba: 100 / 555., 9 / 155., 37 / 455., 1
            Rectangle:
                pos: self.pos
                size: self.size
 
        Label:
            text: 'page 3'
 
        # This Image is directly from the websource
        # By using AsyncImage you can use that
        AsyncImage:
            source: 'http://kivy.org/logos/kivy-logo-black-64.png'
         
 
 
    # Creating Page 4
    Button:
        # Adding image
        # image must be .png
        # and present at the same folder where
        # .kv and main file is saved
        Image:
            source: "image-129.png"
            center_x: self.parent.center_x
            center_y: self.parent.center_y

    {{< /highlight >}}
