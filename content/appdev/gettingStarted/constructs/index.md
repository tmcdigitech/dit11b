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

Python programming offers two kinds of loop, the for loop and the while loop. Using these loops along with loop control statements like break and continue, we can create various forms of loop.

# The infinite loop
We can create an infinite loop using while statement. If the condition of while loop is always True, we get an infinite loop.

Example #1: Infinite loop using while
{{< highlight python "lineNos=table,lineNoStart=1" >}}
# An example of infinite loop
# press Ctrl + c to exit from the loop

while True:
   num = int(input("Enter an integer: "))
   print("The double of",num,"is",2 * num)

{{< /highlight >}}
Output
{{< highlight python >}}
Enter an integer: 3
The double of 3 is 6
Enter an integer: 5
The double of 5 is 10
Enter an integer: 6
The double of 6 is 12
Enter an integer:
Traceback (most recent call last):
{{< /highlight >}}

## Loop with condition at the top
This is a normal while loop without break statements. The condition of the while loop is at the top and the loop terminates when this condition is False.

## Flowchart of Loop With Condition at Top
{{< figure src="Screenshot 2022-02-22 094529.png" title="" >}}

Example #2: Loop with condition at the top
{{< highlight python "lineNos=table,lineNoStart=1" >}}
# Program to illustrate a loop with the condition at the top

# Try different numbers
n = 10

# Uncomment to get user input
#n = int(input("Enter n: "))

# initialize sum and counter
sum = 0
i = 1

while i <= n:
   sum = sum + i
   i = i+1    # update counter

# print the sum
print("The sum is",sum)
{{< /highlight >}}

## Loop with condition in the middle
This kind of loop can be implemented using an infinite loop along with a conditional break in between the body of the loop.

Flowchart of Loop with Condition in Middle
{{< figure src="Screenshot 2022-02-22 095005.png" title="" >}}

### Example #3: Loop with condition in the middle
{{< highlight python "lineNos=table,lineNoStart=1" >}}
# Program to illustrate a loop with condition in the middle. 
# Take input from the user until a vowel is entered

vowels = "aeiouAEIOU"

# infinite loop
while True:
   v = input("Enter a vowel: ")
   # condition in the middle
   if v in vowels:
       break
   print("That is not a vowel. Try again!")

print("Thank you!")

{{< /highlight >}}
Output
{{< highlight python >}}
Enter a vowel: r
That is not a vowel. Try again!
Enter a vowel: 6
That is not a vowel. Try again!
Enter a vowel: ,
That is not a vowel. Try again!
Enter a vowel: u
Thank you!
{{< /highlight >}}

## Loop with condition at the bottom
This kind of loop ensures that the body of the loop is executed at least once. It can be implemented using an infinite loop along with a conditional break at the end. This is similar to the do...while loop in C.

Flowchart of Loop with Condition at Bottom
{{< figure src="Screenshot 2022-02-22 095340.png" title="" >}}

Example #4: Loop with condition at the bottom
{{< highlight python "lineNos=table,lineNoStart=1" >}}
# Python program to illustrate a loop with the condition at the bottom
# Roll a dice until the user chooses to exit

# import random module
import random

while True:
   input("Press enter to roll the dice")

   # get a number between 1 to 6
   num = random.randint(1,6)
   print("You got",num)
   option = input("Roll again?(y/n) ")

   # condition
   if option == 'n':
       break
{{< /highlight >}}
Output
{{< highlight python >}}
Press enter to roll the dice
You got 1
Roll again?(y/n) y
Press enter to roll the dice
You got 5
Roll again?(y/n) 
{{< /highlight >}}

## What is FOR loop in Python?
The for loop in Python is used to iterate over a sequence (list, tuple, string) or other iterable objects. Iterating over a sequence is called traversal.

Syntax of for Loop
{{< highlight python >}}
for val in sequence:
    loop body

{{< /highlight >}}
Here, val is the variable that takes the value of the item inside the sequence on each iteration.

Loop continues until we reach the last item in the sequence. The body of for loop is separated from the rest of the code using indentation.

Flowchart of for Loop
{{< figure src="Screenshot 2022-02-22 095751.png" title="" >}}

Example: Python for Loop
{{< highlight python "lineNos=table,lineNoStart=1,hl_lines=10-11" >}}
# Program to find the sum of all numbers stored in a list

# List of numbers
numbers = [6, 5, 3, 8, 4, 2, 5, 4, 11]

# variable to store the sum
sum = 0

# iterate over the list
for val in numbers:
    sum = sum+val

print("The sum is", sum)
{{< /highlight >}}
When you run the program, the output will be:
{{< highlight python >}}
The sum is 48
{{< /highlight >}}
