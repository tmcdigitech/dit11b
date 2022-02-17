---
title: Pygame Zero
weight: 2
---

Let's get a simple game happening, a bit at a time, so you can see how you might go about it yourself.

All of these examples are complete programs, so make sure you copy them into Mu (or whatever editor you're using)
and run them as you go through this page.

## Screen size
Let's start by setting the size of the screen.

```python {linenos=table}
import pgzrun

WIDTH = 800
HEIGHT = 600

pgzrun.go() # Must be last line
```

## Background
Now let's add a coloured background. To do this we need to define a function called `draw()`, which Pygame Zero will call every time it needs to redraw the screen:

```python {linenos=table,hl_lines=["6-8"]}
import pgzrun

WIDTH = 800
HEIGHT = 600

def draw():
    screen.fill((128, 0, 0))

pgzrun.go() # Must be last line
```

{{< hint info >}}
**Why the double brackets?**\
Notice that we had to use two sets of brackets in that example to set the colour of the background. In Pygame Zero, colours are always written as a set of three numbers like this: `(0, 130, 255)`, which in Python is called a **tuple** (rhyming with 'couple'). A tuple is indicated with round brackets. But the function also takes a set of round brackets, so we know it is a function. So the outer set of brackets belongs to the `fill()` function call, and the inside set to the tuple for the colour.
{{< /hint >}}

## Basic shapes

Let's add a couple of basic shapes.

```python {linenos=table,hl_lines=[8]}
import pgzrun

WIDTH = 800
HEIGHT = 600

def draw():
    screen.fill((128, 0, 0))
    screen.draw.filled_circle((0,150), 10, (200, 100, 200))

pgzrun.go() # Must be last line
```

The `filled_circle()` command takes three bits of information, known as [arguments]({{< relref "/glossary/argument" >}}):
1. the co-ordinates of the circle's centre `(x, y)` as a tuple,
2. the radius,
3. the colour `(r, g, b)` as a tuple.

