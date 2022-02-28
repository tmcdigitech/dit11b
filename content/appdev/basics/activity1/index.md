---
title: Activity 1
weight: 4
---
## Setting up The Python Script
{{< highlight python "lineNos=table,lineNoStart=1" >}}
import kivy
from kivy.app import App
from kivy.uix.label import Label
from kivy.uix.gridlayout import GridLayout
from kivy.uix.textinput import TextInput
from kivy.uix.button import Button
from kivy.uix.widget import Widget
from kivy.properties import ObjectProperty


class MyGrid(Widget):
    pass


class MyApp(App):
    def build(self):
        return MyGrid()


if __name__ == "__main__":
    MyApp().run()

{{< /highlight >}}



## Creating a .kv File
### Separated our logic from our styling and elements
There are a few conventions we need to follow when creating a .kv file.

Naming: The name of your .kv file must follow the rules below in order for python/kivy to be able to see and load the file.
1. It must be all lowercase
2. It must match with the name of your main class. (The one that has the build method)
3. If the name of your main class ends in "app" (lowercase or uppercase) you must not include "app" in your file name.

File Location: The file must be in the same directory as your python script.

File Extension: The file must be saved as type *All Files and end with .kv

For example:

My main classes name is MyApp. Therefore I will name my file my.kv.
{{< highlight python >}}
<MyGrid>:
    
    GridLayout:
        cols:1
        size: root.width, root.height

        GridLayout:
            cols:2
            Label:
                text: "Name: "

            TextInput:
                multinline:False

        Button:
            text:"Submit"
            on_press: root.btn()
        
{{< /highlight >}}
<iframe width="640" height="360" src="https://web.microsoftstream.com/embed/video/c9385eaa-1e43-4f98-96a0-4b6f35b2eaf3?autoplay=false&showinfo=true" allowfullscreen style="border:none;"></iframe>

# Activity 1
1. Add a Surname **Label** and **TextInput** so when the user presses the submit button the surname is also included.
2. Add a **Label** that welcomes the user when submit is pressed
{{< figure src="Screenshot 2022-02-28 164502.png" title="" >}}

<iframe width="640" height="360" src="https://web.microsoftstream.com/embed/video/f0b46fa7-707b-4ce9-8141-fa12fbfe52e6?autoplay=false&showinfo=true" allowfullscreen style="border:none;"></iframe>





