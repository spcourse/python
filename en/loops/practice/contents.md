# Practice with loops
> You don't have to hand in these exercises. These are practice exercises that you can use to test if you fully understood the material you just studied.

Test your understanding with the following practice exercises. Create a file called `loops.py` for your solutions.

## For-loops
**Exercise 1** Write a for-loop that prints the numbers 1 to 50

**Exercise 2** Write a for-loop that prints the between 1 and 50 with steps of 2

**Exercise 3** Write a for-loop that loops over the numbers 0 to 100 with steps of 4 and adds them all together. Print the result.

## While-loops
**Exercise 4** Write a while-loop that continues dividing the variable `s` until the result is 1. Print the value of s at every iteration.

    s = 128
    # your code here

**Exercise 5** Based on the code of the previous exercise. Introduce a second variable called `i`, that counts how many iterations the while-loop runs. Print the resulting value of `i` after the loop is done.

## For and while
**Exercise 6** Consider the following piece of code:

    for i in range(1, 5, 2):
        print(i)

Rewrite this piece of code such that the behavior stays the same, but it uses a while-loop instead of a for.

**Exercise 7**
Consider the following piece of code:

    x = 2
    while x < 12:
        print(x)
        x += 3

Rewrite this such that the behavior stays the same, but it uses a for-loop instead of a while.

## Computing with loops
**Exercise 8**
Consider the following code:

    total = 0
    for x in range(1, 11):
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

**Exercise 9** At this moment we use the numbers from 1 to 4. Let's make this more flexible. Add the variable `maximum` to the beginning of you program and assign it the value `10`. Use this maximum number as the maximum value for the for-loop: `for x in range(1, maximum)`.

**Exercise 10** Make a program that has the same functionality as the example, but now use a while-loop instead of a for-loop.

**Exercise 11** Replace the while-loop condition to ensure that it will stop if the sum of all numbers up to that point is bigger than 20. To help you, the expected output is provided:

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

## Filtering with loops
**Exercise 12**
Consider the following code:

    for number in range(1, 20):
        if number > 15:
            print(f"This number is bigger than 15: {number}")
        if number % 3 == 0:
            print(f"This number is exactly divisible by 3: {number}")

Try to adapt the example above in such a way that, at the end of the loop, the program prints to the screen how many numbers were exactly divisible by 3. To do this you will have to define a so-called 'counter', a variable that is set to zero at the start of the program and that is incremented by 1 every time you encounter a number that is exactly divisible by 3. Also take some time to format the output to the screen and have your program print:

    From the numbers 1 to 20 there are ... numbers that are exactly divisible by 3.

## Nested loops

**Exercise 13** Consider the nested loop below:

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

**Exercise 14** Adapt the program in such a way that `y` does not run from 1 to 4, but from 1 to the value of `x`.

## Solutions
Below you can find some solutions.

> Disclaimer: There are always many ways to solve a problem. The solutions here are not said to be the best solutions.
**Having a different solution, does not necessarily mean it is wrong**.
>
> You should not have to rely on these solutions. If you cannot make the practice exercises at all without looking at these solutions, you should discuss this with your teacher.

<details markdown="1"><summary  markdown="span">Answers</summary>

**Exercise 1**

    for i in range(1, 51):
        print(i)

**Exercise 2**

    for i in range(1, 51, 2):
        print(i)

**Exercise 3**

    total = 0
    for i in range(4, 101, 4):
        total += i
    print(total)

**Exercise 4**

    s = 128
    while s > 1:
        s /= 2
        print(s)

**Exercise 5**

    s = 128
    i = 0
    while s > 1:
        s /= 2
        i += 1
        print(s)
    print(i)

**Exercise 6**

    i = 1
    while i < 5:
        print(i)
        i += 2

**Exercise 7**

    for x in range(2, 12, 3):
        print(x)

**Exercise 8**

    total = 0
    for x in range(1, 5):
        print(f"x now has the value {x}")
        total = total + x
        print(f"The sum of all numbers from 1 to {x} = {total}")

    print(f"The sum of all numbers from 1 to 4 = {total}")

**Exercise 9**

    total = 0
    maximum = 10
    for x in range(1, maximum):
        print(f"x now has the value {x}")
        total = total + x
        print(f"The sum of all numbers from 1 to {x} = {total}")

    print(f"The sum of all numbers from 1 to {maximum} = {total}")


**Exercise 10**

    total = 0
    maximum = 10
    x = 1
    while x < maximum:
        print(f"x now has the value {x}")
        total = total + x
        print(f"The sum of all numbers from 1 to {x} = {total}")
        x += 1

    print(f"The sum of all numbers from 1 to {maximum} = {total}")

**Exercise 11**

    total = 0
    maximum = 10
    x = 1
    while total <= 20:
        print(f"x now has the value {x}")
        total = total + x
        print(f"The sum of all numbers from 1 to {x} = {total}")
        x += 1

    print(f"The sum of all numbers from 1 to {maximum} = {total}")


**Exercise 12**

    count = 0
    for number in range(1, 20):
        if number > 15:
            print(f"This number is bigger than 15: {number}")
        if number % 3 == 0:
            count += 1
            print(f"This number is exactly divisible by 3: {number}")
    print(f"From the numbers 1 to 20 there are {count} numbers that are exactly divisible by 3.")

**Exercise 13**

    for x in range(1, 6):
        for y in range(1, 4):
            print(f"x = {x}, y = {y}")
        print(f"The value of x is now {x} and we have just finished the loop over y")

**Exercise 14**

    for x in range(1, 6):
        for y in range(1, x):
            print(f"x = {x}, y = {y}")
        print(f"The value of x is now {x} and we have just finished the loop over y")

</details>
