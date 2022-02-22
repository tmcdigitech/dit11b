---
title: Classes and Methods
weight: 1
---

## Object Oriented Programming (OOP)
OOP has self-contained objects containing both the programming routine/procedures and the data being processed. These objects interact by sending data to one another.

In OOP, you write classes that represent real world things and create objects based on these classes. Classes attributes as well as procedures (often known as methods).

Class
The class is the blueprint, or template, that defines what an object is. This includes the type of data an object can hold, its initial value and how the object behaves.

From classes, we can create instances. An instance is an object created from a particular class.

If we have a class called Dog, we can create as many instances (Dog1, Dog2, BigDog, SmellyDog) as we like – all with different ages and names.

For example, Dog1 might be an instance of the Dog class:
{{< highlight python  >}}
class Dog:  #creates the Dog class
 def __init__(self, name, age): 
  self.name = name  #self prefix allows all methods to access attributes
  self.age = age

Dog1 = Dog('Bruce', 3)  #creates object Dog1 - name Bruce, age 3
{{< /highlight >}}

## Attributes
Attributes are characteristics of an object. A special method called __init__() is used to initialize the attributes of an object. The Dog class has two attributes (name and age).

### Methods
Methods are functions defined inside the body of a class. They are used to perform operations with the attributes of our objects. For example:
{{< highlight python  >}}
class Dog:
 def __init__(self, name, age):
  self.name = name
  self.age = age

 def bark(self):
   print(self.name + 'is barking')#

Dog1 = Dog('Bruce')
Dog1.bark()

{{< /highlight >}}
This will output: Bruce is barking

