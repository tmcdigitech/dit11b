---
title: Programming Constructs
weight: 8
---

Programs are designed using common building blocks. These building blocks, known as programming constructs (or programming concepts), form the basis for all programs.

There are three basic building blocks to consider:

- **sequence** is the order in which instructions occur and are processed
- **selection** determines which path a program takes when it is running
- **iteration** is the repeated execution of a section of code when a program is running


{{<youtube eSYeHlwDCNA>}}

## Sequence
Sequence is the order in which programming statements are executed. Programming statements usually run one after another in order, unless one of the other programming constructs is used. The sequence of a program is extremely important as once these are translated, carrying out instructions in the wrong order leads to a program performing incorrectly.

The following example code will execute each line in order/sequence
{{< highlight python "lineNos=table,lineNoStart=1" >}}
print("Let's introduce ourselves.")
print("My name is Eliza. What is your name?")
name = input()
print("Hello " + name + ", nice to meet you.")

{{< /highlight >}}

## Selection
### IF statements
Selection is a programming construct where a section of code is run only if a condition is met. In programming, there are often occasions when a decision needs to be made. Selection is the process of making a decision. The result of the decision can either be TRUE or FALSE, this determines which path the program will take next.

The following code uses selection to test the condition **varHeight > 1.6**, if this condition is TRUE then "Tall enough to enter ride" is printed.
{{< highlight python "lineNos=table,lineNoStart=1,hl_lines=1" >}}
if varHeight > 1.6:
	print("Tall enough to enter ride")
{{< /highlight >}}

The following code uses selection to test the condition **username == "Callum"**, if this condition is TRUE then "Access granted" is printed. If the condition is FASLE we can use **else:** to execute a different line of code.
{{< highlight python "lineNos=table,lineNoStart=1,hl_lines=3" >}}
if username == "Callum":
	print("Access granted")
else:
	print("Unknown username")
{{< /highlight >}}

## Iteration or Loop
Programs often need to repeat certain steps while or until a condition has been met. This process is known as **iteration**.

Iteration or repetition is often referred to as looping, since the program **‘loops’** back to an earlier line of code. 

Iteration allows programmers to **simplify a program** and make it **more efficient**. Instead of writing out the same lines of code again and again(mistages happen), a programmer can write a section of code once, and ask the program to execute the same line repeatedly until no longer needed.