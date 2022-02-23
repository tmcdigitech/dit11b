---
title: 1. Hello World
weight: 2
---
*Taken from [prosperocoder.com](https://prosperocoder.com/posts/kivy/kivy-part-3-a-basic-kivy-app/)*

## Hello World – A Basic Kivy App
Well, we’re going to write a basic Kivy app that will display the Hello World text. In Kivy, like in many other GUI libraries and frameworks, static text is usually displayed in a label. In Kivy we call simple GUI elements like labels, buttons, sliders, check boxes, etc. widgets, although widgets don’t have to be simple at all and you can create your own widgets, which we are going to do later.

### Create a folder
Anyway, our program is going to display the text Hello World in a label. Before we write the code, let’s create a folder where we will save it. Then open the folder in your editor or IDE. Here’s how to do it in Visual Studio Code:

{{< figure src="image-21.png" title="Open folder in VSC" >}}

# Setup and install Kivy
Create a new virtual environment for your Kivy project. A virtual environment will prevent possible installation conflicts with other Python versions and packages. It’s optional but strongly recommended, open a New Terminal window and run the following:

1. Open a Terminal window and create the virtual environment named .env in your current directory:
{{< highlight terminal >}}
python -3 -m venv .venv
{{< /highlight >}}
2. Update the security on this folder
{{< highlight terminal >}}
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope Process
{{< /highlight >}}
3. Activate your new virtual environment.
{{< highlight terminal >}}
.venv\scripts\activate
{{< /highlight >}}
4. Install Kivy
 {{< highlight terminal >}}
python -m pip install kivy
{{< /highlight >}}

### Create a new file
When you open your folder, you need a file to write the code to. This is going to be a regular Python file, so with the extension .py. You can name your file whatever you like, I’ll name mine main.py. Here’s how you can create the file: When you hover your mouse over the name of your folder, a menu with a couple icons will appear. The first icon is the one you should click to create a new file:

{{< figure src="image-22.png" title="Open folder in VSC" >}}

All you have to do is type in the name of the file: main.py. As soon as you confirm by hitting Enter, the new file will be listed in the folder (A) and it will open automatically in a new tab (B). This is how we are going to add new files in the future.
{{< figure src="image-24.png" title="Open folder in VSC" >}}



## Write the code of the Kivy app
Now we are ready to write our code. Here it is with comments:
{{< highlight python "lineNos=table,lineNoStart=1" >}}
# We're using Kivy, so we'll need the kivy module
import kivy

# We need the App class. Our application is going to inherit from it.
from kivy.app import App

# We also need the Label widget.
from kivy.uix.button import Label

# Here comes the application class. It inherits from App.
class HelloWorldApp(App):
    def build(self):
        return Label(text='Hello World!')

# And this is where we actually run the app.
if __name__ == '__main__':
    HelloWorldApp().run()

{{< /highlight >}}

## Running Your Kivy App
This is a basic Kivy application. Now we are ready to run it. There are several ways you can do it. Let’s have a look at the most obvious ones:

### 1) the Run Python File in Terminal button
The first way to run the app is by pressing the Run Python File in Terminal button in the upper right corner (A). Here’s what we get when we do that: the application window shows up with our application running in it (B) and the terminal opens at the bottom with the Kivy log (C).
{{< figure src="image-25.png" title="Run Python File in Terminal button" >}}

### 2) Run the Kivy App Without Debugging in the Debug menu
You can also go to the Debug menu and select Run Without Debugging:
{{< figure src="image-26.png" title="Run the Kivy App Without Debugging" >}}

### 3) Start Debugging option in the Debug menu
There is also the Start Debugging option in the Debug menu. You can choose it and then select a Debug Configuration. Go ahead and select the first option, Python File:
{{< figure src="image-27.png" title="Start Debugging option in the Debug menu" >}}

### 4) Hotkeys
For the previous two options you can also use hotkeys:

     – F5 to start debugging

     – Ctrl + F5 to run without debugging

### 5) Context menu
You can also right-click anywhere in the editor tab where the code of your file is and select Run Python File in Terminal:
{{< figure src="image-28.png" title="Context menu" >}}
