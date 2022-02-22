---
title: Buttons and Labels
weight: 1
---

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
{{< highlight python "lineNos=table,lineNoStart=1" >}}
import kivy
from kivy.app import App
from kivy.uix.label import Label
from kivy.uix.gridlayout import GridLayout
from kivy.uix.textinput import TextInput
from kivy.uix.button import Button
from kivy.uix.widget import Widget


class MyGrid(Widget):
    pass


class MyApp(App): # <- Main Class
    def build(self):
        return MyGrid()


if __name__ == "__main__":
    MyApp().run()

{{< /highlight >}}
If you have named your file correctly there is nothing else you need to do to ensure that it is linked with your python script.

## Setting up The Python Script
Before continuing please import the following module from your python script.
{{< highlight python >}}
from kivy.uix.widget import Widget
{{< /highlight >}}

The first thing we need to do to add widgets to our screen using .kv is set up an empty class in our python script. This class will simply inherit from Widget and will be what is used from within the kv file to add widgets.
{{< highlight python  >}}
class MyGrid(Widget):
    pass

{{< /highlight >}}
Now ensure that your main classes build method returns an instance of MyGrid and we are ready to go.
{{< highlight python  >}}
class MyApp(App):
    def build(self):
        return MyGrid()

{{< /highlight >}}

## Adding Widgets From a .kv File
Two important things to remember about .kv files:
- Capitals are Important
- Indentation is important

The first thing we do when writing in a .kv is declare the class we will be adding widgets to. In my case it's MyGrid.
{{< highlight python  >}}
# Filename: my.kv 

<MyGrid>:
{{< /highlight >}}
The next step is to define the widgets that we want to add to that class. Each widget also has several properties associated with it that we can change.
{{< highlight python  >}}
# Filename: my.kv 

<MyGrid>:
    Label:
        text: "Name: "

    TextInput:
        multiline:False
{{< /highlight >}}
You can see that the widgets that are inside of the MyGrid class are tabbed in once and the properties of those widgets are tabbed twice.

## Creating a Form With a .kv File
The file below is the recreation of the form we made in tutorial 3, this time using a kv file. You can see that we have multiple grid layouts like before and that we add widgets to those layouts.

Notice that to make these widgets fill the entire screen we must change the size attribute. By making the size of the first grid layout root.width, root.height we are telling it to fill the size of the window dynamically.
{{< highlight python  >}}
# Filename: my.kv

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

            Label:
                text: "Email: "

            TextInput:
                multiline:False

        Button:
            text:"Submit"
            on_press: app.btn()
{{< /highlight >}}

## Object Properties
After experimenting with the .kv language some of you may have asked the question: How do we access our elements (textinput, button etc.) from our python script? Well that is an excellent question and is what we have object properties for!

An object property allows us to create a reference to widgets from within a .kv file from our python script.

## Modifying the .kv File
To set up object properties we need to create global variables from within our .kv file and assign these variables to the id property of specific widgets.
{{< highlight python  >}}
<MyGrid>:
   
    name: name  # Global variable name references the id name
    email: email  # Global variable email references the id email

    GridLayout:
        cols:1
        size: root.width - 200, root.height -200
        pos: 100, 100

        GridLayout:
            cols:2

            Label:
                text: "Name: "

            TextInput:
                id: name  # <- Add this
                multiline:False

            Label:
                text: "Email: "

            TextInput:
                id: email  # <-Add this
                multiline:False

        Button:
            text:"Submit"

{{< /highlight >}}

## Modifying the Python Script
The first thing we need to do to use an object property from within our python script is import the specific module.
{{< highlight python  >}}
from kivy.properties import ObjectProperty
{{< /highlight >}}
Next we will define two object properties from within our class MyGrid.
{{< highlight python  >}}
class MyGrid(Widget):
    name = ObjectProperty(None)
    email = ObjectProperty(None)
{{< /highlight >}}
We initialize the values as None to start as when we first create the class they will have no value.
Now if we want to access the value of the TextInput box with id email we can simply use self.email to do so. Similarity for the name TextInput.

## Creating a Button On_Press
Like we had in previous tutorials we'd like our button to perform a function when it is clicked. To accomplish this we need to create a method inside of our MyGrid class that we can call each time our button is pressed. We will call this btn().
{{< highlight python  >}}
# Goes inside MyGrid Class
def btn(self):
    print("Name:", self.name.text, "email:", self.email.text)
    self.name.text = ""
    self.email.text = ""
{{< /highlight >}}
This method will print the contents of our form and clear both of the text input boxes.

Now we need to tell the button what it should call when it is pressed. To do this we will add the property on_press in our .kv file.
{{< highlight python  >}}
Button:
    text:"Submit"
    on_press: root.btn() # <- Add this
{{< /highlight >}}
We use app.btn() to reference the class that contains our btn method.

Now we should have a functioning application that works. 

## Full Code
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
    name = ObjectProperty(None)
    email = ObjectProperty(None)

    def btn(self):
        print("Name:", self.name.text, "email:", self.email.text)
        self.name.text = ""
        self.email.text = ""




class MyApp(App):
    def build(self):
        return MyGrid()


if __name__ == "__main__":
    MyApp().run()

{{< /highlight >}}

{{< highlight python  >}}
<MyGrid>:

    name: name
    email: email

    GridLayout:
        cols:1
        size: root.width - 200, root.height -200
        pos: 100, 100

        GridLayout:
            cols:2

            Label:
                text: "Name: "

            TextInput:
                id: name
                multiline:False

            Label:
                text: "Email: "

            TextInput:
                id: email
                multiline:False

        Button:
            text:"Submit"
            on_press: root.btn()
{{< /highlight >}}