---
title: Activity 2
weight: 4
---
# Create a simple calculator



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

## Are you ready? 
{{< hint info >}}
Using your skills and knowledge from Activity 1 start a new Kivy project to create your calculator.  **You will need to setup the GUI.**
{{< /hint >}}

{{< figure src="Screenshot 2022-03-07 155754.png" title="" >}}



### A Simple Password Generator in Python
We will start by generating a random string of 12 characters. To do that we will use the function random.choice() that returns a random character from a sequence.

### We will do the following:

Import the random module.
Set the password length to 12.
Define a list of characters that we will use to generate the random password. In this first version of the program we will use just a few letters and numbers.
Create an empty string called password.
Write a for loop that executes 12 iterations and that at every iteration selects a random character from the string characters and appends it to the password string.
Print the password we have generated.
Import Random at the top of your code
{{< highlight python "lineNos=table,lineNoStart=1" >}}
import random
{{< /highlight >}}

The following will need to be triggered by a button.
{{< highlight python "lineNos=table,lineNoStart=1" >}}
password_length = 12

characters = "abcde12345"

password = ""   

for index in range(password_length):
    password = password + random.choice(characters)

print("Password generated: {}".format(password))
{{< /highlight >}}

And here is an example of a password generated with this code:
{{< highlight python >}}
Password generated: dcb4a2c4aac5
{{< /highlight >}}
As you can see the password is not strong considering that we have used a limited number of characters and numbers.

In the next section we will make it more secure.

### How to Generate a Password Using All Alphanumeric Characters
Let’s improve the complexity of the password by using all alphanumeric characters.

To do that we could simply update the value of the characters string to include all letters and numbers but it would be time consuming and prone to errors.

What can we do instead?

We can import the Python string module that provides a few constants that we can use in the generation of a password.

Here are few examples:
{{< highlight python >}}
>>> import string
>>> string.ascii_lowercase
'abcdefghijklmnopqrstuvwxyz'
>>> string.ascii_uppercase
'ABCDEFGHIJKLMNOPQRSTUVWXYZ'
>>> string.ascii_letters
'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'
>>> string.digits
'0123456789'
>>> string.punctuation
'!"#$%&\'()*+,-./:;<=>?@[\\]^_`{|}~'
{{< /highlight >}}

We won’t use string.ascii_lowercase or string.ascii_uppercase considering that they are both included instring.ascii_letters.

In our password generator we will use the following three sets of characters:

string.ascii_letters
string.digits
string.punctuation
We will use the + symbol to concatenate the three sets of characters to create a single string that we will assign to the characters variable.

This is what you get if you concatenate the three sets of characters in the Python shell:
{{< highlight python >}}
>>> string.ascii_letters + string.digits + string.punctuation
'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789!"#$%&\'()*+,-./:;<=>?@[\\]^_`{|}~'
{{< /highlight >}}
Let’s update our program…
{{< highlight python "lineNos=table,lineNoStart=1" >}}
import random, string

password_length = 12

characters = string.ascii_letters + string.digits + string.punctuation

password = ""   

for index in range(password_length):
    password = password + random.choice(characters)

print("Password generated: {}".format(password))

{{< /highlight >}}

Here are three examples of passwords generated with the updated program:
{{< highlight python >}}
Password generated: iE%g.JqurkB0
Password generated: |>J+qbZ<Vl7$
Password generated: c94,JRgshz#g
{{< /highlight >}}

Update the Password Generator to Receive the Password Length as User Input
Let’s make our password generator a bit more flexible.

We will allow the user to provide the password length instead of hardcoding it in our program. To do that we will use the input function.
{{< highlight python "lineNos=table,lineNoStart=1" >}}
import random, string

password_length = int(input("Provide the password length: "))

characters = string.ascii_letters + string.digits + string.punctuation

password = ""   

for index in range(password_length):
    password = password + random.choice(characters)

print("Password generated: {}".format(password))
{{< /highlight >}}

Notice that we have converted the value returned by the input function into integer considering that when using Python 3 the input function returns a string.

The program works fine.

Confirm it works on your machine too before continuing with this tutorial.
{{< highlight python >}}
Provide the password length: 12
Password generated: ]"c_ga%M^iOd
{{< /highlight >}}

**If you don’t convert the output of the input function into integer you get an error when you use the variable password_length in the for loop.**

How to Create a Python Password Generator that Generates Multiple Passwords
In this section we will enhance our password generator to generate a custom number of passwords.

The approach will be very similar to the one we have used to get the password length from the user with the input function.

We will do the following:

Get the number_of passwords using the input function.
Add a for loop to generate multiple passwords based on the value of the variable number_of passwords provided by the user.
{{< highlight python "lineNos=table,lineNoStart=1" >}}

import random, string

number_of_passwords = int(input("How many passwords do you want to generate? "))
password_length = int(input("Provide the password length: "))

characters = string.ascii_letters + string.digits + string.punctuation

for password_index in range(number_of_passwords):
    password = ""   

    for index in range(password_length):
        password = password + random.choice(characters)

    print("Password {} generated: {}".format(password_index, password))

{{< /highlight >}}
Note: make sure you use the correct indentation as shown in the code above.

Let’s test our code:
{{< highlight python>}}
How many passwords do you want to generate? 3
Provide the password length: 8
Password 0 generated: 2B.1&=~k
Password 1 generated: Wt$@1vi'
Password 2 generated: ,aOXN_@$

{{< /highlight >}}
It works, nice!

How to Generate Strong Passwords in Python
Before completing this tutorial let’s find out how we can enforce a set of rules to make sure the passwords we generate are strong enough.

We will make sure passwords contain at least:
- three digits
- two punctuation characters
To do that we will use two integers that define the number of digits and punctuation characters. Then we will use multiple nested for loops.
{{< highlight python "lineNos=table,lineNoStart=1" >}}
import random, string

number_of_digits = 3
number_of_punctuation_characters = 2
characters = string.ascii_letters + string.digits + string.punctuation

number_of_passwords = int(input("How many passwords do you want to generate? "))
password_length = int(input("Provide the password length: "))

for password_index in range(number_of_passwords):
    password = ""

    for digits_index in range(number_of_digits):
        password = password + random.choice(string.digits)

    for punctuation_index in range(number_of_punctuation_characters):
        password = password + random.choice(string.punctuation)

    for index in range(password_length - number_of_digits - number_of_punctuation_characters):
        password = password + random.choice(string.ascii_letters)

    print("Password {} generated: {}".format(password_index, password))
{{< /highlight >}}


Let’s have a look at a few password generated with this program:
{{< highlight python >}}

How many passwords do you want to generate? 3
Provide the password length: 10
Password 0 generated: 738<>ZKwMA
Password 1 generated: 332|(SlZDT
Password 2 generated: 756%#NFWHs
{{< /highlight >}}
They look fine but to make them stronger we have to avoid having digits and punctuation characters always in the same position of the password string.

To shuffle characters in the password string we will use the random.shuffle() function.

We will create a specific function that does the shuffling.
{{< highlight python "lineNos=table,lineNoStart=1" >}}

def randomize_password(password):
    password_list = list(password)
    random.shuffle(password_list)
    return "".join(password_list)

{{< /highlight >}}
This function converts the password string into a list before applying random.shuffle. Then it returns a string using the string join method.

Then update the last print statement to call therandomize_password function.
{{< highlight python "lineNos=table,lineNoStart=1" >}}

print("Password {} generated: {}".format(password_index, randomize_password(password)))
{{< /highlight >}}
And the output is…

{{< highlight python >}}
How many passwords do you want to generate? 3
Provide the password length: 10
Password 0 generated: X1+dT)4U1q
Password 1 generated: 2T7g+OQ-B4
Password 2 generated: g3n0<3O>if
{{< /highlight >}}

### Conclusion
In this tutorial you have learned how to create a password generator in Python and how to update its logic to increase the strength of the passwords.


We have covered a few Python core concepts:

- importing modules.
- defining functions.
- using the input function to read user input.
- nested for loops.
- selecting random characters from a string and shuffling a string.
- using the string format method.

## Now dress up your App GUI

1. Watch the following video **Change Background Color And Text Color of Labels** to improve the look of your app.
{{<youtube Gt0_BuJmJeI>}} {{<youtube e73K1DoTNio>}}
2. Watch the following video **How To Use Images With Kivy** and add an image to your app.
{{<youtube LMgLt70kAro>}}









