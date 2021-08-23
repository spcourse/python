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

    print(f"The sum of all numbers from 1 to 10 = {total}")

Please change this program by including another print statement: `print(f"The sum of all numbers from 1 to {x} = {total}")`. Include this line beneath `total = total + x`, in such a way that it starts at the same position (the same level of indentation). Run the program and try to understand what happens. Problems with indentation are a very common mistake when using loops, so it is important to see these types of 'mistakes' so you can recognize them later.

**Exercise 9** At this moment we use the numbers from 1 to 10. Please try to adapt the program in such a way that you define a new variable once at the beginning of the program (so not in the range() function) that holds the maximum number. Use this maximum number as the maximum value for the for-loop: `for x in range(1, maximum)`.

**Exercise 10** Make a program that has the same functionality as the example, but now use a while-loop instead of a for-loop.

**Exercise 11** Replace the while-loop condition to ensure that it will stop if the sum of all numbers up to that point is bigger than 123. To help you, the expected output is provided:

	Value of sum_x: 0, value of x: 10
	Value of sum_x: 10, value of x: 11
	Value of sum_x: 21, value of x: 12
	Value of sum_x: 33, value of x: 13
	Value of sum_x: 46, value of x: 14
	Value of sum_x: 60, value of x: 15
	Value of sum_x: 75, value of x: 16
	Value of sum_x: 91, value of x: 17
	Value of sum_x: 108, value of x: 18
	End value of sum_x: 126, end value of x: 19

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

Adapt the program in such a way that the print-statement is only executed *if* the sum of `x` and `y` is more than 6.

**Exercise 14** Adapt the program in such a way that at the moment just before a new value is assigned to `x` (i.e. just after the loop over y is finished), the program prints: `The value of x is now ... and we have just finished the loop over y`.

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

**Exercise 15** Adapt the program in such a way that `y` does not run from 1 to 4, but from 1 to the value of `x`.

**Exercise 16** Adapt the program of exercise 8 to use a while-loop for the value of `y`. The for-loop for `x` stays the same.

**Exercise 17** Adapt the original program in such a way that the loop over `y` is only executed *if* `x` is larger than 3. *Keep* the range(1,6) in the for-loop of `x` the same, using a conditional (an if-statement) as a solution.

Here's an example of what the output should be:

	x = 4, y = 1
	x = 4, y = 2
	x = 4, y = 3
	x = 5, y = 1
	x = 5, y = 2
	x = 5, y = 3

Could you get the same result by changing the range in the for-loop of `x`?

## Solutions
Below you can find some solutions.

> Disclaimer: There are always many ways to solve a problem. The solutions here are not said to be the best solutions.
**Having a different solution, does not necessarily mean it is wrong**.
> 
> You should not have to rely on these solutions. If you cannot make the practice exercises at all without looking at these solutions, you should discuss this with your teacher.

<details markdown="1"><summary  markdown="span">Answers</summary>

</details>
