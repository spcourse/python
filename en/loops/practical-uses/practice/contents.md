# Practice with loops
> **You don't have to hand in these practice exercises.** They're here for you to test yourself. Did you fully understand the theory you just learned?
>
> If there is an exercise that you don't know how to make, review the theory again. If that doesn't help, discuss the exercise with another student and/or the teacher.

Test your understanding with the following practice exercises. Create a file called `loops.py` for your solutions.

## Computing with loops exercises
**Exercise 1**
Consider the following code:

    total = 0
    for x in range(1, 4):
        print(f"x now has the value {x}")
        total = total + x

    print(f"The sum of all numbers from 1 to 4 = {total}")

Please change this program by including another print statement: `print(f"The sum of all numbers from 1 to {x} = {total}")`. Include this line beneath `total = total + x`. (Make sure that you get the indentation right: the new print statement should still be part of the loop.) This should have the following output:

    x now has the value 1
    The sum of all numbers from 1 to 1 = 1
    x now has the value 2
    The sum of all numbers from 1 to 2 = 3
    x now has the value 3
    The sum of all numbers from 1 to 3 = 6
    x now has the value 4
    The sum of all numbers from 1 to 4 = 10
    The sum of all numbers from 1 to 4 = 10

**Exercise 2** At this moment we use the numbers from 1 to 4. Let's make this more flexible. Add the variable `maximum` to the beginning of your program and assign it the value `10`. Use this maximum number as the maximum value for the for-loop: `for x in range(1, maximum)`.

**Exercise 3** Make a program that has the same functionality as the example, but now use a while-loop instead of a for-loop.

**Exercise 4** Replace the while-loop condition to ensure that it will stop if the sum of all numbers up to that point is bigger than 20. To help you, the expected output is provided:

    x now has the value 1
    The sum of all numbers from 1 to 1 = 1
    x now has the value 2
    The sum of all numbers from 1 to 2 = 3
    x now has the value 3
    The sum of all numbers from 1 to 3 = 6
    x now has the value 4
    The sum of all numbers from 1 to 4 = 10
    x now has the value 5
    The sum of all numbers from 1 to 5 = 15
    x now has the value 6
    The sum of all numbers from 1 to 6 = 21
    The sum of all numbers from 1 to 10 = 21

## Filtering with loops exercises
**Exercise 5**
Consider the following code:

    for number in range(1, 20):
        if number > 15:
            print(f"This number is bigger than 15: {number}")
        if number % 3 == 0:
            print(f"This number is exactly divisible by 3: {number}")

Try to adapt the example above in such a way that, at the end of the loop, the program prints to the screen how many numbers were exactly divisible by 3. To do this, you will have to define a so-called 'counter', a variable that is set to zero at the start of the program and that is incremented by 1 every time you encounter a number that is exactly divisible by 3. Also take some time to format the output to the screen and have your program print:

    From the numbers 1 to 20 there are ... numbers that are exactly divisible by 3.

## Nested loops exercises

**Exercise 6** Consider the nested loop below:

    for x in range(1, 6):
       for y in range(1, 4):
           print(f"x = {x}, y = {y}")

Adapt the program in such a way that at the moment just before a new value is assigned to `x` (i.e. just after the loop over y is finished), the program prints: `The value of x is now ... and we have just finished the loop over y`.

The output should look as follows:

	x =  1,  y =  1
	x =  1,  y =  2
	x =  1,  y =  3
	The value of x is now 1, we have just finished the loop over y.
	x =  2,  y =  1
	x =  2,  y =  2
	x =  2,  y =  3
	The value of x is now 2, we have just finished the loop over y.
	...
	The value of x is now 5, we have just finished the loop over y.

**Exercise 7** Adapt the program in such a way that `y` does not run from 1 to 4, but from 1 to the value of `x`.

## Solutions
Below you can find some solutions.

> Disclaimer: There are always many ways to solve a problem. The solutions here are not said to be the best solutions.
**Having a different solution, does not necessarily mean it is wrong**.
>
> You should not have to rely on these solutions. If you cannot make the practice exercises at all without looking at these solutions, you should discuss this with your teacher.

<details markdown="1"><summary  markdown="span">Answers</summary>

**Exercise 1**

    total = 0
    for x in range(1, 5):
        print(f"x now has the value {x}")
        total = total + x
        print(f"The sum of all numbers from 1 to {x} = {total}")

    print(f"The sum of all numbers from 1 to 4 = {total}")

**Exercise 2**

    total = 0
    maximum = 10
    for x in range(1, maximum):
        print(f"x now has the value {x}")
        total = total + x
        print(f"The sum of all numbers from 1 to {x} = {total}")

    print(f"The sum of all numbers from 1 to {maximum} = {total}")


**Exercise 3**

    total = 0
    maximum = 10
    x = 1
    while x < maximum:
        print(f"x now has the value {x}")
        total = total + x
        print(f"The sum of all numbers from 1 to {x} = {total}")
        x += 1

    print(f"The sum of all numbers from 1 to {maximum} = {total}")

**Exercise 4**

    total = 0
    maximum = 10
    x = 1
    while total <= 20:
        print(f"x now has the value {x}")
        total = total + x
        print(f"The sum of all numbers from 1 to {x} = {total}")
        x += 1

    print(f"The sum of all numbers from 1 to {maximum} = {total}")


**Exercise 5**

    count = 0
    for number in range(1, 20):
        if number > 15:
            print(f"This number is bigger than 15: {number}")
        if number % 3 == 0:
            count += 1
            print(f"This number is exactly divisible by 3: {number}")
    print(f"From the numbers 1 to 20 there are {count} numbers that are exactly divisible by 3.")

**Exercise 6**

    for x in range(1, 6):
        for y in range(1, 4):
            print(f"x = {x}, y = {y}")
        print(f"The value of x is now {x} and we have just finished the loop over y")

**Exercise 7**

    for x in range(1, 6):
        for y in range(1, x):
            print(f"x = {x}, y = {y}")
        print(f"The value of x is now {x} and we have just finished the loop over y")

</details>
