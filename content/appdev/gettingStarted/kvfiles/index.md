---
title: 2. Kv Files
weight: 3
---
*Taken from [prosperocoder.com](https://prosperocoder.com/posts/kivy/kivy-part-3-a-basic-kivy-app/)*


Our program contains just one widget, the label. This is all as far as presentation is concerned. We’ll move that part to a new file and leave the rest in the main.py file. So, after we remove the presentation part from the main.py, as well as the comments to make the file clear and transparent, this is what we’ll have:

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
        return Label()

# And this is where we actually run the app.
if __name__ == '__main__':
    HelloWorldApp().run()

{{< /highlight >}}

As you can see, now we’re just telling the app that a label should be used, but it doesn’t know anything more about the label. In particular, it doesn’t know what text should go in the label. This is what the kv file is going to take care of. By the way, I’m going to call the files written in the Kivy language kv files, for the sake of brevity. These files are easily recognizable by the kv extension.

## kv Files and the Kivy Language
Now we are ready to create the kv file. Actually, there are two approaches to this. If you have just one kv file, you can go with the simpler approach.

### Naming Convention
 In this approach we use a naming convention according to which we name the file the same as the app class (the class that inherits from App), but without the ‘App’ part and all lowercase. So, in our example the app class is HelloWorldApp, so the kv file should be named helloworld.kv.

Now, in Visual Studio Code (which I’m going to refer to as VSC from now on, also for brevity’s sake), create a new file, just as you did before and name it helloworld.kv:

{{< figure src="image-32.png" title="Open folder in VSC" >}}

As soon as you hit Enter, the file will open in a new tab. Type the following Kivy language code:
{{< highlight python "lineNos=table,lineNoStart=1" >}}
<Label>:
    text: 'Hello World!'
{{< /highlight>}}

We’re going to talk about the Kivy language in more detail later on, for now it’s enough to say that this is all you need to take care of the label. The <Label>: part means we’re working on the Label class, and below we set the text property to a string of our choice.

Now save the kv file and go back to the main.py. Run the program. This is what you should see:
{{< figure src="image-33.png" title="" >}}

